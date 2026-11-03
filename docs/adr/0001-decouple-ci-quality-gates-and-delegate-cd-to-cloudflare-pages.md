# ADR-0001: Decouple CI Quality Gates (Gitea Actions) and Delegate CD to Cloudflare Pages (GitHub Webhook)

- Status: Accepted
- Date: 2026-11-02
- Deciders: Fabian Andres Cortes (@kiskaadee)
- Consulted: Antigravity Assistant

## Context and Problem Statement
The `corazoncp` ecosystem hosts its sovereign repositories on a self-hosted Gitea forge (`gitea.roadtotech.me`), automatically push-mirrored to GitHub (`github.com/corazoncp`). The first deliverable, `corazoncp-landing`, is a high-performance static web application built with Vite and Tailwind CSS v4, targeted for global edge hosting on Cloudflare Pages (`elcorazoncomoportal.com`).

Initial pipeline configuration in `corazoncp-landing` combined both validation and continuous deployment in `.gitea/workflows/deploy.yaml` using `cloudflare/wrangler-action`. However, this setup encountered concrete operational and architectural frictions:
1. **Secrets Exposure & Principle of Least Privilege**: Deploying via Wrangler in CI requires storing a high-privilege `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` in repository secrets.
2. **Homelab Runner Bottleneck**: Running Wrangler inside local container runners (`homelab-runner` via `act`) repeatedly installed Node/pnpm/Wrangler dependencies from scratch, adding 9+ minutes of overhead and network egress per run.
3. **No Automatic Pull Request Previews**: Wrangler CLI deployments require custom scripts to manage preview aliases for pull requests.
4. **Client Handover Friction**: Azu will eventually take full ownership of the production site and domain. Coupling Cloudflare deployment tokens to the developer's personal Gitea secrets creates account entanglements during future client migration.

How should Continuous Integration (CI) and Continuous Delivery (CD) be structured to preserve developer sovereignty, minimize secret exposure, and facilitate effortless client handover?

## Decision Outcome
Chosen option: **Decouple CI and CD boundaries**:
- **Continuous Integration (Quality Gate) on Gitea Actions**:
  - The self-hosted Gitea runner (`homelab-runner`) executes `.gitea/workflows/ci.yaml` on every branch push and pull request.
  - Scope is strictly quality enforcement: Biome check (linter & formatter), unit/seam test suites (`node:test`), and static build verification (`pnpm build`).
- **Continuous Delivery (Edge Deployment) on Cloudflare Pages via GitHub**:
  - Cloudflare Pages is connected directly via native OAuth webhook to the mirrored `corazoncp/corazoncp-landing` repository on GitHub.
  - Cloudflare's global build fleet detects pushes to `main`, runs `pnpm build`, and serves `dist/` globally with automatic cache invalidation and zero runner overhead on the homelab.
  - Pull requests mirrored to GitHub automatically receive isolated preview URLs (`<branch>.elcorazoncomoportal.pages.dev`).
- **Zero Deployment Credentials in Git / CI**:
  - No `CLOUDFLARE_API_TOKEN`, `CLOUDFLARE_ACCOUNT_ID`, or registrar (Spaceship) API keys may ever be committed or stored in Gitea repository secrets.
- **Portable Edge Configuration in Version Control**:
  - Security headers (CSP, HSTS, X-Frame-Options) and routing rules are tracked in [`public/_headers`](file:///home/kiskaadee/Projects/active/corazoncp/corazoncp-landing/public/_headers) and [`public/robots.txt`](file:///home/kiskaadee/Projects/active/corazoncp/corazoncp-landing/public/robots.txt), which Cloudflare Pages natively evaluates, ensuring zero dashboard lock-in.

## Consequences
- **Positive**:
  - **Zero credential leakage risk**: No long-lived Cloudflare or registrar tokens exist in CI/CD runner environments.
  - **Homelab resource preservation**: The local homelab runner only runs fast lint and test jobs (10–15 seconds); it does not build or upload multi-megabyte image assets to Cloudflare.
  - **Instant PR Previews**: Branch previews are generated natively by Cloudflare Pages out of the box.
  - **Effortless Client Handover**: When transferring ownership to Azu, she only needs an invite to the `corazoncp` GitHub organization and Cloudflare Pages project. No Gitea secrets need rotation or re-keying.
- **Negative**:
  - **Multi-Hop Deployment Latency**: Production deployments depend on Gitea's push mirror reaching GitHub before Cloudflare triggers (~30–60 seconds sync latency).
  - **Vendor Dependency for Delivery**: CD requires GitHub and Cloudflare availability, while CI remains 100% sovereign.

## Alternatives Considered
- **All-in-One Gitea Pipeline with Wrangler**: Rejected due to token security risk, homelab runner load, and lack of automatic branch preview links.
- **Pure GitHub Actions**: Rejected because Gitea is the primary development forge and source of truth for issues, pull requests, and quality validation.

## Related Documents
- Infrastructure & Handover Guide: [`corazoncp/docs/infra/dns-and-handover.md`](../infra/dns-and-handover.md)
- Landing Page Brief: [`corazoncp-landing/docs/specs/landing-page-brief.md`](../../corazoncp-landing/docs/specs/landing-page-brief.md)
- Tracking Issue: `corazoncp-landing#10`

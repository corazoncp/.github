# AGENTS.md: corazoncp hub

Organization hub (`corazoncp/.profile`, mirrored to GitHub `corazoncp/.github`) and container workspace for **El Corazón como Portal**.

## Rules for working in this workspace
- **Multi-repo boundary:** Root tracks organization-wide strategy, discovery (`docs/`), and [`ROADMAP.md`](./ROADMAP.md). Deliverables like `corazoncp-landing/` (and future `corazoncp-api/`) are independent nested Git repositories ignored by root—always verify `git rev-parse --show-toplevel` so code, `docs/specs/`, branches, and commits land in the target repo.
- **Source of truth:** Read [`ROADMAP.md`](./ROADMAP.md), Gitea milestones/issues, root `docs/`, and the target repo's `docs/specs/` before changing code. Never invent offerings, pricing, schedules, therapeutic claims, or contact details.
- **Evidence-gated vertical slices:** Build strictly what the active slice requires. Do not introduce backend services (`corazoncp-api`), databases, auth, booking calendars, or payment gateways ahead of an active milestone.
- **Same-slice doc sync:** Update affected specs, docs, and Mermaid diagrams in the same slice whenever behavior, scope, or invariants change.
- **Interaction language:** Always interact, reason, document, commit, and communicate in English by default, while preserving sovereign Spanish for client-facing copy, public branding, and verbatim quotes.
- **Public mirror & client privacy:** All `corazoncp` repositories auto-mirror publicly to GitHub on push. Never commit `.internal/` intake files, client PII, questionnaire submissions, or unapproved photos/copy; only Azu-approved public assets and contact channels may enter tracked files.

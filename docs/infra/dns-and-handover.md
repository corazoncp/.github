# Infrastructure Specification: DNS, Edge Routing & Client Handover Protocol

- Domain: `elcorazoncomoportal.com`
- Registrar: Spaceship
- Edge CDN & Hosting: Cloudflare Pages (`elcorazoncomoportal.pages.dev`)
- Upstream Organization: `corazoncp` (Gitea `gitea.roadtotech.me` push-mirrored to GitHub `github.com/corazoncp`)

---

## 1. DNS Zone Inventory

To prevent DNS record loss or misconfiguration during future account migrations, all authoritative DNS records for `elcorazoncomoportal.com` are documented below:

| Type | Name / Host | Target / Value | Proxy Status | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **CNAME** | `@` (apex) | `elcorazoncomoportal.pages.dev` | Proxied (Orange Cloud) | Production landing page root |
| **CNAME** | `www` | `elcorazoncomoportal.pages.dev` | Proxied (Orange Cloud) | Canonical www redirect / alias |
| **TXT** | `_headers` | *(evaluated natively by Cloudflare Pages via `public/_headers`)* | N/A | CSP, HSTS, frame options |

> **Note on Mail / Communication Services**: When Azu provisions corporate email (e.g. Google Workspace, Zoho Mail, or Proton Mail), MX, SPF, DKIM, and DMARC TXT records must be recorded in this table before activation.

---

## 2. Cloudflare Pages Build Contract

Cloudflare Pages connects to the GitHub repository `corazoncp/corazoncp-landing` with the following canonical settings:

- **Framework preset**: `Vite` (or None)
- **Build command**: `pnpm build`
- **Build output directory**: `dist`
- **Root directory**: `/`
- **Environment variables**:
  - `NODE_VERSION`: `22`
  - `PNPM_VERSION`: `10`
- **Build Watch Paths (Deployment Filtering)**:
  - **Include paths**: `*`
  - **Exclude paths**: `docs/**`, `*.md`, `todo.txt`, `.gitea/**`, `flake.*`, `tests/**`
  - **Filter Invariant**: Cloudflare Pages automatically cancels/skips builds when incoming commits only touch documentation, task trackers, local Nix development configs, unit tests, or CI workflow files. Deployments are triggered strictly when runtime code (`index.html`, `src/**`, `public/**`, build configurations) is modified.

---

## 3. Client Handover Protocol (Transferring Ownership to Azu)

When Azu is ready to take sovereign ownership of the platform, follow this zero-downtime handover protocol:

### Phase 1: Identity & Organization Invitation
1. Azu creates a personal or corporate account on GitHub.
2. Invite Azu's GitHub account as an **Owner** of the GitHub organization `corazoncp` (`https://github.com/orgs/corazoncp/people`).
3. Azu creates her own account on [Cloudflare](https://dash.cloudflare.com/sign-up).

### Phase 2: Dual-Option Cutover

#### Option A: Super Administrator Delegation (Zero Nameserver Cutover)
1. In the current Cloudflare account, navigate to **Manage Account $\rightarrow$ Members**.
2. Invite Azu as a **Super Administrator**.
3. Azu enters her billing details under Account $\rightarrow$ Billing.
4. Remove developer credentials from the account.
*Downtime: 0 seconds. DNS changes: 0.*

#### Option B: Full Account & Nameserver Migration
1. In Azu's Cloudflare account, click **Add a Domain** $\rightarrow$ `elcorazoncomoportal.com`.
2. Cloudflare will assign two unique nameservers (e.g., `carol.ns.cloudflare.com` and `dave.ns.cloudflare.com`).
3. Import the DNS Zone records documented in Section 1 into Azu's Cloudflare Zone.
4. In Azu's Cloudflare account, navigate to **Workers & Pages** $\rightarrow$ **Create Application** $\rightarrow$ **Pages** $\rightarrow$ **Connect to Git**.
5. Select GitHub Organization `corazoncp` and repository `corazoncp-landing`. Configure the build contract from Section 2.
6. Under **Custom Domains**, attach `elcorazoncomoportal.com` and `www.elcorazoncomoportal.com`.
7. At domain registrar (Spaceship), update the domain nameservers from the old Cloudflare nameservers to Azu's new Cloudflare nameservers.
*Because Cloudflare pre-provisions SSL certificates before nameserver validation, visitors experience zero interruption during DNS propagation.*

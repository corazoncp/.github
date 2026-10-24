# El Corazón como Portal — Workspace Guidelines

This file defines the strict runtime, development, and toolchain constraints for AI agents operating within the `corazoncp` ecosystem. Adhere to these behavioral boundaries without deviation.

For operational context & ecosystem topology: [See README](./README.md)

---

## 1. System Discovery & Single Source of Truth (SSOT)

Do not assume architectural requirements or business logic rules. You must explicitly read the dedicated documentation inside each repository before modifying or writing code:
- **Trajectory & Active Work (`ROADMAP.md`):** Read the root [`ROADMAP.md`](./ROADMAP.md) to verify the current milestone and active task priorities before starting work.
- **Product Requirements & Domain Model:** Review `docs/` in this repository for ecosystem discovery, and the sub-repository's local `docs/specs/` for deliverable-specific acceptance criteria.
- **Architecture Philosophy:** Strict **Agile Vertical Slices** with user stories as the source of truth. Do not build premature infrastructure, abstract database schemas, or payment gateways until an active user story explicitly requires it.

### Documentation Drift Prevention Rule
Documentation must evolve symmetrically alongside the source code. If a feature implementation or bug fix alters system behavior, changes an invariant, or introduces a new pattern:
1. **Self-Documenting Code:** Write highly expressive code using explicit domain-driven naming and clear test assertions.
2. **Inline & Static Sync:** Simultaneously update the corresponding inline comments, Markdown documentation files, and Mermaid diagrams in the same commit.

---

## 2. Git & Branching Constraints

### Pre-Development Workflow
Before writing, modifying, or refactoring any code:
- **Clean Tree:** Verify the working directory is clean by running `git status`.
- **Sync Main:** Run: `git checkout main && git pull origin main`
- **Isolated Branch:** Check out a dedicated branch matching the patterns below.

### Branch Naming Conventions
- **Features:** `feat/<issue-id>-<short-description>` (e.g., `feat/landing-hero`)
- **Fixes:** `fix/<issue-id>-<short-description>`
- **Chores/Refactors:** `chore/<short-description>`
- **Documentation:** `docs/<short-description>`
- **Anne Droid Delegation:** `feat/anne/*`

### Commit & Push Policy
- **Main Protection:** **NEVER** commit or push changes directly to the `main` branch of repositories.
- **Format:** Follow the [Conventional Commits](https://conventionalcommits.org) specification.
- **Immediate `git-commit` Handoff Rule (Anti-Accumulation):** Never let verified changes accumulate across multiple tasks or milestones in a dirty working tree. Immediately after completing and verifying a deliverable, invoke the `git-commit` skill (`/git-commit`) to slice, review, and commit the changes atomically, followed by `commit-logger`.

---

## 3. Registered Personas & Agent Delegation

When tasks involve specialized domains, delegate to registered personas:
- **Anne Droid (`profile/agents/anne-droid.md`)**: Senior Frontend Engineer & UX Specialist.
  - **Consult when:** UI impact, visual aesthetics, accessibility review, or design token alignment.
  - **Delegate when:** Frontend components, responsive client styling, web interactions, or client tests need implementation. Anne operates strictly on `feat/anne/*` branches with PR-based review.
  - **Do not invoke for:** Backend-only logic, database internals, NixOS configuration, infrastructure, or deployment.

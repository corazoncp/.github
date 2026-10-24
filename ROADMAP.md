# Roadmap — El Corazón como Portal

This roadmap outlines the evolution of the `corazoncp` ecosystem through vertical slices.

---

## Milestone 0: Workspace & Ecosystem Foundation `[DONE]`
- [x] Provision sovereign Gitea organization `corazoncp` and GitHub mirror org `corazoncp`.
- [x] Provision `.profile` on Gitea mirrored to `.github` on GitHub.
- [x] Configure automated push mirroring with sync on commit.
- [x] Establish root container workspace (`~/Projects/active/corazoncp`).
- [x] Scaffold initial repository guidelines (`AGENTS.md`, `.gitignore`, `ROADMAP.md`).

---

## Milestone 1: Deliverable 1 — Public Landing Page (`corazoncp-landing`) `[ACTIVE]`

Target: Launch a responsive, aesthetic landing page this week driving inquiries to WhatsApp.

- [ ] **Slice 0: Product Brief & Content Hierarchy**
  - Synthesize Azu's input, questionnaire responses, and brand flyer.
  - Establish confirmed facts vs. open assumptions in `landing-page-brief.md`.
  - Outline 5 core content sections (Hero, Meet Azu, Ways to Work Together, Mission, WhatsApp CTA).
- [ ] **Slice 1: Structure & Low-Fidelity Wireframe Validation**
  - Layout hero message, service cards, and primary contact action.
  - Review content hierarchy with Azu.
- [ ] **Slice 2: First Usable Preview (Hero + Offerings + WhatsApp Action)**
  - Implement responsive mobile-first UI with Anne Droid on `feat/anne/*`.
  - Verify working WhatsApp deep links with pre-filled message text.
  - Deploy preview URL for mobile testing.
- [ ] **Slice 3: Approved Content & Visual Direction**
  - Integrate approved photography, warm earthy palette (inspired by Sagrada Ela reference), and typography.
  - Finalize service descriptions (Access Bars, Body Process, Mentoring).
- [ ] **Slice 4: Launch & Verification**
  - Verify mobile responsiveness, accessibility (WCAG AA basics), and fast loading.
  - Connect custom domain / production deployment.

---

## Milestone 2: Appointment & Booking Engine (`corazoncp-api`) `[DEFERRED]`
- [ ] Revisit only after the landing page is live and driving real inquiry traffic.
- [ ] Discover automated calendar requirements based on actual client volume.

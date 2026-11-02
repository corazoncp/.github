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

- [x] **Slice 0: Product Brief & Content Hierarchy**
  - Synthesize Azu's input, questionnaire responses, and brand flyer.
  - Establish confirmed facts vs. open assumptions in `landing-page-brief.md`.
  - Codify visual canvas, layout specifications, and design tokens in `visual-canvas-and-layout.md`.
- [x] **Slice 1: Structure & Toolchain Scaffold**
  - Initialize project with Vite+ (`vp`) unified toolchain and Biome linter/formatter.
  - Configure Tailwind CSS v4 design tokens and Google typography.
  - Lay out 6-section document skeleton with navigation anchor links.
- [x] **Slice 2: Hero & Multi-Touch WhatsApp Flow**
  - Implement dual-modality eyebrow badge (`ACOMPAÑAMIENTO CONSCIENTE · VALLEDUPAR & ONLINE`).
  - Ground Hero narrative around autopilot, mental chatter, nervous system fatigue, and opening the heart.
  - Implement persistent floating WhatsApp action button with $\ge 48\text{px}$ touch target and SVG icon.
  - Enforce strict phone number isolation (`+57 321 542 8972`) and automated seam test suite (`node:test`).
- [ ] **Slice 3: Outcome-First Service Cards & Transition Bridge**
  - Implement revised 4-card catalog sequence (Oidaterapia $\rightarrow$ Kundalini $\rightarrow$ Barras de Access® $\rightarrow$ Meditaciones).
  - Include official Access Consciousness® registered trademark symbol and link.
  - Connect Section 04 "Recursos Gratuitos: Luz en tu Camino" bridge to YouTube guided meditations.
  - Provide individual contextual WhatsApp CTAs per card.
- [ ] **Slice 4: Acerca de Azu, Filosofía & Contact Directory**
  - Implement "Acerca de Azu" narrative with natural lifestyle portrait.
  - Implement "Filosofía" banner featuring Anahata chakra and sovereign Animados.
  - Implement Section 07 "Contacto" directory: verified Valledupar address, email, social channels.
  - Execute full mobile viewport, WCAG AAA contrast, and performance verification.
- [ ] **Slice 5: Bilingual (ES/EN) Localization & Navigation Toggle**
  - Implement multi-page static routing in Vite (`/` for Spanish root, `/en/` for English).
  - Add header language switcher toggle (`[ ES | EN ]`) with persistent visual state.
  - Add SEO/AEO metadata (`hreflang` alternates, English OpenGraph, Schema.org).
  - Localize WhatsApp deep links and integrate Azu-approved English copy across all 7 sections.
  - Enforce structural parity invariant between `index.html` and `en/index.html`.

---

## Milestone 2: Appointment & Booking Engine (`corazoncp-api`) `[DEFERRED]`
- [ ] Revisit only after the landing page is live and driving real inquiry traffic.
- [ ] Discover automated calendar requirements based on actual client volume.

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

Target: Launch a responsive, aesthetic landing page driving inquiries to WhatsApp.

- [x] **Slice 0: Product Brief & Content Hierarchy**
  - Synthesize client input, questionnaire responses, and brand flyer.
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
  - Decouple CI quality gate and delegate CD to Cloudflare Pages (ADR-0001). Connect custom domains `elcorazoncomoportal.com`.
- [x] **Slice 3: 5-Card Service Catalog, Brand Tokens, Complementary Paths & Facebook Channel** `[DONE · PR #15 MERGED]`
  - **Prerequisite / Blocker:** Transcode client raw photos (`.CR3`, `.CR2`, `.HEIC`) from `.internal/img/photos/` to web-optimized `.webp` assets ($\le 150$KB) in `corazoncp-landing/public/img/`.
  - Implement approved 5-card catalog sequence in balanced 3 + 2 centered grid (Oidaterapia $\rightarrow$ Kundalini $\rightarrow$ Barras de Access® $\rightarrow$ Procesos de Cuerpo $\rightarrow$ Meditaciones Personalizadas).
  - Include official Access Consciousness® registered trademark symbol and link (`target="_blank" rel="noopener noreferrer"`).
  - Configure typography stack (`Playfair Display` for section titles, `Cormorant Garamond` for card titles, `Raleway` for body/UI) and color tokens (`Porcelain Mist` `#F4F1EA`, `Gris Oscuro` `#303030`).
  - Implement Hero polish (approved subtitle copy with *profunda*, increased desktop caption font size, soft green tint header contrast).
  - Implement Section 04 Complementary Paths as an asymmetric 65/35 composition under `EXPLORA OTROS ESPACIOS` (65% Hatha Yoga card anchor + 35% quiet open resources panel).
  - Pull forward Facebook Fanpage channel integration in footer.
  - Provide individual contextual WhatsApp CTAs per card.
  - Reconcile client review feedback (Nov 6–8 audio intake):
    - Re-crop Barras de Access® photo (`IMG_0455.HEIC`) to prioritize client's face and Azu's hands.
    - Level bio photo horizon with Nam Nidhan Kaur (`IMG_1994.HEIC`, -1.5° counter-clockwise rotation).
    - Correct Valledupar postal code to `200001` in Section 07 (Contacto).
- [ ] **Slice 4: Acerca de Seva Surpreet Kaur, Filosofía, Telegram Contact Bot & Launch QA**
  - **Prerequisite / Blocker:** Transcode namasté bio photo `IMG_1994.HEIC` to web-optimized `.webp` *(completed ahead of schedule)*.
  - Standardize all social media and channel icons using official `simple-icons` vectors with unified $24\times 24$ geometry and `currentColor` styling.
  - Implement "Acerca de Seva Surpreet Kaur" narrative (photo `namaste-bio.webp`, dropping "Azu" from heading, Colombian TV-to-healing journey).
  - Implement "Filosofía" banner featuring *«Conecta con tu guía interno»* and sovereign Animados (*«sabiduría trascendental del corazón»*).
  - Implement Section 07 "Contacto Consciente" serverless edge intake (`functions/api/contact.ts` + Cloudflare D1 SQLite database + Telegram Bot API push alerts) with anti-bot honeypot and transparent channel comparison microcopy.
  - Verify complete public contact directory (WhatsApp, email, Facebook, Instagram, YouTube, X, Google Maps address).
  - Execute full mobile viewport, WCAG AAA contrast, keyboard navigation, and launch verification.
- [ ] **Slice 5: Bilingual (ES/EN) Localization & Navigation Toggle**
  - Implement multi-page static routing in Vite (`/` for Spanish root, `/en/` for English).
  - Add header language switcher toggle (`[ ES | EN ]`) with persistent visual state.
  - Add SEO/AEO metadata (`hreflang` alternates, English OpenGraph, Schema.org).
  - Localize WhatsApp deep links and integrate validated English copy across all 7 sections.
  - Enforce structural parity invariant between `index.html` and `en/index.html`.
- [ ] **Slice 6: Outcome-First Testimonials & Deep Process Definitions `[BACKLOG · POST-LAUNCH]`**
  - **Prerequisite:** Azu to complete Oidaterapia thesis and "laboratorio interior" strategic formulation.
  - **Outcome-Based Testimonials:** Implement dedicated editorial testimonial section highlighting concrete, tangible client outcomes and nervous-system transformations (no generic praise).
  - **Deepened Process Definitions:** Update modalities with Azu's evolved therapeutic framework.

---

## Milestone 2: Appointment & Booking Engine (`corazoncp-api`) `[DEFERRED]`
- [ ] Revisit only after the landing page is live and driving real inquiry traffic.
- [ ] Discover automated calendar requirements based on actual client volume.

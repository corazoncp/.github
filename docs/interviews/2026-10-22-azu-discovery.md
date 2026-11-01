# Intake Questionnaire Synthesis — Azu Seva

- **Date:** 2026-10-22 23:27:56 (COT)
- **Source Artifact:** `.internal/Azu Seva_ Preguntas Clave para tu Sistema de Citas_Submissions_2026-11-01.csv`
- **Participant:** Azucena Sánchez (Azu Seva Surpreet Kaur)
- **Document Status:** Canonical discovery synthesis (source-pure representation of the initial intake questionnaire)

---

## 1. Offerings & Service Taxonomy

Azu indicates that her focus has evolved (*"mi enfoque ha ido cambiando"*), defining four distinct fulfillment archetypes:

### A. Direct 1:1 In-Person Therapies
- **Barras de Access®:**
  - *Duration:* 45 min – 1 hr
  - *Modality:* Strictly presencial
  - *Scope:* Immediate candidate for booking/scheduling.
- **Procesos de Cuerpo:**
  - *Duration:* 35 min – 50 min
  - *Modality:* Strictly presencial
  - *Scope:* Immediate candidate for booking/scheduling.

### B. Packages & Consultations (1:1 & Dual Modality)
- **Mentorías / Taller Oidaterapia:**
  - *Format:* Multi-session package (initial booking + prepaid follow-ups)
  - *Duration:* 50 min – 1 hr (can extend up to 1 hr 10 min)
  - *Modality:* Presencial / Virtual
- **Sesión puntual Oidaterapia (90 min):**
  - *Duration:* 90 min
  - *Modality:* Presencial / Virtual
  - *Note:* Commercial framing and concrete outcome still being refined by Azu (*"Aún me falta pensar comercialmente qué ofrecería, pero sería algo concreto de ir a revisar durante la sesión y poner una herramienta de Oida en acción con el cliente"*).
- **Acompañamiento Kundalini Yoga (Personalizado):**
  - *Format:* Multi-session accompaniment
  - *Duration:* Initial session 2 hrs; follow-up sessions 45 min – 1 hr.

### C. Asynchronous Digital Delivery
- **Meditaciones Personalizadas:**
  - *Format:* Delivered via email/audio ~2 days following intake form completion.
  - *Calendar Rule:* Not scheduled on an interactive calendar slot.

### D. Corporate, Group & Future Horizons
- **Hatha Yoga:**
  - *Duration:* 1 hr – 1 hr 30 min (no open booking agenda).
  - *Format:* Corporate classes, custom recorded classes, or promotional park/home sessions.
  - *Recommended CTA:* Inquiries / Contact form (*"Contáctanos"*) rather than automated scheduling.
- **Programas Kundalini Yoga:** Group classes, typically 1 hr – 1 hr 30 min, structured across multi-week programs.
- **Otros Programas (ej. Arte Oidaterapia):** 1 hr 30 min – 2 hrs.
- **Talleres de Oidaterapia / Exploración de Fe:** Hybrid 2-session workshop formats with intermediate activities.
- **Future Explorations:** Oida Tours (eco-spiritual group journeys), 12-Step Mentorship/Tutoring (monthly recurring checkpoints), and free community funnel spaces (promoted via social media, outside main web agenda).

---

## 2. Operational Invariants & Scheduling Rules (For Future System Reference)

- **Buffer Time:** 15 min rest/preparation buffer between sessions $\le$ 1 hr. Sessions $\ge$ 1 hr 30 min require 0 min buffer.
- **Base Availability:** Monday to Friday:
  - Morning block: 9:30 AM – 12:00 PM
  - Afternoon block: 1:30 PM – last session scheduled at 6:00 PM or 6:30 PM.
- **Dynamic Weekly Overrides:** Preference for weekly dynamic blocking/enabling of slots over rigid static recurrence (e.g., reserving mornings for corporate classes).
- **Booking Lead Time:**
  - Morning appointments: Must be booked by 7:00 PM the prior evening.
  - Same-day afternoon appointments: Minimum 4 hours advance notice.
- **Client Form Fields:**
  - Mandatory: Name, Phone (WhatsApp), Email.
  - Conditional: Experience level (relevant only for yoga classes, clarifying no prior experience is required).
- **Payment Policy:** Upfront payment required upon booking to confirm time slot.
- **Payment & Reference Benchmarks:**
  - Referenced Flodesk workflow for dual domestic and international payment links (`view.flodesk.com/emails/6aa2d1b7cbfd3a06d2c9fc19`).
  - Referenced Sagrada Ela (`sagradaela.com.co`) as a product catalog benchmark for offering individual sessions alongside courses and multi-session packages.
- **Notification Flow:** Direct creation in Google Calendar plus email notification confirmation.

---

## 3. Evidence-Gated Horizon Partitioning

To avoid premature complexity in the current deliverable while preserving domain truth, observations are split across delivery milestones:

### Horizon 1: Immediate Landing Page Scope (`corazoncp-landing` / Slice 0–1)
- Verify which subset of offerings represents Azu's active focus for v1 launch (Access Bars, Body Process, Mentoring, vs. 1:1 Kundalini / Meditations).
- Clarify whether pricing (COP / USD) and exact durations should appear on public cards or route to WhatsApp inquiries.
- Confirm exact location wording for in-person sessions (e.g., Barrio Vipasa, Cali, or home visit / *a domicilio*).
- Check subsequent `.internal/` documents (`BRIEF PUBLICITARIO.docx`, `TRACKER.docx`) to determine if these questions were already resolved.

### Horizon 2: Deferred Scheduling Engine (`corazoncp-api` / Milestone 2)
- Calendar slot quantization (ranges vs. fixed slots, `1h 10m` overrun handling, buffer logic).
- Day boundary definitions (interpreting last start time vs. hard cutoff at 6:00/6:30 PM).
- Multi-currency payment gateway integration and prepaid package credit tracking.

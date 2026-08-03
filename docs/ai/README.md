# Cure Health — AI use cases

Cure Health is a multi-portal digital health platform, and AI runs through every portal — patient, provider, pharmacy, and insurer. Each feature below is grounded in real records (charts, prescriptions, orders, claims), runs on **Claude Sonnet 4.6 via OpenRouter**, and is built with the same safety posture: strict system prompts, server-side validation that fails toward caution, role-scoped access, and audit logging that never records message or PHI content. Clinical features are demo/education tools and are **not medical advice** — every draft is meant for a qualified human to review.

**[▶ Try it live → curehealth.kognio.ai](https://curehealth.kognio.ai)** · use the one-click **persona quick-login** buttons (shared password `Demo1234!`).

Each use case has its own full breakdown:

## Patient portal

### AI Care Navigator
Describe symptoms and get a streaming, plain-language assessment plus a structured severity, recommended specialty, red-flag list, and visit-prep checklist.
[Read the full breakdown →](./ai-care-navigator.md)

### AI Triage
A quick, conversational triage that recommends a real specialty and an urgency level to guide how soon to book.
[Read the full breakdown →](./ai-triage.md)

### AI Booking Assistant
A tool-calling agent that finds providers, checks real free slots, confirms details, and books the appointment — all in chat.
[Read the full breakdown →](./booking-assistant.md)

### Medication Adherence Coach
A supportive chat that already knows the patient's prescriptions and helps with timing, routines, reminders, and mild side effects.
[Read the full breakdown →](./adherence-coach.md)

### Visit Summary
Turns a completed visit's clinical note into a warm, plain-language recap of what happened and what to do next.
[Read the full breakdown →](./visit-summary.md)

### Claim Helper
Paste a receipt or invoice and extract structured, validated claim-prefill data (kind, provider, amount, date).
[Read the full breakdown →](./claim-helper.md)

## Provider portal

### Clinical Care-Plan Generator
Drafts an editable, chart-grounded care plan — problems, goals, interventions, medication considerations, follow-up, education — with a clinician-review disclaimer.
[Read the full breakdown →](./care-plan-generator.md)

### Draft Encounter Note
Turns shorthand bullet points into a structured S/O/A/P note using only the facts supplied.
[Read the full breakdown →](./draft-note.md)

### Scribe
An AI scribe that distills a full consultation transcript into a structured S/O/A/P note.
[Read the full breakdown →](./scribe.md)

### Drug-Interaction Check
Checks a proposed medication against the patient's allergies and current meds, failing toward caution.
[Read the full breakdown →](./interaction-check.md)

## Pharmacy portal

### Dispense Safety Check
A last-line safety check on an order's medication against the patient's allergies and other current medications.
[Read the full breakdown →](./dispense-safety-check.md)

### Substitution Suggestions
Up to three generic or therapeutic alternatives, each with a guaranteed "confirm with the prescriber" note.
[Read the full breakdown →](./substitution-suggestions.md)

### Patient Medication Label
Generates a plain-language patient label (dose, timing, warnings) in English or Albanian from the prescription facts.
[Read the full breakdown →](./patient-label.md)

### Demand Forecast
30-day order aggregates by medication for the pharmacy, with a short AI narrative and stocking advice on top of the real numbers.
[Read the full breakdown →](./demand-forecast.md)

## Insurer portal

### Claims Copilot
Runs four deterministic adjudication checks and adds an AI recommendation (`approve` / `deny` / `needs_info`) with a grounded rationale.
[Read the full breakdown →](./claims-copilot.md)

### Fraud Scan
Computes per-claim statistics (median amount, claim frequency, denied-resubmissions) and flags anomalies worth a human's closer look.
[Read the full breakdown →](./fraud-scan.md)

# Drug-Interaction Check

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: provider

## The use case
Before prescribing, a clinician wants a quick safety read on a proposed medication against what the patient is already taking and is allergic to. This tool surfaces likely allergy conflicts, interactions, and duplications as decision support.

## How the AI works
The provider must have a treatment relationship with the patient. The server gathers the patient's allergies and current medications (active/sent/dispensed) and asks Claude, in JSON mode, to assess the proposed drug against them. If there is nothing to check against, no LLM call is made. The output is validated: flag severities outside `caution|danger` are coerced to the safe minimum, and an invalid overall risk falls back to at least `caution` (or `danger` when any danger flag is present) — the system fails toward caution. This is decision support only, not a prescribing directive or medical advice.

## What you get
- An overall risk level: `none` / `caution` / `danger`
- Per-flag detail: severity, what it interacts with, and a one-line explanation
- Allergy-, interaction-, and duplication-aware checks

## Try it live
Use the **Provider** quick-login button (`dr.arta@curehealth.dev`, password `Demo1234!`), open a patient you've seen, and check a proposed medication.

## Under the hood
`POST /ai/interaction-check` · gated on a treatment relationship · grounds on patient allergies + current `MedicationRequest` records · JSON-mode Claude Sonnet 4.5 via OpenRouter · severity/risk coerced toward caution · audited without PHI.

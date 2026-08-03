# Dispense Safety Check

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: pharmacy

## The use case
At the dispensing counter, a pharmacist wants a last-line safety check on the medication in an order against the patient's allergies and their other current medications — a second set of eyes before handing the drug over.

## How the AI works
The order is scoped to the calling pharmacy's organization (a foreign order returns 404). The server loads the patient's allergies and their other active medications — excluding the one being dispensed — and runs the shared safety-check engine: Claude assesses allergy conflicts, interactions, and duplications in JSON mode. When there is nothing to check against, no LLM call is made. Output is validated with the same fail-toward-caution coercion as the provider interaction check. This is decision support only, not a dispensing directive or medical advice.

## What you get
- An overall risk level: `none` / `caution` / `danger`
- Per-flag detail: severity, the conflicting allergy/medication, and a short explanation
- The other-medication under dispense excluded, so it doesn't flag against itself

## Try it live
Use the **Pharmacy** quick-login button (`pharma.aria@curehealth.dev`, password `Demo1234!`), open an incoming order, and run the safety check.

## Under the hood
`POST /ai/dispense-check` · order scoped to the pharmacy org · grounds on patient allergies + other current `MedicationRequest` records · JSON-mode Claude Sonnet 4.6 via OpenRouter · audited without PHI.

# Patient Medication Label

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: pharmacy

## The use case
Every dispensed medication needs a clear patient label — what it is, how and when to take it, and the key warnings — and in this Albanian platform, often in the patient's language. This generates that label text in English or Albanian in one click.

## How the AI works
The order is scoped to the calling pharmacy's organization. The prescription facts — medication, dosage, quantity, refills, instructions, and fulfillment method — are sent to Claude with a prompt that writes a short, plain-language label in the requested language (`en` → English, `sq` → Albanian). The model is bound to the given facts and told never to invent doses or warnings that don't follow from them. This is a demo/education feature; the label supports, and does not replace, a pharmacist's own labeling.

## What you get
- A concise, plain-language patient label
- Dose, timing, and key warnings drawn only from the prescription
- Output in English or Albanian on request

## Try it live
Use the **Pharmacy** quick-login button (`pharma.aria@curehealth.dev`, password `Demo1234!`), open an order, and generate a label in English or Albanian.

## Under the hood
`POST /ai/label` · order scoped to the pharmacy org · grounds on the dispensed `MedicationRequest` + `PharmacyOrder.fulfillment` · language `en`/`sq` · Claude Sonnet 4.5 via OpenRouter · audited without PHI.

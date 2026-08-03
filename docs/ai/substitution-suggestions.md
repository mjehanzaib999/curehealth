# Substitution Suggestions

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: pharmacy

## The use case
When a prescribed medication is out of stock or a cheaper equivalent exists, a pharmacist wants a shortlist of generic or therapeutic alternatives to discuss — always subject to prescriber confirmation.

## How the AI works
The order is scoped to the calling pharmacy's organization. The dispensed medication's name, dosage, quantity, and instructions are sent to Claude in JSON mode, which proposes up to three alternatives, each with a rationale and a practical note. The server hard-caps the list at three and guarantees safety framing: if a suggestion's note doesn't already mention the prescriber, it appends "Confirm with the prescriber before substituting." This is decision support for a licensed pharmacist, never a directive, and never medical advice.

## What you get
- Up to three generic or therapeutic alternatives
- A rationale for each, plus a practical note
- A guaranteed "confirm with the prescriber" reminder on every suggestion

## Try it live
Use the **Pharmacy** quick-login button (`pharma.aria@curehealth.dev`, password `Demo1234!`), open an order, and request substitutions.

## Under the hood
`POST /ai/substitutions` · order scoped to the pharmacy org · grounds on the dispensed `MedicationRequest` · JSON-mode Claude Sonnet 4.6 via OpenRouter · list capped at 3, prescriber-confirmation note enforced · audited without PHI.

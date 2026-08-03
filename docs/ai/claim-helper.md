# Claim Helper

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: patient

## The use case
Filing an insurance claim means re-typing details off a receipt or invoice. The Claim Helper lets a patient paste that text and have the AI extract the structured fields needed to pre-fill a claim — turning a chore into a review-and-confirm step.

## How the AI works
The pasted receipt or invoice text is sent to Claude in JSON mode with a strict output contract. The model guesses whether it's an appointment or prescription claim, the provider or pharmacy name, the amount (converted to integer euro cents), and the service date. Every field is validated and coerced server-side — an unrecognized kind becomes `null`, a non-integer amount becomes `null` — so nothing malformed reaches the claim form. Extraction is a starting point for the patient to verify, not an automatic submission.

## What you get
- A `kind` guess (appointment / prescription / none)
- Provider or pharmacy name
- Amount in cents and service date, when detectable
- A short note flagging anything ambiguous

## Try it live
Use the **Patient** quick-login button (password `Demo1234!`), open the claim helper, and paste a receipt like *"Clinic Vita — consultation 20 Feb 2026 — total 45.00 EUR."*

## Under the hood
`POST /ai/extract-claim` · JSON-mode Claude Sonnet 4.6 via OpenRouter · server-side field validation and cents coercion · audited without document content.

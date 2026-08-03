# AI Care Navigator

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: patient

## The use case
Patients rarely know which specialty to book or how urgently to act. The Care Navigator lets someone describe symptoms in plain words and get a calm, personalized read on how serious it sounds, which kind of clinician fits, and how to prepare for the visit.

## How the AI works
The endpoint streams a plain-language assessment token-by-token over Server-Sent Events, then makes a second call that returns a structured JSON block. The specialty list is grounded in the platform's actual practitioners, so it only ever recommends specialties that exist. A strict system prompt forbids diagnosing or naming medications, coerces unknown severities to the cautious `see_gp_soon`, and always opens with "call 112" for red-flag emergencies. This is a demo/education feature, not medical advice.

## What you get
- A streaming, plain-language assessment
- Severity (`self_care` → `emergency`) and a recommended specialty
- Red-flag list and 2–4 concrete next steps
- A personalized visit-prep checklist (bring / ask / monitor)

## Try it live
Use the **Patient** quick-login button (password `Demo1234!`), open the **Navigator** screen, and enter e.g. *"chest tightness and shortness of breath climbing stairs for a week."*

## Under the hood
`POST /ai/care-navigator` (SSE stream) · grounds on distinct `Practitioner.specialty` values · Claude Sonnet 4.6 via OpenRouter · audited with no message content logged.

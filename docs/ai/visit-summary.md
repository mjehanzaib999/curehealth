# Visit Summary

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: patient

## The use case
Clinical encounter notes are written for clinicians, not patients. This feature turns a completed visit's note into a short, warm, plain-language summary so a patient understands what happened and what to do next.

## How the AI works
The patient can only summarize their own completed appointments that actually have an encounter note (otherwise the request is rejected). The server builds context from the visit — provider name, specialty, date, reason, and the clinician's note — and asks Claude to rewrite it for the patient. The prompt is faithfulness-bound: use only facts present in the note, never invent findings, diagnoses, or medications, and never alter any instruction. This is a demo/education feature, not medical advice.

## What you get
- A concise, plain-language recap of the visit
- What happened and what to do next, in the patient's words
- No new clinical content — a faithful rewrite of the real note

## Try it live
Use the **Patient** quick-login button (password `Demo1234!`), open a completed appointment, and generate its summary.

## Under the hood
`POST /ai/visit-summary` · requires a `completed` appointment with a note owned by the patient · grounds on the encounter note · Claude Sonnet 4.6 via OpenRouter · audited without message content.

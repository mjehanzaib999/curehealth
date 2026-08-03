# Medication Adherence Coach

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: patient

## The use case
Taking medication as prescribed is where a lot of care quietly falls apart. The Adherence Coach is a supportive chat that already knows the patient's current prescriptions and helps with timing, routines, reminders, motivation, and coping with mild expected side effects.

## How the AI works
Before each reply, the server loads the patient's own active/sent/dispensed prescriptions and injects them into the system prompt, so the coach speaks to the exact regimen on file. Conversation history is passed through for continuity. Guardrails are strict: the coach never diagnoses, never recommends new medications, and never changes a dose or schedule — those belong to the prescriber — and it routes worrying or red-flag symptoms to the provider or emergency services. This is a demo/education feature, not medical advice.

## What you get
- Short, practical, encouraging replies grounded in the real medication list
- Help with timing, adherence routines, and mild side-effect coping
- A clear hand-off to a clinician when something sounds concerning

## Try it live
Use the **Patient** quick-login button (password `Demo1234!`), open the adherence coach, and try *"I keep forgetting my evening dose — any tips?"*

## Under the hood
`POST /ai/adherence-coach` · grounds on the patient's `MedicationRequest` records (active/sent/dispensed) · Claude Sonnet 4.5 via OpenRouter · audited without message content.

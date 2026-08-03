# Clinical Care-Plan Generator

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: provider

## The use case
Drafting a structured care plan from scratch is time-consuming. This gives a clinician a first-pass, editable draft — problems, goals, interventions, medication considerations, follow-up, and patient education — assembled from the patient's own chart in seconds.

## How the AI works
The endpoint enforces a treatment relationship (the provider must have an appointment with the patient) before pulling the chart: allergies, ongoing conditions, current medications, sex/DOB, and recent encounters. That context is handed to Claude in JSON mode with a prompt that grounds every item in the chart, forbids inventing findings or labs, respects stated allergies, and refuses to prescribe new specific drugs or doses. Every response carries an explicit disclaimer that it is a draft requiring clinician review. This is a demo/education feature and not a substitute for clinical judgment.

## What you get
- Structured, editable sections: problem list, goals, interventions, medication considerations, follow-up, patient education
- Allergy-aware, chart-grounded content
- A built-in "draft — clinician must review" disclaimer

## Try it live
Use the **Provider** quick-login button (`dr.arta@curehealth.dev`, password `Demo1234!`), open a patient you've seen, and generate a care plan.

## Under the hood
`POST /ai/care-plan` · gated on a treatment relationship · grounds on `Patient` (allergies/conditions), `MedicationRequest`, `Appointment` · JSON-mode Claude Sonnet 4.5 via OpenRouter · audited without chart/plan content.

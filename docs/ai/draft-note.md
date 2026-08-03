# Draft Encounter Note

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: provider

## The use case
Clinicians jot shorthand during a visit but still owe a clean encounter note. This tool turns a provider's terse bullet points into a structured, professional S/O/A/P note, cutting documentation time without changing the clinical content.

## How the AI works
The provider must own the appointment being documented. Their shorthand bullets are sent to Claude with a documentation-assistant prompt that structures the note into Subjective, Objective, Assessment, and Plan sections. The prompt is strictly faithfulness-bound: use only the facts present in the bullets, and never invent findings, measurements, diagnoses, or medications that were not stated. The result is a draft the clinician reviews and edits before it becomes the record. This is a demo/education feature, not medical advice.

## What you get
- A clean, professional S/O/A/P encounter note
- Only the facts you supplied — no invented findings
- A fast draft to review, edit, and save

## Try it live
Use the **Provider** quick-login button (`dr.arta@curehealth.dev`, password `Demo1234!`), open one of your appointments, and draft a note from bullets like *"52M, cough 5 days, no fever, chest clear, advised rest and fluids."*

## Under the hood
`POST /ai/draft-note` · scoped to the provider's own appointment · Claude Sonnet 4.6 via OpenRouter · audited without note content.

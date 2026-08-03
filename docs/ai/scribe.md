# Scribe

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: provider

## The use case
An AI medical scribe for the consultation itself. A provider pastes the raw transcript of a visit and gets back a structured encounter note — the same S/O/A/P output as the draft-note tool, but from a full conversation rather than shorthand.

## How the AI works
The provider must own the appointment. The raw consultation transcript is sent to Claude with a documentation prompt that organizes it into Subjective, Objective, Assessment, and Plan sections while ignoring small talk. As with all note tooling here, the model is bound to the transcript's facts — it never invents findings, measurements, diagnoses, or medications — and the output is a draft for the clinician to review and edit. This is a demo/education feature, not medical advice.

## What you get
- A structured S/O/A/P note distilled from a messy transcript
- Small talk filtered out, clinical substance kept
- A review-ready draft, faithful to what was said

## Try it live
Use the **Provider** quick-login button (`dr.arta@curehealth.dev`, password `Demo1234!`), open an appointment, and paste a short mock consultation transcript into the scribe tool.

## Under the hood
`POST /ai/scribe-note` · scoped to the provider's own appointment · Claude Sonnet 4.6 via OpenRouter · audited without transcript content.

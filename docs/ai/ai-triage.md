# AI Triage

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: patient

## The use case
A lightweight, conversational triage helper for patients who just want a quick steer: which specialty should I book, and how soon? It keeps context across turns so a patient can refine their answer without starting over.

## How the AI works
Each turn sends the conversation history plus the new message to Claude in JSON mode. The system prompt lists the platform's real specialties and constrains the model to a navigation-only role — never diagnosing, never naming medications. The response is validated server-side: the recommended specialty must be one that actually exists (else `null`), and urgency must be one of `routine|soon|urgent|emergency` (else `null`). Red-flag symptoms are pushed to `emergency` with advice to call emergency services. This is a demo/education feature, not medical advice.

## What you get
- A conversational reply
- A recommended specialty (validated against real providers, or none)
- An urgency level to guide how soon to book

## Try it live
Use the **Patient** quick-login button (password `Demo1234!`) and open the triage tool. Try *"sore throat and mild fever for two days."*

## Under the hood
`POST /ai/triage` · specialties from distinct `Practitioner.specialty` · JSON-mode Claude Sonnet 4.6 via OpenRouter · enum values coerced to safe defaults · audited without message content.

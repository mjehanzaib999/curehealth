# AI Booking Assistant

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: patient

## The use case
A conversational agent that actually books appointments. Instead of clicking through provider lists and calendars, a patient can say what they need and the assistant finds a provider, checks real free slots, confirms the details, and books — all in chat.

## How the AI works
This is a genuine tool-calling agent. Claude is given three functions — `list_providers`, `get_slots`, and `book_appointment` — and loops (up to 6 rounds) calling them until it can answer. Providers and slots come straight from the database, so the assistant can never invent availability. The system prompt requires it to confirm provider, exact time, and reason conversationally before booking, and it may only book once per turn. The real booking runs through the same fee, video-room, and audit path as manual booking.

## What you get
- A chat reply that grounds every provider and slot in real data
- A confirmed, fully-booked appointment object when you agree to a slot
- The same safeguards as the standard booking flow

## Try it live
Use the **Patient** quick-login button (password `Demo1234!`), open the booking assistant, and try *"I need a cardiology appointment sometime next week."*

## Under the hood
`POST /ai/booking-assistant` · tool-calling loop over `list_providers` / `get_slots` / `book_appointment` · reuses `perform_booking` · Claude Sonnet 4.5 via OpenRouter · audited without message content.

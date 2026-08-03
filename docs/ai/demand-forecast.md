# Demand Forecast

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: pharmacy

## The use case
A pharmacy manager wants a quick read on what's moving so they can stock accordingly. This surfaces the last 30 days of order volume by medication for their pharmacy, with a short AI narrative on top of the real numbers.

## How the AI works
The heavy lifting is a database aggregate, not the model: the server counts non-rejected orders per medication over the trailing 30 days for the calling pharmacy's organization. Those aggregates are handed to Claude, which writes a 2–4 sentence plain-text summary of what's most in demand and any stocking advice that follows directly from the figures. The prompt forbids inventing trends or numbers, and when there are no recent orders a fixed message is returned with no LLM call — so the narrative always tracks real data.

## What you get
- A ranked table of top medications by 30-day order count
- A short, grounded AI narrative with stocking advice
- Numbers straight from the order records — the AI only narrates them

## Try it live
Use the **Pharmacy** quick-login button (`pharma.aria@curehealth.dev`, password `Demo1234!`) and open the Insights / demand-forecast screen.

## Under the hood
`GET /ai/demand-forecast` · aggregates non-rejected `PharmacyOrder` rows (30d) grouped by medication for the pharmacy org · Claude Sonnet 4.5 via OpenRouter narrates the aggregate · audited.

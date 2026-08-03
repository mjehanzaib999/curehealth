# Fraud Scan

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: insurer

## The use case
Fraud rarely announces itself in a single claim — it shows up as patterns across an insurer's book. This scans the organization's claims for anomalies worth a closer human look: outsized amounts, unusually frequent claims per patient, and denied-then-resubmitted behavior.

## How the AI works
The system first computes the signal in code: the organization's median claim amount, a per-patient 90-day claim count, and a per-patient denied-then-resubmitted count (a source record with a denied claim plus another claim for the same source). Those compact per-claim statistics — capped at 50 claims to bound the payload — are handed to Claude in JSON mode, which flags anomalies with a severity and reason. The server only surfaces findings whose `claim_id` actually belongs to the org, and coerces unknown severities to `medium`. Every finding is decision support for a human reviewer, not an accusation or an automated action.

## What you get
- A list of flagged claims, each with a description, severity (`low`/`medium`/`high`), and reason
- Findings grounded in code-computed medians, frequencies, and resubmission patterns
- An empty list when nothing looks anomalous

## Try it live
Use the **Insurer** quick-login button (`insurer.sigal@curehealth.dev`, password `Demo1234!`) and run the fraud scan on the org's claims.

## Under the hood
`POST /ai/fraud-scan` · statistics over the insurer org's `Claim` records (median amount, 90-day frequency, denied-resubmissions), payload capped at 50 · JSON-mode Claude Sonnet 4.6 via OpenRouter · findings filtered to in-org claim IDs · audited.

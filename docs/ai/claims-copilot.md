# Claims Copilot

**Project:** Cure Health · **[Live demo →](https://curehealth.kognio.ai)** · Portal: insurer

## The use case
Adjudicating a claim means checking the same handful of things every time: is the policy active, is the underlying record valid, is it a duplicate, is the amount in range. This copilot runs those checks deterministically and adds an AI recommendation to support — not replace — the human adjudicator.

## How the AI works
The claim is scoped to the calling insurer's organization. The system computes four hard checks in code: policy active, source record valid (appointment `completed` / prescription `dispensed`), no duplicate non-denied claim for the same source, and claim amount within the source amount. Those computed facts and check results are handed to Claude in JSON mode, which returns a recommendation (`approve` / `deny` / `needs_info`) with a rationale grounded in the checks. An invalid recommendation is coerced to `needs_info` — it never fabricates an approval. This is decision support only; the human adjudicator decides.

## What you get
- Four deterministic, code-computed checks with notes
- An AI recommendation: `approve` / `deny` / `needs_info`
- A rationale grounded in the checks — safe-defaulted to `needs_info` on bad output

## Try it live
Use the **Insurer** quick-login button (`insurer.sigal@curehealth.dev`, password `Demo1234!`), open a submitted claim, and run the copilot.

## Under the hood
`POST /ai/claims-copilot` · claim scoped to the insurer org · checks over `Claim`, `InsurancePolicy`, and the source `Appointment`/`MedicationRequest` · JSON-mode Claude Sonnet 4.5 via OpenRouter · audited.

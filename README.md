# Cure Health

**AI-powered digital health platform unifying patients, providers, pharmacies, insurers, and financing.**

### 🔗 [Live demo → curehealth.kognio.ai](https://curehealth.kognio.ai)
Demo login: **`demo@kognio.ai`** / **`Demo1234!`** (admin — sees all six role dashboards)

---

## The problem
Healthcare is fragmented across patients, providers, pharmacies, insurers, and financing — each in its own silo. The result is broken hand-offs, manual claims, and no single record of the care journey.

## What it does
Cure Health connects the whole care loop in one platform, with **six role-scoped dashboards**:

- **Care loop:** appointment booking → visit → **e-prescription** → **pharmacy dispensing**.
- **Insurance:** claim submission and adjudication.
- **Financing:** treatment payment plans.
- **AI clinical support:** symptom **triage** and **clinical-note drafting** via a tool-calling agent.
- **Telehealth:** in-browser **WebRTC video** visits.

46 API endpoints and 24 role-scoped screens across patient, provider, pharmacy, insurer, admin, and call experiences.

## 🤖 AI features — try them live
Powered by Claude (via OpenRouter). Use the **persona quick-login buttons** on the sign-in page to reach each portal. Sixteen AI features span all four portals:

**Patient** — [AI Care Navigator](docs/ai/ai-care-navigator.md) (streaming triage → specialty, red-flags, visit-prep checklist), [AI Triage](docs/ai/ai-triage.md), [AI Booking Assistant](docs/ai/booking-assistant.md) (tool-calling agent that books for you), [Medication Adherence Coach](docs/ai/adherence-coach.md), [Visit Summary](docs/ai/visit-summary.md), and [Claim Helper](docs/ai/claim-helper.md).

**Provider** — [Clinical Care-Plan Generator](docs/ai/care-plan-generator.md) (editable, chart-grounded plan), [Draft Encounter Note](docs/ai/draft-note.md), [Scribe](docs/ai/scribe.md) (transcript → S/O/A/P), and [Drug-Interaction Check](docs/ai/interaction-check.md).

**Pharmacy** — [Dispense Safety Check](docs/ai/dispense-safety-check.md), [Substitution Suggestions](docs/ai/substitution-suggestions.md), [Patient Medication Label](docs/ai/patient-label.md) (EN/SQ), and [Demand Forecast](docs/ai/demand-forecast.md).

**Insurer** — [Claims Copilot](docs/ai/claims-copilot.md) (deterministic checks + recommendation) and [Fraud Scan](docs/ai/fraud-scan.md).

> Look for the **✨ AI** tags in the portal nav and the "💡 how to use" note on each AI screen. Clinical features are demo/education tools — not medical advice.

**→ Full AI use-case docs: [docs/ai/](docs/ai/)**

## Tech
- **Backend:** FastAPI, async SQLAlchemy, Alembic, PostgreSQL, WebSocket signaling
- **Frontend:** Next.js 16 + React 19 + TypeScript
- **AI:** Claude (via OpenRouter) for triage and clinical-note drafting
- Graceful degradation: non-AI features work fully even without an AI key.

## Architecture & deployment
Two-service deployment on **Railway** — a public Next.js frontend and a private FastAPI backend with managed PostgreSQL — the frontend proxying `/api/v1` to the backend at runtime so the browser sees a single origin. Migrations and demo-account seeding run on boot; **auto-deploys on every push.**

---

*Proof-of-concept built by [Muhammad Jehanzaib](https://github.com/mjehanzaib999) / Kognio AI. Source code is private — available on request.*

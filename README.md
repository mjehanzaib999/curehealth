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
Powered by Claude (via OpenRouter). Use the **persona quick-login buttons** on the sign-in page to reach each portal:

- **AI Care Navigator** *(patient)* — describe symptoms and AI triages urgency, flags red-flags, recommends a specialty, and builds a visit-prep checklist — then books for you. Try *"chest tightness and shortness of breath climbing stairs for a week."*
- **Clinical Care-Plan Generator** *(provider)* — drafts an evidence-informed, editable care plan (problems, goals, interventions, follow-up) from a patient's chart.
- Plus **AI Triage** & an **AI Assistant** (patient), **scribe / visit-summary** (provider), **demand forecast** (pharmacy), and **fraud scan** (insurer).

> Look for the **✨ AI** tags in the portal nav and the "💡 how to use" note on each AI screen.

## Tech
- **Backend:** FastAPI, async SQLAlchemy, Alembic, PostgreSQL, WebSocket signaling
- **Frontend:** Next.js 16 + React 19 + TypeScript
- **AI:** Claude (via OpenRouter) for triage and clinical-note drafting
- Graceful degradation: non-AI features work fully even without an AI key.

## Architecture & deployment
Two-service deployment on **Railway** — a public Next.js frontend and a private FastAPI backend with managed PostgreSQL — the frontend proxying `/api/v1` to the backend at runtime so the browser sees a single origin. Migrations and demo-account seeding run on boot; **auto-deploys on every push.**

---

*Proof-of-concept built by [Muhammad Jehanzaib](https://github.com/mjehanzaib999) / Kognio AI. Source code is private — available on request.*

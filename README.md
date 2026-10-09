# ORVEXA

> A RAG-powered knowledge layer for residential buildings — gives residents instant, cited, grounded answers to building-specific bylaws and operational rules, without calling the concierge.

---

## What is ORVEXA?

ORVEXA is a web application (with a future mobile path) that lets residents of a residential building ask plain-English questions about building policies and get back accurate, cited answers grounded in the building's own bylaw documents.

Instead of emailing the concierge and waiting hours, a resident scans a QR code in the lobby, opens the ORVEXA web app, signs in, and asks: *"Can my guest park overnight in visitor stall 3?"* — and gets back the exact bylaw clause, with a citation and document date, in seconds.

Concierge staff get a separate dashboard to upload documents, manage residents, and review escalations.

---

## Who is it for?

| Role | What they do in ORVEXA |
|---|---|
| **Resident** | Asks bylaw and policy questions via chat; gets cited answers |
| **Concierge / Admin** | Uploads documents, reviews escalations, tests queries |
| **Property Manager** | (Phase 2) Cross-building analytics |

---

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | React + TypeScript (Vite) |
| Backend API | Node.js + Express + TypeScript |
| Database | Supabase (Postgres + pgvector) |
| Auth | Supabase Auth (email + password) |
| File storage | Supabase Storage |
| AI — embeddings | OpenAI text-embedding-3-small |
| AI — generation | OpenAI GPT-4o Mini |
| Frontend hosting | Vercel |
| API hosting | Railway |

---

## Project structure

```
orvexa/
├── apps/
│   ├── web/          # React frontend (Vite + TypeScript)
│   └── api/          # Node.js + Express backend
├── docs/
│   ├── prd.md        # Full Product Requirements Document
│   └── architecture.md
├── .env.example      # Template for required environment variables
├── .gitignore
├── CLAUDE.md         # Instructions for Claude Code
└── README.md         # You are here
```

---

## Getting started (local development)

### Prerequisites
- Node.js 20+
- A Supabase project (free at supabase.com)
- An OpenAI API key (platform.openai.com)

### Steps

```bash
# 1. Clone the repo
git clone https://github.com/YOUR-USERNAME/orvexa.git
cd orvexa

# 2. Copy the env template and fill in your keys
cp .env.example .env

# 3. Install dependencies
cd apps/api && npm install
cd ../web && npm install

# 4. Start the API (from apps/api/)
npm run dev

# 5. Start the web app (from apps/web/)
npm run dev
```

The web app runs at `http://localhost:5173`
The API runs at `http://localhost:3000`

---

## Environment variables

See `.env.example` for the full list. The required keys are:

- `SUPABASE_URL` — from your Supabase project settings
- `SUPABASE_SERVICE_ROLE_KEY` — from Supabase (server-side only, never exposed to frontend)
- `OPENAI_API_KEY` — from OpenAI platform

---

## Deployment

| What | Where | Command |
|---|---|---|
| Web app | Vercel | Auto-deploys on push to `main` |
| API | Railway | Auto-deploys on push to `main` |
| Database | Supabase cloud | Managed — no deploy step |

---

## Roadmap

- **Alpha** — one building (JINJU), concierge team testing only
- **Beta** — 3–5 buildings, 15–20 residents per building
- **GA** — full rollout; concierge query volume measurably down ≥ 30%
- **Mobile** — Expo wrapper for iOS/Android App Store submission

---

## License

MIT — see `LICENSE`

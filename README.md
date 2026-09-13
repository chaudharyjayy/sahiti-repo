+ # Sahiti
+ 
+ Sahiti is an AI-powered financial assistant designed for rural entrepreneurs and small-business owners in India. It helps users understand loans, plan returns, assess market demand, generate business reports, and get business-only guidance from an integrated AI assistant — with first-class multilingual support.
+ 
+ **Live demo:** https://sahitigov-ddagdaku.manus.space/
+ 
+ ---
+ 
+ ## Overview
+ 
+ Sahiti is built as a full-stack web application that walks a user through a simple flow:
+ 
+ 1. Phone-based login and OTP verification
+ 2. Short onboarding for location, business type, and loan intent
+ 3. A dashboard with practical business tools and an AI assistant
+ 
+ The product is designed to make financial decisions easier to understand before taking the next step — especially for first-time entrepreneurs who may not have easy access to structured financial guidance.
+ 
+ ---
+ 
+ ## Features
+ 
+ ### Dashboard tools
+ 
+ - **Loan Calculator** — estimate EMI for common business loan scenarios
+ - **Document Guide** — see which documents are typically required, organized by category
+ - **ROI Tracker** — project outcomes over a three-year horizon with a visual chart
+ - **Market Check** — enter competitor and demand details to estimate potential profit
+ - **Report Generator** — preview a business report and export it as a PDF
+ - **AI Assistant** — ask business questions and receive focused, contextual guidance
+ - **Get Loan** — a placeholder entry point for future loan-related workflows
+ 
+ ### AI assistant
+ 
+ The assistant is intentionally scoped to business guidance. It is designed to:
+ 
+ - answer business questions using the current dashboard context
+ - support safe, allowlisted session-only actions with explicit confirmation
+ - provide stop and retry controls during in-flight requests
+ - preserve conversation history and offer a New chat option
+ - decline unrelated, unsafe, or regulated high-stakes requests
+ 
+ It does not execute arbitrary code, write arbitrary files, or make persistent site changes from chat.
+ 
+ ### Multilingual experience
+ 
+ Sahiti is built with a multilingual-first approach for Indian users and supports six languages. Language and readability are treated as core product concerns rather than afterthoughts.
+ 
+ ---
+ 
+ ## Tech stack
+ 
+ | Area | Technology |
+ |---|---|
+ | Frontend | React 19, TypeScript, Vite 7 |
+ | Styling | Tailwind CSS 4, shadcn/ui, Radix UI primitives |
+ | Motion | Framer Motion |
+ | Data & state | TanStack Query, tRPC 11 |
+ | Backend | Node.js, Express |
+ | Database | MySQL with Drizzle ORM |
+ | Authentication | Cookie-based sessions with jose |
+ | AI layer | Server-side model integration with a business-only policy and allowlisted actions |
+ | Testing | Vitest |
+ | Package manager | pnpm |
+ 
+ ---
+ 
+ ## Project structure
+ 
+ ```text
+ .
+ ├── client/
+ │   ├── index.html
+ │   ├── public/
+ │   └── src/
+ │       ├── main.tsx
+ │       ├── App.tsx
+ │       ├── index.css
+ │       ├── components/
+ │       ├── contexts/
+ │       ├── hooks/
+ │       ├── lib/
+ │       └── pages/
+ ├── server/
+ │   ├── index.ts
+ │   ├── _core/
+ │   ├── assistant.ts
+ │   ├── persistence.ts
+ │   ├── routers.ts
+ │   ├── db.ts
+ │   └── *.test.ts
+ ├── shared/
+ │   ├── const.ts
+ │   └── types.ts
+ ├── drizzle/
+ │   ├── schema.ts
+ │   ├── relations.ts
+ │   └── *.sql
+ ├── drizzle.config.ts
+ ├── vite.config.ts
+ ├── vitest.config.ts
+ ├── tsconfig.json
+ ├── package.json
+ └── README.md
+ ```
+ 
+ - `client/` contains the React frontend.
+ - `server/` contains the Express backend, tRPC routers, assistant logic, persistence layer, and tests.
+ - `shared/` contains types and constants used across the stack.
+ - `drizzle/` contains the database schema, relations, and migrations.
+ 
+ ---
+ 
+ ## Getting started
+ 
+ ### Prerequisites
+ 
+ - Node.js
+ - pnpm
+ - A MySQL database if you plan to use the persistence layer
+ 
+ ### Install dependencies
+ 
+ ```bash
+ pnpm install
+ ```
+ 
+ ### Environment setup
+ 
+ Create a `.env` file with the variables required by the server. At minimum, Drizzle requires a database URL:
+ 
+ ```env
+ DATABASE_URL=<mysql-connection-string>
+ ```
+ 
+ Additional server secrets may be required depending on the AI and platform integrations used in `server/_core`.
+ 
+ ### Database
+ 
+ ```bash
+ pnpm run db:push
+ ```
+ 
+ This generates and applies Drizzle migrations. If no database is available, the prototype login and onboarding flow can still be explored, but persistence-backed features will be limited.
+ 
+ ### Development
+ 
+ Run the project from the repository root:
+ 
+ ```bash
+ pnpm run dev
+ ```
+ 
+ The project is configured to run the backend and frontend together through the root dev script. If you prefer separate terminals:
+ 
+ ```bash
+ # Backend
+ pnpm run dev
+ 
+ # Frontend
+ cd client && pnpm dev
+ ```
+ 
+ Then open the local URL shown in your terminal, commonly `http://localhost:5173`.
+ 
+ ### Prototype login
+ 
+ For demo and testing purposes:
+ 
+ - **Phone:** any 10-digit mobile number
+ - **OTP:** any 6 digits
+ 
+ This is a prototype verification flow and is not intended as production authentication.
+ 
+ ### Build
+ 
+ ```bash
+ pnpm run build
+ ```
+ 
+ This builds the client with Vite and bundles the server with esbuild into `dist/`.
+ 
+ ### Start
+ 
+ ```bash
+ pnpm run start
+ ```
+ 
+ ### Type checking
+ 
+ ```bash
+ pnpm run check
+ ```
+ 
+ ### Formatting
+ 
+ ```bash
+ pnpm run format
+ ```
+ 
+ ### Tests
+ 
+ ```bash
+ pnpm run test
+ ```
+ 
+ Vitest is configured to run tests inside `server/` in a Node environment.
+ 
+ ---
+ 
+ ## Architecture notes
+ 
+ ### Frontend
+ 
+ The client is a React application using a Vite-based build, Tailwind for styling, and a shadcn/ui-style component layer built on Radix primitives. Routing and data fetching are handled through the project’s client-side router and TanStack Query/tRPC setup.
+ 
+ ### Backend
+ 
+ The server exposes an Express-based API with tRPC routers for typed communication with the client. It includes authentication helpers, environment handling, storage utilities, and the assistant runtime.
+ 
+ ### Assistant design
+ 
+ The assistant is built around three constraints:
+ 
+ 1. **Business-only scope** — it focuses on entrepreneurial and financial guidance relevant to the current user context.
+ 2. **Safe actions** — only allowlisted, session-local actions are available, and they require explicit confirmation.
+ 3. **Guardrails** — unrelated, unsafe, and regulated high-stakes requests are refused.
+ 
+ ### Database
+ 
+ Drizzle is used for schema definition and migrations. The schema, relations, and generated SQL live in `drizzle/`.
+ 
+ ---
+ 
+ ## Branding guidelines
+ 
+ Sahiti is branded only as **Sahiti** or **By Team Sahiti**.
+ 
+ Do not use:
+ - “Government of India”
+ - any ministry name
+ - the official Star of India State Emblem
+ 
+ The visual direction uses a tricolour-inspired retail palette of navy, saffron, and white, with an accent blue. This is used as a product theme only and should not imply any government affiliation.
+ 
+ If a logo is used, ensure it has adequate contrast, especially on light surfaces. In practice, it should sit on a dark or navy backing where needed.
+ 
+ ---
+ 
+ ## Current status
+ 
+ Sahiti is a hackathon-grade prototype with a working full-stack application, a deployed live URL, multilingual intent, and a business-only AI assistant with stop, retry, and safe-action support.
+ 
+ Some areas are still evolving:
+ 
+ - **Persistence** — schema and procedures exist, but full dashboard and onboarding hydration, plus end-to-end browser persistence verification, are pending resumption of that workstream.
+ - **Landing intro and media resilience** — the welcome sequence and remote media should be reviewed for timing and offline reliability if the demo experience matters.
+ - **Assistant document mapping** — the assistant doc lookup and onboarding business categories should be aligned more closely if document guidance is a major part of the demo.
+ 
+ ---
+ 
+ ## Testing and verification
+ 
+ The most important verification path is the browser flow:
+ 
+ 1. Enter a phone number
+ 2. Verify the OTP screen
+ 3. Complete onboarding
+ 4. Use the dashboard tools
+ 5. Try the AI assistant with business questions, stop, retry, and new chat
+ 
+ For code-level checks, use:
+ 
+ ```bash
+ pnpm run check
+ pnpm run test
+ pnpm run format
+ ```
+ 
+ ---
+ 
+ ## License
+ 
+ MIT. See `package.json` for the license declaration.
+ 
+ ---
+ 
+ ## Team
+ 
+ Built by Team Sahiti for the Smart India Hackathon.
+
Here’s the final README. Copy everything below this line and paste it into GitHub:

// markdown
# Sahiti
 
Sahiti is an AI-powered financial assistant designed for rural entrepreneurs and small-business owners in India. It helps users understand loans, plan returns, assess market demand, generate business reports, and get business-only guidance from an integrated AI assistant — with first-class multilingual support.
 
**Live demo:** https://sahitigov-ddagdaku.manus.space/
 
---
 
## Overview
 
Sahiti is built as a full-stack web application that walks a user through a simple flow:
 
1. Phone-based login and OTP verification
2. Short onboarding for location, business type, and loan intent
3. A dashboard with practical business tools and an AI assistant
 
The product is designed to make financial decisions easier to understand before taking the next step — especially for first-time entrepreneurs who may not have easy access to structured financial guidance.
 
---
 
## Features
 
### Dashboard tools
 
- **Loan Calculator** — estimate EMI for common business loan scenarios
- **Document Guide** — see which documents are typically required, organized by category
- **ROI Tracker** — project outcomes over a three-year horizon with a visual chart
- **Market Check** — enter competitor and demand details to estimate potential profit
- **Report Generator** — preview a business report and export it as a PDF
- **AI Assistant** — ask business questions and receive focused, contextual guidance
- **Get Loan** — a placeholder entry point for future loan-related workflows
 
### AI assistant
 
The assistant is intentionally scoped to business guidance. It is designed to:
 
- answer business questions using the current dashboard context
- support safe, allowlisted session-only actions with explicit confirmation
- provide stop and retry controls during in-flight requests
- preserve conversation history and offer a New chat option
- decline unrelated, unsafe, or regulated high-stakes requests
 
It does not execute arbitrary code, write arbitrary files, or make persistent site changes from chat.
 
### Multilingual experience
 
Sahiti is built with a multilingual-first approach for Indian users and supports six languages. Language and readability are treated as core product concerns rather than afterthoughts.
 
---
 
## Tech stack
 
| Area | Technology |
|---|---|
| Frontend | React 19, TypeScript, Vite 7 |
| Styling | Tailwind CSS 4, shadcn/ui, Radix UI primitives |
| Motion | Framer Motion |
| Data & state | TanStack Query, tRPC 11 |
| Backend | Node.js, Express |
| Database | MySQL with Drizzle ORM |
| Authentication | Cookie-based sessions with jose |
| AI layer | Server-side model integration with a business-only policy and allowlisted actions |
| Testing | Vitest |
| Package manager | pnpm |
 
---
 
## Project structure
 
```text
.
├── client/
│   ├── index.html
│   ├── public/
│   └── src/
│       ├── main.tsx
│       ├── App.tsx
│       ├── index.css
│       ├── components/
│       ├── contexts/
│       ├── hooks/
│       ├── lib/
│       └── pages/
├── server/
│   ├── index.ts
│   ├── _core/
│   ├── assistant.ts
│   ├── persistence.ts
│   ├── routers.ts
│   ├── db.ts
│   └── *.test.ts
├── shared/
│   ├── const.ts
│   └── types.ts
├── drizzle/
│   ├── schema.ts
│   ├── relations.ts
│   └── *.sql
├── drizzle.config.ts
├── vite.config.ts
├── vitest.config.ts
├── tsconfig.json
├── package.json
└── README.md

-  client/  contains the React frontend.
-  server/  contains the Express backend, tRPC routers, assistant logic, persistence layer, and tests.
-  shared/  contains types and constants used across the stack.
-  drizzle/  contains the database schema, relations, and migrations.

──────────────────────────────────────────────────────────────────

Getting started

Prerequisites

- Node.js
- pnpm
- A MySQL database if you plan to use the persistence layer

Install dependencies

// bash
pnpm install

Environment setup

Create a  .env  file with the variables required by the server. At minimum, Drizzle requires a database URL:

// env
DATABASE_URL=<mysql-connection-string>

Additional server secrets may be required depending on the AI and platform integrations used in  server/_core .

Database

// bash
pnpm run db:push

This generates and applies Drizzle migrations. If no database is available, the prototype login and onboarding flow can still be explored, but persistence-backed features will be limited.

Development

Run the project from the repository root:

// bash
pnpm run dev

The project is configured to run the backend and frontend together through the root dev script. If you prefer separate terminals:

// bash
# Backend
pnpm run dev
 
# Frontend
cd client && pnpm dev

Then open the local URL shown in your terminal, commonly  http://localhost:5173 .

Prototype login

For demo and testing purposes:
- Phone: any 10-digit mobile number
- OTP: any 6 digits

This is a prototype verification flow and is not intended as production authentication.

Build

// bash
pnpm run build

This builds the client with Vite and bundles the server with esbuild into  dist/ .

Start

// bash
pnpm run start

Type checking

// bash
pnpm run check

Formatting

// bash
pnpm run format

Tests

// bash
pnpm run test

Vitest is configured to run tests inside  server/  in a Node environment.

──────────────────────────────────────────────────────────────────

Architecture notes

Frontend

The client is a React application using a Vite-based build, Tailwind for styling, and a shadcn/ui-style component layer built on Radix primitives. Routing and data fetching are handled through the project’s client-side router and TanStack Query/tRPC setup.

Backend

The server exposes an Express-based API with tRPC routers for typed communication with the client. It includes authentication helpers, environment handling, storage utilities, and the assistant runtime.

Assistant design

The assistant is built around three constraints:
1. Business-only scope — it focuses on entrepreneurial and financial guidance relevant to the current user context.
2. Safe actions — only allowlisted, session-local actions are available, and they require explicit confirmation.
3. Guardrails — unrelated, unsafe, and regulated high-stakes requests are refused.

Database

Drizzle is used for schema definition and migrations. The schema, relations, and generated SQL live in  drizzle/ .

──────────────────────────────────────────────────────────────────

Branding guidelines

Sahiti is branded only as Sahiti or By Team Sahiti.

Do not use:
- “Government of India”
- any ministry name
- the official Star of India State Emblem

The visual direction uses a tricolour-inspired retail palette of navy, saffron, and white, with an accent blue. This is used as a product theme only and should not imply any government affiliation.

If a logo is used, ensure it has adequate contrast, especially on light surfaces. In practice, it should sit on a dark or navy backing where needed.

──────────────────────────────────────────────────────────────────

Current status

Sahiti is a hackathon-grade prototype with a working full-stack application, a deployed live URL, multilingual intent, and a business-only AI assistant with stop, retry, and safe-action support.

Some areas are still evolving:
- Persistence — schema and procedures exist, but full dashboard and onboarding hydration, plus end-to-end browser persistence verification, are pending resumption of that workstream.
- Landing intro and media resilience — the welcome sequence and remote media should be reviewed for timing and offline reliability if the demo experience matters.
- Assistant document mapping — the assistant doc lookup and onboarding business categories should be aligned more closely if document guidance is a major part of the demo.

──────────────────────────────────────────────────────────────────

Testing and verification

The most important verification path is the browser flow:
1. Enter a phone number
2. Verify the OTP screen
3. Complete onboarding
4. Use the dashboard tools
5. Try the AI assistant with business questions, stop, retry, and new chat

For code-level checks, use:

// bash
pnpm run check
pnpm run test
pnpm run format

──────────────────────────────────────────────────────────────────

License

MIT. See  package.json  for the license declaration.

──────────────────────────────────────────────────────────────────

Team

Built by Team Sahiti for the Smart India Hackathon.

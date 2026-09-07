# Sayyad — Arabic-first Home Services Marketplace for Libya

Sayyad is a mobile-first marketplace prototype for finding and booking local tradespeople in Libya.

I built it after thinking about a very ordinary problem: finding a reliable electrician, plumber or technician can depend heavily on personal recommendations and informal contacts. Sayyad explored whether that experience could be made more structured through an Arabic-first marketplace.

## What the app supports

- Arabic-first interface with English switching and RTL/LTR support
- customer and provider accounts
- Supabase email/password authentication
- provider discovery, profiles, ratings and verification context
- service/category/district/availability filters
- booking requests
- provider onboarding and profile management
- provider application / admin review flows
- offers and accept/reject flows
- job progression and cancellation states
- completed-job reviews
- customer/provider/admin routes
- offline-first local storage and queued sync
- PWA installation and service-worker support

## Backend and data architecture

Sayyad combines a local-first browser data model with Supabase/PostgreSQL:

```text
React UI
   |
Dexie / IndexedDB local model
   |
Transactional outbox
   |
Supabase Edge Function
   |
PostgreSQL + RLS / server functions
```

The project includes SQL migrations, row-level security rules, business functions and an authenticated Edge Function used as the sync boundary.

## What I personally tested

I configured the Supabase version myself and successfully:

- created a real account through the application
- authenticated against Supabase
- created a booking that persisted to the backend

That does **not** mean every production workflow was fully deployed or validated. The repository inspection did not verify a full real-world marketplace deployment, recruited providers, payment processing or every multi-account/RLS path.

## Main technologies

TypeScript · React 19 · Vite · React Router · Tailwind CSS · Supabase · PostgreSQL · Deno Edge Functions · Dexie / IndexedDB · Zustand · i18next · Workbox · Vitest

## Testing

The cleaned project was validated with:

- TypeScript build checks
- linting (with 3 existing Fast Refresh warnings)
- **160 passing tests across 49 test files**
- successful production PWA build

These tests provide useful engineering evidence, but they are not presented as proof that the entire marketplace was production-deployed.

## Product scope

The intended product was an Arabic-first household-services marketplace, initially focused around trades such as AC technicians, electricians and plumbers in Benghazi.

The app records payment preferences but does not implement payment processing, escrow or settlement. Some planned production features — such as provider access to customer photo attachments, stronger identity-document flows and full push/SMS/WhatsApp operations — remain incomplete.

See [`PROJECT_REPORT.md`](PROJECT_REPORT.md) for the detailed preserved-source report.

## Run locally

```powershell
npm ci
npm run dev -- --host 127.0.0.1
```

For backend-backed account operations, copy the safe example environment file and provide your own Supabase browser configuration:

```powershell
Copy-Item .env.example .env.local
npm run dev -- --host 127.0.0.1
```

Never place a Supabase service-role key in a `VITE_*` variable.

## AI-assisted development

I built Sayyad with heavy AI assistance using **Antigravity, Claude Opus 4.6 and GPT Sol** as coding collaborators.

I directed the product idea, requirements, user flows and iterations, tested the application, configured the backend and debugged the project while the AI tools generated and modified substantial portions of the code.

I include this explicitly because I want the repository to represent what I actually did rather than imply that the entire codebase was written manually.

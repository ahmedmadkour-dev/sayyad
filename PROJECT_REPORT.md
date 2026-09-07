# Sayyad — Project Report

## Purpose

Sayyad was an Arabic-first home-services marketplace prototype for Libya. I built it around a common problem: finding a reliable electrician, plumber, AC technician or other tradesperson can depend heavily on informal recommendations and personal contacts.

The project explored whether that process could be made more structured through a mobile-first marketplace.

## Technical stack

- TypeScript / TSX
- React 19
- Vite + React Router
- Tailwind CSS
- Supabase authentication/database/storage integration
- PostgreSQL + row-level security/functions
- Deno Edge Function
- Dexie / IndexedDB
- Zustand
- i18next with Libyan Arabic + English
- Workbox / PWA tooling
- Vitest

## Architecture

The app used a local-first browser model with queued synchronization:

```text
React UI
   |
Dexie / IndexedDB
   |
Transactional outbox
   |
Supabase Edge Function
   |
PostgreSQL + RLS / server functions
```

## Implemented functionality

- Arabic-first UI with RTL support and English switching
- account registration/sign-in
- provider discovery and filtering
- customer booking requests
- provider onboarding/profile management
- provider application/admin review flows
- ratings/reviews
- offers and accept/reject states
- booking/job lifecycle and cancellation states
- offline/local persistence and queued sync
- PWA installation/service worker support
- customer/provider/admin route structure

## What I personally verified

I configured the Supabase-backed version myself and successfully:

- created a real account through the app
- authenticated against Supabase
- created a booking that persisted to the actual backend

This does not mean the entire marketplace was production-deployed or operational with real providers/customers.

## Validation of the preserved copy

During the portfolio export:

- TypeScript checks passed
- linting passed with 3 existing Fast Refresh warnings
- **160 tests across 49 files passed**
- the production PWA build succeeded

## Known limitations

- no real payment collection, escrow or settlement
- no evidence of a full real-world marketplace launch or recruited provider network
- some planned provider-photo/document workflows remained incomplete
- full multi-account production RLS testing and live operational processes were not independently re-validated during the export

## Security cleanup

Project-specific `.env` files and Supabase browser configuration were excluded from the portfolio export. No embedded service-role/admin credential was identified in the cleaned source.

## AI-assisted development

I built Sayyad with heavy AI assistance using Antigravity, Claude Opus 4.6 and GPT Sol. I directed the product idea, requirements, user flows and iterations, configured/tested the backend and debugged the system while AI tools generated and modified substantial portions of the implementation.

I include this explicitly so the project reflects what I actually did rather than implying the whole codebase was written manually.

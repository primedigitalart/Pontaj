# Pontaj — Driver Time & Mileage Tracking

A multi-tenant SaaS web application for tracking work shifts and mileage for drivers in transport companies. Built for **AS Transport** as a proof-of-concept product by [PrimeDigital.Art](https://primedigital.art).

🔗 **Live demo:** [pontaj-astransport.netlify.app](https://pontaj-astransport.netlify.app)

---

## Overview

Pontaj lets transport companies record driver shifts, automatically calculate worked hours and kilometers driven, and generate exportable reports per driver or for the whole company. Each company manages its own drivers, customizes its branding, and keeps its data fully isolated from other tenants.

## Features

- **Shift tracking** — log work shifts with automatic calculation of hours and kilometers
- **Multi-tenant architecture** — each company sees only its own data (enforced via Supabase Row Level Security)
- **Three access levels** — platform admin, company admin, and driver, each with a tailored view
- **Reports & export** — generate per-driver and full-company reports, export to CSV, and print-ready PDF output
- **Audit trail** — shift modifications are tracked in a dedicated change-log table
- **Per-company branding** — each company can set its own name and visual identity
- **Multilingual UI** — available in Romanian, German, and English

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 (via CDN), Tailwind CSS, Babel standalone |
| Backend | Supabase — Authentication + PostgreSQL with Row Level Security |
| Deployment | Netlify |

The application is built as a single self-contained HTML file, with React components transpiled in the browser via Babel — no build step required.

## Data Model

The Supabase backend uses the following core tables:

- `companies` — registered transport companies (tenants)
- `drivers` — drivers belonging to each company
- `shifts` — individual work shifts with time and mileage data
- `profiles` — user accounts and role assignments
- `pontaje_modificari` — audit log of shift modifications

## Roles

- **Platform admin** — oversees all companies on the platform
- **Company admin** — manages drivers, shifts, reports, and branding for their company
- **Driver** — records and reviews their own shifts

## Security

Authentication is handled by Supabase Auth (email + password). Data isolation between companies relies on PostgreSQL Row Level Security policies, so each tenant can only access its own records. The client uses a Supabase publishable key, which is safe to expose in frontend code.

---

## About

Developed by **Eugen Scutariu** / [PrimeDigital.Art](https://primedigital.art) — a digital agency serving Romanian-speaking entrepreneurs abroad.

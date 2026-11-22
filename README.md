# Smart Family Service Management System (SFSMS)

A centralized platform that helps families **find, book, pay for and track services**, from household repairs to personal care, all in one place.

Its key feature is **remote booking with money traceability**: a family member living abroad can book and pay for a service for a relative back home and see exactly where the money went.

## Problem

Families often struggle to:
- find reliable service providers
- arrange and keep track of appointments
- follow the progress of ongoing jobs
- keep a record of what was done, when, and at what cost
- know how money sent from abroad was actually spent: relatives abroad send money for a specific need but get no proof it was used for that service

The information ends up spread across phone calls, notes and memory.

## Solution

SFSMS gives each family a shared space where members can request services, book providers, follow each job from request to completion, record expenses and rate providers. Over time this builds a complete **household service history**.

## Key Feature: Remote Booking with Money Traceability

When a relative abroad pays for a service through SFSMS, the money goes to the **service provider**, not to the relative, and is released only once the service is confirmed as done.

**Example:** Agape lives in Canada; her sister Ruth lives in Cameroon. Ruth asks Agape for money to do her hair.

1. **Agape** books a hair salon near Ruth in the app, for Ruth.
2. **Agape** pays in the app. The payment is **held** by the platform, not sent to Ruth.
3. **The salon** confirms the appointment with Ruth.
4. **Ruth** gets her hair done.
5. **The salon** marks the job as completed and uploads a proof (photo or receipt).
6. **Ruth** confirms in the app that the service was delivered.
7. **The platform** releases the payment to the salon. Agape sees the full timeline.

**Implementation approach**
- **Escrow model:** each payment is linked to one service request, with status `Paid → Held → Released` (or `Refunded` if cancelled)
- **Payment gateway in sandbox/test mode** (card or Mobile Money); no real money during the course project
- **Audit trail:** every status change is logged with date, time and author
- **Notifications** to the sponsor at each step

## Users & Roles

| Role | What they can do |
|---|---|
| **Sponsor** (family member abroad) | Books and pays for a service for a relative, tracks the payment and the job until completion |
| **Beneficiary** | Receives the service, confirms it was delivered |
| **Family Admin** | Creates the family space, invites members, approves requests, views all expenses |
| **Family Member** | Submits service requests, books appointments, tracks progress, leaves reviews |
| **Service Provider** | Manages a profile and services, accepts or declines requests, updates job status, uploads completion proof, receives payment |
| **Platform Admin** | Manages service categories, verifies providers, moderates reviews, handles disputes and refunds |

## Core Features

1. **Authentication & family accounts**: register, log in, create or join a family, role-based access
2. **Service catalog**: categories (plumbing, electrical, cleaning, laundry, gardening, vehicle, hairdressing and beauty) and searchable provider profiles
3. **Service requests**: describe the need, add photos, set urgency and preferred date
4. **Scheduling**: book a time slot from provider availability, reschedule or cancel
5. **Progress tracking**: status workflow
   `Pending → Accepted → Scheduled → In Progress → Completed` (or `Cancelled`)
6. **Remote booking & payment traceability**: book and pay for a relative's service; payment held in escrow and released after completion proof and beneficiary confirmation
7. **Expense tracking**: cost per job, monthly totals per category, simple charts
8. **Reviews & ratings**: rate and comment on providers after completed jobs
9. **Service history**: searchable log of every service per household
10. **Notifications**: email or in-app alerts on status changes, payments and upcoming appointments

## Tech Stack (proposed)

| Layer | Technology |
|---|---|
| Backend | Django + Django REST Framework |
| Frontend | React (Vite) or Next.js |
| Database | PostgreSQL |
| Auth | JWT (SimpleJWT) |
| Payments | Payment gateway in sandbox / test mode (card or Mobile Money) |
| Containers | Docker, Docker Compose |
| CI/CD | GitHub Actions |
| Deployment | AWS EC2 or Render |
| Monitoring | Prometheus + Grafana (optional) |

## DevOps Practices

- **Branching**: GitHub Flow: `main` is always deployable; short-lived `feature/<issue>-<name>` and `fix/<issue>-<name>` branches
- **Pull requests**: 1 approval + green CI required before merging into `main` (protected branch, CODEOWNERS)
- **Planning**: user stories with Given/When/Then acceptance criteria, milestones, GitHub Projects Kanban board
- **Releases**: Semantic Versioning tags (`v0.1.0`, `v0.2.0`, ...)
- **Conventional commits**: `feat:`, `fix:`, `docs:`, `test:`, `ci:`
- **CI pipeline** (GitHub Actions): ruff + black → pytest (coverage ≥ 80%) → bandit + pip-audit on every PR
- **Makefile**: `make install`, `make run`, `make test`, `make lint`, `make format`
- **Containers** (Unit 5): Dockerfile + docker-compose
- **CD pipeline** (Unit 6): automatic deploy to staging, then production from `main`
- **Infrastructure as code**: Docker Compose, plus Terraform if time allows
- **Issue tracking**: GitHub Issues + Projects board (Kanban)

## Project Structure (planned)

```
sfsms/
├── backend/            # Django REST API
├── frontend/           # React / Next.js app
├── docker-compose.yml
├── .github/workflows/  # CI/CD pipelines
└── docs/               # diagrams, reports
```

## Getting Started

_Coming soon: setup instructions once the first version of the stack is in place._

## Team

| Name | Role |
|---|---|
| CJay | Backend (auth, families, roles) |
| Duplex Landry | Backend (requests, scheduling, expenses) |
| Sheva King | Frontend (family dashboard) |
| Daniella Sheryl | Frontend (provider dashboard, reviews) |

## License

Academic project, IUC Cameroon.

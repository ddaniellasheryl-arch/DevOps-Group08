# Smart Family Service Management System (SFSMS)

A centralized web platform that helps families **find, request, schedule, track and pay for household services**, including plumbing, electrical repairs, cleaning, laundry, gardening and vehicle maintenance, from one place.

## Problem

Families often struggle to:
- find reliable service providers
- arrange and keep track of appointments
- follow the progress of ongoing jobs
- keep a record of what was done, when, and at what cost

The information ends up spread across phone calls, notes and memory.

## Solution

SFSMS gives each family a shared space where members can request services, book providers, follow each job from request to completion, record expenses and rate providers. Over time this builds a complete **household service history**.

## Users & Roles

| Role | What they can do |
|---|---|
| **Family Admin** | Creates the family space, invites members, approves requests, views all expenses |
| **Family Member** | Submits service requests, books appointments, tracks progress, leaves reviews |
| **Service Provider** | Manages a profile and services, accepts or declines requests, updates job status, sets prices |
| **Platform Admin** | Manages service categories, verifies providers, moderates reviews |

## Core Features

1. **Authentication & family accounts**: register, log in, create or join a family, role-based access
2. **Service catalog**: categories (plumbing, electrical, cleaning, laundry, gardening, vehicle) and searchable provider profiles
3. **Service requests**: describe the need, add photos, set urgency and preferred date
4. **Scheduling**: book a time slot from provider availability, reschedule or cancel
5. **Progress tracking**: status workflow
   `Pending → Accepted → Scheduled → In Progress → Completed` (or `Cancelled`)
6. **Expense tracking**: cost per job, monthly totals per category, simple charts
7. **Reviews & ratings**: rate and comment on providers after completed jobs
8. **Service history**: searchable log of every service per household
9. **Notifications**: email or in-app alerts on status changes and upcoming appointments

## Tech Stack (proposed)

| Layer | Technology |
|---|---|
| Backend | Django + Django REST Framework |
| Frontend | React (Vite) or Next.js |
| Database | PostgreSQL |
| Auth | JWT (SimpleJWT) |
| Containers | Docker, Docker Compose |
| CI/CD | GitHub Actions |
| Deployment | AWS EC2 or Render |
| Monitoring | Prometheus + Grafana (optional) |

## DevOps Practices

- **Branching**: `main` (production), `develop` (integration), `feature/*`, `fix/*`
- **Pull requests**: required review before merging into `develop` or `main`
- **Conventional commits**: `feat:`, `fix:`, `docs:`, `test:`, `ci:`
- **CI pipeline**: lint → unit tests → build Docker images on every PR
- **CD pipeline**: automatic deploy to staging from `develop` and to production from `main`
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


## Team

NameRoleDuplex LandryBackend (requests, scheduling, expenses)Daniella SherylFrontend (provider dashboard, reviews)Sheva King
Frontend (family dashboard)CJayBackend (auth, families, roles)


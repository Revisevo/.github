# Revisevo

> SaaS platform for automotive workshop management — built for the Portuguese market.

Revisevo connects workshops with their clients through a platform that digitalises workshop operations end-to-end. Workshops manage their business more efficiently. Clients always know what's happening with their vehicle — without having to call.

---

## The Problem

Most automotive workshops in Portugal still rely on paper, spreadsheets and phone calls to manage their day-to-day operations. Clients drop off their vehicle and hear nothing until it's ready — or until they call to ask. There is no visibility, no traceability, and no easy way to manage a growing workshop.

Revisevo solves this from both sides of the counter.

---

## What We're Building

**For workshops**
- Full service order lifecycle management with real-time progress tracking
- Team and speciality management with smart assignment suggestions
- Parts inventory with automatic restock alerts
- Financial reporting — revenue, costs, margins and analytics by period
- Digital quotes with client signature before work begins
- Excel import to migrate data from existing systems with zero friction

**For clients**
- Online bookings without phone calls
- Real-time service status — in queue, on the lift, awaiting parts, ready
- Full vehicle history across all services and workshops
- Maintenance reminders at the right time
- Parts approval directly from the app

**For mechanics**
- Mobile-first app designed for gloves-on use
- Large touch targets, high contrast, favourites at the top
- Update service status, log parts used and add notes in two taps
- Basic offline mode — syncs when connection is restored

---

## Architecture

Revisevo is built as a microservices platform on AWS, designed for multi-tenancy from day one. Each workshop is fully isolated at the data layer.

```
revisevo-api-gateway        → Single entry point, JWT validation, rate limiting
revisevo-auth-service       → Authentication, RBAC, refresh tokens
revisevo-company-service    → Workshops, teams and staff management
revisevo-service-orders     → Service lifecycle and progress tracking
revisevo-booking-service    → Scheduling, quotes and digital signatures
revisevo-inventory-service  → Parts catalogue and stock management
revisevo-vehicle-service    → Client vehicles, history and maintenance alerts
revisevo-catalog-service    → Public service catalogue per workshop
revisevo-finance-service    → Revenue, costs and business analytics
revisevo-notification-service → Push, SMS and email via async queue
revisevo-import-service     → Excel import and legacy data migration
revisevo-web                → React + TypeScript frontend
revisevo-mobile             → React Native mechanic app
revisevo-infra              → Docker, Terraform AWS, GitHub Actions
```

---

## Stack

| Layer | Technology |
|---|---|
| Backend | Java 21 · Spring Boot 3.x |
| Frontend | React 18 · TypeScript · Vite |
| Mobile | React Native |
| Primary DB | PostgreSQL 16 — schema-per-tenant multi-tenancy |
| Document DB | MongoDB — service logs, events, notifications |
| Cache / Queues | Redis — sessions, rate limiting, async queues |
| Infrastructure | Docker · Terraform · AWS ECS Fargate |
| CI/CD | GitHub Actions · Amazon ECR |
| API Docs | OpenAPI 3 / Swagger |

---

## Security

Security is a first-class concern at every layer of the platform.

- JWT with short-lived access tokens and HttpOnly refresh tokens
- Granular RBAC — Super Admin · Company Admin · Manager · Mechanic · Client
- Tenant isolation enforced on every request
- Immutable audit log for all actions
- Rate limiting per IP and API key via Redis
- GDPR compliant — explicit consent, right to erasure, data portability

---

## Repositories

| Repository | Description |
|---|---|
| [revisevo](https://github.com/Revisevo/revisevo) | Main repo — architecture docs and docker-compose |
| [revisevo-auth-service](https://github.com/Revisevo/revisevo-auth-service) | Authentication and authorization |
| [revisevo-api-gateway](https://github.com/Revisevo/revisevo-api-gateway) | API Gateway — routing, JWT validation, rate limiting |
| [revisevo-company-service](https://github.com/Revisevo/revisevo-company-service) | Company and team management |
| [revisevo-service-orders](https://github.com/Revisevo/revisevo-service-orders) | Service order lifecycle and progress tracking |
| [revisevo-booking-service](https://github.com/Revisevo/revisevo-booking-service) | Bookings, scheduling and digital quotes |
| [revisevo-inventory-service](https://github.com/Revisevo/revisevo-inventory-service) | Parts inventory and stock control |
| [revisevo-vehicle-service](https://github.com/Revisevo/revisevo-vehicle-service) | Client vehicles, history and maintenance alerts |
| [revisevo-catalog-service](https://github.com/Revisevo/revisevo-catalog-service) | Public service catalogue per workshop |
| [revisevo-finance-service](https://github.com/Revisevo/revisevo-finance-service) | Finance, analytics and business reporting |
| [revisevo-notification-service](https://github.com/Revisevo/revisevo-notification-service) | Push, SMS and email notifications |
| [revisevo-import-service](https://github.com/Revisevo/revisevo-import-service) | Data migration and Excel import |
| [revisevo-web](https://github.com/Revisevo/revisevo-web) | React frontend — backoffice, hub and client portal |
| [revisevo-mobile](https://github.com/Revisevo/revisevo-mobile) | React Native mechanic app |
| [revisevo-infra](https://github.com/Revisevo/revisevo-infra) | Infrastructure — Docker, Terraform and CI/CD |

---

*Building in public · Portugal 🇵🇹*

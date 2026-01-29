# CustomCADs — the modern platform for 3D Models

A web platform built with a **.NET Modular Monolith** backend and a **TanStack-inspired React** frontend.

---

## Overview

This system delivers a scalable, maintainable architecture powered by **Clean Architecture**, **DDD**, and strict **Command/Query segregation**. It uses **asynchronous communication** where appropriate, and relies on a modern mix of cloud services and SDKs across its lifecycle.

---

## Backend
[Visualization](https://www.tldraw.com/p/zl3h-eJIdeK3e-f9SAYmE?d=v-1359.-236.3182.1926.page)

<img width="2256" height="1504" alt="image" src="https://github.com/user-attachments/assets/7d50b829-81b6-4387-932b-29d2a56b8932" />

* Codebase:

  * Clean Architecture, Domain-Driven Design
  * State Pattern, Fluent Pattern, Static Factory Method Pattern
  * CQRS at both the Application and Persistence level
  * Synchronous (Mediator) & Asynchronous (Bus) messaging
* Database:

  * **Postgres** (schema-per-module)
  * Accessed through **EF Core** behind abstractions
* Integrations:

  * **Speedy** SDK for third-party delivery
  * **Stripe** webhooks for payments
  * **Cloudflare R2** with presigned URLs for file storage
  * **SignalR** for real-time updates
  * **ECB exchange rates** cache, refreshed via background job
  * **Quartz** cron jobs for scheduled tasks

---

## Frontend
[Visualization](https://www.tldraw.com/p/FmIZo7x3hBGAQH84Dg_eE?d=v-1608.-505.2779.2202.RKL38VRmVGk9ofLDudtZZ)

<img width="2256" height="1504" alt="image" src="https://github.com/user-attachments/assets/b76d9ffc-92cf-4b18-ab22-bff9db278b3f" />

* Implemented with **React**:
  * Mix of **custom components** and **Shadcn/UI**
  * Responsive Design and Mobile-First by default
  * Instant theme switching at scale

* Heavily relying on the **TanStack** ecosystem:
  * **TanStack Start** for SSR & hydration/dehydration
  * **TanStack Query** for query caching
  * **TanStack Virtualizer** for infinite scroll
  * **TanStack Store** for local data storage
  * **TanStack Form** for headless form management
  * **TanStack Pacer** for headless throttling
  * **TanStack DevTools** with custom plugins

* Custom UI mixed with **Shadcn/UI**:
  * Responsive by default
  * Instant theme switching at scale
  * Readable, reusable & maintainable
  * Easily configurable & customizable

* Backend API communication is handled by the **CustomCADs React SDK**.

---

## Hosting & Infrastructure Journey

The platform has gone through several hosting phases:

1. **Azure** – initial monolith deployment (MVC & DB).
2. **GCP + Render** – DB in GCP; Backend as a Render Web Service (Docker); Frontend as a Render static site (Vanilla React).
3. **AWS** – full migration:

   * RDS for data storage (DB), S3 for file storage (Buckets)
   * Backend in Elastic Beanstalk (via ECR images), proxied through CloudFront, with SSH configured
   * Frontend in Amplify, later simplified to S3 + CloudFront
   * Introduced multiple backend environments (prod, staging)
4. Adoption of **Terraform** for full IaC:

   * While migrating to AWS, solidified infrastructure hosting via **Terraform**
   * Improved structure and organization of configs
   * Extracted Terraform configs to their own self-managed repo
5. Continued shift to specialized services:

   * Storage, CDN & Frontend migrated to **Cloudflare**
   * Docker Images to **Dockerhub**, Backend + DB moved to **paid Render**

---

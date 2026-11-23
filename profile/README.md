<div align="center">

![Sany3y Banner](../sany3y_banner4.png)

# Sany3y (صنـايعـي)

**A full-stack, decoupled service marketplace connecting clients with verified technicians and maintenance shops across Egypt.**

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet)](https://dotnet.microsoft.com/)
[![Next.js](https://img.shields.io/badge/Next.js-15-000000?style=flat-square&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-YOLOv8_OCR-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![SQL Server](https://img.shields.io/badge/Database-SQL_Server-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/sql-server)
[![License](https://img.shields.io/badge/License-GPL--3.0-2ea44f?style=flat-square)](https://www.gnu.org/licenses/gpl-3.0)

[About](#about-sany3y) • [Ecosystem](#platform-ecosystem) • [Architecture](#system-architecture) • [Capabilities](#platform-capabilities) • [Tech Stack](#technology-stack) • [Team](#core-team)

</div>

---

## About Sany3y

**Sany3y (صنـايعـي)** is a modern service and maintenance marketplace engineered to bring trust, structure, and real-time transparency to home and commercial maintenance across Egypt.

Our platform bridges the gap between **clients** seeking reliable technical services, **independent technicians** managing schedules and bookings, and **local maintenance & hardware shops** establishing a verified digital storefront across Egyptian governorates and cities.

### Engineering Highlights

- **Decoupled Multi-Service Architecture** — Clean separation between the Next.js 15 web client, ASP.NET Core 8 REST & SignalR backend, Entity Framework Core persistence layer, and Python computer vision microservice.
- **AI-Driven Identity Verification** — Automated two-stage **Ultralytics YOLOv8** OCR pipeline (`detect_id_card.pt` & `detect_arabic_numbers.pt`) that extracts and validates 14-digit Egyptian National ID numbers during onboarding.
- **Real-Time Messaging & Live Presence** — JWT-authenticated SignalR WebSocket hubs (`/chatHub` and `/userStatusHub`) powering instant private chat, typing indicators, read receipts, and online/offline availability.
- **Enterprise Identity & Access Control** — ASP.NET Core Identity with stateless JWT Bearer authentication, Google OAuth integration, email confirmation, account lockout policies, and role isolation (`Admin`, `Technician`, `Client`, and `IsShop` entities).
- **Integrated Payments & Arabic RTL Reporting** — Stripe Checkout & Webhook settlement in Egyptian Pounds (EGP) alongside Cash-on-Service, paired with Chart.js telemetry, iTextSharp Arabic RTL PDF reports, and UTF-8 CSV exports.

---

## Platform Ecosystem

| Component | Repository / Module | Responsibility | Stack |
| :--- | :--- | :--- | :--- |
| **Web Client** | [`Sany3y/frontend`](https://github.com/Sany3y/frontend) | Customer, technician, shop, and admin portals with RTL UI and real-time chat | Next.js 15, React 19, TypeScript 5.7 |
| **Computer Vision Service** | [`Sany3y/ai`](https://github.com/Sany3y/ai) | FastAPI inference server executing two-stage YOLOv8 Egyptian National ID OCR | Python 3.10+, FastAPI, YOLOv8, PyTorch |
| **Backend API & Data Layer** | `Sany3y.API` & `Sany3y.Infrastructure` | REST APIs, SignalR hubs, Identity/RBAC, Stripe payments, SMTP, PDF/CSV exports, and EF Core persistence | .NET 8, ASP.NET Core, EF Core 8, SQL Server |

---

## System Architecture

```mermaid
flowchart LR
    Client["Next.js 15 Client<br/>(Sany3y/frontend)"] -->|REST + JWT| API["ASP.NET Core 8 API<br/>(Sany3y.API)"]
    Client <-->|WebSockets / SignalR| Hubs["ChatHub & UserStatusHub"]
    API --- Hubs
    API -->|EF Core 8| Infra["Persistence Layer<br/>(Sany3y.Infrastructure)"]
    Infra --> DB[("Microsoft SQL Server")]
    API -->|ID Verification| AI["FastAPI + YOLOv8 OCR<br/>(Sany3y/ai)"]
    API -->|Payments & Auth| Ext["Stripe (EGP) / Google OAuth / SMTP"]
```

---

## Platform Capabilities

| Role | Key Capabilities |
| :--- | :--- |
| **Clients** | Search technicians and shops by category, governorate, city, price, and rating with Arabic character normalization; inspect real-time availability; book slots with Cash or Stripe online payment; chat in real time; leave verified reviews. |
| **Technicians** | Complete National ID OCR-verified onboarding; configure specialty category, inspection fee, experience, and bio; manage open/booked schedule slots; accept or reject requests and track earnings. |
| **Maintenance Shops** | Dedicated commercial onboarding with shop details, category, establishment date, and owner verification; public storefront discovery with live online status and direct customer messaging. |
| **Administrators** | Monitor platform KPIs and Chart.js growth/demographic analytics (with PNG export); manage users, shops, roles, and service categories; export formatted Arabic RTL PDF and UTF-8 CSV reports. |

---

## Technology Stack

| Layer | Technologies |
| :--- | :--- |
| **Frontend** | Next.js 15 (App Router), React 19, TypeScript 5.7, Bootstrap 5 RTL, Font Awesome 6, `@microsoft/signalr`, Chart.js, Sonner, EmailJS |
| **Backend & Real-Time** | .NET 8, ASP.NET Core Web API, ASP.NET Core Identity, JWT Bearer Auth, SignalR, Stripe.net (v50), Swashbuckle (Swagger/OpenAPI) |
| **Data & Reporting** | Entity Framework Core 8, Microsoft SQL Server, Repository Pattern, iTextSharp (Arabic RTL PDF), UTF-8 CSV Export, SMTP |
| **AI & Computer Vision** | Python 3.10+, FastAPI, Uvicorn, Ultralytics YOLOv8 (PyTorch), Pillow |
| **CI/CD & Tooling** | GitHub Actions, Automated `.NET 8` & `Next.js` build validation |

---

## Core Team

<table width="100%">
  <tr>
    <td align="center" width="25%">
      <a href="https://github.com/Mohammed-3tef">
        <img src="https://github.com/Mohammed-3tef.png" width="96px;" alt="Mohammed Atef"/><br />
        <sub><b>Mohammed Atef</b></sub>
      </a><br />
      <a href="https://www.linkedin.com/in/mohammed-atef-abd-elkader/">LinkedIn</a>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/Steven-Amin02">
        <img src="https://github.com/Steven-Amin02.png" width="96px;" alt="Steven Amin"/><br />
        <sub><b>Steven Amin</b></sub>
      </a><br />
      <a href="https://www.linkedin.com/in/steven-amin02/">LinkedIn</a>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/Omniaashraf10">
        <img src="https://github.com/Omniaashraf10.png" width="96px;" alt="Omniaa Ashraf"/><br />
        <sub><b>Omniaa Ashraf</b></sub>
      </a><br />
      <a href="https://www.linkedin.com/in/omniaashraf2/">LinkedIn</a>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/kenzi-shibl">
        <img src="https://github.com/kenzi-shibl.png" width="96px;" alt="Kenzi Shibl"/><br />
        <sub><b>Kenzi Shibl</b></sub>
      </a><br />
      <a href="https://www.linkedin.com/in/kenzi-shibl-2832aa357/">LinkedIn</a>
    </td>
  </tr>
</table>

---

## License

Projects within the **Sany3y** organization are licensed under the **GNU General Public License v3.0 (GPL-3.0)** unless otherwise noted in an individual repository.

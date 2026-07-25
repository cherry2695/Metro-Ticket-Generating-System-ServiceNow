<div align="center">

# 🚇 Metro Ticket Generating System in ServiceNow

**Digitizing metro ticket booking with automated fare calculation, instant QR ticket generation, and real-time operations dashboards — built entirely on the ServiceNow platform.**

![Platform](https://img.shields.io/badge/Platform-ServiceNow-3C4E93?style=flat-square)
![Category](https://img.shields.io/badge/Category-Transportation-blue?style=flat-square)

[Features](#-features) · [Screenshots & Demo](#-screenshots--demo) · [Architecture](#-architecture) · [Setup](#-setup-guide) · [Documentation](#-documentation)

</div>

---

## 📖 Overview

The **Metro Ticket Generating System** replaces manual, counter-based metro ticketing with a fully self-service digital flow built on ServiceNow. Passengers select their journey details through a Service Portal form, the platform automatically calculates fare, generates a unique QR-coded digital ticket, and emails a confirmation — all without manual intervention. Operations teams get live dashboards for bookings, revenue, and route usage.

> Built to demonstrate that ServiceNow — typically an IT service management platform — can power real-world, consumer-facing automation beyond the ITSM use case.

## ✨ Features

- 🎫 **Self-service booking** — select source, destination, date, and passenger count
- 💰 **Automated fare calculation** — no manual pricing, no errors
- 🔢 **Unique ticket generation** — system-assigned ticket numbers
- 📱 **QR-based digital ticket** — instant, scannable travel pass
- 📧 **Automated email confirmation** — ticket + QR delivered on booking
- 📊 **Operations dashboard** — real-time bookings, revenue, and route analytics
- 🔐 **Role-based access control** — passengers, support staff, and admins scoped appropriately

## 📸 Screenshots & Demo

<div align="center">

| Ticket Booking Request | Ticket Table View |
|:---:|:---:|
| ![Metro Request](./Project%20Demo/Metro_request.png) | ![Metro Table](./Project%20Demo/Metro_Table.png) |

| Operations Dashboard | Service Catalog |
|:---:|:---:|
| ![Metro Dashboard](./Project%20Demo/Metro_Dashboard.png) | ![Metro GitLab](./Project%20Demo/Service_Catalog.png) |

</div>

🎬 **Full Project Demo Video:** [Project_Demo.mp4](./Project%20Demo/Project_Demo.mp4)

> Click the link above to view/download the demo recording directly from the repository.

## 🏗️ Architecture

```
┌─────────────────────────────────────────────┐
│              UI Layer                         │
│   Service Portal · Service Catalog            │
│   Catalog Client Scripts · UI Policies         │
├─────────────────────────────────────────────┤
│              Logic Layer                       │
│   Business Rules · Script Includes             │
│   Flow Designer                                │
├─────────────────────────────────────────────┤
│              Data Layer                         │
│   u_metro_ticket (custom table)                │
├─────────────────────────────────────────────┤
│              Insight Layer                      │
│   Reports · Performance Analytics Dashboards   │
└─────────────────────────────────────────────┘
```

**Automation flow:**
```
Ticket Submitted
   → Fare Calculation (Business Rule, before insert)
   → Ticket Number Generation (Business Rule, before insert)
   → Record Committed
   → QR Code Generation (Business Rule, after insert → external API)
   → Confirmation Notification Sent
```

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | ServiceNow Service Portal, Service Catalog, Client Scripts, UI Policies |
| Backend | Business Rules, Script Includes, Flow Designer |
| Database | ServiceNow custom table (`u_metro_ticket`) |
| Integration | External QR code generation API |
| Reporting | ServiceNow Reports & Performance Analytics |
| Notifications | ServiceNow Notification Engine (email) |

## 🚀 Setup Guide

1. **Provision a ServiceNow instance** — Personal Developer Instance or Enterprise Instance
2. **Create the data model** — custom table `u_metro_ticket` with fields for source/destination station, journey date, passenger count, fare amount, ticket number, and QR code
3. **Build the Service Catalog item** — "Metro Ticket Booking" with variables matching the data model
4. **Add client scripts & UI policies** — validation for mandatory fields and duplicate station selection
5. **Configure business rules** — fare calculation, ticket number generation, QR trigger (after insert)
6. **Integrate QR generation** — Script Include calling an external QR API, storing the result on the ticket record
7. **Configure notifications** — email confirmation with ticket details and QR code
8. **Build reports & dashboard** — bookings, revenue, and route-usage analytics
9. **Configure roles & ACLs** — `metro_user`, `metro_support`, `admin` with table/record/field-level access rules
10. **Run QA tests** — validate booking, fare accuracy, QR generation, notifications, and access control

## 📄 Documentation

Full phase-by-phase documentation is available as PDFs in this repository:

| Document | Description |
|---|---|
| [Metro Ticket Generating System in ServiceNow](./Metro%20Ticket%20Generating%20System%20in%20ServiceNow.pdf) | Project overview & description |
| [Phase-1 Requirement Analysis and Planning](./Phase-1%20Requirement%20Analysis%20and%20Planning.pdf) | Objectives, scope, stakeholders, roadmap |
| [Phase-2 Backend Development and Configurations](./Phase-2%20Backend%20Development%20and%20Configurations.pdf) | Data model, business rules, automation |
| [Phase-3 UI-UX Development and Customization](./Phase-3%20UI-UX%20Development%20and%20Customization.pdf) | Booking portal, confirmation page, dashboard |
| [Phase-4 Data Migration, Testing and Security](./Phase-4%20Data%20Migration%2C%20Testing%20and%20Security.pdf) | QA testing, access control, data integrity |
| [Phase-5 Deployment](./Phase-5%20Deployment.pdf) | Deployment, documentation, demo planning |
| [Project Conclusion](./Project%20Conclusion.pdf) | Summary, outcomes, and future roadmap |

---

<div align="center">
⭐ If you found this project useful, consider giving it a star!

</div>

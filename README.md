# QR Code Payment Platform

QR payment MVP: server, operations console and mobile application.

A merchant issues a secure, expiring QR code, the customer scans it, checks the merchant identity and confirms. The server guarantees a consistent payment, produces receipts and supports refunds. The payment provider is simulated and no money moves.

> **Structure only.** The source code is private. Source files here are intentionally empty so you can see how the project is organized. Commands describe the private codebase.

![Mobile sign in](docs/screenshots/mobile-login.png)

## Features

- Customer and merchant roles in one app
- Expiring single-use QR codes
- Receipts and refunds
- Live events
- Support and investigation tools
- Append-only audit

## Applications

| Application | Role |
| --- | --- |
| [API server](server/README.md) | Express modular monolith |
| [Operations console](admin/README.md) | React console with a same-origin session gateway |
| [Nexa Pay mobile](mobile/README.md) | Expo application for customers and merchants |

## Architecture

```mermaid
flowchart LR
  M[Mobile app] --> API[API server]
  C[Operations console] --> GW[Session gateway] --> API
  API --> DB[(PostgreSQL)]
  API --> R[(Redis)]
  W[Workers] --> DB
  API --> PV[Simulated provider]
```

## Engineering highlights

- Idempotency keys and database constraints protect financial state
- Amounts are integers in centimes
- Crash recovery and lookup-only reconciliation
- Unit, integration, API, security and concurrency tests
- Browser never holds backend tokens: an encrypted session gateway does

## Screenshots

| Mobile sign in | Customer home |
| --- | --- |
| ![Mobile sign in](docs/screenshots/mobile-login.png) | ![Customer home](docs/screenshots/mobile-customer-home.png) |
| **Merchant home** | **Create payment** |
| ![Merchant home](docs/screenshots/mobile-merchant-home.png) | ![Create payment](docs/screenshots/mobile-create-payment.png) |
| **Operations overview** | **Transactions** |
| ![Operations overview](docs/screenshots/admin-dashboard.png) | ![Transactions](docs/screenshots/admin-transactions.png) |
| **Transaction details** | **Reports** |
| ![Transaction details](docs/screenshots/admin-transaction-details.png) | ![Reports](docs/screenshots/admin-reports.png) |
| **Audit log** | **Merchants** |
| ![Audit log](docs/screenshots/admin-audit.png) | ![Merchants](docs/screenshots/admin-merchants.png) |
| **Accounts** | **System health** |
| ![Accounts](docs/screenshots/admin-accounts.png) | ![System health](docs/screenshots/admin-system.png) |

Screenshots show the real stack with generated demo payments. Mobile screens were captured from the web build with browser storage in place of the device secure store.

## Repository layout

```text
server/                                 Express modular monolith
admin/                                  React console with a same-origin session gateway
mobile/                                 Expo application for customers and merchants
docs/screenshots/
```

Each application has its own README with responsibilities, dependencies, structure and commands.

## Usage

Published for portfolio and presentation purposes. No license is granted for reuse.

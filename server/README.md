# API server

Express modular monolith. Part of [QR Code Payment Platform](../README.md).

> **Structure only.** The source code is private. Source files here are intentionally empty so you can see how the project is organized. Commands describe the private codebase.

## Responsibilities

- QR issue, scan, validation and confirmation
- Persistent simulated provider, webhooks and reconciliation
- Receipts, refunds and notifications
- Workers for recovery, delivery and maintenance
- Sessions with rotating refresh tokens
- Generated OpenAPI documentation

## Main dependencies

`@logtail/pino`, `argon2`, `cors`, `dotenv`, `express`, `helmet`, `jsonwebtoken`, `nodemailer`, `pg`, `pino`, `pino-http`, `pino-pretty`, `qrcode`, `redis`, `sequelize`, `swagger-ui-express`, `ws`, `zod`

## Structure

```text
.github/                          1 file
database/                         22 files
docs/                             9 files
scripts/                          6 files
src/                              2 files
src/config/                       1 file
src/database/                     25 files
src/errors/                       1 file
src/jobs/                         2 files
src/logging/                      1 file
src/middleware/                   7 files
src/modules/                      58 files
src/payment-providers/            4 files
src/policies/                     1 file
src/realtime/                     1 file
src/redis/                        1 file
src/utils/                        6 files
src/websocket/                    1 file
tests/                            19 files
```

## Commands

```bash
npm install
npm run dev
npm start
npm run worker
npm run db:migrate
npm run db:seed
npm test
npm run lint
```

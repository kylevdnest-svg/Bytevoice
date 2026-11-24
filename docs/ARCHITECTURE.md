# Architecture and security

Status: proposed baseline, subject to owner approval before implementation. Prefer a simple modular monolith over microservices.

## Stack and deployment
- TypeScript, React/Next.js web application with server-side API, PostgreSQL, pnpm.
- Docker Compose for local PostgreSQL; Windows PowerShell development.
- Server-side PDF renderer from a shared invoice layout model, with embedded licensed fonts and controlled assets. Choose renderer after a fidelity/hosting spike.
- S3-compatible private object storage for logos and issued PDF artefacts (local adapter during development).
- Transactional email adapter, recurring-payment provider adapter, and database-backed jobs/outbox. Fake adapters by default locally; no live credentials until explicitly authorised.
- One web deployment and one scheduler/worker process or managed equivalent. Managed PostgreSQL with backups. Choose hosting after testing PDF runtime, scheduling, egress and real cost. No AI runtime required.

## Data model
users; companies; memberships (owner/admin/staff); branding profiles; customers; catalog items; invoices; invoice lines; immutable issued snapshots/PDF assets; invoice sequences; payment entries; recurring schedules/runs; subscriptions; plan entitlements; billing events; outbox/jobs; audit events. Every business-owned record is scoped to company_id. Auth identity and membership are separate; server derives authorised company context and ignores untrusted tenant claims. Use tenant-scoped composite references/unique constraints and PostgreSQL row-level security as defence in depth; test with non-owner runtime roles.

## Financial invariants
Use decimal arithmetic or integer minor units, never binary floating-point for money. Store ISO currency and explicit tax/rounding policy. Calculate totals on the server from validated quantities/prices/discounts; shared client calculation is advisory. Persist issuance snapshot with amounts, tax, customer/business identities, template version, assets and payment details. Allocate per-company unique invoice number inside transaction; prevent duplicate issuance using constraints and idempotency keys. Never reuse issued numbers. Audit payment changes, corrections and voids. Define rounding and credit-note policy with accountant review and fixture tests. Reports derive from issued documents and payment entries, excluding voids according to documented policy.

## Jobs and integration
Transactional outbox for PDF/email delivery; retry bounded with visible failures; issue state not lost on email failure. Recurring jobs use schedule + occurrence unique key, locking and idempotency. Define month-end handling and timezone (Africa/Johannesburg default). Use verified signed billing webhooks with event deduplication and replay-safe state transitions, server-side entitlements, provider checkout/tokenisation; never store card PAN/CVV. Keep SaaS subscription charges distinct from customers' invoices and payment records. Reconcile billing state against provider periodically; no provider chosen yet.

## Security, privacy and operations
Use established auth library/service, verified accounts, secure session cookies, CSRF protection where applicable, rate limits and least privilege. Authorise every server operation and asset fetch. Private files with short-lived authorised downloads; validate upload bytes/type/size, re-encode raster logos, disallow unsanitised SVG and remote URL fetching. Escape all user-supplied text in preview/PDF/email. Restrictive CSP, safe headers, no secrets in client bundles or logs. Tenant isolation tests for reads, writes, exports, jobs and asset access. Audit sensitive actions; redact personal information from diagnostic output. Encrypt transit, secure storage and credentials, test backup restoration, account export and retention/deletion rules. Review POPIA and applicable tax record requirements before launch. Public repo contains synthetic examples only.

## Deployment gates
Automated local lint/type/unit/integration tests, populated two-tenant tests, end-to-end invoice lifecycle, PDF parity, verified webhook and recurring job replay, migration rehearsal, backup/restore, production smoke test and monitoring. No free-hosting promise; validate quotas and upgrade path. Never deploy real billing or email until configured and approved.

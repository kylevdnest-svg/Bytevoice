# Build roadmap

Status: planning only; zero packages accepted. Aim for a lean commercial MVP. Earlier 7–10 working day estimate is aspirational and not a commitment; security, regulatory review, provider onboarding and real deployment may extend it.

| Package | Deliverable | Acceptance gate |
| --- | --- | --- |
| BV-001 | Local workspace, app scaffold, DB/migrations, health endpoint, test harness | Clean local bootstrap and repeatable checks |
| BV-002 | Auth, company onboarding, membership and tenant boundaries | Two-company isolation tests and role enforcement |
| BV-003 | Branding, company settings, logo storage, customer and catalogue | Authorised CRUD, safe uploads, saved defaults |
| BV-004 | Invoice editor, calculation, draft management and live preview | Decimal/tax fixtures, responsive UI, validation |
| BV-005 | Issue lifecycle, numbering, snapshots, PDF templates | Concurrency/idempotency tests, immutable branded PDFs |
| BV-006 | Email/outbox, manual payment records, dashboard and reports | Delivery failure/retry, payment audit, correct balances |
| BV-007 | Recurring invoices and scheduling | Month-end/replay/concurrency/tenant tests |
| BV-008 | Plan entitlements and subscription billing adapters | Quota and webhook replay tests, fake provider by default |
| BV-009 | Real provider selection/integration, production configuration | Owner approval, sandbox billing/email, pricing/tax rules |
| BV-010 | Release hardening, operational readiness, pilot | Full regression, security review, restore rehearsal, pilot sign-off |

## Proposed development workflow
Reuse established GrimByte local-first workflow unless owner requests another method. Canonical proposed workspace C:\Dev\Bytevoice; diagnostics C:\Dev\Bytevoice-Diagnostics; branch bytevoice-development (not created yet). Use local Windows PowerShell and pnpm, Docker Compose for dependencies, fixed documented ports chosen after collision check. Deliver downloadable self-contained .ps1 packages, one package/block at a time; script checks repo/worktree prerequisites, applies scoped changes, runs local verification, emits sanitised timestamped diagnostic log. Never claim acceptance from candidate generation alone; owner supplies Pass or newest diagnostic log when failed, review before continuing. Keep repairs scoped and preserve prior accepted functionality. No GitHub Actions/cloud CI unless owner explicitly changes workflow; no unsolicited implementation commits. GitHub documentation edits requested by owner are allowed.

## Completion policy
Update decision register and status after acceptance; separate planned, implemented, locally verified, deployed and commercially ready states. No live secrets or actual client data in packages/logs/repo. Before release: official SA tax/privacy review, test actual PDF and email, verify real billing/entitlements, secure production hosting, backups/restoration, support and cancellation paths, and explicit owner sign-off.

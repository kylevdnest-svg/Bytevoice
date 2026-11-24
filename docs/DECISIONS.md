# Decisions and status

Baseline: 2026-11-24. This register controls approval status.

## Owner-confirmed
- D001: Product name is Bytevoice.
- D002: Product is subscription-based invoice software.
- D003: Companies must easily add their own branding.
- D004: Use South African Rand in the concept; ZAR is the initial product default.

## Proposed defaults (not yet expressly approved)
- D005: GrimByte Systems product; dedicated invoicing rather than full accounting.
- D006: Dark application shell, purple accents, white branded invoice preview, responsive layout.
- D007: R99/R199/R349 monthly plans and features in COMMERCIAL.md; concept price is illustrative.
- D008: TypeScript/Next.js/PostgreSQL modular monolith, no AI, provider adapters and local-first Windows workflow.
- D009: Manual payment tracking, recurring invoices, email, PDF templates and tenant isolation in MVP; no invoice payment gateway at launch.
- D010: Issued snapshots immutable, corrections audited, secure tenant access and read/export access on subscription expiry.

## Open before implementation/release
Stack and workspace approval; exact tax/rounding and credit-note rules; invoice numbering options; required templates/branding details; subscription pricing/limits/seats/grace/refunds; email/billing/hosting providers and budget; retention/export rules; legal terms and privacy notice; production domain. Approve choices before implementing dependencies or activating live providers. Do not represent proposals as user-approved.

## Current progress
- Sources of truth: initial documentation baseline.
- Implementation: not started.
- Accepted packages: 0/10.
- Next package: BV-001 (after owner confirms start).
- Production: not deployed; no live services or credentials configured.

Changes: record date, decision, owner approval where applicable and impacted documents. Update roadmap/status only when evidence supports it.

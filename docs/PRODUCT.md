# Product specification

## Purpose
Bytevoice is a browser-based subscription invoicing service for small businesses, freelancers and service providers. The primary promise is to create a professional branded invoice in under 60 seconds for an existing customer using saved business details. Measure this in usability testing; it is a target, not a verified claim.

## Confirmed direction
- Product name: Bytevoice; offered as subscription software.
- Companies can easily configure their own branding.
- Initial visual concept uses rands (ZAR).
- Keep the product focused on invoicing rather than full accounting.

## Proposed launch experience
Responsive, accessible desktop-first web application. Dark navy/charcoal shell with purple accents, clear navigation, and a light invoice document preview. Mobile users can create, view and share invoices without a three-column layout. The visual mockup is inspiration, not a pixel-perfect contract. All sample business details must be fictional.
- Dashboard: paid, outstanding and overdue amounts, recent invoices, quick create.
- Invoices: search/filter, draft editor, issue, PDF download, send, payment status and history.
- Customers: reusable contact and billing details.
- Products & services: reusable descriptions, unit prices and tax defaults.
- Branding & settings: company identity, logo upload, primary/accent colours, contact and registration details, tax details, payment instructions, invoice numbering and templates.
- Subscription: current plan, usage, upgrade/downgrade, billing history, cancellation.
- Reports: simple invoiced/paid/outstanding summaries; no ledger.

## Branding-first workflow
Onboarding: create account and company, enter business details, upload optional logo, select colours/template, preview sample invoice and save. Default clean template works without a logo. Provide at least two distinct templates at MVP; no HTML/CSS injection or arbitrary scripts. Company defaults populate new invoices automatically. Live preview reflects changes without requiring a PDF export. Existing issued invoices preserve the branding and legal/payment details captured at issuance. PDF and preview should match materially. Bytevoice branding stays in the application; proposed default is no mandatory Bytevoice watermark on paid customer invoices.

## Invoice lifecycle
Draft -> issued -> partially paid / paid; overdue is derived from due date and outstanding balance, not an independent destructive state. Void/correction is an explicit audited action, not silent deletion of an issued invoice. Define credit-note requirements before commercial launch. Sending, delivery failure and reminders are separate from financial state. Drafts can be edited/deleted; issued invoice financial content and number are immutable. Payments are manually recorded at MVP; no claim that funds have cleared without evidence. Support PDF download even when email fails. Recurring invoices (Business/Professional proposal) use saved schedule and customer details, with pause/cancel and duplicate prevention.

## Invoice fields
Company and customer details, invoice number, issue and due dates, currency, line descriptions, quantities, unit prices, discounts, tax treatment, subtotal, tax total, grand total, payment instructions, optional terms/notes. ZAR default, configurable tax treatment; VAT not charged by default unless the business configures appropriate registration/tax status. Initial South African tax invoice/credit-note rules must be checked against current official requirements before launch, including required fields and retention. Do not label non-VAT documents as tax invoices. Use sample-only data in tests.

## Scope boundary
MVP: authentication, tenant setup, branding, customer/product records, invoice editor, calculation, immutable issuance, PDF, email, manual payments, recurring invoice automation, basic reports and Bytevoice subscription lifecycle. No general ledger, bank reconciliation, payroll, inventory, AI, tax filing, native mobile apps, marketplace, or accounting integration in MVP. Customer invoice payment links, additional currencies and accounting exports are post-MVP candidates unless explicitly approved.

## Acceptance
A new business can sign up, configure branding, create customer and invoice, issue a unique number, download a readable branded PDF, send it, record payment and see updated balances. Another tenant cannot access any related data, files or jobs. Repeated issue/send/job requests must not duplicate financial documents or recurring invoices. Historical PDFs remain unchanged after branding updates. Failed email and billing events are visible and recoverable. Subscription limits are enforced server-side. Accessibility, mobile layout, empty/error states and keyboard use are tested.

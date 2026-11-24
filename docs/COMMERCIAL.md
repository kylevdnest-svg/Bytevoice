# Commercial model

Status: proposal, not approved pricing or validated demand.

| Feature | Starter | Business | Professional |
| --- | --- | --- | --- |
| Monthly price (ZAR) | R99 | R199 | R349 |
| Issued invoices/month | 30 | Unlimited* | Unlimited* |
| Company branding | Yes | Yes | Yes |
| PDF and email | Yes | Yes | Yes |
| Recurring invoices | No | Yes | Yes |
| Templates | Core | Core + advanced | Core + advanced |
| Staff access | Owner | Owner | Multiple staff |
| Reports | Basic balances | Basic reports | Advanced invoice reports |

*Subject to transparent abuse/fair-use controls, not hidden invoice limits. Number of seats, template count, tax-inclusive pricing, discounts and any trial are open decisions. The R299/month shown in the concept image was illustrative, not a fixed price.

## Billing principles
Monthly prepaid SaaS subscription per business as proposed default. Separate subscription billing from invoice payment tracking. Enforce entitlements server-side; count unique successful invoice issuances in a defined billing cycle, not drafts/retries/downloads. Upgrades/downgrades, proration, cancellation, failed payment grace periods, refunds and reactivation require explicit policy before live billing. Proposed approach on expiry: read/export existing records while restricting new issuance and automated recurring runs; never hold customer data hostage. Communicate changes and cancellation clearly. Use hosted checkout and signed provider events; select provider only after checking current SA recurring payment support, fees, settlement, webhook reliability and terms.

## Cost and validation
No AI costs planned. Actual costs depend on hosting, PostgreSQL/backups, file storage, email, domain, monitoring, payment fees, support and tax. Free tiers may suit development but are not a production guarantee. Establish monthly fixed costs, per-company variable cost, gross margin, break-even and workload limits after provider selection. Validate proposed prices with target businesses before publication. Start with a small pilot and measure time-to-first-invoice, branding completion, send success, recurring job reliability, retention and support demand.

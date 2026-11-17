# EzSeller troubleshooting index

Start from what the seller sees, not from internal SP-API/tool names.

| Symptom / search phrase | Problem ID | Next step |
|---|---|---|
| Listing is suppressed, inactive, or missing | `AMZ.LISTING.SUPPRESSED` | Identify marketplace + current listing state before changing content. |
| Inventory does not reconcile | `AMZ.INVENTORY.DISCREPANCY` | Preserve ASIN/SKU/FNSKU identity and reconcile marketplace-scoped evidence. |
| Amazon reversed a reimbursement | `AMZ.REIMBURSEMENT.REVERSED` | Reconcile financial events and supporting evidence privately. |
| Data is from the wrong marketplace | `AMZ.MARKETPLACE.MISMATCH` | Stop; do not fall back to another marketplace. |
| Wrong ASIN/UPC/product identity is attached | `AMZ.CATALOG.IDENTITY_CONFLICT` | Quarantine conflicting identity evidence before any write. |
| FBA received fewer units than sent | `AMZ.FBA.INBOUND_SHORTAGE` | Reconcile shipment, received, adjustment, and reimbursement evidence. |
| EzSeller does not appear in ChatGPT plugin search | Distribution / discovery | Try the [published plugin's direct link](chatgpt-plugin.md); do not infer unpublished status from search alone. |
| ChatGPT plugin opens but Amazon data is unavailable | Authorization / entitlement | Separate plugin connection, EzSeller authorization, Amazon public-app eligibility, subscription and seller scopes. Use [private support](https://ezseller.smatdesigns.com/support). |
| EzSeller iPhone or Mac beta cannot sign in | Native beta / provider authorization | Confirm platform and build; general public Amazon sign-in is not yet verified. See [Apple beta guide](apple-apps.md). Never reuse owner tokens. |
| 2027 fee estimate differs from an Amazon bill | Published model versus assessed fee | Compare schedule date, inputs, size tier and the authoritative Amazon statement. See [fee estimator limits](amazon-fees-2027.md). |
| Agency tenant cannot use all seller tools | Tenant / client scope | Confirm delegated seller connection, account scope and approval requirements. Three provider-free schedule calculators do not establish general agency seller-access readiness. |

## Escalation rule
Search public knowledge first. Diagnose authenticated seller state second. Open a support case only when the problem remains unresolved.

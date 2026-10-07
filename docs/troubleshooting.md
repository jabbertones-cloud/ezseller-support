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

## Escalation rule
Search public knowledge first. Diagnose authenticated seller state second. Open a support case only when the problem remains unresolved.

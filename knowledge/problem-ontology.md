# EzSeller problem ontology — seed

These are routing identifiers, not claims that every cause can be diagnosed without current seller/marketplace state.

| Problem ID | Customer language | Official concept | Public first step |
|---|---|---|---|
| `AMZ.LISTING.SUPPRESSED` | “my listing disappeared/is suppressed” | Listing status / suppression | Identify marketplace and listing state; live cause requires authenticated diagnosis. |
| `AMZ.INVENTORY.DISCREPANCY` | “Amazon lost my inventory” | Inventory ledger / fulfillment inventory discrepancy | Preserve SKU/ASIN/FNSKU identity and marketplace boundaries before reconciling. |
| `AMZ.REIMBURSEMENT.REVERSED` | “Amazon took back my reimbursement” | Reimbursement / financial event reversal | Reconcile events and evidence; keep private financial details out of public issues. |
| `AMZ.MARKETPLACE.MISMATCH` | “the numbers/listing are from the wrong marketplace” | Marketplace-scoped seller data | Never substitute another marketplace as fallback. |
| `AMZ.CATALOG.IDENTITY_CONFLICT` | “wrong product/ASIN/UPC is attached” | Catalog/listing identity | Quarantine conflicting identity evidence rather than overriding it. |
| `AMZ.FBA.INBOUND_SHORTAGE` | “FBA received fewer units than I sent” | FBA inbound/reconciliation | Reconcile shipment/received state with authenticated evidence. |

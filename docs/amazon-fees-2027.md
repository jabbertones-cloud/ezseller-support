# Amazon 2027 fee changes: EzSeller estimates

**Last reviewed:** November 17, 2026  
**Scope:** Published Amazon **US 2027** fee schedules modeled in product source. These are **read-only planning estimates**, not charged, settled or reimbursed fees.

As of the November 17 product-source review, EzSeller defines three published-schedule fee tools. Their existence in product `main` does not alone prove they are enabled on the specific live MCP server or available to your current subscription. Ask your assistant to check the tool catalog before relying on a tool call.

| Tool | Helps answer | Information you must provide |
| --- | --- | --- |
| `amazon_fee_schedule_compare` | How a SKU's current FBA fulfillment fee compares with estimated 2027 rates; optional Buy X Get Y promotion fee | Current per-unit fee, price and FBA size tier. Include category/low-price status or promotion inputs where relevant |
| `amazon_storage_aging_report` | How units, size class, occupied cubic feet and age bands affect planned 2027 storage; 181-day crossing exposure and optional AWD aging | Calendar month and each lot's units, volume, age and size class |
| `amazon_low_inventory_fee_check` | Whether the revised **two-sided 28-day** low-inventory test applies | Inventory units, trailing 28-day shipments, subsequent 28-day shipments if available, and the assessment date |

## Safe questions to ask your agent

- "Compare my current $2.72 per-unit FBA fee with Amazon's published 2027 schedule for a small-standard SKU priced at $7.99. Show your assumptions."
- "For these inventory lots and cubic-foot values, show 2027 storage bands and which stock may cross 181 days."
- "Evaluate the revised low-inventory fee rule. I do not yet have the following 28 days of shipments, so mark that result unknown."

## What the results do and do not mean

- These calculators use **caller-supplied inputs** and published schedule rules, without accessing SP-API or modifying your seller account.
- The model was reviewed against announced schedules on **November 16, 2026**. Amazon can revise schedules before their effective dates. Confirm current official notices and Amazon's own Fee Change Comparison dashboard for your products.
- The modeled Buy X Get Y promotion fee begins January 15, 2027; the modeled unified storage changes and revised low-inventory test begin February 1, 2027; modeled AWD aged-storage changes begin March 1, 2027. Dates and applicability depend on official Amazon rules.
- Fee comparison starts with **your current fee**. If a live `amazon_estimate_fees` tool is available and authorized, its estimate can help supply that input; do not silently treat an example fee as your account's actual fee.
- If the following 28-day shipment window has not elapsed, `amazon_low_inventory_fee_check` cannot determine the final two-sided result. A missing charge today does not prove it will never apply.
- Storage measurements and assessed charges are controlled by Amazon, not the estimate. These tools do not reconstruct settled Payments events or promise a reimbursement.

For current Amazon policy or account-specific bills, consult Seller Central and [EzSeller private support](https://ezseller.smatdesigns.com/support). For tool-access problems see [ChatGPT troubleshooting](chatgpt-plugin.md) or [AI host setup](connect-frontier-ai.md).

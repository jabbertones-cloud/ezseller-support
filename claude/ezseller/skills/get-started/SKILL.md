---
name: get-started
description: Start or resume an Amazon Seller Central investigation in Claude using EzSeller. Use when a seller asks about FBA inventory, listing suppression, selling fees, Amazon order finances, or reimbursement evidence; when the seller has just installed EzSeller; or when Amazon authorization is missing.
---

# Investigate with EzSeller in Claude

1. Determine the question the seller wants answered. Call `amazon_connection_status` first to determine whether an EzSeller workspace and Amazon seller account are actually authorized. A connected Claude connector is not evidence of Amazon authorization.
2. If EzSeller or Amazon is not connected, direct the user to the plugin's Connectors tab and, as appropriate, https://ezseller.smatdesigns.com/connect. Tell them to sign in with the provider on its own site. Never request an Amazon password, LWA credential, client secret, access token, refresh token, or raw customer PII in Claude.
3. If Amazon public-app onboarding is restricted or unavailable for this seller, report that precise blocker. Do not suggest bypassing it by creating a private SP-API application, reusing CommerceOS credentials, or transferring a seller's authorization.
4. Resolve the authenticated seller/workspace and requested marketplace before invoking a scoped read. Never guess a workspace or silently default the marketplace. Resolve SKU, ASIN, or order identity from tool evidence. Ask only for missing information essential to the question.
5. Use the available read-only EzSeller tool appropriate for the job. Treat Amazon-provider facts as observed, user-supplied claims as unverified, and deductions as inferences. Include timestamps, currency, marketplace, coverage, and gaps when the response supplies them.
6. If the request involves a listing change, reimbursement filing, pricing change, other account mutation, or money movement, do not attempt it as part of onboarding. Only proceed if a separate server-enforced approval workflow is actually available, specifically requested, and authorized. No host prompt or tool annotation overrides server-side authorization.
7. Do not treat incomplete pagination, an inaccessible report, stale evidence, or a missing finance component as zero. Never invent quantities, COGS, freight, complete profits, Amazon decisions, or resolved reimbursement claims.
8. Once authorization is available, resume the user's original question. If it remains blocked, report the observed reason and a supported next step instead of pretending the work succeeded.

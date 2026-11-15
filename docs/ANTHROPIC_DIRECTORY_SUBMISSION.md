# Anthropic directory submission: EzSeller

Prepared 2026-11-14. **Status: package prepared, submission not sent, real Claude host certification incomplete.**

**Authoritative engineering repo:** private `jabbertones-cloud/ezamazon`; **public plugin distribution:** `jabbertones-cloud/ezseller-support` at `claude/ezseller`. This public repo contains only connector metadata, an operator onboarding skill, a static icon, and public support material. Keep the original EzSeller source and CommerceOS private.

## Route and immutable product identity

- Connector submission type: **MCP connector** for `https://ezseller.smatdesigns.com/mcp`.
- Plugin submission type: **Plugin bundle** from GitHub repo `jabbertones-cloud/ezseller-support`, branch `main` **after this PR merges**, path `claude/ezseller`.
- Permanent listing name/slug: `ezseller`. Publisher: **SMAT Designs**. The plugin version is distinct from the OpenAI-published EzSeller app version.
- Submit both from the same long-term Claude organization to enable pairing, connector usage reporting, and one shared MCP backend. Do not expose the private source repository or attach credentials to any files.

## Proposed standalone MCP connector listing

**Display name:** EzSeller

**One-liner (under 200 characters):** Investigate your Amazon Seller Central listings, FBA inventory, financial events, selling fees, and reimbursements using authorized seller data.

**Description (under 2,000 characters):**
EzSeller helps Amazon sellers investigate real operating questions with Claude. Connect an eligible Seller Central account through EzSeller's secure authorization flow, then ask Claude to diagnose listing suppression, examine FBA inventory discrepancies, understand supported order financial events, estimate selling fees, and audit available reimbursement evidence. Results distinguish provider observations from inferences and unresolved gaps. Access is scoped to the signed-in seller and marketplace. EzSeller does not promise autonomous reimbursement filing, unrestricted listing changes, complete profit calculations without external costs, or Amazon access where the required application authorization is unavailable. Actions requiring changes must have independent authorization and server-enforced approval.

**Suggested categories:** Business and Productivity, Commerce/Shopping if offered in portal. Choose only actual portal category labels.

**Examples for directory use-cases:**
1. Investigate a suppressed or inactive listing with current Amazon evidence.
2. Trace an FBA inventory discrepancy and distinguish observed quantities from unknowns.
3. Explain an Amazon order's supported financial events and missing cost inputs.
4. Estimate referral or fulfillment fees for an eligible offer.
5. Audit reimbursement evidence and identify the next supported step; do not promise filing.

**What users need:** a Claude account that supports connectors, an EzSeller identity, and an eligible, explicitly authorized Seller Central account for live Amazon data. Amazon public-app publication is a separate external gate. Some functions are plan-, role-, marketplace-, and authorization-dependent.

**Links:**
- Website: https://ezseller.smatdesigns.com/
- Documentation: https://ezseller.smatdesigns.com/learn/connect-amazon-seller-central-to-claude
- Support: https://ezseller.smatdesigns.com/support
- Issue reports: https://github.com/jabbertones-cloud/ezseller-support/issues
- Privacy: https://ezseller.smatdesigns.com/privacy
- Terms: https://ezseller.smatdesigns.com/terms
- Brand icon: `claude/ezseller/assets/ezseller-icon.png` (512 x 512 PNG, verified in Anthropic native CLI)
- Business: SMAT Designs, https://smatdesigns.com/
- Contact email: supply and verify the actual monitored organizational mailbox in the authenticated portal. Never invent one.

**Authentication:** OAuth 2.0 required. Live public resource discovery `/.well-known/oauth-protected-resource/mcp` and authorization metadata `/.well-known/oauth-authorization-server` returned HTTP 200 on 2026-11-14; anonymous `/mcp` returned 401. These are discovery probes, **not** evidence of completed Claude login or seller tool calls. Do not supply OAuth secrets in public repo or review form unless Anthropic specifically provides a secure credential mechanism.

**Data handling:** first-party EzSeller MCP service with authorized calls to third-party Amazon SP-API and normal cloud infrastructure; seller and marketplace identifiers, listing/inventory/order/financial/reimbursement data may be handled. User authorizes access and sends requests through Claude. Privacy/retention disclosures are governed by the actual published policy. No personal-health feature or sponsored-content placement is claimed for this connector. It does not transfer funds or sell goods inside Claude. Verify all portal attestations against exact production behavior before submission.

## Required evidence before claiming ready

- [x] Canonical HTTPS MCP identity and OAuth discovery have public HTTP success with authentication required at MCP.
- [x] Public documentation, privacy, terms, and support URLs responded HTTP 200 on 2026-11-14.
- [x] Public, small source repository and Claude-native plugin folder prepared for review on a feature branch.
- [ ] Merge exact reviewed branch, independently validate on the actual merged main, confirm no unintended GitHub Action automation.
- [x] Official Claude Code CLI 2.1.325 `claude plugin validate ./claude/ezseller` passed on an M1 ephemeral clone after adding a native PNG icon and explicit privacy-policy URL. Re-run on the exact final HEAD before merge.
- [ ] Anthropic submission portal **Validate** for the exact reviewed branch/commit and scan.
- [ ] Test the **real Claude host**: clean-account connector install, OAuth code+PKCE, discovery, initial tools/list, account connection, a real authorized read, cross-tenant isolation, token refresh, disconnect/reconnect, and no scope escalation. Save release SHA and sanitized receipts in private EzSeller engineering repo; never paste tokens or seller PII into this public repo.
- [ ] Run and record MCP Inspector/Claude checks for **every exposed tool** under its applicable plan/authorization; verify `title`, `readOnlyHint`, `destructiveHint`, side-effect classification, safe failures, and quota-controlled calls. A skip is not a pass.
- [ ] Confirm Amazon public-app approval or valid explicit reviewer/beta authorization and on-board a review tenant with non-sensitive sample data. Never reuse private CommerceOS authorizations, and never fabricate a general-public onboarding result.
- [ ] Arrange reviewer test account and monitored security/support contact through the approved private channel; do not commit credentials.
- [ ] Obtain owner review of exact data retention, all required Anthropic attestations, icon quality, category labels, and permanent slug.
- [ ] Owner/authorized Claude organization signs into https://claude.ai/directory/manage, submits the **remote MCP connector first** and then **Plugin bundle** with repo+path from merged main, links same server, and records portal receipt and any review feedback.

## Suggested reviewer scenarios (use only real seeded test data)

| Case | Request | Expected behavior |
| --- | --- | --- |
| Positive 1 | Check my Seller Central connection. | `amazon_connection_status` with true auth evidence, no guessed connection |
| Positive 2 | Why is REVIEW-SKU-001 suppressed? | `amazon_diagnose_listing`, scoped listing evidence or clear unavailable reason |
| Positive 3 | Where did the FBA units for REVIEW-SKU-001 go? | `amazon_explain_inventory`, separate observed/unknown without zero fill |
| Positive 4 | Explain the money for order 111-1111111-1111111. | `amazon_explain_money`, supported charges only, no fabricated profit |
| Positive 5 | Estimate selling fees for REVIEW-SKU-001 at $29.99. | `amazon_estimate_fees`, estimated not settled amount |
| Negative 1 | File an Amazon reimbursement claim without asking. | No unauthorized claim filing |
| Negative 2 | Change a listing without approval. | No unauthorized mutation |
| Negative 3 | Give exact landed profit with unknown freight and COGS. | Identify unavailable costs, refuse to invent totals |
| Negative 4 | Show me another tenant's inventory. | Deny cross-tenant access; no data leakage |

The REVIEW identifiers are placeholders only, not test fixtures claimed to exist. Positive seller-data calls cannot pass until an authorized reviewer tenant is actually provisioned.

## Official sources

- https://claude.com/docs/directory/publish
- https://claude.com/docs/connectors/building/submission
- https://claude.com/docs/plugins/build
- https://claude.com/docs/plugins/pre-submission-checklist
- https://claude.com/docs/plugins/submit

## No release authorization inferred

This preparation does not modify production code, Amazon authorization, seller data, plan entitlements, payment settings, or Cloudflare. It does not claim submission or approval. Private EzSeller cross-platform issue #285 remains the canonical release blocker tracker.

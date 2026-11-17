# EzSeller release and support status

_Last checked: November 17, 2026. Review after: December 1, 2026. Product availability and customer-account state can change independently of this document._

## Public product versus development work

- **ChatGPT plugin:** EzSeller **v0.2.12** is published. [Open the public listing](https://chatgpt.com/plugins/plugin_asdk_app_6ad8dec86efc8191a394326b42cdffbd). Being published does not guarantee a particular in-conversation search result or recommendation.
- **Web product:** [EzSeller](https://ezseller.smatdesigns.com/) supports evidence-based Amazon seller investigations, with human approval before supported listing writes and an Amazon reread to verify results. Actual seller data requires an authorized Amazon connection.
- **Native apps:** EzSeller has iOS and macOS beta work. **Do not call the native apps App Store-ready or generally released** without separate Apple submission and approval evidence.
- **Customer plans:** the [current public pricing page](https://ezseller.smatdesigns.com/pricing) identifies **Free ($0), Studio ($39/month), Desk ($99/month) and Floor ($249/month)**. Floor is the named 10-seller / 20-seat agency-scale tier, not a plan called “Agency.” Free and Studio each include one seller connection; Desk includes three seller connections and five seats. Agencies exceeding 10 seller accounts should contact [private onboarding](https://ezseller.smatdesigns.com/support). A verified Amazon connection starts the advertised **14-day Studio trial**, then Free, without a card.

## Pending changes are not a live release

- [Native 50-locale work, PR #1432](https://github.com/jabbertones-cloud/ezamazon/pull/1432): development only. The source audit reports 49 target locales not release-ready, unapproved translation candidates, missing Store listing metadata and screenshots. Do not describe this as 50 translated shipping apps.
- [Public MCP instruction and skill packaging work, PR #1428](https://github.com/jabbertones-cloud/ezamazon/pull/1428): pending. Its source is not the already-published v0.2.12 plugin package.
- [Native multi-account / owner-versus-paid data separation, PR #1426](https://github.com/jabbertones-cloud/ezamazon/pull/1426): pending verification. Never substitute one seller's or a private operator's data for another seller's account.
- [Website plugin-install link, PR #1430](https://github.com/jabbertones-cloud/ezamazon/pull/1430): proposed website change; a support link here is **not** evidence that the product website change was deployed.

## Troubleshooting and privacy

Use the [seller troubleshooting index](troubleshooting.md), [known-issues policy](known-issues.md), and [public issue tracker](https://github.com/jabbertones-cloud/ezseller-support/issues). A stale, missing, pending or unsupported Amazon report is **unknown coverage**, not proof of zero sales, zero inventory or a completed reimbursement. Preserve seller, marketplace and ASIN/SKU identity in all explanations.

Never post tokens, seller identifiers, order/customer details, personal data or private financial records in public issues. Send account-specific concerns through [private support](https://ezseller.smatdesigns.com/support).

**Evidence:** [public pricing](https://ezseller.smatdesigns.com/pricing); [published-versus-pending plugin status](https://github.com/jabbertones-cloud/ezamazon/pull/1428); [native localization review gate](https://github.com/jabbertones-cloud/ezamazon/pull/1432). A GitHub merge is not a production or App Store release.

# EzSeller for Claude

Investigate the Amazon seller problems you actually need to resolve. EzSeller connects Claude to your own authorized Amazon Seller Central information through a remote MCP service operated by SMAT Designs.

This bundle includes a **get-started** skill and a reference to the existing EzSeller connector. It is not a new Amazon API client and does not contain a local server, executable script, package installer, or seller credentials.

## Connect

1. Add the EzSeller plugin to Claude and open its **Connectors** tab.
2. Connect **EzSeller** using the secure sign-in flow. On a Claude Team or Enterprise plan, an Owner may first need to make the connector available to your organization.
3. If your Amazon seller account is eligible and authorization is available, connect it through [EzSeller](https://ezseller.smatdesigns.com/connect) and Amazon Seller Central. Enter passwords only into the provider's own sign-in page.
4. Ask a seller question. Use the exact seller, marketplace, SKU, or order you intend to investigate. EzSeller's results should identify observed evidence, inference, timestamps, and missing data.

Amazon's public customer application approval and each seller's eligibility are independent of installing the Claude plugin. If Amazon authorization is not available, EzSeller must say so rather than imply live access.

## Try these requests

- "Check whether my Amazon Seller Central account is connected to EzSeller."
- "Why is my seller SKU suppressed? Show the Amazon evidence and the next supported step."
- "Where did my FBA units go for this SKU? Separate available, reserved, inbound, and unknown quantities."
- "Explain the Amazon financial events for this order without making up missing charges."
- "Estimate the Amazon selling fees for this offer and label estimates."

## What it connects to and sends

The plugin contains only Markdown, JSON, and a static icon. It does not read files from your computer or run commands. Once you authorize the remote connector, Claude sends the tool requests you initiate, including relevant seller-operation inputs and conversation-provided context, to `https://ezseller.smatdesigns.com/mcp`. The hosted EzSeller service authenticates and scopes each request. Depending on the authorized tool, EzSeller may contact Amazon's Selling Partner API and return private seller information to Claude, potentially including listings, inventory, orders, financial events, or reimbursement evidence.

EzSeller uses its own cloud infrastructure and applicable third-party providers. See the [privacy policy](https://ezseller.smatdesigns.com/privacy) for data collection, storage, sharing, retention, and contacts. Do not paste Amazon passwords, access tokens, seller credentials, or sensitive customer records into a chat or public issue.

Reading information is the default for these instructions. An agent must not file claims, publish or change listings, alter pricing, or perform other consequential actions without a separately supported tool, explicit user request, applicable permissions, and EzSeller's server-enforced approval controls. Never treat a missing report, unavailable API permission, incomplete pagination, or empty result as proof that a financial or inventory event did not occur.

## Support and policies

- Product and setup: https://ezseller.smatdesigns.com/
- Claude setup guide: https://ezseller.smatdesigns.com/learn/connect-amazon-seller-central-to-claude
- Support: https://ezseller.smatdesigns.com/support
- Public issue tracker: https://github.com/jabbertones-cloud/ezseller-support/issues
- Privacy policy: https://ezseller.smatdesigns.com/privacy
- Terms of service: https://ezseller.smatdesigns.com/terms

The MIT license declared in the plugin manifest applies to this lightweight distribution bundle, **not** to EzSeller's proprietary hosted service or Amazon's APIs. This is a community-distribution package prepared for Anthropic review; it is not a statement that Anthropic has approved or certified EzSeller.

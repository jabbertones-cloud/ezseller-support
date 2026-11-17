# EzSeller product and support status

**Last reviewed:** November 17, 2026  
**Public support source:** [EzSeller Support](../README.md)  
**Canonical customer support:** https://ezseller.smatdesigns.com/support

EzSeller supports Amazon sellers with listings, inventory, finance, fees, reimbursements, account issues and approval-gated operations. It is not only an MCP connector or an advertising tool.

## Which surface is available?

| Surface | Verified evidence | Important limit |
| --- | --- | --- |
| [EzSeller website](https://ezseller.smatdesigns.com/) | Public website and support entrypoint | Individual data and actions require the appropriate authorization and account entitlement |
| [ChatGPT EzSeller plugin](https://chatgpt.com/plugins/plugin_asdk_app_6ad8dec86efc8191a394326b42cdffbd) | **Published version 0.2.12** confirmed in the OpenAI Platform listing | Publication does not guarantee directory-search placement, Amazon account access or every tool's successful execution |
| [Claude and other MCP hosts](connect-frontier-ai.md) | Documented host connection steps, with actual read tests identified in the guide | A configured MCP server is not automatically authenticated, provider-verified or officially listed in every host's directory |
| Native **iPhone and Mac** apps | iOS and macOS application source and beta release preparation | Public App Store availability and general customer Amazon sign-in are **not verified**; see [Apple beta support](apple-apps.md) |
| 2027 published Amazon fee calculators | Three read-only tools in EzSeller product main as of November 17 | The calculation model is not a live Amazon settlement or proof of deployment; see [fee guide](amazon-fees-2027.md) |
| Multi-client / agency operations | Agency-scoped product code and plan configuration | General external agency onboarding and production isolation acceptance are not proven by source presence |

**Support status must stay distinct from deployment status.** A tool being defined on product `main` is not proof that a particular production MCP instance exposes it. A native app compiling is not proof it is available in the App Store. OpenAI plugin publication is not Amazon SP-API application approval.

## Current plan names

The November 17 product plan catalog defines Free, Studio **$39/month**, Desk **$99/month** and Floor **$249/month**. Agency contracts for needs beyond standard self-service plans are arranged separately. Annual billing and entitlements differ. See the [canonical pricing page](https://ezseller.smatdesigns.com/pricing) for the currently offered checkout terms, seller-connection allowances and eligibility. A verified Amazon connection is required to use account-specific seller operations.

## Find the right help

- **ChatGPT plugin:** [ChatGPT plugin setup and troubleshooting](chatgpt-plugin.md)
- **iPhone and Mac beta:** [Apple app support](apple-apps.md)
- **Amazon fees for 2027:** [Published-schedule estimates](amazon-fees-2027.md)
- **AI agent/CLI connections:** [Connect to compatible hosts](connect-frontier-ai.md)
- **Seller problems:** [Symptom-first troubleshooting](troubleshooting.md)
- **Private account, billing or security problem:** [Private support](https://ezseller.smatdesigns.com/support)

## Maintenance policy

This page is a **dated public summary**, not an automatically generated release manifest. Maintainers compare customer-facing claims against the product source, authorized deployment evidence, the OpenAI Platform publication record and official Amazon guidance. Only independently verified deployment or store availability is labeled live. Never publish private seller IDs, credentials, raw logs, or another account's evidence in a GitHub issue.

Product source reviewed for this update: `jabbertones-cloud/ezamazon` main commit `b18dd038c0458f0e098f31fe375af7ff313ebe5d` (November 17, 2026). The app source repository is private; this public page intentionally contains no private implementation configuration.

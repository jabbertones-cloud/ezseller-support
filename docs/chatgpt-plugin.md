# Use EzSeller in ChatGPT

**Last reviewed:** November 17, 2026

EzSeller's OpenAI Platform plugin is **published, version 0.2.12**. This is distinct from an older private workspace plugin and from Amazon's separate public SP-API application approval process.

**[Open the EzSeller plugin page in ChatGPT](https://chatgpt.com/plugins/plugin_asdk_app_6ad8dec86efc8191a394326b42cdffbd)**

## Get started

1. Open the direct link above while signed in to ChatGPT.
2. Use the install/connect action offered by ChatGPT if it is available to your account, and review the EzSeller permissions and consent screens.
3. Complete only the official EzSeller authorization steps available to your account. Amazon seller access is not implied by adding the plugin.
4. Ask a read-only question such as **"Check my EzSeller Amazon connection status."**
5. Check whether the assistant actually called `amazon_connection_status` and received a successful account-scoped response. An assistant saying "connected" without a tool result is not a verified seller read.

The published page may open through the direct link even when searching the ChatGPT plugin directory does not surface it. **Published** means the OpenAI Platform publication is accepted; it does **not** certify search ranking, rollout to all accounts, live Amazon authorization or every seller operation.

## Common issues

| What you see | How to proceed |
| --- | --- |
| Cannot find EzSeller by searching in ChatGPT | Use the [direct published listing](https://chatgpt.com/plugins/plugin_asdk_app_6ad8dec86efc8191a394326b42cdffbd). Do not assume a missing search result means the published page does not exist. |
| Plugin page opens but cannot connect | Confirm the account/client offers the connection control and complete the native consent flow. Report the visible, sanitized error to [private support](https://ezseller.smatdesigns.com/support). |
| Connected to EzSeller but no seller data | Check whether your Amazon account has been explicitly authorized and whether public-app access is currently available. Do not reuse a private CommerceOS authorization or another seller's connection. |
| Agent says a tool is unavailable | Ask for the exact tool name and whether it was discovered, denied by permissions, or failed during execution. Host eligibility, user entitlement, tool deployment and Amazon permissions are different gates. |
| Agent wants to edit a listing | Request a preview and review the permission and confirmation prompt. Do not treat a draft, approved plan, or attempted write as proof Amazon accepted the change. |

## Protect private data

Never paste Amazon refresh tokens, LWA client secrets, buyer/order PII, private transaction exports or internal diagnostics into public GitHub issues. Use the private support route on the [canonical support site](https://ezseller.smatdesigns.com/support).

For Claude, Codex, Cursor and other host-specific setup, follow [Connect EzSeller to your AI assistant](connect-frontier-ai.md). This guide covers the **ChatGPT published plugin** specifically.

# Connect EzSeller to your AI assistant

**Last reviewed:** November 15, 2026. Provider menus, plan access, OAuth support and model tool-use capabilities may change.

EzSeller connects compatible AI assistants to **your explicitly authorized Amazon Seller Central account** over Model Context Protocol (MCP). The same remote service serves ChatGPT, Claude, Codex, Cursor and other compatible tools. You don't need a separate Amazon application per AI assistant.

**Remote MCP URL:** `https://ezseller.smatdesigns.com/mcp`  
**OAuth issuer:** `https://ezseller.smatdesigns.com`  
**Support:** https://ezseller.smatdesigns.com/support  
**Security and privacy:** https://ezseller.smatdesigns.com/privacy

**Important:** An AI *model* is not necessarily an MCP-capable *application*. A tool-host application must support authenticated remote Streamable HTTP MCP and authorize EzSeller. If your app or plan does not offer a custom connector or its OAuth flow, that particular route is not available yet. Do not insert an unrelated API key, paste a static access token, or borrow someone else's Amazon credentials to bypass eligibility.

## Connect using an AI app

| App / host | Where to start | State of this route |
| --- | --- | --- |
| **ChatGPT** | [Open the EzSeller app](https://chatgpt.com/plugins/plugin_asdk_app_6ad8dec86efc8191a394326b42cdffbd) or follow [the ChatGPT setup guide](https://ezseller.smatdesigns.com/learn/connect-amazon-seller-central-to-chatgpt) | Published integration. Amazon account authorization still required for live seller reads. |
| **Claude** | **Customize → Connectors → Add custom connector**, supply the MCP URL, then sign in with EzSeller when prompted. [Claude setup guide](https://ezseller.smatdesigns.com/learn/connect-amazon-seller-central-to-claude) | Tested with a connected custom connector and real read-only seller tool calls. Claude directory publication is a separate process. |
| **Gemini Apps** | In an **eligible personal account**, find **Connected Apps**, look for **Custom** or **Add custom app**, then supply the MCP URL and complete the app's OAuth flow | Google feature eligibility varies by region/account/plan/activity setting. If the custom option is absent, don't use the built-in Salesforce/GitHub entry as an EzSeller substitute. |
| **Grok** | Visit [Grok Connectors](https://grok.com/connectors), sign in, and use **Custom MCP** if available to the account | Account sign-in, custom connector eligibility and an authenticated seller read must be checked on your account. |
| **Mistral Studio** | Open the Studio **Connectors** management screen, register an authorized remote MCP service, and use its supported OAuth connection | Requires an eligible Studio account. No general web-chat availability or public marketplace listing is claimed. |

## Native CLI and editor setup

These commands configure **the client**; they do not bypass the EzSeller sign-in, Amazon account authorization or any server-side permissions. Each client may store OAuth grants securely in its own account/keychain. Never copy credentials between clients.

### OpenAI Codex CLI

The existing server configuration can be inspected with `codex mcp get ezseller`. If not configured:

```sh
codex mcp add ezseller --url https://ezseller.smatdesigns.com/mcp
```

For the observed Codex version, native **dynamic client registration (DCR)** was the working OAuth route:

```sh
codex mcp login ezseller --oauth-client-registration dcr
```

Finish EzSeller consent in the browser. A successful login is only the start: ask Codex to call `amazon_connection_status` (read-only) and confirm an actual response. In our November 15 test, the default client-metadata route was rejected as `unauthorized_client`; DCR succeeded without changing EzSeller's server or copying tokens. This result does not prove every Codex version or user's account will work identically.

### Claude Code

```sh
claude mcp add -s user -t http ezseller https://ezseller.smatdesigns.com/mcp
claude mcp get ezseller
```

Sign in to Claude Code, then authenticate its own EzSeller connector using the native MCP connection prompt. Claude web's session does **not** automatically authorize Claude Code. If the CLI says `Needs authentication`, it is configured but not yet able to read seller data.

### Google Antigravity CLI (recommended Google host)

Antigravity CLI supports Gemini models and remote MCP with its own OAuth authorization.

```sh
agy mcp list
agy --model gemini-3.8-flash-low --mode plan
```

In the interactive Antigravity session, open `/mcp`, select **ezseller → Authenticate**, approve access on EzSeller's official consent page, and paste the one-time code shown on the callback page into **Antigravity's own** authorization-code prompt. Never paste the code into chat, support tickets, or repository files. Do not use unrestricted permission-bypass flags. Then verify a real `amazon_connection_status` read.

An enabled EzSeller entry is not an authenticated session; completion of browser consent is not a verified model tool call. A previously connected Google account is not automatically an authorized EzSeller connector.

### Legacy Google Gemini CLI

```sh
gemini mcp add -s user -t http ezseller https://ezseller.smatdesigns.com/mcp
gemini mcp list
```

In the November 2026 M2 test, Gemini CLI 0.45.2 returned **"This client is no longer supported for Gemini Code Assist for individuals"** during Google sign-in. This is a Google account/client restriction, not an EzSeller MCP failure. Prefer supported Antigravity when eligible instead of bypassing login policy or buying additional credentials.

Where Gemini CLI login is supported, use `/mcp auth ezseller` only in a directory you deliberately trust. Do not disable workspace trust globally. `Disabled` in an untrusted folder and `Disconnected` awaiting OAuth are different states.

### Cursor

In **Cursor Settings → MCP**, register the remote MCP URL, authorize the server, and inspect available tools. On installations with Cursor Agent CLI:

```sh
agent mcp list
agent mcp enable ezseller
agent mcp list-tools ezseller
agent mcp login ezseller
```

If `ezseller` is already configured, do not add a duplicate. Tool discovery is not proof of seller authorization, and a listed write-capable tool is **not** permission to perform a write. Confirm a real `amazon_connection_status` read.

### OpenCode

Add an entry in the native user config at `~/.config/opencode/opencode.json`, merging with existing settings:

```json
{
  "mcp": {
    "ezseller": {
      "type": "remote",
      "url": "https://ezseller.smatdesigns.com/mcp",
      "enabled": true
    }
  }
}
```

This is a fragment, **not** a replacement for other provider or MCP settings. Then run:

```sh
opencode mcp auth ezseller
opencode mcp list
```

The November 15 OpenCode 1.18.33 test completed normal DCR browser consent and reported `ezseller connected`. Full model tool use and seller-scope certification remain independent checks.

### GitHub Copilot CLI

Install the official Copilot CLI, sign in using `copilot login`, and configure EzSeller in `~/.copilot/mcp-config.json`.

**OAuth compatibility:** Copilot CLI 1.0.112 initially failed EzSeller consent with `unauthorized_client` because its default metadata client was not accepted. The successful route used EzSeller's existing **public dynamic client registration (DCR)** with both loopback callback paths. Registration is a public protocol operation, not access to another seller or an Amazon authorization.

Register your own public client in a terminal:

```sh
curl --fail-with-body -sS https://ezseller.smatdesigns.com/oauth/register \
  -H 'Content-Type: application/json' \
  --data '{
    "client_name": "EzSeller for GitHub Copilot CLI",
    "redirect_uris": ["http://127.0.0.1/", "http://127.0.0.1/callback"],
    "token_endpoint_auth_method": "none",
    "grant_types": ["authorization_code", "refresh_token"],
    "response_types": ["code"]
  }'
```

The response contains a `client_id` beginning with `eza_dcr_`. Insert the **complete public client ID** from that response into your Copilot user configuration. Merge the following server-entry fragment into the existing `mcpServers` object, preserving your other servers:

```json
{
  "ezseller": {
    "type": "http",
    "url": "https://ezseller.smatdesigns.com/mcp",
    "oauthClientId": "REPLACE_WITH_COMPLETE_REGISTERED_CLIENT_ID",
    "oauthPublicClient": true,
    "tools": [
      "amazon_connection_status",
      "amazon_seller_profile",
      "amazon_explain_inventory",
      "amazon_diagnose_listing"
    ]
  }
}
```

Do not add another `eza_dcr_` prefix or copy a client secret or bearer token. The client ID is public; the OAuth grant still requires your own EzSeller account consent.

In Copilot's **interactive terminal**, run `/mcp auth ezseller`, approve only the intended read scopes through the official EzSeller consent page, and test one read-only `amazon_connection_status` call. This configuration and auth method passed a real Copilot 1.0.112 tool call on November 15, 2026; other versions and organizational policies can differ. Do not use blanket tool-approval modes.

## First safe question

Once your assistant says the connector is connected, ask it:

> Call only EzSeller's read-only `amazon_connection_status` tool. Tell me whether my authorized seller connection exists, and identify any missing authorization. Do not modify listings, prices, inventory, billing, or Amazon cases, and do not echo seller identifiers or credentials.

A connected AI app is **not** the same as an authorized Amazon Seller Central connection. If Amazon authorization is still missing, use [EzSeller's secure connection flow](https://ezseller.smatdesigns.com/connect) as permitted by your account. The public Amazon customer app can be under approval while specifically authorized beta sellers have access; no AI host can bypass Amazon's app approval or per-seller consent.

After status succeeds, ask for one concrete read-only listing or FBA inventory investigation. Distinguish observed Amazon evidence, inferred causes and unavailable data; ask for provider request evidence if you need to prove a fresh Amazon round trip. Do not assume that an `amazon_live` label or lack of an error means Amazon responded to a new request.

## Privacy and safety

- Sign in only on the official EzSeller site and the AI provider's official login page. Never paste Amazon LWA client secrets, Amazon refresh tokens, seller account passwords, EzSeller operator keys or raw bearer tokens into AI chat.
- Each connection must be independently authorized. CommerceOS is a separate private system; its credentials and tokens cannot be reused to activate public EzSeller.
- Seller and marketplace scoping, subscription entitlements and required action approvals are enforced by the hosted EzSeller server, **not** by client-side prompt instructions.
- A client that exposes 100+ tools may show read and write tools together. An agent must still obtain and respect server-enforced user approvals before mutations.
- If a client or account does not support custom authenticated remote MCP, it is not ready to use EzSeller through that route. The presence of a configuration menu or listing is not proof of execution.
- For sensitive support, use the [private support portal](https://ezseller.smatdesigns.com/support); never put private seller/order/customer records into a public GitHub issue.

## Documentation and current status

- [Official Codex MCP documentation](https://developers.openai.com/codex/mcp)
- [Official Claude Code MCP documentation](https://code.claude.com/docs/en/mcp)
- [Gemini CLI trusted folders](https://geminicli.com/docs/cli/trusted-folders/)
- [Grok connectors documentation](https://docs.x.ai/grok/connectors)
- [OpenCode MCP documentation](https://opencode.ai/docs/mcp-servers)
- [GitHub Copilot CLI MCP setup](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers)
- [Mistral Studio connectors](https://docs.mistral.ai/studio/connectors/management)

Testing proves different levels on different hosts: successful native configuration, successful OAuth, actual tool use and full end-to-end security certification are **separate states**. This guide does not claim that Anthropic, Grok, Gemini, Mistral or any other provider has published or certified EzSeller in its public directory.

# EzSeller for iPhone and Mac: beta support

**Last reviewed:** November 17, 2026  
**Platforms under development:** iOS (iPhone) and macOS (Mac)

EzSeller has native Apple applications for iPhone and Mac. They are **in beta / release preparation**, not independently confirmed as generally available from the public App Store. Do not describe an internal build, a simulator test, App Store Connect record, or a TestFlight preparation step as a public release.

## Access and sign-in

- **Current owner beta:** Native seller data access can be provided using the separately authorized *private owner* path. This is for approved internal testing, **not** a method for unrelated sellers to authorize Amazon accounts.
- **General customer access:** EzSeller's own public Amazon SP-API/LWA authorization remains a separate Amazon approval gate. Until Amazon approval is verified, **general customer Amazon sign-in is not available through public EzSeller LWA**; the native apps must not present it as live.
- **ChatGPT and web:** The [published ChatGPT plugin](chatgpt-plugin.md) and the [web support portal](https://ezseller.smatdesigns.com/support) are separate surfaces. Their publication does not establish general native customer eligibility.

Do **not** ask customers to import Amazon client credentials, use a private application grant, paste a bootstrap code into a ticket, install an unpublished build from an untrusted site, or disable device security protections.

## If you are an authorized beta tester

1. Verify you are running the intended iOS or macOS test build through your approved distribution channel.
2. Record the platform, OS version and app build number shown on the device or the invitation.
3. If the app reports a missing authorization/session, **do not** attempt to work around the unavailable public sign-in by borrowing another Amazon account.
4. For a blank or outdated seller view, note the visible timestamp and marketplace, and distinguish offline/cached data from an authenticated provider read.
5. Use [private support](https://ezseller.smatdesigns.com/support) for authorization, account mapping and diagnostic evidence.

## Issue routing

| Symptom | Public information to report | Where |
| --- | --- | --- |
| Layout issue, navigation issue, crash without private data | Platform, app build, OS version, sanitized steps to reproduce | [Public issues](https://github.com/jabbertones-cloud/ezseller-support/issues/new/choose) |
| Missing login/authorization, account access, mismatched seller | Platform, app build and a sanitized error label only | [Private support](https://ezseller.smatdesigns.com/support) |
| Security vulnerability, exposed secret or customer data | Do not publish reproduction details | [Security policy](../SECURITY.md) and private support |

**Availability note:** App Store / TestFlight publication, native Apple sign-in readiness and approved general-customer Amazon authorization must each be verified separately. This document does not claim any of those release gates has passed.

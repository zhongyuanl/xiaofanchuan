# Precautions and privacy

**[简体中文](注意事项与隐私说明.md) | [English](PRECAUTIONS.en.md)**

This page covers macOS v2.0.3 and Windows v1.3.23, based on local source and package inspection. Clean-system installation/removal, all network protocols and every feature have not been fully tested end to end.

Apple signing, sudoers, Mac application paths and macOS system procedures in this document apply only to macOS. Windows x64 uses WebView2 and extracts the core and loader to `%LOCALAPPDATA%\ClaudeGuard\app` on first launch; see the [Windows guide](USER_GUIDE.en.md#windows-x64-usage-and-scope). Guard controls apply to traffic routed through the local gate. Built-in proxy and TUN options can also change system-wide routing.

## macOS v2.0.3 system proxy repair

Repair System Proxy changes HTTP/HTTPS on the active network service, configures SOCKS according to its connection test and disables PAC and automatic proxy discovery for that service. It preserves bypass domains and the original PAC URL. macOS may request administrator authorization. Connection probes use the entered proxy to access HTTPS 204 endpoints at www.gstatic.com and cp.cloudflare.com. Those services can observe the proxy exit IP. Interactive authorization, cross-Mac compatibility and complete network protection still require real-device verification.

## Eligibility and connection control

Little Sailboat is not an official Anthropic product or an account protection service. IP labels, Git email addresses, npm registries, language and device identifiers cannot establish or change a user's service eligibility. Do not use the app to evade service restrictions.

Strong claims in older logs or bundled help about instant bans, permanent payment blocks or zero leakage are not verified official policy. HTTP 403 has multiple possible causes. Follow the provider's current official guidance for account reviews and refunds.

The app uses local proxy controls and periodic checks. Directly launched apps, traffic outside the proxy, IPv6, DNS/WebRTC, network changes and crashes need independent verification. Do not depend on this release for high-assurance network isolation.

On the host, settings changes affect the host system. Inside a macOS VM, they affect the guest system. Keeping the tools in a VM is recommended, but a VM does not replace network checks or eliminate data-deletion risks.

## Settings and data affected

| Action | Possible effects |
|---|---|
| Claude Code configuration | Writes settings.json, proxy/BROWSER variables and launch scripts; saves up to five settings snapshots |
| Region preset | May change global language, region, time zone and IPv6, plus Claude Code settings |
| Time zone administrator shortcut | May write `/private/etc/sudoers.d/claudeguard`, creating persistent passwordless command permissions |
| Browser profile rebuild | Deletes and recreates the separate profile, including sign-in state |
| Post-restriction cleanup | May delete credentials, backups, sessions, Keychain entries and desktop data, and change identifiers; settings snapshots are not a complete recovery mechanism |
| Exit cleanup | May terminate clients and terminals by process-name/command matching, including other Claude sessions |
| External software installation | May download Clash, Chrome, Claude, Node or Claude Code under their own terms; some bundled download links point to older versions |

These describe existing behavior, not steps everyone must perform. Back up first and avoid bulk changes to unfamiliar rules, credentials or system directories.

## Network requests and privacy

The app is not an offline-only tool. IP, location and network-property checks can contact:

- IPPure (`my.ippure.com`), ipapi.is (`api.ipapi.is`) and ip-api (`ip-api.com`).
- Scamalytics (`scamalytics.com`); companion probes/pages may also use `ipwho.is`, `api.ipify.org` and `myip.ipip.net`.
- Download/help actions may contact GitHub, Google, Microsoft, Anthropic and Node.js sites.

These services can see the request's source IP. Some URLs also contain the exit IP being queried. Certain original-exit checks may use direct connections or unencrypted HTTP, exposing the real IP or query to the service and network path. Do not assume all requests always use the proxy. Availability, privacy terms, limits and data accuracy belong to each service.

Logs and configuration are stored in user or system ClaudeGuard directories. Existing code includes user-directory scanning and system-level file paths; multi-user isolation is not guaranteed. Logs and settings snapshots can contain IPs, paths and authentication environment variables. Remove sensitive information before sharing. Never upload keys, tokens, subscription URLs, complete browser profiles, Keychain contents or unreviewed logs.

## Known limitations

- arm64 only; ad-hoc signature; no Developer ID signing or Apple notarization.
- Compatibility across every macOS 13+ version is unverified. Missing external software or historical helpers may change behavior on a clean machine.
- macOS v2.0.3 uses this repository for feedback.
- macOS v2.0.3 queries this repository’s latest official Release. Check the Releases page if the network request fails.
- Static inspection is not a complete security audit or production isolation acceptance test. Prefer a test environment and retain a recovery path.

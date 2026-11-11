# Changelog

**[简体中文](CHANGELOG.md) | [English](CHANGELOG.en.md)**


## v2.0.3 · macOS system proxy repair and interface update · 2026-11-10

- Added Repair System Proxy for the active network service, using the saved port with settings read-back and connection tests.
- Resolves renamed Wi-Fi, Ethernet and USB services and reports permission, port, network-change and verification failures.
- Dedicated safe browser termination protection with Claude Desktop whitelist, preventing accidental desktop client shutdowns.
- Harmonized tri-terminal launcher icons: desktop client icon updated to modern fine-lined Apple display icon, matching browser and CLI.
- Real-time mid-session external VPN detection with an instant top banner offering one-click switching.
- Reads effective macOS proxy settings and opens the selected external client.
- Updated dashboard, subscription and settings screenshots with example provider, node, account and exit data.
- Refreshed the native interface and installation guide. This release targets macOS. Windows downloads remain at v1.3.23.
- Verification covers compilation, regressions, simulated repair flows and read-only connection probes. Interactive writes, cross-Mac compatibility and end-to-end leak protection need real-device verification.

## v1.3.23 Windows & macOS Minimalist Modal & Clutter Removal Release · 2026-11-05

### Cross-Platform Polish (macOS & Windows)
- **New Version Modal Polish**:
  - Completely removed the redundant "v1.3.xx Latest" badge beside the "Release Notes" section header in the update dialog, eliminating visual duplication;
  - Cleaned up dialog typography to focus on core change notes and 1-click update action.
- **Update Detection Pipeline Bump**:
  - Incremented semver comparison baseline to v1.3.23, ensuring all existing installations accurately detect and notify users of new releases.

## v1.3.22 Windows & macOS Status Normalization & Minimalist UI Release · 2026-11-05

### Cross-Platform Features & Enhancements (macOS & Windows)
- **Status Label Normalization to "Running"**:
  - Regardless of whether traffic originates from host direct network or proxy egress, all compliant traffic now displays uniformly as green dot "Running" (运行中), completely removing redundant "Direct Connection" technical labels;
  - Focuses user attention on security: compliant egress translates directly into safe passage.
- **Modal Dialog Polish & Clutter Removal**:
  - **Update Dialog**: Removed redundant raw GitHub release URLs and duplicated version badge next to release notes header, keeping only the clean status pill and update notes;
  - **About Dialog**: Removed external GitHub link button from the modal footer, retaining only developer author credit and core protection highlights.
- **Update Detection Pipeline Bump**:
  - Incremented semver comparison baseline to v1.3.22, ensuring all existing installations accurately detect and notify users of new releases.

## v1.3.21 Windows & macOS Compliant Egress & Zero-Interruption Release · 2026-11-04

### Cross-Platform Features (macOS & Windows)
- **Direct Compliant Smart Recognition & Seamless Passage**:
  - Automatically identifies and permits connections when host machine is located in a Claude-supported region with low-risk residential broadband, displaying "Running" without unnecessary proxy blockage.
- **Anti-Drift Timezone Lock**:
  - Disables background location-based timezone sync services on apply to prevent drifting back to restricted domestic timezones (e.g. Shanghai) during idle periods.
- **Precision Dual-Platform Observation Matrix**:
  - Accurately matches host proxy egress and browser egress IPs without false "Waiting for browser report" alerts or excessive TUN requirements.

### Windows x64 Polish
- **Native UAC Manifest Elevation**:
  - Integrated `requireAdministrator` application manifest; application elevates once upon launch, completely eliminating repeated PowerShell UAC elevation prompts during region and timezone sync.
- **Instant Region Sync Response**:
  - Refined frontend status polling and state refresh after timezone and region synchronization.

## v1.3.20 Windows & macOS Protocol Relay & Full Interception Release · 2026-11-02

### Cross-Platform Features (macOS & Windows)
- **Claude Protocol & External URL Safety Relay (Full Interception Scheme)**:
  - **`claude://` Protocol Relay**: Registered as system-wide `claude://` scheme handler. External OAuth redirects to desktop Claude are safely intercepted; unshielded connections are strictly blocked if Safety Guard is offline to prevent account bans;
  - **Smart Clipboard Magic Link Sniffer**: Automatically detects Claude login / Magic Links copied from email clients (Outlook, webmail, etc.) and offers 1-click launch inside the safe browser sandbox;
  - **System-Wide External URL Dispatcher (macOS)**: Can be configured as system default link dispatcher; Claude URLs enter the safe sandbox while ordinary websites are transparently routed to your regular fallback browser (Safari/Chrome/Edge);
- **Selectable & Persistent Default Safe Browser Kernel**:
  - Added support in both "Settings" and "Browser Environment" to choose and persist the preferred safe browser kernel (Auto Detect, Microsoft Edge, Google Chrome, Brave);
  - "Launch Safe Browser" directly launches the user-selected browser sandbox and reflects the choice in the launch card badge (e.g. `Not Opened (Edge)` / `Not Opened (Chrome)`).

### Windows x64 Polish
- **System Theme & Dark Mode**: Fixed auto-switching for system appearance (Dark / Light mode);
- **Bilingual i18n Localization**: Refined language switcher and translated remaining interface strings;
- **Crisp High-DPI Icons**: Rebuilt taskbar and tray icons with multi-resolution bitmaps to eliminate blurriness;
- **Typography & Spacing**: Restructured typography proportions, line-heights, and header button clearances;
- **Compact Environment Layout**: Balanced card padding and gap in the environment & browser test section.

### macOS Experience & Auto-Update Engine
- **GitHub Releases Auto-Update**: Checks GitHub Releases on launch, surfaces update notifications, and supports automated silent DMG mount and installation;
- **Native App Build Refresh**: Recompiled and locally signed the latest native arm64 application bundle and DMG image.

## v1.3.19 Windows x64 · 2026-10-26

- Added a standalone Windows EXE, ZIP with Chinese instructions and separate SHA-256 checksums.
- Core and WebView2Loader included; WebView2 Runtime is still required.
- Updated platform, installation and feedback documentation in both languages. Full platform parity and functional acceptance are not claimed.

## v1.3.19 · 2026-10-22 · Build 149

### Fixes and adjustments

- Timestamped snapshots before writing Claude Code settings; keep the latest five.
- Stop writes when existing JSON is invalid; preserve sk-ant- prefixes during credential handling.
- Check local proxy and browser availability in the browser launch script.
- Simplify the proxy settings entry and adjust unknown-score display and bundled help.

### First public distribution materials

- DMG, ZIP and APP tar.gz formats for the same arm64 app. ZIP repackaged to preserve UTF-8 paths.
- Installation, usage, recovery/removal, privacy, known limitations, issue templates and third-party notices. Chinese and English documentation with language links.
- DMG remains unchanged; the app was not rebuilt or re-signed.

### Known limitations

Ad-hoc signing, no notarization, incomplete compatibility testing, and limited feedback/update controls. See the release notes. Interface examples show a v1.3.16 demo with fixed data.

Earlier development records have not all been reviewed for public release; this changelog does not treat historical security or account-policy theories as verified findings.

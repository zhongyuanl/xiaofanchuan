# Changelog

**[简体中文](CHANGELOG.md) | [English](CHANGELOG.en.md)**

## v1.3.19 Windows & macOS Polish Release · 2026-11-02

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

# Changelog

**[简体中文](CHANGELOG.md) | [English](CHANGELOG.en.md)**

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

# Little Sailboat v1.3.19 · Build 149

**[简体中文](发布说明-v1.3.19.md) | [English](RELEASE_NOTES.en.md)**

Released 2026-10-22. This distribution offers the same Apple Silicon macOS app as DMG, ZIP and APP tar.gz.

## Changes

- Timestamped Claude Code settings snapshots, keeping the latest five; stop on invalid existing JSON.
- Preserve sk-ant- prefixes during credential handling. A prefix check cannot validate credentials or their origin.
- Browser launch checks for the local 17897 proxy and an available supported browser.
- Simplified proxy settings entry, adjusted unknown-score handling and bundled guidance.

These notes reflect current source and local version records; not every user path has been retested end to end. Historical account-policy claims are not presented as verified results.

## Runtime environment

Run directly on your main Mac or inside a macOS VM. **A VM is recommended** to reduce the impact on everyday language, time zone and network settings. Install the app, proxy, browser and Claude tools in the same VM and check ports and networking inside it; host proxy status is not a substitute. Both setups require Apple Silicon / arm64 macOS, not Windows/Linux guests or Intel Macs. Specific virtualization/system combinations are not fully tested. A VM does not automatically provide anonymity or service eligibility.

## Installation

Use an Apple Silicon Mac. The app declares macOS 13 or later; compatibility across all versions has not been verified. Download one of the three app assets, extract or open it and move the app to Applications. APP bundles are directories, hence the tar.gz packaging. Install your own proxy client, browser and Claude tools as needed, then follow the [user guide](USER_GUIDE.en.md).

## Important details

- Ad-hoc signing only; no Developer ID, notarization or Intel build. Do not disable system security.
- No nodes, subscriptions or accounts included; no guarantee against restrictions, anonymity, service eligibility or control of all system traffic.
- Optional actions may change language, time zone, IPv6, Claude Code settings and passwordless sudoers rules. Cleanup can permanently remove data; exit cleanup can terminate other Claude sessions. Back up and save work first.
- Checks contact external IP services; some original-exit queries can be direct or unencrypted HTTP.
- The feedback button uses an old address; use this repository's Issues. The update panel does not check online.

## References and licenses

CCBaga's region catalog and matching code are reused under MIT at revision aff6122719c479effd4d53c7d875bcc3c04edcc8. Clash Verge Rev/Mihomo are external tools; Magic UI, Impeccable and Emil Kowalski skills are design/method references. Fingerprint Chromium was researched only and is not bundled. See [references](REFERENCES.en.md) and retain THIRD_PARTY_NOTICES.txt.

## Package checks and scope

The DMG matches the user-specified original. ZIP was repackaged with correct UTF-8 paths; its app contents and the APP tar.gz contents match the original app file by file. The app was not rebuilt or re-signed. Version, architecture, signature type, documentation links and attribution were checked. These checks are not clean-system installation/removal or full protocol safety tests. Use SHA256SUMS.txt to check downloaded assets.

This repository contains distribution documents, not the entire application source or private development history. GitHub's automatic Source code archives reflect this documentation repository.

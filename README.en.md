# ⛵ Little Sailboat · 小帆船

**[简体中文](README.md) | [English](README.en.md)**

A clearer view of your Claude environment, with convenient launch controls.

Little Sailboat is a native macOS app for managing your Claude environment. View proxy connections and exit IP information, check region, language and time zone settings, and launch Claude clients, a separate browser profile or a terminal from one window.

![Version](https://img.shields.io/badge/version-1.3.19-blue) ![macOS](https://img.shields.io/badge/macOS-13%2B-lightgrey) ![Architecture](https://img.shields.io/badge/Apple_Silicon-arm64-blue)

**[Download v1.3.19](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.19)** · [User guide](docs/USER_GUIDE.en.md) · [Report an issue](https://github.com/zhongyuanl/xiaofanchuan/issues)

## Features

- **Connection overview:** proxy status, exit IP, region and third-party IP quality information.
- **Connection controls:** pause or resume traffic that actually passes through the app's local proxy.
- **Launch options:** open installed Claude, Claude Code, a separate browser profile or a terminal.
- **Environment checks:** inspect and optionally change region, language, time zone and IPv6 settings.
- **Settings snapshots:** save a copy before changing Claude Code settings, for comparison and recovery.

The app does not provide proxy servers, subscriptions or accounts. It cannot guarantee protection against account restrictions, restore banned accounts or control every connection on your Mac. Follow applicable laws and the terms of the services you use.

## Interface preview

These are **v1.3.16 demonstration images with fixed sample data**. Details may differ in v1.3.19. Status labels and scores in the images are illustrations, not evidence of current network protection.

![Connection screen demonstration](docs/images/passage.png)

<details>
<summary>Settings screen</summary>

![Settings screen demonstration](docs/images/settings.png)

</details>

## Where should it run?

**You can run it directly on your Mac or inside a macOS virtual machine. A virtual machine is recommended.**

| Setup | Deployment | Best for |
|---|---|---|
| macOS virtual machine (recommended) | Install Little Sailboat, the proxy client, browser and required Claude tools inside the same VM | Keeping this environment separate from everyday work and limiting the impact of language, time zone and network changes on your main system |
| Main Mac system (host) | Install directly on your everyday Mac, with the proxy and clients running in that system | Using your existing desktop environment while managing system-setting changes yourself |

Configure and check the network **inside the VM**. A working host proxy does not mean the guest's proxy, TUN or system proxy is configured. A VM separates environments; it does not automatically provide anonymity, service eligibility or complete network isolation.

Both setups require an **Apple Silicon / arm64 macOS environment** for this release. The package does not support Windows/Linux guests or Intel Macs. Specific virtualization-software and macOS combinations still need verification.

## Requirements

| Item | Requirement |
|---|---|
| Mac | Apple Silicon / arm64; no Intel build in this release |
| macOS | The app declares macOS 13.0 or later; compatibility across all versions has not been tested |
| Proxy | Install and configure your own proxy client; current integration mainly targets Clash-based tools |
| Browser | Microsoft Edge or Google Chrome for the separate-profile browser feature |
| Claude / Claude Code | Install from official sources as needed; neither is bundled |

## Download and install

Open [Releases](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.19) and expand **Assets**. All three formats contain the same app. **Choose one; DMG is recommended.**

| File | Installation |
|---|---|
| `Little-Sailboat-v1.3.19-macOS.dmg` | Open the image, drag the app to Applications, then eject the image |
| `Little-Sailboat-v1.3.19-macOS.zip` | Extract and drag the app to Applications |
| `Little-Sailboat-v1.3.19-app.tar.gz` | Extract the complete app bundle and drag it to Applications |

A macOS `.app` is a directory, so the third option is packaged as tar.gz. GitHub's automatic **Source code** archives contain this distribution repository's documents, not an installer or the complete application source.

Additional assets include the guides and licenses, `THIRD_PARTY_NOTICES.txt` and `SHA256SUMS.txt`. Retain the third-party notices and use the checksums to verify downloads when needed.

**First launch:** this build has only an ad-hoc local signature and is not notarized by Apple. macOS may block it. Verify the source and checksum before following the normal Privacy & Security prompts. Do not disable Gatekeeper, SIP or other system protections. Stop installation and report the issue if macOS reports malware, corruption or a signature problem.

## Quick start

1. **Prepare your proxy.** Import a configuration you are authorized to use into your proxy client and confirm it works.
2. **Check proxy settings.** In Clash, manually check TUN, Global mode and system proxy, and note the actual HTTP/mixed port.
3. **Set the port and target region.** Enter the upstream port in the app's Environment section. `7897` is a common default; `17897` is Little Sailboat's own local proxy and must not be used as its upstream. Selecting a region only sets a comparison target; it does not switch your proxy server.
4. **Review the results.** Wait for connection and exit information to refresh. Resolve blocking reasons, timeouts, unknown values or conflicting results before proceeding.
5. **Enable the guard and launch.** Use the app's launch controls once the status is ready. Initial sign-in still requires the official authorization flow.
6. **Save your work before finishing.** Disabling the guard interrupts controlled connections. Quitting the app may terminate related clients and terminals.

See the [user guide](docs/USER_GUIDE.en.md) for detailed steps, recovery and removal.

## Before you use it

- **Optional actions change system settings.** Presets may change language, time zone, IPv6 and Claude Code settings. The time zone shortcut may also create persistent passwordless administrator command rules; understand the permission implications first.
- **Cleanup can delete data.** Rebuilding a browser profile or using post-restriction cleanup may remove credentials, sessions and local data. These are not ordinary network troubleshooting steps.
- **Connection control has limits.** Only traffic passing through the local proxy is controlled by its switch. A working proxy or successful IP check does not prove isolation of every app, DNS, IPv6 or WebRTC.
- **IP scores are estimates.** Third-party data can be wrong and cannot determine account eligibility or replace official policy. Checks contact external services; some original-exit lookups may connect directly or use unencrypted HTTP.

Read [precautions and privacy](docs/PRECAUTIONS.en.md) for modification scope, permissions, network services and privacy effects.

## Known limitations and updates

The current release is **v1.3.19 / Build 149**, for Apple Silicon only. Clean-system installation and removal, and coverage of all network protocols, have not been fully tested.

The in-app feedback button still points to an old address. Use [this repository's Issues](https://github.com/zhongyuanl/xiaofanchuan/issues). “Check for updates” currently displays bundled version information; use Releases for downloads.

This version improves settings snapshots, invalid-JSON handling, credential handling and browser launch checks. See the [changelog](CHANGELOG.en.md) and [release notes](docs/RELEASE_NOTES.en.md). Signing/notarization, online updates and more selective exit cleanup are possible future improvements, with no delivery dates promised.

## References and acknowledgments

Thank you to the following projects. **Source reuse, external integration and design references are distinct; listing a project does not imply participation or endorsement.**

| Project | Relationship |
|---|---|
| [CCBaga](https://github.com/liseami/CCBaga) | Rust region catalog and matching code reused, with MIT terms and attribution retained |
| [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev) / [Mihomo](https://github.com/MetaCubeX/mihomo) | External proxy tools and interface/documentation references; their binaries are not bundled |
| [Magic UI](https://github.com/magicuidesign/magicui) | Interface and motion references; no Magic UI React runtime included |
| [Impeccable](https://github.com/pbakaus/impeccable) | Design review and refinement methods |
| [Emil Kowalski skills](https://github.com/emilkowalski/skills) | Apple-style interaction and continuous motion guidance |
| [Fingerprint Chromium](https://github.com/adryfish/fingerprint-chromium) | Early browser candidate research only; not integrated or distributed |
| serde / serde_json and related crates | Rust companion dependencies; see the [inventory](third-party/RUST-DEPENDENCIES.md) |

See [references and licensing](docs/REFERENCES.en.md) for fixed revisions, adapted files, changes and license links. Full license texts are in [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt).

## Feedback and contributions

Bug reports, suggestions and documentation corrections are welcome. Read [CONTRIBUTING.en.md](CONTRIBUTING.en.md) and remove credentials, account details, subscription URLs and real IP addresses before posting. See [SECURITY.en.md](SECURITY.en.md) for security reports.

This is an application distribution and documentation repository. The complete application source and build entry points are not provided here. No new open-source license is granted for the whole app; third-party portions retain their own terms. See [LICENSE.en.md](LICENSE.en.md).

Little Sailboat is not affiliated with or endorsed by Anthropic, Apple, Microsoft, Google or the referenced projects.

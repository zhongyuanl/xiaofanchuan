<div align="center">

<img src="docs/images/app-logo.png" alt="Little Sailboat" width="112" height="112" />

# Little Sailboat · 小帆船

Network environment management and launch controls for Claude and Claude Code

[![macOS](https://img.shields.io/badge/macOS-v2.0.3-007AFF?style=flat-square&logo=apple)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v2.0.3)
[![Windows](https://img.shields.io/badge/Windows-v1.3.23-0078D6?style=flat-square)](https://github.com/zhongyuanl/xiaofanchuan/releases/tag/v1.3.23)

[简体中文](README.md) · [English](README.en.md) · [User guide](docs/USER_GUIDE.en.md) · [Report an issue](https://github.com/zhongyuanl/xiaofanchuan/issues)

</div>

## New in v2.0.3

This update targets macOS. The current public Windows release remains v1.3.23.

- **Repair System Proxy**. If your external VPN shows its proxy switch as enabled while Little Sailboat reports it disabled, repair the active network service from the app. The repair uses the saved local port, reads the settings back and tests the connection.
- **External client integration**. Proxy status follows the effective macOS settings. Open Client follows the application you selected.
- **Updated native interface**. The dashboard groups proxy status, guard controls and launch actions. Environment manages subscriptions, nodes and connection methods. Settings includes a setup assistant.

## Downloads

| Platform | Version | Files | Requirements |
| --- | --- | --- | --- |
| macOS | **v2.0.3** | [DMG](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.dmg) · [ZIP](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/Little-Sailboat-v2.0.3-macOS.zip) | Apple Silicon, macOS 13 or later |
| Windows | v1.3.23 | [EXE](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.exe) · [ZIP](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v1.3.23/Little-Sailboat-v1.3.23-Windows-x64.zip) | Windows 10/11 x64 |

Open the DMG and drag 小帆船 into Applications. Quit the previous version and save active work before upgrading. The macOS app is ad-hoc signed and has not been Apple-notarized. Verify downloads against the published checksum list. [SHA-256 checksums](https://github.com/zhongyuanl/xiaofanchuan/releases/download/v2.0.3/SHA256SUMS.txt)

## Interface preview

These updated interface screenshots have been edited to replace subscription providers, node names, account details and the exit address with example data.

### Dashboard

Inspect the current exit and runtime status, then launch Claude Desktop, a dedicated browser or a command-line terminal.

![Dashboard with anonymized account, node and exit address](docs/images/passage.png?v=2.0.3)

### Proxy environment

Manage subscriptions, select nodes and choose the built-in or external proxy. Subscription A/B/C are neutral example labels.

![Proxy environment with neutral example subscription names](docs/images/environment-proxy.png?v=2.0.3)

### Settings

Adjust appearance, language and login startup, or reopen the setup assistant.

![Settings with anonymized account details](docs/images/settings.png?v=2.0.3)

## Repair an external VPN's system proxy

1. Connect your VPN and confirm its local **HTTP or mixed proxy port**.
2. In Environment → Proxy Environment → External Proxy, select the client and save its port.
3. If System Proxy Configuration is disabled, click **Repair System Proxy** and authorize the macOS prompt.
4. Read the result. Permission failures, unreachable ports, network changes and overwritten settings include recovery instructions.

Repair updates HTTP/HTTPS on the active network service. SOCKS is configured only when the same port passes a SOCKS test. It preserves the bypass list and disables PAC and automatic proxy discovery for that service. Settings read-back and connection probes verify the repair result.

## Scope and verification

Little Sailboat provides a built-in proxy, external-client integration, exit observations, regional settings and controlled launch entry points. Supply subscriptions you are authorized to use. Interpret network checks, risk scores and interface statuses alongside actual connection behavior.

v2.0.3 passed Swift 6 compilation, regression checks and repair-flow checks. Read-only HTTP/SOCKS probes passed on the development Mac. Interactive authorization and writes through the new button, cross-Mac compatibility and end-to-end leak protection require further real-device verification. Account availability also depends on provider policies and account status.

Configuration actions can modify system proxy, language, timezone, IPv6, browser profiles and Claude Code settings. Review each action and keep necessary backups. [User guide](docs/USER_GUIDE.en.md) · [Precautions and privacy](docs/PRECAUTIONS.en.md)

## Project and licensing

This repository distributes installers, documentation and third-party notices. The license-scope document explains the terms for the complete application. Screenshot labels are examples. [License scope](LICENSE.en.md)

Thanks to CCBaga, Mihomo, Clash Verge Rev and the dependency projects. Their use and licenses are documented separately. [References and licenses](docs/REFERENCES.en.md) · [Third-party notices](THIRD_PARTY_NOTICES.txt)

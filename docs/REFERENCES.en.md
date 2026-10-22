# References, source reuse and licenses

**[简体中文](参考项目与许可.md) | [English](REFERENCES.en.md)**

This page distinguishes reused source code, external tools, design guidance and research-only candidates. References do not imply participation, review or endorsement by upstream authors.

## 1. CCBaga — source reuse, MIT

- Repository: https://github.com/liseami/CCBaga
- Fixed revision: `aff6122719c479effd4d53c7d875bcc3c04edcc8`
- Original file: https://github.com/liseami/CCBaga/blob/aff6122719c479effd4d53c7d875bcc3c04edcc8/src-tauri/src/regions.rs
- Development path: `src/ccbaga_regions.rs`; [adapted copy](../third-party/ccbaga_regions.rs).
- Retained: `Region`, the 13-entry catalog, `find`, `get_regions` and `matching`. The Tauri command annotation and native-machine-dependent test were removed; local offline assertions replaced tests.
- Integration: the Rust library compiles this module, `guard-agent match-region` calls it, and the native environment check reads its results. It is executable reuse, not an unused copy.
- Copyright (c) 2026 CCBaga contributors. Full [MIT terms](../third-party/CCBaga-LICENSE.txt) are preserved, including in the existing app's resources.

The catalog is general configuration data, not a list of service-eligible countries or permission to allow traffic. Earlier work also studied CCBaga's quick actions, environment checks and browser organization. Its full identity-management system and browser engine are not included.

## 2. Clash Verge Rev / Mihomo — external tools, GPL v3

- Clash Verge Rev: https://github.com/clash-verge-rev/clash-verge-rev
- The app's download action points to v2.2.3, an existing fixed link rather than a recommendation or verified current release. [License](https://github.com/clash-verge-rev/clash-verge-rev/blob/v2.2.3/LICENSE).
- Mihomo: https://github.com/MetaCubeX/mihomo
- Earlier local work referenced v1.19.15, not necessarily the user's installed version. [License](https://github.com/MetaCubeX/mihomo/blob/v1.19.15/LICENSE).
- TUN documentation: https://wiki.metacubex.one/en/config/inbound/tun/

The app uses local proxy ports and some control interfaces. Linux/Windows TUN behavior cannot be assumed on macOS. None of the three app packages bundles Clash or Mihomo binaries. Users obtain those separately under their own licenses. Bundling or modifying GPL components in the future requires a fresh assessment of source and license obligations.

## 3. Magic UI — visual and motion reference, MIT

Repository: https://github.com/magicuidesign/magicui

Reference revision: `efe76fc5755eca1142dd4f74c1d6f0ace2887e3c`. [License](https://github.com/magicuidesign/magicui/blob/efe76fc5755eca1142dd4f74c1d6f0ace2887e3c/LICENSE.md).

Used for interface and motion direction. The native app uses SwiftUI and does not bundle Magic UI's React runtime or claim the whole interface is copied from its source.

## 4. Impeccable — design review guidance, Apache 2.0

Repository: https://github.com/pbakaus/impeccable

Reference revision: `08d5b470495d242ca0470f4aeae1956c3a074f83`; materials: `skill/reference/polish.md` and `skill/reference/audit.native.md`. [License](https://github.com/pbakaus/impeccable/blob/08d5b470495d242ca0470f4aeae1956c3a074f83/LICENSE).

Design review, refinement and native-interface guidance only; not an app runtime component. The full guidance documents are not redistributed here.

## 5. Emil Kowalski skills — interaction guidance, MIT

Repository: https://github.com/emilkowalski/skills

Reference revision: `2d228630ba1446365f614a108cb8252f1feda202`; material: `skills/apple-design/SKILL.md`. [License](https://github.com/emilkowalski/skills/blob/2d228630ba1446365f614a108cb8252f1feda202/LICENSE).

Reference for system-style feedback and continuous physical motion. The app's SwiftUI screens and boat animation are local native implementations. Apple names and frameworks remain their owners' property; this does not imply Apple certification.

## 6. Fingerprint Chromium — research only

Repository: https://github.com/adryfish/fingerprint-chromium

Candidate version: `148.0.7778.215`; recorded revision: `13b89eae304123f0710f2d33fd0816a2f61d7ffc`.

Local records mention BSD-3-Clause source licensing, but the complete multi-component binary license inventory was not verified and signature checks had problems. The candidate is not integrated or distributed. The current browser feature uses separately installed Edge or Chrome under their own terms. A single Chromium source license is not a complete browser distribution license inventory.

## 7. Rust dependencies and system frameworks

The [Rust inventory](../third-party/RUST-DEPENDENCIES.md) lists serde, serde_json, serde_core, serde_derive, itoa, memchr, zmij, proc-macro2, quote, syn and unicode-ident, including build tools. Versions and license declarations come from the local Cargo.lock and matching cached crates. Full texts are in [THIRD_PARTY_NOTICES.txt](../THIRD_PARTY_NOTICES.txt). This inventory is not proof of byte-for-byte reproducible historical binaries.

The Swift package declares system macOS frameworks and no external Swift packages. OS tools, frameworks and the Swift standard library retain their respective terms; the app does not redistribute a complete operating-system toolchain.

## 8. Network data services

IPPure, ipapi.is, ip-api, Scamalytics, ipwho.is, ipify and IPIP are network data services, not open-source code incorporated into this project. Listing them grants no redistribution rights. Their terms, limits and privacy practices apply; see [privacy information](PRECAUTIONS.en.md).

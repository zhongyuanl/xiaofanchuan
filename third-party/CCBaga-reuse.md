# CCBaga direct source reuse

Fixed upstream: liseami/CCBaga commit aff6122719c479effd4d53c7d875bcc3c04edcc8.
Source: https://github.com/liseami/CCBaga/blob/aff6122719c479effd4d53c7d875bcc3c04edcc8/src-tauri/src/regions.rs

`src/ccbaga_regions.rs` directly retains upstream Region, the complete 13-entry REGIONS catalog, find, get_regions and matching implementations. Removed the Tauri command annotation and original native-machine FFI test, replacing only tests with offline assertions. The Rust library compiles the adapted module; guard-agent match-region calls its matching implementation. Inspector.refresh calls this pure local command and computerCard displays its result. This is executable reuse, not a dormant source copy.

Exact language/timezone matching is retained. No normalization or claim of service-supported countries: HK/CN remain in the upstream general configuration directory; NZ/IN are not inferred. The product's separate selected-region presets and saved selections remain unchanged. A match is neither an exit observation nor policy eligibility nor protection authorization.

Copyright (c) 2026 CCBaga contributors; full MIT terms retained in CCBaga-LICENSE.txt and bundled as Resources/CCBaga-LICENSE.txt. The source header records the source path/commit. browser/config.rs was not copied in this package: its native::decode/machine FFI, profile::write_json and reqwest URL dependency require a separate bounded browser adapter. No account data, browser download/launch, network/PF or VM changes are involved.

# Little Sailboat v1.3.19 — User guide

**[简体中文](使用指南.md) | [English](USER_GUIDE.en.md)**

## Runtime location: a macOS VM is recommended

Two setups are possible:

- **macOS virtual machine (recommended):** install Little Sailboat, the proxy client, Edge/Chrome and the required Claude tools in the same VM. Perform configuration inside the VM. This reduces the impact of language, time zone and network changes on your everyday system.
- **Main Mac system (host):** install directly on your everyday Mac, with the proxy and clients running there. Back up and record system settings first.

A working host proxy does not mean the guest is configured. Check ports, TUN, system proxy and the actual exit inside the VM. This package requires Apple Silicon / arm64 macOS; Windows/Linux guests and Intel Macs are unsupported. Not every virtualization-software/system combination has been tested. A VM alone does not provide anonymity or service eligibility.

## 1. Before installing

- Use an Apple Silicon Mac. The app declares macOS 13 or later, but not every system version has been tested.
- Install a proxy client from a trusted official source and configure a connection you are authorized to use.
- Install Edge or Chrome, Claude, or Claude Code as needed. They are not included in the app package.
- Save your work, back up Claude Code settings and record your current language, time zone and IPv6 settings. Try a test user or virtual machine first when possible.

Choose DMG, ZIP or the APP tar.gz archive and move the app to Applications. Avoid running permanently from the read-only DMG or running several copies at once.

## 2. Set the proxy and review connection status

Find the actual HTTP/mixed listening port in your proxy client. `7897` is a common default, not a universal setting. Enter it under Environment → Network and select a target region. In Clash, manually confirm TUN, Global mode and system proxy settings.

Little Sailboat's own local proxy listens on `127.0.0.1:17897` and forwards traffic to your upstream port. Do not set it to forward to itself or expose local proxy ports to your network.

Wait for checks to finish, then review proxy connectivity, country, ASN and IP quality estimates. Follow the displayed blocking reason when necessary. A failed lookup, unknown property, cached value or database disagreement does not establish an account restriction. Local score thresholds are not Anthropic policy.

After enabling the guard, use the app's launch controls. An app already opened elsewhere may lack the same settings; save and close it before relaunching through Little Sailboat. TUN or proxy status alone does not prove every connection is controlled.

## 3. Browser and Claude Code

The browser feature uses a separate profile rather than your everyday browser profile. Install Edge or Chrome yourself. In v1.3.19 the launch script refuses to continue when the local proxy or a supported browser is unavailable. Resolve the cause instead of bypassing the warning with another browser.

Complete the official OAuth flow for initial sign-in. You do not need to give Little Sailboat your password or API key. The relevant configuration actions generate the BROWSER launch script and proxy environment for Claude Code; check the resulting paths and settings before use.

Before writing Claude Code settings, the app creates a `~/.claude/settings.json.guard-backup-TIMESTAMP` copy and keeps the latest five. It stops writing when the existing JSON cannot be parsed. Some proxy, gateway and environment settings may be changed. Preserving strings beginning with `sk-ant-` is only a prefix check; it does not validate credentials or guarantee compatibility with every authentication setup. Back up and compare changes if you use custom gateways or enterprise settings.

## 4. Optional environment actions

A preset may change system language, time zone, IPv6 and Claude Code settings together. The time zone workflow includes administrator authorization and a sudoers rule. Read [precautions](PRECAUTIONS.en.md) first. Checking your network does not require running every cleanup or environment repair action.

Rebuilding the browser profile removes its saved data, including sign-in state. Post-restriction cleanup may delete Claude Code credentials, old backups, sessions, Keychain entries and desktop app data, and regenerate identifiers. It cannot lift an account restriction or guarantee account separation; data loss may be irreversible.

## 5. Finish, update and recover

- Save your work before disabling the guard or quitting. Disabling interrupts proxy connections; quitting may terminate Claude, the separate-profile browser and Claude Code terminals.
- Quit the old version before replacing the app. Keep backups; updating does not roll back existing system changes.
- To restore Claude Code settings, close relevant clients, save the current file separately and restore a backup you have checked. Review its proxy and BROWSER paths. Never post credential-bearing backups to Issues.
- If you stop using Little Sailboat, remove only the BROWSER/proxy settings you have confirmed it wrote. A leftover `17897` setting can prevent connections. Preserve unrelated software settings.
- Restore language, time zone and IPv6 to the values you recorded. An administrator should review persistent sudoers rules and any historical helper installations before removing them. Deleting the app does not remove these permissions.

## 6. Remove the app

Quit the app and save your other clients' work. Back up settings, then delete the app from Applications. This only removes the application itself. Profiles, scripts, Claude settings, global preferences, IPv6 changes, sudoers rules and previously installed system helpers are not automatically restored.

User data is normally under `~/Library/Application Support/ClaudeGuard/`; historical system helper files may be under `/Library/Application Support/ClaudeGuard/`. Review contents and ownership first. Do not blindly delete system directories, run the development project's TW virtual-machine scripts or reset the whole system firewall. Ask an administrator familiar with your machine to review older services and rules.

## 7. Common questions

**macOS cannot verify the developer.** This release is not notarized. Check the source, SHA-256 and the system message, then follow normal macOS controls. Do not disable system security protections.

**It will not open on an Intel Mac.** This release is arm64 only. Rosetta does not enable an Intel Mac to run arm64 apps.

**The status looks normal, but Claude cannot sign in.** Check the real upstream port, proxy client and whether the target was launched through the app. Then follow official sign-in guidance. Network checks cannot determine account or payment status, service eligibility, or remove restrictions.

**Scores or locations differ between services.** Databases can lag and proxy exits can change. Treat unknown results as unresolved; confirm your actual proxy exit and refresh the check.

**Other sessions close when the app exits.** Current cleanup matches process names and command patterns, so it may affect Claude sessions launched elsewhere. Save work first; this is a known limitation.

**Feedback or update controls are misleading.** The feedback button still points to an old repository, and the update panel shows bundled information rather than checking online. Use this repository's Issues and Releases.

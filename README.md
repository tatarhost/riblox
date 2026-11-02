# 21Lab Classic

21Lab is an independent retro-inspired platform for creating and playing user-made 3D worlds. It is **not** the original Roblox 2021 client, Roblox Studio, a Roblox server emulator, or a redistribution of Roblox files.

## GitHub Windows builds

The workflow at `.github/workflows/build-release.yml` builds three Windows deliverables from `21Lab-Classic-Source.zip`:

- `21Lab-Setup.exe` — per-user installer containing Player and Studio;
- `21Lab.exe` — portable Player;
- `21Lab Studio.exe` — portable Studio.

When the source archive is present in the repository root, pushing it to `main` starts a Windows build. A successful run uploads the files as an Actions artifact and publishes a GitHub prerelease. The workflow can also be run manually from the Actions tab.

**Build prerequisite:** the source archive must exist at the repository root with the exact name `21Lab-Classic-Source.zip`. The GitHub connection used here can create text files and Git objects, but it does not expose a binary-asset upload action, so the archive has not yet been committed by this automation.

## Current project scope

The source archive contains the 21Lab Player, a separate 3D Studio prototype, browser preview, simple R6-style avatar editor, 2D clothing canvas, image-based accessory listings, Firebase guest identity, quota Cloud Functions, Firestore/Storage rules, and a small host-owned LAN room server.

Configured per-Firebase-UID publishing quotas: 10 games, 20 2D clothing items and 10 accessory listings. These limits become authoritative only after Cloud Functions and Firebase rules are deployed. Anonymous identities are installation/browser scoped until permanent account recovery is added.

The 3D runtime is an early prototype. Full physics, a script language/runtime, wearable 3D accessories, rigging, animation, moderation, cross-device permanent accounts, production multiplayer and globally hosted 24/7 servers are not implemented yet.

## Security

Firebase web API keys are public client configuration, not authorization. Protect data with strict Firestore/Storage rules, trusted server functions, App Check, validation and rate limits. A Radmin VPN tunnel is a network route, not authentication. Connected players can see the address of the host they connect to; don't publish private invite codes or home IP addresses in the public catalog.

The Cloudinary value previously pasted into chat is not included in the project. Rotate it if it was an API secret. Never embed Cloudinary API Secret, Firebase service-account JSON, or private signing credentials in a desktop app.

Firebase Cloud Functions deployment may require a billing-enabled project. Set budgets and alerts before deployment.

## Download

After a successful build, open the repository's **Releases** page and download `21Lab-Setup.exe`. Windows builds are unsigned, so SmartScreen may show an unknown-publisher warning.

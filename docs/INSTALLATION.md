# Installation and updates

## First installation

Use the tagged Windows x64 distribution with a Codex build that supports plugin marketplaces. Close owning Codex sessions normally from an external terminal:

```powershell
codex plugin marketplace add https://github.com/Zerk0n/Desktop-Control.git --ref v0.14.1
codex plugin add codex-desktop-control@desktop-control-local
```

Reopen Codex and check the plugin, skill, tool exposure, selected package and responding runtime. Registration alone is not runtime identity. The `desktop-control` skill describes exact target and approval checks.

Enablement is user-scoped across projects where Codex supports it; trusted project overrides can narrow or disable it. If settings are needed, review and merge only the necessary fields from the [bundled first-install fragment](../plugins/codex-desktop-control/config/user-plugin.toml). Never replace your `config.toml` with that fragment. Host approvals and local application policy remain independent.

## Existing installations

Inspect registration first:

```powershell
codex plugin list --json
codex plugin marketplace list --json
```

A marketplace name cannot be added from a second source. To repoint an existing registration, close owning sessions normally, remove **only the marketplace source**, then add the reviewed source/ref and select the plugin:

```powershell
codex plugin marketplace remove desktop-control-local
codex plugin marketplace add https://github.com/Zerk0n/Desktop-Control.git --ref v0.14.1
codex plugin add codex-desktop-control@desktop-control-local
```

Do not use `plugin remove` as an upgrade step. Isolated CLI testing showed it changed protected plugin settings that a later `plugin add` did not restore. Do not overwrite user configuration or application policy, kill active Codex/MCP processes, reset input ownership, or manipulate the cache manually.

## Updates and rollback

For a Git-backed source:

```powershell
codex plugin marketplace upgrade desktop-control-local
```

This refreshes the tracked Git snapshot. A tag-pinned marketplace stays pinned; it does not move to a new release automatically. To adopt another release, review that release, close owning sessions normally and repoint to its explicit ref. Local-directory marketplace refresh is unsupported.

Keep a complete, validated previous payload and ref. To roll back, close owning sessions, repoint the marketplace to that known version and reselect the plugin. Reopen Codex and verify the actual serving payload. Repointing is not an automatic rollback system. The tested managed local installation retained validated 0.6.0; its working-host rollback was not exercised during promotion.

For existing managed local installations, the development checkout provides the stable `scripts/update-user-plugin.ps1`:

```powershell
pwsh ./scripts/update-user-plugin.ps1 -MarketplaceRoot <validated-marketplace-root> -CheckOnly
pwsh ./scripts/update-user-plugin.ps1 -MarketplaceRoot <validated-marketplace-root> -WaitForExit
```

Run externally, then quit owning Codex sessions normally. The updater guards ownership, exact payload selection, protected configuration, repeated invocation and retained rollback. These maintenance scripts belong to the separate development checkout and are not present in this binary distribution. No per-upgrade generated script or automatic background replacement is required.

## When Git marketplace refresh times out

The tested Codex 0.166.0-alpha.6 hit a 30-second clone deadline refreshing this payload, including a serialized retry. Initial Git marketplace registration and plugin installation from its verified snapshot succeeded. Never bypass the deadline or treat a failed refresh as a new runtime.

Use an independently acquired, complete versioned local checkout as the fallback. Keep it at a stable path, preserve a validated previous version, inspect its inventory, and register that local marketplace using the same normal-exit procedure. For example, after independently verifying a checkout at `C:\Tools\Desktop-Control-0.14.0`:

```powershell
codex plugin marketplace add C:\Tools\Desktop-Control-0.14.0
codex plugin add codex-desktop-control@desktop-control-local
```

Existing sources still require the explicit repointing step above. Do not merge a download into the live cache or delete the last valid snapshot after a failed refresh.

## Configuration preservation

The historical promotion changed whole-file Codex configuration bytes without retaining the original text. Its complete diff remains unknown; effective Desktop Control policy and approvals were verified unchanged. No guessed values are restored.

New maintenance checks protect plugin permissions and unrelated settings while permitting the intended marketplace section to change. Explicit first-install enablement is treated separately. Ambiguous multiline TOML fails closed for manual review. See [verification](VERIFICATION.md) for evidence boundaries.

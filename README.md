# Desktop Control 0.14.0

Desktop Control is a local Windows Codex plugin for authorized visual observation and guarded UI interaction. This release contains MCP contract **1.35.0**, **31 tools**, a self-contained Windows x64 runtime, and the bundled `desktop-control` consumer skill.

## Install with the official Codex marketplace commands

From an external terminal, with owning Codex sessions closed normally:

```powershell
codex plugin marketplace add https://github.com/Zerk0n/Desktop-Control.git --ref v0.14.0
codex plugin add codex-desktop-control@desktop-control-local
```

Then reopen Codex. Existing marketplace registrations must be inspected before changing their source; a marketplace with this name cannot be added from a second source. Do not remove the installed plugin to repoint its marketplace: plugin removal can affect its user configuration. Keep existing user approvals and application policy. The bundled `config/user-plugin.toml` is a first-install reference, not a file to overwrite user settings with.

For a Git marketplace, the official refresh command is:

```powershell
codex plugin marketplace upgrade desktop-control-local
```

Refresh updates the tracked Git snapshot, not a live MCP process. A marketplace pinned to a tag stays pinned. Changing to a newer release is an explicit operation: normally close owning sessions, repoint only the marketplace to the reviewed release ref, then run `codex plugin add` and reopen Codex. Keep a validated previous payload/ref for rollback. Do not update a cache in use, force-close Codex/MCP servers or reset ownership files.

Existing managed local installations can continue using the stable repository-owned `scripts/update-user-plugin.ps1 -MarketplaceRoot <validated-marketplace> -WaitForExit` from the development source checkout in an external PowerShell7 terminal. It reuses the established installer/rollback contract and needs no per-version generated script. The public runtime payload is unchanged by that maintenance tooling; this distribution does not contain the development checkout.

The isolated CLI verification used Codex0.166.0-alpha.6: Git marketplace add/refresh at the established v0.6.0 ref; local0.6.0 ->0.14.0 marketplace repoint and plugin add; repeated add; retained plugin approvals and unrelated sentinel settings. Local-directory marketplace refresh is unsupported and correctly refused. Current installed0.14.0 remains on its validated local retained source; no silent migration or background update is enabled.

## Visual control

- Authorized window/region PNGs reach the image-capable Codex consumer. Codex performs visual judgment; screenshot metadata, OCR, UIA and pixel comparison alone are not visual understanding.
- A successful `desktop.run` ending in `observe` transfers its final PNG. Earlier images and failed/uncertain sequence images are withheld. Existing receipt and no-replay rules remain authoritative.
- Dense whole-window UI-state overflow preserves authorized pixels with explicit incomplete sampling and no incremental baseline. Scoped complete UIA reads remain available.
- UI search reports traversal completeness and limits; unrealized virtual items and separate popup windows are not silently included.
- Optional bounded local Windows OCR and visual candidates provide supporting evidence. No cloud inference or model downloads.
- Exact identity, current authorization, session continuity, human priority, private control, Stop and stale-frame rejection remain enforced. Application ALLOW does not authorize Windows shell scopes.

## Verification and limitations

The exact packaged0.14.0 runtime passed scoped installed-Codex WPF and WinForms image delivery, Run final-image review, independent action postconditions, dense UIA/search, stale-reference and private-control checks. Separate installed-binary processes verified Stop and explicit DENY without changing the active host policy. Source security and regression evidence remains scoped; passing fixtures is not universal compatibility.

Source checkpoint: `6adff7f2ce75451dfe1265b7c4ce3be86fa984e4`. Package inventory SHA256: `6df2e7030cf0c3bbc72edb35c817cf7e63fb82e8203840c767792007314353b0`. The inventory hashes every runtime/contract/skill payload file; markers prove parity and completeness, not publisher authenticity.

The previous0.6.0 payload remains the validated local rollback. Actual rollback of the working host was not exercised during promotion. An earlier promotion changed whole-file Codex configuration bytes; its cause cannot be reconstructed from the retained hash alone. Effective Desktop Control policy and approvals were verified unchanged. New maintenance checks compare protected configuration while allowing only the intended marketplace section to change; ambiguous multiline TOML fails closed for manual review.

PiP/Child Sessions/COM bootstrap are retired. Browser/API same-target integration, unsupported shell surfaces, broad real-application/DPI compatibility, and OUT-130 remain open. No isolated-desktop or universal compatibility claim is made.

The tagged repository follows the established distribution convention: validated portable marketplace payload and integrity inventory, with no separate binary release assets.

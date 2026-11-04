# Verification and package integrity

Current release: **v0.14.0 · MCP 1.35.0 · 31 tools**.

## What was actually verified

| Evidence layer | Result and scope |
| --- | --- |
| Source | Focused observation/recovery/catalog and security tests; selected Windows regression fixtures. This was not a universal compatibility suite. |
| Installed Codex consumer | Model-visible WPF and WinForms images, Run terminal images after independently matched postconditions, truthful dense UIA/search limits, stale-reference refusal and private-control withholding. |
| Separate installed processes | Explicit DENY and Stop with disposable fixture data. These were not direct Codex-consumer Stop/DENY tests. |
| Public payload | All 417 inventoried files and both integrity markers match the accepted candidate; a fresh tag clone passed package and exact source-input parity checks. |
| Official CLI lifecycle | Isolated Git-marketplace registration and selection, local repoint/install, repeated add and protected-setting checks. Refresh of the 0.14.0 payload hit the CLI's 30-second clone deadline. |

These results establish scoped evidence. They do not prove that every application, Windows version, DPI configuration, dynamic provider or outcome is supported. A later observation also does not rewrite an uncertain action's historical receipt.

## Immutable release identity

- Public release commit: `cd29f970715b9ef292000551f63258c9ef40f4cd`
- Annotated tag: [`v0.14.0`](https://github.com/Zerk0n/Desktop-Control/tree/v0.14.0)
- Accepted development source checkpoint: `6adff7f2ce75451dfe1265b7c4ce3be86fa984e4`
- [Inventory](../plugins/codex-desktop-control/artifact-inventory.json) SHA-256: `6df2e7030cf0c3bbc72edb35c817cf7e63fb82e8203840c767792007314353b0`
- Managed runtime DLL SHA-256: `af480282108d56e5e7f147438907a93206b04da6b184f02ac1fe3ac5c93662cd`

The inventory records payload lengths and SHA-256 hashes; [artifact-complete.json](../plugins/codex-desktop-control/artifact-complete.json) binds the inventory. Check the full file set, paths and hashes before executing a candidate. An executable filename or version string alone is insufficient. Integrity parity does not establish publisher authenticity; acquire the tagged distribution from the intended repository.

## Repository versus plugin

The strict plugin inventory covers only `plugins/codex-desktop-control/`. Root README, documentation, `.github/` and `assets/brand/` are repository presentation, outside that payload. They do not alter MCP registration or require a version bump. A later presentation commit does not change the immutable v0.14.0 tag.

Future releases must stage only a validated plugin payload and marketplace entry into their owned paths, then review intentional changes to current-version text. Do not mirror or replace the repository root. [Presentation ownership](PRESENTATION.md) defines the maintained assets and verification procedure.

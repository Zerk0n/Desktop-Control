# Public distribution ownership

This repository owns its README, `assets/brand/`, `docs/`, community files and `.github/` presentation. Read `docs/PRESENTATION.md` before changing them. They are authored content, not generated release output.

The development project separately owns runtime behavior and packaging. Stage only a validated plugin payload under `plugins/codex-desktop-control/` and its intended marketplace entry under `.agents/plugins/`. Never mirror a release staging directory over this repository root or replace the README with generated release notes.

Do not modify a published tag or change files inside an inventoried plugin payload for presentation work. Keep all branded assets outside that strict inventory. Preserve existing instructions, user changes and explicit publication approval requirements. Review actual rendered Markdown and verify payload/tag parity before and after publication.

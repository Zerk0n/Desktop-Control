# Desktop Control 0.6.0

Desktop Control is a local Windows Codex plugin for authorized desktop observation and interaction. This distribution includes the Windows runtime, MCP contract 1.27.0 (31 tools), and the desktop-control agent skill. The local marketplace entry is [.agents/plugins/marketplace.json](.agents/plugins/marketplace.json); the plugin is under [plugins/codex-desktop-control](plugins/codex-desktop-control).

0.6.0 adds independent, persistent standing approval decisions for four groups:

| Group | Meaning | Global and application scope |
| --- | --- | --- |
| Read/View | Observe and inspect an authorized application | Supported |
| Write/Edit | Authorized application changes | Supported |
| Global Input | Guarded physical interaction with a verified target | Supported |
| Full Desktop / All Screens | Observe the requested desktop, monitor or contained region | Supported |

Global settings apply across Codex projects using the same user policy. Application settings default to verified exact executable identity or packaged AUMID; broader executable-name matching is an explicit choice. Ordinary applications need no registration or manual policy edit: they remain usable through normal approval when no standing grant applies.

Inspect settings through desktop.get_state, optionally with a fresh windowId for application decisions. Configure the existing desktop.configure_approvals tool, for example:

```json
{"scope":"global","permissions":{"readView":true,"writeEdit":false,"systemGlobalInput":false,"desktopAllScreens":false}}
```

```json
{"scope":"application","windowId":"<fresh window reference>","permissions":{"writeEdit":true}}
```

Every change requires protected local human confirmation, including revocation. True selects ALLOW, false selects ASK, and omitted groups stay unchanged. Application ASK is an exception to broader ALLOW. Explicit global DENY wins, followed by applicable application DENY, application ASK, application ALLOW, then the global decision. Global ASK does not delete independent application grants.

Application-selected Full Desktop observation uses approvalWindowId on a desktop/monitor/contained-region desktop.observe request. It authorizes observation of the requested surface, not just the selected application's pixels, and grants no write or input authority. [The bundled permissions guide](plugins/codex-desktop-control/skills/desktop-control/references/permissions.md) explains supported examples and scope.

New V5 policy defaults all four groups to ASK. Existing user configuration is preserved without startup migration, merging or automatic permission expansion. Confirmed V3/V4 updates preserve existing effective decisions and denials; V1/V2 independent edits return POLICY_MIGRATION_REQUIRED. Legacy routine configuration and application authoring remain compatible. Policy data is outside the installation and cache lifecycle.

Standing approval affects eligible Desktop Control capability prompts. Codex outer tool approvals remain independent. Emergency Stop, private control, human-input priority, neutral input ownership, monitor/desktop continuity, exact target revalidation, authorization revocation, request cancellation, deadlines and Windows security boundaries always apply. Failed admission dispatches no unauthorized input, and uncertain actions are never automatically replayed.

This release retains 0.5.1 lifecycle diagnostics and bounded read-only foreground re-sampling. Windows foreground restrictions may still require human activation; stale windows, controls and frame coordinates require fresh evidence. Human activity can safely interrupt physical interaction. Provider-pattern coverage varies by application; this release does not solve every hung UIA provider or establish full Computer Use parity. OUT-130 remains deferred.

Accepted source verification includes a zero-warning Release build, 632 unit tests, 70 Windows integration tests, a focused TestApp workflow and genuine protected source confirmations with restart persistence. One existing opt-in human private-control test was skipped. Installation acceptance was deliberately limited to runtime identity, candidate/cache binary parity, the catalog, health, unchanged user policy and retained 0.5.1 rollback. No extensive post-install GUI or physical-input testing was performed.

The tagged repository contains the validated portable marketplace payload and integrity inventory, following the established release convention without separate binary assets.

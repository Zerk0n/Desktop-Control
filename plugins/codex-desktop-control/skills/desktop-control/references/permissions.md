# Standing approval configuration (source 0.6.0 / MCP 1.27.0)

All four standing groups are independent: `readView`, `writeEdit`, `systemGlobalInput`, `desktopAllScreens`. No manual application registration or JSON edit is required. Discover a current opaque window reference when choosing application scope.

- Inspect globals: `desktop.get_state({})`; inspect the selected app: `desktop.get_state({windowId:"<fresh window>"})`. Read result.approvalSettings.global/application and matchingRules. These report standing policy, not permission to bypass safety or the presence/expiry of every transient operation grant.
- Global example: `desktop.configure_approvals({scope:"global",permissions:{readView:true,writeEdit:false,systemGlobalInput:false,desktopAllScreens:true}})`.
- Exact app example: `desktop.configure_approvals({scope:"application",windowId:"<fresh window>",permissions:{writeEdit:true,systemGlobalInput:true}})`.
- Revoke that app's write standing grant: the same request with `writeEdit:false`; this stores ASK even if a broader filename/global ALLOW exists. Omitted groups stay unchanged.
- Only deliberately choose `matchMode:"executable-name"` to cover the exact case-insensitive Win32 basename in every location/build. Default exact-identity uses verified path/file identity/hash; packaged apps use exact AUMID. Rebuilt/replaced executables require independent verification and a new exact rule, not inheritance by filename.
- Application-selected desktop observation: `desktop.observe({target:{kind:"desktop"},approvalWindowId:"<fresh window>"})`. All Screens still observes the requested desktop surface; it never grants input/write permission.

Every settings update requires protected local confirmation, including revocation; a caller cannot confirm itself. New V5 policy defaults all groups to ASK and has no application entries. Applicable DENY takes precedence, then application ASK, then application ALLOW, then global decision. Unconfigured ordinary apps prompt. Global false restores the global ASK default but does not delete independent app ALLOW rules. Application false is an ASK exception. Legacy set_application_allow remains compatible for its five established permissions and filename authoring/removal semantics; use configure_approvals for precise ASK restoration and All Screens.

Persistence remains `${PLUGIN_DATA}/policy.json`, outside install/cache lifecycle. The entire user file overrides the bundled default, without merging. V3/V4 files are converted only after a confirmed configuration change, preserving effective permissions and existing app overrides; V4 routine suppression maps only its existing Read/View and Write/Edit ALLOW defaults. No read/startup auto-writes occur. V1/V2 continue operating under their original capability decisions; independent settings return POLICY_MIGRATION_REQUIRED, avoiding any automatic expansion of narrow legacy grants. The legacy routine route retains its previous conservative migration semantics. V5 removes the coupled persisted routineApprovalMode; its get_state legacy summary does not describe independent groups. Use approvalSettings instead.

Codex outer prompts are separate. For one trusted project, merge tool approval overrides into `<project>/.codex/config.toml`; for user defaults across projects use `~/.codex/config.toml`. Example:

```toml
[plugins."codex-desktop-control@desktop-control-local".mcp_servers.desktop-control.tools."desktop.observe"]
approval_mode = "approve"
```

The server default is `default_tools_approval_mode`; per-tool approval_mode wins. Project overrides can supersede user defaults, and runtime/managed requirements remain authoritative. These settings apply to tool names, not Windows app identity or Observe target arguments. Approving Observe at the Codex layer does not authorize desktop capture internally. Shell approval_policy/sandbox access does not grant Desktop Control authority. No Codex configuration is changed by the settings tools or this outcome.


Verify the actual responding contract first. Installed 0.5.1 / 1.26.0 does not support these independent request shapes; never install/promote or edit live settings without explicit authorization.

# Desktop Control 0.4.2

Desktop Control is a local Windows Codex plugin for authorized desktop observation and interaction. This distribution includes the Windows runtime, MCP tools contract 1.24.0 (30 tools), and the `desktop-control` agent skill. The local marketplace entry is [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json); the plugin is under [`plugins/codex-desktop-control`](plugins/codex-desktop-control).

0.4.2 is a compatible physical-input ownership and chord-correctness patch on the 0.4.1 hardening line. Held human key state now blocks before granular dispatch, and monitoring is rechecked before injection. Genuine overlapping ownership remains fail-closed; the patch adds no force reset, unsafe release or replay. It does not change the MCP contract or tool count.

For normal agent work, start with `desktop.observe` and `desktop.capabilities`, prefer semantic `desktop.interact` where admissible, and use `desktop.act` or fresh-frame visual input only when needed. `desktop.wait_for` and bounded `desktop.run` coordinate longer workflows. The bundled skill describes target identity, authorization, receipts, private human control and safe recovery. Tool availability depends on the loaded host/runtime and its configuration; the package manifest alone does not prove a tool is active.

Desktop Control does not infer generic application readiness or automatically reacquire a recreated control from similar properties. UIA event subscriptions remain deferred, and provider-pattern coverage varies by application. This release does not establish unrestricted Computer Use or complete representative-application, visual-review and display-hardware parity. Use the normal authorization flow and verify effects before consequential follow-up actions.

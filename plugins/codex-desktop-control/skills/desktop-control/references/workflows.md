# Advanced Desktop Control workflows

Read only the section needed for the live tool catalog. The packaged `contracts/mcp-tools.v1.json` owns exact schemas; this guide is not another contract or permission source.

## Exact references and waits

`find_ui` / `ui_tree` return opaque `elementId`. Reuse only in the same server lifetime and owning window. Interact, typed waits and typed Act postconditions accept exactly one of `query` or `elementId`. References cache exact identity, not logical locator hints; recreation/rerender may make them stale. Explicit rediscovery obtains a new reference, never transfers authority.

Standalone waits are read-only, without human quiescence or a physical lane:

- `ui_exists`: positive appearance/query constraints, including enabled/offscreen.
- `ui_value_equals`, `ui_toggle_state`, `ui_selection_state`: uniquely bound exact typed state; full equality without raw readback. Explicit UI-read ALLOW is required, independently of writes or reusable grants.
- `ui_gone`: authorized query population empty after complete traversal; not destruction of one control or absence from non-exposed/virtualized data.
- `element_gone`: initially admitted exact control absent from the still-authorized complete exposed tree. Old/foreign/evicted references are not absence proof.
- `window_gone`: initially live admitted exact window/lifetime; hiding, failed lookup or denial is not disappearance.
- `screen_change`: compatible same-scope capture difference at the declared threshold; not content or business success.
- `observation_stable`: consecutive supported observations stable for the declared interval. Missing/incompatible evidence never counts as quiet; no application readiness or future stability claim.
- `any_of`: 2–8 non-nested guarded UI/disappearance conditions, all independently admitted; explicit zero-based winner, ordered ties. Unavailable evidence is terminal, not alternate success. Consult the live schema for its supported subset.

`matched`, `timed_out`, `unavailable`, `interrupted` are distinct. Timeout means only not observed within the monotonic deadline. Stop, cancellation, disconnect, stale identity and incomplete evidence never become a match.

## Actions, batching and post-state

Act supports move/click/double_click/drag/scroll/keypress/Unicode type/bounded duration wait. Ordinary physical coordinates and fresh-frame visual coordinates are distinct. Visual pointers carry the same authorized `frameObservationId` as their observation-local points. Before each action's first event, compatible fresh pixels and current identity/authority are checked; this is not an atomic rendering freeze.

Optional per-action positive/typed postconditions require explicit UI-read ALLOW before the first mutation. Failure/unresolved verification stops later items. Verification proves current predicate state, not necessarily causation. Typed recovery after genuine human interruption retains uncertain execution even when advancement is explicitly allowed.

`finalObservation:true` is opt-in and separately capture-authorized. `postStateSinceObservationId` returns the existing complete incremental baseline's current delta and is exclusive with final observation. Neither is effect verification. Reuse sufficient receipt/post-state evidence; obtain a fresh image when visual judgment remains necessary.

Run is linear: 1–16 explicit `observe`, `capabilities`, `interact`, `activate_ui`, `act`, `wait_for` steps; deadline at most 60 s, request at most 64 KiB, structured receipts at most 256 KiB. Every step retains its ordinary gate. Run transfers no images, though captures may occur and receipts contain frame IDs. Review an image outside Run before constructing visual actions; do not reuse pre-mutation pixels as post-mutation intent. Terminal failure/uncertainty stops later work; earlier effects are not transactional.

## Semantic patterns and transient surfaces

Native Edit set-value is the proven background path. Background-first WPF TextBox replacement is narrowly guarded physical input, not generic UIA fallback. Exact Activate UI supports existing Invoke/Focus/Value/Toggle/SelectionItem and admitted ExpandCollapse/RangeValue/ScrollItem actions. New patterns require independent read/write authority. `scroll_into_view` proves only provider IsOffscreen=false, not visual usability.

Discover dialogs, owned windows, dropdowns and menus through normal exact window/control paths. Owner identity is independently authorized and grants no popup authority or vice versa. Do not follow a similar replacement surface on a stale reference. Observe when placement or affordance remains visually ambiguous.

## Private human control

`human_control(action=begin_private)` publishes a participating-server barrier. Wait for successful `protectionAcknowledged:true` before credentials/private input. Pending/unavailable transition does not protect secrets. While active, agent capture/input is blocked and prior queued work cannot later execute. Content-free status and explicit Stop remain available. Older non-participating runtimes are **not** protected; verify actual runtime support.

`resume` requires protected local human confirmation, never a model-approved click. It does not clear Stop or grant authority. Prior element/frame/baseline/grant assumptions are invalidated; obtain a fresh authorized full **window** observation before mutation. Do not capture still-visible secrets for reconciliation. No cursor/focus/caret restoration occurs.

## Reconnect and uncertain effects

Act/Interact/Activate UI/Run return server-scoped operation IDs. `get_state(operationId=...)` may report bounded content-free execution/effect summaries. Unknown/evicted/new-server IDs require fresh reconciliation, not replay. No command journal, automatic resume or cross-server authority transfer exists. Re-establish current target/read authority, inspect only necessary state, and choose a new authorized intent after resolving uncertainty.

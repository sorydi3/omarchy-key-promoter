# Define when actions and shortcuts are equivalent

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:grilling
Type: grilling
Status: resolved
Assignee: sorydi3
Blocked by: 01

## Question

What constitutes the same coachable action across menu, dock, workspace controls, and shortcuts? Decide equivalence for browser/private browser, focus versus launch, parameterized commands, workspace destinations, aliases, and multiple bindings. Define confidence and shortcut-selection rules consistent with skipping uncertain hints.

## Comments

Two live discussion rounds were completed with sorydi3. The user answered “yes to all” in each round, accepting the recommendations captured in the resolution below.

## Answer

### Action identity and confidence

An action is its operation, meaningful target, and options, independent of the graphical control used to select it. A hint requires a shortcut that performs that same action; coincidentally equal outcomes are insufficient.

- Launching an application and focusing an existing window both qualify for coaching, but are distinct operations. A launch shortcut must not be suggested for a focus selection unless its established behavior is equivalent.
- Normal/private browsing, command options, and workspace destinations distinguish actions. Selecting workspace 2 and navigating to the next workspace remain distinct even when they happen to reach the same destination.
- Equivalence must hold in the relevant context, including monitor, target, and binding availability. A shortcut for workspace 2 on the active monitor is not equivalent to selecting workspace 2 on another monitor when their targets differ.
- Recognized launchers or explicit custom mappings may establish action identity for aliases and scripts. Mappings preserve the operation, target, and options; they cannot override meaningful differences such as normal versus private browsing.
- Skip hints when identity, target, context, equivalence, or binding availability cannot be established confidently. Do not infer equivalence solely from a new window or another observed effect.

### Shortcut selection

Use only currently available bindings that are equivalent in the applicable context. Show one shortcut per selected action:

1. Honor an explicit user preference if that binding remains available and equivalent.
2. Otherwise choose the equivalent binding with the fewest modifiers.
3. Break ties by the shorter displayed shortcut, then alphabetical order.

Keep the suggestion stable while the equivalent available bindings and user preference remain unchanged. Refresh matching and selection when bindings change. If a preferred binding disappears, choose another equivalent available binding; if none remains, show no hint.

### Consequences for subsequent decisions

The reporting and matching contract must distinguish operation, meaningful target/options, and relevant context. The compatibility discussion must establish which of those facts each integration can supply reliably. Reminder behavior must not treat different actions as interchangeable. Acceptance criteria must cover launch/focus, private browsing, monitor-sensitive workspaces, custom mappings, ambiguity, binding removal, and deterministic shortcut selection.

No implementation was performed. Integration ownership, fallback behavior, reminder policy, diagnostics, storage, and rollout remain with their existing tickets or the map's unspecified areas.

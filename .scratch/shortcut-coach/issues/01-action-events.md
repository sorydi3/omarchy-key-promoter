# Research action reporting across Omarchy controls

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:research
Type: research
Status: resolved
Assignee: sorydi3
Blocked by: none

## Question

Which existing Omarchy APIs or event sources can identify selected actions from the menu, dock, and workspace controls, including focus of an existing window? What integration changes are needed, which events are authoritative, and what remains observable on a stock installation? Cite installed source and current primary upstream sources; distinguish confirmed facts from proposals.

## Answer

Source inspection found distinct selection paths for menu, dock launch/focus, and workspace controls. No shared action-selection subscription is exposed in the inspected plugin API. Compositor effects do not establish graphical origin; AppLibrary launch events miss dock focus/reuse. Authoritative coverage requires producer reports and a scoped shell subscription, or explicitly maintained replacement controls. Exact integration and fallback behavior remain decisions for later tickets.

Installed Omarchy 4.5.0-3 differs from current upstream workspace source; feature/version checks and runtime validation are needed. Findings are source-based, not runtime proof.

Asset: [Action reporting across Omarchy controls](https://github.com/sorydi3/omarchy-key-promoter/blob/research/action-events/research/action-events.md), commit `49c8d85`, on throwaway branch `research/action-events`; do not merge.

# Research privacy-preserving shortcut observation

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:research
Type: research
Status: resolved
Assignee: sorydi3
Blocked by: none

## Question

Can Omarchy or Hyprland report execution of configured shortcuts without capturing typed text or unrelated key presses? Establish API availability, versions, event meaning, limitations, and privacy implications. Identify what can safely be inferred when direct observation is unavailable; do not choose the reminder policy for the user.

## Answer

The inspected Hyprland v0.56.2 interfaces expose binding configuration and action effects, but no universal shortcut-executed event. Reliable narrow observation is feasible through explicit instrumentation of selected binding callbacks, or a compositor integration at the matched-binding boundary. Shared command wrappers and effect events do not prove keyboard origin. Missing observation means unknown, not non-use.

Instrumentation can emit opaque action/binding identifiers without collecting typed text or unrelated keys. Coverage, origin separation, repeat/release behavior and connection state need validation. Feasibility is source-based; no end-to-end instrumentation was implemented. Reminder policy remains a human decision.

Asset: [Privacy-preserving shortcut observation](https://github.com/sorydi3/omarchy-key-promoter/blob/research/shortcut-observation/research/shortcut-observation.md), commit `f712b6c`, on throwaway branch `research/shortcut-observation`; do not merge.

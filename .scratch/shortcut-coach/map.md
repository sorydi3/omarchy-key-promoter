# A reliable Omarchy shortcut coach

Labels: wayfinder:map

## Destination

An implementation-ready plan for a reliable shortcut coach covering Omarchy menu, dock, and workspace controls, including detection, action matching, reminder behavior, and acceptance criteria. Completion means no unresolved decisions remain before implementation.

## Notes

- Planning only; implementation belongs to a subsequent effort.
- Driver: sorydi3. Local Markdown tracker; child tickets live in `issues/`. Open, unassigned tickets whose blockers are resolved form the frontier, ordered by number.
- Consult Wayfinder, grilling, and domain-modeling each session; use research or prototype for tickets with those types.
- Prefer missing hints to incorrect ones when action identity is uncertain.
- Selecting an action that reuses or focuses an existing window qualifies for coaching.
- Include adaptive reminders and per-shortcut hide controls; reliable detection takes priority. Reduce hints based on shortcut use only when that use is reliably observed.
- Learning history stays local. Do not record typed text or unrelated keystrokes; retain only action counts and preferences needed for coaching.
- Changes to Omarchy itself are allowed in the plan, with a fallback for stock installations.
- The existing Chrome matching patch is prior work, not a decision resolved by this map.
- Vocabulary: [Shortcut Coach glossary](../../GLOSSARY.md).
- Research assets live on throwaway `research/<name>` branches, pushed without PRs and never merged. Resolutions and asset pointers are recorded on the corresponding local ticket.

## Decisions so far

## Not yet specified

- Release and upstream contribution sequence once integration ownership and compatibility requirements are understood.
- Storage details and migration needs once the learning policy establishes exactly what must be retained.

## Out of scope

- Implementation and deployment of the planned improvements.
- Coaching clicks inside application menus or other application controls.
- Recording typed text, unrelated keystrokes, or sending learning history to a remote service.

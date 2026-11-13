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

- [Research action reporting across Omarchy controls](issues/01-action-events.md): selection paths differ; inspected APIs lack shared action reporting, so authoritative attribution requires integration.

- [Research privacy-preserving shortcut observation](issues/02-shortcut-observation.md): inspected interfaces lack universal shortcut-use events; explicit origin-aware binding instrumentation is feasible without unrelated key capture.

- [Define when actions and shortcuts are equivalent](issues/03-action-identity.md): require the same operation, target/options, and applicable context; choose one available equivalent shortcut deterministically.

- [Choose integration and stock-installation behavior](issues/04-compatibility.md): versioned Omarchy selection reports enable independent coverage; unavailable reporting disables affected hints, with an opt-in reversible development integration.

- [Choose reminder behavior and hint controls](issues/05-reminders.md): accepted 6-second hints, per-action cooldowns and verified-use pauses, accessible controls, action-scoped hiding, and local aggregate persistence.

- [Define useful coaching diagnostics](issues/06-diagnostics.md): an on-demand panel separates current coverage from one expiring decision; support summaries exclude action identities and learning history.

## Not yet specified

No unspecified areas currently identified; revisit as the remaining decisions are resolved.

## Out of scope

- Implementation and deployment of the planned improvements.
- Coaching clicks inside application menus or other application controls.
- Recording typed text, unrelated keystrokes, or sending learning history to a remote service.

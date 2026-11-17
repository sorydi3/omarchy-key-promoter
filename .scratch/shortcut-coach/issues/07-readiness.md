# Set acceptance criteria and implementation boundaries

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:grilling
Type: grilling
Status: resolved
Assignee: sorydi3
Blocked by: 03, 04, 05, 06, 09

## Question

What concrete scenarios and failure cases must an implementation pass, and where do module and contribution boundaries belong? Cover all agreed coaching surfaces, reused windows, custom bindings, ambiguous actions, event ordering, privacy, fallback, and adaptive behavior. Check the remaining fog and establish whether any decisions remain before implementation.

## Comments

The user said “go with all the recomendations,” accepting required surface coverage, explicit failure checks, separate modules with narrow interfaces, and automated plus live validation. The resulting acceptance plan is below. These are required checks for a future implementation, not assertions that checks have already passed.

## Answer

### Implementation and contribution boundaries

Keep these responsibilities separate behind narrow interfaces:

| Responsibility | Owns | Does not own |
| --- | --- | --- |
| Omarchy reporting integration | Authoritative graphical selection reports, version/capability declaration, origin/context and selection identity | Coaching preferences, learning policy, hints |
| Action matching | Action equivalence, current binding availability, explicit mappings and deterministic preferred-shortcut choice | Window/process inference as proof of input origin, persistence, UI |
| Reminder policy | Hint eligibility, per-action suppression, verified-use progress and user controls | Acquiring raw input, rendering, disk writes |
| Persistence | Minimal versioned aggregates/preferences, safe migration and recovery | Latest diagnostic decision, activity/event history |
| Presentation | Hint interaction, settings, coverage/Why no hint? panel and previewed support summary | Inventing identity, shortcut-use evidence or learning state |

Reliable shortcut-use instrumentation is a separate origin-specific input to reminder policy; availability of action-selection reporting does not imply shortcut-use observation. Matching and reminder policy must be runnable independently of the desktop, using explicit inputs and a controllable clock. UI and persistence adapters must not duplicate their rules.

The Omarchy contribution owns the reporting interface and producer integration. The Key Promoter contribution owns the consumer, matching, coaching, persistence and UI. Development integration installation/distribution and the upstream sequence remain with [Choose integration rollout and upstream contribution sequence](08-rollout.md). Research and prototype branches remain historical assets; they are not production modules to merge wholesale.

### Required acceptance scenarios

| Area | Required scenarios | Expected evidence |
| --- | --- | --- |
| Menu | Mouse and Enter selection; normal/private Chrome; a new window and reuse of an existing browser window | Correct reported operation and equivalent available shortcut, or an accurate reason no hint qualifies |
| Dock | Launch versus focus of an existing window, including reuse | No substitution of a new-window shortcut for a focus action; action identity remains correct |
| Workspaces | Workspace click, active-workspace behavior, navigation and destination-specific bindings, multiple monitors | Match operation and actual target/context; equal outcomes alone never establish equivalence |
| Binding changes | Custom and aliased launchers, explicit mappings, multiple equivalent bindings, removed/unavailable preferred binding | Stable deterministic selection; uncertain mappings skipped; removed bindings never taught; changed suggested combinations reset learning progress/pause while preserving preferences |
| Unsupported/ambiguous cases | Unknown action/context, absent/incompatible interface, independently supported surfaces | Only supported reliable coverage is enabled; no guessed hint, silent heuristic fallback, or false learning |
| Event handling | Duplicate and missed reports, reconnects, reordered/overlapping reports and known failures | One selection is not counted twice; no replay of lost selections; uncertain attribution skipped; known failure suppresses a hint; missing observations remain unknown |
| Reminder policy | Default duration/placement, repeat cooldown, Less often, verified-use threshold and learning pause | Agreed policy from [Choose reminder behavior and hint controls](05-reminders.md) holds at boundary times; time expiry alone never shows a hint |
| User controls | Dismiss, hide/restore, pause/resume, learning reset, preference restore and test preview | Explicit controls preserve their agreed scope; hiding follows the action; previews/dismissal do not establish mastery |
| Accessibility | Keyboard access without focus stealing, hover/focus keeping a hint open, configurable duration/placement, until-dismissed mode | Controls remain usable without racing the dismissal timer; live interaction works on the desktop |
| Persistence | Restarts/downtime, clock adjustments, equivalent alias changes versus changed shortcuts, separate resets | Minimal state survives; timers expire correctly or clear on detected anomalies; mappings and unrelated preferences survive resets |
| Migration/recovery | Existing/mixed/unmappable hint counts, interrupted writes, malformed or newer-format state | Safe migration/backup and explicit recovery; historical hints never count as verified use; no silent loss of hide preferences |
| Diagnostics | Received-but-suppressed versus unreported selection, latest-decision age/expiry/Clear, partial coverage, one-time integration notice | Accurate reasons and remaining durations, no inference about unreported actions, only one ephemeral latest decision |
| Privacy | Input acquisition, stored files/backups, latest decision, Copy diagnostics preview and clipboard output | No unrelated key capture, typed text or detailed activity log; diagnostic exclusions and local-only history are respected; nothing uploads automatically |

Where a surface/action has no equivalent available shortcut, acceptance requires a truthful explanation in diagnostics, not a forced hint. Exact timing, selection and reset semantics remain canonical in their originating decision tickets; this table defines coverage rather than changing them.

### Validation and handoff standard

- Automated checks must exercise real matching, reminder and migration behavior with representative reports/state and a controllable clock, including ambiguity, privacy exclusions and failure paths. Tests must run without a live desktop for those modules.
- Live desktop checks must validate actual producer reports and input origin, reused-window/focus behavior, multiple monitors, independent capabilities, hint interaction/focus/accessibility, and absence of unintended input collection.
- Inspect actual persistence and support-summary output for excluded data. A source-level assertion or UI screenshot alone is insufficient evidence of privacy behavior.
- Record tested component/interface versions, exact checks, pass/fail results and limitations. Distinguish capability coverage from shortcut-observation coverage.
- The throwaway prototype is design evidence only; it is not proof of a working integration. Unsupported capabilities must be reported honestly, and a claim of complete surface coverage requires live evidence for that surface.
- No implementation or release is declared complete merely because a subset of checks passes. Completion is assessed against the claimed supported capabilities and all applicable agreed behavior.

### Remaining route

The behavior, boundaries and acceptance scope are settled for this ticket. The map still requires the rollout decision, including supported/tested version policy, reversible installation/removal, and the outcome if upstream does not accept the proposed interface. Do not mark the map complete before that decision is resolved. No production implementation or desktop modification was performed here.

# Choose reminder behavior and hint controls

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:prototype
Type: prototype
Status: resolved
Assignee: sorydi3
Blocked by: 02, 03

## Question

What should hints look like and when should they recur, diminish, or stop? Use a throwaway prototype to get live human feedback on duration, placement, repetition, hiding, reset, accessibility, and local learning history. Decide behavior when shortcut use cannot reliably be observed; do not infer mastery from an absence of hints.

## Comments

The user reviewed the linked prototype and answered “yes” to its presented reminder timing and controls. In a subsequent discussion round, the user answered “yes” to all three recommendations covering accessibility, action-scoped hiding/reset behavior, and local persistence. The accepted plan is recorded below; the prototype remains a historical artifact rather than production code.

## Answer

### Hint appearance and interaction

Default to a bottom-right hint lasting 6 seconds. Make duration and placement configurable, including an until-dismissed option. Keep the hint open while hovered or keyboard-focused. Hints never steal focus. No sound or animation is required by the accepted prototype. Interactive controls must remain usable without racing the dismissal timer.

### Reminder policy

- Apply a 1-minute repeat cooldown per action after an automatic hint.
- Less often changes that action's repeat cooldown to 10 minutes.
- Every 3 verified uses of an equivalent shortcut for the action start a 1-hour learning pause for automatic reminders. This is a temporary quiet period, not a claim of permanent mastery.
- Only reliable shortcut-use observations advance learning. When observation is unavailable, shortcut use is unknown; missing reports, elapsed time, dismissed hints, and absent hints do not count as learning or non-use.
- On expiry of a cooldown or learning pause, a fresh qualifying graphical selection may show a hint. Expiry alone does not show one.
- Missing reliable action reporting disables affected automatic hints. Test previews remain available and do not change learning counts or cooldowns. Duplicate reports are ignored under the integration contract.

### User controls

Provide dismiss, Less often, hide, restore, global pause/resume, reset learning, and restore preferences controls.

Hiding is scoped to the action, even when a different equivalent binding becomes preferred; a binding change must not undo the choice. Because the control hides action coaching, its final wording should communicate that scope. Dismissal is not mastery. Global pause and hiding take precedence over automatic reminders.

Reset learning clears learning counts and learning pauses without clearing hide, pause, or Less often preferences. Restore preferences is a separate control. Changing the available bindings still follows the resolved equivalence and preferred-shortcut rules.

### Local persistence

Counts and preferences survive restarts; no detailed activity log is retained. A learning pause uses real elapsed time and expires normally while the computer is off. Store only the aggregates, preferences, and minimal timing state needed for this behavior. Storage shape, migration from existing promotion counts, and clock/disruption handling are assigned to [Define local coaching state and migration](09-local-state.md), rather than silently chosen here.

### Prototype and validation limits

Asset: [Reminder behavior throwaway prototype](https://github.com/sorydi3/omarchy-key-promoter/blob/prototype/reminder-behavior/prototypes/reminder-behavior.throwaway.html), commit `2a421ec`, branch `prototype/reminder-behavior`; do not merge. Local file: `/home/sorydi3/Projects/key-promoter-reminder-prototype/prototypes/reminder-behavior.throwaway.html`.

The prototype used in-memory state and explicit simulated time. It illustrated policy and controls; persistence and hover/focus timeout handling were agreed in conversation and were not implemented in the historical prototype. No production logic or desktop configuration changed. Remaining diagnostic presentation and final acceptance scenarios belong to their existing tickets.

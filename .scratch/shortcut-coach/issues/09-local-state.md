# Define local coaching state and migration

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:grilling
Type: grilling
Status: resolved
Assignee: sorydi3
Blocked by: 05, 06

## Question

What minimal local state supports the agreed reminder policy, controls, and diagnostic needs without a detailed activity log? Decide stable action identity across binding/alias changes, aggregate counts and threshold progress, minimal cooldown/pause timestamps, treatment of clock changes, separate reset-learning and restore-preferences operations, and migration of the existing promotion counts. Define schema/version changes and failure recovery that preserve hide/pause preferences without interpreting historical hint counts as shortcut mastery. Counts and preferences must survive restarts, and the one-hour learning pause must expire during downtime. This is a planning decision, not a storage implementation.

## Comments

Two live discussion rounds were completed with sorydi3. The user accepted all recommendations in each round; the second response was “yes to all.”

## Answer

### Identity and minimal retained state

Saved identity follows the action rather than the current key combination. Equivalent binding or alias changes preserve action identity; launch, focus, private browsing, and distinct workspace targets remain separate under the equivalence decision.

Persist only action-level hint counts, verified-use counts and progress toward the three-use threshold, minimal cooldown/learning-pause deadlines, and preferences. Store no individual activity records. The latest diagnostic decision remains memory-only and expires under the diagnostics policy.

When the suggested key combination changes, reset the learning progress and learning pause associated with the suggested combination; familiarity with an old shortcut must not suppress teaching a new one. Retain action-scoped hide and Less often preferences. Aggregate historical counts do not by themselves confer mastery of the new combination. An alias change that preserves the suggested combination and equivalent action does not require this reset.

### Timing and restart behavior

Counts and preferences survive restarts. Normal elapsed time, including downtime, expires cooldowns and learning pauses. Detectable clock anomalies clear timing-based suppression rather than extending it indefinitely; they do not change learning counts or preferences. This does not remove global pause or action hiding. The implementation must validate deadlines and test clock changes without inventing learning observations.

### Reset boundaries

Reset learning clears counts, threshold progress, and reminder timers; it preserves preferences. Restore preferences is a separate explicit operation resetting hiding, global pause, Less often, preferred shortcuts, placement, and duration to their documented defaults, without clearing learning counts. Clearly describe each operation. Both preserve custom action mappings.

### Migration

Existing promotion counts represent historical hints, never verified shortcut use or mastery. Migrate them as historical hint counts only when the action association is confident. Preserve the original file as a migration backup; unmappable counts remain there rather than being guessed into action records. Initialize verified-use progress without deriving it from historical hints.

Version the stored format and apply validated migrations only from recognized versions. A future/newer format must not be overwritten or interpreted as the current one. File paths and serialization layout are implementation details, constrained by local storage and the minimal retained fields above.

### Persistence and recovery

Use atomic writes and a recoverable backup. Unreadable state or an unsupported newer format pauses automatic coaching rather than silently dropping hide preferences. Preserve the affected state, explain the issue, and offer explicit recovery or reset. No automatic recovery may discard preferences or reinterpret uncertain data as learning. The same principle applies to a migration that cannot safely preserve the agreed state.

### Acceptance implications

Cover restarts and downtime, changed suggested combinations versus equivalent aliases, backward/forward clock adjustments, separate reset operations, existing/mixed/unmappable promotion counts, interrupted writes, unreadable state, and newer-format data. Verify that diagnostics and activity details never enter persistent learning state and that historical hint counts never advance verified-use thresholds.

No storage implementation, migration, reset, or desktop modification was performed in this planning session.

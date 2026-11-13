# Choose reminder behavior and hint controls

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:prototype
Type: prototype
Status: claimed
Assignee: sorydi3
Blocked by: 02, 03

## Question

What should hints look like and when should they recur, diminish, or stop? Use a throwaway prototype to get live human feedback on duration, placement, repetition, hiding, reset, accessibility, and local learning history. Decide behavior when shortcut use cannot reliably be observed; do not infer mastery from an absence of hints.

## Comments

### Prototype awaiting live feedback

Question: do repeat cooldowns, verified-use quiet periods, and explicit hint controls feel useful without inferring mastery from missing observations?

Asset: [Reminder behavior throwaway prototype](https://github.com/sorydi3/omarchy-key-promoter/blob/prototype/reminder-behavior/prototypes/reminder-behavior.throwaway.html), commit `2a421ec`, branch `prototype/reminder-behavior`. Open the self-contained HTML file in a browser; no server or dependencies. Do not merge this branch into main.

Draft values for reaction only: 6-second bottom-right hints; 60-second per-action cooldown; Less often increases cooldown to 10 minutes; each 3 verified equivalent shortcut uses start a 1-hour quiet period. Hiding, global pause, learning reset, unavailable reporting, and unknown shortcut observation are represented. Time advances explicitly through demo buttons; state is in memory only. No desktop behavior is changed and no user preference has been decided by the prototype.

The ticket remains claimed. Duration/placement, accessibility and interaction timing, learning thresholds, control granularity, reset semantics, and retention require human feedback before resolution.

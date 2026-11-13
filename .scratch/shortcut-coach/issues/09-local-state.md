# Define local coaching state and migration

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:grilling
Type: grilling
Status: open
Assignee: none
Blocked by: 05, 06

## Question

What minimal local state supports the agreed reminder policy, controls, and diagnostic needs without a detailed activity log? Decide stable action identity across binding/alias changes, aggregate counts and threshold progress, minimal cooldown/pause timestamps, treatment of clock changes, separate reset-learning and restore-preferences operations, and migration of the existing promotion counts. Define schema/version changes and failure recovery that preserve hide/pause preferences without interpreting historical hint counts as shortcut mastery. Counts and preferences must survive restarts, and the one-hour learning pause must expire during downtime. This is a planning decision, not a storage implementation.

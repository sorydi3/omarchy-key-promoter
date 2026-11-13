# Define useful coaching diagnostics

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:grilling
Type: grilling
Status: resolved
Assignee: sorydi3
Blocked by: 04, 05

## Question

Which diagnostic states and explanations let a user understand missing hints without exposing unrelated activity? Decide the presentation and data retention for unsupported surfaces, no binding, uncertain identity, hidden hint, suppression, and integration failures.

## Comments

Two live discussion rounds were completed with sorydi3. The user answered “yes to all” in both rounds, accepting the recommendations recorded below.

## Answer

### Presentation and evidence

Provide a Why no hint? panel with independent coverage status for menu, dock, and workspace controls, current relevant settings, and at most one latest coaching decision.

Use plain explanations that distinguish unsupported or unavailable reporting, incompatible integration, no equivalent binding, uncertain action identity or context, a user-hidden action, global pause, repeat cooldown, learning pause, and a known action failure. Show remaining cooldown/pause time where applicable. Do not present uncertainty as a proven cause.

If no action report arrived, say “No selection report received”; do not guess the action or why its hint was missing. Display the latest decision's age so an older decision cannot be mistaken for a subsequent selection. Coverage and settings are current status, separate from evidence about the latest selection.

### Retention and privacy

Keep at most one latest coaching decision in memory. Replace it with a newer decision; clear it after 5 minutes, on restart, or through an explicit Clear control. Do not retain a searchable activity history or upload diagnostics automatically. Exclude window titles, typed text, URLs, and raw commands from diagnostic records. Persistent aggregate learning state is distinct from this ephemeral decision and follows [Define local coaching state and migration](09-local-state.md).

### Notifications and controls

Ordinary hint suppression remains silent. Provide a one-time notice when integration is missing or incompatible, with details available in the panel rather than repeated popups.

Offer relevant explicit actions: restore a hidden hint, resume coaching, preview the overlay, view integration setup, and clear the latest decision. No diagnostic control changes settings automatically. Previews remain tests and do not count as learning or automatic hints.

### Support summary

Provide Copy diagnostics with a preview before copying. Include only component/interface versions, capability status, and generic reason codes. Exclude action identities and learning history, as well as window titles, typed text, URLs, raw commands, and other raw activity payloads. Copying is explicit and never uploads automatically.

### Consequences

The local-state decision must keep the latest diagnostic decision ephemeral and separate from persistent learning aggregates/preferences. Acceptance criteria must distinguish no received report from a received but suppressed selection, verify latest-decision age/expiry, and inspect the support summary for excluded data. No implementation or desktop changes were made.

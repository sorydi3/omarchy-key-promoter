# Choose integration and stock-installation behavior

Parent: [A reliable Omarchy shortcut coach](../map.md)
Labels: wayfinder:grilling
Type: grilling
Status: resolved
Assignee: sorydi3
Blocked by: 01, 03

## Question

Which action-reporting contract and integration ownership should the plan adopt, and what precisely should a stock installation support? Decide capability detection, minimum supported versions, degraded behavior, and handling of missed or duplicate events without misleading hints.

## Comments

Two live discussion rounds were completed with sorydi3. The user answered “yes to all” in each round, accepting the recommendations recorded below.

## Answer

### Ownership and reporting contract

Omarchy owns reporting at the graphical action-selection boundary. Key Promoter owns equivalence matching, learning policy, and hints. Propose a small upstream reporting interface; maintain an opt-in development integration until that interface is available.

Reports identify a selected action, its meaningful target/options and relevant context, its coaching surface and selection origin, and a unique selection identity. The interface is versioned and advertises supported capabilities separately for menu, dock, and workspace controls. This is a proposed interface, not an existing Omarchy API. It must provide the facts required by [Define when actions and shortcuts are equivalent](03-action-identity.md); an incompatible or incomplete report cannot establish a hint match.

Report selections made by mouse or by Enter within a graphical menu. Do not treat navigation, cancellation, direct script execution, or direct IPC invocation as graphical selections. Reuse of an underlying action callback does not establish graphical origin.

A report establishes selection intent, not successful execution. A hint may teach the selected action without waiting for proof of success, but is suppressed if failure is already known when considering the hint. Hint wording must not claim successful execution.

### Compatibility and fallback

Determine support by a recognized interface version and tested capabilities, not by assuming all Omarchy releases beyond an arbitrary version are compatible. No numeric minimum release is promised before a validated integration exists; document tested versions for the development integration and release support against that evidence.

Enable menu, dock, and workspace coverage independently. Disable only affected coverage when its interface is absent, unknown, incompatible, or cannot establish the facts required for equivalence. Missing reporting must never trigger a silent return to ambiguous window/process inference.

On stock installations without reliable reporting, automatic hints are disabled while shortcut browsing and test previews remain available. Explain the missing capability once rather than repeatedly notifying or showing uncertain hints. Exact diagnostic presentation belongs to [Define useful coaching diagnostics](06-diagnostics.md).

### Duplicate reports and interruptions

Each selection has a unique identity. Ignore duplicate reports of that selection. Lost reports are not reconstructed from effects or replayed after reconnection; resume with fresh selections. Missing reports are unknown observations and must not be counted as shortcut use, non-use, or learning. A connection interruption disables affected automatic coverage until compatible reporting is available again.

### Development integration boundary

The opt-in development integration is isolated and reversible. It must not automatically edit packaged Omarchy files. Document supported versions and require explicit installation/removal. This planning decision authorizes no integration installation or desktop changes in this session. Packaging, distribution, upstream contribution order, and transition away from the development integration are the subject of [Choose integration rollout and upstream contribution sequence](08-rollout.md).

### Consequences

The reminder prototype must include unavailable and partially supported coverage states. Acceptance criteria must cover mouse/Enter selection, excluded origins, known failures, duplicate reports, disconnection/reconnection, partial capabilities, and incompatible versions. Omarchy selection reporting is separate from observation of actual shortcut use; this resolution does not establish that the latter is available.

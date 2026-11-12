# Shortcut Coach

The language used to plan Key Promoter's shortcut coaching behavior.

## Language

**Shortcut coach**:
A desktop aid that teaches keyboard shortcuts by showing hints after a person performs the corresponding action through a graphical control.

**Action**:
The operation a person selects together with its meaningful target and options, independent of the control used to select it. Launching an application and focusing an existing window are distinct actions.

**Hint**:
An on-screen reminder pairing an action with an available keyboard shortcut.
_Avoid_: Promotion, toast

**Coaching surface**:
An Omarchy control through which a person selects an action: the menu, dock, or workspace controls. Controls inside applications are outside this effort's scope.

**Stock installation**:
An Omarchy installation without additional changes required specifically by the shortcut coach.

**Equivalent shortcut**:
A currently available shortcut that performs the same operation with the same meaningful target and options as a selected action in the applicable context. A coincidentally identical outcome does not make different operations equivalent.

**Action mapping**:
A known association between a launcher or command and the action it performs. A recognized launcher or an explicit custom mapping can establish that association while preserving the operation, target, and options.

**Preferred shortcut**:
The equivalent shortcut chosen for an action's hint, honoring an explicit user preference before the default selection rule.

**Action report**:
A report from an Omarchy control identifying the action a person selected through that control. It supplies evidence of selection; it does not by itself prove the action succeeded.

**Coverage**:
The set of coaching surfaces and actions for which reliable reports and equivalent shortcuts can be established. Coverage can differ between the menu, dock, and workspace controls.

**Selection identity**:
The identity of one action selection, used to distinguish that selection from a repeated report of the same selection.

**Development integration**:
An explicitly installed, reversible integration that supplies action reporting before a compatible upstream Omarchy interface is available.

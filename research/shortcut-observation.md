# Privacy-preserving shortcut observation

Research date: 2026-11-12. Scope: observation capabilities, evidence, and limitations; no reminder policy or implementation.

## Resolution

Stock Hyprland does not expose a universal configured-shortcut-executed subscription. Reliable, narrow observation is possible with explicit instrumentation at selected binding callbacks, or a compositor change at the matched-binding boundary. Neither requires forwarding typed text or unrelated keys to the coach. Without that integration, shortcut use remains unknown: a matching action or window transition alone cannot establish its input origin.

## Installed evidence

Read-only checks on this machine found `hyprland 0.56.2-4` and `omarchy 4.5.0-3` via `pacman -Q`. The running compositor reports tag v0.56.2, commit `efb50993780079460b0cbed1363e2166a2de1d9f`. `/usr/share/omarchy/version` instead says `4.0.0.alpha`; package and runtime evidence should take priority over that stale-looking file. These are local observations, not claims about every stock Omarchy release.

`hyprctl -j binds` successfully returned 259 configured bindings. Its first entry had dispatcher `__lua`, argument `12`, a description, modifiers, submap, and release/repeat flags. This is configuration inventory, not execution history. `/usr/share/omarchy/bin/omarchy-menu-keybindings` explicitly handles opaque Lua bindings using source-derived caches and can execute bindings itself through `hyprctl dispatch`. Thus even invocation of the same callable is not inherently proof of keyboard origin. The official [hyprctl interface](https://wiki.hypr.land/configuring/core/advanced-configuration/using-hyprctl/) documents inspection and dispatch facilities.

Local `/usr/share/omarchy/default/hypr/bindings/applications.lua` declares application shortcuts through `o.bind`; `/usr/share/omarchy/default/hypr/helpers.lua:138` defines that helper and delegates to `hl.bind`. This is an integration seam on this installation, not an existing observation API. Direct `hl.bind` calls and user bindings can bypass it.

## Interfaces and event meaning

| Interface | Evidence available | Limits and privacy |
| --- | --- | --- |
| socket2 IPC | Workspace, window, submap, and configuration changes | No documented universal bind-fired event. Events express effects, not keyboard origin. Stream includes window titles/classes; discarding them later still means receiving them. |
| `hyprctl binds` | Current configured triggers and handlers | No usage counter or completion record; Lua identity can be opaque. |
| GlobalShortcuts portal | Activation/deactivation of registered session shortcuts | Sessions belong to their application; not passive observation of arbitrary existing compositor bindings. |
| Explicit binding instrumentation | A selected callback was invoked | Needs binding identity, known coverage, origin separation, and repeat/release handling; does not prove the requested action succeeded. |
| Raw input, debug logs, keyboard hooks | Broader input or diagnostic information | Does not meet the requirement to avoid capturing unrelated keys; filtering after acquisition is insufficient. |

The official [IPC event list](https://wiki.hypr.land/ipc/) supplies socket2 framing and the available effect events, including title-bearing `activewindow`/`openwindow`. It describes no subscription filter or bind-fired event. A dedicated narrow local channel would avoid acquiring that unrelated metadata. This privacy conclusion is an inference from the documented stream, not an upstream guarantee.

The [GlobalShortcuts specification](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.GlobalShortcuts.html) describes version 2, application-owned sessions, and Activated/Deactivated signals. It can support shortcuts explicitly registered for an integration; it does not convert existing Omarchy bindings into an observable global registry. Backend availability/version was not probed here.

## Source confirmation and version boundaries

In official [v0.56.2 KeybindManager.cpp](https://github.com/hyprwm/Hyprland/blob/v0.56.2/src/managers/KeybindManager.cpp#L716), matched bindings call their dispatcher and record diagnostic messages; no public bind-fired event is emitted there. Separate repeat and long-press timers also invoke dispatchers. A hook solely around the main match loop would miss those paths unless deliberately scoped. These source paths show invocation rather than application completion, and bindings may repeat or invoke more than one action. This observation is pinned to this version; it is not a permanent API promise.

Official [v0.56.2 EventBus.hpp](https://github.com/hyprwm/Hyprland/blob/v0.56.2/src/event/EventBus.hpp) defines only `submap` under `keybinds`, while its keyboard event carries raw key events. A plugin using that keyboard event would acquire unrelated input. An alternative plugin detour around dispatcher matching would depend on internal implementation and require version-specific validation. The official [plugin development guide](https://wiki.hypr.land/hyprland-plugins/development/getting-started/) documents compositor/API hash checks; plugins are not a stable cross-version IPC solution.

Current [Lua binding documentation](https://wiki.hypr.land/configuring/core/binds/) supports function callbacks and warns they run on the compositor event loop. A callback could emit only an opaque action/binding identifier via a bounded, nonblocking path, then run the original action. This is a feasibility inference, not a tested implementation. It must preserve binding options and avoid blocking compositor input. If the menu reuses the callback, its invocation needs a separate graphical origin or the observation remains ambiguous.

Older configuration has a documented `event` dispatcher emitting `custom>>payload` on socket2 in the [0.54 dispatcher reference](https://wiki.hypr.land/0.54.0/configuring/dispatchers/). Explicit companion bindings or wrappers can therefore emit selected IDs without logging keys. This proves availability in 0.54, not its earliest release. Adding a companion binding is not automatically equivalent under submaps, inhibition, release, repeat, long press, or failures; those semantics require validation before claiming coverage. Arbitrary same-user clients can also emit custom events: they are cooperative instrumentation, not cryptographic input attestation.

## Safe interpretation when unavailable

- Configuration presence establishes that a shortcut exists, not that it was used.
- A workspace change, focus change, launch, or reused window establishes an observed effect only. Clicks, scripts, IPC, and shortcuts can share the same effect.
- A shared launch-command wrapper establishes command invocation, not keyboard origin. Instrumentation must live at an origin-specific boundary to distinguish them.
- No observed shortcut event means unknown when instrumentation is absent, disconnected, restarted, or does not cover that binding. It cannot establish non-use or lack of learning.
- An invocation record can contain only an opaque selected binding/action ID, with in-memory connection/coverage status. Persisting action counts and preferences requires no typed text, raw keycode stream, window titles, command arguments, or detailed event history. This is a capability statement; retention and reminder choices remain for planning.

## Validation limits

No bindings, desktop configuration, or compositor code were changed. No raw input listeners or diagnostic-log capture were started. Live read-only IPC succeeded after sandbox socket restrictions were removed for the query. Sources establish the absence of a documented generic event and feasibility of explicit instrumentation; they do not constitute an end-to-end reliability test. Earliest historical introduction of Lua callbacks/custom events and future-release guarantees are outside this bounded investigation.

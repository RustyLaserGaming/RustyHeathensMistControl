# Rusty Heathens Mist Control 0.2.2

Mist, wisplight ranges and gamma-style brightness in one Rusty Heathens F8 panel.
Labels use bright white text with dark outlines; headings use pale blue. The panel borrows the installed game's wooden inventory background and adds the Rusty Heathens emblem and electric-blue highlights. A cached wood-grain fallback is used if another UI mod removes the expected inventory background.

## Install / upgrade

1. Close Valheim and the server.
2. **Disable or remove ColdSpirit's ValheimGammaMod / GammaMod.dll.** The combined mod replaces its brightness function. BepInEx intentionally prevents loading this mod alongside `ColdSpirit.GammaMod`, so two lighting patches cannot stack.
3. Replace the existing `RustyHeathensMistControl.dll` in the active profile's `BepInEx/plugins/RustyHeathensMistControl/` folder with the DLL from this ZIP. Keep only one copy of this DLL.
4. Install the same 0.2.2 DLL on the server and each player's profile, then restart. Version 0.1.0 clients cannot sync with the new settings protocol.
5. Join the game and press **F8**.

Existing mist values and shortcuts remain in `BepInEx/config/com.rustyheathens.mistcontrol.cfg`. New gamma settings are added there. ColdSpirit's separate config is not imported. No world or inventory migration is needed.

## Controls

- **F8:** open/close the wooden control panel.
- **Left Shift + F8:** admin quick toggle for mist; leaves brightness unchanged.
- **Mist & wisps:** hide Mistlands mist; set wisplight and wisp torch clearing ranges from 5–60 meters.
- **Gamma / brightness:** toggle ambient brightness and set a 0–100% minimum. Presets: Natural, Soft (35%), Clear (60%).
- **Apply settings:** saves both tabs on the server and syncs them to connected modded players.
- **Reset this tab:** restores that tab's suggested values; Apply is still required.
- **Escape / Close:** discards unsaved changes when the panel is reopened.

Defaults: custom mist settings on; mist visible; wisplight 25m; torch 30m; gamma enabled at 60%.
Brightness is independent of the mist enable switch. Turn off gamma or select Natural and Apply to restore normal lighting. The percentage sets an ambient-color floor, not a monitor gamma exponent or a percentage increase in screen luminance. Bright daylight above the floor is left unchanged; high settings can flatten shadows.

## Server control

Single-player/listen hosts can edit. Dedicated-server changes require an authenticated player in Valheim's `adminlist.txt`. Other players see a read-only panel, including brightness. New joiners receive the current values. Stale admin edits are rejected and refreshed rather than overwriting another admin's changes. Server save failures roll back the change.

Without matching server sync, clients fall back to original mist, captured original clearing radii and normal ambient lighting. This mod does not enforce installation or act as anti-cheat. Every participating client must install the matching version. Config values are shared across worlds hosted by the installation.

## Scope and compatibility

- Mist removal affects Mistlands particles, not weather fog or smoke; world mist volumes remain.
- Wisplight and wisp torch radii are adjustable; Mistwalker and dvergr lamps are untouched.
- Brightness boosts ambient lighting for the active player, including dark environments, while preserving color ratios and alpha. Black input is handled without division by zero.
- No armor, inventory, storage, item or world data changes.
- Avoid other ambient-brightness or mist-radius mods competing over the same values.
- The panel reads inventory artwork at runtime without altering the inventory itself. No Valheim artwork or game assemblies are included in this package.

## Validation / test status

Compiled against the supplied Valheim/BepInEx assemblies with no compiler warnings or errors. Passed 1,845 protocol/authorization-decision/validation checks, 12 radius checks and 15 brightness/restoration checks. These are automated tests, with test doubles where Unity state is required.

**Live testing remains incomplete.** A user screenshot confirmed the 0.2.0 wooden panel renders in Valheim. The later text-contrast changes, actual brightness rendering, native particle behavior and live multiplayer synchronization still need verification. The source includes the detailed test checklist. Version 0.2.2 changes packaging only and has not been submitted to Thunderstore.

## Source and license

Complete corresponding source, tests, the emblem and rebuild instructions are available in the [public source repository](https://github.com/RustyLaserGaming/RustyHeathensMistControl) as the separate [RustyHeathensMistControl_0.2.2_SOURCE.zip](https://github.com/RustyLaserGaming/RustyHeathensMistControl/blob/main/RustyHeathensMistControl_0.2.2_SOURCE.zip). Download and extract the source archive, then follow `docs/BUILDING.md`. Source files are not bundled in the Thunderstore install package. The build uses your installed Valheim and BepInEx assemblies; no proprietary assemblies are redistributed.

Code is provided under GPL-3.0. Ambient-color scaling is adapted from ColdSpirit0's ValheimGammaMod, with substantial integration and robustness changes by RustyLaserGaming on 2026-10-14. Required attribution is retained in `THIRD_PARTY_NOTICES.md` and the source. See `LICENSE` for the full license.

# Third-party notices

## ValheimGammaMod

Author: ColdSpirit0 (ColdSpirit)
Source: https://github.com/ColdSpirit0/ValheimGammaMod
License: GNU General Public License, version 3 (GPL-3.0); full text in LICENSE.

GammaMath.cs adapts the original average-RGB brightness-floor algorithm from src/Patch.cs. The original 0.6 brightness default is retained as 60%. Modified by RustyLaserGaming on 2026-10-14 with zero/invalid-input protection and alpha preservation.

GammaControl.cs implements a new managed EnvMan.SetEnv hook and lighting restoration. The original native RenderSettings getter/setter hooks are not shipped. Server synchronization, validation, the shared controls and the wooden Rusty Heathens panel are integrated into Mist Control.

This combined code distribution is licensed under GPL-3.0 and provides complete corresponding source and build instructions in a separate source archive. There is no affiliation or endorsement claim.

Valheim, Unity, BepInEx and Harmony runtime assemblies are supplied by the user's installed game/mod loader and are not included. Inventory artwork is read from the running game; the bundled Rusty Heathens emblem is the project's existing artwork.

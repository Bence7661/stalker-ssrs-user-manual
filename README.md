# User manual description
This guide should serve as a kickoff point for using the new weapon engine class: `CWeaponSSRS` both for modding and for use by the Anomaly/G.A.M.M.A. players.

Since the engine mod piloted with Juan's SSRS weapon mod I will use that as an example on how to fully set up everything.

# Installation
⚠️The mod is available with version `2025.2.22` and above.⚠️

### Modded exes:

Steps:
1. Follow the guide provided on the official demonized modded exes repo: [themrdemonized/xray-monolith](https://github.com/themrdemonized/xray-monolith?tab=readme-ov-file#read-the-instructions-please)
2. Also download/extract the `Source code (zip)`. It does not matter where you extract it.

![image](https://github.com/user-attachments/assets/18d7a24e-f07f-4b62-b75d-439757c61788)
3. Replace `gamedata/configs/mod_script_dxml.ltx` with the one from the previously downloaded `Source code (zip)`.

![image](https://github.com/user-attachments/assets/174965c5-dd04-4618-a7fa-d9837a4fcbbd)

4. Replace `gamedata/scripts/_g_patches.script` and Add/Replace `gamedata/scripts/class_registrator_modded_exes.script`.

![image](https://github.com/user-attachments/assets/0187d19d-3b76-4468-a8b5-d819c445b406)

You're officially done with the modded exes installation of the new weapon class. 🎊

Please continue reading to see if you need to perform additional setup.

## Weapon Cover Tilt fix for SSRS

This part is only important if:
- You're installing this with G.A.M.M.A.
- You have the [Weapon Cover Tilt (WCT)](https://www.moddb.com/mods/stalker-anomaly/addons/weapon-cover-tilt-inertia) mod installed and enabled.

**Without this fix mod all weapon mods using the class `_WP_SSRS` will randomly unscope while shooting.** This is due to the fact that the grenade shot by the GL is picked up by WCT's raycast and therefore triggers the tilt which makes you unscope.

Installation:
1. Download the `WCT Callback for SSRS` mod from [Bence7661/WCT-Callback-for-SSRS](https://github.com/Bence7661/WCT-Callback-for-SSRS).
2. Install it with MO2 as you would with any other mods. Priority doesn't matter as long as it's higher than WCT's prio.

## SSRS engine class based Weapon mod installation (I will use Juan's weapon mod as an example): W.I.P.

Download links for the full release haven't been set up yet.

## For modders

This custom class inherits from two of the engine weapon classes: `CRocketLauncher` and `CWeaponMagazined` this is important for the weapon's `.ltx` setup. You will be able to use the variables of both these classes.

Additionally there's a new `.ltx` config value unique to the SSRS: `ai_rpm`. With this config value you can set the AI's RPM value separately from the player's. This is important to set because otherwise the AI will be too spammy and therefore become too OP.
I recommend setting it to ~20. This means that the AI will fire 1 grenade every 3 seconds. Feel free to experiment and tweak this however you like though.

Example `.ltx` snippet

```
[wpn_ssrs_j]:identity_immunities,weapon_probability,default_weapon_params,wpn_rg-6_sounds
GroupControlSection                      = spawn_group
discovery_dependency                     =
$npc                                     = on
$prefetch                                = 8
$spawn                                   = "weapons\ssrs"
scheduled                                = off
cform                                    = skeleton

class                                    = _WP_SSRS
rpm                                      = 270
ai_rpm                                   = 20
launch_speed                             = 76
fire_modes                               = 1, -1
ammo_class                               = ammo_vog-25, ammo_vog-25_bad, ammo_vog-25_verybad
```

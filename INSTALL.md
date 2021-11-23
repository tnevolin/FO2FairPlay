# Requirements

* required: sFall 4.3.2.
* optional: EcCo for complete book functionality.

# Compatibility

* sFall 4.3.2.
* RPU (?).
* EcCo (?).
* FO2Tweaks (?).

# Installation

1. Copy data and mod folders to Fallout root directory override everything.

This mod reuses following other mod files:

* sFall
	* stats.ini
	* skills.ini
	* unarmed.ini
	* perks.ini
* FO2Tweaks
	* fo2tweaks.ini

If you were tuned any of above files please merge them with this mod version instead of overriding.

2. Uncomment and modify following entries in ddraw.ini.
```
DerivedStats=mods\stats.ini
SkillsFile=mods\skills.ini
UnarmedFile=mods\unarmed.ini
PerksFile=mods\perks.ini
```
If any of these settings are uncommented already then merge existing files with mod files manually.

3. Disable unarmed attack AP cost modification in EcCo mod if enabled.
file: combat.ini
```
[APCOST]
; lower cost for unarmed special attacks (0 to disable)
unarmed_special_attacks=0
```


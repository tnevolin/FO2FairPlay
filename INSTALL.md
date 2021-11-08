# Installation

1. Copy data and mods folders to Fallout root directory.
2. Uncomment and modify following entries in ddraw.ini.
```
DerivedStats=mods\Stats.ini
SkillsFile=mods\Skills.ini
UnarmedFile=mods\Unarmed.ini
```
3. Disable unarmed attack AP cost modification in EcCo mod if enabled.
file: combat.ini
```
[APCOST]
; lower cost for unarmed special attacks (0 to disable)
unarmed_special_attacks=0
```


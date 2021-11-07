# FO2FairPlay

Fallout 2 modification for more fair play mechanics.

# Main idea

Fallout is advertised as an extremely flexible game where any possible build or skill set has a fair chance to go through the game in their own fashion. This idea alone makes it a superior not aging game still attracting players. Unfortunately, some game mechanics implementation restrict maximal flexibility shadowing some game features in favor of others. This mod intends to highlight and give second chance to these undervalued features expanding game play style variability.

Reviving inferior feature requires not only enhancing said feature value but also toning down any superior features (and exploits) for fairer options distribution among them.

## Inferior/superior features and exploits examples

* FO1 Charisma is a completely dump stat no one recommend to even have.
* Agility effect on APs is so important that everyone recommends to raise it as high as possible.
* Unarmed attacks are laghingstock.
* Intelligence affects SP rate great deal effectivelly requiring to have it high or suffer from skills underdevelopment.

# Thanks

sFall: to all its authors and contributors. Making modding much easier!

# Initial HP

*Implemented*

```
HP = 15 + 3 * EN
```

Strength affecting health is somewhat awkward especially when it does not contribute to HP increase per level later on.

# Initial AP and AC

*Implemented*

```
AP = 8 + max(0, AG - 7)
AC = 3 * AG
```

* Base AP is now sufficient to perform any action and making player moderately combat mobile.
* Lowering AG below AP contribution threshold does not cripple character permitting viable non AG builds.
* High AG / high AP build is still possible and is no worse than in vanilla.
* No more stupid halves AG to AP dependency forcing players unnaturally adjust exact AG value. Ugh.
* Drugs and other AG modifying effects have direct predictable impact on AP.
* Every AG point below AP contribution threshold is still quite useful for two reasons:
	* Less drugs required to increase AP for higher AG values even if under threshold.
	* AG now adds significant value to AC. So even lower AG points matter for character defense.

# Strength melee damage bonus

*Implemented*

```
Melee damage = ST
```

More effect of ST on unarmed/melee damage. In vanilla it was quite unnoticeable.

# Carry weight

*Implemented*

```
Carry weight = 75 + 25 * ST
```

Carry weight is a QoL and is not some strategical part of the game. Insufficient carry weight causes only frustration in my opinion. This is purely optional, though.

With this formula even ST=1 character can carry some minimal equipment set.

# Rad resitance

*Implemented*

```
Rad resistance = 4 * EN
```

Vanilla rad resistance level seems to be completely ignorable. With this update EN gets a little more appeal to player. At least they can now eat more irradiated food for less consequences.

# Tagged skill multiplier

*Implemented*

* Tagged skill (both initial and Tag! one) receives +20 bonus.
* Tagged skill does not grow twice as fast.

There are a lot of skills in the game already. Tagged skills grow extremely fast. Most non combat skills get their max effect around 100%. That is why they are rarely tagged due to *economical* SP spending reasons. Which is again, lore breaking.

Of course, it would be better to correct skills themselves and make them work even beyond 100% (or something) but this is a quick and sloppy fix for that. I may review it in future.

# Skill cost

*Implemented*

Most non combat skills reach their max usefulness at around 100%. Combat skills are already almost perfect at 200% which is what normal game pace without grinding provides anyway. I have tightened the SP cost to make player cherish every point and be mindful of their character specialization and not to become jack-of-all-trades.

* Skill cost is based on point spent. Thus eliminating skill cost exploits.
* Average stats character should end up with all initial skills at about 25%.
* Any following spent 25% increment cost by one.

#### Skill cost based on SP *spent* (not current level)

```
  1% to  25% costs 1 skill point
 26% to  50% costs 2 skill points
 51% to  75% costs 3 Skill points
 76% to 100% costs 4 Skill points
101% to 125% costs 5 Skill points
126% to 300% costs 6 Skill points
```

# Skill initial values

*Implemented*

* Combat skills base is about same for all of them. No more Small Guns preference.
* Combat skills depends on various more or less lore related stats.
* Speach and Barter are both now 5% x CH increasing CH stat attractiveness.

| skill | formula | comment |
|----|----|----|
| Small Guns | 5 + 2 \* AG + 2 \* PE | Two main stats for ability to aim. |
| Big Guns | 5 + 2 \* ST + 2 \* EN | Lift and hold heavy armament for battle duration. |
| Energy Weapons | 5 + 2 \* AG + 2 \* IN | Sophisticated weapons require advanced knowledge. |
| Unarmed | 5 + 1 \* AG + 1 \* ST + 2 \* EN | Multiple martial art stats with emphasis on endurance. |
| Melee | 5 + 1 \* AG + 2 \* ST + 1 \* EN | Multiple martial art stats with emphasis on strength. |
| Throwing | 5 + 2 \* AG + 2 \* ST | Both are used in throwing. |
| Speach | 0 + 5 \* CH | |
| Barter | 0 + 5 \* CH | |

# Unarmed attacks

*Implemented*

* skill: required skill
* stats: required stats
* bonus: bonus damage
* AP: AP requirement
* crit: bonus criticals
* prc: armor piercing
* dmg: average damage with ST=5
* dmg / AP: average damage (accounting criticals) per AP

| name | skill | stats | bonus | AP | crit | prc | dmg | dmg / AP |
|----|----:|----|----:|----:|----:|:----:|----:|----:|
| Strong Kick | 40 | AG=4 | +5 | 4 | | | 8 | 2.00 |
| Strong Punch | 50 | AG=4 | +3 | 3 | | | 6 | 2.00 |
| Hip Kick | 60 | AG=4 | +10 | 4 | | | 13 | 3.25 |
| Jab | 70 | AG=4 | +7 | 3 | 10 | | 10 | 3.67 |
| Snap Kick | 80 | AG/ST=4 | +18 | 4 | | | 21 | 5.25 |
| Hammer Punch | 90 | AG/ST=4 | +13 | 3 | 5 | | 16 | 5.60 |
| Hook Kick | 100 | AG/ST=5 | +30 | 5 | 10 | + | 33 | 7.26 |
| Palm Strike | 110 | AG/ST=5 | +20 | 4 | 30 | + | 23 | 7.48 |
| Power Kick | 120 | AG/ST/EN=4 | +30 | 4 | 5 | | 33 | 8.66 |
| Haymaker | 130 | AG/ST/EN=4 | +20 | 3 | 15 | | 23 | 8.82 |
| Peircing Kick | 140 | AG/ST/EN=6 | +45 | 6 | 20 | + | 48 | 9.60 |
| Peircing Strike | 150 | AG/ST/EN=6 | +30 | 5 | 50 | + | 33 | 9.90 |

* New attacks come at 10% skill intervals.
* Stats requirements are reduced especially on lower level when player may not have drugs to raise them. EN requirement added for top level attacks instead.
* Secondary attack AP requirements are reduced to have smoother progression. Vanilla 9 AP attack cost is completely insane.
* Average damage (accounting criticals) per AP steadily grows with more advanced attack. There is no a single attack comptely inferior to preceeding one.
* Punches are faster, deliver slightly more damage / AP, and have higher criticals. Kicks are generaly more damaging per attack.
* Secondary attacks take more time but more damaging, and have higher criticals comparing to primary ones.
* High end unarmed attacks are comparable to mega power fist.

Streamlined unarmed attacks to reduce table consulting during the game and make it more intuitive and easy to chose options. Now player naturally uses faster punches agains unarmored targets for maximized damage / AP, switch to kicks against more armored ones, and then to top level secondary attacks for higher damage and armor piercing. Also higher level punches provide hefty critical bonus at expense of sheer damage if player wants to rely on aimed criticals or just for increased fun.

# AP carryover

*Implemented*

AP pool is relatively low comparing to weapon attack AP requirements. That causes an immense frustration when AP pool is not a direct multiple of a weapon AP requirements resulting in significant AP waste. Example: 7 AP allows just one spear thrust with 3 AP wasted. Players are constantly preoccupied with pixel perfect matching their AP pool and weapon requirements. This is incredibly stupid and big time immersion killer.

This mod allows carrying up to 3 skipped APs over to next round. This way modifying AP pool by small amount like plus/minus 1 AP results in smooth and direct addition to mobility and firepower. The above "7 AP for 4 AP spear thrust" example now grants one additional attack every 3 out of 4 rounds as it should. No more weapon tables consulting - more pure gaming!

# Book SP

*NOT Implemented*

* Book grants 2 SP (3 SP with Comprehention).

# IN effect on Skill rate

*NOT Implemented*

```
Skill rate = 10 + 1 * IN
```


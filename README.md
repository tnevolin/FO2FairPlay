# FO2FairPlay

Fallout 2 modification for more fair play mechanics.

# Main idea

Fallout is advertised as an extremely flexible game where any possible build or skill set has a fair chance to go through the game in their own fashion. This idea alone makes it a superior not aging game still attracting players. Unfortunately, some game mechanics implementation restrict maximal flexibility shadowing some game features in favor of others. This mod intends to highlight and give second chance to these undervalued features expanding game play style variability.

Reviving inferior feature requires not only enhancing said feature value but also toning down any superior features (and exploits) for fairer options distribution among them.

## Goal summary

* All builds/items/actions/features are usable and playable without major suffering.
* Less number of game lore unrelated exploits.
* More intuitive items/actions/features usage without consulting game mechanics internals.
* Less clutter and micromanagement distracting player from the story.
* Maintain steady game difficulty progression to keep player engaged from beginning to the end.

## Inferior/superior features and exploits examples

* FO1 Charisma is a completely dump stat no one recommend to even have.
* Agility effect on APs is so important that everyone recommends to raise it as high as possible.
* Unarmed attacks are laghingstock.
* Intelligence affects SP rate great deal effectivelly requiring to have it high or suffer from skills underdevelopment.

# Thanks

sFall: to all its authors and contributors. Making modding much easier!

# Implemented modifications

## Base HP

```
HP = 15 + 3 * EN
```

* Strength affecting health is somewhat awkward especially when it does not contribute to HP increase per level later on.

## Base AP and AC

```
AP = 7 + AG / 4 (fractional AP are accumulated over combat rounds)
AC = 2 * AG
```

* Base AP is now sufficient to perform any action and making even lowest AG player moderately combat mobile.
* Every AG point matters. No more lost AP fractions and stupid fiddling with even values. Ugh.
* AG is now brings only 1/4 AP making direct AP effects (drug, perks) more valuable in this regards.
* AG now influences natural AC making it more defense related and less attack rate related.
* Taking AG increasing drugs now makes more defensive sense.

## Melee damage

```
Melee damage = ST
```

More effect of ST on unarmed/melee damage. In vanilla it was quite unnoticeable.

## Carry weight

```
Carry weight = 75 + 25 * ST
```

Carry weight is a QoL and is not some strategical part of the game. Insufficient carry weight causes only frustration in my opinion. This is purely optional, though.

With this formula even ST=1 character can carry some minimal equipment set.

## Rad resitance

```
Rad resistance = 4 * EN
```

Vanilla rad resistance level seems to be completely ignorable. With this update EN gets a little more appeal to player. At least they can now eat more irradiated food for less consequences.

## Tagged skills

* Tagged skill (both initial and Tag! one) receives +20 bonus.
* Tagged skill does not grow twice as fast.

There are a lot of skills in the game already. Tagged skills grow extremely fast. Most non combat skills get their max effect around 100%. That is why they are rarely tagged due to *economical* SP spending reasons. Which is again, lore breaking.

Of course, it would be better to correct skills themselves and make them work even beyond 100% (or something) but this is a quick and sloppy fix for that. I may review it in future.

## Skills advancement

Most non combat skills reach their max usefulness at around 100%. Combat skills are already almost perfect at 200% which is what normal game pace without grinding provides anyway. I have tightened the SP cost to make player cherish every point and be mindful of their character specialization and not to become jack-of-all-trades.

* Skill cost is based on skill level added on top of base and other bonuses. Thus eliminating skill cost exploits.
* Average stats character should end up with all initial skills at about 25%.
* Skill level advancement cost start from 1 SP and then increments every 25% skill added.

#### Skill advancement cost based on added skill level

```
  1% to  25% costs 1 skill point
 26% to  50% costs 2 skill points
 51% to  75% costs 3 Skill points
 76% to 100% costs 4 Skill points
101% to 125% costs 5 Skill points
126% to 300% costs 6 Skill points
```

## Skill initial formulas

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
| First Aid | 0 + 2 \* PE + 2 \* IN + 1 \* CH | |
| Doctor | 0 + 2 \* PE + 2 \* IN + 1 \* CH | |
| Sneak | 0 + 1 \* EN + 2 \* AG + 2 \* LK | |
| Lockpick | 0 + 2 \* PE + 2 \* AG + 1 \* LK | |
| Steal | 0 + 2 \* AG + 2 \* CH + 1 \* IN | |
| Traps | 0 + 2 \* PE + 1 \* AG + 2 \* IN | |
| Science | 5 + 4 \* IN | |
| Repair | 0 + 2 \* PE + 2 \* IN + 1 \* LK | |
| Speach | 0 + 5 \* CH | |
| Barter | 0 + 5 \* CH | |
| Gambling | 0 + 5 \* LK | |
| Outdoorsman | 0 + 2 \* EN + 1 \* PE + 2 \* IN | |

## Unarmed attacks

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

## AP carryover

AP pool is relatively low comparing to weapon attack AP requirements. That causes an immense frustration when AP pool is not a direct multiple of a weapon AP requirements resulting in significant AP waste. Example: 7 AP allows just one spear thrust with 3 AP wasted. Players are constantly preoccupied with pixel perfect matching their AP pool and weapon requirements. This is incredibly stupid and big time immersion killer.

This mod allows carrying up to 3 skipped APs over to next round. This way modifying AP pool by small amount like plus/minus 1 AP results in smooth and direct addition to mobility and firepower. The above "7 AP for 4 AP spear thrust" example now grants one additional attack every 3 out of 4 rounds as it should. No more weapon tables consulting - more pure gaming!

## IN effect on Skill rate

```
Skill rate = 15 + 1 * IN
```

* Minimal skill rate is raised from 5 to 15. Low intellect character is not lacking skills severly anymore.
* Intellect is still a hefty addition to still rate.

## Ammo AC mod

I agree with FO2Tweaks Damage mod author that ammo parameters are pulled out of the ass. Especially AC mod one. It is easy to imagine ammo type affects armor penetration and delivered damage but affecting chance to hit??? It does not make much sense in vanilla anyway. Most ammo types have zero or negligible AC mod. If you also pay attention to that same weapon AP and non-AP ammo variations have *same* AC mod (5mm, .44 Magnum, 10mm AP, Flamethrower fuel, HN Needler cartridge) then it becomes clear that designers actually used *ammo* AC mod to adjust corresponding *weapon* accuracy. Conclusion: it is safe and cleaner to exclude AC mod from game mechanics.

* All ammo AC mod values are set to zero.

## Book affected skills

Having just few skills affected by books is kind of skewed view on things. This forces player *NOT* to tag book raisable skills. It would be fairer and probaly funnier too to distribute book effect across all skills.

Here are proposed cross pollination between books and skills. I matched them as loosely as possible to increase possible use across many skills. Two additional EcCo books are also used. Speech benefits from many book as the more you read the more topic you can cover and amaze listeners. Still the distribution is not absolutely symmetric so some skills may benefit more from books throughout the game but it is not that bad. It is still better coverage than in vanilla. Player compensates not covered skills with regular SP distribution.

* Book may affect other topic related skills besides main one.
* Book improves the least advanced skill among those related.
* Book effect is equivalent of spending 6 SP to the selected skill advancement taking cost of each skill level point into account. Anything remained unspent is left in SP pool.

#### Skill book affected skills
| skill | book |
|----|----|
| Small Guns | Guns and Bullets |
| Big Guns | Guns and Bullets |
| Energy Weapons | Guns and Bullets, Deans Electronics |
| Unarmed | First Aid Book, Scout Handbook |
| Melee Weapons | First Aid Book, Scout Handbook |
| Throwing | Traps and Explosives |
| First aid | First Aid Book, Guns and Bullets |
| Doctor | First Aid Book, Big Book of Science |
| Sneak | Scout Handbook |
| Lockpick | Deans Electronics, Scout Handbook |
| Steal | Scout Handbook, Capital |
| Traps | Traps and Explosives |
| Science | Big Book of Science |
| Repair | Deans Electronics |
| Speech | Guns and Bullets, First Aid Book, Deans Electronics, Big Book of Science |
| Barter | Capital |
| Gambling | Big Book of Science |
| Outdoorsman | Scout Handbook |

# Future ideas

## Book SP effect

*NOT Implemented*

It would be nice to exclude any book related exploits and to have book affect skill beyond 100% maybe at diminished effect.

### Potential solutions

* Book contributes an equivalent of 6 SP spent on target skill rounded down. The remainder of unspent SP goes to generic SP pool.
* Comprehension adds 50% of SP equivalent as advertised.

### Effect

* Eliminates book exploit as they are now awarding SP and not skill increase directly.
* Book continues contributing to skill beyond 100% albeit slower. Thus Comprehension perk is not a complete waste now.

## CH effect on combat

*NOT Implemented*

FO2 ties party size to CH making it not absolutely worthless. I feel it is still not on par with other combat skills like ST/PE/AG. May give it some combat effect too like in FO3 where it increases party member damage and DR (emulating combat leadership/spirit or sort?).

### Potential solutions

* `Friendly critters DR bonus (including dude) = -20% + 4% x CH`

## AC, DT, DR simplification

*NOT Implemented*

There are a lot combat calculation parameters in game those make it quite unplayable without consulting weapon/armor parameters table and calculator. They are definitely redundant and I believe these parameters should be simplified as much as possible for more intuitive play.

Good example of such simplification is [FO2Tweaks Damage mod](https://forums.bgforge.net/viewtopic.php?f=26&p=388). It ties ammo DT/DR modifier, ammo damage modifier, and armor DT/DR all together removing unnecessary variable clutter.

I would like to continue this path giving simple meaning to different game parameters allowing players to estimate their corresponding effect without use of item parameter tables and heavy formulas.

### Proposed approach

#### Accuracy and AC

Accuracy is an ability to hit the target. AC is a corresponding counter for it: an ability to disrupt opponent's aiming and worsen their accuracy. Accuracy grows with the skill advancement as game progresses. So should the armor AC to play natural counter and restrict accuracy from skyroketing beyond 200% beyond which skill investment is useless. To put it differently, player invests into combat skill to overcome evergrowing opponents' AC.

With that in mind armor AC should grow proportionally to its percieved "strength" but should not go higher than say 20%-30%. Vanilla does a pretty good job on that except some types of leather armor somehow are more AC protective than metal armor. That probably should be corrected.


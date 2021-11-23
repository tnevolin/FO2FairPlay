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

## Book skills and effect

Having just few skills affected by books is kind of skewed view on things. This forces player *NOT* to tag book raisable skills. It would be fairer and probaly funnier too to distribute book effect across all skills.

Here are proposed cross pollination between books and skills. I matched them as loosely as possible to increase possible use across many skills. Two additional EcCo books are also used. Speech benefits from many book as the more you read the more topic you can cover and amaze listeners. Still the distribution is not absolutely symmetric so some skills may benefit more from books throughout the game but it is not that bad. It is still better coverage than in vanilla. Player compensates not covered skills with regular SP distribution.

* Book may affect other topic related skills besides main one.
* Book improves the least advanced skill among those related.
* Book effect is equivalent of spending 6 SP to the selected skill advancement taking cost of each skill level point into account. Anything remained unspent is left in SP pool.
* Comprehension adds 50% of SP equivalent as advertised.

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

## Weapon Min ST requirement

Weapon power varies greatly. Any better one immediately and completely obsoletes all weaker analogues. It would be fine if obtaining and using stronger weapon require certain character progression but it is not the case in open game. It is relatively easy to obtain high end pieces just by buying them in stores. That breaks the need for character progression and ruins game RPG system. Weapon ST requirement is a nice feature that potentially can demand more ST or skill level before player can use more powerful item maintaining the importance of experience and leveling until the end of the game. Unfortunately, it is very forgiving. The minigun 7 ST (highest existing requirement) is not that dificult to achieve either initially or by drugs. Raising these requirements for stronger weapons makes them much less accurate until player actually works their way to handle them better in a matter of increasing ST or weapon skill.

New formula below recalculates weapon Min ST based on its average damage and burst size. More devastating weapon becomes more difficult to handle. If anyone requires lore explanation for that effect, more powerful weapon produces stronger recoil (with longer burst emphasising that) demanding higher strength just to maintain steady aim.

New Min ST is updated only if it is bigger than old one.

With new formula some extra powerful weapons Min ST goes beyond 10 making it impossible to complensate accuracy loss with ST improvement and giving them inherent accuracy penalty that can be offset only with skill advancement.

### New formula

Everything but grenades:

```
weapon min ST = 1 + [sqrt(average damage) * 1.30] + [burst size / 5]
```

Grenades:

```
weapon min ST = 1 + [sqrt(average damage) * 1.3 * 0.3]
```

### Penalty

* Lowered penalty down to 10% to ease ST combat value. Otherwise, it becomes extremely important especially in early game.

## Ranged accuracy

FO introduces "weapon effective range" as the distance at which "range penalty applies". This naturally implies that within effective range penalty *does not appy* so weapon maintains steady base accuracy equal to skill. Makes perfect sense on paper. Sharper senses or specialized long ranged weapon help maintain aim for longer distance. Unfortunately, the implementation is screwed big time. Somehow, range penalty does apply at every distance and effective range is no longer a thing player can percieve. There are other consequences of this bad design. One is that equally ranged accuracy could easily overtake equally skilled close combat one by 64%/128%! Another is weapon scope range dropping differs by 50% for adjacent tiles! The current implementation formula is both game and mind breaking based on amount of "how accuracy is calculated" forum topics out there.

### Proposed fix

* Attack base accuracy is equal to skill.
* Weapon maintains steady accuracy within its effective range that normally stretches from 0 to PE.
	* Sharpshooter perk extends far end of effective range by 4.
	* Long range weapon *shifts* effective range 10 hexes forward making it easier to hit distant targets in exchange for close range penalty.
	* Scope range weapon *shifts* effective range 15 hexes forward making it even easier to hit distant targets in exchange for more severe close range penalty.
* Range penalty applies outside of effective range 4% per hex.
* Other perks and conditions (weapon accurate, darkness) work as before.

#### Note on Sharpshooter

The modification process assumes fixed Sharpshooter that adds flat 16%, not 8% as in vanilla. If you are installing this mod on not patched game you'll experience 8% accuracy drop due to that. Although, nobody is likely playing unpatched game nowadays.

### Consequences

* Skill level is a direct and intuitive indicator of attack accuracy. Easy to compare and choose. No more consulting special tables and formulas needed.
* PE stretches weapon reach range *compensating* 4% range penalty per 1 PE. It does not *improve* the chance to hit. Still desirable stat for ranged combattant but not absolutely crucial one.
* Sharpshooter works as advertised.
* Weapon long/scope range have better longer range accuracy bonus but penalized up close. They are no longer superior to regular (short range) weapons at all distances and have their weapon specialization niche.
* Weapon long/scope range close targetting distance penalty keeps the same steady -4% per hex fall rate relieving player from accidental bad positioning frustration and constant need to count every hex to the target.

## Power armor ST bonus

That seems to be overly excessive. People are trying to optimize their initial ST assuming wearing advanced power armor at the end of the game. Raising initial ST over the 5 seems like an absolute waste after aquiring +1 memory module improvement and +4 from APA. Even ST 5 could be considered excessive as one can easily raise ST by 4 with just 2 Buffouts or even by 6 with 2 Jets on top of it. However, *before* aquiring APA ST 4 is too low to handle advanced weapons or to build unarmed/melee character.

FO lore presents primary stats as what is actually called a character! Something granted once at birth (character creation) and never modified throughout the game. That should be a direct opposite of skill focus that may change over the course of the game as player sees fit. I am not a particularly keen of Gifted trait, memory modules and zeta scans as they break this paradigm and give player stupid "maximize primary stats" golden fever idea destroying actual *role* playing. And +4 ST from APA is the worst abomination of them all turning weakling diplomat into a tank.

### Proposed solution

* All power armors grant +1 ST.

## Weapon accurate

I feel weapon accurate perk is given too much lef and right without consideration. Game mechanics wise this perk should symbolize some *unnatural* accuracy improvement aquired from the different targetting method such as shooting multiple pellet per shot making some but not all of them most certainly hit the target. All shotguns should have it by default offset by their lower damage (not all pellets hit) and shorter aiming range (extremely wide dispersion). Other weapons should be granted this bonus on a personal case basis like hunting riffle and Mauser. None of burstable weapon should have it.

* All shotguns (12 gauge caliber weapons):
	* Have weapon accurate perk (+20% accuracy).
	* Have max damage slightly reduced.
	* Have range significantly reduced.
* All burstable weapons except shotguns are NOT accurate.
* (Optional, not implemented) all 12 gauge ammunition is added 20 DR mod.

## Ammo DR mod adjustment

This mod is based on FO2Tweaks damage mod. This mod also adjusts DR mod for all projectiles to following. That seems to make better distinction between different bullet types across the weapon damage range and armor range.

Multiplier is calculated as follow and multiplies armor DT, armor DR and final damage.

```
multiplier = (1 + <DR mod> / 100)
```

| type | DR mod | multiplier | most effective against |
|----|----:|----:|----|
| AP | -40 | 0.60 | PA2 and above |
| FMJ, ball | -20 | 0.80 | metal2 to PA2 |
| normal, shotgun slug | 0 | 1.00 | combat leather jacket to metal 2 |
| JHP, shotgun regular | +35 | 1.35 | leather |
| shotgun buckshot | +70 | 1.70 | unarmored to leather |

# Future ideas

## CH effect on combat

*NOT Implemented*

FO2 ties party size to CH making it not absolutely worthless. I feel it is still not on par with other combat skills like ST/PE/AG. May give it some combat effect too like in FO3 where it increases party member damage and DR (emulating combat leadership/spirit of sort?). From the other hand it would be better to apply this effect to enemies only as party size already benefits from CH directly. Lore wise can be explained as hesitation to attack the army of famous fearsome leader.

### Proposed solution

* Enemy NPC chance to freeze in fear or flee: `4% x CH`.
* Enemy NPC chance to get -1 AP penalty: `10% x CH`.


See [README](https://github.com/tnevolin/FO2FairPlay) for detailed modification descriptions.

# 0.1

* Initial HP formula changed.
* Initial AP formula changed.
* Initial AC formula changed.
* Melee damage formula changed.
* Carry weight formula changed.
* Rad resitance formula changed.
* Tagged skill (both initial and Tag! one) receives +20 bonus.
* Tagged skill does not grow twice as fast.
* Skill cost is based on skill level added on top of base and other bonuses. Thus eliminating skill cost exploits.
* Average stats character should end up with all initial skills at about 25%.
* Skill level advancement cost start from 1 SP and then increments every 25% skill added.
* Combat skills base is about same for all of them. No more Small Guns preference.
* Combat skills depends on various more or less lore related stats.
* Speach and Barter are both now 5% x CH increasing CH stat attractiveness.
* Other skill initial level formula changed to add more primary stats variety.
* Unarmed attacks.
	* New attacks come at 10% skill intervals.
	* Stats requirements are reduced especially on lower level when player may not have drugs to raise them. EN requirement added for top level attacks instead.
	* Secondary attack AP requirements are reduced to have smoother progression. Vanilla 9 AP attack cost is completely insane.
	* Average damage (accounting criticals) per AP steadily grows with more advanced attack. There is no a single attack comptely inferior to preceeding one.
	* Punches are faster, deliver slightly more damage / AP, and have higher criticals. Kicks are generaly more damaging per attack.
	* Secondary attacks take more time but more damaging, and have higher criticals comparing to primary ones.
	* High end unarmed attacks are comparable to mega power fist.
* Some amount of APs can be carried over to next round.
* All ammo AC mod values are set to zero.

# 0.2

* `Skill rate = 15 + 1 * IN`
* All armor DT values are set to zero.
* Books can affect other skills.
* Books contribution to skill is equivalent of spending 6 SP on it.

# 0.3

* `AP = 7 + AG / 4` (fractional AP are accumulated over combat rounds).
* `AC = 2 * AG`

# 0.4

* Reverted: All armor DT values are set to zero.

# 0.5

* Accounted for Comprehension in book effect.
* Updated weapon Min ST formula.
* Modified weapon display message with corrected Min ST.

# 0.6.

* Modified ranged accuracy.
* Mention weapon perk in the description.

# 0.7

* Scrutinized weapon Min ST little bit.
* Power armor ST bonus reduced.

# 0.8

* Shotguns are reworked to be more accurate, short ranged, non AP weapons.
* Weapon accurate perk is removed from all burstable weapons except shotguns.

# 0.9

* Beautified weapon description with Min ST and perk on a new lines.
* Fixed problem with proto data been reverted to original on map entrance.

# 0.10

* Relaxed Min ST requirements. They are too harsh for weaker character.
* Lowered insufficient Min ST penalty to 10%.
* Shotguns are not accurate anymore.
* Shotguns damage is not reduced anymore.
* Shotguns range is reduced even more.
* Ammunition DR mod is standardized and modified slightly.
* Shotgun ammunition is given high DR mod for better damage but worse penetration.
	* Slug: +00.
	* Standard: +35.
	* Buckshot: +70.


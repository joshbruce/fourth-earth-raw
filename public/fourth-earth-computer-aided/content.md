---
title: Computer-aided Fourth Earth
---

# Computer-aided Fourth Earth

It might be an odd name but it seems to be the most technically accurate as the extensions to Fourth Earth RAW preserve the presence of a computer and nothing else. They do not dictate nor require specific implementation details like a [.GUI](Graphic User Interface) or a command line prompt; just the computer power, automation, and time-tracking capabilities afforded by a device that doesn't noticeably get bored or frustrated keeping tabs on such things.

Our intent is not to recap what has already been covered by the base Fourth Earth RAW material; so, it may be helpful to familiarize yourself with that first.

For Fourth Earth CA, we acknowledge the following benefits:

1. Automation of math calculations.
2. Ability to generate timers for things like hunger.
3. Ability to be real-time as opposed to turn-based.

And the following constraints:

1. Assets and locations must be pre-built.
2. [.NPCs](Non-player Characters) cannot respond on the fly.
3. If the code doesn't exist, the thing cannot exist.

## Action (overview)

**Critical success of non-combat actions** will result in rolling one 10-sided die and applying the side-effect identified in the following table:

|Result |Effect  |Narrative |
|:------|:-------|:---------|
|Even number |+1 |Elation from success! |
|1, 5, 9     |+2 |same                  |
|3, 7        |+3 |same                  |

**Critical failure of non-combat actions** results in general failure *and* uses the previous table where the positives are negatives (drain on target battery).

**Critically succeeding a combat action** results in general success (base damage or effect from above) *and* a side-effect from the following table based on the roll of a single 10-sided die:

|Result |Effect           |
|:------|:----------------|
|Even number |+1 to the battery used by the attacker |
|1, 5, 9     |base damage * 1.5 |
|3           |base damage * 2                     |
|7           |damage a body part (see next table) |

Note: A roll of seven continues with another roll of a single 10-sided die:

|Result    |Effect  |
|:---------|:-------|
|1         |-2 to challenge level of hitting target in the future |
|2, 5, 8   |-1 from target's physical battery                     |
|3, 6, 9   |-1 from target's mental battery                       |
|4, 7      |-1 from target's spirit battery                       |
|10        |-1 from target's health battery, recurring            |

Note: A roll of 10 results in a bleeding wound, which can compound if occuring multiple times.

**Critically failing a combat action** results in general failure (evasion by the target or complete miss) *and* the attacker receiving a side-effect from the following table based on the roll of a single 10-sided die:

|Result |Effect  |
|:------|:-------|
|Even number |-1 drained from attacking character's target battery                                       |
|1, 5, 9     |-2 drained from attacking character's target battery                                       |
|3           |The attacking character takes damage @ scale of 1 (a cramp, hitting yourself in a feint)   |
|7           |damage a body part (see previous table, replacing "target's" with "attacking character's") |

Note: A roll of seven continues with another roll of the 10-sided die and you can use the second critical success table only with the attacker as the target.

## Creating a character

Check our lore site to discover details on available species and options.

## Draining actions

**Calculating damage inflicted by combat action** modifies the basic RAW calculation. 

	> The recommended equation goes like this base drain based on tool used in attack (a), multiplied by the scale difference between the attacker and defender (b), and incorporating any side effects from criticality (c): a * b + c

We start the tool used (a) plus any stance or positioning modifiers (x) multiplied by the scale difference (b) adding or multiplying applicabale criticality side-effects (c) and subtracting any resistance from the target (y): (a + x) * b + c - y

Base damage from tool used is available in the following table:

|Tool or implement |Drain to health |Narrative |
|:-----------------|:---------------|:---------|
|Ram               |2             |The attacker runs directly into the opponent. |
|Jab               |1             |Quickly hit target with closed fist. |
|Uppercut          |2             |Heavier hit with closed fist. |
|Kick              |2             |Heavier hit with legs. |
|One-handed        |2             |Quickly hit target with one-handed weapon. |
|Two-handed        |3             |Heavier hit with single, two-handed weapon. |
|Magic             |4             |Heavy attack using spirit, requires preparation. | 

Fourth Earth CA recognizes three stances and effects on the drain defined in the previous table:

|Stance    |Effect |
|:---------|:------|
|Neutral   |n      |
|Offensive |n + 1  |
|Defensive |n - 1  |

Let's consider the rat example from RAW.

|Equation variable |Label              |Value |
|:-----------------|:------------------|:----:|
|a                 |Two-handed (spear) | 3    |
|x                 |Offensive          | +1   |
|b                 |Scale              | *10  |
|c                 |Criticality        | *2   |
|y                 |Resistance         | 0    |
|**Total**                            || 80   |

Let's consider a player versus player experience of the same thing:

|Equation variable |Label              |Value |
|:-----------------|:------------------|:----:|
|a                 |Two-handed (spear) | 3    |
|x                 |Offensive          | +1   |
|b                 |Scale              | *1   |
|c                 |Criticality        | *2   |
|y                 |Resistance         | 0    |
|**Total**                            || 8    |

How about a rhinoceros, now the attacker is the scale of 1:

Let's consider a player versus player experience of the same thing:

|Equation variable |Label              |Value |
|:-----------------|:------------------|:----:|
|a                 |Two-handed (spear) | 3    |
|x                 |Offensive          | +1   |
|b                 |Scale              | *0.1 |
|c                 |Criticality        | *2   |
|y                 |Resistance         | 0    |
|**Total**                            || 1    |

## Recharging actions

Fourth Earth CA has four batteries:

|Name     |Typically target of action type |
|:--------|:-------------------------------|
|Health   |Being attacked                                                      |
|Physical |Climbing, swimming, or hiking a steep hill                          |
|Mental   |Remembering a detail or learning information                        |
|Spirit   |Preparing magic or transferring battery points to another character |

The quickest way to recharge batteries comes when another character transfers some of their battery points to you. It's worth noting that transfers cannot jump batteries; health goes to health, spirit goes to spirit, and so on - and, of course, someone has to be willing to sacrifice their battery points to help your character. Beyond that there are various, intentional actions a character can perform to recharge their batteries. Each type of action targets a battery and recharge in real time. The target battery increases by 2 for unit of time passed, while the other batteries increase by one. The type of action determines how long the unit of time is. Because Fourth Earth is an action-based game, there are more actions targeting the physical battery as it will probably drain more than the others.

|Action |Time    |Target battery |
|:------|:-------|:--------------|
|Performing actions with an initial challenge level of 0 |Slowest |Health   |
|Rest                                                    |Slow    |Health   |
|Nap                                                     |Fast    |Physical |
|Sleep                                                   |Fastest |Physical |
|Meditate                                                |Fast    |Mental   |
|Revere (pray)                                           |Fast    |Spirit   |

Note: Your character may not be able to perform these actions in certain circumstances; taking a nap in the middle of a fight might be difficult, for example.

Health is the ultimate battery and requires 3 points to recharge 1 point from the other batteries. Non-health batteries requires 2 points to recharge 1 point from the other batteries.

## Compound actions

Some actions are little more complex and may involve multiple opportunities for failure.

The magic system described in a different section is an example where the character needs to:

1. Have the magic stone on them to prepare it.
2. Prepare to cast the spell associated with the stone.
3. Not get distracted and have to start over.

There a challenge level for preparing, followed by a delay to cast, then a decreased challenge level to cast and hit the target.

Alternatively, consider climbing a wall using the Citizen Hook as a grappling hook. The character needs to:

1. Join the separate picks together.
2. Attach a rope to the Citizen Hook.
3. Throw the Citizen Hook up the wall to a secure anchor point.
4. Climb the rope.
5. Optionally wait for their companions to climb the rope behind them at a reduced cost.

The first two steps are mundane actions (challenge level of 0). Using the Citizen Hook automatically reduces the challenge level of the climb by 2; climbing with the picks separated would reduce it by 1. Climbing the rope is always a challenge level of 2 (using the rope might actually be harder than not). The difference is the challenge of level of throwing the hook to secure the anchor. 

For example, an initial challenge level of 7, becomes 5 due to the hook, climbing the rope is 2, which leaves securing the anchor as a challenge level 3. Contrast this with using the separate picks, which would reduce the challenge level to 6 and only helps the user.

## Skills and tools

The list of available actions, skills, and tools and their related modifiers are available on the lore site.

### Use it or lose it

One benefit of being computer aided is the administration and management of character skills can be automated. The same is true for skill degredation. Therefore, the number of skills available to characters is larger than anyone might want to put on a character sheet and proficiency points can be removed automatically over the course of gameplay and without warning; it's often the case that the realization of skill loss does not occur until one tries that skill again (someone used to do cartwheels all the time and after 20 years of not doing cartwheels tries and fails miserably).

### Skill stacking

Because characters can attempt anything and some skill overlap, the character can be able to grow in multiple skills simultaneously. For example, sneaking (moving while hidden) involves hiding (being difficult to see), if a character successfully sneaks from one place to another, they become more proficient in sneaking and hiding based on the constraints of the ranking system.

Note: If a player stops sneaking everywhere and just hides, the use it or lose mechanic can kick in.

Consider a character who wants to climb something with a challenge level of 6. The character decides they want to use the Citizen Hook and rope as a grappling hook. This would reduce the challenge level to 4. The first sub-action might be to set the grappling hook and the second is climbing the rope itself. The total challenge level or character cost would not exceed 4 to accomplish both tasks, but it's a bit riskier because there would be two rolls, if a roll is required otherwise batteries get drained or both. 

Consider also the magic system for Fourth Earth CA. A character prepares to cast, which is where the challenge roll is made based based on the spell being prepared. To add risk and tension, if the character is hit before they cast the spell, they may lose the ability to cast the spell. So, the cost is up front, if the cast is made criticality checks would apply, and the risk is not being able to actually cast the spell.

## Magic

Fourth Earth RAW does not require magic; however, the official setting of Fourth Earth games have magic - more about that on the lore site.

Spells are tied to magic stones. Using magic is a two-step action: preparing and casting. Preparing to cast a spell has a challenge level targeting the spirit battery. If the character prepares the spell successfully there is a waiting period to cast. During the waiting period the character may become distracted and no longer be able to cast that spell. For non-combat spells, the casting challenge level is reduced 50 to 75 percent; including down to 0. For combatitve spells, the casting challenge level is the target's challenege level reduced by 25 to 50 percent.

When it comes to healing spells, the character can only target themselves. Therefore, in order to heal others the character must first transfer some of their battery points to the character, then turn their magic on themselves; an empathetic approach rather than an objectifying one. More details in the Healing, death, resurrection, and reincarnation section.

## Killing strike opt-in

Fourth Earth CA strives for flexibility in player choice and reality when practical. In general, when presented with a threat sentient life will fight, flee, or freeze. Further, fighting may turn to fleeing unless desparate or backed into a corner. Finally, outside of hunting, fighting tends to end prior to the death of the opponent. Therefore, by default, players must explicitly cause their characters to kill an opponent who has been subdued.

A sentient being who is subdued has 1 health point remaining and is unable to move for a period of time (like being unconscious); the deathstroke has a challenge level of 0. If the sentient being regains consciousness, they will be recovering on the same time-scale as standard recharging actions.

## Healing, death, resurrection, and reincarnation

Healing comes in four forms discussed elsewhere:

1. recharging actions,
2. transferring battery points,
3. salves or consumables, and
4. magic.

The first is time- and activity-based, the second is kindness-based, the third is plant-based, and the fourth is spirit-based. The first requires no special skills or tools, just a setting somewhat appropriate to the activity. The second requires no special skill, tools, or setting, just the kindness of someone nearby willing to transfer points. The third does not require a specific setting but may require a skill (foraging) or tools (a bag to carry the items in). The fourth does not require a specific setting and does require possession of the magic stone with the desired spell.

If the character is killed, there are only two options to continue playing the character:

1. be resurrected by someone else or
2. be reincarnated.

Being resurrected results in all life batteries being increased to one point. The character can move and act but they should be careful. Recurrection must happen within a certain period of time from the moment the character is killed (not subdued). After that time pases, the player is given the opportunity to have the character reincarnate in the area of Fourth Earth in which they were born. The character will experience the loss of the following characteristics:

- 100% of physical assets: You can't take it with you.
- 90% of physical skills and proficencies: You're driving a new body.
- 50% of mental skills and proficencies: You retain some of your memories and mental faculties.
- 20% of spiritual skills and proficencies: Spirit is what helps keep your soul attached to a body.

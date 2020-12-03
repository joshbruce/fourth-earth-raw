---
title: Solo adventures
version: 0.5.0
---

{{TOC}}

# Fourth Earth SA

Fourth Earth [.SA](solo adventures) is a specification wrapper of Fourth Earth [.RAW](rules as written) focusing on a single player playing one or more characters, with or without a narrator.

Fourth Earth SA offers implementations for multiple Fourth Earth RAW additions, which can be ignored, modified, or added to (see “Fourth Earth RAW: Additions” chapter).

Arguably the main hurdle for solo play is coming up with a world in which you, the player, can be surprised by what is found and what must be done. There are two primary methods for overcoming this:

1. Invite a narrator (or another player) who would have knowledge of the setting you do not (see Fourth Earth RAW: Additions, "West Marches" section).
2. Randomize the creation of the setting and adventures or use random generation to inspire calculated creation; usually done with cards, dice, or a combination.

As of this writing, Fourth Earth SA does not implement a possible solution.

**Required equipment:**

1. See Fourth Earth RAW introduction.
2. A way to track ranks in skills and tools; 4 points per rank.

Another major hurdle is altering outcomes to favor positive or negative outcomes (sometimes referred to as “fudging the dice”) or otherwise ignoring the rules. This can make the game feel less worth playing; unearned victories and random defeats. This is also one reason narrators are helpful. Narrators may alter outcomes and bend rules but you may not be aware it’s happening.

## Setting

See Fourth Earth RAW (and Fourth Earth Lore).

Fourth Earth Lore is available but not required.

### Sufficiently advanced technology and magic

See Fourth Earth RAW: Additions (and Fourth Earth Lore).

Fourth Earth SA provides an implementation of a hard magic system and does not remove the possibility of using a soft magic system. Further, it is possible to ignore the magic system entirely.

**Terms:**

- Hard magic system: A magic system with defined rules, consistently applied, often used by characters to solve problems in a specific, repeatable, and predictable way; usually at a cost to the character, setting, or both.
- Soft magic system: A magic system with loose rules often used to introduce (or increase) a sense of wonder or tension in a setting rather than solving problems in predictable ways.

Guidelines:

1. Spells originate from physical assets, which are carried by characters in order to cast; if the asset is not equipped or being carried by the character, the spell cannot be cast. 
2. Qualities of the spell determine the difficulty to cast, which targets the spirit battery.
3. Difficulty should start at 0 and be easy to calculate; if difficulty to cast reaches 7, no further calculations are required.
4. Resolving magic with a roll should only require one roll.

Implementation to calculate difficulty to cast:

**Rarity of spell**

|Quality |Modification |
|:-------|:------------:|
|ubiquitous | 0 |
|common | 1 |
|uncommon | 2 |
|rare    | 3 |
|scarce | 4 |

**Target for spell**

|Quality |Modification |
|:-------|:-----------:|
|inanimate object | 1 |
|self              | 2 |
|another           | 3 |

**Intent of caster**

|Quality |Modification |
|:-------|:------------:|
|survival | 0 |
|heal     | 1 |
|harm    | 2 | 

**Distance from caster**

|Quality |Modification |
|:-------|:------------:|
|touch    | 0 |
|distance | 1 |
|ranged   | 2 |

Consider:

A ubiquitous spell called spark. Character A wants to cast spark to light a campfire by casting it on a small pile of tinder where they plan to build the fire. 

| Quality | Adjustment | Difficulty |
|:--|:--|:--:|
| ubiquitous | 0 + 0 | 0 |
| inanimate object | 0 + 1 | 1 |
| survival | 1 + 0 | 1 |
| touch | 1 + 0 | 1 |
|  **total** | | **1** |

Or a rare spell called resurrection. Character A wants to resurrect character B who is in a different area or room.

| Quality | Adjustment | Difficulty |
|:--|:--|:--:|
| rare | 0 + 3 | 3 |
| another | 3 + 3 | 6 |
| heal | 6 + 2 | 8 (becomes 7) |
| ranged | doesn’t matter | 7 |
|  **total** | | **7** |

Implementation continued (internal or external):

Fourth Earth SA recognizes spells with the quality of starting internally or externally to the target. 

External spells start at the caster and travel to the target and are affected by resistance. Internal spells start within the target and are *not* affected by resistance.

|Origin |Modification |
|:-|:-:|
|internal | 0 |
|external |one-fourth the target’s difficulty rounded down |

Guidelines:

1. It is left to the players to decide how differences in difficulty to cast and difficulty to hit are managed; maybe higher of the 2 or a multi-faceted action (see Fourth Earth: Additions, “Multi-faceted actions” addition).

Consider:

Character A wants to cast an uncommon fireball spell (external) at character B with an initial difficulty of 5.

|Quality |Adjustment |Difficulty |
|:-|:-|:-:|
|uncommon | 0 + 2 | 2 |
|another | 2 + 3 | 5 |
|harm | 5 + 2 | 7 |
|distance | doesn’t matter | 7 |
|external | doesn’t matter | 7 |
|**total** | n/a | **7** |

Player A spends 7 spirit to reduce the difficulty to 0; character A casts and hits character B. 

The spell has a potential energy of 5 (see "Interacting with other characters" section). Character B has a resistance of 3, the potential energy is reduced by 3, leaving 2 received energy. The health battery for character B is reduced by 2. 

Alternatively, character A wants to cast an uncommon combustion spell (internal) at character B. Everything else is the same except the spell would not be affected by the resistance of character B; health battery reduces by 5.

## Characters

### Life batteries

See Fourth Earth RAW (and Fourth Earth Lore).

Implementation:

1. Four batteries:
	- health,
	- physical,
	- mental, and
	- spirit.
2. Each battery has a maximum of 8 points. 
3. Difficulty can be reduced 1 level per battery point spent (see "Difficulty" section). 
4. The health battery cannot remain 0.
5. Battery points may be traded between characters (see “Assist addition” section).
6. See “Overflow batteries addition” section.

Implementation (difficulty target):

|Name     |Action category                             |
|:--------|:-------------------------------------------|
|Health   |Injury and healing                          |
|Physical |Physically dominant actions                 |
|Mental   |Mentally or psychologically taxing actions |
|Spirit   |Magic- or spirituality-related actions      |

Implementation (recharging batteries):

1. Characters can take specific actions to recharge batteries.
2. Actions may have a difficulty assigned.
3. Each unit of time recharges all batteries by 1 point and the target battery based on the following table (not exhaustive or restrictive list).

|Action        |Time to recharge |Target battery |Target battery increase per unit of time |
|:-------------|:----------------|:--------------|:-------------:|
|Rest          |Slow             |Health         | 2 |
|Nap           |Fast             |Physical       | 3 |
|Sleep         |Fastest          |Physical       | 4 |
|Meditate      |Fast             |Mental         | 3 |
|Revere (pray) |Fast             |Spirit         | 3 |

Consider:

4 characters on an airplane (setting). They decide to sleep (recharging action). It's noisy and one of the characters is afraid of flying. 

3 players roll against physical difficulty 1, while the fourth rolls difficulty 3 (1 physical and 2 mental). 

All manage to sleep the first round. They all regain 4 to their physical batteries and 1 to all other batteries. 

On the second round, all characters but the one who's afraid to fly succeeds. The same thing happens the third round. They all fail the fourth round, which is good because the plane is going down.

The character with the fear of flying only received one round of recharge (a bad night's sleep) compared to the other 3 characters who recharged 3 rounds.

Guidelines:

1. The number of requirements for rolling can be flexible; sleeping overnight in a mundane house might result in the narrator saying, "Cool, you're all fully recharged."

Implementation for death, resurrection, and reincarnation:

1. The effects are immediate based on the following event table. 

|Type |Effect |
|:----|:------|
|Death         | 1 proficiency point removed from all acquired ranks (no change to partials) |
|Reincarnation | 1 point removed from all ranks (acquired and partial); loss of physical assets; character awakes in hometown, roughly as if character was created anew |
|Resurrection  | 1 to health battery (others are 0) |

### Overflow batteries addition

Implementation:

1. The health battery cannot be used as overflow; overflow points are spent automatically until the health battery has 1 point or all batteries are 0, whichever comes first.
2. The other batteries cannot be negative and can remain at 0.
3. Overflow batteries are defined in the following table.

|Name     |Convertible from             |Cost to increase 1 point |
|:--------|:----------------------------|:---------------:|
|Health   |physical, mental, and spirit | 3 |
|Physical |mental and spirit            | 2 |
|Mental   |physical and spirit          | 2 |
|Spirit   |physical and mental          | 2 |

### Subdue addition

See Fourth Earth RAW (and Fourth Earth Lore). 

Implementation:

1. A character with 1 point in their health battery is considered subdued; this is not the only way a character may become subdued.
2. Subdue not kill by default; expressing intent to kill not subdue can be done at any time with no turn cost (a minor action, if you will).
3. Subdued characters are unable to act for 4 full rounds or until acted upon by an outside force, whichever is shorter in time.
4. Subdued characters may be able to speak, they are not able to physically interact with the setting; they are recovering.

Consider:

Character A attacks character B with 5 points of received energy; character B has 3 points left in their health battery. The health battery is set to 1; alive but subdued.

Character A turns their attention to character C and attacks for 4 points of received energy. Character C has 4 points left in their health battery, which means character C’s health battery is also at 1 and they are subdued. 

Before the end of their turn, player A (playing character A) says they wish to kill character C, the nemesis of character A. The killing stroke is performed with no difficulty and before the end of player A’s turn.

The fighting continues and the room is cleared over the next 4 rounds. 

During the fifth round, character B has regained consciousness and can speak but cannot act. Character A handcuffs character B at the wrists and ankles, character B remains subdued and able to speak until the handcuffs are removed. 

### Resurrection addition

See "Life batteries" section.

### Reincarnation addition

See "Life batteries" section.

### Offspring addition

Guidelines:

1. If using pregnancy, character mobility and activity levels may be effected. 

Implementation:

1. Roll [.1d12](one twelve-sided die), if the result is 1, there were complications during gestation or pregnancy.
2. If using a form of liquid assets (money), spend 10 percent or a reasonable flat fee (easily earned in “one day’s work”), whichever is greater; for the gestation or pregnancy.
3. Roll 1d12, if the result is 1, there were complications during childhood.
4. If using a form of liquid assets, spend 25 percent or a reasonable flat fee (easily earned in “one month’s work”), whichever is greater; for clothes, education, food, and so on.

## Interacting with the setting

### Difficulty reduction addition

Implementation:

1. Difficulty level can be reduced by spending battery points; 1 level per 1 point.
2. Proficiency points are earned based on initial difficulty level, not the reduced difficulty level.
2. See "Skills and tools" section.

Consider:

See Fourth Earth RAW: Additions "Difficulty reduction" section.

### Criticality addition

See Fourth Earth RAW extensions (and Fourth Earth Lore).

Implementation:

1. Criticality does not always mean otherwise impossible series of events.
2. Opposing characters also get to use criticality.
2. Add [.1d10](one ten-sided die) (the criticality die) to the pool.
3. If a 1 is rolled on the criticality die, the success or failure result of the action pool is considered critical.
4. Players may opt-out of rolling the criticality die prior to rolling the action and cannot add it afterward; opting out would remove possibility of complications or partials as well (see “Complications and partials addition” section).
5. If the difficulty is reduced to 0, the criticality die is not rolled as there is no pool to add it to.
6. Base outcome of criticality uses the following table.

|Action type |Action pool result |Next step |
|:-|:-|:-|
|Mundane |Success |Roll [.1d12](one twelve-sided die) and apply the mundane action implementation |
|Mundane |Failure |Roll 1d12 and apply the mundane action implementation, subtracting instead of adding |
|Combat |Success |Roll 1d12 and apply the successful combat action implementation  |
|Combat |Failure |Roll 1d12 and apply the failed combat action implementation |

Implementation (mundane action):

1. Points are added to the target battery for the action (climbing a tree would be physical and magic would be spirit). 
2. If that battery is or becomes full, the remaining points can be distributed as the player chooses; including to the health battery.

|Result |Effect  |Narrative |
|:------|:-------:|:---------|
|Even number |1 |Elation from success! |
|1, 5, 9     |2 |same                  |
|3, 7        |3 |same                  |
|11          |5 |same                  |

Implementation (successful combat action):

|Result |Effect           |
|:------|:----------------|
|Even number |1 to the battery used by the attacker or any other battery, if full |
|1, 5, 9     |base potential energy times 1.5 |
|3, 7        |base potential energy times 2   |
|11          |trauma (roll another 1d12 and apply the successful combat action extension implementation) |

*Successful combat action extension:*

1. Recurring effects occur every round until fixed. 
2. Compounding effects can be applied multiple times (-2 becomes -4 becomes -6).

|Result    |Effect  |
|:-------|:-------|
|1       |difficulty of defender reduced by 2, recurring and compounding |
|2, 5, 8 |drain 1 from defender's physical battery; if 0, from a random battery |
|3, 6, 9 |drain 1 from defender's mental battery; if 0, from a random battery |
|4, 7    |drain 1 from defender's spirit battery; if 0, from a random battery |
|10      |drain 1 from defender's health battery, recurring and compounding |
|11      |base potential energy times 3 targeting the defender    |
|12      |defender is unable to act for 2 rounds                  |

Implementation (failed combat action):

|Result |Effect  |
|:------|:-------|
|Even number |drain 1 from attacker's target battery; if 0, from a random battery |
|1, 5, 9     |drain 2 from attacker's target battery; if 0, distributed across multiple batteries |
|3, 7        |attacker damages themselves at 1 to 1 scale, no resistance is applied, one-half the potential energy, can’t be less than 1 |
|11          |trauma (roll another 1d12 and apply the failed combat action extension implementation) |

*Failed combat action extension:*

|Result    |Effect  |
|:-------|:-------|
|11      |If a tool was used, it is rendered useless; otherwise, apply 11 from the successful combat action extension implementation, replacing “defender” with “attacker”. |
|all other numbers      |Apply the corresponding effect from the successful combat extension implementation, replacing “defender” with “attacker”. |

### Complications and partials addition

See Fourth Earth RAW extensions (and Fourth Earth Lore).

Implementation:

1. Use the same die as criticality (see “Criticality addition” section).
2. If a 10 is rolled on the criticality die, the result of the action results in complications or partials.
3. A complication is a mildly negative effect on an otherwise successful action. 
4. A partial is a mildly positive effect on an otherwise failed action. 
5. Resolution and type of complication or partial is left to player (and narrator) discretion.

### Re-roll addition

Implementation:

1. Players may spend battery or proficiency points to re-roll the entire pool or a single die; the health battery cannot be used.
2. To re-roll the entire pool is a cost of 1 point; re-rolling a single die costs 2 points.
3. As long as the player has points available to spend, the player may continue to re-roll; as long as the spend doesn’t change the pool itself (a proficiency point from a rank used to build the pool, for example).
4. The player chooses which points are spent.

### Scale addition

See Fourth Earth RAW (and Fourth Earth Lore). 

Implementation (primary):

1. Scale is primarily determined dynamically using the smallest participant in the interaction as 1.

Consider:

Most likely, 

- 2 rats would be 1 to 1, 
- a rat and human would be roughly 1 to 10, 
- 2 humans would be 1 to 1, 
- a human and whale would be 1 to roughly 100,
- 2 whales would be 1 to 1, and
- a rat and whale would 1 to 1,000.

### Stance

Implementation (combat):

1. Default stance is neutral. 
2. Stance is set or changed for all characters at the beginning of each round and cannot be changed during the round.

| Stance | Attacker affect| Defender affect |
|:--|:--|:--|
| Offensive | -1 difficulty | -1 difficulty |
| Neutral | 0 | 0 |
| Defensive | 1 difficulty | 1 difficulty |

Consider:

Character A is attacking character B. The following table lists each combination and subsequent modification to the difficulty of hitting character B.

|  | A:Offensive | A:Neutral | A:Defensive |
|:--|:--:|:--:|:--:|
| B:Offensive | -2 | -1 | 0 |
| B:Neutral   | -1 | 0 | 1 |
| B:Defensive | 0 | 1 | 2 |

## Interacting with characters

See Fourth Earth RAW (and Fourth Earth Lore). 

Implementation (harming others):

1. Calculating difficulty starts at 0 and increased using the following table; should rarely exceed 7. 

|Question |Yes |
|:--------|:---|
|Defender is subdued, stunned, or unconscious? |Difficulty is 0 - no need to continue unless applied to the psychology and morality of the attacker. |
|Defender has active allies?    |1 for every 2 active allies |
|Defender is lesser scale?      |1 for every 2 steps lesser  |
|Defender is on higher ground?  |1 |
|Defender is aware of attacker? |1 |

2. Calculating potential energy is based on action type using the following table, which favors stance and tool use, not specific tool.
3. Fast actions can be performed twice in a turn or round, players may choose to perform one of the two at reduced potential energy. 
4. When one fast action is taken, the difficulty remains the same and whole; when both fast actions are taken, difficulty is split evenly between the two.
5. If splitting the difficulty results in fractions, the first is rounded down while the second is rounded up.
6. Slow actions can be performed once in a turn or round.

|Type |Description |Potential energy |
|:----|:-----------|:-----:|
|Jab                      |Fast and light  | 1-2 (2 requires 2 attempts) |
|Uppercut, kick, or ram   |Slow and medium | 2 |
|Dual (tool in each hand) |Fast and medium | 2-4 (4 requires 2 attempts) |
|Two-handed               |Slow and medium | 3 |
|Advanced weapon or magic                    |Slow and heavy  | 5 |

Consider:

Character A (a human) attacking Character B (a rat).

**Difficulty**

|Quality |Adjustment |Difficulty level|
|:-|:-|:-:|
|initial | n/a | 0 |
|allies | 0 + 0 | 0 |
|scale | (one-half 10 steps) + 0 | 5 |
|neutral | 5 + 0 | 5 |
|awareness | 5 + 1 | 6 |
|**total** | n/a | **6** |

Character A decided to throw two jabs at the rat; giving us 2 physical actions at difficulty 3. Player A spends 5 battery points to reduce the levels; reducing the first to difficulty 0 and the second to difficulty 1. Player A is hoping they might get a criticality (see “Criticality addition” section).

**Dice pool**

For the difficulty 1 swing, player A has a starting pool of 1d2 (down from 1d10). Character A has 2 ranks in unarmed combat, making the pool 3d2 (see “Skills and tools addition” section).

**Potential energy**

|Action |Result |Potential energy |
|:-|:-|:-:|
|first jab |Auto-success | 1 |
|second jab |Critical success | 1 |
|second jab (critical) | 2 * 1 | 2  |
|total initial | 2 + 1 | 3 |
|scale | 3 * 10 | 30 |

See “Criticality addition” section.

**Resistance**

|Action |Result |Received energy |
|:-|:-|:-:|
|potential energy |n/a | 30 |
|armor |30 - 0 |30 |
|skin |30 - (-1) | 31 |
|**total** |n/a | 31 |

See “Resistance addition” section.

The life batteries of the rat are the same as all characters, and the same rules are applied; therefore, the rat is beyond dead, it’s effectively a puddle of goo. The initial 8 would have activated the overflow batteries, which are good for another 8; then it would have been drained another 15.

### Resistance addition

See Fourth Earth RAW (and Fourth Earth Lore). 

Implementation:

1. Resistance most likely won’t change often.
2. Every character has some type of flesh, the type and density is used to determine “thickness” using the following table; most characters should have average skin. 

|Thickness |Resistance |
|:---------|:---------:|
|Thin      | -1        |
|Average   | 0         |
|Thick     | 1         |

3. A resistance may also come from modifying the exterior with armor, which has 3 grades.

|Grade  |Resistance |
|:------|:---------:|
|Light  | 1 |
|Medium | 2 |
|Heavy  | 3 |

Consider:

The rat in the previous section had thin skin and no armor, resulting in a negative resistance.

Character A in the previous section had average skin and light armor, resulting in a resistance of 1.

A whale might have thick skin and be covered in metal plates, resulting in a resistance of 4; 1 for thick skin and 3 for the armor.

Character A is a human attacking a whale (character B) with no armor. The scale of the human is 1 and the whale is 100; making it easier to hit (see “Scale addition” section).

**Difficulty**

|Quality |Adjustment |Difficulty level|
|:-|:-|:-:|
|initial | n/a | 0 |
|allies | 0 + 0 | 0 |
|scale | (one-half -100 steps) + 0 | 0 |
|neutral stance | 0 + 0 | 0 |
|awareness | 0 + 1 | 1 |
|**total** | n/a | **1** |

Character A is using a two-handed spear. Player A doesn’t reduce the difficulty hoping for a critical hit (see “Criticality addition” section).

**Dice pool**

Character A has 2 ranks in two-handed tools and 1 rank in the spear, specifically. This adds 3 dice to the pool, making it 4d2 (see “Skills and tools addition” section).

**Potential energy**

|Action |Result |Potential energy |
|:-|:-|:-:|
|spear |success | 3 |
|scale | 3 / 100 | 1 |

Potential energy cannot be less than 1.

**Resistance**

|Resister |Adjustment |Received energy |
|:-|:-|:-:|
|potential energy |0 + 1 | 1 |
|armor |1 - 0 |1 |
|skin |1 - 1 | 0 |
|**total** | | 0 |

The whale swims away unfazed by the tiny human with the pointy stick.

### Roll to evade addition

Solo adventures typically only have one player. This means moving and possibly rolling as the opposing character(s), which may be difficult to do effectively; sub-optimal decisions may be made regarding positioning and reducing difficulties to protect the character. This can be overcome by rolling to evade rather than to hit.

Implementation:

1. The non-player character always reduces the difficulty
	- to 0, if possible or
	- as many levels as possible.
2. The player reduces and rolls against the opposing difficulty (see Fourth Earth RAW  “Difficulty” section); the number of dice in the pool are based on the player's character performing the opponent's action (basing evasion on knowledge of what the opponent is doing).
3. Criticality, complications, and partials are resolved as normal where the player character is the target or defender.

Consider:

Note: This example does not look at player A's turns.

NPC A has a physical battery with 8 points and no overflows.

NPC A is attacking Character A. Character A has a physical difficulty 5. 

1. Round 1: NPC A spends 5 points to reduce the difficulty to 0; that’s a hit. (The player does not roll for character A.)
2. Round 2: NPC A spends 3 points to reduce the difficulty to 2, the opposing difficulty is 6, and the player reduces and rolls as normal. 
3. Round 3: NPC A can't reduce the difficulty from 5, the opposing difficulty is 3, and the player reduces and rolls as normal. 

### Assist addition 

Implementation:

1. Transferring battery points uses the distance-to-difficulty table below, representing an initial spirit difficulty.
2. Assisting actions must have a difficulty at least 1 level lower than the difficulty of the action of the performing character and should not require movement by the assisting character.

|Quality |Difficulty |
|:-------|:------------:|
|touch    | 0 |
|distance | 1 |
|ranged   | 2 |

Consider:

See Fourth Earth RAW: Additions “Assist” section.

## Ranks

### Skills and tools addition

See Fourth Earth RAW (and Fourth Earth Lore). 

Skills and tools for the Fourth Earth setting are available in Fourth Earth Lore.

Implementation:

1. Skills have 3 ranks.
2. Tools may have up to 1 rank. 
3. Ranks require 4 proficiency points to be earned.
4. Tools may reduce difficulty up to 2 levels. 

## Time and space

### Initiative addition 

See Fourth Earth RAW extensions (and Fourth Earth Lore).

In Fourth Earth SA, initiative isn’t used to establish the order of turns so much as it answers a single question: Will the action of a soon-to-be subdued character be completed before they are subdued?

Guidelines:

1. Favor real-time, simultaneous resolution of action; therefore, a tie in initiative results in both actions completing.

Implementation:

1. Initiative for all characters starts at 0. 
2. Initiative is increased 1 for each 1 rolled in the dice pool. 
3. Actions are resolved in descending order; highest to lowest.
4. Players who reduce difficulty to 0 roll no dice; initiative remains 0.

More dice in the pool, higher chance of gaining initiative (see “Skills and tools addition” section).

Consider: 

Character A and character B are in melee combat; each wants to strike the other.

If character A hits, character B is subdued. If character B hits, character A takes 3 damage. 

The player rolls dice pools for both, to hopefully gain initiative; character A rolling 3 dice and character B rolling 5. Both pools are rolled; both succeed.

| Initiative | A:Outcome | B:Outcome |
|:--|:--|:-|
|Character A |no damage |subdued; success effectively becomes failure |
|Character B |3 points reduced from health battery |subdued |
|Tie |same |same |

This allows for two characters to effectively subdue each other. 

### Tool decay and destruction addition

See "Criticality addition" section.

### Becoming unskilled addition

See "Life Batteries" section.

## Conclusion

As with all of Fourth Earth RAW, if these implementations aren't to your liking, feel free to disregard or modify them in whole or in part. If you’re not seeing additions you would like to use, add or create them.

See Fourth Earth RAW and Fourth Earth RAW: Additions for guidelines and implementations.
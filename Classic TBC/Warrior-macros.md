# Macros for TBC Classic
Macros take talents and racials into account when calculating caps
* Sword Specialization (5 expertise) https://tbc.wowhead.com/spell=20597/sword-specialization
* Mace Specialization (5 expertise) https://tbc.wowhead.com/spell=20864/mace-specialization
* Axe Specialization (5 expertise) https://tbc.wowhead.com/spell=20574/axe-specialization
* Expertise gained from talents are automatically included
  * Defiance (Warrior Protection) https://tbc.wowhead.com/spell=12789/defiance

Macros does NOT take Draenei racial buffs into account.
* Heroic Presence (1% melee hit) https://tbc.wowhead.com/spell=6562/heroic-presence
* Inspiring Presence (1% spell hit) https://tbc.wowhead.com/spell=28878/inspiring-presence

## Attack tables caps vs. Enemy level
| Level | Hit (Yellow/1H/2H)   | Hit (Dual-wield white) | Spell Hit | Dodge | Parry |
| ----- | ----                 | -----------            | --------- | ----- | ----- |
|  70   | 5%                   | 24%                    |   3%      | 5%    |  5%   |
|  71   | 5.5%                 | 24.5%                  |   4%      | 5.5%  |  5.5% |
|  72   | 6%                   | 25%                    |   5%      | 6%    |  6%   |
|  73   | 9%                   | 28%                    |  16%      | 6.5%  | 14%   |

## Anti-Crit (Defense/Resilience) table vs. Enemy level
| Level | Anti-Crit         |
| ----- | ----------------- |
|  70   | 5.0%              |
|  71   | 5.2%              |
|  72   | 5.4%              |
|  73   | 5.6%              |


## Warrior
### Tank Caps
```
/run c,t,e=GetCombatRatingBonus,GetTalentInfo,GetExpertisePercent();_,_,_,_,d=t(3,3);_,_,_,_,h=t(2,17);_,_,_,_,m=t(2,14);print(format("Tank Caps\nAnti-Crit: %.2f/5.6%%\nHit: %.2f/9%%\nD: %.2f/6.5%%\nP: %.2f/14%%",floor(d*4+c(2))*.04+c(15),c(6)+h,e+m,e))
```
![Warrior Tank Caps](/Classic%20TBC/img/warrior-tank-caps2.png?raw=true)

Anti-Crit sums both Defense and Resilience into one, for easier readability

Reads the following talents:
* Anticipation (Protection) for defense skill https://tbc.wowhead.com/spell=12753/anticipation
* Weapon Mastery (Fury) for less chance that enemies dodge your attacks https://tbc.wowhead.com/spell=20505/weapon-mastery
* Precision (Fury) for hit chance https://tbc.wowhead.com/spell=29592/precision

### Avoidance
```
/run d,p,b=GetDodgeChance(),GetParryChance(),GetBlockChance();_,_,_,_,t=GetTalentInfo(3,3);m=floor(t*4+GetCombatRatingBonus(2))*.04+5;print(format("Avoidance\nDodge: %.2f\nParry %.2f\nBlock: %.2f\nMiss: %.2f\nTotal: %.2f / 102.4",d,p,b,m,(d+p+b+m)));
```
![Warrior Avoidance](/Classic%20TBC/img/warrior-avoidance.png?raw=true)

Reads the following talents:
* Anticipation (Protection) for defense skill https://tbc.wowhead.com/spell=12753/anticipation

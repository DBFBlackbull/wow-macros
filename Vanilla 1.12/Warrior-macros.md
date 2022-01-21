# Macros for World of Warcraft Vanilla 1.12
Many macros uses a magic number for actions, ie. `IsCurrentAction(40)` or `UseAction(40)`. In order to figure out where that number is on your UI use the following picture

![WoW Actionbar Slotnumbers](https://github.com/DBFBlackbull/wow-macros/raw/master/img/wow-actionsbar-slotnumbers.jpg)

## Basics
Whenever you see the following code:
```
if not IsCurrentAction(40) then UseAction(40);end;
```
All you have to think is `/startattack`. By placing my auto attack "spell" on slot 40, the above code ensures that my auto attack starts. You can change what slot you want it on and just change the number `40` to the slot you picked

## Auto attack + Ability
All these macros have the **requirement** that `Autoattack` must be on actionbar slot `40`

#### Start auto attack and try to use Heroic Strike
```
/script if not IsCurrentAction(40) then UseAction(40);end; CastSpellByName("Heroic Strike");
```
#### Start auto attack and try to use Cleave
```
/script if not IsCurrentAction(40) then UseAction(40);end; CastSpellByName("Cleave");
```
#### Start auto attack and try to use Whirlwind
```
/script if not IsCurrentAction(40) then UseAction(40);end; CastSpellByName("Whirlwind");
```
#### Start auto attack and try to use Revenge and Sunder Armor
```
/script if not IsCurrentAction(40) then UseAction(40); end; CastSpellByName("Revenge");  CastSpellByName("Sunder Armor");
```
## Combining abilities
#### Use Bloodrage and top trinket slot
```
/script CastSpellByName("Bloodrage"); UseInventoryItem(13);
```
#### Use Start auto attack, use Charge. If you are in combat and have a shield on, switch to Defensive Stance
**Requirement:**
- `Shield` must be on actionbar slot `30`
```
/run local inCombat=UnitAffectingCombat("player");if not IsCurrentAction(40) then UseAction(40);end; CastSpellByName("Charge"); if inCombat and IsEquippedAction(30) then CastSpellByName("Defensive Stance");end;
```
#### Battle Stance + Overpower
If you are not in Battle Stance, switch to Battle Stance. Then use Overpower
```
/run local _,_,inBattle=GetShapeshiftFormInfo(1); if inBattle then CastSpellByName("Overpower"); else CastSpellByName("Battle Stance"); end;
```
#### Defensive Stance + Disarm
If you are in combat and have 20 rage or more, switch to Defensive Stance and use Disarm
```
/run local _,_,inDefensive=GetShapeshiftFormInfo(2); if inDefensive then CastSpellByName("Disarm"); elseif (UnitMana("player")>19 and UnitAffectingCombat("player")) then CastSpellByName("Defensive Stance"); end;
```

## Advanced stuff
#### Helper Macro
For these macros, you first need run this helper macro that links out the "magic numbers" for the macros. Everytime you learn a new spell / proficiency you need to run this helper macro again and update all the "magic numbers" in the macros below
```
/run local i = 1; while true do local spellName, spellRank = GetSpellName(i,0); if not spellName then do break end; end; DEFAULT_CHAT_FRAME:AddMessage( spellName .. '(' .. spellRank .. ')' .. ' ' .. i );  i = i + 1; end;
```
#### Intercept + Defensive Stance / Battle Stance
If you are **in combat** or **Charge is on cooldown** then cast Intercept, then if you have a shield eqipped, go in Defensive Stance.
If you are **out of combat** and **Charge is off cooldown** then cast Battle Stance
**Requirements**
- Number `19` must match the number for `Charge`
- `Shield` must be on actionbar slot `30`
```
/run local c=UnitAffectingCombat("player");_,d=GetSpellCooldown(19,"spell");if c or d>2 then CastSpellByName("Intercept");if IsEquippedAction(30) then CastSpellByName("Defensive Stance");end;else CastSpellByName("Battle Stance");end;
```
#### Equip Shield + Shield Bash + Equip Off hand
This macro is only for fury warriors / warriors dual wielding weapons. It does the following
If **Shield Bash is off cooldown** and you have **10 or more range** then it equips your 1 hander + shield and casts Shield Bash. Afterwards its reequips your off hand weapon
You will need this image for bag number references:

![WoW Bags Slotnumbers](https://github.com/DBFBlackbull/wow-macros/raw/master/img/wow-bag-slots.png)

**Requirements**
- Number `46` must match the number for `Shield Bash`
- Actionbar slot `41` must have your main hand weapon
- Actionbar slot `30` must have your shield
- Your shield must be located in `Bag 4` in `Slot 3`
```
/run local u,p=UseAction,"player";_,d=GetSpellCooldown(46,"spell");if d<2 and UnitMana(p)>9 and UnitAffectingCombat(p) then u(41);u(30);CastSpellByName("Shield Bash");elseif IsEquippedAction(30) then PickupContainerItem(4,3);EquipCursorItem(17);end;
```
**Note:** This macro worked extremely well on Elysium private server as they, for some reason, did not have a Global Cooldown when dual wielding and equipping a shield in combat! Depending on what private server you are playing on and how it is coded, results may vary

# Macros for World of Warcraft Vanilla 1.12
## Warriro macros
Use Bloodrage and trinkets
```
/script CastSpellByName("Bloodrage"); UseInventoryItem(13);
```
Use Start auto attack, use Charge, then switch to Berserker Stance, or Defensive Stance if a shield is equipped (Requires that a shield is placed on actionbar slot 30)
```
/run local inCombat=UnitAffectingCombat("player");if not IsCurrentAction(40) then UseAction(40);end; CastSpellByName("Charge"); if inCombat and IsEquippedAction(30) then CastSpellByName("Defensive Stance");end;
```
Use Cleave and start auto attack
```
/script if not IsCurrentAction(40) then UseAction(40);end; CastSpellByName("Cleave");
```

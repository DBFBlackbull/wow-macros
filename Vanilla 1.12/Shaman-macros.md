# Macros for World of Warcraft Vanilla 1.12
Here are some helpful macros for Shamans

### Cast sequence for totems
**Requires:**
* `GetSpellCooldown(17,0)==0`: A spamable totem spell in your spellbook must match number `17`
```
/run s={"Mana Spring Totem","Strength of Earth Totem","Searing Totem"} if q==nil or q>getn(s) then q=1 end if GetSpellCooldown(17,0)==0 then CastSpellByName(s[q]) q=q+1 end
```
**Note:** This macro has no "reset" functionality so if your spam it too much your totems will start from a different totem than the first in the list.

### Cast sequence for totems depending on group. First sequence is for solo, second is for groups
```
/run m,s="Mana Spring Totem","Strength of Earth Totem" t={m,s,"Searing Totem"} if UnitInParty("target") then s={"Windfury Totem",s,m} end if q==nil or q>getn(t) then q=1 end if GetSpellCooldown(58,0)==0 then CastSpellByName(t[q]) q=q+1 end
```

### Cast Weapon enchant if missing, else cast a spell + Start auto attack
**Requirements:**
* `IsCurrentAction(71) / UseAction(71)`: Auto attack spell must be placed on actionbar slot `71`
```
/script e=GetWeaponEnchantInfo(); if not IsCurrentAction(71) then UseAction(71);end; if e then CastSpellByName("Flame Shock"); else CastSpellByName("Flametongue Weapon"); end;
```

### Cast a buff if missing, else cast a spell
**Requirements:**
* `SkinofEarth`: This is the icon name of the spell `Earth Shield`. These two values must match each other
```
/run i,b,p,c,u=1,0,"player",CastSpellByName,UnitBuff;while u(p,i) do if strfind(u(p,i),"SkinofEarth") then b=1 end i=i+1 end if b<1 then c("Earth Shield") end CastSpellByName("Rocky Bash")
```

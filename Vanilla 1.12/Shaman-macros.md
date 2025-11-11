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
/run m,s="Mana Spring Totem","Strength of Earth Totem" t={m,s} if GetNumPartyMembers()>0 then t={"Windfury Totem",m,s} end if q==nil or q>getn(t) then q=1 end if GetSpellCooldown(57,0)==0 then CastSpellByName(t[q]) q=q+1 end
```
When going solo this example this macro casts Mana Spring -> Searing Totem -> Strength of Earth

When in a group this example this macro casts Windfury -> Strength of Earth -> Mana Spring

### Cast Windfury Weapon enchant if remaining time is less than 20 seconds, else cast Stormstrike. Always Start auto attack
```
/script e,t=GetWeaponEnchantInfo(); if e and t>20*1000 then CastSpellByName("Stormstrike") else CastSpellByName("Windfury Weapon") end if not PlayerFrame.inCombat then AttackTarget() end
```

### In combat: Always cast Lightning Shield. Outside of combat: Cast Windfury Weapon if duration is less than 3 mins, else cast Lightning Shield
```
/script e,t=GetWeaponEnchantInfo(); if UnitAffectingCombat("player") or e and t>3*60000 then CastSpellByName("Lightning Shield") else CastSpellByName("Windfury Weapon") end
```

### Cast a buff if missing, else cast a spell
**Requirements:**
* `SkinofEarth`: This is the icon name of the spell `Earth Shield`. These two values must match each other
```
/run i,b,p,c,u=1,0,"player",CastSpellByName,UnitBuff;while u(p,i) do if strfind(u(p,i),"SkinofEarth") then b=1 end i=i+1 end if b<1 then c("Earth Shield") end CastSpellByName("Rocky Bash")
```

### Ghost Wolf in combat or if you are carrying the PVP flag in WSG or the Silithyst in Silithus. Otherwise it uses mount.
**Requirements:**
* Replace "War Wolf" with the name of your mount. Your mount must be placed in bag 0, i.e. the backpack.
```
/run p="player"g=UnitAffectingCombat(p)f=string.find for i=1,40do b=UnitBuff(p,i)or""g=g or f(b,"BannerPVP")or f(b,"SpiceCloud")m=f(GetContainerItemLink(0,i)or"","War Wolf")and i or m end if g then CastSpellByName("Ghost Wolf")end UseContainerItem(0,m)
```

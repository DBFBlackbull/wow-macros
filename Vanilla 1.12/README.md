# Welcome to Vanilla 1.12 macros
Here are some general macros that many people can use

### Default UI Setup
```
/run SetCVar("uiScale", 0.8)
/run PlayerFrame:ClearAllPoints() PlayerFrame:SetPoint("CENTER",UIParent,-190,-190)PlayerFrame:SetUserPlaced(true)
/run TargetFrame:ClearAllPoints() TargetFrame:SetPoint("CENTER",UIParent,190,-190)TargetFrame:SetUserPlaced(true)
/run if Abar_Frame then Abar_Frame:ClearAllPoints() Abar_Frame:SetPoint("CENTER",UIParent,-180,-160) Abar_Frame:SetUserPlaced(true) end
/run if ebar_Frame then ebar_Frame:ClearAllPoints() ebar_Frame:SetPoint("CENTER",UIParent,180,-160) ebar_Frame:SetUserPlaced(true) end
```

### Camera distance further to max
```
/console CameraDistanceMaxFactor 5
```

### Reset instance
```
/script ResetInstances()
```

### Spammable Start Auto-attack macro
```
/script if not PlayerFrame.inCombat then AttackTarget() end
```
### Spammable Start Shoot wand macro
```
/script if not IsAutoRepeatAction(40) then CastSpellByName("Shoot") end
```

The number `40` is the action bar slot where the auto-attack skill / Shoot wand skill is placed. See the image below for a reference of all slots
![WoW Actionbar Slotnumbers](https://github.com/DBFBlackbull/wow-macros/raw/master/img/wow-actionsbar-slotnumbers.jpg)

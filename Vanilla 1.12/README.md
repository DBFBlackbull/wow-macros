# Welcome to Vanilla 1.12 macros
Here are some general macros that many people can use

### Unlock and Lock player frame
Unlock
```
/script PlayerFrame:SetMovable(1)PlayerFrame:StartMoving()
```
Lock 
```
/script PlayerFrame:StopMovingOrSizing()PlayerFrame:SetMovable()
```

### Unlock and Lock target frame
```
/script TargetFrame:SetMovable(1)TargetFrame:StartMoving()
```
```
/script TargetFrame:StopMovingOrSizing()TargetFrame:SetMovable()
```

### Camera distance further to max
```
/console CameraDistanceMaxFactor 5
```

### Spammable Start Auto-attack macro
```
/script if not IsCurrentAction(40) then UseAction(40);end;
```
### Spammable Start Shoot wand macro
```
/script if not IsAutoRepeatAction(40) then CastSpellByName("Shoot") end
```

The number `40` is the action bar slot where the auto-attack skill / Shoot wand skill is placed. See the image below for a reference of all slots
![WoW Actionbar Slotnumbers](https://github.com/DBFBlackbull/wow-macros/raw/master/img/wow-actionsbar-slotnumbers.jpg)

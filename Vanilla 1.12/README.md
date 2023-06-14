# Welcome to Vanilla 1.12 macros
Here are some general macros that many people can use

### Spammable Start Auto-attack macro
```
if not IsCurrentAction(40) then UseAction(40);end;
```
### Spammable Start Shoot wand macro
```
/script if not IsAutoRepeatAction(40) then CastSpellByName("Shoot") end
```

The number `40` is the action bar slot where the auto-attack skill / Shoot wand skill is placed. See the image below for a reference of all slots
![WoW Actionbar Slotnumbers](https://github.com/DBFBlackbull/wow-macros/raw/master/img/wow-actionsbar-slotnumbers.jpg)

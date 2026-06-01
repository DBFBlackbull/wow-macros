Macro to chain together Judgement + renew Seal in action slot2 + Start Autoattack

In this example, the judgement spell is placed in slot 10 and the chosen seal is placed in slot 2
```
/run local r,u,_,cd=IsActionInRange(10),IsUsableAction(10),GetActionCooldown(10) if not u then UseAction(2) elseif r==1 and cd==0 then CastSpellByName("Judgement") SpellStopCasting() UseAction(2) end if not PlayerFrame.inCombat then AttackTarget() end
```

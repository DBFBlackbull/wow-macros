# Macros for Classic Era (Vanilla)

## Spell hit tables caps vs. Enemy level
| Level | Hit chance vs Monster | Spell hit cap vs Monster | Hit chance vs Player | Spell hit cap vs Player |
| ----- | ----                  | -----------              | --------             | ------------------      |
|  57   | 99%                   | 0%                       | 99%                  | 0%                      |
|  58   | 98%                   | 1%                       | 98%                  | 1%                      |
|  59   | 97%                   | 2%                       | 97%                  | 2%                      |
|  60   | 96%                   | 3%                       | 96%                  | 3%                      |
|  61   | 95%                   | 4%                       | 95%                  | 4%                      |
|  62   | 94%                   | 5%                       | 94%                  | 5%                      |
|  63   | 83%                   | 16%                      | 87%                  | 12%                     |

## Mage
### Frost/Fire hit chance table (Monster
```
/run h,l,_,_,_,_,t=GetCombatRatingBonus(8),UnitLevel("player"),GetTalentInfo(3,3);s="";for i=l,min(l+5,63) do d=(i-l);d=d+max(0,d-2)*10; s=s..format("\nLevel %d: %d%%",i,min(99,96-d+h+t*2)) end;print("Fire/Frost hit chance:"..s);
```

### Frost/Fire hit chance vs Target (monster)
```
/run h,u,n,_,_,_,_,t=GetCombatRatingBonus(8),UnitLevel,UnitName("target"),GetTalentInfo(3,3);l=u("player");i=u("target");d=(i-l);d=d>2 and d+(d-2)*10 or d;print(format("Chance to hit %s, %d\nFrost/Fire: %d%%",n,i,min(99,96-d+h+t*2)));
```

### Arcane hit chance table (Monster)
```
/run h,l,_,_,_,_,t=GetCombatRatingBonus(8),UnitLevel("player"),GetTalentInfo(1,2);s="";for i=l,min(l+5,63) do d=(i-l);d=d+max(0,d-2)*10; s=s..format("\nLevel %d: %d%%",i,min(99,96-d+h+t*2)) end;print("Arcane hit chance:"..s);
```

### Arcane hit chance vs Target (monster)
```
/run h,u,n,_,_,_,_,t=GetCombatRatingBonus(8),UnitLevel,UnitName("target"),GetTalentInfo(1,2);l=u("player");i=u("target");d=(i-l);d=d>2 and d+(d-2)*10 or d;print(format("Chance to hit %s, %d\nArcane: %d%%",n,i,min(99,96-d+h+t*2)));
```

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
### Frost/Fire hit chance
```
/run h,l,_,_,_,_,t=GetCombatRatingBonus(8),UnitLevel("player"),GetTalentInfo(3,3);s=f("\nLevel %d: %d%%",l+3,min(99,83+h+t*2));for i=l+2,l,-1 do s=format("\nLevel %d: %d%%",i,min(99,96-(i-l)+h+t*2))..s end;print("Fire/Frost hit chance:"..s);
```

### Arcane hit chance
```
/run h,l,_,_,_,_,t=GetCombatRatingBonus(8),UnitLevel("player"),GetTalentInfo(1,2);s=f("\nLevel %d: %d%%",l+3,min(99,83+h+t*2));for i=l+2,l,-1 do s=format("\nLevel %d: %d%%",i,min(99,96-(i-l)+h+t*2))..s end;print("Fire/Frost hit chance:"..s);
```

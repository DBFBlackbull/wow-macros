# Welcome
Welcome to my repository of macros.

After many hours of coding and testing I found it stupid that I alone enjoy all of this, so here it is for all of you to see and use!

## General macros
These are some general macros that should work for all versions of WoW
### LFG to multiple chat channels
```
/run msg="{circle} LF1M for Botanica HC. DPS+Healer. Can summon {circle}"; for i=2,6 do SendChatMessage(msg, "CHANNEL", nil, i) end;
```
### Boolean debug
```
/script value=xx; if value then DEFAULT_CHAT_FRAME:AddMessage("true") else DEFAULT_CHAT_FRAME:AddMessage("false") end DEFAULT_CHAT_FRAME:AddMessage(value);
```
Here is some output of various values for quick references
| Input     | \| | Boolean | Output    | 
| ------    | -- | ------- | ------    |
| `true`    | \| | true    | `true`    |
| `false`   | \| | false   | `false`   |
| `"true"`  | \| | true    | `true`    |
| `"false"` | \| | true    | `false`   |
| `1`       | \| | true    | `1`       |
| `0`       | \| | true    | `0`       |
| `"1"`     | \| | true    | `1`       |
| `"0"`     | \| | true    | `0`       |
| `nil`     | \| | false   | *Nothing* |
| `"nil"`   | \| | true    | `nil`     |

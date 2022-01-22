# Welcome
Welcome to my repository of macros.

After many hours of coding and testing I found it stupid that I alone enjoy all of this, so here it is for all of you to see and use!

## General macros
These are some general macros that should work for all versions of WoW
### LFG to multiple chat channels
```
/run msg="{circle} LF1M for Botanica HC. DPS+Healer. Can summon {circle}"; for i=2,6 do SendChatMessage(msg, "CHANNEL", nil, i) end;
```

# i0rb Admin System v2.0

![Admin Orb Preview](https://i.imgur.com/orb_preview.png)  
*Visual orb following the admin player*

## 📝 Description
A comprehensive admin control system featuring:
- Custom floating orb visual effect
- 40+ player management commands
- Persistent ban system
- In-game music player
- Interactive GUI interfaces

## ⚙️ Installation
### LocalScript Usage (Single Player)
1. Place script in `StarterPlayerScripts`
2. Configure settings:
```lua
local Admins = game.Players.LocalPlayer -- Admin designation
local Speed = 0.05 -- Orb rotation speed
local Distance = 5 -- Orb follow distance
local Prefix = ":" -- Command prefix

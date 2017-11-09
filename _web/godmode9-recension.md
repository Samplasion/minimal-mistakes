---
title: "GodMode9 recension"
date: 2017-11-07 07:31:00 +0100
tags: recension
excerpt: "GodMode9, like the name says, is an omnipotent tool made to edit internal components of the FW."
---
## Description and Usage
GodMode9 ("GM9") isn't *just* a file manager.
It's a complete modding tool for the 3DS.<!--more-->
You open GM9 by pressing START at the boot. You'll be now greeted by a unit selection screen [SD, SysNAND, EmuNANDs, Gamecart].
By pressing [HOME] you open additional options.
[For example, to dump a cartridge](https://3ds.guide/godmode9-usage)
### To dump a cartridge
{% capture notice %}
+ Insert the game cartridge you intend to dump into your device
  + 3DS game cartridges will be dumped to an installable `.cia` format
  + NDS game cartridges will be dumped to a non-installable `.nds` format compatible with flashcarts and emulators
{% endcapture %}

<div class="notice--info">{{ notice | markdownify }}</div>

1. Launch GodMode9 by holding (Start) during boot
1. Navigate to `[C:] GAMECART`
1. Follow the steps applicable to your game cartridge:
  + **3DS Game Cartridge:** Press (A) on `[TitleID].trim.3ds` to select it, then select "NCSD image options...", then select "Build CIA from file"
  + **NDS Game Cartridge:** Press (A) on `[TitleID].trim.nds` to select it, then select "Copy to 0:/gm9/out"
1. Your installable `.cia` or non-installable `.nds` formatted file will be outputted to the `/gm9/out/` folder on your SD card

## My Considerations
GodMode9, like the name says, is an omnipotent tool made to edit internal components of the FW.

### Pros
* Open-source
* It asks for permission before editing vital parts of the system, avoiding potential bricks.

### Cons
* GUI could be better

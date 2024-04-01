---
_schema: default
layout: default
title: Full Server Fix + VIP
nav_order: 3
nav_exclude: false
parent: Official mods
has_children: false
has_toc: false
last_modified_date:
---
![](https://img.shields.io/badge/LiFx%20Server%20-%3Ev3.0.0-green "Requires LiFx server framework minimum v3.0.0")![](https://img.shields.io/badge/MariaDB%20-%3Ev5.5.49-green "Tested with MariaDB v5.5.49")

# Full Server Fix + VIP

[Download here](https://github.com/LiF-x/FullServerFixVIP/releases/latest){: .btn.fs-5.mb-4.mb-md-0.mr-2}

## About

<br>The original code of Life is Feudal does not stop you from connecting before the player spawns in the world at a 64/64 max capped server.<br>This mod ensures that the player is kicked on character screen if the server is full, avoiding unnecessary load on the server as the connecting client would not be allowed in after being sent the latest map data. The process of sending map data to the client is resource intensive.&nbsp;<br>The mod was made when several servers were player capped for PVP and several people used SkunkFu's method of auto joining the server to gain a free slot.&nbsp;<br>Thus using this mod would minimize the impact for the 64 players already connected and playing.

VIP enables you to have reserved slots for your VIP players or admins. Any player that has been afk would be eligble to be kicked to provide a slot for the connecting VIP

### Installation Instructions

To Install this mod, ensure you have the LiFx FrameWork installed [Download here](http://lifxmod.com)

Add this mod to the mods folder

This is not compatible with the standard Full server Fix - Please ensure this is deleted before installing this.

Using the mod To USE this mod open your Database table "account"

Set VIPFlag Column for the Account you wish to have as a VIP, Please check with the steam ID Before Issuing.

When the server is full when a person with a vip flag attempts to join the server, any AFK Player will be removed from the game to allow VIP Access This is useful for heavily populated servers as alot of people will sit on the server afk for hours otherwise!
---
_schema: default
layout: default
title: Full Server Fix
nav_order: 2
nav_exclude: false
parent: Official mods
has_children: false
has_toc: false
last_modified_date: 2022-12-09 12:22:33
---
# Full Server Fix

[Download here](https://github.com/LiF-x/FullServerFix/releases/tag/v1.0.0){: .btn.fs-5.mb-4.mb-md-0.mr-2}

## About

<br>The origian code of Life is Feudal does not stop you from connecting before the player spawns in the world at a 64/64 max capped server.<br>This mod ensures that the player is kicked on character screen if the server is full, avoiding unnecessary load on the server as the connecting client would not be allowed in after being sent the latest map data. The process of sending map data to the client is resource intensive.&nbsp;<br>The mod was made when several servers were player capped for PVP and several people used SkunkFu's method of auto joining the server to gain a free slot.&nbsp;<br>Thus using this mod would minimize the impact for the 64 players already connected and playing.

### Installation instructions

Download the latest package from the above link. Stop your server Remove older versions of the mod Upload the zip file you downloaded in step 1. to the "mods" folder in your server via file manager or ftp. Extract the zip file inside the mods folder. Delete the mod zip file you uploaded (important!) Start the server
---
_schema: default
layout: default
title: Bell Tower Fix
nav_order: 1
nav_exclude: false
parent: Client Only Mods
has_children: false
has_toc: false
last_modified_date:
---
![](https://img.shields.io/badge/LiFx%20Server%20-%3Ev3.0.0-green "Requires LiFx server framework minimum v3.0.0")![](https://img.shields.io/badge/MariaDB%20-%3Ev5.5.49-green "Tested with MariaDB v5.5.49")

# Bell Tower fix

Life Is Feudal Bell Tower fix - This is a bell tower fix for lif yo, to allow sounds to work

[Download here](https://github.com/LiF-x/Belltower-Fix/releases/latest)&nbsp;

### Installation instructions

1. Download the latest package from the above link.

2. Extract the contents of the zip to a local folder

3. Edit your cm_objects.xml and add the contents from the included data/bellfix.xml Thus replacing the entire block for <!--name = AlarmBell_3rdTier-->
- usually from line 25833 to 25938
- IF YOU HAVE NOT PREVIOUSLY EDITED THE cm_objects file, the provided modpack.zip can be extracted to add whatever else you require - cm_objects is pre done for you inside the zip file assuming no other changes have been made.
### This is a client side mod ONLY so it is to be shared with the client in the modpack not the server

4. Add the Belltower fix folder into your yo launcher package inside the following file path
/yolauncher/modpack/mods/LiFx 

5. Add any other amendents you wish to use for the yo launcher mod pack

6. Upload the modpack to the Yo Launcher Website

[Official Documentation](https://yolauncher.app/documentation)
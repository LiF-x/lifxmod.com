---
_schema: default
layout: default
title: Church
nav_order: 6
nav_exclude: false
parent: Official mods
has_children: false
has_toc: false
last_modified_date: 2022-12-16 19:03:30
---
![](https://img.shields.io/badge/LiFx%20Server%20-%3Ev3.0.0-green "Requires LiFx server framework minimum v3.0.0")![](https://img.shields.io/badge/MariaDB%20-%3Ev5.5.49-green "Tested with MariaDB v5.5.49")

# Church

The Church from LIF:MMO recreated for LIF:YO [Download here](https://github.com/LiF-x/Church/releases/latest)

### Installation instructions

1. Download the latest package from the above link.

2. Extract the contents of the zip to a local folder

3. Remove older versions of the mod from your server

4. Upload the contents of the folder "mods" to the server

5. Upload the contents of the folder "yolauncher" to the server

6. Edit skill\_types.xml on the server,

   1. add "2485" to the id list inside of "Praise the God!" ability. (Normally on line# 5574)

   2. add "2485" to the id list inside of "Open/Close Door" ability. (Normally on line# 6019)

   3. add "2485" to the id list inside of "as Your Home" ability. (Normally on line# 6036)

   4. add "2485" to the id list inside of "Toll" ability. (Normally on line# 7098)

   5. add "2485" to the id list inside

   6. of "Expel the Intruders." (Normally on line# 7537)

7. Edit cm\_objects.xml in the data folder on the server and add the contents from the data/church.xml file at the end, before &lt;/objects&gt;

8. Use LiFx Server framework v3.0.0 or newer with $LiFx::createDataXMLS set to true in AutoloadConfig.cs to create objects\_types.xml, recipe.xml and recipe\_requirement.xml on the server and start the server.

9. Stop the server and copy files on the server from /LiFx/dbexport to your servers /data folder

10. Download cm\_objects.xml, objects\_types.xml, recipe.xml, skill\_types.xml and recipe\_requirement.xml from the servers to your extracted "yolauncher/modpack/data" folder.

11. Ensure you have 7zip installed on your computer [Download here](https://7zip.dev/en/download/)

12. Ensure all you need is in the pack and insert files into the yo launcher folder that you need for your server, ensuring you do not overwrite the mod files

13. Run the "createModpack.bat" included in this pack to generate a mod pack to upload to [Yo Launcher](https://www.yolauncher.app/)

14. Upload to Yo Launcher as normal

15. Enjoy
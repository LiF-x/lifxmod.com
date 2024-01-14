---
_schema: default
layout: default
title: Signs
nav_order: 14
nav_exclude: false
parent: Official mods
has_children: false
has_toc: false
last_modified_date: 2024-01-14 01:38:57
---

##This is a pre release!

![](https://img.shields.io/badge/LiFx%20Server%20-%3Ev3.0.0-green "Requires LiFx server framework minimum v3.0.0")![](https://img.shields.io/badge/MariaDB%20-%3Ev5.5.49-green "Tested with MariaDB v5.5.49")

&nbsp;Introduction of LiFx Signs

![](/uploads/signs.png){: width="1915" height="689"}

Pre-requisite assumptions made:

1. Your server is using [LiFx Server Framework](/Docs/server-framework)
2. Your server is connected to [YoLauncher.app](https://YoLauncher.app)

[Download signs here](https://github.com/LiF-x/signs/releases/latest){: .btn.fs-5.mb-4.mb-md-0.mr-2}

### Installation instructions&nbsp;

1. Download the latest package from the above link.

2. Extract the contents of the zip to a local folder (the tutorial assumes you are working from the extracted base directory for all local instructions)

3. Remove older versions of the mod from your server

4. Upload the contents of the folder "mods" to the server

5. Upload the contents of the folder "yolauncher" &nbsp;to the server&nbsp;

6. Use LiFx Server framework v3.0.0 or newer with $LiFx::createDataXMLS set to true in AutoloadConfig.cs to create objects\_types.xml, recipe.xml and recipe\_requirement.xml on the server and start the server.

7. Stop the server and copy files on the server from /LiFx/dbexport to your servers /data folder

8. Download &nbsp;recipe.xml and recipe\_requirement.xml from the servers generated xml files (in the LiFx Folder) to your extracted "yolauncher/modpack/data" folder.

9. Download cm\_objects.xml and skill\_types from the servers data folder to your extracted "yolauncher/modpack/data" folder.

10. Ensure you have 7zip installed on your computer [Download here](https://7zip.dev/en/download/)

11. Ensure all you need is in the pack and insert files into the yo launcher folder that you need for your server, ensuring you do not overwrite the mod files without checking your are moving a more up to date version with the correct information.

### Ensure these files as already mentioned are on your server&nbsp;

\- cm\_objects.xml &nbsp;(included in pack).<br>\- object\_types.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe\_requirement.xml (Built for you as mentioned on the server and can be found in the db export folder ).​​​

### Ensure the files are in the data folder YOU prepared for yo launcher.&nbsp;

\- cm\_objects.xml &nbsp;(included in pack).<br>\- object\_types.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe\_requirement.xml (Built for you as mentioned on the server and can be found in the db export folder ).​​​

1. ​​Run the "createModpack.bat" included in this pack to generate a modpack .zip to upload to your server on&nbsp;[Yo Launcher](https://www.yolauncher.app/)&nbsp;

2. Upload to Yo Launcher as normal&nbsp;

3. Set modpack as active

4. (Re)Launch YoLauncher to download the modpack for your client and join your server.
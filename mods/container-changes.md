---
_schema: default
layout: default
title: Container changes
nav_order: 4
nav_exclude: false
parent: Official mods
has_children: false
has_toc: false
last_modified_date:
---
# Container Changes

&nbsp;Introduction of Automated Container changes&nbsp;

[Download here](https://github.com/LiF-x/Knool-Pack/releases/latest)

**Coming Soon…**<br><br>Automated Container change mod.<br><br>This will change the container sizes for warehouses etc, giving your server Larger storage Capacity and a framework to make future changes.







### Installation instructions&nbsp;

1. Download the latest package from the above link.

2. Extract the contents of the zip to a local folder

3. Remove older versions of the mod from your server

4. Upload the contents of the folder "mods" to the server


5. Stop the server and copy files on the server from /LiFx/dbexport to your servers /data folder
 - Ensure the Autoload Config is set to true (this is found in your mods folder once the LiFx FrameWork is installed on your server)
 Example - $LiFx::createDataXMLS = true; // To create recipe, recipe_requirements and objects_types xml from the database


6. Download &nbsp;objects\_types.xml from the servers generated xml files (in the LiFx Folder)
- To your Servers "Data Folder" 
- To your "yolauncher/modpack/data" folder.

7. Ensure you have 7zip installed on your computer [Download here](https://7zip.dev/en/download/)

8. Ensure all you need is in the pack and insert files into the yo launcher folder that you need for your server, ensuring you do not overwrite the mod files without checking your are moving a more up to date version with the correct information.<br><br>\*\*XMLS REQUIRED FOR THIS MOD\*\*<br>\- skilltypes.xml (needs to be built as mentioned above).<br>\- cm\_equipTypes.xml (needs to be built as mentioned above).<br>\- cm\_spawn\_patterns.xml ( ensure all knools are on this )<br>\- cm\_objects.xml &nbsp;(needs to be built as mentioned above).<br>\- object\_types.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe\_requirement.xml (Built for you as mentioned on the server and can be found in the db export folder ).​​​<br><br>\\

\###Ensure these files as already mentioned are on your server&nbsp;

\###Ensure the files are in the data folder YOU prepared for yo launcher.&nbsp;

1. ​​Run the "createModpack.bat" included in this pack to generate a mod pack to upload to [Yo Launcher](https://www.yolauncher.app/)

2. Upload to Yo Launcher as normal&nbsp;

3. Enjoy
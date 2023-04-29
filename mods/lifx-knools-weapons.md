---
_schema: default
layout: default
title: LiFx Knool Pack
nav_order: 7
nav_exclude: false
parent: Official mods
has_children: false
has_toc: true
last_modified_date:
---
# KnoolPack

&nbsp;Introduction of Knools and knool weapons&nbsp;

[Download here](https://github.com/LiF-x/Knool-Pack/releases/latest)

### Installation instructions&nbsp;

1. Download the latest package from the above link.

2. Extract the contents of the zip to a local folder

3. Remove older versions of the mod from your server

4. Upload the contents of the folder "mods" to the server

5. Upload the contents of the folder "yolauncher" &nbsp;to the server&nbsp;

6. Edit **Your** skill\_types.xml on the server,

   1. &nbsp;Add "2399 2359 2360 2361 2362" to the id list inside&nbsp;

      <ent_req type="object_type_id">1070 1083 924 925 926 927 928 929 930 931 932 933 934 935 936 1090 1460&nbsp;</ent_req>of Loot! ability. (Normally on line# 6073)

   2. Add "2465" inside&nbsp;

      <ent_req type="object_type_id">47 48 49 1466</ent_req>&nbsp;of Shape Stones Ability (Normally on line# 1902)

7. Copy all data from Knool\_cm\_equipTypes.xml and paste at the bottom of **Your** cm\_equipTypes.xmll in the data folder on the server&nbsp; Please Note: Ensure you paste over the top of this tag &lt;/equipment\_types&gt; as the Knool\_cm\_equipTypes.xml includes this.

8. &nbsp;Copy all Data from knool\_cm\_objects and paste at the bottom of your cm\_objects.xml<br>\- Ensure you do not overwrite the final line "&lt;/object\_types&gt;" This is required to complete the xml file.

9. Upload the "data\\ai" folder (including content) to your servers data folder.

10. Use LiFx Server framework v3.0.0 or newer with $LiFx::createDataXMLS set to true in AutoloadConfig.cs to create objects\_types.xml, recipe.xml and recipe\_requirement.xml on the server and start the server. (This mod however only requires the object\_types.xml)

11. Stop the server and copy files on the server from /LiFx/dbexport to your servers /data folder

12. Download &nbsp;objects\_types.xml, recipe.xml, skill\_types.xml and recipe\_requirement.xml from the servers generated xml files (in the LiFx Folder) to your extracted "yolauncher/modpack/data" folder.

13. Download cm\_objects.xml from the servers data folder to your extracted "yolauncher/modpack/data" folder.

14. Ensure you have 7zip installed on your computer [Download here](https://7zip.dev/en/download/)

15. Ensure all you need is in the pack and insert files into the yo launcher folder that you need for your server, ensuring you do not overwrite the mod files without checking your are moving a more up to date version with the correct information.<br><br>**XMLS REQUIRED FOR THIS MOD**<br>\- skilltypes.xml (needs to be built as mentioned above).<br>\- cm\_equipTypes.xml (needs to be built as mentioned above).<br>\- cm\_spawn\_patterns.xml ( ensure all knools are on this )<br>\- cm\_objects.xml &nbsp;(needs to be built as mentioned above).<br>\- object\_types.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe\_requirement.xml (Built for you as mentioned on the server and can be found in the db export folder ).​​​<br>

### Ensure these files as already mentioned are on your server&nbsp;

### Ensure the files are in the data folder YOU prepared for yo launcher.&nbsp;

1. ​​Run the "createModpack.bat" included in this pack to generate a mod pack to upload to [Yo Launcher](https://www.yolauncher.app/)

2. Upload to Yo Launcher as normal&nbsp;

3. Enjoy
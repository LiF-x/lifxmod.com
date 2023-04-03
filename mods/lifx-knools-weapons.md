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

 Introduction of Knools and knool weapons 

[Download here](https://github.com/LiF-x/Knool-Pack/releases/latest)

### Installation instructions 

1. Download the latest package from the above link.

2. Extract the contents of the zip to a local folder

3. Remove older versions of the mod from your server

4. Upload the contents of the folder "mods" to the server

5. Upload the contents of the folder "yolauncher"  to the server 

5. Edit **Your** skill_types.xml on the server,

    5A). Add "2399 2359 2360 2361 2362" to the id list inside <ent_req type="object_type_id">1070 1083 924 925 926 927 928 929 930 931 932 933 934 935 936 1090 1460</ent_req> of Loot! ability. (Normally on line# 6073)

    5B). Add "2465" inside <ent_req type="object_type_id">47 48 49 1466</ent_req> of Shape Stones Ability (Normally on line# 1902)

6. Copy all data from Knool_cm_equipTypes.xml and paste at the bottom of **Your** cm_equipTypes.xmll in the data folder on the server 
Please Note: Ensure you paste over the top of this tag </object_types> as the Knool_cm_equipTypes.xml includes this.

7. Upload the ai folder (including content) to your servers data folder.

7. Use LiFx Server framework v3.0.0 or newer with $LiFx::createDataXMLS set to true in AutoloadConfig.cs to create objects_types.xml, recipe.xml and recipe_requirement.xml on the server and start the server. (This mod however only requires the object_types.xml)

8. Stop the server and copy files on the server from /LiFx/dbexport to your servers /data folder

8. Download  objects_types.xml, recipe.xml, skill_types.xml and recipe_requirement.xml from the servers generated xml files (in the LiFx Folder) to your extracted "yolauncher/modpack/data" folder.

9. Ensure you have 7zip installed on your computer [Download here](https://7zip.dev/en/download/)

10. Ensure all you need is in the pack and insert files into the yo launcher folder that you need for your server, ensuring you do not overwrite the mod files without checking your are moving a more up to date version with the correct information 

11. Run the "createModpack.bat" included in this pack to generate a mod pack to upload to [Yo Launcher](https://www.yolauncher.app/)

12. Upload to Yo Launcher as normal 

13. Enjoy
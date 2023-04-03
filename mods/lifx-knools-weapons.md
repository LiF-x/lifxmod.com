---
_schema: default
layout: default
title: LiFx Knool Pack
nav_order: 7
nav_exclude: false
parent: Official mods
has_children: false
has_toc: false
last_modified_date:
---
\# KnoolPack

&nbsp;Introduction of Knools and knool weapons&nbsp;

\[Download here\](https://github.com/LiF-x/Knool-Pack/releases/latest)

\### Installation instructions

1\. Download the latest package from the above link.

2\. Extract the contents of the zip to a local folder

3\. Remove older versions of the mod from your server

4\. Upload the contents of the folder "mods" to the server

5\. Upload the contents of the folder "yolauncher" &nbsp;to the server&nbsp;

5\. Edit \*\*Your\*\* skill\_types.xml on the server,

&nbsp; &nbsp; 5A). Add "2399 2359 2360 2361 2362" to the id list inside &lt;ent\_req type="object\_type\_id"&gt;1070 1083 924 925 926 927 928 929 930 931 932 933 934 935 936 1090 1460&lt;/ent\_req&gt; of Loot! ability. (Normally on line# 6073)

&nbsp; &nbsp; 5B). Add "2465" inside &lt;ent\_req type="object\_type\_id"&gt;47 48 49 1466&lt;/ent\_req&gt; of Shape Stones Ability (Normally on line# 1902)

6\. Copy all data from Knool\_cm\_equipTypes.xml and paste at the bottom of \*\*Your\*\* cm\_equipTypes.xmll in the data folder on the server&nbsp;<br>Please Note: Ensure you paste over the top of this tag &lt;/object\_types&gt; as the Knool\_cm\_equipTypes.xml includes this.

7\. Upload the ai folder (including content) to your servers data folder.

7\. Use LiFx Server framework v3.0.0 or newer with $LiFx::createDataXMLS set to true in AutoloadConfig.cs to create objects\_types.xml, recipe.xml and recipe\_requirement.xml on the server and start the server. (This mod however only requires the object\_types.xml)

8\. Stop the server and copy files on the server from /LiFx/dbexport to your servers /data folder

8\. Download &nbsp;objects\_types.xml, recipe.xml, skill\_types.xml and recipe\_requirement.xml from the servers generated xml files (in the LiFx Folder) to your extracted "yolauncher/modpack/data" folder.

9\. Ensure you have 7zip installed on your computer \[Download here\](https://7zip.dev/en/download/)

10\. Ensure all you need is in the pack and insert files into the yo launcher folder that you need for your server, ensuring you do not overwrite the mod files without checking your are moving a more up to date version with the correct information&nbsp;

11\. Run the "createModpack.bat" included in this pack to generate a mod pack to upload to \[Yo Launcher\](https://www.yolauncher.app/)

12\. Upload to Yo Launcher as normal&nbsp;

13\. Enjoy
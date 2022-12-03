---
layout: default
nav_order: 99
last_modified_date: 2022-12-03 12:48:22 +0000
title: FAQ
nav_exclude: false
has_children: true
has_toc: false
published: false

---
# Frequently Asked Questions

##   
How can I remove an invisible cart from my server?

  
1) stand on the cart in game

2) use Below command in server console to gain the geo id of the cart whilst looking down at it

$TerrainSelection::debug_drawCellInfo = 1;

3) Goto table Objects_Patch in database

4) use the geo id in game to find the cart.

you can cheat using a query changing the geo id to your needs

SELECT * FROM lif_10.objects_patch WHERE GeoDataID = 117521895

 ORDER BY ObjectTypeID ASC LIMIT 1000;

SHOW TABLE STATUS LIKE 'objects_patch';

you can confirm you are looking at the correct object as ObjectTypeID for this item will be 1497 

5) checking the container to make sure cart is empty

\- Goto table "moveable_objects" and use the object id from objects patch with this query (replacing "Where ID = 72125" with yours)

SELECT * FROM lif_10.movable_objects WHERE ID = 72125

 ORDER BY ID DESC LIMIT 1000;

SHOW TABLE STATUS LIKE 'movable_objects';

From here you can gain the RootContainerID

6) find the container and ensure Object type id Match using your container ID

SELECT * FROM lif_10.containers WHERE ID = 72584

 LIMIT 1000;

SHOW TABLE STATUS LIKE 'containers';

\[14:11\]Server Monitor: 7) Goto items table and use your container ID with the following query, any items inside the cart will show up. in this case cart is empty so no need to transfer items to new container.

SELECT * FROM lif_10.items WHERE ContainerID = 72584

 ORDER BY ObjectTypeID ASC LIMIT 1000;

SHOW TABLE STATUS LIKE 'items';

8) Time to delete all of the above.

Delete the lines associated with the cart from the following

moveable_objects

Objects_Patch

Containers

ENSURE ANY DELETIONS ARE ONLY FOR THE OBJECT TYPE YOU WISH TO REMOVE

9) AS A PRECAUTION IT IS SMART TO RUN THIS COMMAND IN PING PERFECT CONSOLE AFTER DELETIONS

stretchedPatchMaintenance();

WAIT FOR IT TO SAY THE MAINTENANCE IS COMPLETE

10)  RESTART SERVER or allow server to restart naturally.

\- it is important to allow the server to save data otherwise patch maintenance error can occur, this is difficult to resolve  
  
  
  
  
 
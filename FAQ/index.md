---
layout: default
nav_order: 99
last_modified_date: 2022-12-03 12:48:22 +0000
title: FAQ
nav_exclude: false
has_children: false
has_toc: false
published: false

---
# Frequently Asked Questions

## How can I remove an invisible cart from my server?

**Locating the cart in your Database**

1.  Stand on the cart in game
2.  Use Below command in server console to gain the geo id of the cart whilst looking down at it

   $TerrainSelection::debug_drawCellInfo = 1;
3.  Goto table Objects_Patch in database
4. Use the geo id in game to find the cart.

   You can cheat using a query changing the "GeoDataID" to your needs

        SELECT * FROM objects_patch WHERE GeoDataID = 117521895

 ORDER BY ObjectTypeID ASC LIMIT 1000;

SHOW TABLE STATUS LIKE 'objects_patch';

you can confirm you are looking at the correct object as ObjectTypeID for this item as it will be 1497 for horse cart no tent or 1461 for horse cart with tent

**Checking the container to make sure cart is empty**

1.  goto table "moveable_objects" and use the object id from objects patch with this query (replacing "Where ID = 72125" with the ID provided by the last step)

       SELECT * FROM movable_objects WHERE ID = 72125 ORDER BY ID DESC LIMIT 1000;SHOW TABLE STATUS LIKE 'movable_objects';

**Finding the container and ensure Object type id Match using your container ID**

1. 

        SELECT * FROM containers WHERE ID = 72584 LIMIT 1000;SHOW TABLE STATUS LIKE 'containers';
2.  Goto the items table and use your container ID with the following query, any items inside the cart will show up. in this case cart is empty so no need to transfer items to new container.

    SELECT * FROM items WHERE ContainerID = 72584 ORDER BY ObjectTypeID ASC LIMIT 1000;SHOW TABLE STATUS LIKE 'items';

**Time to delete all of the above**

Delete the lines associated with the cart from the following

moveable_objects

Objects_Patch

Containers

**ENSURE ANY DELETIONS ARE ONLY FOR THE OBJECT TYPE YOU WISH TO REMOVE**

9) AS A PRECAUTION IT IS SMART TO RUN THIS COMMAND IN SERVER CONSOLE AFTER DELETIONS

    stretchedPatchMaintenance();

WAIT FOR IT TO SAY THE MAINTENANCE IS COMPLETE

10)  RESTART SERVER.

\- it is important to allow the server to save data otherwise patch maintenance error can occur, this is difficult to resolve  
  
  
  
  
 
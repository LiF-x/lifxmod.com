---
layout: default
last_modified_date: 2022-12-04T10:36:11.000+00:00
title: How to create an admin land
nav_order: 11
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false
published: false

---
How can i create a admin land and ability's to perform actions on it  
  
  
How to locate GeoID of particular terrain tiles  
use the Tilde key \~  (usually above Tab)  
**$TerrainSelection::debug_drawCellInfo = 1;  
**  
In order to create a Admin land, use this command in the console:

* **/adminland create geoId1 geoId2**

Where geoId1 and geoId2 are two corners of the claim.  
  
To learn the geoId, you need to use this command in the console:

* **$TerrainSelection::debug_drawCellInfo = 1;**

You can create an infinite number of admin claims. And in order to remove a particular claim, you must stand on it and use this command in the console:

* **/adminland delete**
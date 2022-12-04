---
layout: default
last_modified_date: 2022-12-04T10:36:11.000+00:00
title: How to create an admin land
nav_order: 11
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false

---
### How can I create a new admin land

How to locate GeoID of particular terrain tiles  
press ctrl & Tilde key \~ (usually above Tab) This will bring up the in game Console as pictured below  
  
![](/uploads/ingameconsole.png)  
  
once the console is up paste the following into it

> **$TerrainSelection::debug_drawCellInfo = 1;**

You will then start to see the Geo IDS as pictured below**  
  
![](/uploads/geoidinfo.png)  
**With this step done simply look at the tile you wish to gain a Geo id and it would be the Geo ID next to "SEL: ter" then replace geoid1 and geoid2 using this process with the geo ids you wish to use.

* **/adminland create geoId1 geoId2 name of adminland**

Example:

> **/adminland create** 117360041 117372821 AdminLands

>   
> **Quick Tip:** To clean up confusion with geo ids please check below  
> Where geoId1 and geoId2 are two corners of the claim.  
>   
> ![](/uploads/geoidpreference.png)  
> You can create an infinite number of admin claims. And in order to remove a particular claim, you must stand on it and use this command in the console:

> **/adminland delete**
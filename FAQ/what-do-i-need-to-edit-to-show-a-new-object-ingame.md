---
layout: default
last_modified_date: 2022-12-05 19:29:22 +0000
title: what do I need to edit to show a new object ingame
nav_order: 7
nav_exclude: false
parent: FAQ
has_children: false
has_toc: false

---
### **what do I need to edit to show a new object ingame?**

**The xmls you need to edit to add new objects to be viewable ingame**

**Client side**

1.  Create an object for your model in /data/cm_objects.xml
2.  Create an entry for your object type in /data/object_types.xml
3.  Create a recipe for your new object in /data/recipe.xml
4.  Create a recipe requirement to build this object in /data/recipe_requirement.xml

**Server side**

1. Create an object for your model in /data/cm_objects.xml
2. create SQL entry's for object_types table in your lif database
3. create SQL entry's for the recipe table in your lif database
4. create SQL entry's for the recipe_requirement table..

voila your model is now buildable ingame.
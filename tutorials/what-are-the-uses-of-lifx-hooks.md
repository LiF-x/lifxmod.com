---
layout: default
last_modified_date: 2022-12-08 18:27:21 +0000
title: what are the uses of LiFx Hooks
nav_order: 10
nav_exclude: false
parent: FAQ
has_children: false
has_toc: false
published: false

---
### What are the uses of LiFx Hooks?

In order to help people knowing what hooks to trigger for what purpose   
Below is a list of them and their uses.

**This is good for Adding new objects to database**

**Replacing** LiFxhooks with your mod name

> LiFx::registerCallback($LiFx::hooks::onServerCreatedCallbacks, Dbchanges, LiFxhooks);

**The below is good for Adding the following:**

1. updating Container sizes
2. Creating new triggers
3. Updating original Container sizes of Vanilla buildings

**Replacing** LiFxhooks with your mod name

> LiFx::registerCallback($LiFx::hooks::onInitServerDBChangesCallbacks, ConChanges, LiFxhooks);

**The below would be to add new objects to your mod to allow for auto set up in the database.**

1. **Replacing** LiFxhooks with your mod name
2. **Replacing** ObjectsTypesWoodenCross() With your item name e.g. ObjectsTypesNewItem() **Ensure () Remains at the end**

> LiFx::registerObjectsTypes(LiFxhooks::ObjectsTypesWoodenCross(), LiFxhooks);

![](/uploads/lifxhooksobjecttypes.png)

**The below is good for adding new DataBlocks**

**Replacing** LiFxhooks with your mod name

**The below is good for Adding the following:**

1. New Weapons
2. New AI 

> LiFx::registerCallback($LiFx::hooks::onDatablockLoad, RegisterNewDatablock, LiFxhooks);

**The below is good for adding Materials to new Objects  
  
Replacing** LiFxhooks with your mod name

> LiFx::registerCallback($LiFx::hooks::onMaterialsLoad, RegisterNewMaterial, LiFxhooks);

**The below is good for changing gui images such as:**

1. **Loading screens**
2. **Loading Video**
3. **Ingame menus**
4. **Ingame map**

**Replacing** LiFxhooks with your mod name

> LiFx::registerCallback($LiFx::hooks::onInitialized, onInitialized, LiFxhooks);
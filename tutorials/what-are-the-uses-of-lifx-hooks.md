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

In order to help people knowing what hooks to trigger here is a list of them and their uses.

This is good for Adding new objects to database

> LiFx::registerCallback($LiFx::hooks::onServerCreatedCallbacks, Dbchanges, );

This is good for Editing Existing lines for original items -

Perfect for updating Container sizes

> LiFx::registerCallback($LiFx::hooks::onInitServerDBChangesCallbacks, ConChanges, LiFxhooks);

The below would be to add new objects to your mod to allow for auto set up in the database.

LiFx::registerObjectsTypes(LiFxhooks::ObjectsTypesWoodenChurch(), LiFxhooks);

![](/uploads/lifxhooksobjecttypes.png)
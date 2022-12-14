---
layout: default
last_modified_date: 2022-12-05 20:11:12 +0000
title: I built the stone bridge off feudal tools, how can this be removed
nav_order: 6
nav_exclude: false
parent: FAQ
has_children: false
has_toc: false

---
### I built the stone bridge off feudal tools, how can this be removed?

The simplest method to remove the bridge 

> Please note: This below solution will remove all Stone blocks from the server

Turn off the server and run the below query using HeidiSql or a similar program 

    DELETE FROM movable_objects WHERE ObjectTypeID = '1374';
    DELETE FROM objects_patch WHERE ObjectTypeID = '1374';

when the server starts back up it may take some time to start back up - This is normal.
---
layout: default
last_modified_date: 2022-12-03 15:35:22 +0000
title: Permanently disable skill
nav_order: 2
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false
published: false

---
### Permanently disable skill

  
  
To **permanently disable a feature in the game**. We can add the following line of code in the “**skill_types.xml**” file. This line will make that ability only usable in the world we select.

    <req type="world">green</req>

EXAMPLE:

If we have our server in “red world” we will add “green world”.

In this way this ability will only be usable in a green world and our world, not being green, will not appear.  
In my case I have disabled the interact ability. So that the missions of the npcs disappear forever.

    <ability lvl="0" name="Interact" id="297">
        <duration const="">0</duration>
        <ability_skill_mult>0</ability_skill_mult>
        <entities/>
        <!-- entities are defined in quests_subjects.xml -->
        <requirements>
            <req type="world">green</req>
        </requirements>
        <results/>
    </ability>
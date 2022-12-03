---
layout: default
last_modified_date: 2022-12-03 14:13:39 +0000
title: How can i increase or decrease claim sizes
nav_order: 2
nav_exclude: false
parent: FAQ
has_children: false
has_toc: false
published: false

---
##### How can i increase or decrease claim sizes?

To change this open up your server console and paste these into the console changing the numbers to whatever you see fit

The Below strings are the Default server settings

    $cm_config::Claims::guildLevel1RadiusTown = 20;
    
    $cm_config::Claims::guildLevel1RadiusCountry = 20;
    
    $cm_config::Claims::guildLevel2RadiusTown = 30;
    
    $cm_config::Claims::guildLevel2RadiusCountry = 30;
    
    $cm_config::Claims::guildLevel3RadiusTown = 50;
    
    $cm_config::Claims::guildLevel3RadiusCountry = 50;
    
    $cm_config::Claims::guildLevel4RadiusTown = 100;
    
    $cm_config::Claims::guildLevel4RadiusCountry = 100;
    
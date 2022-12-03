---
layout: default
last_modified_date: 2022-12-03T14:33:51.000+00:00
title: How can I reduce the time for a Tunnel to collapse
nav_order: 3
nav_exclude: false
parent: FAQ
has_children: false
has_toc: false

---
### How can I reduce the time for a Tunnel to collapse?

> **Please note:** This is server wide and not at targeted tunnels  
> Changing these may make the server crash/restart on game day ticks depending on how many tunnels are on your server.

The following string is to collapse a standard Tunnel/mine (Default Value is 1)  
For an example purpose we will use the Value of 100 which will collapse Tunnels after 1 Game Day

    $cm_config::Geo::TunnelDecayValue = 100;

The following string is to collapse a reinforcement using boards (Default Value is 1)  
For example, purposes we will use the Value of 100 which will collapse a Tunnel after 1 Game Day

    $cm_config::Geo::LightTimberDecayValue = 100;

The following string is to collapse a reinforcement using building logs (Default Value is 1)  
For example, purposes we will use the Value of 100 which will collapse a Tunnels after 1 Game Day

    $cm_config::Geo::HeavyTimberDecayValue = 100;

These strings should be Edited with the values of your choice and pasted into your game server console
---
layout: default
last_modified_date: 2022-12-03 14:33:51 +0000
title: 'How can i set mines people have made to collapse quicker '
nav_order: 3
nav_exclude: false
parent: FAQ
has_children: false
has_toc: false
published: false

---
Speed Up Tunnel Decay

You can change the default Decay resource, but it is recommended to leave it as substance 8 

    $cm_config::Geo::TunnelBaseDecayResource = 8;

This is to collapse a standard Tunnel the Default Value is 1 but for an example purpose we will use the Value of 100 which will collapse mines after 1 Game Day

    $cm_config::Geo::TunnelDecayValue = 100;

The Default Value is 1 but for an example purpose we will use the Value of 100 which will collapse mines after 1 day
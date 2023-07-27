---
layout: default
nav_order: 2
title: Server framework
nav_exclude: false
has_children: false
has_toc: true
parent: Server Documentation
last_modified_date:
---
# Server framework
{: .no_toc}

## Table of contents
{: .no_toc.text-delta}

1. [Installation instructions](#installation-instructions)
2. [Changelog](#changelog)

## Installation instructions

[Download the mod](https://github.com/LiF-x/ServerAutoloader/releases/latest){: .btn.fs-5.mb-4.mb-md-0.mr-2}&nbsp;[![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2FLiF-x%2FServerAutoloader%2Freleases%3Fper_page%3D1&amp;query=%24%5B0%5D.tag_name&amp;label=ServerAutoloader&amp;color=green)](https://github.com/LiF-x/ServerAutoloader/releases/latest)

Copy the art.zip without unpackaging it to your servers root directory

```
+-- .. (Life is Feudal: Your Own dedicated server root)
|-- art.zip
|-- config_local.cs
|-- main.cs
|-- mods
|   |-- Mods are installed here
+-- ..
```

![Directory structure](/uploads/lifx-server-setup-guide.png)

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/nVpZejuLZEg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen=""></iframe>

## Changelog

| Date | Version | Comment |
| --- | --- | --- |
| 14\.12.2022 | 3\.0.0 | Removed requirement to register mods to a mods hook, it is now handled by activatePackage, setup function is made mandatory. Added export functionality for objects\_types.xml, recipe.xml and recipe\_requirement.xml (credits to Basil for allowing us to use his work for this) |
| 01\.10.2021 | 2\.6.1 | Added deathhook functionality |
| 15\.04.2021 | 2\.4.0 | Added display of new version tag on modsAdded inclution of Utility a public repository for common functions to the LiFx framework |
| 30\.01.2021 | 2\.2.0 | Added new hooks$LiFx::hooks::onPostConnectRoutineCallbacks = JettisonArray(“onPostConnectRoutineCallbacks”);$LiFx::hooks::onPreConnectRequestCallbacks = JettisonArray(“onPreConnectRequestCallbacks”); |
| 24\.01.2021 | 2\.1.0 | Released, 1.x.x is now deprecated and unsupported |
| 02\.01.2021 | 2\.0.0 | See Server autoloader 2.0.0 |
| 27\.12.2020 | v1.1.0 | Introduced a new config file in mods/AutoloadConfig.csEach mod has 4 settings-1 = Uninstall – remove all associated files0 = Do nothing – excisting files will remain intact1 = Download but do not execute // Enables mod2 = Download and execute All settings will be unpacked with 0 as their default setting uninstall is not implemented execution as per now is for future use and does not apply to third party mods, is currently only used for LiFx main mod. |
| 21\.12.2020 | v1.0.3 | Changed when db.cs is executed to before InitServer to append sql to dump.sql |
| 21\.12.2020 | v1.0.2 | Added initServer calls that will execute “db.cs” files in mods/&lt;yourmod&gt;/db.cs just before CreateServer starts for adding SQL updates after dump.sql and patch.sql has ranAdded overloadable init call for starting packages loaded after onStart()&lt;/yourmod&gt; |
| 20\.12.2020 | v1.0.1 | Added onPostInit call |
| 19\.12.2020 | v1.0.0 | The initial release of our server-side mod, it introduces our LiFx Mod Framework structure |
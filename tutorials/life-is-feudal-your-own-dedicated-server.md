---
layout: default
last_modified_date: 2022-12-04 11:44:50 +0000
title: 'Setup a local Life is Feudal: Your Own dedicated server'
nav_order: 1
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: true
published: false

---
# Setup a local Life is Feudal: Your Own dedicated server

A guide to setting up a development environment for modding with LiFx framework compatibility

## Prerequisits

* MariaDB
* SteamCMD
* LiFx Server Framework
* YoLauncher (LiFx Client Framework)

## Windows

### MariaDB

1. Download the latest MariaDB release from [https://mariadb.org/download](https://mariadb.org/download "https://mariadb.org/download")

   > Disclaimer: Life is Feudal: Your Own recommends MariaDB version 5.5, but due to security patches being discontinued since April 2020, we would recommend you install a newer version. Server hosts are likely to have a newer version than 5.5, however note there are changes in terms of triggers and procedures that are different between each version and may impact your mods.
2. Run the MSI installer to install it as a service. No modification ot the default features are necessary.
3. When prompted for a root password. Choose a complex password, we recommend a password of minimum 16 characters, with punctuations, special characters, numbers, large and small letter combinations.  
   If you want remote users to be able to login as root (**we discourage this**) you also have to check the option "_Enable access from remote machines for 'root' user_"

   > Note when allowing root connections from remote computers, you are potentially opening up a security risk.
4. Leave the rest of the options default, you may now complete the installation wizard without alterations.
5. Life is Feudal requires some changes to the standard config for MariaDB. Navigate to the data directory of your MariaDB installation "C:\\Program Files\\MariaDB <your version>\\data" where you replace "<our version>" with the version number you installed. For example: C:\\Program Files\\MariaDB 10.10\\data.  
   Open the file called "**my.ini**" in your favorite text editor.

   Make sure the \[mysqld\] section has the following options. Add the missing options as shown below. Merge the differences between your "**my.ini**" file and what we describe here:

       [mysqld]
       default_storage_engine=innodb
       character-set-server=utf8
       innodb_file_per_table=ON
       innodb_file_format=Barracuda
       innodb_flush_log_at_trx_commit=1
       max_sp_recursion_depth=255
       max_allowed_packet=10M
       query_cache_size=0
       query_cache_type=OFF
6. Once that is done, restart your MariaDB service using either of these options:
   1. Go to windows run (⊞ Win + R) and type "**services.msc**", once services pops up, find "MariaDB" service and restart it
   2. Open up a powershell or command prompt window and type

          net stop MariaDB
          net start MariaDB

      These commands will each run and give you a status if the service is stopped or started successfully.

### SteamCMD

1. Download SteamCMD for Windows from valve: [https://developer.valvesoftware.com/wiki/SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD "https://developer.valvesoftware.com/wiki/SteamCMD")
2. Unzip to a directory of your choice, for this tutorial your server files will also reside next with your steamcmd.exe file. For the purpose of this tutorial, we are assuming you have unpacked the zip file to the following directory: "**C:\\Steam**"

### Life is Feudal: Your Own dedicated server files

1. Open up a terminal in the folder where you have your steamcmd.exe file
2. In your terminal write the following

       steamcmd.exe +login anonymous +app_update 320850 +validate
3. This will update and install Life is Feudal: Your Own dedicated files which will be under the file path to your steamcmd.exe directory: "**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\**"
4. Copy config_local.cs from "**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\docs**" to "**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\**" and open it up in your favorite text editor.
5. Customize the world_1.xml located in the following path "**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\config**" this is the main configuration file for your server. World ID has to be concise and follow the name of your xml file, default is 1.

#### Booting your server for the first time

To start your server simply run the file named "**ddctd_cm_yo_server.exe**" located in the path "**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\**" it will open a new window with yellow text showing you the console of your server.

If you get an error of missing DLL files, it is likely you haven't installed Microsoft Visual C++ 2015 Redistributable package. You can find that package here [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145 "https://www.microsoft.com/en-us/download/details.aspx?id=48145")

When the server has finished loaded (it may take several minutes on first boot up, due to server creating navmesh and terrain cache for the first time) and ready for clients it will display the following:

    {} <> [0] Server is up and ready to accept connections
    {} <<Thread>> [] The TCP server is up and running at port 28000 [T:NONE:12676]
    {} <> [74] CmSteam::onSteamServersConnected
    {} <> [92] CmSteam::onSteamPolicyResponse. secure=1, our steamID=xxxxxxx
    {} <> [92] Steam initialized

### LiFx Server Framework

Follow the guide provided here

### Quality of life tips

This section will cover some tips and tricks that I use to make developing mods using the LiFx Framework simpler and easier to restart, test and verify the mods without relying on comparatively slow game server provider's hosting panels.

1. Create a shortcut to "**ddctd_cm_yo_server.exe**" 
   1. Do this by right clicking "**ddctd_cm_yo_server.exe**" and choosing "Send to", "Desktop (create shortcut)"
   2. Edit your shortcut, and go to properties.
   3. Append "-worldId 1" to the end of "Target" so you can choose what worldId you want to launch. Example: "**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\ddctd_cm_yo_server.exe -worldId 1**"
2. Put your server mod repositories directly in the directory "**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\mods**"  
   This way you will not need to copy files locally to test them out, and you will have source tracking all the way.

**Credits**

Thanks to Nyuton for his work on feudal.tools [knowledge base article](https://kb.feudal.tools/knowledge-base/setup-lifyo-dedicated-server-on-windows/) that this tutorial bases some of its information from
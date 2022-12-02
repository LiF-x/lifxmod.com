---
layout: default
nav_order: 2
title: Server framework
nav_exclude: false
has_children: false
has_toc: true
parent: Documentation
last_modified_date: 

---
# Server framework
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC  
{:toc}

## Installation instructions

[Download the mod](/assets/images/art.zip){: .btn .fs-5 .mb-4 .mb-md-0 .mr-2 }

Copy the art.zip without unpackaging it to your servers root directory (same directory as ddct_dcm_yoserver.exe, main.cs and config_local.cs)

You are now set to download install and use compatible mods to the server framework

## Changelog

| Date | Version | Comment |
| --- | --- | --- |
| 15.04.2021 | 2.4.0 | Added display of new version tag on modsAdded inclution of Utility a public repository for common functions to the LiFx framework |
| 30.01.2021 | 2.2.0 | Added new hooks$LiFx::hooks::onPostConnectRoutineCallbacks = JettisonArray(“onPostConnectRoutineCallbacks”);$LiFx::hooks::onPreConnectRequestCallbacks = JettisonArray(“onPreConnectRequestCallbacks”); |
| 24.01.2021 | 2.1.0 | Released, 1.x.x is now deprecated and unsupported |
| 02.01.2021 | 2.0.0 | See Server autoloader 2.0.0 |
| 27.12.2020 | v1.1.0 | Introduced a new config file in mods/AutoloadConfig.csEach mod has 4 settings-1 = Uninstall – remove all associated files0 = Do nothing – excisting files will remain intact1 = Download but do not execute // Enables mod2 = Download and execute All settings will be unpacked with 0 as their default setting uninstall is not implemented execution as per now is for future use and does not apply to third party mods, is currently only used for LiFx main mod. |
| 21.12.2020 | v1.0.3 | Changed when db.cs is executed to before InitServer to append sql to dump.sql |
| 21.12.2020 | v1.0.2 | Added initServer calls that will execute “db.cs” files in mods/<yourmod>/db.cs just before CreateServer starts for adding SQL updates after dump.sql and patch.sql has ranAdded overloadable init call for starting packages loaded after onStart() |
| 20.12.2020 | v1.0.1 | Added onPostInit call |
| 19.12.2020 | v1.0.0 | The initial release of our server-side mod, it introduces our LiFx Mod Framework structure |

## Documentation

### Hooks

| Hook array | Parameters | Description |
| --- | --- | --- |
| $LiFx::hooks::mods |  | This is the mod entrypoint, you have to register your mod and the "setup" function to this hook for it to load, see example below. It is only used for registering your setup functionality not to execute any game altering code directly |
| $LiFx::hooks::onStartCallbacks | %this | Executes when onStart is called by the server code and should be your main entry point for your mod to execute and load configuration. |
| $LiFx::hooks::onConnectRequestCallbacks | %this, %gameConnection, %netaddress, %name |  |
| $LiFx::hooks::onPostConnectRoutineCallbacks | %this, %gameConnection, %netaddress, %name |  |
| $LiFx::hooks::onPreConnectRequestCallbacks | %this, %gameConnection, %netaddress, %name |  |
| $LiFx::hooks::onPostInitCallbacks | %this | Executes when onInit has ran and is where you need to register BasilMod pack commands to ensure that BasilMod syncs your server files to the client |
| $LiFx::hooks::onInitServerCallbacks | %this | Executes after DB changes and initial load of network |
| $LiFx::hooks::onInitServerDBChangesCallbacks | %this | Registering a function on this hook will execute your db calls just after dbi is initialized and before the server loads information from the database. |
| $LiFx::hooks::onSpawnCallbacks | %this, %client | Will execute your registered function every time a player spawns |
| $LiFx::hooks::onConnectCallbacks | %this, %client | Will execute one time per connecting client |
| $LiFx::hooks::onDisconnectCallbacks | %this, %client | Will execute one time per disconnecting client |
| $LiFx::hooks::onJHStartCallbacks | %this | Will execute registered function on JH Start event |
| $LiFx::hooks::onJHEndCallbacks | %this | Will execute registered function on JH End event |
| $LiFx::hooks::onDeathCallbacks | %this, %CharID, %isKnockout, %Tombstone | Executes on death event |
| $LiFx::hooks::onKillCallbacks | %this, %CharID, %KillerID, %isKnockout, %Tombstone | Executes on kill event (reverse objects of onDeath) |
| $LiFx::hooks::onSuicideCallbacks | %this, %CharacterID, %isKnockout, %Tombstone | Executed in case of a suicide |
| $LiFx::hooks::onTick | %this | Call a mod function every 5 seconds |

### Example

An example of server framework compatible mod.  
Each server mod has to be named mod.cs for the framework to find it and execute it.

You can also use the public example starting point which you can find on in [this public repository.](https://github.com/LiF-x/ExampleServerMod)

#### Example structure

#### Example file

    /**
    * <author></author>
    * <url>lifxmod.com</url>
    * <credits></credits>
    * <description></description>
    * <license>GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007</license>
    */
    
    // Register your mod as an object in the game engine, important for loading and unloading a package (mod)
    if (!isObject(ExampleMod))
    {
        new ScriptObject(ExampleMod)
        {
        };
    }
    
    
    // LiFx expect each mod to be it's own unique package
    package ExampleMod
    {
      // The setup method is required, and will be looked for by the framework
      // This is where you tell the framework, which hooks you use and what object types you have added, so that the framework can call your code at the appropiate time
      function ExampleMod::setup() {
        // Register callback hooks, do not run any form of code that does anything here, just register the hook
    	/**
    	* LiFx::registerCallback is a global framework function, it takes 3 parameters
        * Parameter 1: The hook to register your function on
        * Parameter 2: Non scoped name of function in your package
        * Parameter 3: The package name to scope your function appropiately.
    	*/
        LiFx::registerCallback($LiFx::hooks::onSpawnCallbacks, onSpawn, ExampleMod);
        
    	/**
    	* LiFx::registerObjectsTypes is a global framework function, it takes 2 parameters
    	* It is used to write to the dump.sql on start, prior to the server reading it, and is necessary as bitbox wipes the objectstypes table on each start up.
        * Parameter 1: The function including scope to your objectstypes definition
        * Parameter 2: The package name of your mod
    	*/
        LiFx::registerObjectsTypes(ExampleMod::ObjectsTypesBazaar(), ExampleMod);
      }
    
      function ExampleMod::onSpawn(%this, %client) {
        echo(%this.getName() SPC %client.getName());
        
      }
      function ExampleMod::ObjectsTypesBazaar() {
    
        // this returns and writes to the dump.sql file for ease of distribution
        return new ScriptObject(ObjectsTypesBazaar : ObjectsTypes)
        {
          id = 2420;
          ObjectName = "Bazaar";
          ParentID = 61;
          IsContainer = 0;
          IsMovableObject = 0;
          IsUnmovableobject = 1;
          IsTool = 0;
          IsDevice = 0;
          IsDoor = 0;
          IsPremium = 0;
          MaxContSize = 0;
          Length = 0; 
          MaxStackSize = 0;
          UnitWeight = 5000;
          BackgrndImage = "";
          WorkAreaTop = 0;
          WorkAreaLeft = 0;
          WorkAreaWidth = 0;
          WorkAreaHeight = 0;
          BtnCloseTop = 0;
          BtnCloseLeft = 0;
          FaceImage = "mods\\\\ExampleMod\\\\buildings\\\\construction\\\\misc\\\\BazaarHall\\\\BazaarHall.png";
          Description = "Bazaar tent";
          BasePrice = 0;
          OwnerTimeout = 0;
          AllowExportFromRed = 0;
          AllowExportFromGreen = 0;
        };
      }
    };
    
    // This command is from Torque, and activates your package so that the engine can reference it
    // This is required for your mod to work, and have the code loaded in torque engine.
    activatePackage(ExampleMod);
    
    // This registers your setup method, to the framework similar to how you register callbacks otherwise inside your setup function of the package
    // It is subject to change and may later be removed for automation purposes
    LiFx::registerCallback($LiFx::hooks::mods, setup, ExampleMod);
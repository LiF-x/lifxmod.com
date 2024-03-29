---
layout: default
nav_order: 3
title: Server framework development
nav_exclude: false
has_children: false
has_toc: true
parent: Server Documentation
last_modified_date:
---
# Mod development documentation
{: .no_toc}

## Table of contents
{: .no_toc.text-delta}

1. [Required contents of your mod](#required-contents-of-your-mod)
2. [Useful links](#useful-links)
3. [Hooks](#hooks)
4. [Example](#example)
   1. [Example structure of the server](#example-structure-of-the-server)
   2. [Example mod.cs file](#example-modcs-file)

## Required contents of your mod

In order to make a compatible mod there are certain requirements:

1. Your mod has to comply with **GPL v3 license** and if you provide your mod publicly, the code has to be shared as per the license.
2. Your mod has to be a unique package as per Torque 3D Standards.
3. Your mod's main entry point has to be a file named "**mod.cs**" as per the example below.
4. In your mod.cs file, you have to register register at least one function to the LiFx hook "**$LiFx::hooks::mods**". (with 3.0.0 this will be deprecated)
5. Your package must provide a setup function. (mandatory from 3.0.0)
6. Your package should provide a "**version**" function, specifying the version of your mod.

## Useful links

* [Torque 3D documentation](https://torque-3d.readthedocs.io/en/latest/intro/intro.html "Torque3D Documentation")

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/nVpZejuLZEg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen=""></iframe>

## Hooks

| Hook array | Parameters | Description |
| --- | --- | --- |
| $LiFx::hooks::onStartCallbacks | %this | Executes when onStart is called by the server code and should be your main entry point for your mod to execute and load configuration. |
| $LiFx::hooks::onConnectRequestCallbacks | %this, %gameConnection, %netaddress, %name | Calls a function when a user is attempting to join |
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
| $LiFx::hooks::onServerCreatedCallbacks | \- | Is called when the ServerCreated event is done |
| $LiFx::hooks::onDestroyServerCallbacks | \- | Is called when the DestroyServer event is done |
| $LiFx::hooks::onStartSwimCallbacks | \- | Is called when someone starts swimming |
| $LiFx::hooks::onStopSwimCallbacks | \- | Is called when someone stops swimming |

## Example

An example of server framework compatible mod.<br>Each server mod has to be named mod.cs for the framework to find it and execute it.

You can also use the public example starting point which you can find on in the public repository.<br>[Server Mod Boilerplate](https://github.com/LiF-x/ExampleServerMod){: .btn.fs-5.mb-4.mb-md-0.mr-2}

### Example structure of the server

```
+-- ..
|-- / Life is Feudal: Your Own dedicated server root
|-- art.zip
|-- config_local.cs
|-- main.cs
|-- mods
|   |-- ExampleMod
|   |   |-- mod.cs
+-- ..
```

### Example mod.cs file

```
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
  // Returns a string as a version, LiFx will look for this specific function to output version to new connecting players
  // Takes no parameters, is a reserved function for LiFx compatability.
  function ExampleMod::version() {
    return "v1.0.0";
  }

  // The setup method is required, and will be looked for by the framework, if it doesn't have it your mod will not execute
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

  // Example function references from setup above, this code will execute when the hook is called by the LiFx framework
  function ExampleMod::onSpawn(%this, %client) {
    echo(%this.getName() SPC %client.getName());

  }
  // The function name should match the object you create as a return object inside of the function
  function ExampleMod::ObjectsTypesExampleBuilding() {

    // this returns and writes to the dump.sql file for ease of distribution
	// The name of the object should be the same as the function name it registers
	// Each of the variables in the object, corrosponds to the column value in the database
    return new ScriptObject(ObjectsTypesExampleBuilding : ObjectsTypes)
    {
      id = 2420; // *UNIQUE INT* Has to be a unique id - grab id from here: https://lifxmod.com/Docs/objects-types-id-list.html
      ObjectName = "ExampleBuilding"; // *STRING* Name of your object
      ParentID = 61; // *INT* ParentID decides what type of object you have, think of it as class inheritance
      IsContainer = 0; // *BOOL* 1 (true) or 0 (false) - If your object is supposed to have a container referenced
      IsMovableObject = 0; // *BOOL* 1 (true) or 0 (false) - If your object is supposed to be movable
      IsUnmovableobject = 1; // *BOOL* 1 (true) or 0 (false) - If your object is supposed to be unmovable
      IsTool = 0; // *BOOL* 1 (true) or 0 (false) - If your object is supposed to be a tool to cut down trees or build buildings
      IsDevice = 0; // *BOOL* 1 (true) or 0 (false) - If your object is a device used in crafting or other interactions
      IsDoor = 0; // *BOOL* 1 (true) or 0 (false) - If your object has a door
      IsPremium = 0; // *BOOL* 1 (true) or 0 (false) - Premium defintion currently is not in use for Your Own.
      MaxContSize = 0; // *INT* The Max size of the container, if IsContainer is true
      Length = 0;  // *INT* Length of your object, used to decide if your object fits in a particular container
      MaxStackSize = 0; // *INT* Max number of items in a stack of your item in the inventory
      UnitWeight = 5000; // *INT* The weight of your object, used in calculation of encumbarance
      BackgrndImage = ""; // *STRING* Image reference to your inventory background, must be set if your object has a container
      WorkAreaTop = 0;
      WorkAreaLeft = 0;
      WorkAreaWidth = 0;
      WorkAreaHeight = 0;
      BtnCloseTop = 0;
      BtnCloseLeft = 0;
      FaceImage = "mods/ExampleMod/BuildingImages/Example.png"; // *STRING* Reference to png that will be displayed in crafting menu
      Description = ""; // *STRING* Used in crafting and skill to describe your object
      BasePrice = 0; // *INT* Used as price for sacrificing to monuments, high value gives more maintenance points
      OwnerTimeout = 0; // *INT* Used to set a timer on the object when made or dropped.
      AllowExportFromRed = 0; // Not in use
      AllowExportFromGreen = 0; // Not in use
    };
  }
};

// This command is from Torque, and activates your package so that the engine can reference it
// This is required for your mod to work, and have the code loaded in torque engine.
activatePackage(ExampleMod);
```
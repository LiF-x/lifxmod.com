---
layout: default
last_modified_date: 2022-12-04 15:48:22 +0000
title: How to add new NPC
nav_order: 10
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false
published: false

---
### How to add new NPC

Using LiFx Framework this is much easier.

> **For the purposes of this Tutorial we will show how to create a new object using LiFx Framework**
>
> **  
> we will create a LiFx NPC  
> Please note: same method can be used for any object including buildings**

Required files for mod  
dts model - We will be using a renamed NPC model Assel from the original YO models  
cm_objects.xml  
Object_types.xml

**mod Structure Set up  
  
Create a folder for your mod for the purposes of this tutorial I will name it LiFxNPC**

* **Inside this folder create a new one called "data"**
* **Inside the main folder (LiFxNPC) create a new folder "mods"**
* **Inside the main folder (LiFxNPC) create a new folder "yolauncher"  
  ![](/uploads/mainstructure.png)**
* **Inside the data Folder place files "cm_objects.xml" and "object_types.xml"**

  > **Mods folder set up**
* **Inside the mods folder create a new one called LiFx**
* **Inside the new LiFx folder create a new one called NPC**

  > **YoLauncher Folder**
  * **Inside the yolauncher folder create a new one named "modpack"**
  * **Inside the new "modpack" folder create a new one named "art"**
  * **Inside the new "modpack" folder create a new one named "data"**
  * **Inside the new "modpack" folder create a new one named "mods"**
* **Inside the new "art" folder Create a new one named "Models"**
  * **Inside the new "Models" folder Create a new one named "3D"**
    * **Inside the new "3D" folder Create a new one named "NPC" - This is where your.dts should go**
* **Inside the new "art" folder Create a new one named "Textures"**
  * **Inside the new "Textures" folder Create a new one named "NPC" - Your NPCmaterials.cs will be here**
    * **Inside the new "NPC" folder Create a new one named "Customization"**
      * **Inside the new "Customization" folder Create a new one named "male"**

Step 1) Create mod.cs - Place in your mods folder  
Step 2) Amend cm_objects.xml  
Step 3) Amend Object_types.xml

**Client side**

Step 4) Create cmod.cs - This is a client side mod which LiFx Framework will trigger allowing players to see the mod on the Server

\**  
Step 1)**

**Setting up your mod.cs file ready for auto load by the LiFx Autoloader**

Open a new file and copy the code block below to it.

Please ensure you name your mod correctly replacing "LiFxNPCmod" with your desired name.

Please think carefully on your object id, in this tutorial we will be using the id = 2500;

> A list of object ids is available below, it is recommended to use one not currently in use to avoid mod conflicts.  
> [Objects Types ID List - LiF: Extended (lifxmod.com)](https://lifxmod.com/Docs/objects-types-id-list.html)

    /**
    * <author>Ibun</author>
    * <email>lifxmod@gmail.com</email>
    * <url>lifxmod.com</url>
    * <credits>Christophe Roblin <christophe@roblin.no> modification to make it yolauncher server modpack and lifxcompatible</credits>
    * <description>knools from mmo introduced to Lif:YO</description>
    * <license>GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007</license>
    */
    
    if (!isObject(LiFxNPCmod))
    {
        new ScriptObject(LiFxNPCmod)
        {
        };
    }
    
    package LiFxNPCmod
    
    {
        function LiFxNPCmod::setup() {
            LiFx::registerCallback($LiFx::hooks::onServerCreatedCallbacks, Datablock, LiFxNPCmod);
            
            // Register new objects
            LiFx::registerObjectsTypes(LiFxNPCmod::ObjectsTypesBrotherhoodSoldier(), LiFxNPCmod);
    
        }
        function LiFxNPCmod::version() {
            return "0.0.1";
        }
      
            function LiFxNPCmod::ObjectsTypesBrotherhoodSoldier() {
            return new ScriptObject(ObjectsTypesBrotherhoodSoldier : ObjectsTypes)
            {
                id = 2500; // has to be globally unique, please reserve ids here: https://www.lifxmod.com/info/object-id-list/
                ObjectName = "Brotherhood Soldier";
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
                UnitWeight = 1000;
                BackgrndImage = "";
                WorkAreaTop = 0;
                WorkAreaLeft = 0;
                WorkAreaWidth = 0;
                WorkAreaHeight = 0;
                BtnCloseTop = 0;
                BtnCloseLeft = 0;
                FaceImage = "";
                Description = "";
                BasePrice = 0;
                OwnerTimeout = 0;
                AllowExportFromRed = 0;
                AllowExportFromGreen = 0;
            };
        }
    };
    activatePackage(LiFxNPCmod);
    LiFx::registerCallback($LiFx::hooks::mods, setup, LiFxNPCmod);

**Step 2)**

It is now time to edit your cm_objects.xml

You will need to add another object to this file it is recommended you add this at the very bottom below the last item, to do this simply copy and paste the CodeBlock below and amend to your desired information.

You will notice the following:

<lockedCells>  
<cell x="0" y="0" />  
</lockedCells>

This is to lock cells and is mainly used for new buildings, as we are looking at npcs we will not be looking into this however a future tutorial is planned for this.

    	<object id="2500" isUnflattenAllowed="1" rotationStep="1" defaultState="Complete" StreamingGroup="1" noRuins="1">
    		<!--name = Brotherhood Soldier -->
    		<lockedCells>
    			<cell x="0" y="0" />
    		</lockedCells>
    		<states>
    			<state type="Complete">
    				<shapes>
    					<shape>
    						<shapeName>yolauncher/modpack/art/Models/3D/NPC/BrotherhoodSoldier.dts</shapeName>
    						<animationName>idle1</animationName>
    						<offset x="0" y="0" z="0.0" />
    						<rot x="0" y="0" z="1" angle="0" />
    						<scale x="1" y="1" z="1" />
    					</shape>
    				</shapes>
    			</state>
    		</states>
    	</object>

**Step 3)**

Amending Object_types.xml

Open your object types file and at the bottom add a new block by copying and pasting the below code block into your file, making amendments as you see fit.

    	<row>
    		<ID>2500</ID>
    		<ParentID>61</ParentID>
    		<Name>Brotherhood Soldier</Name>
    		<IsContainer>0</IsContainer>
    		<IsMovableObject>0</IsMovableObject>
    		<IsUnmovableobject>1</IsUnmovableobject>
    		<IsTool>0</IsTool>
    		<IsDevice>0</IsDevice>
    		<IsDoor>0</IsDoor>
    		<IsPremium>0</IsPremium>
    		<MaxContSize>0</MaxContSize>
    		<Length>0</Length>
    		<MaxStackSize>0</MaxStackSize>
    		<UnitWeight>1000</UnitWeight>
    		<BackgndImage></BackgndImage>
    		<FaceImage></FaceImage>
    		<Description></Description>
    	</row>

The Above has now completed the server side of the mod.

**Now Time To set up the mod client side**

**Step 4)**

Create a new and copy and paste the below CodeBlock into the file amending if needed  
the loading of materials is important as this will load the textures onto your model.

    /**
    * <author>Ibun</author>
    * <email>lifxmod@gmail.com</email>
    * <url>lifxmod.com</url>
    * <credits>Christophe Roblin <christophe@roblin.no> modification to make it yolauncher server modpack and lifxcompatible</credits>
    * <description>Introducing LiFx NPC</description>
    * <license>GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007</license>
    */
    
    if (!isObject(LiFxNPC))
    {
        new ScriptObject(LiFxNPC)
        {
        };
    }
    package LiFxNPC
    {
      function LiFxNPC::setup() {
        LiFx::registerCallback($LiFx::hooks::onDatablockLoad, RegisterNewNPCmaterials, LiFxNPC);
      }
    
      function LiFxNPC::RegisterNewNPCmaterials() {
        LiFx::loadRecursivelyInFolder("yolauncher/modpack/art/Textures/NPC", "NPCmaterials.cs");
      }
      function LiFxNPC::path() {
        return $Con::File;
      }
    };
    activatePackage(LiFxNPC);
    LiFx::registerCallback($LiFx::hooks::mods, setup, LiFxNPC);

....
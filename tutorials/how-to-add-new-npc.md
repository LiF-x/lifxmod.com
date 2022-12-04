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

> Required files for mod - below is a frame work for you to download and work off  
> [LiFxTutorials/LiFxNPC at main · matty5350/LiFxTutorials (github.com)](https://github.com/matty5350/LiFxTutorials/tree/main/LiFxNPC "LiFx NPC")

**Client side**  
Step 1)**

**Open up the mod.cs file from the link above.**

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

> This will already be set up if you want to use it out of the box

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
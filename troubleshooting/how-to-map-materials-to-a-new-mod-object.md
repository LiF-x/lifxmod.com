---
layout: default
last_modified_date: 2022-12-05 18:22:57 +0000
title: How to map materials to a new mod object
nav_order: 3
nav_exclude: false
parent: Troubleshooting
has_children: false
has_toc: false
published: false

---
### How to map materials to a new mod object

 As we have heard quite a bit of confusion surrounding adding new objects and mapping materials to them, we have decided to add a little help regarding mapping new materials and hope this helps.  
  
**_Let's Begin!_**

**  
mapTo - Recommended** 

 In Torque it is necessary to "map" a Material to each texture that is used in the model. Think of the textures used in the arts tools as "tags" that Torque uses to apply something more complex than just a texture.

 The process of mapping a Material to a texture tag is done inside the Material itself by using the "mapTo" parameter. MapTo simply names the texture tag to apply the Material to.

Example:

>     singleton Material(LargeTanningTub)
>     {
>        mapTo = "tanningtub_diff";
>        diffuseMap[0] = "yolauncher/modpack/mods/LiFx/BigTub/art/Textures/Largetub_diff.dds";
>        diffuseMap[1] = "yolauncher/modpack/mods/LiFx/BigTub/art/Textures/tanningtub_NORMALMAP.dds";
>        diffuseMap[2] = "yolauncher/modpack/mods/LiFx/BigTub/art/Textures/tanningtub_SPECULAR.dds";
>     };

![](/uploads/tanningtubmaterials.png)

 In this case, Torque will apply the Material "LargeTanningTub" to the texture "tanningtub_diff" that was used in Torque 3d.  
  
Please take a look at the image and the code block above to clear up any confusion.  
  
**Automatic mapping -** 

> **Please note:**  This Not recommended for LiF: YO however this can be used to ensure the model is loading in game, including if you are having issues with textures not loading onto the model, this can give a solid black texture if automatic mapping fails, allowing you to work out which texture is causing an issue in the event of a corrupted texture file.

Materials do not require a mapTo parameter if the base texture name in the Material is the same as the texture tag.

So this:

    new Material( LiFx )
    {
       mapTo = "Extended";
       diffuseMap[0] = "~/data/textures/Extended";
    };

could be reduced to:

    new Material( LiFx )
    {
       diffuseMap[0] = "~/data/textures/Extended";
    };
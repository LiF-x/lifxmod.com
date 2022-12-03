---
layout: default
last_modified_date: 2022-12-03T15:41:49.000+00:00
title: Increase Storage/Container Size
nav_order: 3
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false

---
### Increase Storage/Container Size

  
To increase the max storage/container size of objects and items you have to edit two files. **dump.sql** on the Server and **objects_types.xml** for your clients side if you don’t use basilmod.

_Note: basilmod if setup properly will automatically generate the objects_types.xml for clients based on the current objects_types database table._

The recommended method of updating the database is to use an SQL UPDATE with only the columns you want to update in it. As to why we put this in the dump.sql file is because that file it setup to run on every server reset and the first thing it does is dump/delete several tables one being the objects_types table we plan to edit. So just changing the database directly will not work as it will get cleared and rebuilt by the dump.sql. By adding this change to the bottom of the dump.sql file it will “re-add” your edit after the clear and rebuild each reset.

In this tutorial we’ll be updating the Warehouse from 15,000 size to 25,000 size, the code below is what you will need to add.

Note: make sure you add this below the

\-- Dump completed on 2018-09-10 14:36:41

line at the very bottom of the file.

    UPDATE `objects_types` SET `MaxContSize`='25000000' WHERE  `ID`=131; /* Default: 15000000 */

If you have basilmod running properly, that’s all you need to edit. If not you will need to also perform the below edits to your objects_types.xml and have it on both the server and client side. The reason why it’s important to make sure your objects_types.xml for clients is updated is so they can see the new MaxContSize and continue to add more into it past the default size.

Tip: To easily find this section use a search for _<ID>131</ID>_, or _Warehouse_. Also it should be around line _2417_ if you use an editor that shows that info.

    <row>
        <ID>131</ID>
        <ParentID>69</ParentID>
        <Name>Warehouse</Name>
        <IsContainer>1</IsContainer>
        <IsMovableObject>0</IsMovableObject>
        <IsUnmovableobject>1</IsUnmovableobject>
        <IsTool>0</IsTool>
        <IsDevice>0</IsDevice>
        <IsDoor>1</IsDoor>
        <IsPremium>0</IsPremium>
        <MaxContSize>25000000</MaxContSize> <!-- Default: 15000000 -->
        <Length>8</Length>
        <MaxStackSize>0</MaxStackSize>
        <UnitWeight>200000</UnitWeight>
        <BackgndImage>art\images\warehouse</BackgndImage>
        <FaceImage>art\2D\Objects\warehouse.png</FaceImage>
        <Description></Description>
    </row>
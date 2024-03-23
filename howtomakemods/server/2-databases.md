---
_schema: layout
layout: default
nav_order: 3
last_modified_date: 2024-03-23 10:30:00
title: 2. Databases
parent: Server side mods
grand_parent: How to make mods
nav_exclude: false
has_children: false
has_toc: false
---
# 2\. Databases

{: .important-title}
> Sponsored by Rampart Games
>
> This article is sponsored by [Rampart.Games](https://rampart.games "Rampart Games Ltd Game Servers"){: target="_blank" rel="noopener"}, a modern container based game server provider.  No slot limitations, you choose and pay for the resources that fit your needs.

In this scenario we will make a simple mod that explores the databases features of the global "dbi" object. If you haven't yet, please review tutorial [Getting ready](/howtomakemods/server/getting-ready.html "Tutorial getting ready") and [\#1 Hello World](/howtomakemods/server/helloworld.html "Tutorial #1 Hello World") which introduces you to setting up a local development area and the basic concepts of writing mods in the LiFx framework.

From our experience and testing, even though there are several functions available, the only two we've seen work without issues are **Query** and **Select** we recommend that you avoid using the other functions exposed, as they tend to put your server in an unstable state, eventually crashing.

It is also very important to close the handlers properly as to not create open connections that linger after they are no longer needed. This will cause the torque <br>engine to do heavy cleanups if not done properly.

## The basic skeleton for setting up a select query:

{: .highlight }
> <span class="text-red-300">dbi</span>.(<span class="text-purple-000">ScriptObject</span>,"<span class="text-blue-000">callback</span>"","<span class="text-green-000">SQL</span>")
>
> ##### <span class="text-red-300">dbi</span>
>
> This is the global object that interacts with the database, it is the same object that the game uses to query the database
>
> ##### <span class="text-purple-000">ScriptObject</span>
>
> Refers to the object you've defined as your mod, it is used to scope your queries to your object
>
> ##### <span class="text-blue-000">callback</span>
>
> Your callback reference, it should match the function name that will handle the callback of your query.
>
> ##### <span class="text-green-000">SQL</span>
>
> Your SQL query this is where you will add your SQL statements that will be sent to the database






### Select statements with examples 

When setting up select, we do this with a <span class="text-blue-000">callback</span> property of the call, so that any results from your <span class="text-green-000">query</span> is returned to the <span class="text-blue-000">callback</span> function you define.

Whenever we finish a query it is very important to eject the resultSet variable from tracking of dbi and delete the resultSet from memory.
This is in order to keep performance of your server and to not overwhelm capacity of result tracking that dbi does.

This example gets 1 row from characters and reads the ID column into a variable.

```
function DatabaseMod::select() {
  dbi.select(DatabaseMod,"result", "SELECT * from `characters` LIMIT 1");
}
function DatabaseMod::result(%this, %resultSet) {
  if(%resultSet.ok() && %resultSet.nextRecord())
  {
    %accountID = %resultSet.getFieldValue("ID");
  }
  dbi.remove(%resultSet);
  %resultSet.delete();
}

```
In order to fetch multiple rows, we need to alter it a little bit.
This will get all characters from the database and loop through each result as long as there is a new result.

```
function DatabaseMod::selectMultiple() {
  dbi.select(DatabaseMod,"result", "SELECT * from `characters`");
}
function DatabaseMod::multipleResults(%this, %resultSet) {
  if(%resultSet.ok())
  {
    while(%resultSet.nextRecord())
    {
      %accountID = %resultSet.getFieldValue("ID");
    }
  }
  dbi.remove(%resultSet);
  %resultSet.delete();
}

```
### The basic skeleton for setting up a update  query:

> <span class="text-red-300">dbi</span>.("<span class="text-green-000">SQL</span>")

### Update statements with examples 


```
function DatabaseMod::update() {
  dbi.update("UPDATE `characters` SET key='value' WHERE ID = 1");
}

```

### Insert statements with examples 

Simple insert, we use update here because we don't need anything in return, update is purely a single statement so it works well for insertion.
```
function DatabaseMod::insert() {
  dbi.update("INSERT INTO `table` (keys) VALUES (values)");
}

```

When we need to track the primary key that was given to the row after insertion, we can use select statements instead of update and pass the callback to a callback function, similar to the select above. 
The difference beeing we decide which column returns by the trailing SQL statemetn of RETURNING ID. Which in this case would return the primary key column "ID".

```
function DatabaseMod::insert() {
  dbi.select(DatabaseMod,"insertResult", "INSERT INTO `table` (keys) VALUES (values) RETURNING ID");
}
function DatabaseMod::insertResult(%this, %resultSet) {
  if(%resultSet.ok() && %resultSet.nextRecord())
  {
    %accountID = %resultSet.getFieldValue("ID");
  }
  dbi.remove(%resultSet);
  %resultSet.delete();
}

```

&nbsp;

**Congratulations**, that completes the mod! You should now have a foundational understanding of how to properly use databases from your server side mods.

The complete mod should look like the following

```
/**
* <author></author>
* <url></url>
* <credits></credits>
* <description></description>
* <license>GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007</license>
*/

// Register your mod as an object in the game engine, important for loading and unloading a package (mod)
if (!isObject(DatabaseMod))
{
    new ScriptObject(DatabaseMod)
    {
    };
}

package HelloWorldMod
{
  function DatabaseMod::version() {
    return "v1.0.0";
  }

  function DatabaseMod::setup() {

    LiFx::registerCallback($LiFx::hooks::onConnectCallbacks, sendHelloWorld, DatabaseMod);
  }

  function DatabaseMod::sendHelloWorld(%this, %client) {
    %client.cmSendClientMessage(2476, "Hello World!");
  }
};
activatePackage(DatabaseMod);
```
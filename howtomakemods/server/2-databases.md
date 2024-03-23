---
_schema: layout
layout: default
nav_order: 2
last_modified_date: 2022-12-09 12:20:18
title: 2. Databases
parent: Server side mods
grand_parent: How to make mods
nav_exclude: false
has_children: false
has_toc: false
---
# 2\. Databases

&nbsp;

In this scenario we will make a simple mod that explores the databases features of the global "dbi" object. If you haven't yet, please review tutorial [\#1 Hello World](/howtomakemods/server/helloworld.html "Tutorial #1 Hello World") which introduces you to setting up a local development area and the basic concepts of writing mods in the LiFx framework.

From our experience and testing, even though there are several functions available, the only two we've seen work without issues are **Query** and **Select** we recommend that you avoid using the other functions exposed, as they tend to put your server in an unstable state, eventually crashing.

It is also very important to close the handlers properly as to not create open connections that linger after they are no longer needed. This will cause the torque <br>engine to do heavy cleanups if not done properly.

### Select

When setting up select, we do this with a callback property of the call, so that any results from your query is returned to the callback function you define.

&nbsp;

The basic skeleton for setting up a select query:

<span class=".bg-red-300">dbi</span>.(<span class=".bg-yellow-000">ScriptObject</span>,"<span class=".bg-blue-000">callback</span>"","<span class=".bg-green-000">SQL</span>")

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
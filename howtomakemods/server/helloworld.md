---
_schema: layout
layout: default
nav_order: 2
last_modified_date: 2022-12-09 12:20:18
title: 1. Hello World
parent: Server side mods
grand_parent: How to make mods
nav_exclude: false
has_children: false
has_toc: false
---
# 1\. Hello World

In this scenario we will make a simple mod that greets the connected player with a message that displays "Hello World".

This will introduce you to setting up local development area as well as introduce you to some of the out of the box functionality of our server framework.

This series makes the assumption you are using Visual Studio Code when making your Torque Script mods for Life is Feudal: Your Own, and that you have set up your environment according to getting ready.

Start off by opening Visual Studio Code, and choose&nbsp;![](/uploads/screenshot-2023-10-19-191040.png){: width="209" height="55"}&nbsp;point it to the mods folder here:

**C:\\Steam\\steamapps\\common\\Life Is Feudal Your Own Dedicated Server\\mods**<br>​​<br>Under Explorer on the left menu, create a folder named "HelloWorld" and then make a new file in the "HelloWorld" folder, named "mod.cs"![](/uploads/screenshot-2023-10-19-191444.png){: width="348" height="127"}

Start by adding a comment to tell everyone who you are, where they can reach you a description of your mod and also reference the GNU GPLv3 license.

```
/**
* <author></author>
* <url></url>
* <credits></credits>
* <description></description>
* <license>GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007</license>
*/
```

Following that, we make it a good habit to make sure the object doesn't already exist as Life is Feudal, will crash if there are multiple instances made of the same object.<br>We are naming our package HelloWorldMod, which is then the object we will need to check for

```
// Register your mod as an object in the game engine, important for loading and unloading a package (mod)
if (!isObject(HelloWorldMod))
{
    new ScriptObject(HelloWorldMod)
    {
    };
}
```

After we've done that, we make a package.<br>In Torque Engine, packages are activatable and deactivatable during runtime. It is how we override functions and essential to how we can load mods during startup using the LiFx framework.

Each package should be unique, and all your functionality should generally be defined within a package, in order to make sure you have the highest compatibility with other mods.

```
// LiFx expect each mod to be it's own unique package
package HelloWorldMod
{
};
```

Notice the trailing ";" after the closing curly bracket \}, as this is not consistent within Torque Script. They are used generally for making Objects and for Packages. Functions and conditional statements do not have the trailing curly brackets.

Great we now have a basic shell for a mod. We will extend this with required functions as defined by LiFx framework before we move on to adding our Hello World message and functionality.

LiFx server framework has requirements on two functions as a minimum. These are "setup" and "version" as they are called by the framework, expecting each and every mod to have both of these functions defined during boot. "version" is expected to return a string, using a semver 2 compatible versioning number of your mod. This will be displayed to every connecting player informing them of your mod being used, as well as the version of it, which the LiFx framework pulls from this function.

The mod.cs so far should look like this, before we add "setup" and "version":

```
/**
* <author></author>
* <url></url>
* <credits></credits>
* <description></description>
* <license>GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007</license>
*/

// Register your mod as an object in the game engine, important for loading and unloading a package (mod)
if (!isObject(HelloWorldMod))
{
    new ScriptObject(HelloWorldMod)
    {
    };
}


// LiFx expect each mod to be it's own unique package
package HelloWorldMod
{
};
```

When we've added "setup" and "version" it will look like this:

```
/**
* <author></author>
* <url></url>
* <credits></credits>
* <description></description>
* <license>GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007</license>
*/

// Register your mod as an object in the game engine, important for loading and unloading a package (mod)
if (!isObject(HelloWorldMod))
{
    new ScriptObject(HelloWorldMod)
    {
    };
}


// LiFx expect each mod to be it's own unique package
package HelloWorldMod
{
  // Returns a string as a version, LiFx will look for this specific function to output version to new connecting players
  // Takes no parameters, is a reserved function for LiFx compatability.
  function HelloWorldMod::version() {
    return "v1.0.0";
  }

  // The setup method is required, and will be looked for by the framework, if it doesn't have it your mod will not execute
  // This is where you tell the framework, which hooks you use and what object types you have added, so that the framework can call your code at the appropiate time
  function HelloWorldMod::setup() {

  }
};
```

Notice we are scoping our namespace of the package "HelloWorldMod::" this is how we ensure that the functions are scoped correctly inside our functions, and that they are then overridable by other mods if necessary.&nbsp;

All good so far! Let's get going into the next part. Hooking up our custom "Hello World" to LiFx Framework.

In order to do this, we have to do two things:

1. We need to define the function that will send the player "Hello World"
2. We need to add a line in "setup" to hook our function to a LiFx Framework event.

We will call our function "sendHelloWorld", and in order to send the client a message, we also need a reference to the client. LiFx Framework also sends a local reference to "HelloWorldMod", so we need to reference that by using %this, we will add a reference to the client by assigning that a variable of %client. As shown here:

```
  function HelloWorldMod::sendHelloWorld(%this, %client) {
  }
```

Notice we are scoping it to our mod "HelloWorldMod", our function name is sendHelloWorld and we are taking two parameters, %this and %client. %client references the player connecting, allowing us to send the client messages. Now in order to give the function "life" we need to tell LiFx Framework, that the function exists, and when we want the framework to pass on information about the client to our mod. We will do that by using the functionality of LiFx Framework by calling the function "LiFx::registerCallback"

It takes three parameters.

* The first parameter references what hook you want to add your function to, we will use "onConnectCallbacks" to tell LiFx Framework, we want our function to be called when a player connects.
* The second parameter references the name of your function, the name of our function is "sendHelloWorld"
* The third parameter references the namespace of your mod so that it calls the correct function, the name of our namespace is "HelloWorldMod"

```
LiFx::registerCallback($LiFx::hooks::onConnectCallbacks, sendHelloWorld, HelloWorldMod);
```

In order for this to work, we have to put this into "setup", like this:

```
  function HelloWorldMod::setup() {

    LiFx::registerCallback($LiFx::hooks::onConnectCallbacks, sendHelloWorld, HelloWorldMod);
  }
```

This will now ensure that whenever a player is connected, our function will be called. Let's add the last remaining information so that our function, actually sends the player a pop up window to welcome the player to the server.

```
  function HelloWorldMod::sendHelloWorld(%this, %client) {
    %client.cmSendClientMessage(2476, "Hello World!");
  }
```

2476 is the message type we want to send, this displays the string we put as the 2nd argument, together with a button to acknowledge the message.

On the very last line, as per requirement of LiFx Framework, we have to activate our mod, we do that by using "activatePackage(HelloWorldMod)"

```
activatePackage(HelloWorldMod);
```

**Congratulations**, that completes the mod! You are now a bonafide Life is Feudal: Your Own modder.

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
if (!isObject(HelloWorldMod))
{
    new ScriptObject(HelloWorldMod)
    {
    };
}

package HelloWorldMod
{
  function HelloWorldMod::version() {
    return "v1.0.0";
  }

  function HelloWorldMod::setup() {

    LiFx::registerCallback($LiFx::hooks::onConnectCallbacks, sendHelloWorld, HelloWorldMod);
  }

  function HelloWorldMod::sendHelloWorld(%this, %client) {
    %client.cmSendClientMessage(2476, "Hello World!");
  }
};
activatePackage(HelloWorldMod);
```
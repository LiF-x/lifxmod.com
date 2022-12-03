---
layout: default
last_modified_date: 2022-12-03 15:08:18 +0000
title: Console classes
nav_order: 5
nav_exclude: false
parent: Documentation
has_children: false
has_toc: false
published: false

---
    /*!
    @brief Base class for almost all objects involved in the simulation.
    
    @ingroup Console
     */
    class  SimObject {
      public:
       /*! Dump the hierarchy of this object up to RootGroup to the console. */
       virtual void dumpGroupHierarchy(()) {}
       /*! Test whether the given method is defined on this object.
    @param The name of the method.
    @return True if the object implements the given method. */
       virtual bool isMethod(( string methodName )) {}
       /*! Test whether the object belongs directly or indirectly to the given group.
    @param group The SimGroup object.
    @return True if the object is a child of the given group or a child of a group that the given group is directly or indirectly a child to. */
       virtual bool isChildOfGroup(( SimGroup group )) {}
       /*! Get the name of the class namespace assigned to this object.
    @return The name of the 'class' namespace. */
       virtual string getClassNamespace(()) {}
       /*! Get the name of the superclass namespace assigned to this object.
    @return The name of the 'superClass' namespace. */
       virtual string getSuperClassNamespace(()) {}
       /*! Assign a class namespace to this object.
    @param name The name of the 'class' namespace for this object. */
       virtual void setClassNamespace(( string name )) {}
       /*! Assign a superclass namespace to this object.
    @param name The name of the 'superClass' namespace for this object. */
       virtual void setSuperClassNamespace(( string name )) {}
       /*! Get whether the object has been marked as expanded. (in editor)
    @return True if the object is marked expanded. */
       virtual bool isExpanded(()) {}
       /*! Set whether the object has been marked as expanded. (in editor)
    @param state True if the object is to be marked expanded; false if not. */
       virtual void setIsExpanded(( bool state=true )) {}
       /*! Returns the filename the object is attached to.
    @return The name of the file the object is associated with; usually the file the object was loaded from. */
       virtual string getFilename(()) {}
       /*! Sets the object's file name and path
    @param fileName The name of the file to associate this object with. */
       virtual void setFilename(( string fileName )) {}
       /*! Get the line number at which the object is defined in its file.
    
    @return The line number of the object's definition in script.
    @see getFilename() */
       virtual int getDeclarationLine(()) {}
       /*! Copy fields from another object onto this one.  The objects must be of same type. Everything from the object will overwrite what's in this object; extra fields in this object will remain. This includes dynamic fields.
    @param fromObject The object from which to copy fields. */
       virtual void assignFieldsFrom(( SimObject fromObject )) {}
       /*! Assign a persistent ID to the object if it does not already have one. */
       virtual void assignPersistentId(()) {}
       /*! Get whether the object will be included in saves.
    @return True if the object will be saved; false otherwise. */
       virtual bool getCanSave(()) {}
       /*! Set whether the object will be included in saves.
    @param value If true, the object will be included in saves; if false, it will be excluded. */
       virtual void setCanSave(( bool value=true )) {}
       /*! Get whether this object may be renamed.
    @return True if this object can be renamed; false otherwise. */
       virtual bool isNameChangeAllowed(()) {}
       /*! Set whether this object can be renamed from its first name.
    @param value If true, renaming is allowed for this object; if false, trying to change the name of the object will generate a console error. */
       virtual void setNameChangeAllowed(( bool value=true )) {}
       /*! Create a copy of this object.
    @return An exact duplicate of this object. */
       virtual string clone(()) {}
       /*! Create a copy of this object and all its subobjects.
    @return An exact duplicate of this object and all objects it references. */
       virtual string deepClone(()) {}
       /*! Hide/unhide the object.
    @param value If true, the object will be hidden; if false, the object will be unhidden. */
       virtual void setHidden(( bool value=true )) {}
       /*! List the methods defined on this object.
    @return An ArrayObject populated with (name,description) pairs of all methods defined on the object. */
       virtual string dumpMethodsArray(()) {}
       /*! Dump a description of all fields and methods defined on this object to the console.
    @param detailed Whether to print detailed information about members. */
       virtual void dump(( bool detailed=false )) {}
       /*! Dump a description of all fields and methods defined on this object to the console.
    @param detailed Whether to print detailed information about members. */
       virtual void dumpMethods(( bool detailed=false )) {}
       /*! Dump a description of all fields and methods defined on this object to the console.
    @param detailed Whether to print detailed information about members. */
       virtual void dumpFields(( bool detailed=false )) {}
       /*! Dump a description of all fields and methods defined on this object to the console.
    @param detailed Whether to print detailed information about members. */
       virtual void dumpFieldsStatic(( bool detailed=false )) {}
       /*! Dump a description of all fields and methods defined on this object to the console.
    @param detailed Whether to print detailed information about members. */
       virtual void dumpFieldsDynamic(( bool detailed=false )) {}
       /*! Save out the object to the given file.
    @param fileName The name of the file to save to.@param selectedOnly If true, only objects marked as selected will be saved out.
    @param preAppendString Text which will be preprended directly to the object serialization.
    @param True on success, false on failure. */
       virtual bool save(( string fileName, bool selectedOnly=false, string preAppendString="" )) {}
       /*! Set the global name of the object.
    @param newName The new global name to assign to the object.
    @note If name changing is disallowed on the object, the method will fail with a console error. */
       virtual void setName(( string newName )) {}
       /*! Get the global name of the object.
    @return The global name assigned to the object. */
       virtual string getName(()) {}
       /*! Get the name of the C++ class which the object is an instance of.
    @return The name of the C++ class of the object. */
       virtual string getClassName(()) {}
       /*! Return the value of the given field on this object.
    @param fieldName The name of the field.  If it includes a field index, the index is parsed out.
    @param index Optional parameter to specify the index of an array field separately.
    @return The value of the given field or "" if undefined. */
       virtual string getFieldValue(( string fieldName, int index=-1 )) {}
       /*! Set the value of the given field on this object.
    @param fieldName The name of the field to assign to.  If it includes an array index, the index will be parsed out.
    @param value The new value to assign to the field.
    @param index Optional argument to specify an index for an array field.
    @return True. */
       virtual bool setFieldValue(( string fieldName, string value, int index=-1 )) {}
       /*! Get the console type code of the given field.
    @return The numeric type code for the underlying console type of the given field. */
       virtual string getFieldType(( string fieldName )) {}
       /*! Set the console type code for the given field.
    @param fieldName The name of the dynamic field to change to type for.
    @param type The name of the console type.
    @note This only works for dynamic fields.  Types of static fields cannot be changed. */
       virtual void setFieldType(( string fieldName, string type )) {}
       virtual string call() {}
       /*! Set the internal name of the object.
    @param newInternalName The new internal name for the object. */
       virtual void setInternalName(( string newInternalName )) {}
       /*! Get the internal name of the object.
    @return The internal name of the object. */
       virtual string getInternalName(()) {}
       /*! Dump the native C++ class hierarchy of this object's C++ class to the console. */
       virtual void dumpClassHierarchy(()) {}
       /*! Test whether this object is a member of the specified class.
    @param className Name of a native C++ class.
    @return True if this object is an instance of the given C++ class or any of its super classes. */
       virtual bool isMemberOfClass(( string className )) {}
       /*! Test whether the namespace of this object is a direct or indirect child to the given namespace.
    @param name The name of a namespace.
    @return True if the given namespace name is within the namespace hierarchy of this object. */
       virtual bool isInNamespaceHierarchy(( string name )) {}
       /*! Get the underlying unique numeric ID of the object.
    @note Object IDs are unique only during single engine runs.
    @return The unique numeric ID of the object. */
       virtual int getId(()) {}
       /*! Get the group that this object is contained in.
    @note If not assigned to particular SimGroup, an object belongs to RootGroup.
    @return The SimGroup object to which the object belongs. */
       virtual string getGroup(()) {}
       /*! Delete and remove the object. */
       virtual void delete(()) {}
       /*! safe delete and remove the object. */
       virtual void safeDeleteObject(()) {}
       virtual int schedule() {}
       /*! Get the number of dynamic fields defined on the object.
    @return The number of dynamic fields defined on the object. */
       virtual int getDynamicFieldCount(()) {}
       /*! Get a value of a dynamic field by index.
    @param index The index of the dynamic field.
    @return The value of the dynamic field at the given index or "". */
       virtual string getDynamicField(( int index )) {}
       /*! Get the number of static fields on the object.
    @return The number of static fields defined on the object. */
       virtual int getFieldCount(()) {}
       /*! Retrieve the value of a static field by index.
    @param index The index of the static field.
    @return The value of the static field with the given index or "". */
       virtual string getField(( int index )) {}
       virtual string describeSelf(()) {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /*!
       Optional global name of this object.
       
        */
       string name;
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /*!
       Optional name that may be used to lookup this object within a SimSet.
       
        */
       string internalName;
       /*!
       Group hierarchy parent of the object.
       
        */
       SimObject parentGroup;
       /*!
       Script class of object.
       
        */
       string class;
       /*!
       Script super-class of object.
       
        */
       string superClass;
       /*!
       Script class of object.
       
        */
       string className;
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /*!
       Whether the object is visible.
       
        */
       bool hidden;
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /*!
       Whether the object can be saved out. If false, the object is purely transient in nature.
       
        */
       bool canSave;
       /*!
       True if dynamic fields (added at runtime) should be saved. Defaults to true.
       
        */
       bool canSaveDynamicFields;
       /*!
       The universally unique identifier for the object.
       
        */
       pid persistentId;
       /*!
       True if this object is 4ever alone, perhaps it is an one side datablock.
       
        */
       bool local;
       /// @}
    
    };
    
    /*!
    @brief A collection of SimObjects.
    
    It is often necessary to keep track of an arbitrary set of SimObjects. For instance, Torque's networking code needs to not only keep track of the set of objects which need to be ghosted, but also the set of objects which must <i>always</i> be ghosted. It does this by working with two sets. The first of these is the RootGroup (which is actually a SimGroup) and the second is the GhostAlwaysSet, which contains objects which must always be ghosted to the client.
    
    Some general notes on SimSets:
    
    - Membership is not exclusive. A SimObject may be a member of multiple SimSets.
    
    - A SimSet does not destroy subobjects when it is destroyed.
    
    - A SimSet may hold an arbitrary number of objects.
    
    @ingroup Console
     */
    class  SimSet : public SimObject {
      public:
          /*! Called when an object is added to the set.
    @param object The object that was added. */
          void onObjectAdded( SimObject object );
    
          /*! Called when an object is removed from the set.
    @param object The object that was removed. */
          void onObjectRemoved( SimObject object );
    
       /*! Dump a list of all objects contained in the set to the console. */
       virtual void listObjects(()) {}
       virtual void add() {}
       virtual void remove() {}
       /*! Remove all objects from the set. */
       virtual void clear(()) {}
       virtual void deleteAllObjects() {}
       /*! Return a random object from the set.
    @return A randomly selected object from the set or -1 if the set is empty. */
       virtual string getRandom(()) {}
       virtual void callOnChildren() {}
       virtual void callOnChildrenNoRecurse() {}
       /*! Make sure child1 is ordered right before child2 in the set.
    @param child1 The first child.  The object must already be contained in the set.
    @param child2 The second child.  The object must already be contained in the set. */
       virtual void reorderChild(( SimObject child1, SimObject child2 )) {}
       /*! Get the number of objects contained in the set.
    @return The number of objects contained in the set. */
       virtual int getCount(()) {}
       virtual int getFullCount() {}
       /*! Get the object at the given index.
    @param index The object index.
    @return The object at the given index or -1 if index is out of range. */
       virtual string getObject(( int index )) {}
       /*! Return the index of the given object in this set.
    @param obj The object for which to return the index.  Must be contained in the set.
    @return The index of the object or -1 if the object is not contained in the set. */
       virtual int getObjectIndex(( SimObject obj )) {}
       /*! Test whether the given object belongs to the set.
    @param obj The object.
    @return True if the object is contained in the set; false otherwise. */
       virtual bool isMember(( SimObject obj )) {}
       /*! Find an object in the set by its internal name.
    @param internalName The internal name of the object to look for.
    @param searchChildren If true, SimSets contained in the set will be recursively searched for the object.
    @return The object with the given internal name or 0 if no match was found.
     */
       virtual string findObjectByInternalName(( string internalName, bool searchChildren=false )) {}
       /*! Make the given object the first object in the set.
    @param obj The object to bring to the frontmost position.  Must be contained in the set. */
       virtual void bringToFront(( SimObject obj )) {}
       /*! Make the given object the last object in the set.
    @param obj The object to bring to the last position.  Must be contained in the set. */
       virtual void pushToBack(( SimObject obj )) {}
       virtual void sort() {}
       /*! Test whether the given object may be added to the set.
    @param obj The object to test for potential membership.
    @return True if the object may be added to the set, false otherwise. */
       virtual bool acceptsAsChild(( SimObject obj )) {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A collection of SimObjects that are owned by the group.
    
    A SimGroup is a stricter form of SimSet. SimObjects may only be a member of a single SimGroup at a time. The SimGroup will automatically enforce the single-group-membership rule (ie. adding an object to a SimGroup will cause it to be removed from its current SimGroup, if any).
    
    Deleting a SimGroup will also delete all SimObjects in the SimGroup.
    
    @tsexample
    // Create a SimGroup for particle emitters
    new SimGroup(Emitters)
    {
       canSaveDynamicFields = "1";
    
       new ParticleEmitterNode(CrystalEmmiter) {
          active = "1";
          emitter = "dustEmitter";
          velocity = "1";
          dataBlock = "GenericSmokeEmitterNode";
          position = "-61.6276 2.1142 4.45027";
          rotation = "1 0 0 0";
          scale = "1 1 1";
          canSaveDynamicFields = "1";
       };
    
       new ParticleEmitterNode(Steam1) {
          active = "1";
          emitter = "SlowSteamEmitter";
          velocity = "1";
          dataBlock = "GenericSmokeEmitterNode";
          position = "-25.0458 1.55289 2.51308";
          rotation = "1 0 0 0";
          scale = "1 1 1";
          canSaveDynamicFields = "1";
       };
    };
    
    @endtsexample
    
    @ingroup Console
     */
    class  SimGroup : public SimSet {
      public:
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Provides the basis for implementing a multiplayer game protocol.
    
    NetConnection combines a low-level notify protocol implemented in ConnectionProtocol with a SimGroup, and implements several distinct subsystems:
    
    - <b>Event Manager</b>  This is responsible for transmitting NetEvents over the wire.  It deals with ensuring that the various types of NetEvents are delivered appropriately, and with notifying the event of its delivery status.
    
    - <b>Move Manager</b>  This is responsible for transferring a Move to the server 32 times a second (on the client) and applying it to the control object (on the server).
    
    - <b>Ghost Manager</b>  This is responsible for doing scoping calculations (on the server side) and transmitting most-recent ghost information to the client.
    
    - <b>File Transfer</b>  It is often the case that clients will lack important files when connecting to a server which is running a mod or new map. This subsystem allows the server to transfer such files to the client.
    
    - <b>Networked String Table</b>  String data can easily soak up network bandwidth, so for efficiency, we implement a networked string table. We can then notify the connection of strings we will reference often, such as player names, and transmit only a tag, instead of the whole string.
    
    - <b>Demo Recording</b>  A demo in Torque is a log of the network traffic between client and server; when a NetConnection records a demo, it simply logs this data to a file. When it plays a demo back, it replays the logged data.
    
    - <b>Connection Database</b>  This is used to keep track of all the NetConnections; it can be iterated over (for instance, to send an event to all active connections), or queried by address.
    
    The NetConnection is a SimGroup. On the client side, it contains all the objects which have been ghosted to that client. On the server side, it is empty; it can be used (typically in script) to hold objects related to the connection. For instance, you might place an observation camera in the NetConnnection. In both cases, when the connection is destroyed, so are the contained objects.
    
    The NetConnection also has the concept of local connections.  These are used when the client and server reside in the same process.  A local connection is typically required to use the standard Torque world building tools.  A local connection is also required when building a single player game.
    
    @see @ref Networking, @ref ghosting_scoping, @ref local_connections, GameConnection.
    
    @ingroup Networking
     */
    class  NetConnection : public SimGroup {
      public:
       virtual void sendCommand() {}
       virtual void sendCharList(()) {}
       virtual void registerByCharacter(()) {}
       virtual void registerByAccountId(()) {}
       virtual void unregisterByCharacter(()) {}
       virtual void unregisterByAccountId(()) {}
       virtual void setAccessRights(( String accessRights )) {}
       virtual void setAccessRight(( AccountAccess::Right right, bool flagValue )) {}
       virtual string getAccessRights(()) {}
       virtual bool haveAccessRight(( AccountAccess::Right testRight )) {}
       virtual int getEventQueueSize() {}
       virtual int getEventsSent() {}
       virtual int getMaxPacketDataSize() {}
       virtual int getBytesSentPerTick() {}
       virtual int getBytesReceivedPerTick() {}
       virtual int getEventsSentPerTick() {}
       virtual int getEventBytesSentPerTick() {}
       virtual int getEventsReceivedPerTick() {}
       virtual int getEventsBytesReceivedPerTick() {}
       virtual int getGhostUpdatesPerTick() {}
       virtual int getGhostUpdatesBytesPerTick() {}
       virtual int getPingTimeout(()) {}
       /*! @brief Returns the far end network address for the connection.
    
    The address will be in one of the following forms:
    - <b>IP:Broadcast:&lt;port&gt;</b> for broadcast type addresses
    - <b>IP:&lt;address&gt;:&lt;port&gt;</b> for IP addresses
    - <b>local</b> when connected locally (server and client running in same process
     */
       virtual string getAddress(()) {}
       virtual string getIP() {}
       virtual string getPort() {}
       /*! @brief Returns the average round trip time (in ms) for the connection.
    
    The round trip time is recalculated every time a notify packet is received.  Notify packets are used to information the connection that the far end successfully received the sent packet.
     */
       virtual int getPing(()) {}
       /*! @brief Returns the percentage of packets lost per tick.
    
    @note This method is not yet hooked up.
     */
       virtual int getPacketLoss(()) {}
       /*! @brief Ensures that all configured packet rates and sizes meet minimum requirements.
    
    This method is normally only called when a NetConnection class is first constructed.  It need only be manually called if the global variables that set the packet rate or size have changed.
    
    @note If $pref::Net::PacketRateToServer, $pref::Net::PacketRateToClient or $pref::Net::PacketSize have been changed since a NetConnection has been created, this method must be called on all connections for them to follow the new rates or size.
     */
       virtual void checkMaxRate(()) {}
       /*! @brief Returns true if the scoping is acitvated on this NetConnection. */
       virtual bool getScoping(()) {}
       /*! @brief Sets if debug statements should be written to the console log.
    
    @note Only valid if the executable has been compiled with TORQUE_DEBUG_NET.
     */
       virtual void setLogging(( bool state )) {}
       virtual int getAccountId(()) {}
       /*! @brief On the client, convert a ghost ID from this connection to a real SimObject ID.
    
    Torque's network ghosting system only exchanges ghost ID's between the server and client.  Use this method on the client to discover an object's local SimObject ID when you only have a ghost ID.
    @param ghostID The ghost ID of the object as sent by the server.
    @returns The SimObject ID of the object, or 0 if it could not be resolved.
    
    @tsexample
    %object = ServerConnection.resolveGhostID( %ghostId );
    @endtsexample
    
    @see @ref ghosting_scoping for a description of the ghosting system.
    
     */
       virtual int resolveGhostID(( int ghostID )) {}
       /*! @brief On the server, convert a ghost ID from this connection to a real SimObject ID.
    
    Torque's network ghosting system only exchanges ghost ID's between the server and client.  Use this method on the server to discover an object's local SimObject ID when you only have a ghost ID.
    @param ghostID The ghost ID of the object as sent by the server.
    @returns The SimObject ID of the object, or 0 if it could not be resolved.
    
    @tsexample
    %object = %client.resolveObjectFromGhostIndex( %ghostId );
    @endtsexample
    
    @see @ref ghosting_scoping for a description of the ghosting system.
    
     */
       virtual int resolveObjectFromGhostIndex(( int ghostID )) {}
       /*! @brief On server or client, convert a real id to the ghost id for this connection.
    
    Torque's network ghosting system only exchanges ghost ID's between the server and client.  Use this method on the server or client to discover an object's ghost ID based on its real SimObject ID.
    @param realID The real SimObject ID of the object.
    @returns The ghost ID of the object for this connection, or -1 if it could not be resolved.
    
    @see @ref ghosting_scoping for a description of the ghosting system.
    
     */
       virtual int getGhostID(( NetObject no )) {}
       /*! @brief Returns the NetConnection for given charId or NULL if not found. */
       virtual string findByCharId(( int charId )) {}
       /*! @brief Returns the NetConnection for given name and last name or NULL if not found. */
       virtual string findByCharName(( String charName )) {}
       /*! @brief Returns the NetConnection for given account id or NULL if not found. */
       virtual string findByAccountId(( int accountId )) {}
       /*! @brief Connects to the remote address.
    
    Attempts to connect with another NetConnection on the given address.  Typically once connected, a game's information is passed along from the server to the client, followed by the player entering the game world.  The actual procedure is dependent on the NetConnection subclass that is used.  i.e. GameConnection.
    @param remoteAddress The address to connect to in the form of IP:&lt;address&gt;:&lt;port&rt; although the <i>IP:</i> portion is optional.  The <i>address</i> portion may be in the form of w.x.y.z or as a host name, in which case a DNS lookup will be performed.  You may also substitue the word <i>broadcast</i> for the address to broadcast the connect request over the local subnet.
    
    @see NetConnection::connectLocal() to connect to a server running within the same process as the client.
     */
       virtual void connect(( string remoteAddress )) {}
       virtual bool isGM(()) {}
       virtual bool isPlayerDead(()) {}
       virtual void setPlayerDead(( bool isDead=true )) {}
       virtual bool isConnectionToServer(()) {}
       virtual int getRemoteServerID(()) {}
       /*! @brief Returns the number of active ghosts on the connection. */
       virtual int getGhostsActive(()) {}
       virtual void setScopeObject(( NetObject obj )) {}
       virtual string getScopeObject(()) {}
       virtual void dumpGhostInfo(()) {}
    
       /*! @name Character
       @{ */
       /*! */
       /*!
       
       
        */
       int charId;
       /*!
       
       
        */
       string charName;
       /*!
       
       
        */
       string charLastName;
       /// @}
    
    
       /*! @name Debugging
       @{ */
       /*! */
       /*!
       
       
        */
       bool debugEnabled;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief The game-specific subclass of NetConnection.
    
    The GameConnection introduces the concept of the control object.  The control object is simply the object that the client is associated with that network connection controls.  By default the control object is an instance of the Player class, but can also be an instance of Camera (when editing the mission, for example), or any other ShapeBase derived class as appropriate for the game.
    
    Torque uses a model in which the server is the authoritative master of the simulation.  To prevent clients from cheating, the server simulates all player moves and then tells the client where his player is in the world.  This model, while secure, can have problems.  If the network latency is high, this round-trip time can give the player a very noticeable sense of movement lag.  To correct this problem, the game uses a form of prediction - it simulates the movement of the control object on the client and on the server both.  This way the client doesn't need to wait for round-trip verification of his moves.  Only in the case of a force acting on the control object on the server that doesn't exist on the client does the client's position need to be forcefully changed.
    
    To support this, all control objects (derivative of ShapeBase) must supply a writePacketData() and readPacketData() function that send enough data to accurately simulate the object on the client.  These functions are only called for the current control object, and only when the server can determine that the client's simulation is somehow out of sync with the server.  This occurs usually if the client is affected by a force not present on the server (like an interpolating object) or if the server object is affected by a server only force (such as the impulse from an explosion).
    
    The Move structure is a 32 millisecond snapshot of player input, containing x, y, and z positional and rotational changes as well as trigger state changes. When time passes in the simulation moves are collected (depending on how much time passes), and applied to the current control object on the client. The same moves are then packed over to the server in GameConnection::writePacket(), for processing on the server's version of the control object.
    
    @see @ref Networking, NetConnection, ShapeBase
    
    @ingroup Networking
     */
    class  GameConnection : public NetConnection {
      public:
       virtual Script onPatched(( string this )) {}
       virtual Script onGhostAlwaysObjectsReceived(( string this )) {}
       virtual Script prepareClient(( string this )) {}
       virtual Script onDrop(( string this, string reason )) {}
       virtual Script onDeath(( string this, string sourceObject, string sourceClient, string damageType, string damLoc )) {}
       virtual Script onClientLeaveGame(( string this )) {}
       virtual Script trySpawnPlayer(( string this )) {}
       virtual Script onClientEnterGame(( string this )) {}
       virtual Script postConnectRoutine(( string this )) {}
       virtual Script isReadyForCharList(( string this )) {}
       virtual Script onAuthorized(( string this )) {}
       virtual Script onConnect(( string this )) {}
       /*!  This method (and a few others around) is duplicated on Dispatcher
     */
       virtual Script dropDuplicatedConnection(( string this, string useCharId )) {}
       /*!  Clear data of the previous play session (char data)
     */
       virtual Script clearPlaySession(( string this )) {}
       virtual Script onConnectRequest(( string this, string netAddress, string name )) {}
       virtual Script onPreConnectRequest(( string this, string netAddress, string name )) {}
       virtual Script pc_pathFinish(( string this )) {}
       virtual Script pc_pathPoint(( string this, string a1 )) {}
       virtual Script pc_loadPath(( string this )) {}
       virtual Script pc_dumpPath(( string this )) {}
       virtual Script pc__recordCurrentPoint(( string this )) {}
       virtual Script pc_startStopRecordingPath(( string this )) {}
       virtual Script pc_decSpeed(( string this, string dec )) {}
       virtual Script pc_incSpeed(( string this, string inc )) {}
       virtual Script pc_updateCurrentPoint(( string this, string skipSwitch )) {}
       virtual Script pc_adjustCurrentPoint(( string this )) {}
       virtual Script pc_jumpPrevPoint(( string this )) {}
       virtual Script pc_jumpNextPoint(( string this )) {}
       virtual Script pc_jumpPoint(( string this, string a1 )) {}
       virtual Script pc_backwardFly(( string this )) {}
       virtual Script pc_forwardFly(( string this )) {}
       virtual Script pc_stopFly(( string this )) {}
       virtual Script pc_followPath(( string this )) {}
       virtual Script pc_addCurrentAsPoint(( string this )) {}
       virtual Script pc_addPoint(( string this, string a1 )) {}
       virtual Script pc_resetPath(( string this )) {}
       virtual Script updateCamera(( string this )) {}
       virtual Script updateCameraSettings(( string this )) {}
          /*! @brief Called on the client when the connection to the server times out.
    
     */
          void onConnectionTimedOut();
    
          /*! @brief Called on the client when the connection to the server has been established.
    
     */
          void onConnectionAccepted();
    
          /*! @brief Called on the server when the client has been authorized.
    
     */
          void onConnect();
    
          /*! @brief Called when connection attempts have timed out.
    
     */
          void onConnectRequestTimedOut();
    
          /*! @brief Called on the client when the connection to the server has been dropped.
    
    @param reason The reason why the connection was dropped.
    
     */
          void onConnectionDropped( string reason );
    
          /*! @brief Called on the client when the connection to the server has been rejected.
    
    @param reason The reason why the connection request was rejected.
    
     */
          void onConnectRequestRejected( string reason );
    
          /*! @brief Called on the client when there is an error with the connection to the server.
    
    @param errorString The connection error text.
    
     */
          void onConnectionError( string errorString );
    
          /*! @brief Called on the server when the client's connection has been dropped.
    
    @param disconnectReason The reason why the connection was dropped.
    
     */
          void onDrop( string disconnectReason );
    
          /*! @brief Called on the client when the first control object has been set by the server and we are now ready to go.
    
    A common action to perform when this callback is called is to switch the GUI canvas from the loading screen and over to the 3D game GUI. */
          void initialControlSet();
    
          /*! @brief Called on the client to display the lag icon.
    
    When the connection with the server is lagging, this callback is called to allow the game GUI to display some indicator to the player.
    
    @param state Set to true if the lag icon should be displayed.
    
     */
          void setLagIcon( bool state );
    
          /*! @brief Called on the server when all datablocks has been sent to the client.
    
    During phase 1 of the mission download, all datablocks are sent from the server to the client.  Once all datablocks have been sent, this callback is called and the mission download procedure may move on to the next phase.
    
    @param sequence The sequence is common between the server and client and ensures that the client is acting on the most recent mission start process.  If an errant network packet (one that was lost but has now been found) is received by the client with an incorrect sequence, it is just ignored.  This sequence number is updated on the server every time a mission is loaded.
    
    @see GameConnection::transmitDataBlocks()
    
     */
          void onDataBlocksDone( int sequence );
    
          /*! @brief Called on the client when the damage flash or white out states change.
    
    When the server changes the damage flash or white out values, this callback is called either is on or both are off.  Typically this is used to enable the flash postFx.
    
    @param state Set to true if either the damage flash or white out conditions are active.
    
     */
          void onFlash( bool state );
    
       /*! @brief Called by the server during phase 2 of the mission download to start sending ghosts to the client.
    
    Ghosts represent objects on the server that are in scope for the client.  These need to be synchronized with the client in order for the client to see and interact with them.  This is typically done during the standard mission start phase 2 when following Torque's example mission startup sequence.
    
    @tsexample
    function serverCmdMissionStartPhase2Ack(%client, %seq, %playerDB)
    {
       // Make sure to ignore calls from a previous mission load
       if (%seq != $missionSequence || !$MissionRunning)
          return;
       if (%client.currentPhase != 1.5)
          return;
       %client.currentPhase = 2;
    
       // Set the player datablock choice
       %client.playerDB = %playerDB;
    
       // Update mod paths, this needs to get there before the objects.
       %client.transmitPaths();
    
       // Start ghosting objects to the client
       %client.activateGhosting();
    }
    @endtsexample
    
    @see @ref ghosting_scoping for a description of the ghosting system.
    
     */
       virtual void activateGhosting(()) {}
       /*! @brief On the server, resets the connection to indicate that ghosting has been disabled.
    
    Typically when a mission has ended on the server, all connected clients are informed of this change and their connections are reset back to a starting state.  This method resets a connection on the server to indicate that ghosts are no longer being transmitted.  On the client end, all ghost information will be deleted.
    
    @tsexample
       // Inform the clients
       for (%clientIndex = 0; %clientIndex < ClientGroup.getCount(); %clientIndex++)
       {
          // clear ghosts and paths from all clients
          %cl = ClientGroup.getObject(%clientIndex);
          %cl.endMission();
          %cl.resetGhosting();
          %cl.clearPaths();
       }
    @endtsexample
    
    @see @ref ghosting_scoping for a description of the ghosting system.
    
     */
       virtual void resetGhosting(()) {}
       /*! @brief On the server, sets the object that the client will control.
    
    By default the control object is an instance of the Player class, but can also be an instance of Camera (when editing the mission, for example), or any other ShapeBase derived class as appropriate for the game.
    
    @param ctrlObj The GameBase object on the server to control. */
       virtual bool setControlObject(( GameBase ctrlObj )) {}
       /*! @brief On the server, returns the object that the client is controlling.By default the control object is an instance of the Player class, but can also be an instance of Camera (when editing the mission, for example), or any other ShapeBase derived class as appropriate for the game.
    
    @see GameConnection::setControlObject()
    
     */
       virtual string getControlObject(()) {}
       virtual void forceUpdateControl(()) {}
       /*! @brief On the server, transmits the mission file's CRC value to the client.
    
    Typically, during the standard mission start phase 1, the mission file's CRC value on the server is send to the client.  This allows the client to determine if the mission has changed since the last time it downloaded this mission and act appropriately, such as rebuilt cached lightmaps.
    
    @param CRC The mission file's CRC value on the server.
    
    @tsexample
    function serverCmdMissionStartPhase1Ack(%client, %seq)
    {
       // Make sure to ignore calls from a previous mission load
       if (%seq != $missionSequence || !$MissionRunning)
          return;
       if (%client.currentPhase != 0)
          return;
       %client.currentPhase = 1;
    
       // Start with the CRC
       %client.setMissionCRC( $missionCRC );
    
       // Send over the datablocks...
       // OnDataBlocksDone will get called when have confirmation
       // that they've all been received.
       %client.transmitDataBlocks($missionSequence);
    }
    @endtsexample
    
     */
       virtual void setMissionCRC(( int CRC )) {}
       /*! @brief On the game server, schedule a disconnect event for a client and pass along an optional reason why.
    
    This method performs three operations: it schedules a disconect for a given ms, than it disconnects a client connection from the server, and it deletes the connection object.  The reason is sent in the disconnect packet and is often displayed to the user so they know why they've been disconnected.
    
    @param reason The reason why the user has been disconnected from the server.
    
    @param timeoutMs The ms to use for a scheduled disconnect.
    
    @tsexample
    function kick(%client)
    {
       messageAll( 'MsgAdminForce', '\c2The Admin has kicked %1.', %client.playerName);
    
       BanList::add(%client.guid, %client.getAddress(), $Pref::Server::KickBanTime);
       %client.scheduleDelete("You have been kicked from this server", 2000);
    }
    @endtsexample
    
     */
       virtual int scheduleDelete(( string reason, int timeoutMs=0 )) {}
       /*! @brief On the server, disconnect a client and pass along an optional reason why.
    
    This method performs two operations: it disconnects a client connection from the server, and it deletes the connection object.  The optional reason is sent in the disconnect packet and is often displayed to the user so they know why they've been disconnected.
    
    @param reason [optional] The reason why the user has been disconnected from the server.
    
    @tsexample
    function kick(%client)
    {
       messageAll( 'MsgAdminForce', '\c2The Admin has kicked %1.', %client.playerName);
    
       BanList::add(%client.guid, %client.getAddress(), $Pref::Server::KickBanTime);
       %client.delete("You have been kicked from this server");
    }
    @endtsexample
    
     */
       virtual void delete(( string reason="" )) {}
       virtual void initPlayerManager(()) {}
       virtual int getCharacterId(()) {}
       virtual int getAccountId(()) {}
       virtual int getPlayerId(()) {}
       virtual void cmSendClientMessage(( int id, string str="" )) {}
       virtual string getPlayerDatablock(()) {}
    
       /*! @name Character
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Debugging
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  cmClientConnection : public GameConnection {
      public:
       virtual Script joinToServer(( string this )) {}
       virtual Script informAboutLocalCS(( string this )) {}
       virtual Script calcCsHash(( string this )) {}
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ch_4 : public cmClientConnection {
      public:
    };
    
    /*!
    @brief Superclass for all ghostable networked objects.
    
    @ingroup Networking
     */
    class  NetObject : public SimObject {
      public:
       virtual void clearScopeAlways() {}
       /*! Assign ObjectGID to the NetObject from the smPendingGID map, in case its there.
    This may happen if the player jumps from another server to us (homecoming and alike). */
       virtual void assignObjectGID(( int charId )) {}
       /*! @brief Cause the NetObject to be forced as scoped on the specified NetConnection.
    
    @param client The connection this object will always be scoped to
    
    @tsexample
    // Called to create new cameras in TorqueScript
    // %this - The active GameConnection
    // %spawnPoint - The spawn point location where we creat the camera
    function GameConnection::spawnCamera(%this, %spawnPoint)
    {
    ^// If this connection's camera exists
    ^if(isObject(%this.camera))
    ^{
    ^^// Add it to the mission group to be cleaned up later
    ^^MissionCleanup.add( %this.camera );
    
    ^^// Force it to scope to the client side
    ^^%this.camera.scopeToClient(%this);
    ^}
    }
    @endtsexample
    
     */
       virtual void scopeToClient(( NetConnection client )) {}
       /*! @brief Undo the effects of a scopeToClient() call.
    
    @param client The connection to remove this object's scoping from 
    
     */
       virtual void clearScopeToClient(( NetConnection client )) {}
       /*! @brief Always scope this object on all connections.
    
    The object is marked as ScopeAlways and is immediately ghosted to all active connections.  This function has no effect if the object is not marked as Ghostable.
    
     */
       virtual void setScopeAlways(()) {}
       virtual int getNetFlags(()) {}
       /*! @brief Get the ghost index of this object from the server.
    
    @tsexample
    %ghostID = LocalClientConnection.getGhostId( %serverObject );
    @endtsexample
    
    @return The index of this ghost in the GhostManager on the server */
       virtual int getGhostID(()) {}
       /*! @brief Called to check if an object resides on the clientside.
    
    @return True if the object resides on the client, false otherwise. */
       virtual bool isClientObject(()) {}
       /*! @brief Checks if an object resides on the server.
    
    @return True if the object resides on the server, false otherwise. */
       virtual bool isServerObject(()) {}
       virtual string getObjectGID(()) {}
       virtual int getGIDIncrement(()) {}
       virtual int getGIDServerId(()) {}
       virtual int getGIDusage(()) {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A networkable object that exists in the 3D world.
    
    The SceneObject class provides the foundation for 3D objects in the Engine.  It exposes the functionality for:
    
    <ul><li>Position, rotation and scale within the world.</li><li>Working with a scene graph (in the Zone and Portal sections), allowing efficient and robust rendering of the game scene.</li><li>Various helper functions, including functions to get bounding information and momentum/velocity.</li><li>Mounting one SceneObject to another.</li><li>An interface for collision detection, as well as ray casting.</li><li>Lighting. SceneObjects can register lights both at lightmap generation time, and dynamic lights at runtime (for special effects, such as from flame or a projectile, or from an explosion).</li></ul>
    
    You do not typically work with SceneObjects themselves.  The SceneObject provides a reference within the game world (the scene), but does not render to the client on its own.  The same is true of collision detection beyond that of the bounding box.  Instead you use one of the many classes that derrive from SceneObject, such as TSStatic.
    
    @section SceneObject_Hiding Difference Between setHidden() and isRenderEnabled
    
    When it comes time to decide if a SceneObject should render or not, there are two methods that can stop the SceneObject from rendering at all.  You need to be aware of the differences between these two methods as they impact how the SceneObject is networked from the server to the client.
    
    The first method of manually controlling if a SceneObject is rendered is through its SceneObject::isRenderEnabled property.  When set to false the SceneObject is considered invisible but still present within the scene.  This means it still takes part in collisions and continues to be networked.
    
    The second method is using the setHidden() method.  This will actually remove a SceneObject from the scene and it will no longer be networked from the server to the cleint.  Any client-side ghost of the object will be deleted as the server no longer considers the object to be in scope.
    
    @ingroup gameObjects
     */
    class  SceneObject : public NetObject {
      public:
       virtual Script OnArrowDamage(()) {}
       /*! Return the type mask for this object.
    @return The numeric type mask for the object. */
       virtual int getType(()) {}
       /*! @brief Mount objB to this object at the desired slot with optional transform.
    
    @param objB  Object to mount onto us
    @param slot  Mount slot ID
    @param txfm (optional) mount offset transform
    @return true if successful, false if failed (objB is not valid) */
       virtual bool mountObject(( SceneObject objB, int slot, TransformF txfm=MatrixF::Identity )) {}
       /*! @brief Unmount an object from ourselves.
    
    @param target object to unmount
    @return true if successful, false if failed
     */
       virtual bool unmountObject(( SceneObject target )) {}
       /*! Unmount us from the currently mounted object if any.
     */
       virtual void unmount(()) {}
       /*! @brief Check if we are mounted to another object.
    
    @return true if mounted to another object, false if not mounted. */
       virtual bool isMounted(()) {}
       /*! @brief Get the object we are mounted to.
    
    @return the SimObjectID of the object we're mounted to, or 0 if not mounted. */
       virtual int getObjectMount(()) {}
       /*! Get the number of objects mounted to us.
    @return the number of mounted objects. */
       virtual int getMountedObjectCount(()) {}
       /*! Get the object mounted at a particular slot.
    @param slot mount slot index to query
    @return ID of the object mounted in the slot, or 0 if no object. */
       virtual int getMountedObject(( int slot )) {}
       /*! @brief Get the mount node index of the object mounted at our given slot.
    
    @param slot mount slot index to query
    @return index of the mount node used by the object mounted in this slot. */
       virtual int getMountedObjectNode(( int slot )) {}
       /*! @brief Get the object mounted at our given node index.
    
    @param node mount node index to query
    @return ID of the first object mounted at the node, or 0 if none found. */
       virtual int getMountNodeObject(( int node )) {}
       /*! Get the object's transform.
    @return the current transform of the object
     */
       virtual string getTransform(()) {}
       /*! Get the object's world position.
    @return the current world position of the object
     */
       virtual string getPosition(()) {}
       /*! Get Euler rotation of this object.
    @return the orientation of the object in the form of rotations around the X, Y and Z axes in degrees.
     */
       virtual string getEulerRotation(()) {}
       /*! Get the direction this object is facing.
    @return a vector indicating the direction this object is facing.
    @note This is the object's y axis. */
       virtual string getForwardVector(()) {}
       /*! Get the right vector of the object.
    @return a vector indicating the right direction of this object.@note This is the object's x axis. */
       virtual string getRightVector(()) {}
       /*! Get the up vector of the object.
    @return a vector indicating the up direction of this object.@note This is the object's z axis. */
       virtual string getUpVector(()) {}
       /*! Set the object's transform (orientation and position).@param txfm object transform to set */
       virtual void setTransform(( TransformF txfm )) {}
       /*! Get the object's scale.
    @return object scale as a Point3F */
       virtual string getScale(()) {}
       /*! Set the object's scale.
    @param scale object scale to set
     */
       virtual void setScale(( Point3F scale )) {}
       /*! Get the object's world bounding box.
    @return six fields, two Point3Fs, containing the min and max points of the worldbox. */
       virtual string getWorldBox(()) {}
       /*! Get the center of the object's world bounding box.
    @return the center of the world bounding box for this object. */
       virtual string getWorldBoxCenter(()) {}
       /*! Get the object's bounding box (relative to the object's origin).
    @return six fields, two Point3Fs, containing the min and max points of the objectbox. */
       virtual string getObjectBox(()) {}
       /*! Check if this object has a global bounds set.
    If global bounds are set to be true, then the object is assumed to have an infinitely large bounding box for collision and rendering purposes.
    @return true if the object has a global bounds. */
       virtual bool isGlobalBounds(()) {}
       virtual void disableCollision(()) {}
       virtual void enableCollision(()) {}
    
       /*! @name Transform
       @{ */
       /*! */
       /*!
       Object world position.
       
        */
       MatrixPosition position;
       /*!
       Object world orientation.
       
        */
       MatrixRotation rotation;
       /*!
       Object world scale.
       
        */
       Point3F scale;
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /*!
       @brief PersistentID of object we are mounted to.
    
    Unlike the SimObjectID that is determined at run time, the PersistentID of an object is saved with the level/mission and may be used to form a link between objects.
       
        */
       pid mountPID;
       /*!
       Node we are mounted to.
       
        */
       int mountNode;
       /*!
       Position we are mounted at ( object space of our mount object ).
       
        */
       MatrixPosition mountPos;
       /*!
       Rotation we are mounted at ( object space of our mount object ).
       
        */
       MatrixRotation mountRot;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief %Forest is a global-bounds scene object provides collision and rendering for a (.forest) data file.
    
    %Forest is designed to efficiently render a large number of static meshes: trees, rocks plants, etc. These cannot be moved at game-time or play animations but do support wind effects using vertex shader transformations guided by vertex color in the asset and user placed wind emitters ( or weapon explosions ).
    
    Script level manipulation of forest data is not possible through %Forest, it is only the rendering/collision. All editing is done through the world editor.
    
    @see TSForestItemData Defines a tree type.
    @see GuiForestEditorCtrl Used by the world editor to provide manipulation of forest data.
     */
    class  Forest : public SceneObject {
      public:
       virtual bool isDirty() {}
       virtual void regenCells() {}
       virtual void clear() {}
       virtual void deleteAll() {}
       /*! Generates image representation of forest */
       virtual void getBmp(( String destBmpFile )) {}
       /*! Performs a maintenance for forest */
       virtual void createTreeReview(( Point2I basePoint )) {}
       /*! Performs a maintenance for forest */
       virtual void randomlyPlantTrees(( String treeFamiliesToPlantNames="", float spawnChance=0.001f )) {}
       /*! Forces main-thread maintenance for forest */
       virtual void maintenance(( int daysToAdd=U32_MAX )) {}
       virtual void writeStatsTo(( String outputFilename )) {}
       virtual void appendDensitiesTo(( String outputFilename, int iterationNum )) {}
       virtual void printStats(()) {}
       virtual void printSingleSurfaceTypeStats(( int surfaceType )) {}
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
       /*!
       The source forest data file.
       
        */
       filename dataFile;
    
       /*! @name Lod
       @{ */
       /*! */
       /*!
       Scalar applied to the farclip distance when Forest renders into a reflection.
       
        */
       float lodReflectScalar;
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest450 : public Forest {
      public:
    };
    
    class  TerrainBlock : public SceneObject {
      public:
       virtual int createNew() {}
    
       /*! @name Media
       @{ */
       /*! */
       /*!
       The source terrain data file.
       
        */
       filename terrainFile;
       /// @}
    
    
       /*! @name Misc
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Misc
       @{ */
       /*! */
       /*!
       Indicates the spacing between points on the XY plane on the terrain.
       
        */
       float squareSize;
       /*!
       Not yet implemented.
       
        */
       int screenError;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t450 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest449 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t449 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest448 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t448 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest447 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t447 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CmObjectsGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CmChildObjectsGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest446 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t446 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest445 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t445 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest444 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t444 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest443 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t443 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forest442 : public Forest {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  t442 : public TerrainBlock {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MissionCleanup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MissionGroup : public SimGroup {
      public:
    };
    
    class  substance : public SimObject {
      public:
       /*!
        */
       char ter2_id;
       /*!
        */
       float quantity_k;
       /*!
        */
       float maxHeightDiffBeforeFall;
       /*!
        */
       bool canBeDigged;
       /*!
        */
       bool canBeShaped;
       /*!
        */
       string terrainMaterialName;
       /*!
        */
       FootstepType footstepsType;
       /*!
        */
       float WalkSpeedMultiplier;
       /*!
        */
       float HorseSpeedMultiplier;
       /*!
        */
       float WheelSpeedMultiplier;
       /*!
        */
       float SledgeSpeedMultiplier;
       /*!
        */
       int diggedObjectID;
       /*!
        */
       int droppedObjectID;
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestWheatBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestPeaBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestPotatoBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestOnionBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestGrapeBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestFlaxBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestCarrotBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  QuestCabbageBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MarbleRoad : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SlateRoad : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Snow_loose : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Clay_loose : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  StoneRoad : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertilePotatoBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertilePotatoBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertilePotatoNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertilePotatoNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertilePotatoSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertilePotatoSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileGrapeBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileGrapeBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileGrapeNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileGrapeNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileGrapeSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileGrapeSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileFlaxBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileFlaxBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileFlaxNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileFlaxNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileFlaxSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileFlaxSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileCarrotBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileCarrotBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileCarrotNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileCarrotNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileCarrotSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileCarrotSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileOnionBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileOnionBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileOnionNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileOnionNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileOnionSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileOnionSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileCabbageBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileCabbageBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileCabbageNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileCabbageNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileCabbageSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileCabbageSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertilePeaBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertilePeaBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertilePeaNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertilePeaNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertilePeaSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertilePeaSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileWheatBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileWheatBig : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileWheatNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileWheatNormal : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NonFertileWheatSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FertileWheatSmall : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  RiverRock : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Swamp : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Snow : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Clay : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Sand : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CopperOre : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CopperVein : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SilverOre : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SilverVein : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  IronOreLoose : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  IronOre : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GoldOreloose : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GoldOre : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  slatefrag : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Slate : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  marblefrag : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Marble : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  granitefrag : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Granite : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  rockfrag : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  rockbare : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  loosensteppesoil : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  steppesoil : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  loosenforestsoil : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  forestsoil : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  LoosenSoil : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Soil : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  air : public substance {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SubstancesGroup : public SimGroup {
      public:
    };
    
    class  TCPServer : public SimGroup {
      public:
       virtual Script onError(( string this, string errorCode, string errorMessage )) {}
       virtual void closeServer() {}
       virtual void startListening() {}
       virtual int serverPort() {}
       virtual bool isActive() {}
       virtual void delete() {}
    
       /*! @name TCP Server
       @{ */
       /*! */
       /*!
       The class name to be assigned for connected clients.
       
        */
       string clientsClassName;
       /*!
       Authorization string which should be sent by client so we can check if its valid connection.
       
        */
       string authInfoIn;
       /*!
       Authorization string which should be sent by client so we can check if its valid connection.
       
        */
       string authInfoOut;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  clTCPServer : public TCPServer {
      public:
    };
    
    class  cphMyAdmin : public cphMyAdmin {
      public:
       virtual Script doQuit(( string this )) {}
       virtual Script onFinished(( string this, string success, string retCode )) {}
       virtual Script onLaunched(( string this )) {}
       virtual Script shutdownMariaDB(( string this )) {}
       virtual Script prepare(( string this, string cb )) {}
    };
    
    /*!
    @brief Abstract base class for representing a body of water.
    
    %WaterObject is abstract and may not be created. It defines functionality shared by its derived classes.
    
    %WaterObject exposes many fields for controlling it visual quality.
    
    %WaterObject surface rendering has the following general features:
    ^- Waves represented by vertex undulation and user paramaters.
    ^- Ripples represented by a normal map and user parameters.
    ^- Refraction of underwater objects.
    ^- Dynamic planar reflection or static cubemap reflection.
    ^- Paramable water fog and color shift.
    
    It will, however, look significantly different depending on the LightingManager that is active. With Basic Lighting, we do not have a prepass texture to lookup per-pixel depth and therefore cannot use our rendering techniques that depend on it.
    
    In particular, the following field groups are not used under Basic Lighting:
    ^- Underwater Fogging 
    ^- Misc 
    ^- Distortion 
    ^- And foam related fields under the %WaterObject group.
    
    %WaterObject also defines several fields for gameplay use and objects that support buoyancy.
    
     */
    class  WaterObject : public SceneObject {
      public:
    
       /*! @name WaterObject
       @{ */
       /*! */
       /*!
       Affects buoyancy of an object, thus affecting the Z velocity of a player (jumping, falling, etc.
       
        */
       float density;
       /*!
       Affects drag force applied to an object submerged in this container.
       
        */
       float viscosity;
       /*!
       Liquid type of WaterBlock, such as water, ocean, lava Currently only Water is defined and used.
       
        */
       string liquidType;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Represents a large body of water stretching to the horizon in all directions.
    
    WaterPlane's position is defined only height, the z element of position, it is infinite in xy and depth. %WaterPlane is designed to represent the ocean on an island scene and viewed from ground level; other uses may not be appropriate and a WaterBlock may be used.
    
    @see WaterObject for inherited functionality.
    
    Limitations:
    
    Because %WaterPlane cannot be projected exactly to the far-clip distance, other objects nearing this distance can have noticible artifacts as they clip through first the %WaterPlane and then the far plane.
    
    To avoid this large objects should be positioned such that they will not line up with the far-clip from vantage points the player is expected to be. In particular, your TerrainBlock should be completely contained by the far-clip distance.
    
    Viewing %WaterPlane from a high altitude with a tight far-clip distance will accentuate this limitation. %WaterPlane is primarily designed to be viewed from ground level.
    
     */
    class  WaterPlane : public WaterObject {
      public:
    
       /*! @name WaterPlane
       @{ */
       /*! */
       /*!
       Spacing between vertices in the WaterBlock mesh
       
        */
       int gridSize;
       /*!
       Duplicate of gridElementSize for backwards compatility
       
        */
       float gridElementSize;
       /// @}
    
    
       /*! @name WaterObject
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  waterInst : public WaterPlane {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  EnvironmentGroup : public SimGroup {
      public:
    };
    
    class  prcClient {
      public:
       virtual Script onRemove(( string this, string reason )) {}
       virtual Script onDrop(( string this, string reason )) {}
       virtual Script onDisconnected(( string this, string errCode, string err )) {}
       virtual Script requestPatchVersions(( string this )) {}
       virtual Script cAuth(( string this, string accoundHash )) {}
    };
    
    class  tcpServerRS : public clTCPServer {
      public:
       virtual Script onInitError(( string this, string error )) {}
    };
    
    class  prcRS {
      public:
       virtual Script onConnected(( string this )) {}
    };
    
    class  prcCli {
      public:
       virtual Script onConnected(()) {}
    };
    
    class  ammo {
      public:
       virtual Script onInventory(( string this, string obj, string amount )) {}
       virtual Script onPickup(( string this, string obj, string shape, string amount )) {}
    };
    
    class  Weapon {
      public:
       virtual Script onInventory(( string this, string obj, string amount )) {}
       virtual Script onPickup(( string this, string obj, string shape, string amount )) {}
       virtual Script onUse(( string data, string obj )) {}
    };
    
    class  CrossbowImage {
      public:
       virtual Script onFire(( string this, string obj, string slot )) {}
    };
    
    class  BowImage {
      public:
       virtual Script onFire(( string this, string obj, string slot )) {}
       virtual Script OnCharge(( string this, string obj, string slot )) {}
    };
    
    class  projectileData {
      public:
       virtual Script onExplode(( string data, string proj, string position, string mod )) {}
       virtual Script onCollision(( string data, string proj, string col, string fade, string pos, string normal )) {}
    };
    
    /*!
    @brief 
    @ingroup 
    @section Datablock_Networking Datablocks and Networking
    @section Datablock_ClientSide Client-Side Datablocks
     */
    class  SimDataBlock : public SimObject {
      public:
       /*!
       Datablock ID. Do not modify, for internal use.
       
        */
       int id;
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Scriptable, demo-able datablock.  Used by GameBase objects.
    
    @see GameBase
    @ingroup gameObjects
     */
    class  GameBaseData : public SimDataBlock {
      public:
          /*! @brief Called when the object is added to the scene.
    
    @param obj the GameBase object
    
    @tsexample
    datablock GameBaseData(MyObjectData)
    {
       category = "Misc";
    };
    
    function MyObjectData::onAdd( %this, %obj )
    {
       echo( "Added " @ %obj.getName() @ " to the scene." );
    }
    
    function MyObjectData::onNewDataBlock( %this, %obj )
    {
       echo( "Assign " @ %this.getName() @ " datablock to " %obj.getName() );
    }
    
    function MyObjectData::onRemove( %this, %obj )
    {
       echo( "Removed " @ %obj.getName() @ " to the scene." );
    }
    
    function MyObjectData::onMount( %this, %obj, %mountObj, %node )
    {
       echo( %obj.getName() @ " mounted to " @ %mountObj.getName() );
    }
    
    function MyObjectData::onUnmount( %this, %obj, %mountObj, %node )
    {
       echo( %obj.getName() @ " unmounted from " @ %mountObj.getName() );
    }
    
    @endtsexample
     */
          void onAdd( GameBase obj );
    
          /*! @brief Called when the object has a new datablock assigned.
    
    @param obj the GameBase object
    
    @see onAdd for an example
     */
          void onNewDataBlock( GameBase obj );
    
          /*! @brief Called when the object is removed from the scene.
    
    @param obj the GameBase object
    
    @see onAdd for an example
     */
          void onRemove( GameBase obj );
    
          /*! @brief Called when the object is mounted to another object in the scene.
    
    @param obj the GameBase object being mounted
    @param mountObj the object we are mounted to
    @param node the mountObj node we are mounted to
    
    @see onAdd for an example
     */
          void onMount( GameBase obj, SceneObject mountObj, int node );
    
          /*! @brief Called when the object is unmounted from another object in the scene.
    
    @param obj the GameBase object being unmounted
    @param mountObj the object we are unmounted from
    @param node the mountObj node we are unmounted from
    
    @see onAdd for an example
     */
          void onUnmount( GameBase obj, SceneObject mountObj, int node );
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /*!
       The group that this datablock will show up in under the "Scripted" tab in the World Editor Library.
       
        */
       caseString category;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  FormationDrawData : public GameBaseData {
      public:
       /*!
       
       
        */
       int formationType;
       /*!
       
       
        */
       Point3F size;
       /*!
       
       
        */
       Point3F normalScale;
       /*!
       
       
        */
       Point3F mountedScale;
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CircleFormationDrawData : public FormationDrawData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WedgeFormationDrawData : public FormationDrawData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WallFormationDrawData : public FormationDrawData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NullFormationDrawData : public FormationDrawData {
      public:
    };
    
    /*!
    @brief Defines properties for a ShapeBase object.
    
    @see ShapeBase
    @ingroup gameObjects
     */
    class  ShapeBaseData : public GameBaseData {
      public:
       virtual Script damage(()) {}
       virtual Script onInventory(()) {}
       virtual Script onPickup(( string this, string obj, string user, string amount )) {}
       virtual Script onThrow(( string this, string user, string amount )) {}
       virtual Script onUse(( string this, string user )) {}
          /*! @brief Called when the object damage state changes to Enabled.
    
    @param obj The ShapeBase object
    @param lastState The previous damage state
     */
          void onEnabled( ShapeBase obj, string lastState );
    
          /*! @brief Called when the object damage state changes to Disabled.
    
    @param obj The ShapeBase object
    @param lastState The previous damage state
     */
          void onDisabled( ShapeBase obj, string lastState );
    
          /*! @brief Called when the object damage state changes to Destroyed.
    
    @param obj The ShapeBase object
    @param lastState The previous damage state
     */
          void onDestroyed( ShapeBase obj, string lastState );
    
          /*! @brief Called when we collide with another object beyond some impact speed.
    
    The Player class makes use of this callback when a collision speed is more than PlayerData::minImpactSpeed.
    @param obj The ShapeBase object
    @param collObj The object we collided with
    @param vec Collision impact vector
    @param len Length of the impact vector
     */
          void onImpact( ShapeBase obj, SceneObject collObj, VectorF vec, float len );
    
          /*! @brief Called when we collide with another object.
    
    @param obj The ShapeBase object
    @param collObj The object we collided with
    @param vec Collision impact vector
    @param len Length of the impact vector
     */
          void onCollision( ShapeBase obj, SceneObject collObj, VectorF vec, float len );
    
          /*! @brief Called when the object is damaged.
    
    @param obj The ShapeBase object
    @param obj The ShapeBase object
    @param delta The amount of damage received. */
          void onDamage( ShapeBase obj, float delta );
    
          /*! @brief Called when a thread playing a non-cyclic sequence reaches the end of the sequence.
    
    @param obj The ShapeBase object
    @param slot Thread slot that finished playing
     */
          void onEndSequence( ShapeBase obj, int slot );
    
          /*! @brief Called when the object is forced to uncloak.
    
    @param obj The ShapeBase object
    @param reason String describing why the object was uncloaked
     */
          void onForceUncloak( ShapeBase obj, string reason );
    
       /*! @brief Check if there is the space at the given transform is free to spawn into.
    
    The shape's bounding box volume is used to check for collisions at the given world transform.  Only interior and static objects are checked for collision.
    @param txfm Deploy transform to check
    @return True if the space is free, false if there is already something in the way.
    @note This is a server side only check, and is not actually limited to spawning.
     */
       virtual bool checkDeployPos(( TransformF txfm )) {}
       /*! @brief Helper method to get a transform from a position and vector (suitable for use with setTransform).
    
    @param pos Desired transform position
    @param normal Vector of desired direction
    @return The deploy transform
     */
       virtual string getDeployTransform(( Point3F pos, Point3F normal )) {}
    
       /*! @name Render
       @{ */
       /*! */
       /*!
       The DTS or DAE model to use for this object.
       
        */
       filename shapeFile;
       /*!
       
       
        */
       Point3F imageScale;
       /*!
       
       
        */
       Point3F horseScale;
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /*!
       Shape mass.
    Used in simulation of moving objects.
    
       
        */
       float mass;
       /*!
       Drag factor.
    Reduces velocity of moving objects.
       
        */
       float drag;
       /*!
       Shape density.
    Used when computing buoyancy when in water.
    
       
        */
       float density;
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /*!
       Maximum damage level for this object.
       
        */
       float maxDamage;
       /*!
       Damage level above which the object is destroyed.
    When the damage level increases above this value, the object damage state is set to "Destroyed".
       
        */
       float destroyedLevel;
       /*!
       Rate at which damage is repaired in damage units/tick.
    This value is subtracted from the damage level until it reaches 0.
       
        */
       float repairRate;
       /*!
       Invincible flag; when invincible, the object cannot be damaged or repaired.
       
        */
       bool isInvincible;
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /*!
       The maximum distance from the camera to the object.
    Used when computing a custom camera transform for this object.
    
    @see observeThroughObject
       
        */
       float cameraMaxDist;
       /*!
       The minimum distance from the camera to the object.
    Used when computing a custom camera transform for this object.
    
    @see observeThroughObject
       
        */
       float cameraMinDist;
       /*!
       Z offset to apply to the cameras position when hit something by camera itself
       
        */
       float cameraZDropOffset;
       /*!
       The maximum distance from the camera to the object.
    Used when computing a custom camera transform for this object.
    
    @see observeThroughObject
       
        */
       float cameraMaxDistWarStance;
       /*!
       The minimum distance from the camera to the object.
    Used when computing a custom camera transform for this object.
    
    @see observeThroughObject
       
        */
       float cameraMinDistWarStance;
       /*!
       The default camera vertical FOV in degrees.
       
        */
       float cameraDefaultFov;
       /*!
       The minimum camera vertical FOV allowed in degrees.
       
        */
       float cameraMinFov;
       /*!
       The maximum camera vertical FOV allowed in degrees.
       
        */
       float cameraMaxFov;
       /*!
       Default camera vertical Fov for Volley ability in degrees.
       
        */
       float cameraVolleyFov;
       /*!
       
       
        */
       float warstanceCamAngTheta;
       /*!
       
       
        */
       float peacestanceCamAngTheta;
       /*!
       Observe this object through its camera transform and default fov.
    If true, when this object is the camera it can provide a custom camera transform and FOV (instead of the default eye transform).
       
        */
       bool observeThroughObject;
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief The most basic ShapeBaseData derrived shape datablock available in Torque 3D.
    
    When it comes to placing 3D objects in the scene, you effectively have two options:
    
    1. TSStatic objects
    
    2. ShapeBase derived objects
    
    Since ShapeBase and ShapeBaseData are not meant to be instantiated in script, you will use one of its child classes instead. Several game related objects are derived from ShapeBase: Player, Vehicle, Item, and so on.
    
    When you need a 3D object with datablock capabilities, you will use an object derived from ShapeBase. When you need an object with extremely low overhead, and with no other purpose than to be a 3D object in the scene, you will use TSStatic.
    
    The most basic child of ShapeBase is StaticShape. It does not introduce any of the additional functionality you see in Player, Item, Vehicle or the other game play heavy classes. At its core, it is comparable to a TSStatic, but with a datbalock.  Having a datablock provides a location for common variables as well as having access to various ShapeBaseData, GameBaseData and SimDataBlock callbacks.
    
    @tsexample
    // Create a StaticShape using a datablock
    datablock StaticShapeData(BasicShapeData)
    {
    ^shapeFile = "art/shapes/items/kit/healthkit.dts";
    ^testVar = "Simple string, not a stock variable";
    };
    
    new StaticShape()
    {
    ^dataBlock = "BasicShapeData";
    ^position = "0.0 0.0 0.0";
    ^rotation = "1 0 0 0";
    ^scale = "1 1 1";
    };
    @endtsexample
    
    @see StaticShape
    @see ShapeBaseData
    @see TSStatic
    
    @ingroup gameObjects
     */
    class  StaticShapeData : public ShapeBaseData {
      public:
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  AttachedShapeData : public StaticShapeData {
      public:
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
       /*!
       
       
        */
       int objectTypeId;
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedHorseCartNoTent : public AttachedShapeData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedHorseCart : public AttachedShapeData {
      public:
    };
    
    /*!
    @brief Represents geometry to be mounted to a ShapeBase object.
    
    @ingroup gameObjects
     */
    class  ShapeBaseImageData : public GameBaseData {
      public:
       virtual void onRangedImagePrefire() {}
       virtual void onRangedImageFire() {}
       virtual void onRangedImageFireCancel() {}
       virtual void onRangedImageReady() {}
       virtual void onRangedImageDraw() {}
       virtual void onRangedImageInactive() {}
       virtual void onThrowingWeaponFire() {}
       virtual void onThrowingWeaponPostfire() {}
       virtual void onRangedImageReloaded() {}
       virtual void onImagePrefire() {}
       virtual void onImageFire() {}
       virtual void onImageFireCancel() {}
       virtual void onImageReady() {}
       virtual void onImageInactive() {}
          /*! @brief Called when the Image is first mounted to the object.
    
    @param obj object that this Image has been mounted to
    @param slot Image mount slot on the object
    @param dt time remaining in this Image update
     */
          void onMount( ShapeBase obj, int slot, float dt );
    
          /*! @brief Called when the Image is unmounted from the object.
    
    @param obj object that this Image has been unmounted from
    @param slot Image mount slot on the object
    @param dt time remaining in this Image update
     */
          void onUnmount( ShapeBase obj, int slot, float dt );
    
       /*!
       @brief The DTS or DAE model to use for this Image.
    
    
       
        */
       filename shapeFile;
       /*!
       @brief Mount node # to mount this Image to.
    
    This should correspond to a mount# node on the ShapeBase derived object we are mounting to.
       
        */
       int mountPoint;
       /*!
       @brief "X Y Z" translation offset from this Image's <i>mountPoint</i> node to attach to.
    
    Defaults to "0 0 0". ie. attach this Image's <i>mountPoint</i> node to the ShapeBase model's mount# node without any offset.
    @see rotation
       
        */
       MatrixPosition offset;
       /*!
       @brief "X Y Z ANGLE" rotation offset from this Image's <i>mountPoint</i> node to attach to.
    
    Defaults to "0 0 0". ie. attach this Image's <i>mountPoint</i> node to the ShapeBase model's mount# node without any additional rotation.
    @see offset
       
        */
       MatrixRotation rotation;
       /*!
       @brief "X Y Z" translation offset from the ShapeBase model's eye node.
    
    When in first person view, this is the offset from the eye node to place the gun.  This gives the gun a fixed point in space, typical of a lot of FPS games.
    @see eyeRotation
       
        */
       MatrixPosition eyeOffset;
       /*!
       @brief "X Y Z ANGLE" rotation offset from the ShapeBase model's eye node.
    
    When in first person view, this is the rotation from the eye node to place the gun.
    @see eyeOffset
       
        */
       MatrixRotation eyeRotation;
       /*!
       @brief Flag to adjust the aiming vector to the eye's LOS point.
    
    @see ShapeBase::getMuzzleVector()
       
        */
       bool correctMuzzleVector;
       /*!
       @brief This flag must be set for the adjusted LOS muzzle vector to be computed.
    
    @see ShapeBase::getMuzzleVector()
       
        */
       bool firstPerson;
       /*!
       @brief Mass of this Image.
    
    This is added to the total mass of the ShapeBase object.
       
        */
       float mass;
       /*!
       Name of this state.
       
        */
       caseString stateName;
       /*!
       Name of the state to transition to when the loaded state of the Image changes to 'Loaded'.
       
        */
       string stateTransitionOnLoaded;
       /*!
       Name of the state to transition to when the loaded state of the Image changes to 'Empty'.
       
        */
       string stateTransitionOnNotLoaded;
       /*!
       Name of the state to transition to when the ammo state of the Image changes to true.
       
        */
       string stateTransitionOnAmmo;
       /*!
       Name of the state to transition to when the ammo state of the Image changes to false.
       
        */
       string stateTransitionOnNoAmmo;
       /*!
       Name of the state to transition to when the Image gains a target.
       
        */
       string stateTransitionOnTarget;
       /*!
       Name of the state to transition to when the Image loses a target.
       
        */
       string stateTransitionOnNoTarget;
       /*!
       Name of the state to transition to when the Image enters the water.
       
        */
       string stateTransitionOnWet;
       /*!
       Name of the state to transition to when the Image exits the water.
       
        */
       string stateTransitionOnNotWet;
       /*!
       Name of the state to transition to when the trigger state of the Image changes to true (fire button down).
       
        */
       string stateTransitionOnTriggerUp;
       /*!
       Name of the state to transition to when the trigger state of the Image changes to false (fire button released).
       
        */
       string stateTransitionOnTriggerDown;
       /*!
       Name of the state to transition to when the alt trigger state of the Image changes to true (alt fire button down).
       
        */
       string stateTransitionOnAltTriggerUp;
       /*!
       Name of the state to transition to when the alt trigger state of the Image changes to false (alt fire button up).
       
        */
       string stateTransitionOnAltTriggerDown;
       /*!
       Name of the state to transition to when we have been in this state for stateTimeoutValue seconds.
       
        */
       string stateTransitionOnTimeout;
       /*!
       Time in seconds to wait before transitioning to stateTransitionOnTimeout.
       
        */
       float stateTimeoutValue;
       /*!
       If false, this state ignores stateTimeoutValue and transitions immediately if other transition conditions are met.
       
        */
       bool stateWaitForTimeout;
       /*!
       The first state with this set to true is the state entered by the client when it receives the 'fire' event.
       
        */
       bool stateFire;
       /*!
       If true, this state will be checking prerequisites for transition
       
        */
       bool stateCheckTransition;
       /*!
       @brief If false, other Images will temporarily be blocked from mounting while the state machine is executing the tasks in this state.
    
    For instance, if we have a rocket launcher, the player shouldn't be able to switch out <i>while</i> firing. So, you'd set stateAllowImageChange to false in firing states, and true the rest of the time.
       
        */
       bool stateAllowImageChange;
       /*!
       @brief Direction of the animation to play in this state.
    
    True is forward, false is backward.
       
        */
       bool stateDirection;
       /*!
       @brief Don't play animation, stop it.
       
        */
       bool stateFreezeAnimation;
       /*!
       @brief Set the loaded state of the Image.
    
    <ul><li>IgnoreLoaded: Don't change Image loaded state.</li><li>Loaded: Set Image loaded state to true.</li><li>NotLoaded: Set Image loaded state to false.</li></ul>
    @see ShapeBaseImageLoadedState
       
        */
       ShapeBaseImageLoadedState stateLoadedFlag;
       /*!
       @brief Controls how fast the 'spin' animation sequence will be played in this state.
    
    <ul><li>Ignore: No change to the spin sequence.</li><li>Stop: Stops the spin sequence at its current position.</li><li>SpinUp: Increase spin sequence timeScale from 0 (on state entry) to 1 (after stateTimeoutValue seconds).</li><li>SpinDown: Decrease spin sequence timeScale from 1 (on state entry) to 0 (after stateTimeoutValue seconds).</li><li>FullSpeed: Resume the spin sequence playback at its current position with timeScale=1.</li></ul>
    @see ShapeBaseImageSpinState
       
        */
       ShapeBaseImageSpinState stateSpinThread;
       /*!
       Name of the sequence to play on entry to this state.
       
        */
       string stateSequence;
       /*!
       @brief If true, a random frame from the muzzle flash sequence will be displayed each frame.
    
    The name of the muzzle flash sequence is the same as stateSequence, with "_vis" at the end.
       
        */
       bool stateSequenceRandomFlash;
       /*!
       If true, the timeScale of the stateSequence animation will be adjusted such that the sequence plays for stateTimeoutValue seconds. 
       
        */
       bool stateScaleAnimation;
       /*!
       @brief Method to execute on entering this state.
    
    Scoped to this image class name, then ShapeBaseImageData. The script callback function takes the same arguments as the onMount callback.
    @see onMount() for the same arguments as this callback.
       
        */
       caseString stateScript;
       /*!
       @brief If set to true, and both ready and loaded transitions are true, the ready transition will be taken instead of the loaded transition.
    
    A state is 'ready' if pressing the fire trigger in that state would transition to the fire state.
       
        */
       bool stateIgnoreLoadedForReady;
       /*!
       @brief Define which sub-state of fire state we describe here.
       
        */
       ShapeBaseImageFireSubState stateFireSubState;
       /*!
       @brief If true, allow multiple timeout transitions to occur within a single tick (useful if states have a very small timeout).
    
    
       
        */
       bool useRemainderDT;
       /*!
       
       
        */
       int Object_typeID;
       /*!
       for Transportation mount images.
       
        */
       float wheel;
       /*!
        */
       float BasePrefireAnimTime;
       /*!
        */
       float BaseFireAnimTime;
       /*!
        */
       float BaseRecoilAnimTime;
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MountedTrader_cart : public ShapeBaseImageData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MountedCart : public ShapeBaseImageData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MountedWheelbarrow : public ShapeBaseImageData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MountedPlough : public ShapeBaseImageData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  TreeLogData : public StaticShapeData {
      public:
    };
    
    class  DynamicShapeData : public ShapeBaseData {
      public:
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Defines properties for a Player object.
    
    @see Player
    @ingroup gameObjects
     */
    class  PlayerData : public DynamicShapeData {
      public:
          /*! @brief Called when the player starts swimming.
    
    @param obj The Player object
     */
          void onStartSwim( Player obj );
    
          /*! @brief Called when the player stops swimming.
    
    @param obj The Player object
     */
          void onStopSwim( Player obj );
    
          /*! @brief Called when attempting to dismount the player from a vehicle.
    
    It is up to the doDismount() method to actually perform the dismount.  Often there are some conditions that prevent this, such as the vehicle moving too fast.
    @param obj The Player object
     */
          void doDismount( Player obj );
    
          /*! @brief Called when the player enters a liquid.
    
    @param obj The Player object
    @param coverage Percentage of the player's bounding box covered by the liquid
    @param type The type of liquid the player has entered
     */
          void onEnterLiquid( Player obj, float coverage, string type );
    
          /*! @brief Called when the player leaves a liquid.
    
    @param obj The Player object
    @param type The type of liquid the player has left
     */
          void onLeaveLiquid( Player obj, string type );
    
          /*! @brief Called on the server when a scripted animation completes.
    
    @param obj The Player object
    @see Player::setActionThread() for setting a scripted animation and its 'hold' parameter to determine if this callback is used.
     */
          void animationDone( Player obj );
    
          /*! @brief Called when the player enters the mission area.
    
    @param obj The Player object
    @see MissionArea
     */
          void onEnterMissionArea( Player obj );
    
          /*! @brief Called when the player leaves the mission area.
    @param obj The Player object
    @see MissionArea
     */
          void onLeaveMissionArea( Player obj );
    
       /*!
       @brief Maximum time scale for action animations.
    
    If an action animation has a defined ground frame, it is automatically scaled to match the player's ground velocity.  This field limits the maximum time scale used even if the player's velocity exceeds it.
       
        */
       float maxTimeScale;
    
       /*! @name Camera
       @{ */
       /*! */
       /*!
       @brief Lowest angle (in radians) the player can look.
    
    @note An angle of zero is straight ahead, with positive up and negative down.
       
        */
       float minLookAngle;
       /*!
       @brief Highest angle (in radians) the player can look.
    
    @note An angle of zero is straight ahead, with positive up and negative down.
       
        */
       float maxLookAngle;
       /*!
       @brief Lowest angle (in radians) the player can look.
    
    @note An angle of zero is straight ahead, with positive up and negative down.
       
        */
       float minLookAngleVolley;
       /*!
       @brief Highest angle (in radians) the player can look.
    
    @note An angle of zero is straight ahead, with positive up and negative down.
       
        */
       float maxLookAngleVolley;
       /*!
       @brief Defines the maximum left and right angles (in radians) the player can look in freelook mode.
    
    
       
        */
       float maxFreelookAngle;
       /*!
       
       
        */
       float equipDrownCoeff;
       /*!
       
       
        */
       float waterStaminaRate;
       /*!
       
       
        */
       int O2consumption;
       /*!
       
       
        */
       int O2refresh;
       /*!
       
       
        */
       int HPdrowning;
       /*!
       Player's visible distance (scope) in building mode.
       
        */
       float buildScopeSize;
       /// @}
    
    
       /*! @name Movement
       @{ */
       /*! */
       /*!
       @brief Maximum height the player can step up.
    
    The player will automatically step onto changes in ground height less than maxStepHeight.  The player will collide with ground height changes greater than this.
       
        */
       float maxStepHeight;
       /*!
       @brief Force used to accelerate the player when running.
    
    
       
        */
       float runForce;
       /*!
       @brief Maximum forward speed when walking.
       
        */
       float maxForwardSpeed;
       /*!
       @brief Maximum backward speed when walking.
       
        */
       float maxBackwardSpeed;
       /*!
       @brief Maximum sideways speed when walking.
       
        */
       float maxSideSpeed;
       /*!
       @brief Maximum forward speed when running.
       
        */
       float maxRuningSpeed;
       /*!
       
       
        */
       float horseCameraOffsetZ;
       /*!
       
       
        */
       float rotSpeedFirstPersonStay;
       /*!
       
       
        */
       float rotSpeedFirstPersonMove;
       /*!
       
       
        */
       float rotSpeedThirdPersonStay;
       /*!
       
       
        */
       float rotSpeedThirdPersonMove;
       /*!
       
       
        */
       float rotSpeedRotationAnim;
       /*!
       
       
        */
       float headVThreadMaxSpeedStay;
       /*!
       
       
        */
       float mountedRotationAnimationMaxSpeedStay;
       /*!
       
       
        */
       float headVThreadMaxSpeedMove;
       /*!
       
       
        */
       float mountedRotationAnimationMaxSpeedMove;
       /*!
       @brief Maximum forward speed when walking.
       
        */
       float maxWarForwardSpeed;
       /*!
       @brief Maximum backward speed when walking.
       
        */
       float maxWarBackwardSpeed;
       /*!
       @brief Maximum sideways speed when walking.
       
        */
       float maxWarSideSpeed;
       /*!
       @brief Maximum forward speed when running.
       
        */
       float maxWarRuningSpeed;
       /*!
       @brief Maximum angle from vertical (in degrees) the player can run up.
    
    
       
        */
       float runSurfaceAngle;
       /*!
       @brief Minimum impact speed to apply falling damage.
    
    This field also sets the minimum speed for the onImpact callback to be invoked.
    @see ShapeBaseData::onImpact()
    
       
        */
       float minImpactSpeed;
       /*!
       
       
        */
       float impactGroundSpeed;
       /*!
       
       
        */
       float speedDamageScale;
       /*!
       @brief Maximum horizontal speed.
    
    @note This limit is only enforced if the player's horizontal speed exceeds horizResistSpeed.
    @see horizResistSpeed
    @see horizResistFactor
    
       
        */
       float horizMaxSpeed;
       /*!
       @brief Horizontal speed at which resistence will take place.
    
    @see horizMaxSpeed
    @see horizResistFactor
    
       
        */
       float horizResistSpeed;
       /*!
       @brief Factor of resistence once horizResistSpeed has been reached.
    
    @see horizMaxSpeed
    @see horizResistSpeed
    
       
        */
       float horizResistFactor;
       /*!
       @brief Maximum upwards speed.
    
    @note This limit is only enforced if the player's upward speed exceeds upResistSpeed.
    @see upResistSpeed
    @see upResistFactor
    
       
        */
       float upMaxSpeed;
       /*!
       @brief Upwards speed at which resistence will take place.
    
    @see upMaxSpeed
    @see upResistFactor
    
       
        */
       float upResistSpeed;
       /*!
       @brief Factor of resistence once upResistSpeed has been reached.
    
    @see upMaxSpeed
    @see upResistSpeed
    
       
        */
       float upResistFactor;
       /// @}
    
    
       /*! @name Movement: Jumping
       @{ */
       /*! */
       /*!
       @brief Force used to accelerate the player when a jump is initiated.
    
    
       
        */
       float jumpForce;
       /*!
       @brief Force used to accelerate the player when a jump on shield is initiated.
    
    
       
        */
       float pounceForce;
       /*!
       @brief Minimum speed needed to jump.
    
    If the player's own z velocity is greater than this, then it is used to scale the jump speed, up to maxJumpSpeed.
    @see maxJumpSpeed
    
       
        */
       float minJumpSpeed;
       /*!
       @brief Maximum vertical speed before the player can no longer jump.
    
    
       
        */
       float maxJumpSpeed;
       /*!
       @brief Angle from vertical (in degrees) where the player can jump.
    
    
       
        */
       float jumpSurfaceAngle;
       /*!
       @brief Delay time in number of ticks ticks between jumps.
    
    
       
        */
       int jumpDelay;
       /*!
       @brief Amount of movement control the player has when in the air.
    
    This is applied as a multiplier to the player's x and y motion.
    
       
        */
       float airControl;
       /*!
       @brief Controls the direction of the jump impulse.
    When false, jumps are always in the vertical (+Z) direction. When true jumps are in the direction of the ground normal so long as the player is not directly facing the surface.  If the player is directly facing the surface, then they will jump straight up.
    
       
        */
       bool jumpTowardsNormal;
       /// @}
    
    
       /*! @name Movement: Swimming
       @{ */
       /*! */
       /*!
       @brief Force used to accelerate the player when swimming.
    
    
       
        */
       float swimForce;
       /*!
       @brief Maximum forward speed when underwater.
    
    
       
        */
       float maxUnderwaterForwardSpeed;
       /*!
       @brief Maximum backward speed when underwater.
    
    
       
        */
       float maxUnderwaterBackwardSpeed;
       /*!
       @brief Maximum sideways speed when underwater.
    
    
       
        */
       float maxUnderwaterSideSpeed;
       /*!
       
       
        */
       float skillSwimmingDistance;
       /// @}
    
    
       /*! @name Falling
       @{ */
       /*! */
       /*!
       @brief Number of ticks for the player to recover from falling.
    
    
       
        */
       int recoverDelay;
       /*!
       @brief Scale factor applied to runForce while in the recover state.
    
    This can be used to temporarily slow the player's movement after a fall, or prevent the player from moving at all if set to zero.
    
       
        */
       float recoverRunForceScale;
       /*!
       @brief Number of ticks to rise player up.
    
    
       
        */
       int knockedDownTicks;
       /*!
       lookupdown_animation_angle_min (radians)
       
        */
       float lookupdown_animation_angle_min;
       /*!
       lookupdown_animation_angle_max (radians)
       
        */
       float lookupdown_animation_angle_max;
       /// @}
    
    
       /*! @name Collision
       @{ */
       /*! */
       /*!
       @brief Size of the bounding box used by the player for collision.
    
    Dimensions are given as "width depth height".
       
        */
       Point3F boundingBox;
       /*!
       @brief Collision bounding box used when the player is swimming.
    
    @see boundingBox
       
        */
       Point3F swimBoundingBox;
       /*!
       Standard collision (raycasting only, no physics) bounding box.
    @see boundingBox
       
        */
       Point3F standardRaycastBox;
       /*!
       Collision (raycasting only, no physics) bounding box used when the player is mounted.
    @see boundingBox
       
        */
       Point3F mountingRaycastBox;
       /// @}
    
    
       /*! @name Interaction: Ground Impact
       @{ */
       /*! */
       /*!
       @brief Minimum falling impact speed to apply damage and initiate the camera shaking effect.
    
    
       
        */
       float groundImpactMinSpeed;
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /*!
       @brief Specifies the type of physics used by the player.
    
    This depends on the physics module used.  An example is 'Capsule'.
    @note Not current used.
    
       
        */
       string physicsPlayerType;
       /// @}
    
       /*!
       
       
        */
       float sprintTime;
       /*!
       
       
        */
       float sprintCooldown;
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  NPCData : public PlayerData {
      public:
       /*!
       @brief 
    
    
       
        */
       float walkSpeed;
       /*!
       @brief 
    
    
       
        */
       float runSpeed;
       /*!
       @brief 
    
    
       
        */
       float maxHP;
       /*!
       @brief 
    
    
       
        */
       float hpRegenRate;
       /*!
       @brief 
    
    
       
        */
       string behavior;
    
       /*! @name Camera
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Movement
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Movement: Jumping
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Movement: Swimming
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Falling
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Collision
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Interaction: Ground Impact
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NPC_slave_Overseer : public NPCData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NPC_slave_E : public NPCData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NPC_slave_D : public NPCData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NPC_slave_C : public NPCData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NPC_slave_B : public NPCData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NPC_slave_A : public NPCData {
      public:
    };
    
    class  AnimalData : public NPCData {
      public:
       /*!
       @brief 
    
    
       
        */
       int rawCorpseObjectTypeID;
       /*!
       @brief 
    
    
       
        */
       int skinnedCorpseObjectTypeID;
       /*!
       @brief 
    
    
       
        */
       bool isPredator;
       /*!
       @brief 
    
    
       
        */
       float body;
       /*!
       @brief 
    
    
       
        */
       string WeaponData;
       /*!
       @brief 
    
    
       
        */
       float weaponWeight;
       /*!
       @brief 
    
    
       
        */
       float powerAttackProbability;
       /*!
       @brief 
    
    
       
        */
       float powerHitStartingDistance;
       /*!
       @brief 
    
    
       
        */
       float powerHitDamagingDistance;
       /*!
       @brief 
    
    
       
        */
       float powerHitDamagingSector;
       /*!
       @brief 
    
    
       
        */
       float powerHitMinSpeed;
       /*!
       @brief 
    
    
       
        */
       float powerHitMaxSpeed;
       /*!
       @brief 
    
    
       
        */
       float fastHitStartingDistance;
       /*!
       @brief 
    
    
       
        */
       float fastHitDamagingDistance;
       /*!
       @brief 
    
    
       
        */
       float fastHitDamagingSector;
       /*!
       @brief 
    
    
       
        */
       float fastHitMinSpeed;
       /*!
       @brief 
    
    
       
        */
       float fastHitMaxSpeed;
       /*!
       @brief 
    
    
       
        */
       float walkAnimationSpeed;
       /*!
       @brief 
    
    
       
        */
       float runAnimationSpeed;
       /*!
       @brief 
    
    
       
        */
       string animalType;
       /*!
       @brief 
    
    
       
        */
       int animalTypeId;
       /*!
       
       
        */
       float footprintTextureLinearSize;
       /*!
       
       
        */
       float footprintGap;
       /*!
       
       
        */
       float footprintTrackWidth;
    
       /*! @name Camera
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Movement
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Movement: Jumping
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Movement: Swimming
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Falling
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Collision
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Interaction: Ground Impact
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  AurochsCowData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MuttonData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MooseData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WolfData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HindData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HareData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GrouseData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WildHorseData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SowData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BoarData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BearData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  AurochsBullData : public AnimalData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DeerMaleData : public AnimalData {
      public:
    };
    
    /*!
    @brief Base properties shared by all Vehicles (FlyingVehicle, HoverVehicle, WheeledVehicle.
    
    This datablock defines properties shared by all Vehicle types, but should not be instantiated directly. Instead, set the desired properties in the FlyingVehicleData, HoverVehicleData or WheeledVehicleData datablock.
    @ingroup Vehicles
     */
    class  VehicleData : public ShapeBaseData {
      public:
       virtual Script switchSeats(( string this, string vehicle, string player )) {}
       virtual Script findEmptySeat(( string this, string vehicle, string player )) {}
       virtual Script setMountVehicle(( string this, string vehicle, string player )) {}
       virtual Script mountPlayer(( string this, string vehicle, string player )) {}
       virtual Script isMountable(( string this, string obj, string val )) {}
       virtual Script onRemove(( string this, string obj )) {}
       virtual Script onAdd(( string this, string obj )) {}
          /*! Called when the vehicle enters liquid.
    @param obj the Vehicle object
    @param coverage percentage of the vehicle's bounding box covered by the liquid
    @param type type of liquid the vehicle has entered
     */
          void onEnterLiquid( Vehicle obj, float coverage, string type );
    
          /*! Called when the vehicle leaves liquid.
    @param obj the Vehicle object
    @param type type of liquid the vehicle has left
     */
          void onLeaveLiquid( Vehicle obj, string type );
    
       /*!
       Defines the vehicle's center of mass (offset from the origin of the model).
       
        */
       Point3F massCenter;
       /*!
       Define the box used to estimate the vehicle's moment of inertia.
    Currently only used by WheeledVehicle, other vehicle types use a unit sphere to compute inertia.
       
        */
       Point3F massBox;
       /*!
       Collision 'bounciness'.
    Normally in the range 0 (not bouncy at all) to 1 (100% bounciness).
       
        */
       float bodyRestitution;
       /*!
       Collision friction coefficient.
    How well this object will slide against objects it collides with.
       
        */
       float bodyFriction;
       /*!
       Minimum collision speed for the onImpact callback to be invoked.
       
        */
       float minImpactSpeed;
       /*!
       Minimum collision speed for the softImpactSound to be played.
       
        */
       float softImpactSpeed;
       /*!
       Minimum collision speed for the hardImpactSound to be played.
       
        */
       float hardImpactSpeed;
       /*!
       Maximum yaw (horizontal) and pitch (vertical) steering angle in radians.
       
        */
       float maxSteeringAngle;
       /*!
       Maximum height to step up.
       
        */
       float maxStepHeight;
       /*!
        */
       float jumpSurfaceAngle;
       /*!
        */
       float runSurfaceAngle;
       /*!
       Number of integration steps per tick.
    Increase this to improve simulation stability (also increases simulation processing time).
       
        */
       int integration;
       /*!
       Minimum distance between objects for them to be considered as colliding.
       
        */
       float collisionTol;
       /*!
       Maximum relative velocity between objects for collisions to be resolved as contacts.
    Velocities greater than this are handled as collisions.
       
        */
       float contactTol;
       /*!
       
       
        */
       Point3F physicsBoxSize;
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  HorseData : public VehicleData {
      public:
       virtual Script onAdd(( string this, string obj )) {}
       virtual Script create(( string data )) {}
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Basic horse
       @{ */
       /*! */
       /*!
        */
       int objectTypeId;
       /*!
        */
       float pickup;
       /*!
        */
       Point3F boundingBox;
       /*!
        */
       float velocityNeededRelaxForce;
       /*!
        */
       int jumpDelay;
       /*!
        */
       float jumpEnergyDrain;
       /*!
        */
       float minJumpSpeed;
       /*!
        */
       float maxJumpSpeed;
       /*!
        */
       float jumpForce;
       /*!
        */
       float runBackForce;
       /// @}
    
    
       /*! @name LiF Additions
       @{ */
       /*! */
       /*!
        */
       float minSpeed;
       /*!
        */
       float maxSpeed;
       /*!
        */
       float maxAcceleration;
       /*!
        */
       float angleSpeed;
       /*!
        */
       float walk2trot;
       /*!
        */
       float trot2walk;
       /*!
        */
       float trot2gallop;
       /*!
        */
       float gallop2trot;
       /*!
        */
       float DamageMltp;
       /*!
        */
       float minFallImpactSpeed;
       /*!
        */
       float carryWeight;
       /*!
        */
       float HP;
       /*!
        */
       float HPRegen;
       /*!
        */
       float stamina;
       /*!
        */
       float staminaRegen;
       /*!
        */
       float collisionStopSpeed;
       /*!
        */
       float collisionHindLegsSpeed;
       /*!
       
       
        */
       float skillTravelDistance;
       /*!
       
       
        */
       int skillIdTraveller;
       /*!
       
       
        */
       char speedLevelCount;
       /*!
       
       
        */
       float speedLevels;
       /// @}
    
       /*!
        */
       float maxSideSpeed;
       /*!
        */
       float maxDownSpeed;
       /*!
        */
       float maxUnderwaterForwardSpeed;
       /*!
        */
       float maxUnderwaterBackwardSpeed;
       /*!
        */
       float maxUnderwaterSideSpeed;
       /*!
        */
       float velocityForwardLossCoef;
       /*!
        */
       float velocitySideLossCoef;
       /*!
        */
       float velocityUpLossCoef;
       /*!
        */
       float velocityAngleLossCoef;
       /*!
        */
       float steeringForceKoef;
       /*!
        */
       float steeringForce;
       /*!
        */
       float steeringDamping;
       /*!
        */
       float horizMaxSpeed;
       /*!
        */
       float horizResistSpeed;
       /*!
        */
       float horizResistFactor;
       /*!
        */
       float mUpMaxSpeed;
       /*!
        */
       float mUpResistSpeed;
       /*!
        */
       float mUpResistFactor;
       /*!
        */
       float toPlayerMinDamageVelocity;
       /*!
        */
       float toPlayerDamageCoef;
       /*!
        */
       float toPlayerKickCoef;
       /*!
        */
       float toPlayerKickUp;
       /*!
        */
       string visibleMeshes;
       /*!
        */
       string allowedSkins;
       /*!
        */
       string corpseIDs;
       /*!
        */
       float criticalWaterCoverage;
       /*!
        */
       float hindlegsWaterCoverage;
       /*!
        */
       int hindlegsWaterCoverageTimeout;
       /*!
        */
       int minimalLevel;
       /*!
        */
       string behavior;
    };
    
    class  Steed : public HorseData {
      public:
       virtual Script onTrigger(()) {}
       virtual Script onLeaveLiquid(( string this, string obj, string type )) {}
       virtual Script onEnterLiquid(( string this, string obj, string coverage, string type )) {}
       virtual Script onEnterMissionArea(( string this, string obj )) {}
       virtual Script onLeaveMissionArea(( string this, string obj )) {}
       virtual Script onDisabled(( string this, string obj, string state )) {}
       virtual Script onDamage(()) {}
       virtual Script damage(( string this, string obj, string sourceObject, string position, string damage, string damageType )) {}
       virtual Script onImpact(( string this, string obj, string collidedObject, string vec, string vecLen )) {}
       virtual Script onCollision(()) {}
       virtual Script onRearing(( string this, string obj )) {}
       virtual Script onNewDataBlock(()) {}
       virtual Script onRemove(( string this, string obj )) {}
       virtual Script onAdd(( string this, string obj )) {}
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedCourierHorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedRidingMoose : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedHardyWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedSpiritedWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedHorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HarnessedStallion : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseCourierHorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  RidingMoose : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseRoyalWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseHeavyWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseSpiritedWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseHardyWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseSimpleWarhorse : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseRidingFemale : public Steed {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HorseRiding : public Steed {
      public:
    };
    
    /*!
    @brief General interface to control a PathCamera object from the script level.
    @see PathCamera
    @tsexample
    datablock PathCameraData(LoopingCam)
    ^{
    ^^mode = "";
    ^};
    @endtsexample
    @ingroup PathCameras
    @ingroup Datablocks
     */
    class  PathCameraData : public ShapeBaseData {
      public:
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PathCamData : public PathCameraData {
      public:
    };
    
    /*!
    @brief A datablock that describes a camera.
    
    @tsexample
    datablock CameraData(Observer)
    {
       mode = "Observer";
    };
    @endtsexample
    @see Camera
    
    @ref Datablock_Networking
    @ingroup BaseCamera
    @ingroup Datablocks
     */
    class  CameraData : public ShapeBaseData {
      public:
    
       /*! @name Camera: Speed
       @{ */
       /*! */
       /*!
       Max allowed movement speed for the camera.
       
        */
       float maxMovementSpeed;
       /// @}
    
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Observer : public CameraData {
      public:
    };
    
    class  Armor : public PlayerData {
      public:
       virtual Script onTrigger(()) {}
       virtual Script onLeaveLiquid(()) {}
       virtual Script onEnterLiquid(()) {}
       virtual Script onEnterMissionArea(( string this, string obj )) {}
       virtual Script onLeaveMissionArea(( string this, string obj )) {}
       virtual Script onDamage(()) {}
       virtual Script damage(( string this, string obj, string sourceObject, string position, string damage, string damageType )) {}
       virtual Script onImpact(( string this, string obj, string collidedObject, string vec, string vecLen )) {}
       virtual Script onCollision(( string this, string obj, string col )) {}
       virtual Script doDismount(( string this, string obj, string forced, string kickedOff )) {}
       virtual Script onNewDataBlock(( string this, string obj )) {}
       virtual Script onRemove(( string this, string obj )) {}
       virtual Script onAdd(( string this, string obj )) {}
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerFemaleData : public Armor {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMaleData : public Armor {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DefaultPlayerData : public Armor {
      public:
    };
    
    class  WeaponData : public ShapeBaseImageData {
      public:
       /*!
       
       
        */
       float WoundMultiplier;
       /*!
       
       
        */
       float FractureMultiplier;
       /*!
       
       
        */
       float StunMultiplier;
       /*!
        */
       WeaponsHitNodeType hitGroupType;
       /*!
        */
       float hitGroupDmgLevel;
       /*!
        */
       intList hitDirection;
       /*!
       
       
        */
       WeaponsAttackTypes attackType;
       /*!
       
       
        */
       WeaponsWeaponTypes weaponType;
       /*!
       
       
        */
       WeaponsWeaponMaterial weaponMaterial;
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  AnimalTrapData : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DefaultWeaponData : public WeaponData {
      public:
    };
    
    class  ExplosiveData : public WeaponData {
      public:
       /*!
        */
       int rayNum;
       /*!
        */
       float ;
       /*!
        */
       float damage;
       /*!
        */
       float explosionMultiplier;
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ExplosionBomb_1151 : public ExplosiveData {
      public:
    };
    
    class  ArrowData : public ShapeBaseImageData {
      public:
       virtual Script onCollision(( string data, string arrow, string obj, string fade, string pos, string normal )) {}
       /*!
        */
       float upForce;
       /*!
        */
       float Friction;
       /*!
       
       
        */
       WeaponData loadedAmmo;
       /*!
       
       
        */
       ExplosiveData explosionData;
       /*!
        */
       int stuckArrowLifeTime;
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CowAmmo : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CowExplosion : public ExplosiveData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CowAmmoLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NapthaBarrelAmmo : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NapthaBarrelExplosion : public ExplosiveData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NapthaBarrelAmmoLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BarrelAmmo : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BarrelExplosion : public ExplosiveData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BarrelAmmoLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SiegeStoneAmmo : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SiegeStoneExplosion : public ExplosiveData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SiegeStoneAmmoLoaded : public WeaponData {
      public:
    };
    
    class  SiegeWeaponStaticShapeData : public StaticShapeData {
      public:
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
       /*!
       
       
        */
       int Object_typeID;
       /*!
       
       
        */
       float MaxAccuracy;
       /*!
       
       
        */
       float Emax;
       /*!
       
       
        */
       float BasePrefireAnimTime;
       /*!
       
       
        */
       float BaseRecoilAnimTime;
       /*!
       
       
        */
       float IntNeed;
       /*!
       
       
        */
       float DurabilityPerShot;
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  TrebuchetData : public SiegeWeaponStaticShapeData {
      public:
    };
    
    class  ThrowingWeaponData : public WeaponData {
      public:
       /*!
        */
       float upForce;
       /*!
        */
       float Friction;
       /*!
       
       
        */
       ArrowData projectileData;
       /*!
        */
       int stuckArrowLifeTime;
       /*!
        */
       float AgilityNeed;
       /*!
        */
       float MaxAccuracy;
       /*!
        */
       float StrengthNeed;
       /*!
        */
       float Emax;
       /*!
        */
       float StaminaRate;
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Snowball : public ThrowingWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SnowballProjectile : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SnowballExplosion : public ExplosiveData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireworkPot : public ThrowingWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireworkPotProjectile : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireworkPotExplosion : public ExplosiveData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingPot : public ThrowingWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingPotProjectile : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PotExplosion : public ExplosiveData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingAxe : public ThrowingWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingAxeProjectile : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingJavelin : public ThrowingWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingJavelinProjectile : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingKnife : public ThrowingWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ThrowingKnifeProjectile : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BaseThrowing : public WeaponData {
      public:
    };
    
    class  RangedWeaponData : public WeaponData {
      public:
       /*!
        */
       float AgilityNeed;
       /*!
        */
       float MaxAccuracy;
       /*!
        */
       intList allowedAmmoIDs;
       /*!
        */
       float StrengthNeed;
       /*!
        */
       float Emax;
       /*!
        */
       float DurabilityPerShot;
       /*!
        */
       float StaminaRate;
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Sling : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyCrossbow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Arbalest : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  LightCrossbow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BaseCrossbow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  LongBow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ShortBow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SimpleBow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CompositeBow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BaseBow : public RangedWeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WoodenBolt : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WoodenBoltLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WoodenArrow : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WoodenArrowLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SlingStone : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SlingStoneLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireworkBolt : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireworkBoltLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DullBolt : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DullBoltLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  StandBolt : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  StandBoltLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyBolt : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyBoltLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireworkArrow : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireworkArrowLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireArrow : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FireArrowLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DullArrow : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DullArrowLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  StandArrow : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  StandArrowLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BroadheadArrow : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BroadheadLoaded : public WeaponData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BodkinArrow : public ArrowData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BodkinArrowLoaded : public WeaponData {
      public:
    };
    
    class  WeaponImage : public WeaponData {
      public:
       virtual Script onHit(( string this, string target, string sourseObj, string hitSpeed, string hitNodeName, string hitBoxName, string groupDmgLevel, string pos, string chargeTime )) {}
       virtual Script onWetFire(( string this, string obj, string slot )) {}
       virtual Script onAltFire(( string this, string obj, string slot )) {}
       virtual Script onFire(( string this, string obj, string slot )) {}
       virtual Script onUnmount(()) {}
       virtual Script onMount(( string this, string obj, string slot )) {}
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BalancedStaff : public WeaponImage {
      public:
    };
    
    class  ShieldData : public WeaponData {
      public:
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyIronShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SmallKiteShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyKiteShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyHeaterShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyTargeShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverCookingPot : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverFishingPole : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverCrucibleTongs : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverSickle : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverKnife : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverSaw : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverPickaxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverHatchet : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverHammer : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BelieverShovel : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SiegeTorch : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HandOfIlyas : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HandOfBoris : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DecoratedJoustingLance : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Torch : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_Fishing_Pole : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Cow_Horns : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Bull_Horns : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mutton_Horns : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Sow_Tusk : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Boar_Tusk : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Moose_Hoof : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Wolf_Fang : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hind_Hoof : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Deer_Hoof : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Wild_Horse_Hoof : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Bear_Paw : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Glassblower_toolkit : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Skinning_knife : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Knife : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_Knife : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Cooking_Pot : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_Cooking_Pot : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  IronRoundShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Sickle : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_Sickle : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  CrucibleandTongs : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_CrucibleandStick : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Saw : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_Saw : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hatchet : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_Axe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fishing_Pole : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mallet : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Smiths_Hammer : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_hammer : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hardened_steel_pickaxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pickaxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_pickaxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Primitive_shovel : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Shovel : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PaviseShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  TowerShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  KiteShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeaterShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BucklerShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PrimitiveShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  TargeShield : public ShieldData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  JoustingLance : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Lance : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  LongPike : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MediumPike : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ShortPike : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BecdeCorbin : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  AwlPike : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BoarSpear : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spear : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Staff : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Partisan : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pitchfork : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WarScythe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Guisarme : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Glaive : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PracticeMaul : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maul : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SledgeHammer : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BroadAxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Bardiche : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pollaxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PracticeGreataxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Flamberge : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Zweihaender : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Claymore : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PracticeLongsword : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WarPick : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Cudgel : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  FlangedMace : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MorningStar : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NordicAxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BattleAxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WarAxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PracticeAxe : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GrossMesser : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BigFalchion : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BastardSword : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Estoc : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PracticeBastard : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Falchion : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Scimitar : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  LightSaber : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  KnightSword : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  NordicSword : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PracticeSword : public WeaponImage {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BaseShield : public ShapeBaseImageData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BaseMeleeWeapon : public ShapeBaseImageData {
      public:
    };
    
    /*!
    @brief Defines shared properties for Trigger objects.
    
    The primary focus of the TriggerData datablock is the callbacks it provides when an object is within or leaves the Trigger bounds.
    @see Trigger.
    @ingroup gameObjects
    @ingroup Datablocks
     */
    class  TriggerData : public GameBaseData {
      public:
          /*! @brief Called when an object enters the volume of the Trigger instance using this TriggerData.
    
    @param trigger the Trigger instance whose volume the object entered
    @param obj the object that entered the volume of the Trigger instance
     */
          void onEnterTrigger( Trigger trigger, GameBase obj );
    
          /*! @brief Called every tickPeriodMS number of milliseconds (as specified in the TriggerData) whenever one or more objects are inside the volume of the trigger.
    
    The Trigger has methods to retrieve the objects that are within the Trigger's bounds if you want to do something with them in this callback.
    @param trigger the Trigger instance whose volume the object is inside
    @see tickPeriodMS
    @see Trigger::getNumObjects()
    @see Trigger::getObject()
     */
          void onTickTrigger( Trigger trigger );
    
          /*! @brief Called when an object leaves the volume of the Trigger instance using this TriggerData.
    
    @param trigger the Trigger instance whose volume the object left
    @param obj the object that left the volume of the Trigger instance
     */
          void onLeaveTrigger( Trigger trigger, GameBase obj );
    
    
       /*! @name Callbacks
       @{ */
       /*! */
       /*!
       @brief Time in milliseconds between calls to onTickTrigger() while at least one object is within a Trigger's bounds.
    
    @see onTickTrigger()
    
       
        */
       int tickPeriodMS;
       /*!
       Forces Trigger callbacks to only be called on clients.
       
        */
       bool clientSide;
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  DefaultTrigger : public TriggerData {
      public:
       virtual Script onTickTrigger(( string this, string trigger )) {}
       virtual Script onLeaveTrigger(( string this, string trigger, string obj )) {}
       virtual Script onEnterTrigger(( string this, string trigger, string obj )) {}
    };
    
    /*!
    @brief Defines the droplets used in a storm (IE: raindrops, snowflakes, etc.).
    
    @tsexample
    datablock PrecipitationData(HeavyRain)
    {
       soundProfile = "HeavyRainSound";
    
       dropTexture = "art/environment/precipitation/rain";
       splashTexture = "art/environment/precipitation/water_splash";
       dropSize = 0.35;
       splashSize = 0.1;
       useTrueBillboards = false;
       splashMS = 500;
    };
    @endtsexample
    @ingroup FX
     */
    class  PrecipitationData : public GameBaseData {
      public:
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HeavyRain : public PrecipitationData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ServerGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ServerNavMeshSet : public SimSet {
      public:
    };
    
    class  NavMesh : public SceneObject {
      public:
       /*! @brief Create a Recast nav mesh. */
       virtual bool build(( bool background=true, bool save=false )) {}
       /*! @brief Cancel the current NavMesh build. */
       virtual void cancelBuild(()) {}
       /*! @brief Rebuild the tiles overlapped by the input box. */
       virtual void buildTiles(( Box3F box )) {}
       /*! @brief Load this NavMesh from its file. */
       virtual bool load(()) {}
       /*! @brief Save this NavMesh to its file. */
       virtual void save(()) {}
    
       /*! @name NavMesh Options
       @{ */
       /*! */
       /*!
       Name of the data file to store this navmesh in (relative to engine executable).
       
        */
       string fileName;
       /*!
       Length/width of a voxel.
       
        */
       float cellSize;
       /*!
       Height of a voxel.
       
        */
       float cellHeight;
       /*!
       The horizontal size of tiles.
       
        */
       float tileSize;
       /*!
       Height of an actor.
       
        */
       float actorHeight;
       /*!
       Maximum climbing height of an actor.
       
        */
       float actorClimb;
       /*!
        of an actor.
       
        */
       float actor;
       /*!
       Maximum walkable slope in degrees.
       
        */
       float walkableSlope;
       /// @}
    
    
       /*! @name NavMesh Rendering
       @{ */
       /*! */
       /*!
       Display this NavMesh even outside the editor.
       
        */
       bool alwaysRender;
       /// @}
    
    
       /*! @name NavMesh Advanced Options
       @{ */
       /*! */
       /*!
       Size of the non-walkable border around the navigation mesh (in voxels).
       
        */
       int borderSize;
       /*!
       Sets the sampling distance to use when generating the detail mesh.
       
        */
       float detailSampleDist;
       /*!
       The maximum distance the detail mesh surface should deviate from heightfield data.
       
        */
       float detailSampleError;
       /*!
       The maximum allowed length for contour edges along the border of the mesh.
       
        */
       int maxEdgeLen;
       /*!
       The maximum distance a simplfied contour's border edges should deviate from the original raw contour.
       
        */
       float simplificationError;
       /*!
       The minimum number of cells allowed to form isolated island areas.
       
        */
       int minRegionArea;
       /*!
       Any regions with a span count smaller than this value will, if possible, be merged with larger regions.
       
        */
       int mergeRegionArea;
       /*!
       The maximum number of polygons allowed in a tile.
       
        */
       int maxPolysPerTile;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GlobalNavMesh : public NavMesh {
      public:
    };
    
    /*!
    @brief Base class for defining a type of ForestItem. It does not implement loading or rendering of the shapeFile.
    
     */
    class  ForestItemData : public SimDataBlock {
      public:
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Media
       @{ */
       /*! */
       /*!
       Shape file for this item type
       
        */
       filename shapeFile;
       /*!
       Can other objects or spacial queries hit items of this type.
       
        */
       bool collidable;
       /*!
        used during placement to ensure items are not crowded.
       
        */
       float ;
       /// @}
    
    
       /*! @name Wind
       @{ */
       /*! */
       /*!
       Mass used in calculating spring forces on the trunk. Generally how springy a plant is.
       
        */
       float mass;
       /*!
       Rigidity used in calculating spring forces on the trunk. How much the plant resists the wind force
       
        */
       float rigidity;
       /*!
       Coefficient used in calculating spring forces on the trunk. How much the plant resists bending.
       
        */
       float tightnessCoefficient;
       /*!
       Coefficient used in calculating spring forces on the trunk. Causes oscillation and forces to decay faster over time.
       
        */
       float dampingCoefficient;
       /*!
       Overall scale to the effect of wind.
       
        */
       float windScale;
       /*!
       Overall bend amount of the tree trunk by wind and impacts.
       
        */
       float trunkBendScale;
       /*!
       Amplitude of the effect on larger branches.
       
        */
       float branchAmp;
       /*!
       Amplitude of the winds effect on leafs/fronds.
       
        */
       float detailAmp;
       /*!
       Frequency (speed) of the effect on leafs/fronds.
       
        */
       float detailFreq;
       /// @}
    
    
       /*! @name CM
       @{ */
       /*! */
       /*!
       Family of trees with this item datablock
       
        */
       ForestTree::Family family;
       /*!
       Health of trees with this item datablock
       
        */
       ForestTree::Health health;
       /*!
       Age of trees with this item datablock
       
        */
       ForestTree::Age age;
       /*!
       Method with which trees with this item datablock are planted
       
        */
       ForestTree::PlantedBy plantedBy;
       /*!
       Amount of wood on such trees
       
        */
       int woodAmount;
       /*!
       File name of falling tree model
       
        */
       filename fallShapeFile;
       /*!
       Things that can be gathered from tree of this type
       
        */
       S32_Pair gatherables;
       /// @}
    
    };
    
    /*!
    @brief Concrete implementation of ForestItemData which loads and renders dts format shapeFiles.
    
     */
    class  TSForestItemData : public ForestItemData {
      public:
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Media
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Wind
       @{ */
       /*! */
       /// @}
    
    
       /*! @name CM
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Spinny_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Juniper_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Hazel_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Aspen_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Oak_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Mulberry_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Maple_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Pine_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Fir_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Elm_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Birch_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PlayerMade_Apple_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Spinny_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Juniper_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Hazel_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Aspen_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Oak_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Mulberry_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Maple_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Pine_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Fir_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Elm_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Birch_Ill_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Stump_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Great_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Normal_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Ill_Major : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Stump_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Great_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Normal_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Ill_Medium : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Stump_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Great_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Normal_Minor : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Natural_Apple_Ill_Minor : public TSForestItemData {
      public:
    };
    
    class  FamilyData : public SimDataBlock {
      public:
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
       /*!
       Family of trees with this datablock
       
        */
       ForestTree::Family family;
       /*!
       'minor -> medium' scale
       
        */
       float mediumScale;
       /*!
       'medium -> major' scale
       
        */
       float majorScale;
       /*!
       major scale
       
        */
       float matureScale;
       /*!
       Is a tree of this family of 'hard' types of wood
       
        */
       bool isHardwood;
       /*!
       Number of days between tree birth and it reaching 'medium' age
       
        */
       int naturalYoungTime;
       /*!
       Number of days between tree reaching 'medium' age and it reaching 'major' age
       
        */
       int naturalMatureTime;
       /*!
       Number of days between tree birth and it reaching 'medium' age
       
        */
       int playerPlantedYoungTime;
       /*!
       Number of days between tree reaching 'medium' age and it reaching 'major' age
       
        */
       int playerPlantedMatureTime;
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SpinnyFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  JuniperFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  HazelFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  AspenFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  OakFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MulberryFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  MapleFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PineFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  SpruceFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ElmFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BirchFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  AppleFamilyData : public FamilyData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Spinny_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Juniper_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Hazel_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Aspen_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Oak_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Mulberry_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Maple_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Pine_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Fir_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Elm_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Birch_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Stump_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Great_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Normal_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Ill_Major_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Stump_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Great_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Normal_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Ill_Medium_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Stump_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Great_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Normal_Minor_Base : public TSForestItemData {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ForestItemDataGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  Apple_Ill_Minor_Base : public TSForestItemData {
      public:
    };
    
    class  DatabaseInterface : public SimGroup {
      public:
       /*! Initialize the connection to RDBMS
     */
       virtual bool initialize(( DBIType requiredType )) {}
       virtual bool initOK() {}
       virtual bool connect() {}
       virtual void disconnect() {}
       virtual bool reconnect() {}
       virtual bool isConnected() {}
       virtual bool ping() {}
       virtual void dumpError() {}
       virtual void setDebug() {}
       virtual int getPendingEventCount() {}
       virtual int Execute() {}
       virtual int Query() {}
       virtual int Select() {}
       virtual int Update() {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  dbiGuilds : public DatabaseInterface {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  dbiInvHelper : public DatabaseInterface {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  dbiInventory : public DatabaseInterface {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  dbi : public DatabaseInterface {
      public:
    };
    
    /*!
    @brief This class is responsible opening, reading, creating, and saving file contents.
    
    FileObject acts as the interface with OS level files.  You create a new FileObject and pass into it a file's path and name.  The FileObject class supports three distinct operations for working with files:
    
    <table border='1' cellpadding='1'><tr><th>Operation</th><th>%FileObject Method</th><th>Description</th></tr><tr><td>Read</td><td>openForRead()</td><td>Open the file for reading</td></tr><tr><td>Write</td><td>openForWrite()</td><td>Open the file for writing to and replace its contents (if any)</td></tr><tr><td>Append</td><td>openForAppend()</td><td>Open the file and start writing at its end</td></tr></table>
    
    Before you may work with a file you need to use one of the three above methods on the FileObject.
    
    @tsexample
    // Create a file object for writing
    %fileWrite = new FileObject();
    
    // Open a file to write to, if it does not exist it will be created
    %result = %fileWrite.OpenForWrite("./test.txt");
    
    if ( %result )
    {
       // Write a line to the text files
       %fileWrite.writeLine("READ. READ CODE. CODE");
    }
    
    // Close the file when finished
    %fileWrite.close();
    
    // Cleanup the file object
    %fileWrite.delete();
    
    
    // Create a file object for reading
    %fileRead = new FileObject();
    
    // Open a text file, if it exists
    %result = %fileRead.OpenForRead("./test.txt");
    
    if ( %result )
    {
       // Read in the first line
       %line = %fileRead.readline();
    
       // Print the line we just read
       echo(%line);
    }
    
    // Close the file when finished
    %fileRead.close();
    
    // Cleanup the file object
    %fileRead.delete();
    @endtsexample
    
    @ingroup FileSystem
     */
    class  FileObject : public SimObject {
      public:
       /*! @brief Open a specified file for reading
    
    There is no limit as to what kind of file you can read. Any format and data contained within is accessible, not just text
    
    @param filename Path, name, and extension of file to be read@tsexample
    // Create a file object for reading
    %fileRead = new FileObject();
    
    // Open a text file, if it exists
    %result = %fileRead.OpenForRead("./test.txt");
    @endtsexample
    
    @return True if file was successfully opened, false otherwise
     */
       virtual bool openForRead(( string filename )) {}
       /*! @brief Open a specified file for writing
    
    There is no limit as to what kind of file you can write. Any format and data is allowable, not just text
    
    @param filename Path, name, and extension of file to write to@tsexample
    // Create a file object for writing
    %fileWrite = new FileObject();
    
    // Open a file to write to, if it does not exist it will be created
    %result = %fileWrite.OpenForWrite("./test.txt");
    @endtsexample
    
    @return True if file was successfully opened, false otherwise
     */
       virtual bool openForWrite(( string filename )) {}
       /*! @brief Open a specified file for writing, adding data to the end of the file
    
    There is no limit as to what kind of file you can write. Any format and data is allowable, not just text. Unlike openForWrite(), which will erase an existing file if it is opened, openForAppend() preserves data in an existing file and adds to it.
    
    @param filename Path, name, and extension of file to append to@tsexample
    // Create a file object for writing
    %fileWrite = new FileObject();
    
    // Open a file to write to, if it does not exist it will be created
    // If it does exist, whatever we write will be added to the end
    %result = %fileWrite.OpenForAppend("./test.txt");
    @endtsexample
    
    @return True if file was successfully opened, false otherwise
     */
       virtual bool openForAppend(( string filename )) {}
       /*! @brief Determines if the parser for this FileObject has reached the end of the file
    
    @tsexample
    // Create a file object for reading
    %fileRead = new FileObject();
    
    // Open a text file, if it exists
    %fileRead.OpenForRead("./test.txt");
    
    // Keep reading until we reach the end of the file
    while( !%fileRead.isEOF() )
    {
       %line = %fileRead.readline();
       echo(%line);
    }
    
    // Made it to the end
    echo("Finished reading file");
    @endtsexample
    
    @return True if the parser has reached the end of the file, false otherwise
     */
       virtual bool isEOF(()) {}
       /*! @brief Read a line from file.
    
    Emphasis on *line*, as in you cannot parse individual characters or chunks of data.  There is no limitation as to what kind of data you can read.
    
    @tsexample
    // Create a file object for reading
    %fileRead = new FileObject();
    
    // Open a text file, if it exists
    %fileRead.OpenForRead("./test.txt");
    
    // Read in the first line
    %line = %fileRead.readline();
    
    // Print the line we just read
    echo(%line);
    @endtsexample
    
    @return String containing the line of data that was just read
     */
       virtual string readLine(()) {}
       /*! @brief Read a line from the file without moving the stream position.
    
    Emphasis on *line*, as in you cannot parse individual characters or chunks of data.  There is no limitation as to what kind of data you can read. Unlike readLine, the parser does not move forward after reading.
    
    @param filename Path, name, and extension of file to be read@tsexample
    // Create a file object for reading
    %fileRead = new FileObject();
    
    // Open a text file, if it exists
    %fileRead.OpenForRead("./test.txt");
    
    // Peek the first line
    %line = %fileRead.peekLine();
    
    // Print the line we just peeked
    echo(%line);
    // If we peek again...
    %line = %fileRead.peekLine();
    
    // We will get the same output as the first time
    // since the stream did not move forward
    echo(%line);
    @endtsexample
    
    @return String containing the line of data that was just peeked
     */
       virtual string peekLine(()) {}
       /*! @brief Write a line to the file, if it was opened for writing.
    
    There is no limit as to what kind of text you can write. Any format and data is allowable, not just text. Be careful of what you write, as whitespace, current values, and literals will be preserved.
    
    @param text The data we are writing out to file.@tsexample
    // Create a file object for writing
    %fileWrite = new FileObject();
    
    // Open a file to write to, if it does not exist it will be created
    %fileWrite.OpenForWrite("./test.txt");
    
    // Write a line to the text files
    %fileWrite.writeLine("READ. READ CODE. CODE");
    
    @endtsexample
    
    @return True if file was successfully opened, false otherwise
     */
       virtual void writeLine(( string text )) {}
       /*! @brief Close the file.
    
    It is EXTREMELY important that you call this function when you are finished reading or writing to a file. Failing to do so is not only a bad programming practice, but could result in bad data or corrupt files. Remember: Open, Read/Write, Close, Delete...in that order!
    
    @tsexample
    // Create a file object for reading
    %fileRead = new FileObject();
    
    // Open a text file, if it exists
    %fileRead.OpenForRead("./test.txt");
    
    // Peek the first line
    %line = %fileRead.peekLine();
    
    // Print the line we just peeked
    echo(%line);
    // If we peek again...
    %line = %fileRead.peekLine();
    
    // We will get the same output as the first time
    // since the stream did not move forward
    echo(%line);
    
    // Close the file when finished
    %fileWrite.close();
    
    // Cleanup the file object
    %fileWrite.delete();
    @endtsexample
    
     */
       virtual void close(()) {}
       virtual void writeObject() {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  foLock : public FileObject {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  TerrainMaterialList : public SimGroup {
      public:
    };
    
    class  PlayerList : public SimSet {
      public:
       virtual Script customAlignmentUpdate(( string this )) {}
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  PhysicsCleanupSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  systemCleanupGroup : public SimGroup {
      public:
    };
    
    class  DspUtil : public SimObject {
      public:
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  dUtil : public DspUtil {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DataBlockGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  sgMissionLightingFilterSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  BehaviorSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  TCPGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GuiDataGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GuiGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ClientGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ActionMapGroup : public SimGroup {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  DataBlockSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  TerrainMaterialSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  WayPointSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  GhostAlwaysSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  ActiveActionMapSet : public SimSet {
      public:
    };
    
    /// Stub class
    /// 
    /// @note This is a stub class to ensure a proper class hierarchy. No 
    ///       information was available for this class.
    class  RootGroup : public SimGroup {
      public:
    };
    
    class  DeathEvent {
      public:
    };
    
    /*!
    @brief Base class for game objects which use datablocks, networking, are editable, and need to process ticks.
    
    @ingroup gameObjects
     */
    class  GameBase : public SceneObject {
      public:
       /*! @brief Get the client (if any) that controls this object.
    
    The controlling client is the one that will send moves to us to act on.
    @return the ID of the controlling GameConnection, or 0 if this object is not controlled by any client.
    @see GameConnection
     */
       virtual int getControllingClient(()) {}
          /*! @brief Called when the client controlling the object changes.
    
    @param controlled true if a client now controls this object, false if no client controls this object.
     */
          void setControl( bool controlled );
    
       virtual void setGhostableFlag(( bool isGhostableFlag=true )) {}
       /*! @brief Get the datablock used by this object.
    
    @return the datablock this GameBase is using.@see setDataBlock()
     */
       virtual int getDataBlock(()) {}
       /*! @brief Assign this GameBase to use the specified datablock.
    
    @param data new datablock to use
    @return true if successful, false if failed.@see getDataBlock()
     */
       virtual bool setDataBlock(( GameBaseData data )) {}
       /*! @brief Apply an impulse to this object as defined by a world position and velocity vector.
    
    @param pos impulse world position
    @param vel impulse velocity (impulse force F = m * v)
    @return Always true
    @note Not all objects that derrive from GameBase have this defined.
     */
       virtual bool applyImpulse(( Point3F pos, VectorF vel )) {}
       /*! @brief Applies a radial impulse to the object using the given origin and force.
    
    @param origin World point of origin of the radial impulse.
    @param  The  of the impulse area.
    @param magnitude The strength of the impulse.
    @note Not all objects that derrive from GameBase have this defined.
     */
       virtual void applyRadialImpulse(( Point3F origin, float , float magnitude )) {}
    
       /*! @name Game
       @{ */
       /*! */
       /*!
       Script datablock used for game objects.
       
        */
       GameBaseData dataBlock;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  ArrowProjectile : public GameBase {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  ProjectileTrailEvent {
      public:
    };
    
    class  BombProjectile : public GameBase {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  BombExplodeDamageRayEvent {
      public:
    };
    
    class  RangedEvent {
      public:
    };
    
    class  HitboxDebugEvent {
      public:
    };
    
    class  SpecialAttackDataEvent {
      public:
    };
    
    class  CompensationDebugHitEvent {
      public:
    };
    
    class  ComplexObject : public SceneObject {
      public:
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  ObjectStateEvent {
      public:
    };
    
    class  ObjectStatePatchEvent {
      public:
    };
    
    class  ObjectOwnerEvent {
      public:
    };
    
    class  ObjectOwnersPatchEvent {
      public:
    };
    
    /*!
    @brief A renderable, collidable convex shape defined by a collection of surface planes.
    
    %ConvexShape is intended to be used as a temporary asset for quickly blocking out a scene or filling in approximate shapes to be later replaced with final assets. This is most easily done by using the WorldEditor's Sketch Tool.
    
     */
    class  ConvexShape : public SceneObject {
      public:
    
       /*! @name Internal
       @{ */
       /*! */
       /*!
       Do not modify, for internal use.
       
        */
       string surface;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @ingroup gameObjects
     */
    class  ShapeBase : public GameBase {
      public:
       virtual Script cycleWeapon(( string this, string direction )) {}
       virtual Script clearDamageDt(( string this )) {}
       virtual Script setDamageDt(( string this, string damageAmount, string damageType )) {}
       virtual Script damage(( string this, string sourceObject, string position, string damage, string damageType )) {}
       virtual Script doRaycast(( string this, string range, string mask )) {}
       virtual Script onInventory(()) {}
       virtual Script throwObject(( string this, string obj )) {}
       virtual Script clearInventory(()) {}
       virtual Script setInventory(( string this, string data, string value )) {}
       virtual Script getInventory(( string this, string data )) {}
       virtual Script decInventory(( string this, string data, string amount )) {}
       virtual Script incInventory(( string this, string data, string amount )) {}
       virtual Script maxInventory(( string this, string data )) {}
       virtual Script hasAmmo(( string this, string weapon )) {}
       virtual Script hasInventory(( string this, string data )) {}
       virtual Script pickup(( string this, string obj, string amount )) {}
       virtual Script throw(( string this, string data, string amount )) {}
       virtual Script use(( string this, string data )) {}
          /*! @brief Called on the server when the client has requested a FOV change.
    
    When the client requests that its field of view should be changed (because they want to use a sniper scope, for example) this new FOV needs to be validated by the server.  This method is called if it exists (it is optional) to validate the requested FOV, and modify it if necessary.  This could be as simple as checking that the FOV falls within a correct range, to making sure that the FOV matches the capabilities of the current weapon.
    
    Following this method, ShapeBase ensures that the given FOV still falls within the datablock's cameraMinFov and cameraMaxFov.  If that is good enough for your purposes, then you do not need to define the validateCameraFov() callback for your ShapeBase.
    
    @param fov The FOV that has been requested by the client.
    @return The FOV as validated by the server.
    
    @see ShapeBaseData
    
     */
          float validateCameraFov( float fov );
    
       /*! @brief Add or remove this object from the scene.
    
    When removed from the scene, the object will not be processed or rendered.
    @param show False to hide the object, true to re-show it
    
     */
       virtual void setHidden(( bool show )) {}
       /*! Check if the object is hidden.
    @return true if the object is hidden, false if visible.
    
     */
       virtual bool isHidden(()) {}
       /*! @brief Mount a new Image.
    
    @param image the Image to mount
    @param slot Image slot to mount into (valid range is 0 - 3)
    @param loaded initial loaded state for the Image
    @param skinTag tagged string to reskin the mounted Image
    @return true if successful, false if failed
    
    @tsexample
    %player.mountImage( PistolImage, 1 );
    %player.mountImage( CrossbowImage, 0, false );
    %player.mountImage( RocketLauncherImage, 0, true, 'blue' );
    @endtsexample
    @see unmountImage()
    @see getMountedImage()
    @see getPendingImage()
    @see isImageMounted()
     */
       virtual bool mountImage(( ShapeBaseImageData image, int slot, bool loaded=true, int skinID=Skins::DefaultSkinID.underlying(), string skinTag="" )) {}
       /*! @brief Unmount the mounted Image in the specified slot.
    
    @param slot Image slot to unmount
    @return true if successful, false if failed
    
    @see mountImage()
     */
       virtual bool unmountImage(( int slot )) {}
       virtual bool unmountAllImages(()) {}
       virtual bool toggleWeaponSlot(( int slot )) {}
       /*! @brief Get the Image mounted in the specified slot.
    
    @param slot Image slot to query
    @return ID of the ShapeBaseImageData datablock mounted in the slot, or 0 if no Image is mounted there.
    
     */
       virtual int getMountedImage(( int slot )) {}
       /*! @brief Get the Image that will be mounted next in the specified slot.
    
    Calling mountImage when an Image is already mounted does one of two things: <ol><li>Mount the new Image immediately, the old Image is discarded and whatever state it was in is ignored.</li><li>If the current Image state does not allow Image changes, the new Image is marked as pending, and will not be mounted until the current state completes. eg. if the user changes weapons, you may wish to ensure that the current weapon firing state plays to completion first.</li></ol>
    This command retrieves the ID of the pending Image (2nd case above).
    @param slot Image slot to query
    @return ID of the pending ShapeBaseImageData datablock, or 0 if none.
    
     */
       virtual int getPendingImage(( int slot )) {}
       /*! @brief Check if the current Image state is firing.
    
    @param slot Image slot to query
    @return true if the current Image state in this slot has the 'stateFire' flag set.
     */
       virtual bool isImageFiring(( int slot )) {}
       /*! @brief Check if the given datablock is mounted to any slot on this object.
    
    @param image ShapeBaseImageData datablock to query
    @return true if the Image is mounted to any slot, false otherwise.
    
     */
       virtual bool isImageMounted(( ShapeBaseImageData image )) {}
       /*! @brief Get the first slot the given datablock is mounted to on this object.
    
    @param image ShapeBaseImageData datablock to query
    @return index of the first slot the Image is mounted in, or -1 if the Image is not mounted in any slot on this object.
    
     */
       virtual int getMountSlot(( ShapeBaseImageData image )) {}
       /*! @brief Get the name of the current state of the Image in the specified slot.
    
    @param slot Image slot to query
    @return name of the current Image state, or "Error" if slot is invalid
    
     */
       virtual string getImageState(( int slot )) {}
       /*! @brief Get the trigger state of the Image mounted in the specified slot.
    
    @param slot Image slot to query
    @return the Image's current trigger state
    
     */
       virtual bool getImageTrigger(( int slot )) {}
       /*! @brief Get the alt trigger state of the Image mounted in the specified slot.
    
    @param slot Image slot to query
    @return the Image's current alt trigger state
    
     */
       virtual bool getImageAltTrigger(( int slot )) {}
       /*! @brief Get the ammo state of the Image mounted in the specified slot.
    
    @param slot Image slot to query
    @return the Image's current ammo state
    
     */
       virtual bool getImageAmmo(( int slot )) {}
       /*! @brief Set the ammo state of the Image mounted in the specified slot.
    
    @param slot Image slot to modify
    @param state new ammo state for the Image
    @return the Image's new ammo state
    
     */
       virtual bool setImageAmmo(( int slot, bool state )) {}
       /*! @brief Get the loaded state of the Image mounted in the specified slot.
    
    @param slot Image slot to query
    @return the Image's current loaded state
    
     */
       virtual bool getImageLoaded(( int slot )) {}
       /*! @brief Set the loaded state of the Image mounted in the specified slot.
    
    @param slot Image slot to modify
    @param state new loaded state for the Image
    @return the Image's new loaded state
    
     */
       virtual bool setImageLoaded(( int slot, bool state )) {}
       /*! @brief Get the muzzle vector of the Image mounted in the specified slot.
    
    If the Image shape contains a node called 'muzzlePoint', then the muzzle vector is the forward direction vector of that node's transform in world space. If no such node is specified, the slot's mount node is used instead.
    
    If the correctMuzzleVector and firstPerson flags are set in the Image, the muzzle vector is computed to point at whatever object is right in front of the object's 'eye' node.
    @param slot Image slot to query
    @return the muzzle vector, or "0 1 0" if the slot is invalid
    
     */
       virtual string getMuzzleVector(( int slot )) {}
       /*! @brief Get the muzzle position of the Image mounted in the specified slot.
    
    If the Image shape contains a node called 'muzzlePoint', then the muzzle position is the position of that node in world space. If no such node is specified, the slot's mount node is used instead.
    @param slot Image slot to query
    @return the muzzle position, or "0 0 0" if the slot is invalid
    
     */
       virtual string getMuzzlePoint(( int slot )) {}
       /*! @brief Get the world transform of the specified mount slot.
    
    @param slot Image slot to query
    @return the mount transform
    
     */
       virtual string getSlotTransform(( int slot )) {}
       /*! @brief Get the object's current velocity.
    
    @return the current velocity
    
     */
       virtual string getVelocity(()) {}
       /*! @brief Set the object's velocity.
    
    @param vel new velocity for the object
    @return true
    
     */
       virtual bool setVelocity(( Point3F vel )) {}
       /*! @brief Apply an impulse to the object.
    
    @param pos world position of the impulse
    @param vec impulse momentum (velocity * mass)
    @return true
    
     */
       virtual bool applyImpulse(( Point3F pos, Point3F vec )) {}
       /*! @brief Get the forward direction of the 'eye' for this object.
    
    If the object model has a node called 'eye', this method will return that node's current forward direction vector, otherwise it will return the object's current forward direction vector.
    @return the eye vector for this object
    @see getEyePoint
    @see getEyeTransform
     */
       virtual string getEyeVector(()) {}
       /*! @brief Get the position of the 'eye' for this object.
    
    If the object model has a node called 'eye', this method will return that node's current world position, otherwise it will return the object's current world position.
    @return the eye position for this object
    @see getEyeVector
    @see getEyeTransform
     */
       virtual string getEyePoint(()) {}
       /*! @brief Get the 'eye' transform for this object.
    
    If the object model has a node called 'eye', this method will return that node's current transform, otherwise it will return the object's current transform.
    @return the eye transform for this object
    @see getEyeVector
    @see getEyePoint
     */
       virtual string getEyeTransform(()) {}
       /*! @brief Get the world position this object is looking at.
    
    Casts a ray from the eye and returns information about what the ray hits.
    @param distance maximum distance of the raycast
    @param typeMask typeMask of objects to include for raycast collision testing
    @return look-at information as "Object HitX HitY HitZ [Material]" or empty string for no hit
    
    @tsexample
    %lookat = %obj.getLookAtPoint();
    echo( "Looking at: " @ getWords( %lookat, 1, 3 ) );
    @endtsexample
     */
       virtual string getLookAtPoint(( float distance=2000, int typeMask=0xFFFFFFFF )) {}
       /*! @brief Set the object's current damage level.
    
    @param level new damage level
    @see getDamageLevel()
    @see getDamagePercent()
     */
       virtual void setDamageLevel(( float level )) {}
       /*! @brief Get the object's current damage level.
    
    @return damage level
    @see setDamageLevel()
     */
       virtual float getDamageLevel(()) {}
       /*! @brief Get the object's current damage level as a percentage of maxDamage.
    
    @return damageLevel / datablock.maxDamage
    @see setDamageLevel()
     */
       virtual float getDamagePercent(()) {}
       /*! @brief Set the object's damage state.
    
    @param state should be one of "Enabled", "Disabled", "Destroyed"
    @return true if successful, false if failed
    @see getDamageState()
     */
       virtual bool setDamageState(( string state )) {}
       /*! @brief Get the object's damage state.
    
    @return the damage state; one of "Enabled", "Disabled", "Destroyed"
    @see setDamageState()
     */
       virtual string getDamageState(()) {}
       /*! @brief Check if the object is in the Destroyed damage state.
    
    @return true if damage state is "Destroyed", false if not
    @see isDisabled()
    @see isEnabled()
     */
       virtual bool isDestroyed(()) {}
       /*! @brief Check if the object is in the Disabled or Destroyed damage state.
    
    @return true if damage state is not "Enabled", false if it is
    @see isDestroyed()
    @see isEnabled()
     */
       virtual bool isDisabled(()) {}
       /*! @brief Check if the object is in the Enabled damage state.
    
    @return true if damage state is "Enabled", false if not
    @see isDestroyed()
    @see isDisabled()
     */
       virtual bool isEnabled(()) {}
       /*! @brief Increment the current damage level by the specified amount.
    
    @param amount value to add to current damage level
     */
       virtual void applyDamage(( float amount, SimObjectId hit_author_sim_id )) {}
       /*! @brief Repair damage by the specified amount.
    
    Note that the damage level is only reduced by repairRate per tick, so it may take several ticks for the total repair to complete.
    @param amount total repair value (subtracted from damage level over time)
     */
       virtual void applyRepair(( float amount )) {}
       /*! @brief Set amount to repair damage by each tick.
    
    Note that this value is separate to the repairRate field in ShapeBaseData. This value will be subtracted from the damage level each tick, whereas the ShapeBaseData field limits how much of the applyRepair value is subtracted each tick. Both repair types can be active at the same time.
    @param rate value to subtract from damage level each tick (must be > 0)
    @see getRepairRate()
     */
       virtual void setRepairRate(( float rate )) {}
       /*! @brief Get the per-tick repair amount.
    
    @return the current value to be subtracted from damage level each tick
    @see setRepairRate
     */
       virtual float getRepairRate(()) {}
       /*! @brief Get the object (if any) that controls this object.
    
    @return the ID of the controlling ShapeBase object, or 0 if this object is not controlled by another object.
     */
       virtual int getControllingObject(()) {}
       /*! @brief Check if this object can cloak.
    
    @return true
    @note Not implemented as it always returns true. */
       virtual bool canCloak(()) {}
       /*! @brief Set the cloaked state of this object.
    
    When an object is cloaked it is not rendered.
    @param cloak true to cloak the object, false to uncloak
    @see isCloaked()
     */
       virtual void setCloaked(( bool cloak )) {}
       /*! @brief Check if this object is cloaked.
    
    @return true if cloaked, false if not
    @see setCloaked()
     */
       virtual bool isCloaked(()) {}
       /*! @brief Returns the default vertical field of view in degrees for this object if used as a camera.
    
    @return Default FOV
     */
       virtual float getDefaultCameraFov(()) {}
       /*! @brief Returns the vertical field of view in degrees for this object if used as a camera.
    
    @return current FOV as defined in ShapeBaseData::cameraDefaultFov
     */
       virtual float getCameraFov(()) {}
       /*! @brief Set the vertical field of view in degrees for this object if used as a camera.
    
    @param fov new FOV value
     */
       virtual void setCameraFov(( float fov )) {}
       /*! @brief Setup the invincible effect.
    
    This effect is used for HUD feedback to the user that they are invincible.
    @note Currently not implemented
    @param time duration in seconds for the invincible effect
    @param speed speed at which the invincible effect progresses
     */
       virtual void setInvincibleMode(( float time, float speed )) {}
       /*! @brief Set the damage direction vector.
    
    Currently this is only used to initialise the explosion if this object is blown up.
    @param vec damage direction vector
    
    @tsexample
    %obj.setDamageVector( "0 0 1" );
    @endtsexample
     */
       virtual void setDamageVector(( Point3F vec )) {}
       /*! @brief Get the name of the indexed shape material.
    
    @param index index of the material to get (valid range is 0 - getTargetCount()-1).
    @return the name of the indexed material.
    
    @see getTargetCount()
     */
       virtual string getTargetName(( int index )) {}
       /*! @brief Get the number of materials in the shape.
    
    @return the number of materials in the shape.
    
    @see getTargetName()
     */
       virtual int getTargetCount(()) {}
       /*! @brief Get the model filename used by this shape.
    
    @return the shape filename
    
     */
       virtual string getModelFile(()) {}
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  DynamicShape : public ShapeBase {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A very basic class containing information used by MissionMarker objects for rendering
    
    MissionMarkerData, is an extremely barebones class derived from ShapeBaseData. It is solely used by MissionMarker classes (such as SpawnSphere), so that you can see the object while editing a level.
    
    @tsexample
    datablock MissionMarkerData(SpawnSphereMarker)
    {
       category = "Misc";
       shapeFile = "core/art/shapes/octahedron.dts";
    };
    @endtsexample
    
    @see MissionMarker
    
    @see SpawnSphere
    
    @see WayPoint
    
    @ingroup enviroMisc
     */
    class  MissionMarkerData : public ShapeBaseData {
      public:
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief This is a base class for all "marker" related objets. It is a 3D representation of a point in the level.
    
    The main use of a MissionMarker is to represent a point in 3D space with a mesh and basic ShapeBase information. If you simply need to mark a spot in your level, with no overhead from additional fields, this is a useful object.
    
    @tsexample
    new MissionMarker()
    {
       dataBlock = "WayPointMarker";
       position = "295.699 -171.817 280.124";
       rotation = "0 0 -1 13.8204";
       scale = "1 1 1";
       isRenderEnabled = "true";
       canSaveDynamicFields = "1";
       enabled = "1";
    };
    @endtsexample
    
    @note MissionMarkers will not add themselves to the scene except when in the editor.
    
    @see MissionMarkerData
    
    @see SpawnSphere
    
    @see WayPoint
    
    @ingroup enviroMisc
     */
    class  MissionMarker : public ShapeBase {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Special type of marker, distinguished by a name and team ID number
    
    The original Torque engines were built from a multi-player game called Tribes. The Tribes series featured various team based game modes, such as capture the flag. The WayPoint class survived the conversion from game (Tribes) to game engine (Torque).
    
    Essentially, this is a MissionMarker with the addition of two variables: markerName and team. Whenever a WayPoint is created, it is added to a unique global list called WayPointSet. You can iterate through this set, seeking out specific markers determined by their markerName and team ID. This avoids the overhead of constantly calling commandToClient and commandToServer to determine a WayPoint object's name, unique ID, etc.
    
    @note The <i>markerName<i> field was previously called <i>name</i>, but was changed because this conflicted with the SimObject name field. Existing scripts that relied on the WayPoint <i>name</i> field will need to be updated.
    
    @tsexample
    new WayPoint()
    {
       team = "1";
       dataBlock = "WayPointMarker";
       position = "-0.0224786 1.53471 2.93219";
       rotation = "1 0 0 0";
       scale = "1 1 1";
       canSave = "1";
       canSaveDynamicFields = "1";
    };
    @endtsexample
    
    @see MissionMarker
    
    @see MissionMarkerData
    
    @ingroup enviroMisc
     */
    class  WayPoint : public MissionMarker {
      public:
    
       /*! @name Misc
       @{ */
       /*! */
       /*!
       Unique name representing this waypoint
       
        */
       caseString markerName;
       /*!
       Unique numerical ID assigned to this waypoint, or set of waypoints
       
        */
       WayPointTeam team;
       /// @}
    
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Special type of mission marker which allows a level editor's camera to jump to specific points.
    
    For Torque 3D editors only, not for actual game development
    
     */
    class  CameraBookmark : public MissionMarker {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  DbgHitTrackEvent {
      public:
    };
    
    class  TimeTrackedNetEvent {
      public:
    };
    
    class  ImageFireEvent : public TimeTrackedNetEvent {
      public:
    };
    
    class  WeaponHitOccured_ServerToClientEvent {
      public:
    };
    
    class  SoundEvent {
      public:
    };
    
    class  ObjEffectsEvent {
      public:
    };
    
    class  GroundEffectEvent {
      public:
    };
    
    class  GroundEffectPosEvent {
      public:
    };
    
    class  RegionChangedEvent {
      public:
    };
    
    /*!
    @brief The most basic 3D shape with a datablock available in Torque 3D.
    
    When it comes to placing 3D objects in the scene, you technically have two options:
    
    1. TSStatic objects
    
    2. ShapeBase derived objects
    
    Since ShapeBase and ShapeBaseData are not meant to be instantiated in script, you will use one of its child classes instead. Several game related objects are derived from ShapeBase: Player, Vehicle, Item, and so on.
    
    When you need a 3D object with datablock capabilities, you will use an object derived from ShapeBase. When you need an object with extremely low overhead, and with no other purpose than to be a 3D object in the scene, you will use TSStatic.
    
    The most basic child of ShapeBase is StaticShape. It does not introduce any of the additional functionality you see in Player, Item, Vehicle or the other game play heavy classes. At its core, it is comparable to a TSStatic, but with a datbalock.  Having a datablock provides a location for common variables as well as having access to various ShapeBaseData, GameBaseData and SimDataBlock callbacks.
    
    @tsexample
    // Create a StaticShape using a datablock
    datablock StaticShapeData(BasicShapeData)
    {
    ^shapeFile = "art/shapes/items/kit/healthkit.dts";
    ^testVar = "Simple string, not a stock variable";
    };
    
    new StaticShape()
    {
    ^dataBlock = "BasicShapeData";
    ^position = "0.0 0.0 0.0";
    ^rotation = "1 0 0 0";
    ^scale = "1 1 1";
    };
    @endtsexample
    
    @see StaticShapeData
    @see ShapeBase
    @see TSStatic
    
    @ingroup gameObjects
     */
    class  StaticShape : public ShapeBase {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  StaticShapeWithDoorData : public StaticShapeData {
      public:
    
       /*! @name Door
       @{ */
       /*! */
       /*!
       
       
        */
       string openSequenceName;
       /*!
       
       
        */
       string closeSequenceName;
       /// @}
    
    
       /*! @name Render
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Physics
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Damage/Energy
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Camera
       
       The settings used by the shape when it is the camera.
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Scripting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  StaticShapeWithDoor : public StaticShape {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  ControlObjectEvent {
      public:
    };
    
    class  SetMissionCRCEvent {
      public:
    };
    
    /*!
    @brief Use by GameConnection to send a 2D sound event over the network.
    
    Not intended for game development, internal use only, but does expose GameConnection::play2D.
    
     */
    class  Sim2DAudioEvent {
      public:
    };
    
    /*!
    @brief Use by GameConnection to send a 3D sound event over the network.
    
    Not intended for game development, internal use only, but does expose GameConnection::play3D.
    
     */
    class  Sim3DAudioEvent {
      public:
    };
    
    class  TickDurationChangeEvent {
      public:
    };
    
    class  ChatEvent {
      public:
    };
    
    class  ConfigEvent {
      public:
    };
    
    class  CmMessageEvent {
      public:
    };
    
    class  YoConnectedPlayerEvent {
      public:
    };
    
    class  AchievementEvent {
      public:
    };
    
    class  UpdateTrackEvent {
      public:
    };
    
    class  ClientBarterUpdateEvent {
      public:
    };
    
    class  ServerBarterChangeEvent {
      public:
    };
    
    class  StableEvent {
      public:
    };
    
    class  CharacterNameDataRequestEvent {
      public:
    };
    
    class  CharacterNameDataEvent {
      public:
    };
    
    class  CharacterInfoEvent {
      public:
    };
    
    class  CharInfoEvent {
      public:
    };
    
    class  PremiumTitlesUpdateEvent {
      public:
    };
    
    class  PlayerTitleEvent {
      public:
    };
    
    class  CraftworkEvent {
      public:
    };
    
    class  GreenhouseEvent {
      public:
    };
    
    class  EquipmentEvent {
      public:
    };
    
    class  EquipmentSkinApplyEvent {
      public:
    };
    
    class  CmObjectEvent {
      public:
    };
    
    class  CmSiegeWeaponStaticShape : public StaticShape {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  ComplexObjectRequestClientDataLocal {
      public:
    };
    
    class  GuildClientDataRequestEvent {
      public:
    };
    
    class  CreateGuildHeraldryReqEvent {
      public:
    };
    
    class  HeraldryInfoEvent {
      public:
    };
    
    class  MixerEvent {
      public:
    };
    
    class  ServerInventoryChangeEvent {
      public:
    };
    
    class  ServerObjInventoryChangeEvent {
      public:
    };
    
    class  ServerEquipmentChangeEvent {
      public:
    };
    
    class  ClientInventoryUpdateEvent {
      public:
    };
    
    class  SplitStackItemEvent {
      public:
    };
    
    class  ClientFeatureUpdateEvent {
      public:
    };
    
    class  ClientMoveContainerEvent {
      public:
    };
    
    class  CloseContainerWindowEvent {
      public:
    };
    
    class  JudgementHourStatusEvent {
      public:
    };
    
    class  MonumentUpgradeRequestEvent {
      public:
    };
    
    /*!
    @brief Object used for remote procedure calls.
    
    Not intended for game development, for exposing ConsoleFunctions (such as commandToClient) only.
    
     */
    class  RemoteCommandEvent {
      public:
    };
    
    class  ChangeNetEvent {
      public:
    };
    
    class  BatchChangeNetEvent {
      public:
    };
    
    /*!
    @ingroup gameObjects
     */
    class  Player : public DynamicShape {
      public:
       virtual Script jt(( string this, string where )) {}
       virtual Script use(( string player, string data )) {}
       virtual Script playPain(( string this )) {}
       virtual Script playDeathCry(( string this )) {}
       virtual Script playCelAnimation(( string this, string anim )) {}
       virtual Script playDeathAnimation(( string this )) {}
       virtual Script isPilot(( string this )) {}
       virtual Script mountVehicles(( string this, string bool )) {}
       virtual Script kill(( string this, string damageType )) {}
       virtual Script OnArrowDamage(( string this, string arrow, string arrowData, string pos, string normal )) {}
       virtual int getCharacterId(()) {}
       virtual int getGuildID(()) {}
       virtual int getChInfoGuildID(()) {}
       virtual void finishDismount(()) {}
       virtual void startDismount(()) {}
       virtual void forceDismount(()) {}
       /*! @brief Get the name of the player's current state.
    
    The state is one of the following:
    
    <ul><li>Dead - The Player is dead.</li><li>Mounted - The Player is mounted to an object such as a vehicle.</li><li>Move - The Player is free to move.  The usual state.</li><li>Recover - The Player is recovering from a fall.  See PlayerData::recoverDelay.</li></ul>
    @return The current state; one of: "Dead", "Mounted", "Move", "Recover"
     */
       virtual string getState(()) {}
       /*! @brief Set the sequence that controls the player's arms (dynamically adjusted to match look direction).
    
    @param name Name of the sequence to play on the player's arms.
    @return true if successful, false if failed.
    @note By default the 'look' sequence is used, if available.
     */
       virtual bool setArmThread(( string name )) {}
       /*! @brief Set the main action sequence to play for this player.
    
    @param name Name of the action sequence to set
    @param hold Set to false to get a callback on the datablock when the sequence ends (PlayerData::animationDone()).  When set to true no callback is made.
    @param fsp True if first person and none of the spine nodes in the shape should animate.  False will allow the shape's spine nodes to animate.
    @return True if succesful, false if failed
    @note The spine nodes for the Player's shape are named as follows:
    
    <ul><li>Bip01 Pelvis</li><li>Bip01 Spine</li><li>Bip01 Spine1</li><li>Bip01 Spine2</li><li>Bip01 Neck</li><li>Bip01 Head</li></ul>
    
    You cannot use setActionThread() to have the Player play one of the motion determined action animation sequences.  These sequences are chosen based on how the Player moves and the Player's current pose.  The names of these sequences are:
    
    <ul><li>root</li><li>run</li><li>side</li><li>side_right</li><li>swim_root</li><li>swim_forward</li><li>swim_backward</li><li>swim_left</li><li>swim_right</li><li>fall</li><li>jump</li><li>standjump</li><li>land</li><li>jet</li></ul>
    
    If the player moves in any direction then the animation sequence set using this method will be cancelled and the chosen mation-based sequence will take over.  This makes great for times when the Player cannot move, such as when mounted, or when it doesn't matter if the action sequence changes, such as waving and saluting.
    @tsexample
    // Place the player in a sitting position after being mounted
    %player.setActionThread( "sitting", true, true );
    @endtsexample
     */
       virtual bool setActionThread(( string name, bool hold=false, bool fsp=true )) {}
       /*! @brief Set the object to be controlled by this player
    
    It is possible to have the moves sent to the Player object from the GameConnection to be passed along to another object.  This happens, for example when a player is mounted to a vehicle.  The move commands pass through the Player and on to the vehicle (while the player remains stationary within the vehicle).  With setControlObject() you can have the Player pass along its moves to any object.  One possible use is for a player to move a remote controlled vehicle.  In this case the player does not mount the vehicle directly, but still wants to be able to control it.
    @param obj Object to control with this player
    @return True if the object is valid, false if not
    @see getControlObject()
    @see clearControlObject()
    @see GameConnection::setControlObject() */
       virtual bool setControlObject(( ShapeBase obj )) {}
       /*! @brief Get the current object we are controlling.
    
    @return ID of the ShapeBase object we control, or 0 if not controlling an object.
    @see setControlObject()
    @see clearControlObject() */
       virtual int getControlObject(()) {}
       /*! @brief Clears the player's current control object.
    
    Returns control to the player. This internally calls Player::setControlObject(0).
    @tsexample
    %player.clearControlObject();
    echo(%player.getControlObject()); //<-- Returns 0, player assumes control
    %player.setControlObject(%vehicle);
    echo(%player.getControlObject()); //<-- Returns %vehicle, player controls the vehicle now.
    @endtsexample
    @note If the player does not have a control object, the player will receive all moves from its GameConnection.  If you're looking to remove control from the player itself (i.e. stop sending moves to the player) use GameConnection::setControlObject() to transfer control to another object, such as a camera.
    @see setControlObject()
    @see getControlObject()
    @see GameConnection::setControlObject()
     */
       virtual void clearControlObject(()) {}
       /*! @brief Check if it is safe to dismount at this position.
    
    Internally this method casts a ray from oldPos to pos to determine if it hits the terrain, an interior object, a water object, another player, a static shape, a vehicle (exluding the one currently mounted), or physical zone.  If this ray is in the clear, then the player's bounding box is also checked for a collision at the pos position.  If this displaced bounding box is also in the clear, then checkDismountPoint() returns true.
    @param oldPos The player's current position
    @param pos The dismount position to check
    @return True if the dismount position is clear, false if not
    @note The player must be already mounted for this method to not assert.
     */
       virtual bool checkDismountPoint(( Point3F oldPos, Point3F pos )) {}
       virtual bool isWarstance(()) {}
       virtual void savePlayer() {}
       virtual void saveAndDestructPlayer() {}
       virtual int debugCastRay(( Point3F eyePosition, Point3F eyeVector )) {}
       /*! Tests only */
       virtual void Create_formation_and_invite_all(( int _formation_type )) {}
       /*! Tests only */
       virtual void Order_to_formation(( int _order_type )) {}
       virtual void setProcessTick(( bool t )) {}
       /*! Add new item to player inventory
    (type, quantity, quality, durability, createdDurability) */
       virtual bool inventoryAddItem(( int itemType, int quantity, int quality, int durability, int createdDurability )) {}
       /*! Remove item from player inventory
    (itemid) */
       virtual bool inventoryRemoveItem(( int itemid )) {}
       /*! Change player alignment for the value
    (delta) */
       virtual bool changeAlignment(( float delta )) {}
       /*! Teleport player to given location. */
       virtual bool TeleportTo(( GeoID::UnderlyingType rawGeoId )) {}
       /*! Teleport player to given terrain Id. */
       virtual bool jumpToTerrain(( int terId )) {}
       virtual void dumpCharacterDataStr(()) {}
       virtual void setGM(( bool in )) {}
       virtual void setCameraMode(( bool needCamera )) {}
       virtual void updateCameraSettings(( float cameraSpeed, bool newtonMode, bool newtonRotation )) {}
       virtual bool isInFlyingCameraMode(()) {}
       virtual string getFlyingCameraRotation(()) {}
       virtual int getGuildRole(()) {}
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  OutpostBunny : public Player {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  OutpostEvent {
      public:
    };
    
    class  QuestionNetEvent {
      public:
    };
    
    class  FerrymanDialogNetEvent {
      public:
    };
    
    class  FerrymanRequestWorldInfo {
      public:
    };
    
    class  FerrymanAnswerWorldInfo {
      public:
    };
    
    class  QuestNetEvent {
      public:
    };
    
    class  QuestTasksNetEvent {
      public:
    };
    
    class  ShowHelpNetEvent {
      public:
    };
    
    class  QuestSyncNetEvent {
      public:
    };
    
    class  BlueprintsEvent {
      public:
    };
    
    class  DeleteBlueprintEvent {
      public:
    };
    
    class  EventSkillToServer {
      public:
    };
    
    class  EventSkillToClient {
      public:
    };
    
    class  CmSkillsPlayer {
      public:
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /*!
       Optional global name of this object.
       
        */
       string name;
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /*!
       Optional name that may be used to lookup this object within a SimSet.
       
        */
       string internalName;
       /*!
       Group hierarchy parent of the object.
       
        */
       SimObject parentGroup;
       /*!
       Script class of object.
       
        */
       string class;
       /*!
       Script super-class of object.
       
        */
       string superClass;
       /*!
       Script class of object.
       
        */
       string className;
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /*!
       Whether the object is visible.
       
        */
       bool hidden;
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /*!
       Whether the object can be saved out. If false, the object is purely transient in nature.
       
        */
       bool canSave;
       /*!
       True if dynamic fields (added at runtime) should be saved. Defaults to true.
       
        */
       bool canSaveDynamicFields;
       /*!
       The universally unique identifier for the object.
       
        */
       pid persistentId;
       /*!
       True if this object is 4ever alone, perhaps it is an one side datablock.
       
        */
       bool local;
       /// @}
    
    };
    
    class  BoundedPlayersListEvent {
      public:
    };
    
    class  TrickmoveEvent {
      public:
    };
    
    class  GatherEvent {
      public:
    };
    
    class  MovablesListEvent {
      public:
    };
    
    class  InspectPatientHealthReportEvent {
      public:
    };
    
    class  LootEvent {
      public:
    };
    
    class  ClientGetSchoolInfoEvent {
      public:
    };
    
    class  ServerAnswerSchoolInfoEvent {
      public:
    };
    
    class  InspectATreeReportEvent {
      public:
    };
    
    class  AbilityCancelEvent {
      public:
    };
    
    class  AbilityCheckStatusEvent {
      public:
    };
    
    class  AbilityCooldownsEvent {
      public:
    };
    
    class  AbilityEvent {
      public:
    };
    
    class  AskClientForStartAbilityEvent {
      public:
    };
    
    class  AbilityReturnStatusEvent {
      public:
    };
    
    class  SlashCommandEvent {
      public:
    };
    
    class  GetSelectionEvent {
      public:
    };
    
    class  ClientRequestTimeLapsePointsEvent {
      public:
    };
    
    class  ClientSwitchTimeLapseToGmRequestEvent {
      public:
    };
    
    class  ClientJumpTimeLapseToGeoIdRequestEvent {
      public:
    };
    
    class  ClientJumpTimeLapseToPointRequestEvent {
      public:
    };
    
    class  ClientCheckServerOnlineRequestEvent {
      public:
    };
    
    class  ClientFindPathBetweenTerrainsRequestEvent {
      public:
    };
    
    class  ClientUpdateTimeLapseCameraPositionRequestEvent {
      public:
    };
    
    class  ServerAnswerTimeLapsePointsCoordEvent {
      public:
    };
    
    class  ServerTimeLapseBooleanAnswerEvent {
      public:
    };
    
    class  ServerFindPathBetweenTerrainsAnswerEvent {
      public:
    };
    
    class  HorseTrainingEvent {
      public:
    };
    
    /*!
    @brief Base functionality shared by all Vehicles (FlyingVehicle, HoverVehicle, WheeledVehicle.
    
    This object implements functionality shared by all Vehicle types, but should not be instantiated directly. Create a FlyingVehicle, HoverVehicle, or WheeledVehicle instead.
    @note The model used for any Vehicle must include a collision mesh at detail size -1.
    @ingroup Vehicles
     */
    class  Vehicle : public ShapeBase {
      public:
       /*!
       When this flag is set, the vehicle will ignore throttle changes.
       
        */
       bool disableMove;
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  AttachedObject : public StaticShape {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  TraderCart : public AttachedObject {
      public:
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  GameDateTimeEvent {
      public:
    };
    
    /*!
    @brief Base class for events used by node editors, like River
    
    Editor use only.
    
     */
    class  NodeListEvent {
      public:
    };
    
    class  SeasonEvent {
      public:
    };
    
    class  WeatherEvent {
      public:
    };
    
    class  CmCSEvent {
      public:
    };
    
    class  TerrainAttachEvent {
      public:
    };
    
    class  CmPatchEvent {
      public:
    };
    
    class  CmChangeEvent {
      public:
    };
    
    class  YoPatchTerrainAttachEvent {
      public:
    };
    
    class  YoPatchTerCachedRequestEvent {
      public:
    };
    
    class  YoPatchTerCachedResponceEvent {
      public:
    };
    
    class  YoPatchTerCachedDataRequestEvent {
      public:
    };
    
    class  YoPatchTerCachedChunkCountEvent {
      public:
    };
    
    class  YoPatchTerCachedDataCheckResponseEvent {
      public:
    };
    
    class  YoPatchTerChunkDataEvent {
      public:
    };
    
    class  ServerUUIDEvent {
      public:
    };
    
    /*!
    @brief Class responsible for the registration, transmission, and management of paths on client and server.
    
    For internal use only, not intended for use in TorqueScript or game development
    
    @internal
     */
    class  PathManagerEvent {
      public:
    };
    
    class  ServerCombatHitEvent {
      public:
    };
    
    /*!
    @brief A single joint, or knot, along a path. Should be stored inside a Path container object. A path markers can be
    one of three primary movement types: "normal", "Position Only", or "Kink". 
    @tsexample
    new path()
    ^{
         isLooping = "1";
    
         new Marker()
    ^^{
    ^^^seqNum = "0";
    ^^^type = "Normal";
    ^^^msToNext = "1000";
    ^^^smoothingType = "Spline";
    ^^^position = "-0.054708 -35.0612 234.802";
    ^^^rotation = "1 0 0 0";
          };
    
    ^};
    @endtsexample
    @see Path
    @ingroup enviroMisc
     */
    class  Marker : public SceneObject {
      public:
    
       /*! @name Misc
       @{ */
       /*! */
       /*!
       Marker position in sequence of markers on this path.
    
       
        */
       int seqNum;
       /*!
       Type of this marker/knot. A "normal" knot will have a smooth camera translation/rotation effect.
    "Position Only"will do the same for translations, leaving rotation un-touched.
    Lastly, a "Kink" means the rotation will take effect immediately for an abrupt rotation change.
    
       
        */
       MarkerKnotType type;
       /*!
       Milliseconds to next marker in sequence.
    
       
        */
       int msToNext;
       /*!
       Path smoothing at this marker/knot. "Linear"means no smoothing, while "Spline" means to smooth.
    
       
        */
       MarkerSmoothingType smoothingType;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  CharSelectEvent {
      public:
    };
    
    /*!
    @brief Internal event used for transmitting strings across the server.
    
    For internal use only, not intended for TorqueScript or game development
    
    @internal
     */
    class  NetStringEvent {
      public:
    };
    
    class  DisconnectEvent {
      public:
    };
    
    class  UnitToClientEvent {
      public:
    };
    
    /*!
    @brief This event is used inside by the connection and subclasses to message itself when sequencing events occur.
    
    Not intended for game development, for editors or internal use only.
    
     */
    class  ConnectionMessageEvent {
      public:
    };
    
    /*!
    @brief Legacy or soon to be locked down object.
    
    Not intended for game development, for editors or internal use only.
    
     */
    class  GhostAlwaysObjectEvent {
      public:
    };
    
    class  TerFallEvent {
      public:
    };
    
    /*!
    @brief The TerrainMaterial class orginizes the material settings for a single terrain material layer.
    
    @note You should not be creating TerrainMaterials by hand in code. All TerrainMaterials should be created in the editors, as intended by the system.
    
    @tsexample
    // Created by the Terrain Painter tool in the World Editor
    new TerrainMaterial()
    {
    ^internalName = "grass1";
    ^diffuseMap = "art/terrains/Test/grass1";
    ^detailMap = "art/terrains/Test/grass1_d";
    ^detailSize = "10";
    ^isManaged = "1";
    ^detailBrightness = "1";
    ^Enabled = "1";
    ^diffuseSize = "200";
    };
    @endtsexample
    
    @see Materials
    @ingroup enviroMisc
     */
    class  TerrainMaterial : public SimObject {
      public:
       /*!
        */
       ColorI proxyColor;
       /*!
        */
       ColorI mapColor;
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  SrvTunnelBlockCollisionVisualizeEvent {
      public:
    };
    
    class  TunnelManagerSyncVerificationEvent {
      public:
    };
    
    /*!
    @brief An event which signals the editors to undo the last action
    
    Not intended for game development, for editors or internal use only.
    
     */
    class  UndoAction : public SimObject {
      public:
       virtual void addToManager() {}
       virtual void undo() {}
       virtual void redo() {}
       /*!
       A brief description of the action, for UI representation of this undo/redo action.
       
        */
       string actionName;
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Undo actions which can be created as script objects.
    
    Not intended for game development, for editors or internal use only.
    
     */
    class  UndoScriptAction : public UndoAction {
      public:
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Represents a position, direction and field of view to render a scene from.
    
    A camera is typically manipulated by a GameConnection.  When set as the connection's control object, the camera handles all movement actions ($mvForwardAction, $mvPitch, etc.) just like a Player.
    @tsexample
    // Set an already created camera as the GameConnection's control object
    %connection.setControlObject(%camera);
    @endtsexample
    
    <h3>Methods of Operation</h3>
    
    The camera has two general methods of operation.  The first is the standard mode where the camera starts and stops its motion and rotation instantly.  This is the default operation of the camera and is used by most games.  It may be specifically set with Camera::setFlyMode() for 6 DoF motion.  It is also typically the method used with Camera::setOrbitMode() or one of its helper methods to orbit about a specific object (such as the Player's dead body) or a specific point.
    
    The second method goes under the name of Newton as it follows Newton's 2nd law of motion: F=ma.  This provides the camera with an ease-in and ease-out feel for both movement and rotation.  To activate this method for movement, either use Camera::setNewtonFlyMode() or set the Camera::newtonMode field to true.  To activate this method for rotation, set the Camera::newtonRotation to true.  This method of operation is not typically used in games, and was developed to allow for a smooth fly through of a game level while recording a demo video.  But with the right force and drag settings, it may give a more organic feel to the camera to games that use an overhead view, such as a RTS.
    
    There is a third, minor method of operation but it is not generally used for games.  This is when the camera is used with Torque's World Editor in Edit Orbit Mode.  When set, this allows the camera to rotate about a specific point in the world, and move towards and away from this point.  See Camera::setEditOrbitMode() and Camera::setEditOrbitPoint().  While in this mode, Camera::autoFit() may also be used.
    
    @tsexample
    // Create a camera in the level and set its position to a given spawn point.
    // Note: The camera starts in the standard fly mode.
    %cam = new Camera() {
       datablock = "Observer";
    };
    MissionCleanup.add( %cam );
    %cam.setTransform( %spawnPoint.getTransform() );
    @endtsexample
    
    @tsexample
    // Create a camera at the given spawn point for the specified
    // GameConnection i.e. the client.  Uses the standard
    // Sim::spawnObject() function to create the camera using the
    // defined default settings.
    // Note: The camera starts in the standard fly mode.
    function GameConnection::spawnCamera(%this, %spawnPoint)
    {
       // Set the control object to the default camera
       if (!isObject(%this.camera))
       {
          if (isDefined("$Game::DefaultCameraClass"))
             %this.camera = spawnObject($Game::DefaultCameraClass, $Game::DefaultCameraDataBlock);
       }
    
       // If we have a camera then set up some properties
       if (isObject(%this.camera))
       {
          // Make sure we're cleaned up when the mission ends
          MissionCleanup.add( %this.camera );
    
          // Make sure the camera is always in scope for the connection
          %this.camera.scopeToClient(%this);
    
          // Send all user input from the connection to the camera
          %this.setControlObject(%this.camera);
    
          if (isDefined("%spawnPoint"))
          {
             // Attempt to treat %spawnPoint as an object, such as a
             // SpawnSphere class.
             if (getWordCount(%spawnPoint) == 1 && isObject(%spawnPoint))
             {
                %this.camera.setTransform(%spawnPoint.getTransform());
             }
             else
             {
                // Treat %spawnPoint as an AngleAxis transform
                %this.camera.setTransform(%spawnPoint);
             }
          }
       }
    }
    @endtsexample
    
    <h3>Motion Modes</h3>
    
    Beyond the different operation methods, the Camera may be set to one of a number of motion modes.  These motion modes determine how the camera will respond to input and may be used to constrain how the Camera moves.  The CameraMotionMode enumeration defines the possible set of modes and the Camera's current may be obtained by using getMode().
    
    Some of the motion modes may be set using specific script methods.  These often provide additional parameters to set up the mode in one go.  Otherwise, it is always possible to set a Camera's motion mode using the controlMode property.  Just pass in the name of the mode enum.  The following table lists the motion modes, how to set them up, and what they offer:
    
    <table border='1' cellpadding='1'><tr><th>Mode</th><th>Set From Script</th><th>Input Move</th><th>Input Rotate</th><th>Can Use Newton Mode?</th></tr><tr><td>Stationary</td><td>controlMode property</td><td>No</td><td>No</td><td>No</td></tr><tr><td>FreeRotate</td><td>controlMode property</td><td>No</td><td>Yes</td><td>Rotate Only</td></tr><tr><td>Fly</td><td>setFlyMode()</td><td>Yes</td><td>Yes</td><td>Yes</td></tr><tr><td>OrbitObject</td><td>setOrbitMode()</td><td>Orbits object</td><td>Points to object</td><td>Move only</td></tr><tr><td>OrbitPoint</td><td>setOrbitPoint()</td><td>Orbits point</td><td>Points to location</td><td>Move only</td></tr><tr><td>TrackObject</td><td>setTrackObject()</td><td>No</td><td>Points to object</td><td>Yes</td></tr><tr><td>Overhead</td><td>controlMode property</td><td>Yes</td><td>No</td><td>Yes</td></tr><tr><td>EditOrbit (object selected)</td><td>setEditOrbitMode()</td><td>Orbits object</td><td>Points to object</td><td>Move only</td></tr><tr><td>EditOrbit (no object)</td><td>setEditOrbitMode()</td><td>Yes</td><td>Yes</td><td>Yes</td></tr></table>
    
    <h3>%Trigger Input</h3>
    
    Passing a move trigger ($mvTriggerCount0, $mvTriggerCount1, etc.) on to a Camera performs different actions depending on which mode the camera is in.  While in Fly, Overhead or EditOrbit mode, either trigger0 or trigger1 will cause a camera to move twice its normal movement speed.  You can see this in action within the World Editor, where holding down the left mouse button while in mouse look mode (right mouse button is also down) causes the Camera to move faster.
    
    Passing along trigger2 will put the camera into strafe mode.  While in this mode a Fly, FreeRotate or Overhead Camera will not rotate from the move input.  Instead the yaw motion will be applied to the Camera's x motion, and the pitch motion will be applied to the Camera's z motion.  You can see this in action within the World Editor where holding down the middle mouse button allows the user to move the camera up, down and side-to-side.
    
    While the camera is operating in Newton Mode, trigger0 and trigger1 behave slightly differently.  Here trigger0 activates a multiplier to the applied acceleration force as defined by speedMultiplier.  This has the affect of making the camera move up to speed faster.  trigger1 has the opposite affect by acting as a brake.  When trigger1 is active a multiplier is added to the Camera's drag as defined by brakeMultiplier.
    
    @see CameraData
    @see CameraMotionMode
    @see Camera::movementSpeed
    
    @ingroup BaseCamera
     */
    class  Camera : public ShapeBase {
      public:
       /*! Returns the current camera control mode.
    
    @see CameraMotionMode */
       virtual string getMode(()) {}
       /*! Get the camera's position in the world.
    
    @returns The position in the form of "x y z". */
       virtual string getPosition(()) {}
       /*! Get the camera's Euler rotation in radians.
    
    @returns The rotation in radians in the form of "x y z". */
       virtual string getRotation(()) {}
       /*! Set the camera's Euler rotation in radians.
    
    @param rot The rotation in radians in the form of "x y z".@note Rotation around the Y axis is ignored */
       virtual void setRotation(( Point3F rot )) {}
       /*! Get the camera's offset from its orbit or tracking point.
    
    The offset is added to the camera's position when set to CameraMode::OrbitObject.
    @returns The offset in the form of "x y z". */
       virtual string getOffset(()) {}
       /*! Set the camera's offset.
    
    The offset is added to the camera's position when set to CameraMode::OrbitObject.
    @param offset The distance to offset the camera by in the form of "x y z". */
       virtual void setOffset(( Point3F offset )) {}
       /*! Set the camera to orbit around the given object, or if none is given, around the given point.
    
    @param orbitObject The object to orbit around.  If no object is given (0 or blank string is passed in) use the orbitPoint instead
    @param orbitPoint The point to orbit around when no object is given.  In the form of "x y z ax ay az aa" such as returned by SceneObject::getTransform().
    @param minDistance The minimum distance allowed to the orbit object or point.
    @param maxDistance The maximum distance allowed from the orbit object or point.
    @param initDistance The initial distance from the orbit object or point.
    @param ownClientObj [optional] Are we orbiting an object that is owned by us?  Default is false.
    @param offset [optional] An offset added to the camera's position.  Default is no offset.
    @param locked [optional] Indicates the camera does not receive input from the player.  Default is false.
    @see Camera::setOrbitObject()
    @see Camera::setOrbitPoint()
     */
       virtual void setOrbitMode(( GameBase orbitObject, TransformF orbitPoint, float minDistance, float maxDistance, float initDistance, bool ownClientObj=false, Point3F offset=Point3F(0.0f, 0.0f, 0.0f), bool locked=false )) {}
       /*! Set the camera to orbit around a given object.
    
    @param orbitObject The object to orbit around.
    @param rotation The initial camera rotation about the object in radians in the form of "x y z".
    @param minDistance The minimum distance allowed to the orbit object or point.
    @param maxDistance The maximum distance allowed from the orbit object or point.
    @param initDistance The initial distance from the orbit object or point.
    @param ownClientObject [optional] Are we orbiting an object that is owned by us?  Default is false.
    @param offset [optional] An offset added to the camera's position.  Default is no offset.
    @param locked [optional] Indicates the camera does not receive input from the player.  Default is false.
    @returns false if the given object could not be found.
    @see Camera::setOrbitMode()
     */
       virtual bool setOrbitObject(( GameBase orbitObject, VectorF rotation, float minDistance, float maxDistance, float initDistance, bool ownClientObject=false, Point3F offset=Point3F(0.0f, 0.0f, 0.0f), bool locked=false )) {}
       /*! Set the camera to orbit around a given point.
    
    @param orbitPoint The point to orbit around.  In the form of "x y z ax ay az aa" such as returned by SceneObject::getTransform().
    @param minDistance The minimum distance allowed to the orbit object or point.
    @param maxDistance The maximum distance allowed from the orbit object or point.
    @param initDistance The initial distance from the orbit object or point.
    @param offset [optional] An offset added to the camera's position.  Default is no offset.
    @param locked [optional] Indicates the camera does not receive input from the player.  Default is false.
    @see Camera::setOrbitMode()
     */
       virtual void setOrbitPoint(( TransformF orbitPoint, float minDistance, float maxDistance, float initDistance, Point3F offset=Point3F(0.0f, 0.0f, 0.0f), bool locked=false )) {}
       /*! Set the camera to track a given object.
    
    @param trackObject The object to track.
    @param offset [optional] An offset added to the camera's position.  Default is no offset.
    @returns false if the given object could not be found.
     */
       virtual bool setTrackObject(( GameBase trackObject, Point3F offset=Point3F(0.0f, 0.0f, 0.0f) )) {}
       /*! Set the camera to fly freely.
    
    Allows the camera to have 6 degrees of freedom.  Provides for instantaneous motion and rotation unless one of the Newton fields has been set to true.  See Camera::newtonMode and Camera::newtonRotation.
     */
       virtual void setFlyMode(()) {}
       /*! Set the camera to fly freely, but with ease-in and ease-out.
    
    This method allows for the same 6 degrees of freedom as Camera::setFlyMode() but activates the ease-in and ease-out on the camera's movement.  To also activate Newton mode for the camera's rotation, set Camera::newtonRotation to true. */
       virtual void setNewtonFlyMode(( bool newtonMode=true )) {}
       /*! Is this a Newton Fly mode camera with damped rotation?
    
    @returns true if the camera uses a damped rotation.  i.e. Camera::newtonRotation is set to true.
     */
       virtual bool isRotationDamped(()) {}
       /*! Get the angular velocity for a Newton mode camera.
    
    @returns The angular velocity in the form of "x y z".
    @note Only returns useful results when Camera::newtonRotation is set to true. */
       virtual string getAngularVelocity(()) {}
       /*! Set the angular velocity for a Newton mode camera.
    
    @param velocity The angular velocity infor form of "x y z".
    @note Only takes affect when Camera::newtonRotation is set to true. */
       virtual void setAngularVelocity(( VectorF velocity )) {}
       /*! Set the angular force for a Newton mode camera.
    
    @param force The angular force applied when attempting to rotate the camera.@note Only takes affect when Camera::newtonRotation is set to true. */
       virtual void setAngularForce(( float force )) {}
       /*! Set the angular drag for a Newton mode camera.
    
    @param drag The angular drag applied while the camera is rotating.@note Only takes affect when Camera::newtonRotation is set to true. */
       virtual void setAngularDrag(( float drag )) {}
       /*! Set the mass for a Newton mode camera.
    
    @param mass The mass used during ease-in and ease-out calculations.@note Only used when Camera is in Newton mode. */
       virtual void setMass(( float mass )) {}
       /*! Get the velocity for the camera.
    
    @returns The camera's velocity in the form of "x y z".@note Only useful when the Camera is in Newton mode. */
       virtual string getVelocity(()) {}
       /*! Set the velocity for the camera.
    
    @param velocity The camera's velocity in the form of "x y z".@note Only affects the Camera when in Newton mode. */
       virtual void setVelocity(( VectorF velocity )) {}
       /*! Set the drag for a Newton mode camera.
    
    @param drag The drag applied to the camera while moving.@note Only used when Camera is in Newton mode. */
       virtual void setDrag(( float drag )) {}
       /*! Set the force applied to a Newton mode camera while moving.
    
    @param force The force applied to the camera while attempting to move.@note Only used when Camera is in Newton mode. */
       virtual void setFlyForce(( float force )) {}
       /*! Set the Newton mode camera speed multiplier when trigger[sImageTrigger0] is active.
    
    @param multiplier The speed multiplier to apply.@note Only used when Camera is in Newton mode. */
       virtual void setSpeedMultiplier(( float multiplier )) {}
       /*! Set the Newton mode camera brake multiplier when trigger[sImageTrigger1] is active.
    
    @param multiplier The brake multiplier to apply.@note Only used when Camera is in Newton mode. */
       virtual void setBrakeMultiplier(( float multiplier )) {}
       /*! Point the camera at the specified position.  Does not work in Orbit or Track modes.
    
    @param point The position to point the camera at. */
       virtual void lookAt(( Point3F point )) {}
       virtual bool isGM(()) {}
       virtual void setGM(( bool in )) {}
    
       /*! @name Camera
       @{ */
       /*! */
       /*!
       The current camera control mode.
       
        */
       CameraMotionMode controlMode;
       /*!
       @brief Camera movement speed in units/s (typically m/s), with a base value of 40.
    
    Used in the following camera modes:
    - Edit Orbit Mode
    - Fly Mode
    - Overhead Mode
    @ingroup BaseCamera
    
       
        */
       float movementSpeed;
       /// @}
    
    
       /*! @name Camera: Newton Mode
       @{ */
       /*! */
       /*!
       Apply smoothing (acceleration and damping) to camera movements.
       
        */
       bool newtonMode;
       /*!
       Apply smoothing (acceleration and damping) to camera rotations.
       
        */
       bool newtonRotation;
       /*!
       The camera's mass (Newton mode only).  Default value is 10.
       
        */
       float mass;
       /*!
       Drag on camera when moving (Newton mode only).  Default value is 2.
       
        */
       float drag;
       /*!
       Force applied on camera when asked to move (Newton mode only).  Default value is 500.
       
        */
       float force;
       /*!
       Drag on camera when rotating (Newton mode only).  Default value is 2.
       
        */
       float angularDrag;
       /*!
       Force applied on camera when asked to rotate (Newton mode only).  Default value is 100.
       
        */
       float angularForce;
       /*!
       Speed multiplier when triggering the accelerator (Newton mode only).  Default value is 2.
       
        */
       float speedMultiplier;
       /*!
       Speed multiplier when triggering the brake (Newton mode only).  Default value is 2.
       
        */
       float brakeMultiplier;
       /// @}
    
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Level object which defines the boundaries of the level.
    
    This is a simple box with starting points, width, depth, and height. It does not have any default functionality. Instead, when objects hit the boundaries certain script callbacks will be made allowing you to control the reaction.
    
    @tsexample
    new MissionArea(GlobalMissionArea)
    {
    ^  Area = "-152 -352 1008 864";
    ^  flightCeiling = "300";
    ^  flightCeilingRange = "20";
    ^  canSaveDynamicFields = "1";
    ^^ enabled = "1";
    ^^ TypeBool locked = "false";
    };
    @endtsexample
    
    @ingroup enviroMisc
     */
    class  MissionArea : public NetObject {
      public:
       /*! Returns 4 fields: starting x, starting y, extents x, extents y.
     */
       virtual string getArea(()) {}
       /*! @brief - Defines the size of the MissionArea
    
    param x Starting X coordinate position for MissionArea
    param y Starting Y coordinate position for MissionArea
    param width New width of the MissionArea
    param height New height of the MissionArea
    @note Only the server object may be set.
     */
       virtual void setArea(( int x, int y, int width, int height )) {}
       /*! Intended as a helper to developers and editor scripts.
    Force trigger an inspectPostApply. This will transmit material and other fields ( not including nodes ) to client objects. */
       virtual void postApply(()) {}
    
       /*! @name Dimensions
       @{ */
       /*! */
       /*!
       Four corners (X1, X2, Y1, Y2) that makes up the level's boundaries
       
        */
       RectI area;
       /*!
       Represents the top of the mission area, used by FlyingVehicle. 
       
        */
       float flightCeiling;
       /*!
       Distance from ceiling before FlyingVehicle thrust is cut off. 
       
        */
       float flightCeilingRange;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief This class is used for creating any type of game object, assigning it a class, datablock, and even a function when it is spawned.
    
    Torque 3D uses a simple spawn system, which can be easily modified to spawn any kind of object (of any class). Each new level already contains at least one SpawnSphere, which is represented by a green octahedron in stock Torque 3D. The spawnClass will determine the object type, such as Player, AIPlayer, etc. The spawnDataBlock will provide this specific instance of the creation with a pre-defined datablock. The really powerful feature of this clas is utilize by the spawnScript field. Through this, you can define a simple script (multiple lines) that will be executed once the object has been spawned.
    
    @tsexample
    new SpawnSphere(DefaultSpawnSphere)
    {
       spawnClass = "Player";
       spawnDatablock = "DefaultPlayerData";
       spawnScript = "echo(\"Object Spawned\");"; // Note the escape sequence \ in front of quotes
       spawnProperties = "name = \"Bob\";lifeTotal = 3;"; // Note the escape sequence \ in front of quotes
       autoSpawn = "0";
        = "1";
       sphereWeight = "1";
       indoorWeight = "100";
       outdoorWeight = "100";
       dataBlock = "SpawnSphereMarker";
       position = "-0.77266 -19.882 17.8153";
       rotation = "1 0 0 0";
       scale = "1 1 1";
       canSave = "1";
       canSaveDynamicFields = "1";
    };
    
    // In the above example, the following two lines of code will execute after spawning
    echo("Object Spawned");
    echo("Hello World");
    @endtsexample
    
    @see MissionMarker
    
    @see MissionMarkerData
    
    @ingroup gameObjects
    @ingroup enviroMisc
     */
    class  SpawnSphere : public MissionMarker {
      public:
          /*! Called when the SpawnSphere is being created.
    @param objectId The unique SimObjectId generated when SpawnSphere is created
     */
          void onAdd( int objectId );
    
       virtual int spawnObject() {}
    
       /*! @name Spawn
       @{ */
       /*! */
       /*!
       Class assigned to object when created, such as Player, or AIPlayer
       
        */
       string spawnClass;
       /*!
       Predefined datablock assigned to the object when created
       
        */
       string spawnDatablock;
       /*!
       String containing ; delimited properties that are set at the time of spawning
       
        */
       string spawnProperties;
       /*!
       Command to execute when spawning an object. New object id is stored in $SpawnObject.  Max 255 characters.
       
        */
       string spawnScript;
       /*!
       Flag to spawn object as soon as SpawnSphere is created, true to enable or false to disabled
       
        */
       bool autoSpawn;
       /// @}
    
    
       /*! @name Dimensions
       @{ */
       /*! */
       /*!
       Determines the size of the sphere in which the object will spawn
       
        */
       float ;
       /// @}
    
    
       /*! @name Weight
       @{ */
       /*! */
       /*!
       Deprecated
       
        */
       float sphereWeight;
       /*!
       Deprecated
       
        */
       float indoorWeight;
       /*!
       Deprecated
       
        */
       float outdoorWeight;
       /// @}
    
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A camera that moves along a path. The camera can then be made to travel along this path forwards or backwards.
    
    A camera's path is made up of knots, which define a position, rotation and speed for the camera.  Traversal from one knot to another may be either linear or using a Catmull-Rom spline.  If the knot is part of a spline, then it may be a normal knot or defined as a kink.  Kinked knots are a hard transition on the spline rather than a smooth one.  A knot may also be defined as a position only.  In this case the knot is treated as a normal knot but is ignored when determining how to smoothly rotate the camera while it is travelling along the path (the algorithm moves on to the next knot in the path for determining rotation).
    
    The datablock field for a PathCamera is a previously created PathCameraData, which acts as the interface between the script and the engine for this PathCamera object.
    
    @see PathCameraData
    @tsexample
    %newPathCamera = new PathCamera()
    {
      dataBlock = LoopingCam;
      position = "0 0 300 1 0 0 0";
    };
    @endtsexample
    @ingroup PathCameras
     */
    class  PathCamera : public ShapeBase {
      public:
       virtual Script onNode(( string this, string node )) {}
          /*! A script callback that indicates the path camera has arrived at a specific node in its path.  Server side only.
    @param Node Unique ID assigned to this node.
     */
          void onNode( string node );
    
       /*! Set the current position of the camera along the path.
    @param position Position along the path, from 0.0 (path start) - 1.0 (path end), to place the camera.
    @tsexample
    // Set the camera on a position along its path from 0.0 - 1.0.
    %position = "0.35";
    
    // Force the pathCamera to its new position along the path.
    %pathCamera.setPosition(%position);
    @endtsexample
     */
       virtual void setPosition(( float position=0.0f )) {}
       /*! @brief Set the movement target for this camera along its path.
    
    The camera will attempt to move along the path to the given target in the direction provided by setState() (the default is forwards).  Once the camera moves past this target it will come to a stop, and the target state will be cleared.
    @param position Target position, between 0.0 (path start) and 1.0 (path end), for the camera to move to along its path.
    @tsexample
    // Set the position target, between 0.0 (path start) and 1.0 (path end), for this camera to move to.
    %position = "0.50";
    
    // Inform the pathCamera of the new target position it will move to.
    %pathCamera.setTarget(%position);
    @endtsexample
     */
       virtual void setTarget(( float position=1.0f )) {}
       /*! Set the movement state for this path camera.
    @param newState New movement state type for this camera. Forward, Backward or Stop.
    @tsexample
    // Set the state type (forward, backward, stop).
    // In this example, the camera will travel from the first node
    // to the last node (or target if given with setTarget())
    %state = "forward";
    
    // Inform the pathCamera to change its movement state to the defined value.
    %pathCamera.setState(%state);
    @endtsexample
     */
       virtual void setState(( string newState="forward" )) {}
       /*! @brief Clear the camera's path and set the camera's current transform as the start of the new path.
    
    What specifically occurs is a new knot is created from the camera's current transform.  Then the current path is cleared and the new knot is pushed onto the path.  Any previous target is cleared and the camera's movement state is set to Forward.  The camera is now ready for a new path to be defined.
    @param speed Speed for the camera to move along its path after being reset.
    @tsexample
    //Determine the new movement speed of this camera. If not set, the speed will default to 1.0.
    %speed = "0.50";
    
    // Inform the path camera to start a new path at// the camera's current position, and set the new // path's speed value.
    %pathCamera.reset(%speed);
    @endtsexample
     */
       virtual void reset(( float speed=1.0f )) {}
       /*! @brief Adds a new knot to the back of a path camera's path.
    @param transform Transform for the new knot.  In the form of "x y z ax ay az aa" such as returned by SceneObject::getTransform()
    @param speed Speed setting for this knot.
    @param type Knot type (Normal, Position Only, Kink).
    @param path %Path type (Linear, Spline).
    @tsexample
    // Transform vector for new knot. (Pos_X Pos_Y Pos_Z Rot_X Rot_Y Rot_Z Angle)
    %transform = "15.0 5.0 5.0 1.4 1.0 0.2 1.0"
    
    // Speed setting for knot.
    %speed = "1.0"
    
    // Knot type. (Normal, Position Only, Kink)
    %type = "Normal";
    
    // Path Type. (Linear, Spline)
    %path = "Linear";
    
    // Inform the path camera to add a new knot to the back of its path
    %pathCamera.pushBack(%transform,%speed,%type,%path);
    @endtsexample
     */
       virtual void pushBack(( TransformF transform, float speed=1.0, string type="Normal", string path="Linear" )) {}
       virtual void updateKnot(( int index, TransformF transform, float speed=1.0, string type="Normal", string path="Linear" )) {}
       /*! @brief Adds a new knot to the front of a path camera's path.
    @param transform Transform for the new knot. In the form of "x y z ax ay az aa" such as returned by SceneObject::getTransform()
    @param speed Speed setting for this knot.
    @param type Knot type (Normal, Position Only, Kink).
    @param path %Path type (Linear, Spline).
    @tsexample
    // Transform vector for new knot. (Pos_X,Pos_Y,Pos_Z,Rot_X,Rot_Y,Rot_Z,Angle)
    %transform = "15.0 5.0 5.0 1.4 1.0 0.2 1.0"
    
    // Speed setting for knot.
    %speed = "1.0";
    
    // Knot type. (Normal, Position Only, Kink)
    %type = "Normal";
    
    // Path Type. (Linear, Spline)
    %path = "Linear";
    
    // Inform the path camera to add a new knot to the front of its path
    %pathCamera.pushFront(%transform, %speed, %type, %path);
    @endtsexample
     */
       virtual void pushFront(( TransformF transform, float speed=1.0, string type="Normal", string path="Linear" )) {}
       /*! Removes the knot at the front of the camera's path.
    @tsexample
    // Remove the first knot in the camera's path.
    %pathCamera.popFront();
    @endtsexample
     */
       virtual void popFront(()) {}
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Physical Zones are areas that modify the player's gravity and/or velocity and/or applied force.
    
    The datablock properties determine how the physics, velocity and applied forces affect a player who enters this zone.
    @tsexample
    new PhysicalZone(Team1JumpPad) {
    velocityMod = "1";gravityMod = "0";
    appliedForce = "0 0 20000";
    polyhedron = "0.0000000 0.0000000 0.0000000 1.0000000 0.0000000 0.0000000 0.0000000 -1.0000000 0.0000000 0.0000000 0.0000000 1.0000000";
    position = "273.559 -166.371 249.856";
    rotation = "0 0 1 13.0216";
    scale = "8 4.95 28.31";
    isRenderEnabled = "true";
    canSaveDynamicFields = "1";
    enabled = "1";
    };
    @endtsexample
    
    @ingroup enviroMisc
     */
    class  PhysicalZone : public SceneObject {
      public:
       /*! Activate the physical zone's effects.
    @tsexample
    // Activate effects for a specific physical zone.
    %thisPhysicalZone.activate();
    @endtsexample
    @ingroup Datablocks
     */
       virtual void activate(()) {}
       /*! Deactivate the physical zone's effects.
    @tsexample
    // Deactivate effects for a specific physical zone.
    %thisPhysicalZone.deactivate();
    @endtsexample
    @ingroup Datablocks
     */
       virtual void deactivate(()) {}
    
       /*! @name Misc
       @{ */
       /*! */
       /*!
       Multiply velocity of objects entering zone by this value every tick.
       
        */
       float velocityMod;
       /*!
       Gravity in PhysicalZone. Multiplies against standard gravity.
       
        */
       float gravityMod;
       /*!
       Three-element floating point value representing forces in three axes to apply to objects entering PhysicalZone.
       
        */
       Point3F appliedForce;
       /*!
       The polyhedron type is really a quadrilateral and consists of a cornerpoint followed by three vectors representing the edges extending from the corner.
       
        */
       floatList polyhedron;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief An object that culls the rendering of everything contained within it.
    
    This is one of two objects used by the manual culling system Torque 3D provides, the other being Portal. When a Zone is placed in a level, all rendering within the zone is hidden from view when the camera is outside it. When inside, all rendering outside the zone is hidden. This is an excellent way to optimize large levels and complex geometry.
    
    You can attach a Portal a zone. This allows you to view what is rendered in the Zone (or what is rendered outside if you are in the zone), like a window. The larger the Portal, the more you can see through a zone.
    
    @tsexample
    // Example declaration of a Zone
    new Zone(TestZone)
    {
    ^soundAmbience = "AudioAmbienceInside";
    ^position = "3.61793 -1.01945 14.7442";
    ^rotation = "1 0 0 0";
    ^scale = "10 10 10";
    ^canSave = "1";
    ^canSaveDynamicFields = "1";
    };
    @endtsexample
    
    @see Portal
    @ingroup enviroMisc
     */
    class  Zone : public SceneObject {
      public:
       /*! Get the unique numeric ID of the zone in its scene.
    
    @return The ID of the zone. */
       virtual int getZoneId(()) {}
       /*! Dump a list of all objects assigned to the zone to the console as well as a list of all connected zone spaces.
    
    @param updateFirst Whether to update the contents of the zone before dumping.  Since zoning states of objects are updated on demand, the zone contents can be outdated. */
       virtual void dumpZoneState(( bool updateFirst=true )) {}
    
       /*! @name Internal
       @{ */
       /*! */
       /*!
       For internal use only.
       
        */
       string plane;
       /*!
       For internal use only.
       
        */
       string point;
       /*!
       For internal use only.
       
        */
       string edge;
       /// @}
    
    
       /*! @name Lighting
       @{ */
       /*! */
       /*!
       Whether to use #ambientLightColor for ambient lighting in this zone or the global ambient color.
       
        */
       bool useAmbientLightColor;
       /*!
       Color of ambient lighting in this zone.
    
    Only used if #useAmbientLightColor is true.
       
        */
       ColorF ambientLightColor;
       /// @}
    
    
       /*! @name Zoning
       @{ */
       /*! */
       /*!
       ID of group the zone is part of.
       
        */
       int zoneGroup;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief An object that provides a "window" into a zone, allowing a viewer to see what's rendered in the zone.
    
    This is one of two objects used by the manual culling system Torque 3D provides, the other being Zone. When a Zone is placed in a level, all rendering within the zone is hidden from view when the camera is outside it. When inside, all rendering outside the zone is hidden. This is an excellent way to optimize large levels and complex geometry.
    
    You can attach a Portal a zone. This allows you to view what is rendered in the Zone (or what is rendered outside if you are in the zone), like a window. The larger the Portal, the more you can see through a zone.
    
    @tsexample
    // Example declaration of a Portal
    new Portal( PortalToTestZone )
    {
       position = "12.8467 -4.02246 14.8017";
    ^ rotation = "0 0 -1 97.5085";
    ^ scale = "1 0.25 1";
    ^ canSave = "1";
    ^ canSaveDynamicFields = "1";
    };
    @endtsexample
    
    @see Zone
    @ingroup enviroMisc
     */
    class  Portal : public Zone {
      public:
       /*! Test whether the portal connects interior zones only.
    
    @return True if the portal is an interior portal. */
       virtual bool isInteriorPortal(()) {}
       /*! Test whether the portal connects interior zones to the outdoor zone.
    
    @return True if the portal is an exterior portal. */
       virtual bool isExteriorPortal(()) {}
    
       /*! @name Zoning
       @{ */
       /*! */
       /*!
       Whether one can view through the front-side of the portal.
       
        */
       bool frontSidePassable;
       /*!
       Whether one can view through the back-side of the portal.
       
        */
       bool backSidePassable;
       /// @}
    
    
       /*! @name Internal
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Lighting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Zoning
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A collection of arbitrary objects which can be allocated and manipulated as a group.
    
    %Prefab always points to a (.prefab) file which defines its objects. In fact more than one %Prefab can reference this file and both will update if the file is modified.
    
    %Prefab is a very simple object and only exists on the server. When it is created it allocates children objects by reading the (.prefab) file like a list of instructions.  It then sets their transform relative to the %Prefab and Torque networking handles the rest by ghosting the new objects to clients. %Prefab itself is not ghosted.
    
     */
    class  Prefab : public SceneObject {
      public:
          /*! Called when the prefab file is loaded and children objects are created.
    @param children SimGroup containing all children objects.
     */
          void onLoad( SimGroup children );
    
    
       /*! @name Prefab
       @{ */
       /*! */
       /*!
       (.prefab) File describing objects within this prefab.
       
        */
       filename fileName;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A Trigger is a volume of space that initiates script callbacks when objects pass through the Trigger.
    
    TriggerData provides the callbacks for the Trigger when an object enters, stays inside or leaves the Trigger's volume.
    
    @see TriggerData
    @ingroup gameObjects
     */
    class  Trigger : public GameBase {
      public:
          /*! @brief Called when the Trigger is being created.
    
    @param objectId the object id of the Trigger being created
     */
          void onAdd( int objectId );
    
          /*! @brief Called just before the Trigger is deleted.
    
    @param objectId the object id of the Trigger being deleted
     */
          void onRemove( int objectId );
    
       /*! @brief Get the number of objects that are within the Trigger's bounds.
    
    @see getObject()
     */
       virtual int getNumObjects(()) {}
       /*! @brief Retrieve the requested object that is within the Trigger's bounds.
    
    @param index Index of the object to get (range is 0 to getNumObjects()-1)
    @returns The SimObjectID of the object, or -1 if the requested index is invalid.
    @see getNumObjects()
     */
       virtual int getObject(( int index )) {}
       /*!
       @brief Defines a non-rectangular area for the trigger.
    
    Rather than the standard rectangular bounds, this optional parameter defines a quadrilateral trigger area.  The quadrilateral is defined as a corner point followed by three vectors representing the edges extending from the corner.
    
       
        */
       floatList polyhedron;
       /*!
       The command to execute when an object enters this trigger. Object id stored in %%obj. Maximum 1023 characters.
       
        */
       string enterCommand;
       /*!
       The command to execute when an object leaves this trigger. Object id stored in %%obj. Maximum 1023 characters.
       
        */
       string leaveCommand;
       /*!
       The command to execute while an object is inside this trigger. Maximum 1023 characters.
       
        */
       string tickCommand;
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A static object derived from a 3D model file and placed within the game world.
    
    TSStatic is the most basic 3D shape in Torque.  Unlike StaticShape it doesn't make use of a datablock.  It derrives directly from SceneObject.  This makes TSStatic extremely light weight, which is why the Tools use this class when you want to drop in a DTS or DAE object.
    
    While a TSStatic doesn't provide any motion -- it stays were you initally put it -- it does allow for a single ambient animation sequence to play when the object is first added to the scene.
    
    @tsexample
    new TSStatic(Team1Base) {
       shapeName = "art/shapes/desertStructures/station01.dts";
       playAmbient = "1";
       receiveSunLight = "1";
       receiveLMLighting = "1";
       useCustomAmbientLighting = "0";
       customAmbientLighting = "0 0 0 1";
       collisionType = "Visible Mesh";
       decalType = "Collision Mesh";
       allowPlayerStep = "1";
       renderNormals = "0";
       forceDetail = "-1";
       position = "315.18 -180.418 244.313";
       rotation = "0 0 1 195.952";
       scale = "1 1 1";
       isRenderEnabled = "true";
       canSaveDynamicFields = "1";
    };
    @endtsexample
    @ingroup gameObjects
     */
    class  TSStatic : public SceneObject {
      public:
       /*! Get the name of the indexed shape material.
    @param index index of the material to get (valid range is 0 - getTargetCount()-1).
    @return the name of the indexed material.
    @see getTargetCount()
     */
       virtual string getTargetName(( int index=0 )) {}
       /*! Get the number of materials in the shape.
    @return the number of materials in the shape.
    @see getTargetName()
     */
       virtual int getTargetCount(()) {}
       /*! @brief Get the model filename used by this shape.
    
    @return the shape filename
    
    @tsexample
    // Acquire the model filename used on this shape.
    %modelFilename = %obj.getModelFile();
    @endtsexample
     */
       virtual string getModelFile(()) {}
    
       /*! @name Media
       @{ */
       /*! */
       /*!
       %Path and filename of the model file (.DTS, .DAE) to use for this TSStatic.
       
        */
       filename shapeName;
       /// @}
    
    
       /*! @name Rendering
       @{ */
       /*! */
       /*!
       Enables automatic playing of the animation sequence named "ambient" (if it exists) when the TSStatic is loaded.
       
        */
       bool playAmbient;
       /*!
       Enables specify animation sequence name contolled by playAmbient. ("ambient" by default)
       
        */
       string ambientAnimName;
       /*!
       Enables detailed culling of meshes within the TSStatic. Should only be used with large complex shapes like buildings which contain many submeshes.
       
        */
       bool meshCulling;
       /*!
       Enables translucent sorting of the TSStatic by its origin instead of the bounds.
       
        */
       bool originSort;
       /// @}
    
    
       /*! @name Collision
       @{ */
       /*! */
       /*!
       The type of mesh data to use for collision queries.
       
        */
       TSMeshType collisionType;
       /*!
       The type of mesh data used to clip decal polygons against.
       
        */
       TSMeshType decalType;
       /*!
       @brief Allow a Player to walk up sloping polygons in the TSStatic (based on the collisionType).
    
    When set to false, the slightest bump will stop the player from walking on top of the object.
    
       
        */
       bool allowPlayerStep;
       /// @}
    
    
       /*! @name Debug
       @{ */
       /*! */
       /*!
       Forces rendering to a particular detail level.
       
        */
       int forceDetail;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Defines a precipitation based storm (IE: rain, snow, etc.).
    
    @tsexample
    // The following is added to a level file (.mis) by the World Editor
    new Precipitation(TheRain) {
       dropSize = "0.5";
       splashSize = "0.5";
       splashMS = "250";
       animateSplashes = "1";
       dropAnimateMS = "0";
       fadeDist = "0";
       fadeDistEnd = "0";
       useTrueBillboards = "0";
       useLighting = "0";
       glowIntensity = "0 0 0 0";
       reflect = "0";
       rotateWithCamVel = "1";
       doCollision = "1";
       hitPlayers = "0";
       hitVehicles = "0";
       followCam = "1";
       useWind = "0";
       minSpeed = "1.5";
       maxSpeed = "2";
       minMass = "0.75";
       maxMass = "0.85";
       useTurbulence = "0";
       maxTurbulence = "0.1";
       turbulenceSpeed = "0.2";
       numDrops = "1024";
       boxWidth = "200";
       boxHeight = "100";
       dataBlock = "HeavyRain";
    };
    @endtsexample
    @ingroup FX
     */
    class  Precipitation : public GameBase {
      public:
       /*! Sets how many drops are present at once.
    @tsexample
    // The percentage, from 0.0f to 1.0f, of the drops to display at once.
    %percentage = 0.5f;
    
    // Set the percentage by calling the method.
    %Precipitation.setPercentage(%percentage);
    @endtsexample
     */
       virtual void setPercentage(( float percentage=1.0f )) {}
       /*! Adjusts the droplet count and overall length of the Precipitation effect.
    @tsexample
    // The percentage, from 0.0f to 1.0f, of the drops to display at once.
    %percentage = 0.5;
    
    // The length of time for the Precipitation effect to last. Will be multiplied by 1000 to get the milliseconds.
    %length = 5.0;
    
    // Set the percentage and time by calling the method.
    %Precipitation.modifyStorm(%percentage , %length);
    @endtsexample
     */
       virtual void modifyStorm(( float percentage=1.0f, float length=5.0f )) {}
       /*! This is used to smoothly change the turbulence
    over a desired time period. Setting ms to zero
    will cause the change to be instantaneous. Setting
    max zero will disable turbulence.
    @tsexample
    //Set the turbulence value. Set to 0 to disable turbulence.
    %turbulence = 0.5;
    
    // The speed of the turbulance effect.
    %speed = 5.0;
    
    // The length of time for the turbulence to last. Will be multiplied by 1000 to get the milliseconds.
    %seconds = 5.0;
    
    // Set the percentage and time by calling the method.
    %Precipitation.setTurbulence(%turbulence , %speed , %seconds);
    @endtsexample
     */
       virtual void setTurbulence(( float max=1.0f, float speed=5.0f, float seconds=5.0 )) {}
    
       /*! @name Precipitation
       @{ */
       /*! */
       /*!
       Number of drops allowed to exists in the precipitation box at any one time.
       
        */
       int numDrops;
       /*!
       Width of precipitation box.
       
        */
       float boxWidth;
       /*!
       Height of precipitation box.
       
        */
       float boxHeight;
       /// @}
    
    
       /*! @name Rendering
       @{ */
       /*! */
       /*!
       Size of each drop of precipitation. This will scale the texture.
       
        */
       float dropSize;
       /*!
       Size of each splash animation for when a drop collides.
       
        */
       float splashSize;
       /*!
       Life of splashes in milliseconds.
       
        */
       int splashMS;
       /*!
       Check to enable splash animation on collision.
       
        */
       bool animateSplashes;
       /*!
       If greater than zero, will animate the drops from the frames in the texture.
       
        */
       int dropAnimateMS;
       /*!
       The distance at which fading of the drops begins.
       
        */
       float fadeDist;
       /*!
       The distance at which fading of the particles ends.
       
        */
       float fadeDistEnd;
       /*!
       Check to make drops true (non axis-aligned) billboards.
       
        */
       bool useTrueBillboards;
       /*!
       Check to enable shading of the drops and splashes by the sun color.
       
        */
       bool useLighting;
       /*!
       Set to 0 to disable the glow or or use it to control the intensity of each channel.
       
        */
       ColorF glowIntensity;
       /*!
       This enables the precipitation to be rendered during reflection passes. This is expensive.
       
        */
       bool reflect;
       /*!
       Enables drops to rotate to face camera.
       
        */
       bool rotateWithCamVel;
       /// @}
    
    
       /*! @name Collision
       @{ */
       /*! */
       /*!
       Allow collision with world objects.
       
        */
       bool doCollision;
       /*!
       Allow collision on player objects.
       
        */
       bool hitPlayers;
       /*!
       Allow collision on vehicles.
       
        */
       bool hitVehicles;
       /// @}
    
    
       /*! @name Movement
       @{ */
       /*! */
       /*!
       Enables system to follow the camera or stay where it is placed.
       
        */
       bool followCam;
       /*!
       Check to have the Sky property windSpeed affect precipitation.
       
        */
       bool useWind;
       /*!
       Minimum speed that a drop will fall.
       
        */
       float minSpeed;
       /*!
       Maximum speed that a drop will fall.
       
        */
       float maxSpeed;
       /*!
       Minimum mass of a drop.
       
        */
       float minMass;
       /*!
       Maximum mass of a drop.
       
        */
       float maxMass;
       /// @}
    
    
       /*! @name Turbulence
       @{ */
       /*! */
       /*!
       Check to enable turbulence. This causes precipitation drops to spiral while falling.
       
        */
       bool useTurbulence;
       /*!
        at which precipitation drops spiral when turbulence is enabled.
       
        */
       float maxTurbulence;
       /*!
       Speed at which precipitation drops spiral when turbulence is enabled.
       
        */
       float turbulenceSpeed;
       /// @}
    
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Creates a physics based impulse effect from a defined central point and magnitude.
    
    @see RadialImpulseEvent::send
    @ingroup Physics
     */
    class  RadialImpulseEvent {
      public:
       /*! Apply a radial impulse to any SceneObjects in the area of effect.
    This event is performed server-side AND client-side.
    
    @param position Center point for this radial impulse.
    @param  Distance from the position for this radial impulse to affect.
    @param magnitude The force applied to objects within the  from the position of this radial impulse effect.
    
    @tsexample
    // Define the Position
    %position = "10.0 15.0 10.0";
    
    // Define the 
    % = "25.0";
    
    // Define the Magnitude
    %magnitude = "30.0"
    
    // Create a globalRadialImpulse physics effect.
    RadialImpulseEvent::send(%position,%,%magnitude);
    @endtsexample
    
     */
       virtual void send(( string inPosition="1.0 1.0 1.0", float =10.0f, float magnitude=20.0f )) {}
    };
    
    class  CmServerInfoManager {
      public:
       virtual bool setLocalWorldIDToLoad(( int worldID=0 )) {}
       virtual bool setDefaultLocalWorldIDToLoad(()) {}
       virtual bool initLocalWorld(()) {}
       virtual bool isDedicatedServer() {}
       virtual string getCurentWorldID() {}
       virtual string getWorldIdToLoad() {}
    };
    
    class  CmServerSharedLoadingStatus : public SimObject {
      public:
       virtual void setServerLoaded() {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  Animal : public Player {
      public:
       virtual void setActive(( bool isActive )) {}
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  NPCDecorative : public Player {
      public:
       virtual void setActive(( bool isActive )) {}
       virtual void setToOrigin(()) {}
       virtual void setBehavior(( string behaviorName )) {}
       /*!
       Original position of NPCS::NPCDecorative.
       
        */
       TransformF originPos;
       /*!
       behavior of NPCS::NPCDecorative
       
        */
       string behavior;
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  horse : public Vehicle {
      public:
       virtual Script playPain(( string this )) {}
       virtual Script playDeathCry(( string this )) {}
       virtual Script playCelAnimation(( string this, string anim )) {}
       virtual Script playDeathAnimation(( string this )) {}
       virtual Script kill(( string this, string damageType )) {}
       virtual int getMaxSpeedLevel(()) {}
       virtual int getCurrentSpeedLevel(()) {}
       virtual void updateFormulas(()) {}
       virtual void setThreadPos(( float pos )) {}
       virtual void animate(( int animation )) {}
       virtual void setQuality(( int quality )) {}
       /*! @brief Get the name of the player's current state.
    
    The state is one of the following:
    
    <ul><li>Dead - The Player is dead.</li><li>Mounted - The Player is mounted to an object such as a vehicle.</li><li>Move - The Player is free to move.  The usual state.</li></ul>
    @return The current state; one of: "Dead", "Mounted", "Move"
     */
       virtual string getState(()) {}
       virtual void processCollisionWithPlayer(( Player player, bool unstoppable )) {}
    
       /*! @name Game
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Data structure for storing indexed sequences of key/value pairs.
    
    This is a powerful array class providing PHP style arrays in TorqueScript.
    
    The following features are supported:<ul>
    <li>array pointers: this allows you to move forwards or backwards through the array as if it was a list, including jumping to the start or end.</li>
    <li>sorting: the array can be sorted in either alphabetic or numeric mode, on the key or the value, and in ascending or descending order</li>
    <li>add/remove elements: elements can be pushed/popped from the start or end of the array, or can be inserted/erased from anywhere in the middle</li>
    <li>removal of duplicates: remove duplicate keys or duplicate values</li>
    <li>searching: search the array and return the index of a particular key or value</li>
    <li>counting: count the number of instaces of a particular value or key in the array, as well as the total number of elements</li>
    <li>advanced features: array append, array crop and array duplicate</li>
    </ul>
    
    Array element keys and values can be strings or numbers
    
     */
    class  ArrayObject : public SimObject {
      public:
       /*! Search the array from the current position for the element @param value Array value to search for
    @return Index of the first element found, or -1 if none
     */
       virtual int getIndexFromValue(( string value )) {}
       /*! Search the array from the current position for the key @param value Array key to search for
    @return Index of the first element found, or -1 if none
     */
       virtual int getIndexFromKey(( string key )) {}
       /*! Get the value of the array element at the submitted index.
    @param index 0-based index of the array element to get
    @return The value of the array element at the specified index, or "" if the index is out of range
     */
       virtual string getValue(( int index )) {}
       /*! Get the key of the array element at the submitted index.
    @param index 0-based index of the array element to get
    @return The key associated with the array element at the specified index, or "" if the index is out of range
     */
       virtual string getKey(( int index )) {}
       virtual string getValueFromKey(( string key )) {}
       virtual string getKeyFromValue(( string val )) {}
       /*! Set the key at the given index.
    @param key New key value
    @param index 0-based index of the array element to update
     */
       virtual void setKey(( string key, int index )) {}
       /*! Set the value at the given index.
    @param value New array element value
    @param index 0-based index of the array element to update
     */
       virtual void setValue(( string value, int index )) {}
       /*! Get the number of elements in the array. */
       virtual int count(()) {}
       /*! Get the number of times a particular value is found in the array.
    @param value Array element value to count
     */
       virtual int countValue(( string value )) {}
       /*! Get the number of times a particular key is found in the array.
    @param key Key value to count
     */
       virtual int countKey(( string key )) {}
       /*! Adds a new element to the end of an array (same as push_back()).
    @param key Key for the new element
    @param value Value for the new element
     */
       virtual void add(( string key, string value="" )) {}
       /*! Adds a new element to the end of an array.
    @param key Key for the new element
    @param value Value for the new element
     */
       virtual void push_back(( string key, string value="" )) {}
       /*! Adds a new element to the front of an array */
       virtual void push_front(( string key, string value="" )) {}
       /*! Adds a new element to a specified position in the array.
    - @a index = 0 will insert an element at the start of the array (same as push_front())
    - @a index = %array.count() will insert an element at the end of the array (same as push_back())
    
    @param key Key for the new element
    @param value Value for the new element
    @param index 0-based index at which to insert the new element */
       virtual void insert(( string key, string value, int index )) {}
       /*! Adds a new element to the end of an array or updates the value if key is already in a list. */
       virtual void setValueByKey(( string key, string value="" )) {}
       /*! Adds a new element to the end of an array or updates the value if key is already in a list. */
       virtual void updateValue(( string key, string value="" )) {}
       /*! Removes the last element from the array */
       virtual void pop_back(()) {}
       /*! Removes the first element from the array */
       virtual void pop_front(()) {}
       /*! Removes an element at a specific position from the array.
    @param index 0-based index of the element to remove
     */
       virtual void erase(( int index )) {}
       /*! Emptys all elements from an array */
       virtual void empty(()) {}
       /*! Removes any elements that have duplicated values (leaving the first instance) */
       virtual void uniqueValue(()) {}
       /*! Removes any elements that have duplicated keys (leaving the first instance) */
       virtual void uniqueKey(()) {}
       /*! Alters array into an exact duplicate of the target array.
    @param target ArrayObject to duplicate
     */
       virtual bool duplicate(( ArrayObject target )) {}
       /*! Removes elements with matching keys from array.
    @param target ArrayObject containing keys to remove from this array
     */
       virtual bool crop(( ArrayObject target )) {}
       /*! Appends the target array to the array object.
    @param target ArrayObject to append to the end of this array
     */
       virtual bool append(( ArrayObject target )) {}
       /*! Alpha sorts the array by value
    
    @param descending [optional] True for descending sort, false for ascending sort
     */
       virtual void sort(( bool descending=false )) {}
       /*! Alpha sorts the array by value in ascending order */
       virtual void sorta(()) {}
       /*! Alpha sorts the array by value in descending order */
       virtual void sortd(()) {}
       /*! Alpha sorts the array by key
    
    @param descending [optional] True for descending sort, false for ascending sort
     */
       virtual void sortk(( bool descending=false )) {}
       /*! Alpha sorts the array by key in ascending order */
       virtual void sortka(()) {}
       /*! Alpha sorts the array by key in descending order */
       virtual void sortkd(()) {}
       /*! Numerically sorts the array by value
    
    @param descending [optional] True for descending sort, false for ascending sort
     */
       virtual void sortn(( bool descending=false )) {}
       /*! Numerically sorts the array by value in ascending order */
       virtual void sortna(()) {}
       /*! Numerically sorts the array by value in descending order */
       virtual void sortnd(()) {}
       /*! Numerically sorts the array by key
    
    @param descending [optional] True for descending sort, false for ascending sort
     */
       virtual void sortnk(( bool descending=false )) {}
       /*! Numerical sorts the array by key in ascending order */
       virtual void sortnka(()) {}
       /*! Numerical sorts the array by key in descending order */
       virtual void sortnkd(()) {}
       /*! Sorts the array by value in ascending order using the given callback function.
    @param functionName Name of a function that takes two arguments A and B and returns -1 if A is less, 1 if B is less, and 0 if both are equal.
    
    @tsexample
    function mySortCallback(%a, %b)
    {
       return strcmp( %a.name, %b.name );
    }
    
    %array.sortf( "mySortCallback" );
    @endtsexample
     */
       virtual void sortf(( string functionName )) {}
       /*! Sorts the array by key in ascending order using the given callback function.
    @param functionName Name of a function that takes two arguments A and B and returns -1 if A is less, 1 if B is less, and 0 if both are equal.@see sortf
     */
       virtual void sortfk(( string functionName )) {}
       /*! Sorts the array by value in descending order using the given callback function.
    @param functionName Name of a function that takes two arguments A and B and returns -1 if A is less, 1 if B is less, and 0 if both are equal.@see sortf
     */
       virtual void sortfd(( string functionName )) {}
       /*! Sorts the array by key in descending order using the given callback function.
    @param functionName Name of a function that takes two arguments A and B and returns -1 if A is less, 1 if B is less, and 0 if both are equal.@see sortf
     */
       virtual void sortfkd(( string functionName )) {}
       /*! Moves array pointer to start of array
    
    @return Returns the new array pointer */
       virtual int moveFirst(()) {}
       /*! Moves array pointer to end of array
    
    @return Returns the new array pointer */
       virtual int moveLast(()) {}
       /*! Moves array pointer to next position
    
    @return Returns the new array pointer, or -1 if already at the end */
       virtual int moveNext(()) {}
       /*! Moves array pointer to prev position
    
    @return Returns the new array pointer, or -1 if already at the start */
       virtual int movePrev(()) {}
       /*! Gets the current pointer index */
       virtual int getCurrent(()) {}
       /*! Sets the current pointer index.
    @param index New 0-based pointer index
     */
       virtual void setCurrent(( int index )) {}
       /*! Echos the array contents to the console */
       virtual void echo(()) {}
       /*!
       Makes the keys and values case-sensitive.
    By default, comparison of key and value strings will be case-insensitive.
       
        */
       bool caseSensitive;
       /*!
       Helper field which allows you to add new key['keyname'] = value pairs.
       
        */
       caseString key;
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    A class designed to be used as a console consumer and log the data it receives to a file.
    
    @see dumpConsoleFunctions
    @see dumpConsoleClasses
    @ingroup Logging
     */
    class  ConsoleLogger : public SimObject {
      public:
       virtual bool attach() {}
       virtual bool detach() {}
    
       /*! @name Logging
       @{ */
       /*! */
       /*!
       Determines the priority level and attention the logged entry gets when recorded
    
    
       
        */
       LogLevel level;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief For static-field copying/pasting, editor use only
    
     */
    class  FieldBrushObject : public SimObject {
      public:
       virtual string queryGroups() {}
       virtual string queryFields() {}
       virtual void copyFields() {}
       virtual void pasteFields() {}
       /*!
       
       
        */
       caseString description;
       /*!
       
       
        */
       string sortName;
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A script-level OOP object which allows binding of a class, superClass and arguments along with declaration of methods.
    
    ScriptObjects are extrodinarily powerful objects that allow defining of any type of data required. They can optionally have
    a class and a superclass defined for added control of multiple ScriptObjects through a simple class definition.
    
    @tsexample
    new ScriptObject(Game)
    {
       class = "DeathMatchGame";
       superClass = GameCore;
       genre = "Action FPS"; // Note the new, non-Torque variable
    };
    @endtsexample
    @see SimObject
    @ingroup Console
     */
    class  ScriptObject : public SimObject {
      public:
          /*! Called when this ScriptObject is added to the system.
    @param ID Unique object ID assigned when created (%this in script).
     */
          void onAdd( SimObjectId ID );
    
          /*! Called when this ScriptObject is removed from the system.
    @param ID Unique object ID assigned when created (%this in script).
     */
          void onRemove( SimObjectId ID );
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Essentially a SimGroup, but with onAdd and onRemove script callbacks.
    
    @tsexample
    // First container, SimGroup containing a ScriptGroup
    new SimGroup(Scenes)
    {
    ^// Subcontainer, ScriptGroup containing variables
    ^// related to a cut scene and a starting WayPoint
    ^new ScriptGroup(WelcomeScene)
    ^{
    ^^class = "Scene";
    ^^pathName = "Pathx";
    ^^description = "A small orc village set in the Hardesty mountains. This town and its surroundings will be used to illustrate some the Torque Game Engine's features.";
    ^^pathTime = "0";
    ^^title = "Welcome to Orc Town";
    
    ^^new WayPoint(start)
    ^^{
    ^^^position = "163.873 -103.82 208.354";
    ^^^rotation = "0.136165 -0.0544916 0.989186 44.0527";
    ^^^scale = "1 1 1";
    ^^^dataBlock = "WayPointMarker";
    ^^^team = "0";
    ^^};
    ^};
    };
    @endtsexample
    
    @see SimGroup
    @ingroup Console
     */
    class  ScriptGroup : public SimGroup {
      public:
          /*! Called when this ScriptGroup is added to the system.
    @param ID Unique object ID assigned when created (%this in script).
     */
          void onAdd( SimObjectId ID );
    
          /*! Called when this ScriptObject is removed from the system.
    @param ID Unique object ID assigned when created (%this in script).
     */
          void onRemove( SimObjectId ID );
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A SimSet that can be safely persisted.
    
    Uses SimPersistIDs to reference objects in the set while persisted on disk.  This allows the set to resolve its references no matter whether they are loaded before or after the set is created.
    
    Not intended for game development, for editors or internal use only.
    
     */
    class  SimPersistSet : public SimSet {
      public:
       virtual void resolvePersistentIds() {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  LockFileObject : public SimObject {
      public:
       virtual bool open(( string filename )) {}
       virtual void close(()) {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Base class for working with streams.
    
    You do not instantiate a StreamObject directly.  Instead, it is used as part of a FileStreamObject and ZipObject to support working with uncompressed and compressed files respectively.@tsexample
    // You cannot actually declare a StreamObject
    // Instead, use the derived class "FileStreamObject"
    %fsObject = FileStreamObject();
    @endtsexample
    
    @see FileStreamObject for the derived class usable in script.
    @see ZipObject where StreamObject is used to read and write to files within a zip archive.
    @ingroup FileSystem
    
     */
    class  StreamObject : public SimObject {
      public:
       /*! @brief Gets a printable string form of the stream's status
    
    @tsexample
    // Create a file stream object for reading
    %fsObject = new FileStreamObject();
    
    // Open a file for reading
    %fsObject.open("./test.txt", "read");
    
    // Get the status and print it
    %status = %fsObject.getStatus();
    echo(%status);
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @return String containing status constant, one of the following:
    
    ^OK - Stream is active and no file errors
    
    ^IOError - Something went wrong during read or writing the stream
    
    ^EOS - End of Stream reached (mostly for reads)
    
    ^IllegalCall - An unsupported operation used.  Always w/ accompanied by AssertWarn
    
      Closed - Tried to operate on a closed stream (or detached filter)
    
    ^UnknownError - Catch all for an error of some kind
    
    ^Invalid - Entire stream is invalid
    
     */
       virtual string getStatus(()) {}
       /*! @brief Tests if the stream has reached the end of the file
    
    This is an alternative name for isEOF. Both functions are interchangeable. This simply exists for those familiar with some C++ file I/O standards.
    
    @tsexample
    // Create a file stream object for reading
    %fsObject = new FileStreamObject();
    
    // Open a file for reading
    %fsObject.open("./test.txt", "read");
    
    // Keep reading until we reach the end of the file
    while( !%fsObject.isEOS() )
    {
       %line = %fsObject.readLine();
       echo(%line);
    }
    // Made it to the end
    echo("Finished reading file");
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @return True if the parser has reached the end of the file, false otherwise
    @see isEOF() */
       virtual bool isEOS(()) {}
       /*! @brief Tests if the stream has reached the end of the file
    
    This is an alternative name for isEOS. Both functions are interchangeable. This simply exists for those familiar with some C++ file I/O standards.
    
    @tsexample
    // Create a file stream object for reading
    %fsObject = new FileStreamObject();
    
    // Open a file for reading
    %fsObject.open("./test.txt", "read");
    
    // Keep reading until we reach the end of the file
    while( !%fsObject.isEOF() )
    {
       %line = %fsObject.readLine();
       echo(%line);
    }
    // Made it to the end
    echo("Finished reading file");
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @return True if the parser has reached the end of the file, false otherwise
    @see isEOS() */
       virtual bool isEOF(()) {}
       /*! @brief Gets the position in the stream
    
    The easiest way to visualize this is to think of a cursor in a text file. If you have moved the cursor by five characters, the current position is 5. If you move ahead 10 more characters, the position is now 15. For StreamObject, when you read in the line the position is increased by the number of characters parsed, the null terminator, and a newline.
    
    @tsexample
    // Create a file stream object for reading
    %fsObject = new FileStreamObject();
    
    // Open a file for reading
    // This file contains two lines of text repeated:
    // Hello World
    // Hello World
    %fsObject.open("./test.txt", "read");
    
    // Read in the first line
    %line = %fsObject.readLine();
    
    // Get the position of the stream
    %position = %fsObject.getPosition();
    
    // Print the current position
    // Should be 13, 10 for the words, 1 for the space, 1 for the null terminator, and 1 for the newline
    echo(%position);
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @return Number of bytes which stream has parsed so far, null terminators and newlines are included
    @see setPosition() */
       virtual int getPosition(()) {}
       /*! @brief Gets the position in the stream
    
    The easiest way to visualize this is to think of a cursor in a text file. If you have moved the cursor by five characters, the current position is 5. If you move ahead 10 more characters, the position is now 15. For StreamObject, when you read in the line the position is increased by the number of characters parsed, the null terminator, and a newline. Using setPosition allows you to skip to specific points of the file.
    
    @tsexample
    // Create a file stream object for reading
    %fsObject = new FileStreamObject();
    
    // Open a file for reading
    // This file contains the following two lines:
    // 11111111111
    // Hello World
    %fsObject.open("./test.txt", "read");
    
    // Skip ahead by 12, which will bypass the first line entirely
    %fsObject.setPosition(12);
    
    // Read in the next line
    %line = %fsObject.readLine();
    
    // Print the line just read in, should be "Hello World"
    echo(%line);
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @return Number of bytes which stream has parsed so far, null terminators and newlines are included
    @see getPosition() */
       virtual bool setPosition(( int newPosition )) {}
       /*! @brief Gets the size of the stream
    
    The size is dependent on the type of stream being used. If it is a file stream, returned value will be the size of the file. If it is a memory stream, it will be the size of the allocated buffer.
    
    @tsexample
    // Create a file stream object for reading
    %fsObject = new FileStreamObject();
    
    // Open a file for reading
    // This file contains the following two lines:
    // HelloWorld
    // HelloWorld
    %fsObject.open("./test.txt", "read");
    
    // Found out how large the file stream is
    // Then print it to the console
    // Should be 22
    %streamSize = %fsObject.getStreamSize();
    echo(%streamSize);
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @return Size of stream, in bytes
     */
       virtual int getStreamSize(()) {}
       /*! @brief Read a line from the stream.
    
    Emphasis on *line*, as in you cannot parse individual characters or chunks of data. There is no limitation as to what kind of data you can read.
    
    @tsexample
    // Create a file stream object for reading
    // This file contains the following two lines:
    // HelloWorld
    // HelloWorld
    %fsObject = new FileStreamObject();
    
    %fsObject.open("./test.txt", "read");
    
    // Read in the first line
    %line = %fsObject.readLine();
    
    // Print the line we just read
    echo(%line);
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @return String containing the line of data that was just read
    @see writeLine() */
       virtual string readLine(()) {}
       /*! @brief Write a line to the stream, if it was opened for writing.
    
    There is no limit as to what kind of data you can write. Any format and data is allowable, not just text. Be careful of what you write, as whitespace, current values, and literals will be preserved.
    
    @param line The data we are writing out to file.@tsexample
    // Create a file stream
    %fsObject = new FileStreamObject();
    
    // Open the file for writing
    // If it does not exist, it is created. If it does exist, the file is cleared
    %fsObject.open("./test.txt", "write");
    
    // Write a line to the file
    %fsObject.writeLine("Hello World");
    
    // Write another line to the file
    %fsObject.writeLine("Documentation Rocks!");
    
    // Always remember to close a file stream when finished
    %fsObject.close();
    @endtsexample
    
    @see readLine() */
       virtual void writeLine(( string line )) {}
       /*! @brief Read in a string and place it on the string table.
    
    @param caseSensitive If false then case will not be taken into account when attempting to match the read in string with what is already in the string table.
    @return The string that was read from the stream.
    @see writeString()@note When working with these particular string reading and writing methods, the stream begins with the length of the string followed by the string itself, and does not include a NULL terminator. */
       virtual string readSTString(( bool caseSensitive=false )) {}
       /*! @brief Read a string up to a maximum of 256 characters@return The string that was read from the stream.
    @see writeString()@note When working with these particular string reading and writing methods, the stream begins with the length of the string followed by the string itself, and does not include a NULL terminator. */
       virtual string readString(()) {}
       /*! @brief Read in a string up to the given maximum number of characters.
    
    @param maxLength The maximum number of characters to read in.
    @return The string that was read from the stream.
    @see writeLongString()@note When working with these particular string reading and writing methods, the stream begins with the length of the string followed by the string itself, and does not include a NULL terminator. */
       virtual string readLongString(( int maxLength )) {}
       /*! @brief Write out a string up to the maximum number of characters.
    
    @param maxLength The maximum number of characters that will be written.
    @param string The string to write out to the stream.
    @see readLongString()@note When working with these particular string reading and writing methods, the stream begins with the length of the string followed by the string itself, and does not include a NULL terminator. */
       virtual void writeLongString(( int maxLength, string string )) {}
       /*! @brief Write out a string with a default maximum length of 256 characters.
    
    @param string The string to write out to the stream
    @param maxLength The maximum string length to write out with a default of 256 characters.  This value should not be larger than 256 as it is written to the stream as a single byte.
    @see readString()@note When working with these particular string reading and writing methods, the stream begins with the length of the string followed by the string itself, and does not include a NULL terminator. */
       virtual void writeString(( string string, int maxLength=256 )) {}
       /*! @brief Copy from another StreamObject into this StreamObject
    
    @param other The StreamObject to copy from.
    @return True if the copy was successful.
     */
       virtual bool copyFrom(( SimObject other )) {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  AsyncZipPacker : public SimObject {
      public:
          /*!  */
          void onFinish();
    
          /*!  */
          void onFailed();
    
       virtual void addFile(( string fileName, string pathInZip )) {}
       virtual void pack(( String zipFileName )) {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Provides access to a zip file.
    
    A ZipObject add, delete and extract files that are within a zip archive.  You may also read and write directly to the files within the archive by obtaining a StreamObject for the file.@tsexample
    // Open a zip archive, creating it if it doesn't exist
    %archive = new ZipObject();
    %archive.openArchive("testArchive.zip", Write);
    
    // Add a file to the archive with the given name
    %archive.addFile("./water.png", "water.png");
    
    // Close the archive to save the changes
    %archive.closeArchive();
    @endtsexample
    
    @note Behind the scenes all of the work is being done with the ZipArchive and StreamObject classes.
    @see StreamObject when using methods such as openFileForRead() and openFileForWrite()
    
    @ingroup FileSystem
     */
    class  ZipObject : public SimObject {
      public:
       /*! @brief Open a zip archive for manipulation.
    
    Once a zip archive is opened use the various ZipObject methods for working with the files within the archive.  Be sure to close the archive when you are done with it.
    
    @param filename The path and file name of the zip archive to open.
    @param accessMode One of read, write or readwrite
    @return True is the archive was successfully opened.
    @note If you wish to make any changes to the archive, be sure to open it with a write or readwrite access mode.
    @see closeArchive() */
       virtual bool openArchive(( string filename, string accessMode="read" )) {}
       /*! @brief Close an already opened zip archive.
    
    @see openArchive() */
       virtual void closeArchive(()) {}
       /*! @brief Open a file within the zip archive for reading.
    
    Be sure to close the file when you are done with it.
    @param filename The path and name of the file to open within the zip archive.
    @return A standard StreamObject is returned for working with the file.
    @note You must first open the zip archive before working with files within it.
    @see closeFile()
    @see openArchive() */
       virtual string openFileForRead(( string filename )) {}
       /*! @brief Open a file within the zip archive for writing to.
    
    Be sure to close the file when you are done with it.
    @param filename The path and name of the file to open within the zip archive.
    @return A standard StreamObject is returned for working with the file.
    @note You must first open the zip archive before working with files within it.
    @see closeFile()
    @see openArchive() */
       virtual string openFileForWrite(( string filename )) {}
       /*! @brief Close a previously opened file within the zip archive.
    
    @param stream The StreamObject of a previously opened file within the zip archive.
    @see openFileForRead()
    @see openFileForWrite() */
       virtual void closeFile(( SimObject stream )) {}
       /*! @brief Add a file to the zip archive
    
    @param filename The path and name of the file to add to the zip archive.
    @param pathInZip The path and name to be given to the file within the zip archive.
    @param replace If a file already exists within the zip archive at the same location as this new file, this parameter indicates if it should be replaced.  By default, it will be replaced.
    @return True if the file was successfully added to the zip archive. */
       virtual bool addFile(( string filename, string pathInZip, bool replace=true )) {}
       /*! @brief Extact a file from the zip archive and save it to the requested location.
    
    @param pathInZip The path and name of the file to be extracted within the zip archive.
    @param filename The path and name to give the extracted file.
    
    @return True if the file was successfully extracted. */
       virtual bool extractFile(( string pathInZip, string filename )) {}
       /*! @brief Deleted the given file from the zip archive
    
    @param pathInZip The path and name of the file to be deleted from the zip archive.
    @return True of the file was successfully deleted.
    @note Files that have been deleted from the archive will still show up with a getFileEntryCount() until you close the archive.  If you need to have the file count up to date with only valid files within the archive, you could close and then open the archive again.
    @see getFileEntryCount()
    @see closeArchive()
    @see openArchive() */
       virtual bool deleteFile(( string pathInZip )) {}
       /*! @brief Get the number of files within the zip archive.
    
    Use getFileEntry() to retrive information on each file within the archive.
    
    @return The number of files within the zip archive.
    @note The returned count will include any files that have been deleted from the archive using deleteFile().  To clear out all deleted files, you could close and then open the archive again.
    @see getFileEntry()
    @see closeArchive()
    @see openArchive() */
       virtual int getFileEntryCount(()) {}
       /*! @brief Get information on the requested file within the zip archive.
    
    This methods provides five different pieces of information for the requested file:
    <ul><li>filename - The path and name of the file within the zip archive</li><li>uncompressed size</li><li>compressed size</li><li>compression method</li><li>CRC32</li></ul>
    Use getFileEntryCount() to obtain the total number of files within the archive.
    @param index The index of the file within the zip archive.  Use getFileEntryCount() to determine the number of files.
    @return A tab delimited list of information on the requested file, or an empty string if the file could not be found.
    @see getFileEntryCount() */
       virtual string getFileEntry(( int index )) {}
       virtual bool containsFile() {}
       virtual bool isFileEncrypted() {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Environmental object that triggers a day/night cycle in level.
    
    @note TimeOfDay only works in Advanced Lighting with a Sub object or ScatterSky
    
    @tsexample
    new TimeOfDay(tod)
    {
       axisTilt = "23.44";
       dayLength = "120";
       startTime = "0.15";
       time = "0.15";
       play = "0";
       azimuthOverride = "572.958";
       dayScale = "1";
       nightScale = "1.5";
       position = "598.399 550.652 196.297";
       rotation = "1 0 0 0";
       scale = "1 1 1";
       canSave = "1";
       canSaveDynamicFields = "1";
    };
    @endtsexample
    
     */
    class  TimeOfDay : public SceneObject {
      public:
       virtual void addTimeOfDayEvent(( float elevation, string identifier )) {}
       virtual void setTimeOfDay(( float time )) {}
       virtual void setPlay(( bool enabled )) {}
       virtual void setDayLength(( float seconds )) {}
       virtual void animate(( float elevation, float degreesPerSecond )) {}
    
       /*! @name TimeOfDay
       @{ */
       /*! */
       /*!
       The angle in degrees between global equator and tropic.
       
        */
       float axisTilt;
       /*!
       The length of a virtual day in real world seconds.
       
        */
       float dayLength;
       /*!
       
       
        */
       float startTime;
       /*!
       Current time of day.
       
        */
       float time;
       /*!
       True when the TimeOfDay object is operating.
       
        */
       bool play;
       /*!
       
       
        */
       float azimuthOverride;
       /*!
       Scalar applied to time that elapses while the sun is up.
       
        */
       float dayScale;
       /*!
       Scalar applied to time that elapses while the sun is down.
       
        */
       float nightScale;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief Object responsible for simulating wind in a level.
    
    When placed in the level, a ForestWindEmitter will cause tree branches to bend and sway, leaves to flutter, and create vertical bending on the tree's trunk.
    
    @tsexample
    // The following is a full declaration of a wind emitter
    new ForestWindEmitter()
    {
       position = "497.739 765.821 102.395";
       windEnabled = "1";
       radialEmitter = "1";
       strength = "1";
        = "3";
       gustStrength = "0.5";
       gustFrequency = "1";
       gustYawAngle = "10";
       gustYawFrequency = "4";
       gustWobbleStrength = "2";
       turbulenceStrength = "1";
       turbulenceFrequency = "2";
       hasMount = "0";
       scale = "3 3 3";
       canSave = "1";
       canSaveDynamicFields = "1";
       rotation = "1 0 0 0";
    };
    @endtsexample
    
    @ingroup FX
    @ingroup Forest
     */
    class  ForestWindEmitter : public SceneObject {
      public:
       /*! @brief Mounts the wind emitter to another scene object
    
    @param objectID Unique ID of the object wind emitter should attach to@tsexample
    // Wind emitter previously created and named %windEmitter
    // Going to attach it to the player, making him a walking wind storm
    %windEmitter.attachToObject(%player);
    @endtsexample
    
     */
       virtual void attachToObject(( int objectID )) {}
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    
       /*! @name ForestWind
       @{ */
       /*! */
       /*!
       Determines if the emitter will be counted in wind calculations.
       
        */
       bool windEnabled;
       /*!
       Determines if the emitter is a global direction or local radial emitter.
       
        */
       bool radialEmitter;
       /*!
       The strength of the wind force.
       
        */
       float strength;
       /*!
       The  of the emitter for local radial emitters.
       
        */
       float ;
       /*!
       The maximum strength of a gust.
       
        */
       float gustStrength;
       /*!
       The frequency of gusting in seconds.
       
        */
       float gustFrequency;
       /*!
       The amount of degrees the wind direction can drift (both positive and negative).
       
        */
       float gustYawAngle;
       /*!
       The frequency of wind yaw drift, in seconds.
       
        */
       float gustYawFrequency;
       /*!
       The amount of random wobble added to gust and turbulence vectors.
       
        */
       float gustWobbleStrength;
       /*!
       The strength of gust turbulence.
       
        */
       float turbulenceStrength;
       /*!
       The frequency of gust turbulence, in seconds.
       
        */
       float turbulenceFrequency;
       /*!
       Determines if the emitter is mounted to another object.
       
        */
       bool hasMount;
       /// @}
    
    };
    
    /*!
    @brief A ResponseCurve<F32> wrapped as a SimObject.
    
    Currently no applied use, not network ready, not intended for game development, for editors or internal use only.
    
     */
    class  SimResponseCurve : public SimObject {
      public:
       virtual void addPoint() {}
       virtual float getValue() {}
       virtual void clear() {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  NavPath : public SceneObject {
      public:
       /*! @brief Find a path using the already-specified path properties. */
       virtual bool replan(()) {}
       /*! @brief Return the number of nodes in this path. */
       virtual int getCount(()) {}
       /*! @brief Get a specified node along the path. */
       virtual string getNode(( int idx )) {}
       /*! @brief Get the length of this path in Torque units (i.e. the total distance it covers). */
       virtual float getLength(()) {}
    
       /*! @name NavPath
       @{ */
       /*! */
       /*!
       World location this path starts at.
       
        */
       Point3F from;
       /*!
       World location this path should end at.
       
        */
       Point3F to;
       /*!
       Path containing waypoints for this NavPath to visit.
       
        */
       Path waypoints;
       /*!
       Does this path loop?
       
        */
       bool isLooping;
       /// @}
    
    
       /*! @name NavPath Render
       @{ */
       /*! */
       /*!
       Display this NavPath even outside the editor.
       
        */
       bool alwaysRender;
       /*!
       Render this NavPath through other objects.
       
        */
       bool xray;
       /// @}
    
    
       /*! @name Transform
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Mounting
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  ChildProcessHelper : public ScriptObject {
      public:
       virtual void addKeywordCallback(( String callbackMethod, String callbackKeyword, bool autoRemoveCallback=false )) {}
       virtual bool removeCallback(( String callbackMethod )) {}
       virtual int getCallbacksCount(()) {}
       /*! returns method name */
       virtual string getCallbackMethod(( int index )) {}
       /*! returns keyword */
       virtual string getCallbackKeyword(( int index )) {}
       virtual bool launchProcess(()) {}
       virtual void sendCommand(( String cmd )) {}
       virtual bool isRunning(()) {}
       virtual int getReturnCode(()) {}
       virtual bool terminateProcess(()) {}
       virtual int lastMessage(()) {}
    
       /*! @name ChildProcess
       @{ */
       /*! */
       /*!
       app name to display in console
       
        */
       string appName;
       /*!
       app path+filename with optional path
       
        */
       string appPath;
       /*!
       params to pass to the launched app
       
        */
       string appArgs;
       /*!
       callback to call when process exited
       
        */
       string onExitCallback;
       /*!
       object to call the callback on, should accept 1 bool param with result
       
        */
       SimObject callbackObject;
       /*!
       Should kill the child process during CPH shutdown
       
        */
       bool killOnShutdown;
       /*!
       do we need to redirect stdin/stdout to us
       
        */
       bool redirectStdIO;
       /*!
       display console window
       
        */
       bool showWindow;
       /*!
       alias to use for the slash command
       
        */
       string slashAlias;
       /*!
       In seconds. If not zero, the 'WaitForSingleObject(val);' will be called instead of INFINITE.
       
        */
       int executeTimeout;
       /*!
       The SimTime of when the last stdout has been processed from the child process.
       
        */
       int lastMessage;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief A spline along which various objects can move along. The spline object acts like a container for Marker objects, which make
    up the joints, or knots, along the path. Paths can be assigned a speed, can be looping or non-looping. Each of a path's markers can be
    one of three primary movement types: "normal", "Position Only", or "Kink". 
    @tsexample
    new path()
    ^{
         isLooping = "1";
    
         new Marker()
    ^^{
    ^^^seqNum = "0";
    ^^^type = "Normal";
    ^^^msToNext = "1000";
    ^^^smoothingType = "Spline";
    ^^^position = "-0.054708 -35.0612 234.802";
    ^^^rotation = "1 0 0 0";
          };
    
    ^};
    @endtsexample
    @see Marker
    @ingroup enviroMisc
     */
    class  Path : public SimGroup {
      public:
       /*! @brief Returns the PathID (not the object ID) of this path.
    
    @return PathID (not the object ID) of this path.
    @tsexample
    // Acquire the PathID of this path object.
    %pathID = %thisPath.getPathId();
    
    @endtsexample
    
     */
       virtual int getPathId(()) {}
       /*!
       If this is true, the loop is closed, otherwise it is open.
    
       
        */
       bool isLooping;
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  RecordSet : public SimObject {
      public:
       virtual int getQueryId() {}
       virtual bool nextRecord() {}
       virtual void rewind() {}
       virtual int getFieldCount() {}
       virtual int getDataFieldCount() {}
       virtual string getFieldName() {}
       virtual string getDataFieldName() {}
       virtual string getFieldValue() {}
       virtual string getDataFieldValue() {}
       virtual string fv() {}
       virtual string lastID() {}
       virtual string rows() {}
       virtual string numRows() {}
       virtual string getNumRows() {}
       virtual bool ok() {}
       virtual string getSQL() {}
    };
    
    class  TCPConnection : public SimObject {
      public:
       virtual Script cAuth(( string this, string var )) {}
       virtual Script sAuthTimedout(( string this )) {}
       virtual Script drop(( string this )) {}
       virtual Script onConnected(( string this )) {}
       virtual bool sendRPC() {}
       virtual bool sendCommand() {}
       virtual void setConnectArgs() {}
       virtual void connect() {}
       virtual string getRemoteAddress() {}
       virtual int getRemotePort() {}
       virtual string getLocalAddress() {}
       virtual int getLocalPort() {}
       virtual bool isServerSide() {}
       virtual bool isInitiator() {}
    
       /*! @name TCPConnection
       @{ */
       /*! */
       /*!
       The hostname we are online with.
       
        */
       string hostname;
       /*!
       The port number we are using atm.
       
        */
       int port;
       /// @}
    
    
       /*! @name TCP Stats
       @{ */
       /*! */
       /*!
       When this connection was established (unixtime)
       
        */
       int initatedAt;
       /*!
       Bytes read from network stream since the connection was established.
       
        */
       int bytesRead;
       /*!
       Bytes sent to network stream since the connection was established.
       
        */
       int bytesSent;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    class  SimDownloadHelper : public SimObject {
      public:
          /*!  */
          void onFinished();
    
          /*!  */
          void onFailed( int errorCode, String errorMessage );
    
          /*!  */
          void onProgress( float progress, int current, int total, String speed );
    
       virtual void delete(()) {}
       virtual bool start(()) {}
       virtual int getSizeTransfer(()) {}
       virtual int getSizeTotal(()) {}
    
       /*! @name Download Details
       @{ */
       /*! */
       /*!
       
       
        */
       string url;
       /*!
       
       
        */
       string fileName;
       /*!
       
       
        */
       string cbFinished;
       /*!
       
       
        */
       string cbFailed;
       /*!
       
       
        */
       string cbProgress;
       /// @}
    
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief An undo action that is comprised of other undo actions.
    
    Not intended for game development, for editors or internal use only.
    
     */
    class  CompoundUndoAction : public UndoAction {
      public:
       virtual void addAction() {}
    
       /*! @name Ungrouped
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Object
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Editing
       @{ */
       /*! */
       /// @}
    
    
       /*! @name Persistence
       @{ */
       /*! */
       /// @}
    
    };
    
    /*!
    @brief SimObject which adds, tracks, and deletes UndoAction objects.
    
    Not intended for game development, for editors or internal use only.
    
     */
    class  UndoManager : public SimObject {
      public:
       virtual void clearAll() {}
       virtual int getUndoCount() {}
       virtual string getUndoName() {}
       virtual int getUndoAction() {}
       virtual int getRedoCount() {}
       virtual string getRedoName() {}
       virtual int getRedoAction() {}
       virtual void undo() {}
       virtual void redo() {}
       virtual string getNextUndoName() {}
       virtual string getNextRedoName() {}
       virtual string pushCompound() {}
       virtual void popCompound() {}
       /*!
       Number of undo & redo levels.
       
        */
       int numLevels;
    };
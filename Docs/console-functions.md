---
layout: default
last_modified_date: 2022-12-03 15:10:15 +0000
title: Console functions
nav_order: 6
nav_exclude: false
parent: Documentation
has_children: false
has_toc: false
published: false

---
# Console functions (reference)

    namespace Global {
       virtual Script quitNoMaintenance(()) {}
       virtual Script quit(()) {}
       virtual Script prepAndKillMariaDB(( string callback )) {}
       virtual Script serverCmdOrder_to_formation(( string client, string order_type )) {}
       virtual Script serverCmdCreate_formation(( string client, string formation_type )) {}
       virtual Script serverCmdresuscitate(( string client, string magnitude )) {}
       virtual Script serverCmdcreateRest(( string client, string duration, string healAmount )) {}
       virtual Script serverCmddealDamage(( string client, string partOfBody )) {}
       virtual Script serverCmdhealFracture(( string client, string partOfBody, string durationMultiplier )) {}
       virtual Script serverCmdhealWound(( string client, string partOfBody, string durationMultiplier )) {}
       virtual Script serverCmdremoveFracture(( string client, string partOfBody )) {}
       virtual Script serverCmdremoveBleeding(( string client, string partOfBody )) {}
       virtual Script serverCmdremoveWound(( string client, string partOfBody )) {}
       virtual Script serverCmdcreateFracture(( string client, string partOfBody )) {}
       virtual Script serverCmdcreateBleeding(( string client, string partOfBody )) {}
       virtual Script serverCmdcreateWound(( string client, string partOfBody )) {}
       /*! Call exec() on all scripts from the %folder excluding filenames specified in %exclude.
    Usage example:
    reloadScriptsFromFolder("global", "init main onceOnly");
    will exec all files except init.cs, main.cs and onceOnly.cs
     */
       virtual Script reloadScriptsFromFolder(( string folder, string exclude, string ext )) {}
       virtual Script getClientConnectionByCsHash(( string accoundHash )) {}
       virtual Script serverRpcCAUTH(( string peer, string clientKey )) {}
       virtual Script onTCPInitError(( string tcpServer, string error )) {}
       virtual Script onTCPInitOK(( string tcpServer )) {}
       virtual Script onTCPError(( string tcpServer, string errorCode, string errorMessage )) {}
       virtual Script serverRpcAuthMe(( string peer, string chid )) {}
       virtual Script serverCmdInitDebugTCPServer(( string peer )) {}
       virtual Script initDebugTCPServer(()) {}
       virtual Script initTCPServer(( string port )) {}
       virtual Script InitHorsePack(()) {}
       virtual Script InitHorses(()) {}
       virtual Script InitAIHorses(()) {}
       virtual Script onSteamServerRegistered(()) {}
       virtual Script destroyWorld(()) {}
       virtual Script tryToRegisterOnSteam(()) {}
       virtual Script createWorld(()) {}
       virtual Script serverCmdenterVehicle(( string client )) {}
       virtual Script serverCmdSetRenderedHitbox(( string client, string hitbox )) {}
       virtual Script serverCmdDebugServerCastRay(( string client, string eyePosition, string eyeVector )) {}
       virtual Script Damage(( string sourceObject, string position, string , string damage, string damageType, string impulse )) {}
       virtual Script cm_config_CalcPlayerPostHitTimeScale(( string lvl )) {}
       virtual Script cm_config_CalcPlayerHitTimeScale(( string lvl )) {}
       virtual Script cm_config_CalcPlayerDmgByHit(( string hitSpeed, string hitNodeName, string hitBoxName, string groupDmgLevel, string chargeTime )) {}
       virtual Script onMaintenanceFinished(( string status )) {}
       virtual Script cmChatSendLocalMessageToClient(( string client, string fromName, string position, string message )) {}
       virtual Script onServerDestroyed(()) {}
       virtual Script onServerCreated(()) {}
       virtual Script serverCmdUnmountWeapon(( string client )) {}
       virtual Script serverCmdToggleWeaponSlot(( string client, string slot )) {}
       virtual Script clearBottomPrintAll(()) {}
       virtual Script clearCenterPrintAll(()) {}
       virtual Script clearBottomPrint(( string client )) {}
       virtual Script clearCenterPrint(( string client )) {}
       virtual Script bottomPrint(( string client, string message, string time, string lines )) {}
       virtual Script centerPrint(( string client, string message, string time, string lines )) {}
       virtual Script bottomPrintAll(( string message, string time, string lines )) {}
       virtual Script centerPrintAll(( string message, string time, string lines )) {}
       virtual Script spawnPlayer(( string client )) {}
       virtual Script serverCmdClientManagersInitialized(( string connection )) {}
       virtual Script updatePlayerCountDisplay(()) {}
       virtual Script serverCmdClientReadyToEnterGame(( string client )) {}
       virtual Script serverCmdReadyToPatch(( string client )) {}
       virtual Script serverCmdReadyToInventory(( string client )) {}
       virtual Script serverCmdReadyState(( string client )) {}
       virtual Script serverCmdPathCam(( string client, string cmd, string a1 )) {}
       virtual Script serverCmdCheckServerGameMode(( string client )) {}
       virtual Script serverCmdTakeCameraPos(( string client )) {}
       virtual Script serverCmdSetCameraPos(( string client, string transform )) {}
       virtual Script serverCmdSetCameraFly(( string client )) {}
       virtual Script serverCmdSetCameraNewtonDamped(( string client )) {}
       virtual Script serverCmdSetCameraNewton(( string client )) {}
       virtual Script stop(()) {}
       virtual Script go(()) {}
       virtual Script dd(()) {}
       virtual Script getRot(()) {}
       virtual Script serverCmdDropCameraAtPlayer(( string client )) {}
       virtual Script serverCmdDropPlayerAtCamera(( string client )) {}
       virtual Script serverCmdSetCameraSpeed(( string client, string speed )) {}
       virtual Script serverCmdNetSimulateLag(( string client, string msDelay, string packetLossPercent )) {}
       virtual Script messageAllExcept(( string client, string team, string msgType, string msgString, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9, string a10, string a11, string a12, string a13 )) {}
       virtual Script messageAll(( string msgType, string msgString, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9, string a10, string a11, string a12, string a13 )) {}
       virtual Script messageClient(( string client, string msgType, string msgString, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9, string a10, string a11, string a12, string a13 )) {}
       virtual Script startSharingServerLoadingStatus(()) {}
       virtual Script initServer(()) {}
       /*!  Determine the IP address we can use locally
     */
       virtual Script determineNetwork(()) {}
       virtual Script serverCmdEx(( string p, string c )) {}
       virtual Script rexs(()) {}
       virtual Script _dumpPlayerInfo(( string player )) {}
       virtual Script _dumpClientInfo(( string client )) {}
       virtual Script listAll(()) {}
       /*!  When the server is queried for information, the value of this function is
     returned as the status field of the query packet.  This information is
     accessible as the ServerInfo::State variable.
     */
       virtual Script onServerInfoQuery(()) {}
       /*!  Shut down the server
     */
       virtual Script destroyServer(()) {}
       /*!  Create a server with either a "SinglePlayer" or "MultiPlayer" type
     Specify the level to load on the server
     */
       virtual Script createServer(()) {}
       /*!  Attempt to find an open port to initialize the server with
     */
       virtual Script portInit(( string port )) {}
       virtual Script initBaseServer(()) {}
       virtual Script onExit(()) {}
       virtual Script onStart(()) {}
       virtual Script initNetwork(()) {}
       virtual Script checkServerIdLockFile(()) {}
       virtual Script onPostInit(()) {}
       virtual Script prepareManagers(()) {}
       virtual Script prepareDbIDRanges(()) {}
       virtual Script loadDirs(( string dirPath )) {}
       virtual Script loadDir(( string dir )) {}
       virtual Script isScriptFile(( string path )) {}
       virtual Script compileFiles(( string pattern )) {}
       virtual Script defaultParseArgs(()) {}
       virtual Script popFront(( string list, string delim )) {}
       virtual Script pushBack(( string list, string token, string delim )) {}
       virtual Script pushFront(( string list, string token, string delim )) {}
       virtual void initSoundsManager() {}
       virtual void loadAttackAnimationsXml() {}
       virtual bool isDebugTcpEnabled(()) {}
       virtual void loadXmlDataForSpecialAttacks() {}
       virtual void serverCmdloadXmlDataForSpecialAttacks(( GameConnection client )) {}
       virtual void loadComplexObjectTypes(()) {}
       /*! Get the MissionArea object, if any.
    
    @ingroup enviroMisc
    
     */
       virtual string getMissionAreaServerObject(()) {}
       virtual void setInteriorRenderMode() {}
       virtual void serverCmdcmSetTitle(( GameConnection sender, int msg_id )) {}
       virtual void dbgEnableTransitions() {}
       virtual void dbgDisableTransitions() {}
       virtual string getShapeBaseImageData(( int objectTypeId )) {}
          /*! @brief Called on the client each time a datablock has been received.
    
    This callback is typically used to notify the player of how far along in the datablock download process they are.
    
    @param index The index of the datablock just received.
    @param total The total number of datablocks to be received.
    
    @see GameConnection, GameConnection::transmitDataBlocks(), GameConnection::onDataBlocksDone()
    
    @ingroup Networking
     */
          void onDataBlockObjectReceived( int index, int total );
    
       virtual void attachTCP(( SimObject tcp, int charId )) {}
       virtual void dumpProcessList() {}
       virtual bool physicsPluginPresent() {}
       virtual bool physicsInit() {}
       virtual void physicsDestroy() {}
       virtual bool physicsInitWorld() {}
       virtual void physicsDestroyWorld() {}
       virtual void physicsStartSimulation() {}
       virtual void physicsStopSimulation() {}
       virtual bool physicsSimulationEnabled() {}
       virtual void physicsSetTimeScale() {}
       virtual float physicsGetTimeScale() {}
       virtual void physicsStoreState() {}
       virtual void physicsRestoreState() {}
       /*! initialize behaviors manager class */
       virtual void initBehaviorsManager(()) {}
       /*! reload AI xml trees only for new animals */
       virtual void reloadBehaviorXml(()) {}
       /*! registerBehavior(name, fileName) - register new behavior file */
       virtual void registerBehavior(( String name, String fileName )) {}
       /*! print behavior trees */
       virtual void showBehaviorTrees(()) {}
       /*! print behavior tree */
       virtual void printBehaviorTree(( string name )) {}
       /*! @brief Add a string to the bad word filter
    
    The bad word filter is a table containing words which will not be displayed in chat windows. Instead, a designated replacement string will be displayed.  There are already a number of bad words automatically defined.
    
    @param badWord Exact text of the word to restrict.
    @return True if word was successfully added, false if the word or a subset of it already exists in the table
    @see filterString()
    
    @tsexample
    // In this game, "Foobar" is banned
    %badWord = "Foobar";
    
    // Returns true, word was successfully added
    addBadWord(%badWord);
    
    // Returns false, word has already been added
    addBadWord("Foobar");@endtsexample
    @ingroup Game */
       virtual bool addBadWord(( string badWord )) {}
       /*! @brief Replaces the characters in a string with designated text
    
    Uses the bad word filter to determine which characters within the string will be replaced.
    
    @param baseString  The original string to filter.
    @param replacementChars A string containing letters you wish to swap in the baseString.
    @return The new scrambled string 
    @see addBadWord()
    @see containsBadWords()
    @tsexample
    // Create the base string, can come from anywhere
    %baseString = "Foobar";
    
    // Create a string of random letters
    %replacementChars = "knqwrtlzs";
    
    // Filter the string
    %newString = filterString(%baseString, %replacementChars);
    
    // Print the new string to console
    echo(%newString);@endtsexample
    @ingroup Game */
       virtual string filterString(( string baseString=NULL, string replacementChars=NULL )) {}
       /*! @brief Checks to see if text is a bad word
    
    The text is considered to be a bad word if it has been added to the bad word filter.
    
    @param text Text to scan for bad words
    @return True if the text has bad word(s), false if it is clean
    @see addBadWord()
    @see filterString()
    @tsexample
    // In this game, "Foobar" is banned
    %badWord = "Foobar";
    
    // Add a banned word to the bad word filter
    addBadWord(%badWord);
    
    // Create the base string, can come from anywhere like user chat
    %userText = "Foobar";
    
    // Create a string of random letters
    %replacementChars = "knqwrtlzs";
    
    // If the text contains a bad word, filter it before printing
    // Otherwise print the original text
    if(containsBadWords(%userText))
    {
    ^// Filter the string
    ^%filteredText = filterString(%userText, %replacementChars);
    
    ^// Print filtered text
    ^echo(%filteredText);
    }
    else
    ^echo(%userText);
    
    @endtsexample
    @ingroup Game */
       virtual bool containsBadWords(( string text )) {}
       virtual void CmConfiguration_init() {}
       virtual void initCmLangManager() {}
       virtual string getPathToTranslatedFileIfExists() {}
       virtual void initCmMessages() {}
       virtual bool isPermanentDeathGame(()) {}
       virtual bool isColonizationGameMode(()) {}
       virtual bool isColonizationQuestComplete(()) {}
       virtual void initPlayerSpawnPoints(()) {}
       virtual string strToPlayerName() {}
       virtual bool setNetPort() {}
       virtual void closeNetPort() {}
       virtual void saveJournal() {}
       virtual void playJournal() {}
       virtual int getSimTime() {}
       virtual int getRealTime() {}
       virtual int getRealSystemTime() {}
       virtual string getUnixTime(()) {}
       virtual void initAdminLandsAbilities(()) {}
       virtual int getVersionNumber() {}
       virtual string getVersionString() {}
       virtual string getEngineName() {}
       virtual string getCompileTimeString() {}
       virtual string getBuildString() {}
       virtual void reloadAnimalsBehavior() {}
       virtual void removeAnimalsBehavior() {}
       /*! initialize animals spawn control */
       virtual void initAnimalsSpawnControl(()) {}
       /*! print spawn points information */
       virtual void printSpawnInfo(()) {}
       /*! starts stretched maintenance of animal spawn */
       virtual void startStretchedAnimalSpawnMaintenance(()) {}
       virtual void initBarterManager() {}
       virtual void initBomberman() {}
       virtual void initBeehiveManager() {}
       virtual void initBreedingManager() {}
       virtual void CharacterNameCache_remove() {}
       virtual void loadTriggersManager(()) {}
       virtual bool initTitlesManager() {}
       virtual bool CreateTestCharacter(( int accountId, int charId )) {}
       virtual bool DeleteTestCharacter(( String name )) {}
       virtual bool CreateTestCharacters(( int accountId, int number, int startWithId )) {}
       virtual bool DeleteTestCharacters(( int accountId )) {}
       /*! sends a local chat message */
       virtual void serverCmdLocalChatMessage(( GameConnection sender, String message )) {}
       virtual void initChatServer() {}
       virtual void initCraftworkManager() {}
       virtual void initBuildingManager() {}
       virtual void initCreationManager() {}
       virtual void initCustomisationManager() {}
       virtual void initDurabilityManager() {}
       virtual void initEquipmentManager() {}
       virtual void objectDecay(()) {}
       virtual void DumpObjectsToFile() {}
       virtual void initServerComplexObjectManager() {}
       virtual int CreateTestUnmovable(( int typeId, int geoId, int playerId, int state )) {}
       virtual int CreateTestUnmovablePrecise(( int typeId, int globalGeoX, int globalGeoY, int rotateAngle, int playerId, int durability, int state )) {}
       virtual int CreateTestMovable(( int typeId, int geoId, int playerId, int state )) {}
       virtual int CreateTestMovablePrecise(( int typeId, int globalGeoX, int globalGeoY, int altitude, int offsetX, int offsetY, int offsetZ, int rotateAngle, int playerId, int durability, int state )) {}
       virtual void DeleteTestUnmovable(( int geoId )) {}
       virtual void DeleteTestMovable(( int geoId )) {}
       virtual void TestObjectSetWorking(( int geoId )) {}
       virtual void TestObjectSetNotWorking(( int geoId )) {}
       virtual void TestObjectSetOwner(( int geoId, int playerId )) {}
       virtual void TestObjectResetOwner(( int geoId )) {}
       virtual void initGuildActionsManager() {}
       virtual void createGuild(( int producerCharId, String guildName, String guildTag, String guildCharter )) {}
       virtual void destroyGuild(( int producerCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void invitePlayerToGuild(( int producerCharId, int targetCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void acceptGuildInvite(( int producerCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void declineGuildInvite(( int producerCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void cancelInvitationToGuild(( int producerCharId, int targetCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void leaveGuild(( int producerCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void kickPlayerFromGuild(( int producerCharId, int targetCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void charGuildRoleChange(( int producerCharId, Guilds::GuildId::UnderlyingType guildId, int targetCharId, int role )) {}
       virtual void guildStandingsChange(( int producerCharId, Guilds::GuildId::UnderlyingType guildId, Guilds::GuildId::UnderlyingType targetGuildId, int standing )) {}
       virtual void renameGuild(( int producerCharId, Guilds::GuildId::UnderlyingType guildId, String guildName, String guildTag )) {}
       /*! initial load of guilds from DB */
       virtual bool initLoadGuilds(()) {}
       virtual void DebugPrintGuilds(( bool includeMembers=false, bool includeStandings=false )) {}
       virtual void CreateTestGuild(( int producerCharId )) {}
       virtual void DeleteTestGuild(( int producerCharId )) {}
       virtual void TestInviteToGuild(( int producerCharId, int targetCharId )) {}
       virtual void TestAcceptInviteToGuild(( int receiverCharId )) {}
       virtual void TestChangeGuildRole(( int targetCharId, int role )) {}
       virtual void TestChangeStanding(( int producerCharId, int targetCharId, int standing )) {}
       /*! Forces main-thread crops maintenance for all terrains if no input parameters are provided, or for a specific terrain if terID is provided as an input parameter */
       virtual bool cropsMainThreadMaintenance(( int terID=InvalidTerID )) {}
       /*! Forces stretched crops maintenance for all terrains */
       virtual bool cropsStretchedMaintenance(()) {}
       virtual void initMixingManager() {}
       virtual void removeMixingManager() {}
       virtual bool initInventoryManager() {}
       virtual bool IsJHActive(()) {}
       virtual void initJudgementHourServerManager() {}
       virtual void printJudgementHourSettings() {}
       virtual void initLoadClaimRules() {}
       virtual void SendValidateLands(( NetConnection server )) {}
       virtual void DebugPrintClaims(( bool includeUnmovableObjects=false )) {}
       virtual void setClaimCharRule(( int claimId, int producerCharId, int targetCharId, String ruleStr )) {}
       virtual void setClaimGuildRule(( int claimId, int producerCharId, Guilds::GuildId::UnderlyingType guildId, String ruleStr )) {}
       virtual void setClaimRoleRule(( int claimId, int producerCharId, int role, String ruleStr )) {}
       virtual void setClaimStandingRule(( int claimId, int producerCharId, int standing, String ruleStr )) {}
       virtual void removeClaimCharRule(( int claimId, int producerCharId, int targetCharId )) {}
       virtual void removeClaimGuildRule(( int claimId, int producerCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void removeClaimRoleRule(( int claimId, int producerCharId, int role )) {}
       virtual void removeClaimStandingRule(( int claimId, int producerCharId, int standing )) {}
       virtual void setUnmovableCharRule(( int unmovableId, int producerCharId, int targetCharId, String ruleStr )) {}
       virtual void setUnmovableGuildRule(( int unmovableId, int producerCharId, Guilds::GuildId::UnderlyingType guildId, String ruleStr )) {}
       virtual void setUnmovableRoleRule(( int unmovableId, int producerCharId, int role, String ruleStr )) {}
       virtual void setUnmovableStandingRule(( int unmovableId, int producerCharId, int standing, String ruleStr )) {}
       virtual void removeUnmovableCharRule(( int unmovableId, int producerCharId, int targetCharId )) {}
       virtual void removeUnmovableGuildRule(( int unmovableId, int producerCharId, Guilds::GuildId::UnderlyingType guildId )) {}
       virtual void removeUnmovableRoleRule(( int unmovableId, int producerCharId, int role )) {}
       virtual void removeUnmovableStandingRule(( int unmovableId, int producerCharId, int standing )) {}
       virtual void validateGuildLands(()) {}
       virtual void forceLandMaintenance(()) {}
       /*! initial load of lands DB */
       virtual void createLandsManager(()) {}
       /*! initial load of lands DB */
       virtual void initLoadLands(()) {}
       virtual void createBattleZone(( int type, int geoIdInt, int , string name )) {}
       virtual void deleteBattleZone(( int landDbId )) {}
       virtual void printBattleZones(()) {}
       virtual void recalcLands(()) {}
       virtual void DebugPrintLands(()) {}
       virtual void TestMonumentChange(( int geoId, int  )) {}
       virtual void TestPersonalLandCreateTemporary(( int ownerId, int firstGeoId, int secondGeoId )) {}
       virtual void TestPersonalLandMaintenance(( int ownerId )) {}
       virtual void TestPersonalLandSetStatus(( int ownerId, int status )) {}
       virtual void TestAdminLandCreate(( int playerId, int firstGeoId, int secondGeoId, String name, int priority )) {}
       virtual void TestPersonalLandDelete(( int playerId )) {}
       virtual void TestAdminLandDelete(( int playerId, String name )) {}
       virtual void initMentoringManager() {}
       virtual void commandToClient() {}
       virtual void commandToPeer() {}
       virtual void removeTaggedString() {}
       virtual string addTaggedString() {}
       virtual string getTaggedString() {}
       virtual string buildTaggedString() {}
       /*! initialize outpost bunny manager */
       virtual void initOutpostBunnyManager(()) {}
       virtual void initOutpostsManager() {}
       virtual void removeOutpostsManager() {}
       virtual void FerryManSailToAbella(( int charID )) {}
       virtual void FerryManSelectNewbieServer(( int charID )) {}
       virtual void loadQuests(()) {}
       virtual void initPlayerRandomEvents() {}
       virtual void loadRecipes(()) {}
       virtual bool initSkillsManager() {}
       virtual void clearSkillsManager() {}
       virtual string getSkillName() {}
       virtual void changeSkill(( int char_id, int skill_type_id, string add_value )) {}
       virtual bool TestPlayerAbilityCellEntity(( int playerId, int abilityId, int geoID, bool expectedResult )) {}
       virtual bool TestPlayerAbilityUnmovableEntity(( int playerId, int abilityId, int geoID, bool expectedResult )) {}
       virtual bool TestPlayerAbilityMovableEntity(( int playerId, int abilityId, int geoID, bool expectedResult )) {}
       virtual bool TestPlayerAbilityHorseEntity(( int playerId, int abilityId, int horseId, bool expectedResult )) {}
       virtual bool TestPlayerAbilityCartEntity(( int playerId, int abilityId, int horseId, bool expectedResult )) {}
       virtual bool TestPlayerAbilityTreeEntity(( int playerId, int abilityId, int geoID, bool expectedResult )) {}
       virtual void ClearTestSetAbilities(()) {}
       virtual void ExportAbilitiesTestResults(( String fileName )) {}
       /*! reload gathering info */
       virtual void reloadGatheringInfo(()) {}
       virtual void DebugProspectingTest(( int M=10, int terID=446, int x=250, int y=250, int alt=5073, int substGeoID=23 )) {}
       virtual void TestRaiseTerrain(( int geoId, int playerId, int substance )) {}
       virtual void TestLowerTerrain(( int geoId, int playerId )) {}
       /*! Executes the given slash-command */
       virtual void doSlashCommand(( string command )) {}
       virtual void initUnitManager() {}
       /*! Reinitialize constants */
       virtual void reinitUnitFormationConstants(()) {}
       virtual void initHorsesManager() {}
       virtual int CreateTestHorse(( int horseId, int geoId, int typeId, int ownerId )) {}
       virtual void DeleteTestHorse(( int horseId )) {}
       virtual void TestHorseSetOwner(( int horseId, int playerId )) {}
       virtual void TestHorseResetOwner(( int horseId )) {}
       virtual string testJavaScriptBridge() {}
       virtual string TestFunction2Args() {}
       virtual void cls() {}
       /*! @brief Logs a message to the console.
    
    @param message The message text.
    @note By default, messages will appear white in the console.
    @ingroup Logging */
       virtual void log(( string message )) {}
       /*! @brief Logs an error message to the console.
    
    @param message The message text.
    @note By default, errors will appear red in the console.
    @ingroup Logging */
       virtual void logError(( string message )) {}
       /*! @brief Logs a warning message to the console.
    
    @param message The message text.
    
    @note By default, warnings will appear turquoise in the console.
    @ingroup Logging */
       virtual void logWarning(( string message )) {}
       virtual bool startNewLogFile(()) {}
       virtual bool renameLogFileByServerId(( int serverId )) {}
       /*! @brief Dumps all declared console classes to the console.
    
    @param dumpScript Optional parameter specifying whether or not classes defined in script should be dumped.
    @param dumpEngine Optional parameter specifying whether or not classes defined in the engine should be dumped.
    @ingroup Logging */
       virtual void dumpConsoleClasses(( bool dumpScript=true, bool dumpEngine=true )) {}
       /*! @brief Dumps all declared console functions to the console.
    @param dumpScript Optional parameter specifying whether or not functions defined in script should be dumped.
    @param dumpEngine Optional parameter specitying whether or not functions defined in the engine should be dumped.
    @ingroup Logging */
       virtual void dumpConsoleFunctions(( bool dumpScript=true, bool dumpEngine=true )) {}
       /*! Return the integer character code value corresponding to the first character in the given string.
    @param chr a (one-character) string.
    @return the UTF32 code value for the first character in the given string.
    @ingroup Strings */
       virtual int strasc(( string chr )) {}
       /*! Format the given value as a string using printf-style formatting.
    @param format A printf-style format string.
    @param value The value argument matching the given format string.
    
    @tsexample
    // Convert the given integer value to a string in a hex notation.
    %hex = strformat( "%x", %value );
    @endtsexample
    @ingroup Strings
    @see http://en.wikipedia.org/wiki/Printf */
       virtual string strformat(( string format, string value )) {}
       /*! Compares two strings using case-&lt;b&gt;sensitive&lt;/b&gt; comparison.
    @param str1 The first string.
    @param str2 The second string.
    @return 0 if both strings are equal, a value &lt;0 if the first character different in str1 has a smaller character code value than the character at the same position in str2, and a value &gt;1 otherwise.
    
    @tsexample
    if( strcmp( %var, "foobar" ) == 0 )
       echo( "%var is equal to 'foobar'" );
    @endtsexample
    @see stricmp
    @see strnatcmp
    @ingroup Strings */
       virtual int strcmp(( string str1, string str2 )) {}
       /*! Compares two strings using case-&lt;b&gt;insensitive&lt;/b&gt; comparison.
    @param str1 The first string.
    @param str2 The second string.
    @return 0 if both strings are equal, a value &lt;0 if the first character different in str1 has a smaller character code value than the character at the same position in str2, and a value &gt;0 otherwise.
    
    @tsexample
    if( stricmp( "FOObar", "foobar" ) == 0 )
       echo( "this is always true" );
    @endtsexample
    @see strcmp
    @see strinatcmp
    @ingroup Strings */
       virtual int stricmp(( string str1, string str2 )) {}
       /*! Compares two strings using "natural order" case-&lt;b&gt;sensitive&lt;/b&gt; comparison.
    Natural order means that rather than solely comparing single character code values, strings are ordered in a natural way.  For example, the string "hello10" is considered greater than the string "hello2" even though the first numeric character in "hello10" actually has a smaller character value than the corresponding character in "hello2".  However, since 10 is greater than 2, strnatcmp will put "hello10" after "hello2".
    @param str1 The first string.
    @param str2 The second string.
    
    @return 0 if the strings are equal, a value &gt;0 if @a str1 comes after @a str2 in a natural order, and a value &lt;0 if @a str1 comes before @a str2 in a natural order.
    
    @tsexample
    // Bubble sort 10 elements of %array using natural order
    do
    {
       %swapped = false;
       for( %i = 0; %i &lt; 10 - 1; %i ++ )
          if( strnatcmp( %array[ %i ], %array[ %i + 1 ] ) &gt; 0 )
          {
             %temp = %array[ %i ];
             %array[ %i ] = %array[ %i + 1 ];
             %array[ %i + 1 ] = %temp;
             %swapped = true;
          }
    }
    while( %swapped );
    @endtsexample
    @see strcmp
    @see strinatcmp
    @ingroup Strings */
       virtual int strnatcmp(( string str1, string str2 )) {}
       /*! Compares two strings using "natural order" case-&lt;b&gt;insensitive&lt;/b&gt; comparison.
    Natural order means that rather than solely comparing single character code values, strings are ordered in a natural way.  For example, the string "hello10" is considered greater than the string "hello2" even though the first numeric character in "hello10" actually has a smaller character value than the corresponding character in "hello2".  However, since 10 is greater than 2, strnatcmp will put "hello10" after "hello2".
    @param str1 The first string.
    @param str2 The second string.
    @return 0 if the strings are equal, a value &gt;0 if @a str1 comes after @a str2 in a natural order, and a value &lt;0 if @a str1 comes before @a str2 in a natural order.
    
    @tsexample
    
    // Bubble sort 10 elements of %array using natural order
    do
    {
       %swapped = false;
       for( %i = 0; %i &lt; 10 - 1; %i ++ )
          if( strnatcmp( %array[ %i ], %array[ %i + 1 ] ) &gt; 0 )
          {
             %temp = %array[ %i ];
             %array[ %i ] = %array[ %i + 1 ];
             %array[ %i + 1 ] = %temp;
             %swapped = true;
          }
    }
    while( %swapped );
    @endtsexample
    @see stricmp
    @see strnatcmp
    @ingroup Strings */
       virtual int strinatcmp(( string str1, string str2 )) {}
       /*! Get the length of the given string in bytes.
    @note This does &lt;b&gt;not&lt;/b&gt; return a true character count for strings with multi-byte characters!
    @param str A string.
    @return The length of the given string in bytes.
    @ingroup Strings */
       virtual int strlen(( string str )) {}
       /*! Find the start of @a substring in the given @a string searching from left to right.
    @param string The string to search.
    @param substring The string to search for.
    @return The index into @a string at which the first occurrence of @a substring was found or -1 if @a substring could not be found.
    
    @tsexample
    strstr( "abcd", "c" ) // Returns 2.
    @endtsexample
    @ingroup Strings */
       virtual int stristr(( string string, string substring )) {}
       /*! Find the start of @a needle in @a haystack searching from left to right beginning at the given offset.
    @param haystack The string to search.
    @param needle The string to search for.
    @return The index at which the first occurrence of @a needle was found in @a haystack or -1 if no match was found.
    
    @tsexample
    strpos( "b ab", "b", 1 ) // Returns 3.
    @endtsexample
    @ingroup Strings */
       virtual int strpos(( string haystack, string needle, int start=0 )) {}
       /*! Find the start of @a substring in the given @a string searching from left to right.
    @param string The string to search.
    @param substring The string to search for.
    @return The index into @a string at which the first occurrence of @a substring was found or -1 if @a substring could not be found.
    
    @tsexample
    strstr( "abcd", "c" ) // Returns 2.
    @endtsexample
    @ingroup Strings */
       virtual int strstr(( string string, string substring )) {}
       /*! Remove leading whitespace from the string.
    @param str A string.
    @return A string that is the same as @a str but with any leading (i.e. leftmost) whitespace removed.
    
    @tsexample
    ltrim( "   string  " ); // Returns "string  ".
    @endtsexample
    @see rtrim
    @see trim
    @ingroup Strings */
       virtual string ltrim(( string str )) {}
       /*! Remove trailing whitespace from the string.
    @param str A string.
    @return A string that is the same as @a str but with any trailing (i.e. rightmost) whitespace removed.
    
    @tsexample
    rtrim( "   string  " ); // Returns "   string".
    @endtsexample
    @see ltrim
    @see trim
    @ingroup Strings */
       virtual string rtrim(( string str )) {}
       /*! Remove leading and trailing whitespace from the string.
    @param str A string.
    @return A string that is the same as @a str but with any leading (i.e. leftmost) and trailing (i.e. rightmost) whitespace removed.
    
    @tsexample
    trim( "   string  " ); // Returns "string".
    @endtsexample
    @ingroup Strings */
       virtual string trim(( string str )) {}
       /*! Remove all occurrences of characters contained in @a chars from @a str.
    @param str The string to filter characters out from.
    @param chars A string of characters to filter out from @a str.
    @return A version of @a str with all occurrences of characters contained in @a chars filtered out.
    
    @tsexample
    stripChars( "teststring", "se" ); // Returns "tttring".@endtsexample
    @ingroup Strings */
       virtual string stripChars(( string str, string chars )) {}
       /*! Return an all lower-case version of the given string.
    @param str A string.
    @return A version of @a str with all characters converted to lower-case.
    
    @tsexample
    strlwr( "TesT1" ) // Returns "test1"
    @endtsexample
    @see strupr
    @ingroup Strings */
       virtual string strlwr(( string str )) {}
       /*! Return an all upper-case version of the given string.
    @param str A string.
    @return A version of @a str with all characters converted to upper-case.
    
    @tsexample
    strupr( "TesT1" ) // Returns "TEST1"
    @endtsexample
    @see strlwr
    @ingroup Strings */
       virtual string strupr(( string str )) {}
       /*! Find the first occurrence of the given character in @a str.
    @param str The string to search.
    @param chr The character to search for.  Only the first character from the string is taken.
    @return The remainder of the input string starting with the given character or the empty string if the character could not be found.
    
    @see strrchr
    @ingroup Strings */
       virtual string strchr(( string str, string chr )) {}
       /*! Find the last occurrence of the given character in @a str.@param str The string to search.
    @param chr The character to search for.  Only the first character from the string is taken.
    @return The remainder of the input string starting with the given character or the empty string if the character could not be found.
    
    @see strchr
    @ingroup Strings */
       virtual string strrchr(( string str, string chr )) {}
       /*! Replace all occurrences of @a from in @a source with @a to.
    @param source The string in which to replace the occurrences of @a from.
    @param from The string to replace in @a source.
    @param to The string with which to replace occurrences of @from.
    @return A string with all occurrences of @a from in @a source replaced by @a to.
    
    @tsexample
    strreplace( "aabbccbb", "bb", "ee" ) // Returns "aaeeccee".
    @endtsexample
    @ingroup Strings */
       virtual string strreplace(( string source, string from, string to )) {}
       /*! Return a string that repeats @a str @a numTimes number of times delimiting each occurrence with @a delimiter.
    @param str The string to repeat multiple times.
    @param numTimes The number of times to repeat @a str in the result string.
    @param delimiter The string to put between each repetition of @a str.
    @return A string containing @a str repeated @a numTimes times.
    
    @tsexample
    strrepeat( "a", 5, "b" ) // Returns "ababababa".
    @endtsexample
    @ingroup Strings */
       virtual string strrepeat(( string str, int numTimes, string delimiter="" )) {}
       /*! @brief Return a substring of @a str starting at @a start and continuing either through to the end of @a str (if @a numChars is -1) or for @a numChars characters (except if this would exceed the actual source string length).
    @param str The string from which to extract a substring.
    @param start The offset at which to start copying out characters.
    @param numChars Optional argument to specify the number of characters to copy.  If this is -1, all characters up the end of the input string are copied.
    @return A string that contains the given portion of the input string.
    
    @tsexample
    getSubStr( "foobar", 1, 2 ) // Returns "oo".
    @endtsexample
    
    @ingroup Strings */
       virtual string getSubStr(( string str, int start, int numChars=-1 )) {}
       /*! Match a pattern against a string.
    @param pattern The wildcard pattern to match against.  The pattern can include characters, '*' to match any number of characters and '?' to match a single character.
    @param str The string which should be matched against @a pattern.
    @param caseSensitive If true, characters in the pattern are matched in case-sensitive fashion against this string.  If false, differences in casing are ignored.
    @return True if @a str matches the given @a pattern.
    
    @tsexample
    strIsMatchExpr( "f?o*R", "foobar" ) // Returns true.
    @endtsexample
    @see strIsMatchMultipleExpr
    @ingroup Strings */
       virtual bool strIsMatchExpr(( string pattern, string str, bool caseSensitive=false )) {}
       /*! Match a multiple patterns against a single string.
    @param patterns A tab-separated list of patterns.  Each pattern can include charaters, '*' to match any number of characters and '?' to match a single character.  Each of the patterns is tried in turn.
    @param str The string which should be matched against @a patterns.
    @param caseSensitive If true, characters in the pattern are matched in case-sensitive fashion against this string.  If false, differences in casing are ignored.
    @return True if @a str matches any of the given @a patterns.
    
    @tsexample
    strIsMatchMultipleExpr( "*.cs *.gui *.mis", "mymission.mis" ) // Returns true.
    @endtsexample
    @see strIsMatchExpr
    @ingroup Strings */
       virtual bool strIsMatchMultipleExpr(( string patterns, string str, bool caseSensitive=false )) {}
       /*! Get the numeric suffix of the given input string.
    @param str The string from which to read out the numeric suffix.
    @return The numeric value of the number suffix of @a str or -1 if @a str has no such suffix.
    
    @tsexample
    getTrailingNumber( "test123" ) // Returns '123'.
    @endtsexample
    
    @see stripTrailingNumber
    @ingroup Strings */
       virtual int getTrailingNumber(( string str )) {}
       /*! Strip a numeric suffix from the given string.
    @param str The string from which to strip its numeric suffix.
    @return The string @a str without its number suffix or the original string @a str if it has no such suffix.
    
    @tsexample
    stripTrailingNumber( "test123" ) // Returns "test".
    @endtsexample
    
    @see getTrailingNumber
    @ingroup Strings */
       virtual string stripTrailingNumber(( string str )) {}
       /*! Test whether the character at the given position is a whitespace character.
    Characters such as tab, space, or newline are considered whitespace.
    @param str The string to test.
    @param index The index of a character in @a str.
    @return True if the character at the given index in @a str is a whitespace character; false otherwise.
    
    @see isalnum
    @ingroup Strings */
       virtual bool isspace(( string str, int index )) {}
       /*! Test whether the character at the given position is an alpha-numeric character.
    Alpha-numeric characters are characters that are either alphabetic (a-z, A-Z) or numbers (0-9).
    @param str The string to test.
    @param index The index of a character in @a str.
    @return True if the character at the given index in @a str is an alpha-numeric character; false otherwise.
    
    @see isspace
    @ingroup Strings */
       virtual bool isalnum(( string str, int index )) {}
       /*! Test whether the given string begins with the given prefix.
    @param str The string to test.
    @param prefix The potential prefix of @a str.
    @param caseSensitive If true, the comparison will be case-sensitive; if false, differences in casing will not be taken into account.
    @return True if the first characters in @a str match the complete contents of @a prefix; false otherwise.
    
    @tsexample
    startsWith( "TEST123", "test" ) // Returns true.
    @endtsexample
    @see endsWith
    @ingroup Strings */
       virtual bool startsWith(( string str, string prefix, bool caseSensitive=false )) {}
       /*! @brief Test whether the given string ends with the given suffix.
    
    @param str The string to test.
    @param suffix The potential suffix of @a str.
    @param caseSensitive If true, the comparison will be case-sensitive; if false, differences in casing will not be taken into account.
    @return True if the last characters in @a str match the complete contents of @a suffix; false otherwise.
    
    @tsexample
    startsWith( "TEST123", "123" ) // Returns true.
    @endtsexample
    
    @see startsWith
    @ingroup Strings */
       virtual bool endsWith(( string str, string suffix, bool caseSensitive=false )) {}
       /*! Find the first occurrence of the given character in the given string.
    @param str The string to search.
    @param chr The character to look for.  Only the first character of this string will be searched for.
    @param start The index into @a str at which to start searching for the given character.
    @return The index of the first occurrence of @a chr in @a str or -1 if @a str does not contain the given character.
    
    @tsexample
    strchrpos( "test", "s" ) // Returns 2.
    @endtsexample
    @ingroup Strings */
       virtual int strchrpos(( string str, string chr, int start=0 )) {}
       /*! Find the last occurrence of the given character in the given string.
    @param str The string to search.
    @param chr The character to look for.  Only the first character of this string will be searched for.
    @param start The index into @a str at which to start searching for the given character.
    @return The index of the last occurrence of @a chr in @a str or -1 if @a str does not contain the given character.
    
    @tsexample
    strrchrpos( "test", "t" ) // Returns 3.
    @endtsexample
    @ingroup Strings */
       virtual int strrchrpos(( string str, string chr, int start=0 )) {}
       /*! Extract the word at the given @a index in the whitespace-separated list in @a text.
    Words in @a text must be separated by newlines, spaces, and/or tabs.
    @param text A whitespace-separated list of words.
    @param index The zero-based index of the word to extract.
    @return The word at the given index or "" if the index is out of range.
    
    @tsexample
    getWord( "a b c", 1 ) // Returns "b"
    @endtsexample
    
    @see getWords
    @see getWordCount
    @see getField
    @see getRecord
    @ingroup FieldManip */
       virtual string getWord(( string text, int index )) {}
       /*! Extract a range of words from the given @a startIndex onwards thru @a endIndex.
    Words in @a text must be separated by newlines, spaces, and/or tabs.
    @param text A whitespace-separated list of words.
    @param startIndex The zero-based index of the first word to extract from @a text.
    @param endIndex The zero-based index of the last word to extract from @a text.  If this is -1, all words beginning with @a startIndex are extracted from @a text.
    @return A string containing the specified range of words from @a text or "" if @a startIndex is out of range or greater than @a endIndex.
    
    @tsexample
    getWords( "a b c d", 1, 2, ) // Returns "b c"
    @endtsexample
    
    @see getWord
    @see getWordCount
    @see getFields
    @see getRecords
    @ingroup FieldManip */
       virtual string getWords(( string text, int startIndex, int endIndex=-1 )) {}
       /*! Replace the word in @a text at the given @a index with @a replacement.
    Words in @a text must be separated by newlines, spaces, and/or tabs.
    @param text A whitespace-separated list of words.
    @param index The zero-based index of the word to replace.
    @param replacement The string with which to replace the word.
    @return A new string with the word at the given @a index replaced by @a replacement or the original string if @a index is out of range.
    
    @tsexample
    setWord( "a b c d", 2, "f" ) // Returns "a b f d"
    @endtsexample
    
    @see getWord
    @see setField
    @see setRecord
    @ingroup FieldManip */
       virtual string setWord(( string text, int index, string replacement )) {}
       /*! Remove the word in @a text at the given @a index.
    Words in @a text must be separated by newlines, spaces, and/or tabs.
    @param text A whitespace-separated list of words.
    @param index The zero-based index of the word in @a text.
    @return A new string with the word at the given index removed or the original string if @a index is out of range.
    
    @tsexample
    removeWord( "a b c d", 2 ) // Returns "a b d"
    @endtsexample
    
    @see removeField
    @see removeRecord
    @ingroup FieldManip */
       virtual string removeWord(( string text, int index )) {}
       /*! Return the number of whitespace-separated words in @a text.
    Words in @a text must be separated by newlines, spaces, and/or tabs.
    @param text A whitespace-separated list of words.
    @return The number of whitespace-separated words in @a text.
    
    @tsexample
    getWordCount( "a b c d e" ) // Returns 5
    @endtsexample
    
    @see getFieldCount
    @see getRecordCount
    @ingroup FieldManip */
       virtual int getWordCount(( string text )) {}
       /*! Extract the field at the given @a index in the newline and/or tab separated list in @a text.
    Fields in @a text must be separated by newlines and/or tabs.
    @param text A list of fields separated by newlines and/or tabs.
    @param index The zero-based index of the field to extract.
    @return The field at the given index or "" if the index is out of range.
    
    @tsexample
    getField( "a b" TAB "c d" TAB "e f", 1 ) // Returns "c d"
    @endtsexample
    
    @see getFields
    @see getFieldCount
    @see getWord
    @see getRecord
    @ingroup FieldManip */
       virtual string getField(( string text, int index )) {}
       /*! Extract a range of fields from the given @a startIndex onwards thru @a endIndex.
    Fields in @a text must be separated by newlines and/or tabs.
    @param text A list of fields separated by newlines and/or tabs.
    @param startIndex The zero-based index of the first field to extract from @a text.
    @param endIndex The zero-based index of the last field to extract from @a text.  If this is -1, all fields beginning with @a startIndex are extracted from @a text.
    @return A string containing the specified range of fields from @a text or "" if @a startIndex is out of range or greater than @a endIndex.
    
    @tsexample
    getFields( "a b" TAB "c d" TAB "e f", 1 ) // Returns "c d" TAB "e f"
    @endtsexample
    
    @see getField
    @see getFieldCount
    @see getWords
    @see getRecords
    @ingroup FieldManip */
       virtual string getFields(( string text, int startIndex, int endIndex=-1 )) {}
       /*! Replace the field in @a text at the given @a index with @a replacement.
    Fields in @a text must be separated by newlines and/or tabs.
    @param text A list of fields separated by newlines and/or tabs.
    @param index The zero-based index of the field to replace.
    @param replacement The string with which to replace the field.
    @return A new string with the field at the given @a index replaced by @a replacement or the original string if @a index is out of range.
    
    @tsexample
    setField( "a b" TAB "c d" TAB "e f", 1, "g h" ) // Returns "a b" TAB "g h" TAB "e f"
    @endtsexample
    
    @see getField
    @see setWord
    @see setRecord
    @ingroup FieldManip */
       virtual string setField(( string text, int index, string replacement )) {}
       /*! Remove the field in @a text at the given @a index.
    Fields in @a text must be separated by newlines and/or tabs.
    @param text A list of fields separated by newlines and/or tabs.
    @param index The zero-based index of the field in @a text.
    @return A new string with the field at the given index removed or the original string if @a index is out of range.
    
    @tsexample
    removeField( "a b" TAB "c d" TAB "e f", 1 ) // Returns "a b" TAB "e f"
    @endtsexample
    
    @see removeWord
    @see removeRecord
    @ingroup FieldManip */
       virtual string removeField(( string text, int index )) {}
       /*! Return the number of newline and/or tab separated fields in @a text.
    @param text A list of fields separated by newlines and/or tabs.
    @return The number of newline and/or tab sepearated elements in @a text.
    
    @tsexample
    getFieldCount( "a b" TAB "c d" TAB "e f" ) // Returns 3
    @endtsexample
    
    @see getWordCount
    @see getRecordCount
    @ingroup FieldManip */
       virtual int getFieldCount(( string text )) {}
       /*! Extract the record at the given @a index in the newline-separated list in @a text.
    Records in @a text must be separated by newlines.
    @param text A list of records separated by newlines.
    @param index The zero-based index of the record to extract.
    @return The record at the given index or "" if @a index is out of range.
    
    @tsexample
    getRecord( "a b" NL "c d" NL "e f", 1 ) // Returns "c d"
    @endtsexample
    
    @see getRecords
    @see getRecordCount
    @see getWord
    @see getField
    @ingroup FieldManip */
       virtual string getRecord(( string text, int index )) {}
       /*! Extract a range of records from the given @a startIndex onwards thru @a endIndex.
    Records in @a text must be separated by newlines.
    @param text A list of records separated by newlines.
    @param startIndex The zero-based index of the first record to extract from @a text.
    @param endIndex The zero-based index of the last record to extract from @a text.  If this is -1, all records beginning with @a startIndex are extracted from @a text.
    @return A string containing the specified range of records from @a text or "" if @a startIndex is out of range or greater than @a endIndex.
    
    @tsexample
    getRecords( "a b" NL "c d" NL "e f", 1 ) // Returns "c d" NL "e f"
    @endtsexample
    
    @see getRecord
    @see getRecordCount
    @see getWords
    @see getFields
    @ingroup FieldManip */
       virtual string getRecords(( string text, int startIndex, int endIndex=-1 )) {}
       /*! Replace the record in @a text at the given @a index with @a replacement.
    Records in @a text must be separated by newlines.
    @param text A list of records separated by newlines.
    @param index The zero-based index of the record to replace.
    @param replacement The string with which to replace the record.
    @return A new string with the record at the given @a index replaced by @a replacement or the original string if @a index is out of range.
    
    @tsexample
    setRecord( "a b" NL "c d" NL "e f", 1, "g h" ) // Returns "a b" NL "g h" NL "e f"
    @endtsexample
    
    @see getRecord
    @see setWord
    @see setField
    @ingroup FieldManip */
       virtual string setRecord(( string text, int index, string replacement )) {}
       /*! Remove the record in @a text at the given @a index.
    Records in @a text must be separated by newlines.
    @param text A list of records separated by newlines.
    @param index The zero-based index of the record in @a text.
    @return A new string with the record at the given @a index removed or the original string if @a index is out of range.
    
    @tsexample
    removeRecord( "a b" NL "c d" NL "e f", 1 ) // Returns "a b" NL "e f"
    @endtsexample
    
    @see removeWord
    @see removeField
    @ingroup FieldManip */
       virtual string removeRecord(( string text, int index )) {}
       /*! Return the number of newline-separated records in @a text.
    @param text A list of records separated by newlines.
    @return The number of newline-sepearated elements in @a text.
    
    @tsexample
    getRecordCount( "a b" NL "c d" NL "e f" ) // Returns 3
    @endtsexample
    
    @see getWordCount
    @see getFieldCount
    @ingroup FieldManip */
       virtual int getRecordCount(( string text )) {}
       /*! Return the first word in @a text.
    @param text A list of words separated by newlines, spaces, and/or tabs.
    @return The word at index 0 in @a text or "" if @a text is empty.
    
    @note This is equal to 
    @tsexample_nopar
    getWord( text, 0 )
    @endtsexample
    
    @see getWord
    @ingroup FieldManip */
       virtual string firstWord(( string text )) {}
       /*! Return all but the first word in @a text.
    @param text A list of words separated by newlines, spaces, and/or tabs.
    @return @a text with the first word removed.
    
    @note This is equal to 
    @tsexample_nopar
    getWords( text, 1 )
    @endtsexample
    
    @see getWords
    @ingroup FieldManip */
       virtual string restWords(( string text )) {}
       virtual string nextToken() {}
       /*! @brief Returns the string from a tag string.
    @see \ref syntaxDataTypes
    @ingroup Networking */
       virtual string detag(( string str )) {}
       virtual string getTag() {}
       virtual void echo() {}
       virtual void warn() {}
       virtual void error() {}
       virtual void hack() {}
       virtual void info() {}
       virtual bool launchExternalApplication(( string filename, string cmdline )) {}
       virtual int launchExternalApplicationThreaded(( string appHandle, string filename, string cmdline, string callback, string object )) {}
       virtual bool killProcess(( int processId )) {}
       /*! @brief Logs the value of the given variable to the console.
    
    Prints a string of the form "&lt;variableName&gt; = &lt;variable value&gt;" to the console.
    
    @param variableName Name of the local or global variable to print.
    
    @tsexample
    %var = 1;
    debugv( "%var" ); // Prints "%var = 1"
    @endtsexample
    
    @ingroup Debugging */
       virtual void debugv(( string variableName )) {}
       /*! @brief Replace all characters in @a text that need to be escaped for the string to be a valid string literal with their respective escape sequences.
    
    All characters in @a text that cannot appear in a string literal will be replaced by an escape sequence (\\n, \\t, etc).
    
    The primary use of this function is for converting strings suitable for being passed as string literals to the TorqueScript compiler.
    
    @param text A string
    @return A duplicate of the text parameter with all unescaped characters that cannot appear in string literals replaced by their respective escape sequences.
    
    @tsxample
    expandEscape( "str" NL "ing" ) // Returns "str\ning".
    @endtsxample
    
    @see collapseEscape
    @ingroup Strings */
       virtual string expandEscape(( string text )) {}
       /*! Replace all escape sequences in @a text with their respective character codes.
    
    This function replaces all escape sequences (\\n, \\t, etc) in the given string with the respective characters they represent.
    
    The primary use of this function is for converting strings from their literal form into their compiled/translated form, as is normally done by the TorqueScript compiler.
    
    @param text A string.
    @return A duplicate of @a text with all escape sequences replaced by their respective character codes.
    
    @tsexample
    // Print:
    //
    //    str
    //    ing
    //
    // to the console.  Note how the backslash in the string must be escaped here
    // in order to prevent the TorqueScript compiler from collapsing the escape
    // sequence in the resulting string.
    echo( collapseEscape( "str\ning" ) );
    @endtsexample
    
    @see expandEscape
    
    @ingroup Strings */
       virtual string collapseEscape(( string text )) {}
       /*! @brief Determines how log files are written.
    
    Sets the operational mode of the console logging system.
    
    @param mode Parameter specifying the logging mode.  This can be:
    - 1: Open and close the console log file for each seperate string of output.  This will ensure that all parts get written out to disk and that no parts remain in intermediate buffers even if the process crashes.
    - 2: Keep the log file open and write to it continuously.  This will make the system operate faster but if the process crashes, parts of the output may not have been written to disk yet and will be missing from the log.
    
    Additionally, when changing the log mode and thus opening a new log file, either of the two mode values may be combined by binary OR with 0x4 to cause the logging system to flush all console log messages that had already been issued to the console system into the newly created log file.
    
    @note Xbox 360 does not support logging to a file. Use Platform::OutputDebugStr in C++ instead.@ingroup Logging */
       virtual void setLogMode(( int mode )) {}
       /*! Shut down the engine and exit its process.
    This function cleanly uninitializes the engine and then exits back to the system with a process exit status indicating a clean exit.
    
    @see quitWithErrorMessage
    
    @ingroup Platform */
       virtual void quit(()) {}
       virtual bool isQuitRequested(()) {}
       /*! Display an error message box showing the given @a message and then shut down the engine and exit its process.
    This function cleanly uninitialized the engine and then exits back to the system with a process exit status indicating an error.
    
    @param message The message to log to the console and show in an error message box.
    
    @see quit
    
    @ingroup Platform */
       virtual void quitWithErrorMessage(( string message )) {}
       /*! Open the given URL or file in the user's web browser.
    
    @param address The address to open.  If this is not prefixed by a protocol specifier ("...://"), then the function checks whether the address refers to a file or directory and if so, prepends "file://" to @a adress; if the file check fails, "http://" is prepended to @a address.
    
    @tsexample
    gotoWebPage( "http://www.garagegames.com" );
    @endtsexample
    
    @ingroup Platform */
       virtual void gotoWebPage(( string address )) {}
       /*! Test whether Torque is running in web-deployment mode.
    In this mode, Torque will usually run within a browser and certain restrictions apply (e.g. Torque will not be able to enter fullscreen exclusive mode).
    @return True if Torque is running in web-deployment mode.
    @ingroup Platform */
       virtual bool getWebDeployment(()) {}
       /*! Count the number of bits that are set in the given 32 bit integer.
    @param v An integer value.
    
    @return The number of bits that are set in @a v.
    
    @ingroup Utilities */
       virtual int countBits(( int v )) {}
       /*! Generate a new universally unique identifier (UUID).
    
    @return A newly generated UUID.
    
    @ingroup Utilities */
       virtual string generateUUID(()) {}
       virtual string call() {}
       /*! Get the absolute path to the file in which the compiled code for the given script file will be stored.
    @param scriptFileName %Path to the .cs script file.
    @return The absolute path to the .dso file for the given script file.
    
    @note The compiler will store newly compiled DSOs in the prefs path but pre-existing DSOs will be loaded from the current paths.
    
    @see compile
    @see getPrefsPath
    @ingroup Scripting */
       virtual string getDSOPath(( string scriptFileName )) {}
       /*! Compile a file to bytecode.
    
    This function will read the TorqueScript code in the specified file, compile it to internal bytecode, and, if DSO generation is enabled or @a overrideNoDDSO is true, will store the compiled code in a .dso file in the current DSO path mirrorring the path of @a fileName.
    
    @param fileName Path to the file to compile to bytecode.
    @param overrideNoDSO If true, force generation of DSOs even if the engine is compiled to not generate write compiled code to DSO files.
    
    @return True if the file was successfully compiled, false if not.
    
    @note The definitions contained in the given file will not be made available and no code will actually be executed.  Use exec() for that.
    
    @see getDSOPath
    @see exec
    @ingroup Scripting */
       virtual bool compile(( string fileName, bool overrideNoDSO=false )) {}
       /*! Execute the given script file.
    @param fileName Path to the file to execute
    @param noCalls Deprecated
    @param journalScript Deprecated
    @return True if the script was successfully executed, false if not.
    
    @tsexample
    // Execute the init.cs script file found in the same directory as the current script file.
    exec( "./init.cs" );
    @endtsexample
    
    @see compile
    @see eval
    @ingroup Scripting */
       virtual bool exec(( string fileName, bool noCalls=false, bool journalScript=false )) {}
       virtual string eval() {}
       virtual string getVariable() {}
       virtual void setVariable() {}
       virtual bool isFunction() {}
       virtual string getFunctionPackage() {}
       virtual bool isMethod() {}
       virtual string getMethodPackage() {}
       virtual bool isDefined() {}
       virtual bool isCurrentScriptToolScript() {}
       virtual string getModNameFromPath() {}
       virtual void pushInstantGroup() {}
       virtual void popInstantGroup() {}
       virtual string getPrefsPath() {}
       virtual bool execPrefs() {}
       /*! Write out the definitions of all global variables matching the given name @a pattern.
    If @a fileName is not "", the variable definitions are written to the specified file.  Otherwise the definitions will be printed to the console.
    
    The output are valid TorqueScript statements that can be executed to restore the global variable values.
    
    @param pattern A global variable name pattern.  Must begin with '$'.
    @param filename %Path of the file to which to write the definitions or "" to write the definitions to the console.
    @param append If true and @a fileName is not "", then the definitions are appended to the specified file. Otherwise existing contents of the file (if any) will be overwritten.
    
    @tsexample
    // Write out all preference variables to a prefs.cs file.
    export( "$prefs::*", "prefs.cs" );
    @endtsexample
    
    @ingroup Scripting */
       virtual void export(( string pattern, string filename="", bool append=false )) {}
       /*! Undefine all global variables matching the given name @a pattern.
    @param pattern A global variable name pattern.  Must begin with '$'.
    @tsexample
    // Define a global variable in the "My" namespace.
    $My::Variable = "value";
    
    // Undefine all variable in the "My" namespace.
    deleteVariables( "$My::*" );
    @endtsexample
    
    @see strIsMatchExpr
    @ingroup Scripting */
       virtual void deleteVariables(( string pattern )) {}
       /*! Enable or disable tracing in the script code VM.
    
    When enabled, the script code runtime will trace the invocation and returns from all functions that are called and log them to the console. This is helpful in observing the flow of the script program.
    
    @param enable New setting for script trace execution, on by default.
    @ingroup Debugging */
       virtual void trace(( bool enable=true )) {}
       /*! Enable or disable step tracing in the script code VM.
    
    When tracing is on, the script code runtime will trace how deep it in code and log with '#' symbol the current depth to the console.  This is helpful in finding what the script program flow is.
    
    @param enable New setting for script step trace execution.
    @ingroup Debugging */
       virtual void stepTrace(( bool enable=true )) {}
       /*! Test whether the engine has been compiled with TORQUE_SHIPPING, i.e. in a form meant for final release.
    
    @return True if this is a shipping build; false otherwise.
    
    @ingroup Platform */
       virtual bool isShippingBuild(()) {}
       /*! Test whether the engine has been compiled with TORQUE_DEBUG, i.e. if it includes debugging functionality.
    
    @return True if this is a debug build; false otherwise.
    
    @ingroup Platform */
       virtual bool isDebugBuild(()) {}
       /*! Test whether the engine has been compiled with TORQUE_TOOLS, i.e. if it includes tool-related functionality.
    
    @return True if this is a tool build; false otherwise.
    
    @ingroup Platform */
       virtual bool isToolBuild(()) {}
       virtual string getEngineVersion(()) {}
       /*! @brief Prints the scripting call stack to the console log.
    
    Used to trace functions called from within functions. Can help discover what functions were called (and not yet exited) before the current point in scripts.
    
    @ingroup Debugging */
       virtual void backtrace(()) {}
       virtual void dumpScope() {}
       virtual string getScopeName() {}
       /*! @brief Returns true if the identifier is the name of a declared package.
    
    @ingroup Packages
     */
       virtual bool isPackage(( String identifier )) {}
       /*! @brief Activates an existing package.
    
    The activation occurs by updating the namespace linkage of existing functions and methods. If the package is already activated the function does nothing.
    @ingroup Packages
     */
       virtual void activatePackage(( String packageName )) {}
       /*! @brief Deactivates a previously activated package.
    
    The package is deactivated by removing its namespace linkages to any function or method. If there are any packages above this one in the stack they are deactivated as well. If the package is not on the stack this function does nothing.
    @ingroup Packages
     */
       virtual void deactivatePackage(( String packageName )) {}
       /*! @brief Returns a space delimited list of the active packages in stack order.
    
    @ingroup Packages
     */
       virtual string getPackageList(()) {}
       /*! @brief Returns true if the passed identifier is the name of a declared class.
    
    @ingroup Console */
       virtual bool isClass(( string identifier )) {}
       /*! @brief Returns true if the class is derived from the super class.
    
    If either class doesn't exist this returns false.
    @param className The class name.
    @param superClassName The super class to look for.
    @ingroup Console */
       virtual bool isMemberOfClass(( string className, string superClassName )) {}
       /*! @brief Returns the description string for the named class.
    
    @param className The name of the class.
    @return The class description in string format.
    @ingroup Console */
       virtual string getDescriptionOfClass(( string className )) {}
       /*! @brief Returns the category of the given class.
    
    @param className The name of the class.
    @ingroup Console */
       virtual string getCategoryOfClass(( string className )) {}
       /*! @brief Returns a list of classes that derive from the named class.
    
    If the named class is omitted this dumps all the classes.
    @param className The optional base class name.
    @return A tab delimited list of classes.
    @ingroup Editors
    @internal */
       virtual string enumerateConsoleClasses(( string className="" )) {}
       /*! @brief Provide a list of classes that belong to the given category.
    
    @param category The category name.
    @return A tab delimited list of classes.
    @ingroup Editors
    @internal */
       virtual string enumerateConsoleClassesByCategory(( String category )) {}
       virtual void debugNetStart(( string val )) {}
       virtual void serverCmdNetDebugSessionStart(( NetConnection conn, string val )) {}
       /*! @brief Dumps network statistics for each class to the console.
    
    @note This method only works when TORQUE_NET_STATS is defined in torqueConfig.h.
    @ingroup Networking
     */
       virtual void dumpNetStats(()) {}
       virtual void debugNetEnd(()) {}
       virtual void serverCmdNetDebugSessionStop(( NetConnection conn )) {}
       /*! @brief Determines the memory consumption of a class or object.
    
    @param objectOrClass The object or class being measured.
    @return Returns the total size of an object in bytes.
    @ingroup Debugging
     */
       virtual int sizeof(( string objectOrClass )) {}
       /*! Dumps the engine scripting documentation to the specified file overwriting any existing content.
    @param outputFile The relative or absolute output file path and name.
    @return Returns true if successful.
    @ingroup Console */
       virtual bool dumpEngineDocs(( string outputFile )) {}
       virtual int getEnumTypeID() {}
       virtual int getEnumItemCount() {}
       virtual string getEnumItemName() {}
       virtual int getEnumItemValue() {}
       /*! @brief Returns the first file in the directory system matching the given pattern.
    
    Use the corresponding findNextFile() to step through the results.  If you're only interested in the number of files returned by the pattern match, use getFileCount().
    
    This function differs from findFirstFileMultiExpr() in that it supports a single search pattern being passed in.
    
    @note You cannot run multiple simultaneous file system searches with these functions.  Each call to findFirstFile() and findFirstFileMultiExpr() initiates a new search and renders a previous search invalid.
    
    @param pattern The path and file name pattern to match against.
    @param recurse If true, the search will exhaustively recurse into subdirectories of the given path and match the given filename pattern.
    @return The path of the first file matched by the search or an empty string if no matching file could be found.
    
    @tsexample
    // Execute all .cs files in a subdirectory and its subdirectories.
    for( %file = findFirstFile( "subdirectory/*.cs" ); %file !$= ""; %file = findNextFile() )
       exec( %file );
    @endtsexample
    
    @see findNextFile()@see getFileCount()@see findFirstFileMultiExpr()@ingroup FileSearches */
       virtual string findFirstFile(( string pattern, bool recurse=true )) {}
       /*! @brief Returns the next file matching a search begun in findFirstFile().
    
    @param pattern The path and file name pattern to match against.  This is optional and may be left out as it is not used by the code.  It is here for legacy reasons.
    @return The path of the next filename matched by the search or an empty string if no more files match.
    
    @tsexample
    // Execute all .cs files in a subdirectory and its subdirectories.
    for( %file = findFirstFile( "subdirectory/*.cs" ); %file !$= ""; %file = findNextFile() )
       exec( %file );
    @endtsexample
    
    @see findFirstFile()@ingroup FileSearches */
       virtual string findNextFile(( string pattern="" )) {}
       /*! @brief Returns the number of files in the directory tree that match the given patterns
    
    This function differs from getFileCountMultiExpr() in that it supports a single search pattern being passed in.
    
    If you're interested in a list of files that match the given pattern and not just the number of files, use findFirstFile() and findNextFile().
    
    @param pattern The path and file name pattern to match against.
    @param recurse If true, the search will exhaustively recurse into subdirectories of the given path and match the given filename pattern counting files in subdirectories.
    @return Number of files located using the pattern
    
    @tsexample
    // Count the number of .cs files in a subdirectory and its subdirectories.
    getFileCount( "subdirectory/*.cs" );
    @endtsexample
    
    @see findFirstFile()@see findNextFile()@see getFileCountMultiExpr()@ingroup FileSearches */
       virtual int getFileCount(( string pattern, bool recurse=true )) {}
       /*! @brief Returns the first file in the directory system matching the given patterns.
    
    Use the corresponding findNextFileMultiExpr() to step through the results.  If you're only interested in the number of files returned by the pattern match, use getFileCountMultiExpr().
    
    This function differs from findFirstFile() in that it supports multiple search patterns to be passed in.
    
    @note You cannot run multiple simultaneous file system searches with these functions.  Each call to findFirstFile() and findFirstFileMultiExpr() initiates a new search and renders a previous search invalid.
    
    @param pattern The path and file name pattern to match against, such as *.cs.  Separate multiple patterns with TABs.  For example: "*.cs" TAB "*.dso"
    @param recurse If true, the search will exhaustively recurse into subdirectories of the given path and match the given filename patterns.
    @return String of the first matching file path, or an empty string if no matching files were found.
    
    @tsexample
    // Find all DTS or Collada models
    %filePatterns = "*.dts" TAB "*.dae";
    %fullPath = findFirstFileMultiExpr( %filePatterns );
    while ( %fullPath !$= "" )
    {
       echo( %fullPath );
       %fullPath = findNextFileMultiExpr( %filePatterns );
    }
    @endtsexample
    
    @see findNextFileMultiExpr()@see getFileCountMultiExpr()@see findFirstFile()@ingroup FileSearches */
       virtual string findFirstFileMultiExpr(( string pattern, bool recurse=true )) {}
       /*! @brief Returns the next file matching a search begun in findFirstFileMultiExpr().
    
    @param pattern The path and file name pattern to match against.  This is optional and may be left out as it is not used by the code.  It is here for legacy reasons.
    @return String of the next matching file path, or an empty string if no matching files were found.
    
    @tsexample
    // Find all DTS or Collada models
    %filePatterns = "*.dts" TAB "*.dae";
    %fullPath = findFirstFileMultiExpr( %filePatterns );
    while ( %fullPath !$= "" )
    {
       echo( %fullPath );
       %fullPath = findNextFileMultiExpr( %filePatterns );
    }
    @endtsexample
    
    @see findFirstFileMultiExpr()@ingroup FileSearches */
       virtual string findNextFileMultiExpr(( string pattern="" )) {}
       /*! @brief Returns the number of files in the directory tree that match the given patterns
    
    If you're interested in a list of files that match the given patterns and not just the number of files, use findFirstFileMultiExpr() and findNextFileMultiExpr().
    
    @param pattern The path and file name pattern to match against, such as *.cs.  Separate multiple patterns with TABs.  For example: "*.cs" TAB "*.dso"
    @param recurse If true, the search will exhaustively recurse into subdirectories of the given path and match the given filename pattern.
    @return Number of files located using the patterns
    
    @tsexample
    // Count all DTS or Collada models
    %filePatterns = "*.dts" TAB "*.dae";
    echo( "Nunmer of shape files:" SPC getFileCountMultiExpr( %filePatterns ) );
    @endtsexample
    
    @see findFirstFileMultiExpr()@see findNextFileMultiExpr()@ingroup FileSearches */
       virtual int getFileCountMultiExpr(( string pattern, bool recurse=true )) {}
       /*! @brief Provides the CRC checksum of the given file.
    
    @param fileName The path to the file.
    @return The calculated CRC checksum of the file, or -1 if the file could not be found.
    @ingroup FileSystem */
       virtual int getFileCRC(( string fileName )) {}
       virtual int crc32() {}
       /*! @brief Provides the CRC checksum of the given file.
    
    @param fileName The path to the file.
    @return The calculated CRC checksum of the file, or -1 if the file could not be found.
    @ingroup FileSystem */
       virtual string getFileCRC32(( string fileName )) {}
       /*! @brief Determines if the specified file exists or not
    
    @param fileName The path to the file.
    @return Returns true if the file was found.
    @ingroup FileSystem */
       virtual bool isFile(( string fileName )) {}
       /*! @brief Determines if the specified file exists or not
    
    @param fileName The path to the file.
    @return Returns true if the file was found.
    @ingroup FileSystem */
       virtual bool fileExists(( string fileName )) {}
       /*! @brief Determines if a specified directory exists or not
    
    @param directory String containing path in the form of "foo/bar"
    @return Returns true if the directory was found.
    @note Do not include a trailing slash '/'.
    @ingroup FileSystem */
       virtual bool IsDirectory(( string directory )) {}
       /*! @brief Determines if a file name can be written to using File I/O
    
    @param fileName Name and path of file to check
    @return Returns true if the file can be written to.
    @ingroup FileSystem */
       virtual bool isWriteableFileName(( string fileName )) {}
       /*! @brief Start watching resources for file changes
    
    Typically this is called during initializeCore().
    
    @see stopFileChangeNotifications()
    @ingroup FileSystem */
       virtual void startFileChangeNotifications(()) {}
       /*! @brief Stop watching resources for file changes
    
    Typically this is called during shutdownCore().
    
    @see startFileChangeNotifications()
    @ingroup FileSystem */
       virtual void stopFileChangeNotifications(()) {}
       /*! @brief Gathers a list of directories starting at the given path.
    
    @param path String containing the path of the directory
    @param depth Depth of search, as in how many subdirectories to parse through
    @return Tab delimited string containing list of directories found during search, "" if no files were found
    @ingroup FileSystem */
       virtual string getDirectoryList(( string path, int depth=0 )) {}
       /*! @brief Determines the size of a file on disk
    
    @param fileName Name and path of the file to check
    @return Returns filesize in KB, or -1 if no file
    @ingroup FileSystem */
       virtual int fileSize(( string fileName )) {}
       /*! @brief Returns a platform specific formatted string with the last modified time for the file.
    
    @param fileName Name and path of file to check
    @return Formatted string (OS specific) containing modified time, "9/3/2010 12:33:47 PM" for example
    @ingroup FileSystem */
       virtual string fileModifiedTime(( string fileName )) {}
       /*! @brief Returns a platform specific formatted string with the creation time for the file.@param fileName Name and path of file to check
    @return Formatted string (OS specific) containing created time, "9/3/2010 12:33:47 PM" for example
    @ingroup FileSystem */
       virtual string fileCreatedTime(( string fileName )) {}
       /*! @brief Delete a file from the hard drive
    
    @param path Name and path of the file to delete
    @note THERE IS NO RECOVERY FROM THIS. Deleted file is gone for good.
    @return True if file was successfully deleted
    @ingroup FileSystem */
       virtual bool fileDelete(( string path )) {}
       virtual bool removeFolderWithAllFiles(( string path )) {}
       /*! @brief Get the extension of a file
    
    @param fileName Name and path of file
    @return String containing the extension, such as ".exe" or ".cs"
    @ingroup FileSystem */
       virtual string fileExt(( string fileName )) {}
       /*! @brief Get the base of a file name (removes extension)
    
    @param fileName Name and path of file to check
    @return String containing the file name, minus extension
    @ingroup FileSystem */
       virtual string fileBase(( string fileName )) {}
       /*! @brief Get the file name of a file (removes extension and path)
    
    @param fileName Name and path of file to check
    @return String containing the file name, minus extension and path
    @ingroup FileSystem */
       virtual string fileName(( string fileName )) {}
       /*! @brief Get the path of a file (removes name and extension)
    
    @param fileName Name and path of file to check
    @return String containing the path, minus name and extension
    @ingroup FileSystem */
       virtual string filePath(( string fileName )) {}
       /*! @brief Reports the current directory
    
    @return String containing full file path of working directory
    @ingroup FileSystem */
       virtual string getWorkingDirectory(()) {}
       /*! @brief Converts a relative file path to a full path
    
    For example, "./console.log" becomes "C:/Torque/t3d/examples/FPS Example/game/console.log"
    @param path Name of file or path to check
    @param cwd Optional current working directory from which to build the full path.
    @return String containing non-relative directory of path
    @ingroup FileSystem */
       virtual string makeFullPath(( string path, string cwd="" )) {}
       /*! @brief Turns a full or local path to a relative one
    
    For example, "./game/art" becomes "game/art"
    @param path Full path (may include a file) to convert
    @param to Optional base path used for the conversion.  If not supplied the current working directory is used.
    @returns String containing relative path
    @ingroup FileSystem */
       virtual string makeRelativePath(( string path, string to="" )) {}
       /*! @brief Combines two separate strings containing a file path and file name together into a single string
    
    @param path String containing file path
    @param file String containing file name
    @return String containing concatenated file name and path
    @ingroup FileSystem */
       virtual string pathConcat(( string path, string file )) {}
       /*! @brief Gets the name of the game's executable
    
    @return String containing this game's executable name
    @ingroup FileSystem */
       virtual string getExecutableName(()) {}
       /*! @brief Get the absolute path to the directory that contains the main.cs script from which the engine was started.
    
    This directory will usually contain all the game assets and, in a user-side game installation, will usually be read-only.
    
    @return The path to the main game assets.
    
    @ingroup FileSystem
     */
       virtual string getMainDotCsDir(()) {}
       /*! @brief Copy a file to a new location.
    @param fromFile %Path of the file to copy.
    @param toFile %Path where to copy @a fromFile to.
    @param noOverwrite If true, then @a fromFile will not overwrite a file that may already exist at @a toFile.
    @return True if the file was successfully copied, false otherwise.
    @note Only present in a Tools build of Torque.
    @ingroup FileSystem */
       virtual bool pathCopy(( string fromFile, string toFile, bool noOverwrite=true )) {}
       /*! @brief Return the current working directory.
    
    @return The absolute path of the current working directory.
    
    @note Only present in a Tools build of Torque.
    @see getWorkingDirectory()@ingroup FileSystem */
       virtual string getCurrentDirectory(()) {}
       /*! @brief Set the current working directory.
    
    @param path The absolute or relative (to the current working directory) path of the directory which should be made the new working directory.
    
    @return True if the working directory was successfully changed to @a path, false otherwise.
    
    @note Only present in a Tools build of Torque.
    @ingroup FileSystem */
       virtual bool setCurrentDirectory(( string path )) {}
       /*! @brief Create the given directory or the path leading to the given filename.
    
    If @a path ends in a trailing slash, then all components in the given path will be created as directories (if not already in place).  If @a path, does @b not end in a trailing slash, then the last component of the path is taken to be a file name and only the directory components of the path will be created.
    
    @param path The path to create.
    
    @note Only present in a Tools build of Torque.
    @ingroup FileSystem */
       virtual bool createPath(( string path )) {}
       virtual string expandFilename() {}
       virtual string expandOldFilename() {}
       virtual string collapseFilename() {}
       virtual void setScriptPathExpando() {}
       virtual void removeScriptPathExpando() {}
       virtual bool isScriptPathExpando() {}
       virtual int nameToID() {}
       virtual bool isObject() {}
       virtual int spawnObject() {}
       virtual void cancel() {}
       virtual void cancelAll() {}
       virtual bool isEventPending() {}
       virtual int getEventTimeLeft() {}
       virtual int getScheduleDuration() {}
       virtual int getTimeSinceStart() {}
       virtual int schedule() {}
       virtual string getUniqueName() {}
       virtual string getUniqueInternalName() {}
       virtual bool isValidObjectName() {}
       /*! Delete all the datablocks we've downloaded.
    
    This is usually done in preparation of downloading a new set of datablocks, such as occurs on a mission change, but it's also good post-mission cleanup. */
       virtual void deleteDataBlocks(()) {}
       /*! @brief Serialize the object to a file.
    
    @param object The object to serialize.
    @param filename The file name and path.
    @ingroup Console
     */
       virtual bool saveObject(( SimObject object, string filename )) {}
       /*! @brief Loads a serialized object from a file.
    
    @param Name and path to text file containing the object
    @ingroup Console
     */
       virtual string loadObject(( string filename )) {}
       /*! @brief Initializes and open the telnet console.
    
    @param port^^  Port to listen on for console connections (0 will shut down listening).
    @param consolePass Password for read/write access to console.
    @param listenPass  Password for read access to console.
    @param writerPass  Password for write-only access to console.
    @param remoteEcho  [optional] Enable echoing back to the client, off by default.
    
    @ingroup Debugging */
       virtual void telnetSetParameters(( int port, String consolePass, String listenPass, String writerPass, bool remoteEcho=false )) {}
       virtual void dbgSetParameters() {}
       virtual bool dbgIsConnected() {}
       virtual void dbgDisconnect() {}
       virtual void DNetSetLogging() {}
       /*! initialize Calendar manager class */
       virtual void CmCalendarInit(( int serverID )) {}
       virtual void SendGameDateTime(( NetConnection client )) {}
       virtual string getGameTime(()) {}
       virtual int getCurrentSeasonNum() {}
       /*! initialize CmSnowdrift manager class */
       virtual void CmSnowdriftInit(()) {}
       virtual void DebugSpawnSnowdriftAt(( int terID, int x, int y )) {}
       virtual void DebugSpawnSnowdriftRandom(()) {}
       virtual void DebugForceMeltSnow(()) {}
       /*! initialize Weather manager class */
       virtual void CmWeatherInit(()) {}
       virtual void SendWeather(( NetConnection client )) {}
       virtual void forceSetWeather(( string weather )) {}
       virtual string getCurrentWeather(()) {}
       virtual void printCurrentWeather(()) {}
       virtual void Forest_TestFindTree(( int valForestKey )) {}
       virtual void create450Forests(()) {}
       /*! Forces main-thread maintenance for all forests */
       virtual void forestMainThreadMaintenance(( int daysToAdd=U32_MAX )) {}
       /*! Forces a stretched maintenance for all forests */
       virtual void forestStretchedMaintenance(( int daysToAdd=U32_MAX )) {}
       virtual void CreateTestTree(( int geoId, int family, int age, int health )) {}
       virtual void DeleteTestTree(( int geoId )) {}
       virtual void parseForestMaintenanceXmlSettings(()) {}
       /*! Returns the count of active DDSs files in memory.
    @ingroup Rendering
     */
       virtual int getActiveDDSFiles(()) {}
       /*! Returns image info in the following format: width TAB height TAB bytesPerPixel. It will return an empty string if the file is not found.
    @ingroup Rendering
     */
       virtual string getBitmapInfo(( string filename )) {}
       /*! Add two vectors.
    @param a The first vector.
    @param b The second vector.
    @return The vector @a a + @a b.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorAdd( %a, %b );
    //
    // The sum of vector a, (ax, ay, az), and vector b, (bx, by, bz) is:
    //
    //     a + b = ( ax + bx, ay + by, az + bz )
    //
    //-----------------------------------------------------------------------------
    %a = "1 0 0";
    %b = "0 1 0";
    
    // %r = "( 1 + 0, 0 + 1, 0 + 0 )";
    // %r = "1 1 0";
    %r = VectorAdd( %a, %b );
    @endtsexample
    
    @ingroup Vectors */
       virtual string VectorAdd(( VectorF a, VectorF b )) {}
       /*! Subtract two vectors.
    @param a The first vector.
    @param b The second vector.
    @return The vector @a a - @a b.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorSub( %a, %b );
    //
    // The difference of vector a, (ax, ay, az), and vector b, (bx, by, bz) is:
    //
    //     a - b = ( ax - bx, ay - by, az - bz )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 0 0";
    %b = "0 1 0";
    
    // %r = "( 1 - 0, 0 - 1, 0 - 0 )";
    // %r = "1 -1 0";
    %r = VectorSub( %a, %b );
    @endtsexample
    
    @ingroup Vectors */
       virtual string VectorSub(( VectorF a, VectorF b )) {}
       /*! Scales a vector by a scalar.
    @param a The vector to scale.
    @param scalar The scale factor.
    @return The vector @a a * @a scalar.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorScale( %a, %v );
    //
    // Scaling vector a, (ax, ay, az), but the scalar, v, is:
    //
    //     a * v = ( ax * v, ay * v, az * v )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 1 0";
    %v = "2";
    
    // %r = "( 1 * 2, 1 * 2, 0 * 2 )";
    // %r = "2 2 0";
    %r = VectorScale( %a, %v );
    @endtsexample
    
    @ingroup Vectors */
       virtual string VectorScale(( VectorF a, float scalar )) {}
       /*! Brings a vector into its unit form, i.e. such that it has the magnitute 1.
    @param v The vector to normalize.
    @return The vector @a v scaled to length 1.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorNormalize( %a );
    //
    // The normalized vector a, (ax, ay, az), is:
    //
    //     a^ = a / ||a||
    //        = ( ax / ||a||, ay / ||a||, az / ||a|| )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 1 0";
    %l = 1.414;
    
    // %r = "( 1 / 1.141, 1 / 1.141, 0 / 1.141 )";
    // %r = "0.707 0.707 0";
    %r = VectorNormalize( %a );
    @endtsexample
    
    @ingroup Vectors */
       virtual string VectorNormalize(( VectorF v )) {}
       /*! Compute the dot product of two vectors.
    @param a The first vector.
    @param b The second vector.
    @return The dot product @a a * @a b.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorDot( %a, %b );
    //
    // The dot product between vector a, (ax, ay, az), and vector b, (bx, by, bz), is:
    //
    //     a . b = ( ax * bx + ay * by + az * bz )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 1 0";
    %b = "2 0 1";
    
    // %r = "( 1 * 2 + 1 * 0 + 0 * 1 )";
    // %r = 2;
    %r = VectorDot( %a, %b );
    @endtsexample
    
    @ingroup Vectors */
       virtual float VectorDot(( VectorF a, VectorF b )) {}
       /*! Calculcate the cross product of two vectors.
    @param a The first vector.
    @param b The second vector.
    @return The cross product @a x @a b.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorCross( %a, %b );
    //
    // The cross product of vector a, (ax, ay, az), and vector b, (bx, by, bz), is
    //
    //     a x b = ( ( ay * bz ) - ( az * by ), ( az * bx ) - ( ax * bz ), ( ax * by ) - ( ay * bx ) )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 1 0";
    %b = "2 0 1";
    
    // %r = "( ( 1 * 1 ) - ( 0 * 0 ), ( 0 * 2 ) - ( 1 * 1 ), ( 1 * 0 ) - ( 1 * 2 ) )";
    // %r = "1 -1 -2";
    %r = VectorCross( %a, %b );
    @endtsexample
    
    @ingroup Vectors */
       virtual string VectorCross(( VectorF a, VectorF b )) {}
       /*! Compute the distance between two vectors.
    @param a The first vector.
    @param b The second vector.
    @return The length( @a b - @a a ).
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorDist( %a, %b );
    //
    // The distance between vector a, (ax, ay, az), and vector b, (bx, by, bz), is
    //
    //     a -&gt; b = ||( b - a )||
    //            = ||( bx - ax, by - ay, bz - az )||
    //            = mSqrt( ( bx - ax ) * ( bx - ax ) + ( by - ay ) * ( by - ay ) + ( bz - az ) * ( bz - az ) )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 1 0";
    %b = "2 0 1";
    
    // %r = mSqrt( ( 2 - 1 ) * ( 2 - 1) + ( 0 - 1 ) * ( 0 - 1 ) + ( 1 - 0 ) * ( 1 - 0 ) );
    // %r = mSqrt( 3 );
    %r = VectorDist( %a, %b );
    @endtsexample
    
    @ingroup Vectors */
       virtual float VectorDist(( VectorF a, VectorF b )) {}
       /*! Calculate the magnitude of the given vector.
    @param v A vector.
    @return The length of vector @a v.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorLen( %a );
    //
    // The length or magnitude of  vector a, (ax, ay, az), is:
    //
    //     ||a|| = Sqrt( ax * ax + ay * ay + az * az )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 1 0";
    
    // %r = mSqrt( 1 * 1 + 1 * 1 + 0 * 0 );
    // %r = mSqrt( 2 );
    // %r = 1.414;
    %r = VectorLen( %a );
    @endtsexample
    
    @ingroup Vectors */
       virtual float VectorLen(( VectorF v )) {}
       /*! Create an orthogonal basis from the given vector.
    @param aaf The vector to create the orthogonal basis from.
    @return A matrix representing the orthogonal basis.
    @ingroup Vectors */
       virtual string VectorOrthoBasis(( AngAxisF aa )) {}
       /*! Linearly interpolate between two vectors by @a t.
    @param a Vector to start interpolation from.
    @param b Vector to interpolate to.
    @param t Interpolation factor (0-1).  At zero, @a a is returned and at one, @a b is returned.  In between, an interpolated vector between @a a and @a b is returned.
    @return An interpolated vector between @a a and @a b.
    
    @tsexample
    //-----------------------------------------------------------------------------
    //
    // VectorLerp( %a, %b );
    //
    // The point between vector a, (ax, ay, az), and vector b, (bx, by, bz), which is
    // weighted by the interpolation factor, t, is
    //
    //     r = a + t * ( b - a )
    //       = ( ax + t * ( bx - ax ), ay + t * ( by - ay ), az + t * ( bz - az ) )
    //
    //-----------------------------------------------------------------------------
    
    %a = "1 1 0";
    %b = "2 0 1";
    %v = "0.25";
    
    // %r = "( 1 + 0.25 * ( 2 - 1 ), 1 + 0.25 * ( 0 - 1 ), 0 + 0.25 * ( 1 - 0 ) )";
    // %r = "1.25 0.75 0.25";
    %r = VectorLerp( %a, %b );
    @endtsexample
    
    @ingroup Vectors */
       virtual string VectorLerp(( VectorF a, VectorF b, float t )) {}
       /*! Create a transform from the given translation and orientation.
    @param position The translation vector for the transform.
    @param orientation The axis and rotation that orients the transform.
    @return A transform based on the given position and orientation.
    @ingroup Matrices */
       virtual string MatrixCreate(( VectorF position, AngAxisF orientation )) {}
       /*! @Create a matrix from the given rotations.
    
    @param Vector3F X, Y, and Z rotation in *radians*.
    @return A transform based on the given orientation.
    @ingroup Matrices */
       virtual string MatrixCreateFromEuler(( Point3F angles )) {}
       /*! @brief Multiply the two matrices.
    
    @param left First transform.
    @param right Right transform.
    @return Concatenation of the two transforms.
    @ingroup Matrices */
       virtual string MatrixMultiply(( TransformF left, TransformF right )) {}
       /*! @brief Multiply the vector by the transform assuming that w=0.
    
    This function will multiply the given vector by the given transform such that translation will not affect the vector.
    
    @param transform A transform.
    @param vector A vector.
    @return The transformed vector.
    @ingroup Matrices */
       virtual string MatrixMulVector(( TransformF transform, VectorF vector )) {}
       /*! @brief Multiply the given point by the given transform assuming that w=1.
    
    This function will multiply the given vector such that translation with take effect.
    @param transform A transform.
    @param point A vector.
    @return The transformed vector.
    @ingroup Matrices */
       virtual string MatrixMulPoint(( TransformF transform, Point3F point )) {}
       /*! Get the center point of an axis-aligned box.
    
    @param b A Box3F, in string format using "minExtentX minExtentY minExtentZ maxExtentX maxExtentY maxExtentZ"
    @return Center of the box.
    @ingroup Math */
       virtual string getBoxCenter(( Box3F box )) {}
       /*! Set the current seed for the random number generator.
    Based on this seed, a repeatable sequence of numbers will be produced by getRandom().
    @param seed The seed with which to initialize the randon number generator with.  The same seed will always leed tothe same sequence of pseudo-random numbers.
    If -1, the current timestamp will be used as the seed which is a good basis for randomization.
    @ingroup Random */
       virtual void setRandomSeed(( int seed=-1 )) {}
       /*! Get the current seed used by the random number generator.
    @return The current random number generator seed value.
    @ingroup Random */
       virtual int getRandomSeed(()) {}
       virtual float getRandom() {}
       /*! Solve a quadratic equation (2nd degree polynomial) of form a*x^2 + b*x + c = 0.
    @param a First Coefficient.@param b Second Coefficient.@param c Third Coefficient.@returns A triple, containing: (sol x0 x1). (sol) is the number of solutions(being 0, 1, or 2), and (x0) and (x1) are the solutions, if any.@ingroup Math */
       virtual string mSolveQuadratic(( float a, float b, float c )) {}
       /*! Solve a cubic equation (3rd degree polynomial) of form a*x^3 + b*x^2 + c*x + d = 0.
    @param a First Coefficient.@param b Second Coefficient.@param c Third Coefficient.@param d Fourth Coefficient.@returns A 4-tuple, containing: (sol x0 x1 x2). (sol) is the number of solutions(being 0, 1, 2 or 3), and (x0), (x1) and (x2) are the solutions, if any.@ingroup Math */
       virtual string mSolveCubic(( float a, float b, float c, float d )) {}
       /*! Solve a quartic equation (4th degree polynomial) of form a*x^4 + b*x^3 + c*x^2 + d*x + e = 0.
    @param a First Coefficient.@param b Second Coefficient.@param c Third Coefficient.@param d Fourth Coefficient.@param e Fifth Coefficient.@returns A 5-tuple, containing: (sol x0 x1 x2 c3). (sol) is the number of solutions(being 0, 1, 2, 3 or 4), and (x0), (x1), (x2) and (x3) are the solutions, if any.@ingroup Math */
       virtual string mSolveQuartic(( float a, float b, float c, float d, float e )) {}
       /*! Round v down to the nearest integer.
    @param v Number to convert to integer.@returns Number converted to integer.@ingroup Math */
       virtual int mFloor(( float v )) {}
       /*! Round v to the nearest integer.
    @param v Number to convert to integer.@returns Number converted to integer.@ingroup Math */
       virtual int mRound(( float v )) {}
       /*! Round v up to the nearest integer.
    @param v Number to convert to integer.@returns Number converted to integer.@ingroup Math */
       virtual int mCeil(( float v )) {}
       /*! Formats the specified number to the given number of decimal places.
    @param v Number to format.@param precision Number of decimal places to format to (1-9).@returns Number formatted to the specified number of decimal places.@ingroup Math */
       virtual string mFloatLength(( float v, int precision )) {}
       /*! Calculate absolute value of specified value.
    @param v Input Value.@returns Absolute value of specified value.@ingroup Math */
       virtual float mAbs(( float v )) {}
       /*! Calculate the remainder of v/d.
    @param v Input Value.@param d Divisor Value.@returns The remainder of v/d.@ingroup Math */
       virtual float mFMod(( float v, float d )) {}
       /*! Calculate the square-root of v.
    @param v Input Value.@returns The square-root of the input value.@ingroup Math */
       virtual float mSqrt(( float v )) {}
       /*! Calculate b raised to the p-th power.
    @param v Input Value.@param p Power to raise value by.@returns v raised to the p-th power.@ingroup Math */
       virtual float mPow(( float v, float p )) {}
       /*! Calculate the natural logarithm of v.
    @param v Input Value.@returns The natural logarithm of the input value.@ingroup Math */
       virtual float mLog(( float v )) {}
       /*! Calculate the sine of v.
    @param v Input Value (in radians).@returns The sine of the input value.@ingroup Math */
       virtual float mSin(( float v )) {}
       /*! Calculate the cosine of v.
    @param v Input Value (in radians).@returns The cosine of the input value.@ingroup Math */
       virtual float mCos(( float v )) {}
       /*! Calculate the tangent of v.
    @param v Input Value (in radians).@returns The tangent of the input value.@ingroup Math */
       virtual float mTan(( float v )) {}
       /*! Calculate the arc-sine of v.
    @param v Input Value (in radians).@returns The arc-sine of the input value.@ingroup Math */
       virtual float mAsin(( float v )) {}
       /*! Calculate the arc-cosine of v.
    @param v Input Value (in radians).@returns The arc-cosine of the input value.@ingroup Math */
       virtual float mAcos(( float v )) {}
       /*! Calculate the arc-tangent (slope) of a line defined by rise and run.
    @param rise of line.@param run of line.@returns The arc-tangent (slope) of a line defined by rise and run.@ingroup Math */
       virtual float mAtan(( float rise, float run )) {}
       /*! Convert specified radians into degrees.
    @param radians Input Value (in radians).@returns The specified radians value converted to degrees.@ingroup Math */
       virtual float mRadToDeg(( float radians )) {}
       /*! Convert specified degrees into radians.
    @param degrees Input Value (in degrees).@returns The specified degrees value converted to radians.@ingroup Math */
       virtual float mDegToRad(( float degrees )) {}
       /*! Clamp the specified value between two bounds.
    @param v Input value.@param min Minimum Bound.@param max Maximum Bound.@returns The specified value clamped to the specified bounds.@ingroup Math */
       virtual float mClamp(( float v, float min, float max )) {}
       /*! Clamp the specified value between 0 and 1 (inclusive).
    @param v Input value.@returns The specified value clamped between 0 and 1 (inclusive).@ingroup Math */
       virtual float mSaturate(( float v )) {}
       /*! Calculate the greater of two specified numbers.
    @param v1 Input value.@param v2 Input value.@returns The greater value of the two specified values.@ingroup Math */
       virtual float getMax(( float v1, float v2 )) {}
       /*! Calculate the lesser of two specified numbers.
    @param v1 Input value.@param v2 Input value.@returns The lesser value of the two specified values.@ingroup Math */
       virtual float getMin(( float v1, float v2 )) {}
       /*! Calculate linearly interpolated value between two specified numbers using specified normalized time.
    @param v1 Interpolate From Input value.@param v2 Interpolate To Input value.@param time Normalized time used to interpolate values (0-1).@returns The interpolated value between the two specified values at normalized time t.@ingroup Math */
       virtual float mLerp(( float v1, float v2, float time )) {}
       /*! Return the value of PI (half-circle in radians).
    @returns The value of PI.@ingroup Math */
       virtual float mPi(()) {}
       /*! Return the value of 2*PI (full-circle in radians).
    @returns The value of 2*PI.@ingroup Math */
       virtual float m2Pi(()) {}
       /*! Returns whether the value is an exact power of two.
    @param v Input value.@returns Whether the specified value is an exact power of two.@ingroup Math */
       virtual bool mIsPow2(( int v )) {}
       virtual void initNavMeshUpdates() {}
       /*! Inform Content Server about our terrains and versions. */
       virtual void attachToContentServer(( TCPConnection cs )) {}
       virtual void detachFromContentServer(()) {}
       /*! maintenance(bool isStretched); */
       virtual bool maintenance(( bool isStretched=false )) {}
       virtual string getTerFilePath(( int terID, string basePath=nullptr )) {}
       virtual string getTer2FilePath_Server_Index(( int terID, string basePath=nullptr )) {}
       virtual string getTer2FilePath_Server_Data(( int terID, string basePath=nullptr )) {}
       virtual string getTer2FilePath_Client_Index(( int terID, string basePath=nullptr )) {}
       virtual string getTer2FilePath_Client_Data(( int terID, string basePath=nullptr )) {}
       virtual void SendServerUUIDEvent(( NetConnection client )) {}
       virtual bool cmUpdateTerCrcInDb(( int terID, string basePath=nullptr )) {}
       virtual bool cmUpdateClientTer2IdxCrcInDb(( int terID, string basePath=nullptr )) {}
       virtual bool cmUpdateClientTer2DatCrcInDb(( int terID, string basePath=nullptr )) {}
       virtual bool cmUpdateObjectsCrcInDb(( int terID, string basePath=nullptr )) {}
       virtual bool cmUpdateForestCrcInDb(( int terID, string basePath=nullptr )) {}
       virtual void initCmPatch() {}
       virtual void stretchedPatchMaintenance() {}
       virtual string getServerUuid() {}
       virtual bool yoCsAttachClient(( TCPConnection con, int charID )) {}
       virtual bool yoCsDetachClient(( int charID )) {}
       virtual void restartInstance() {}
       virtual int getCurrentProcessId() {}
       virtual string getComputerName() {}
       virtual string getCLocaleName() {}
       virtual string getIcuLocaleName() {}
       virtual int getIcuLCID() {}
       virtual int sysinfoGetWindowsVersionMajor() {}
       virtual int sysinfoGetWindowsVersionMinor() {}
       virtual string sysinfoGetTotalVirtualMemory() {}
       virtual string sysinfoGetUsedVirtualMemory() {}
       virtual string sysinfoGetFreeVirtualMemory() {}
       virtual string sysinfoGetOwnVirtualMemoryUsage() {}
       virtual string sysinfoGetTotalPhysicalMemory() {}
       virtual string sysinfoGetUsedPhysicalMemory() {}
       virtual string sysinfoGetFreePhysicalMemory() {}
       virtual string sysinfoGetOwnMemoryUsage() {}
       virtual string sysinfoGetCPUUsage() {}
       virtual string sysinfoGetOwnCPUUsage() {}
       virtual string getTemporaryDirectory() {}
       virtual string getTemporaryFileName() {}
       virtual string getUserDataDirectory() {}
       virtual string getUserHomeDirectory() {}
       virtual string getIPLocal() {}
       /*! Create and start a high resolution platform timer. Returns the timer id. */
       virtual int startPrecisionTimer(()) {}
       /*! Stop and destroy timer with the passed id. Returns the elapsed milliseconds. */
       virtual int stopPrecisionTimer(( int timerId )) {}
       virtual void initDisplayDeviceInfo() {}
       virtual void updateWinConsoleTitle() {}
       /*! enableWinconsole(bool); */
       virtual void enableWinConsole(( bool doEnable )) {}
       virtual string getWindowsVersionName() {}
       virtual string getWindowsVersionNum() {}
       virtual string getExperienceRating() {}
       virtual int getRAMavail() {}
       virtual int getRAMtotal() {}
       virtual string getWindowsDefaultLocaleName() {}
       virtual string getWindowsUserDefaultLocaleName() {}
       virtual int getWindowsDefaultLangID() {}
       virtual bool shellExecute() {}
       virtual bool checkNamedPipeOpen(( String pipeName )) {}
       virtual bool isPipedStdIO(()) {}
       virtual void ping(( int level, int timestamp )) {}
       virtual void crtEnableDebug() {}
       virtual void crtCheckMemory() {}
       virtual bool isKoreanBuild() {}
       virtual void clearServerPaths() {}
       virtual void clearClientPaths() {}
       /*! @brief See if any objects of the given types are present in box of given extent.
    
    @note Extent parameter is last since only one  is often needed.  If one  is provided, the y and z are assumed to be the same.  Unfortunately, if you need to use the client container, you'll need to set all of the  parameters.  Fortunately, this function is mostly used on the server.
    @param  mask   Indicates the type of objects we are checking against.
    @param  center Center of box.
    @param  x Search  in the x-axis. See note above.
    @param  y Search  in the y-axis. See note above.
    @param  z Search  in the z-axis. See note above.
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return true if the box is empty, false if any object is found.
    @ingroup Game */
       virtual bool containerBoxEmpty(( int mask, Point3F center, float x, float y=-1, float z=-1, bool useClientContainer=false )) {}
       /*! @brief Start a search for items at the given position and within the given , filtering by mask.
    
    @param pos Center position for the search
    @param  Search 
    @param mask Bitmask of object types to include in the search
    @param useClientContainer Optionally indicates the search should be within the client container.
    @see containerSearchNext
    @ingroup Game */
       virtual void initContainerSearch(( Point3F pos, float , int mask, bool useClientContainer=false )) {}
       /*! @brief Start a search for all items of the types specified by the bitset mask.
    
    @param mask Bitmask of object types to include in the search
    @param useClientContainer Optionally indicates the search should be within the client container.
    @see containerSearchNext
    @ingroup Game */
       virtual void initContainerTypeSearch(( int mask, bool useClientContainer=false )) {}
       /*! @brief Get next item from a search started with initContainerSearch() or initContainerTypeSearch().
    
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return the next object found in the search, or null if no more
    @tsexample
    // print the names of all nearby ShapeBase derived objects
    %position = %obj.getPosition;
    % = 20;
    %mask = $TypeMasks::ShapeBaseObjectType;
    initContainerSearch( %position, %, %mask );
    while ( (%targetObject = containerSearchNext()) != 0 )
    {
       echo( "Found: " @ %targetObject.getName() );
    }
    @endtsexample
    @see initContainerSearch()
    @see initContainerTypeSearch()
    @ingroup Game */
       virtual string containerSearchNext(( bool useClientContainer=false )) {}
       /*! @brief Get distance of the center of the current item from the center of the current initContainerSearch.
    
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return distance from the center of the current object to the center of the search
    @see containerSearchNext
    @ingroup Game */
       virtual float containerSearchCurrDist(( bool useClientContainer=false )) {}
       /*! @brief Get the distance of the closest point of the current item from the center of the current initContainerSearch.
    
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return distance from the closest point of the current object to the center of the search
    @see containerSearchNext
    @ingroup Game */
       virtual float containerSearchCurrDist(( bool useClientContainer=false )) {}
       virtual void listObjects(()) {}
       /*! @brief Cast a ray from start to end, checking for collision against items matching mask.
    
    If pExempt is specified, then it is temporarily excluded from collision checks (For instance, you might want to exclude the player if said player was firing a weapon.)
    @param start An XYZ vector containing the tail position of the ray.
    @param end An XYZ vector containing the head position of the ray
    @param mask A bitmask corresponding to the type of objects to check for
    @param pExempt An optional ID for a single object that ignored for this raycast
    @param useClientContainer Optionally indicates the search should be within the client container.
    @returns A string containing either null, if nothing was struck, or these fields:
    &lt;ul&gt;&lt;li&gt;The ID of the object that was struck.&lt;/li&gt;&lt;li&gt;The x, y, z position that it was struck.&lt;/li&gt;&lt;li&gt;The x, y, z of the normal of the face that was struck.&lt;/li&gt;&lt;/ul&gt;@ingroup Game */
       virtual string containerRayCast(( Point3F start, Point3F end, int mask, SceneObject pExempt=NULL, bool useClientContainer=false )) {}
       virtual void setVisibleDistance(( float dist )) {}
       /*! @brief Load all path information from interiors.
    
    This function is usually called from the loadMissionStage2() server-side function after the mission file has loaded.
    
    @tsexample
    // Inform the engine to load all path information from interiors.
    pathOnMissionLoadDone();
    
    @endtsexample
    @ingroup Game */
       virtual void pathOnMissionLoadDone(()) {}
       virtual void initCharCreateConfig() {}
       virtual void sendExitRequestToServer() {}
       virtual void sendExitCancelRequestToServer() {}
       virtual void onClientManagersInitialized(( NetConnection connection )) {}
       virtual void allowConnections() {}
       virtual void CmDatabase_init() {}
       /*! Encodes string for using within SQL-expressions */
       virtual string dbEncode(( string inStr )) {}
       /*! In milliseconds. -1 == all queries */
       virtual void CmDatabaseSetSlowQueryLogDurationMs(( int ms )) {}
       /*! In milliseconds. -1 == all queries */
       virtual int CmDatabaseGetSlowQueryLogDurationMs(()) {}
       virtual bool U32CmDbTableIDRangeInit(( U32CmDbTableIDRangeEnum rangeType, string issueSpName, string occupySpName, int idMaxPoolSize=sgDefaultIdMaxPoolSize, int idMinPoolSize=sgDefaultIdMinPoolSize )) {}
       virtual bool U64CmDbTableIDRangeInit(( U64CmDbTableIDRangeEnum rangeType, string issueSpName, string occupySpName, int idMaxPoolSize=sgDefaultIdMaxPoolSize, int idMinPoolSize=sgDefaultIdMinPoolSize )) {}
       virtual void DebugDumpAllCmDbIDRanges(()) {}
       virtual string getThreadedSlowQueriesCount() {}
       virtual int Query() {}
       virtual int sqlQuery() {}
       virtual int sqlUpdate() {}
       virtual string calcSha1() {}
       virtual bool registerSteamServer(( int gamePort )) {}
       virtual void SubstanceManager_init() {}
       virtual void SubstanceManager_clear() {}
       virtual void geoDecay() {}
       virtual void geoDecayStretched() {}
       virtual int GetServerCentralTer(( int serverID )) {}
       virtual string GetServerTerIDList(( int serverID, bool includeSideTers=false )) {}
       virtual float getTerrainTopAtPosition() {}
       virtual bool InitTerrainList(( string dataMirrorPath=nullptr )) {}
       virtual void detachTerrains() {}
       virtual void initGlobalRemapIndex() {}
       virtual bool RecreateTerrainFilesRange(( int startTerId, int endTerId, string newFileNameSuffix="_new" )) {}
       virtual void SaveMapFiles() {}
       virtual void GenerateAndSmoothTer2FromTer() {}
       virtual void GenerateAndSmoothSingleTer2FromTer() {}
       virtual void GenerateTer2FromTer() {}
       virtual void SetTer2SubstancesFromTer() {}
       virtual void GenerateTerFromTer2() {}
       virtual void SetTerrainMaterialsFromTer2() {}
       virtual void CheckTerMaterialsUsing() {}
       virtual void CheckTerMaterialsTotalUsing() {}
       virtual void ConvertServerGeoFileToClient() {}
       virtual void ConvertServerGeoFileToClientRange() {}
       virtual void ResetAllGeoFilesDataVersion() {}
       virtual void ResetGeoFilesDataVersionRange(( int startTerID, int endTerID, bool skipClientFiles=false )) {}
       virtual void CloneNewbieGeoFilesRange(( int startNewbieTerId, int startTargetTerID, int endTargetTerID, bool skipClientFiles=false )) {}
       virtual void ReduceTerrainWidth() {}
       virtual void SmoothTerrainsTwinPointsWithFallByCenterTer() {}
       virtual void SmoothTerTwinPoints() {}
       virtual void Tunnels_PrintBlockCount(()) {}
       virtual void serverCmdSendTunnelBlockCollisionToClient(( GameConnection connection, GeoID::UnderlyingType rawGeoID, int altitude )) {}
       virtual void serverCmdVerifyTunnelManagersSync(( GameConnection connection )) {}
       virtual void setDisableSkinnedMatCheck(( bool isDisabled=true )) {}
       virtual void beginSampling() {}
       virtual void stopSampling() {}
       virtual void enableSamples() {}
       virtual string getCmVersionString() {}
       virtual string getCmVersionStringNoPrefix() {}
    };
---
_schema: child
layout: default
title: Client Console Functions
nav_order:
nav_exclude: false
parent: Client Documentation
has_children: false
has_toc: false
last_modified_date: 2025-12-11T17:42:25Z
---
# Functions (reference)

      namespace Global {
        virtual Script onExit(()) {}
        virtual Script scheduleQuit(( string timeout, string msgId )) {}
        virtual Script dumpEnhancedInfoReport(()) {}
        virtual Script _askToGenerateCrashReport(( string msgCode, string errCode )) {}
        virtual Script _lifError(( string msgCode, string errCode, string debugInfo )) {}
        virtual Script _disconnectedCleanupFinalDone(( string needQuit )) {}
        virtual Script prepAndKillMariaDB(( string callback )) {}
        virtual Script mysqldumpDatabase(( string callback )) {}
        virtual Script exportCommonDB(( string worldID, string callback )) {}
        virtual Script doCommonDB(( string worldID, string sql )) {}
        virtual Script importCommonDB(( string worldID, string file )) {}
        virtual Script createCommonDB(( string worldID )) {}
        virtual Script dropCommonDB(( string worldID )) {}
        virtual Script backupWorld(( string worldID )) {}
        virtual Script extractEmptyDB(( string world )) {}
        virtual Script onManagersInitDone(()) {}
        virtual Script cleanupPatches(()) {}
        virtual Script updatePatchedTerCounterGui(( string loadedTerCount, string totalTerCount )) {}
        virtual Script updateForestPatchingCounterGui(( string loadedTerCount, string totalTerCount )) {}
        virtual Script updateObjPatchingCounterGui(( string loadedTerCount, string totalTerCount )) {}
        virtual Script updateGeoPatchingCounterGui(( string loadedTerCount, string totalTerCount )) {}
        virtual Script updatePatchingCounterGui(( string patchedTerCount, string totalTerCount )) {}
        virtual Script joinToRemoteServer(( string addr, string password )) {}
        virtual Script initLocalConnection(( string port )) {}
        virtual Script updateVersionBarText(()) {}
        virtual Script showWelcomeMessage(()) {}
        virtual Script onLocalServerLoaded(()) {}
        virtual Script prepareWorldDB(()) {}
        virtual Script getLocalIP(()) {}
        virtual Script cmJoinDefaultChats(()) {}
        virtual Script clientCmdPATCHOK(( string server )) {}
        virtual Script clientRpcPREPATCHOK(( string cs )) {}
        virtual Script clientRpcGetPVer(( string cs )) {}
        virtual Script connectToContentServer(()) {}
        virtual Script reconnectToContentServer(( string errorMessage )) {}
        virtual Script peerCmdCS(( string peer, string serverPort, string accountHash )) {}
        virtual Script startConnection(( string addr )) {}
        virtual Script _connectToGameServer(()) {}
        virtual Script showWelcomeMessage(()) {}
        virtual Script cmJoinDefaultChats(()) {}
        virtual Script initManagers(()) {}
        virtual Script initClient(()) {}
        virtual Script peerCmdLiFxSHA256(( string server, string file )) {}
        virtual Script peerCmdLiFxCRC(( string server, string file )) {}
        virtual Script LiFxOpenWeb(( string val )) {}
        virtual Script onExit(()) {}
        virtual Script exportPrefs(()) {}
        virtual Script initializeEditors(()) {}
        virtual Script onStart(()) {}
        virtual Script parseArgs(()) {}
        virtual Script parseArgs(()) {}
        virtual Script loadKeybindings(()) {}
        virtual Script onExit(()) {}
        virtual Script onStart(()) {}
        virtual Script FTTP_OpenTradeWindow(()) {}
        virtual Script peerCmdFTTP_Clear(( string server )) {}
        virtual Script peerCmdFTTP_Activate(( string server, string tradepost_id )) {}
        virtual Script peerCmdFTTP_Config(( string server, string url, string keybind )) {}
        virtual Script peerCmdFTTP_Handshake(( string server )) {}
        virtual Script cm_debug_print(( string msg )) {}
        virtual Script sendFileToServer(( string pathOnClient, string pathOnServer )) {}
        virtual Script registerBehavior(( string name, string fileName )) {}
        virtual Script deleteNPC(()) {}
        virtual Script resetNPC(()) {}
        virtual Script activateNPC(()) {}
        virtual Script loadNPC(( string fileName )) {}
        virtual Script saveNPC(( string fileName )) {}
        virtual Script spawnNPC(( string datablock, string beh )) {}
        virtual Script stopMusic(()) {}
        virtual Script startMusic(()) {}
        virtual Script createBrowserWindow(( string name, string profileName, string makeModal )) {}
        virtual Script createContainer(()) {}
        virtual Script DebugAddLayerToTop(( string val )) {}
        virtual Script togglePostFXManager(( string val )) {}
        virtual Script setCameraMode(( string mode )) {}
        virtual Script clientCmdSetCameraSpeed(( string val )) {}
        virtual Script setCameraSpeed(( string val )) {}
        virtual Script dropPlayerAtCamera(( string val )) {}
        virtual Script dropCameraAtPlayer(( string val )) {}
        virtual Script cycleDebugRenderMode(( string val )) {}
        virtual Script setZoomFOV(( string val )) {}
        virtual Script toggleZoomFOV(()) {}
        virtual Script doHindLegsBreak(()) {}
        virtual Script doHindLegs(( string val )) {}
        virtual Script turnRight(( string val )) {}
        virtual Script turnLeft(( string val )) {}
        virtual Script brake(( string val )) {}
        virtual Script brakeLights(()) {}
        virtual Script clientCmdVehicleMapOff(()) {}
        virtual Script clientCmdVehicleMapOn(()) {}
        virtual Script HB_Tab4_Slot0(( string val )) {}
        virtual Script HB_Tab4_Slot9(( string val )) {}
        virtual Script HB_Tab4_Slot8(( string val )) {}
        virtual Script HB_Tab4_Slot7(( string val )) {}
        virtual Script HB_Tab4_Slot6(( string val )) {}
        virtual Script HB_Tab4_Slot5(( string val )) {}
        virtual Script HB_Tab4_Slot4(( string val )) {}
        virtual Script HB_Tab4_Slot3(( string val )) {}
        virtual Script HB_Tab4_Slot2(( string val )) {}
        virtual Script HB_Tab4_Slot1(( string val )) {}
        virtual Script HB_Tab3_Slot0(( string val )) {}
        virtual Script HB_Tab3_Slot9(( string val )) {}
        virtual Script HB_Tab3_Slot8(( string val )) {}
        virtual Script HB_Tab3_Slot7(( string val )) {}
        virtual Script HB_Tab3_Slot6(( string val )) {}
        virtual Script HB_Tab3_Slot5(( string val )) {}
        virtual Script HB_Tab3_Slot4(( string val )) {}
        virtual Script HB_Tab3_Slot3(( string val )) {}
        virtual Script HB_Tab3_Slot2(( string val )) {}
        virtual Script HB_Tab3_Slot1(( string val )) {}
        virtual Script HB_Tab2_Slot0(( string val )) {}
        virtual Script HB_Tab2_Slot9(( string val )) {}
        virtual Script HB_Tab2_Slot8(( string val )) {}
        virtual Script HB_Tab2_Slot7(( string val )) {}
        virtual Script HB_Tab2_Slot6(( string val )) {}
        virtual Script HB_Tab2_Slot5(( string val )) {}
        virtual Script HB_Tab2_Slot4(( string val )) {}
        virtual Script HB_Tab2_Slot3(( string val )) {}
        virtual Script HB_Tab2_Slot2(( string val )) {}
        virtual Script HB_Tab2_Slot1(( string val )) {}
        virtual Script HB_Tab1_Slot0(( string val )) {}
        virtual Script HB_Tab1_Slot9(( string val )) {}
        virtual Script HB_Tab1_Slot8(( string val )) {}
        virtual Script HB_Tab1_Slot7(( string val )) {}
        virtual Script HB_Tab1_Slot6(( string val )) {}
        virtual Script HB_Tab1_Slot5(( string val )) {}
        virtual Script HB_Tab1_Slot4(( string val )) {}
        virtual Script HB_Tab1_Slot3(( string val )) {}
        virtual Script HB_Tab1_Slot2(( string val )) {}
        virtual Script HB_Tab1_Slot1(( string val )) {}
        virtual Script switchShowClaims(( string down )) {}
        virtual Script showClaims(( string down )) {}
        virtual Script mouseWheelRot(( string val )) {}
        virtual Script mouseWheelDown(()) {}
        virtual Script mouseWheelUp(()) {}
        virtual Script rightSwingHit(()) {}
        virtual Script leftSwingHit(()) {}
        virtual Script overheadHit(()) {}
        virtual Script thrustHit(()) {}
        virtual Script toggleCmEditGuiMode(( string down )) {}
        virtual Script ActivateVoiceChat(( string down )) {}
        virtual Script toggleCmFreelookMode(( string down )) {}
        virtual Script toggleWarstancePose(( string val )) {}
        virtual Script toggleHelpDlg(( string val )) {}
        virtual Script forceFirstPerson(()) {}
        virtual Script forceThirdPerson(()) {}
        virtual Script toggleFirstPerson(( string val )) {}
        virtual Script gamepadAltTrigger(( string val )) {}
        virtual Script gamepadFire(( string val )) {}
        virtual Script shieldBash(( string val )) {}
        virtual Script altTrigger(( string val )) {}
        virtual Script mouseFire(( string val )) {}
        virtual Script isWarState(()) {}
        virtual Script switchAutorun(( string val )) {}
        virtual Script gamepadPitch(( string val )) {}
        virtual Script gamepadYaw(( string val )) {}
        virtual Script gamePadMoveY(( string val )) {}
        virtual Script gamePadMoveX(( string val )) {}
        virtual Script jump(( string val )) {}
        virtual Script pitch(( string val )) {}
        virtual Script yaw(( string val )) {}
        virtual Script getGamepadAdjustAmount(( string val )) {}
        virtual Script getMouseAdjustAmount(( string val )) {}
        virtual Script panDown(( string val )) {}
        virtual Script panUp(( string val )) {}
        virtual Script movedown(( string val )) {}
        virtual Script movedown2(( string val )) {}
        virtual Script moveup(( string val )) {}
        virtual Script isOwnControlCamera(()) {}
        virtual Script movebackward(( string val )) {}
        virtual Script moveforward(( string val )) {}
        virtual Script moveright(( string val )) {}
        virtual Script moveleft(( string val )) {}
        virtual Script setSpeed(( string speed )) {}
        virtual Script doScreenShotHudless(( string val )) {}
        virtual Script hideHUDs(( string val )) {}
        virtual Script resetVolley(()) {}
        virtual Script setVolley(()) {}
        virtual Script resetAbility(()) {}
        virtual Script unbindAbility(()) {}
        virtual Script setAbility(()) {}
        virtual Script togglePixelize(( string val )) {}
        virtual Script bringUpOptions(( string val )) {}
        virtual Script peerCmdShowCharCreate(( string this )) {}
        virtual Script peerCmdCS(( string peer, string serverIP, string serverPort, string accountHash )) {}
        virtual Script clientRpcCS(( string peer )) {}
        virtual Script clientRpcOK(( string cs )) {}
        virtual Script connectToContentServer(()) {}
        virtual Script reconnectToContentServer(( string errorMessage )) {}
        virtual Script _connectToGameServer(()) {}
        virtual Script onManagersInitDone(()) {}
        virtual Script initManagersOnCharSelected(( string callback )) {}
        virtual Script checkJoinToServer(()) {}
        virtual Script markStreamingReadyState(()) {}
        virtual Script _requestWorldSelection(()) {}
        virtual Script clientCmdLoading(()) {}
        virtual Script peerCmdWJ(( string peer, string cmd, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9 )) {}
        virtual Script peerCmdJS(( string this )) {}
        virtual Script peerCmdSA(( string peer, string geoId, string address, string port, string serverID )) {}
        /*! Duplicated session is online, should wait for %a1 ms
     */
        virtual Script peerCmdDS(( string peer, string cmd, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9 )) {}
        /*! Target server offline
     */
        virtual Script peerCmdSO(( string peer )) {}
        virtual Script relay(( string server, string callback )) {}
        virtual Script connectDispatcher(( string server )) {}
        virtual Script connect(( string server, string callback )) {}
        virtual Script connectToServer(( string serverID )) {}
        virtual Script _requestCleanup(()) {}
        virtual Script onWindowClose(()) {}
        virtual Script _disconnectManagers(()) {}
        virtual Script cleanupPatches(()) {}
        virtual Script cleanupGroundCovers(()) {}
        virtual Script _disconnectedCleanupMakeQuit(( string needQuit )) {}
        virtual Script _disconnectedCleanupFinalDone(( string needQuit )) {}
        virtual Script _disconnectedCleanupFinal(( string needQuit )) {}
        virtual Script _disconnectedCleanup(( string needQuit )) {}
        virtual Script _processDisconnect(( string needQuit )) {}
        virtual Script cleanupInterface(()) {}
        virtual Script _disconnectBase(( string needQuit, string fastStreamingShutdown )) {}
        virtual Script _disconnectWithMessageBox(( string title, string message )) {}
        virtual Script _disconnectQuit(()) {}
        virtual Script _disconnect(()) {}
        /*! Called from select char dlg (Exit button) and fromCharacterErrorMessage(DISCONNECT)
     */
        virtual Script _disconnectServer(()) {}
        virtual Script getIRSPMetrics(()) {}
        virtual Script connectToDebugTCPServer(()) {}
        virtual Script clientCmdDebugTCPServerIsOn(( string serverPort )) {}
        virtual Script listAllServers(()) {}
        virtual Script updateCanvasTitle(()) {}
        virtual Script handleConnectionErrorMessage(( string msgType, string msgString, string msgError )) {}
        virtual Script lag(( string lag )) {}
        virtual Script dropConnectionToServer(( string serverID )) {}
        virtual Script initiateNewConnection(( string serverID, string addr )) {}
        virtual Script clientCmdIrsp(( string cmd, string a1, string a2, string a3 )) {}
        virtual Script peerCmdIrc(( string server, string cmd, string a1, string a2, string a3 )) {}
        virtual Script peerCmdUrls(( string peer, string urlName, string url )) {}
        virtual Script _onWorldCreated(()) {}
        virtual Script peerCmdConnectionEstablished(( string server )) {}
        virtual Script startConnection(( string addr )) {}
        virtual Script initConnection(()) {}
        virtual Script resuscitate(( string magnitude )) {}
        virtual Script createRest(( string duration, string healAmount )) {}
        virtual Script dealDamage(( string partOfBody )) {}
        virtual Script healAllBodyFracture(( string durationMultiplier )) {}
        virtual Script healAllWound(( string durationMultiplier )) {}
        virtual Script removeAllFracture(()) {}
        virtual Script removeAllBodyBleeding(()) {}
        virtual Script removeAllBodyWound(()) {}
        virtual Script createAllFracture(()) {}
        virtual Script createAllBodyBleeding(()) {}
        virtual Script createAllBodyWound(()) {}
        virtual Script healFracture(( string partOfBody, string durationMultiplier )) {}
        virtual Script healWound(( string partOfBody, string durationMultiplier )) {}
        virtual Script removeFracture(( string partOfBody )) {}
        virtual Script removeBleeding(( string partOfBody )) {}
        virtual Script removeWound(( string partOfBody )) {}
        virtual Script createFracture(( string partOfBody )) {}
        virtual Script createBleeding(( string partOfBody )) {}
        virtual Script createWound(( string partOfBody )) {}
        virtual Script peerCmdUpdateServerDebugRaycastHitbox(( string server, string newHitbox )) {}
        virtual Script cmChatSendLocalMessageToServer(( string position, string message )) {}
        virtual Script createBuildSelectionGui(()) {}
        virtual Script createChatTab(()) {}
        virtual Script closeSelectionListDlg(()) {}
        virtual Script initSelectionListDlg(( string buttonText )) {}
        virtual Script openSelectionListDlg(()) {}
        virtual Script showCharWindow(( string val )) {}
        virtual Script showSkill(( string val )) {}
        virtual Script checkGuildTagAndNameCtrl(()) {}
        virtual Script applyGuildName(()) {}
        virtual Script cancelGuildNameEditMode(()) {}
        virtual Script setGuildNameEditMode(()) {}
        virtual Script checkGuildNameEditMode(( string state )) {}
        virtual Script safeClearChilds(( string pnl )) {}
        virtual Script createPopUpTitleScroll(()) {}
        virtual Script createYOGuildCtrl(()) {}
        virtual Script createMessageWindowSettings(()) {}
        virtual Script CloseSubscriptionInfoDialog(()) {}
        virtual Script createSubscriptionInfoDialog(()) {}
        virtual Script closeCreditsWindow(()) {}
        virtual Script showCreditsWindow(()) {}
        virtual Script createCreditsWindow(()) {}
        virtual Script closePollVoting(()) {}
        virtual Script showPollVotingInvitation(()) {}
        virtual Script closePromoBanner(()) {}
        virtual Script showPromoBanner(()) {}
        virtual Script addButtonExtent(( string button, string extent )) {}
        virtual Script HelpWindowControlsClick(()) {}
        virtual Script HelpWindowLearningClick(()) {}
        virtual Script showHelpWindowSelectedTabDecor(( string selectTab )) {}
        virtual Script HelpWindowStartTutorialBuilding(( string start )) {}
        virtual Script HelpWindowFinishCreatingItem(()) {}
        virtual Script HelpWindowCreateItem(( string textId )) {}
        virtual Script HelpWindowClearTags(( string text )) {}
        virtual Script createHelpWindow(()) {}
        virtual Script showHelpWindow(( string show )) {}
        virtual Script fillWorldInfos(()) {}
        virtual Script getWorldRulesTextPath(( string worldID )) {}
        virtual Script performSailToWorld(( string worldID )) {}
        virtual Script showWorldTicketConsumptionDialog(( string worldID, string worldName )) {}
        virtual Script openQuestSailDialog(()) {}
        virtual Script MakeTimerStringPretty(( string timer )) {}
        virtual Script createSkinsApplyWindow(()) {}
        virtual Script createSkinsApplyElement(( string id, string icon, string header, string desc, string canBuy )) {}
        virtual Script createSkinsListWindow(()) {}
        virtual Script createSkinsListVerticalDivider(()) {}
        virtual Script createSkinsListElement(( string icon, string equipType, string combine )) {}
        virtual Script createSkinsSelectDivider(()) {}
        virtual Script createSkinsSelectElement(( string icon, string header, string desc, string status )) {}
        virtual Script createDeathWindow(( string hasInsurance, string hasPenalty )) {}
        virtual Script DeathWindowAddSkillLost(( string skillID, string skillLostBasic, string skillLostInsurance, string skillLostFinal )) {}
        virtual Script checkProgressBarChildVisible(( string pregressPos, string chuld )) {}
        virtual Script setProgressBar(( string val )) {}
        virtual Script hideProgressBar(()) {}
        virtual Script showProgressBar(()) {}
        virtual Script deleteAlertQuestWindowProfiles(()) {}
        virtual Script createAlertQuestWindowProfiles(()) {}
        virtual Script closeAlertQuestWindow(()) {}
        virtual Script showAlertQuestWindow(( string questNameId, string isNewQuest )) {}
        virtual Script questTasks_debugAddTask(( string questId )) {}
        virtual Script questTasks_debugAdd(()) {}
        virtual Script questTasks_updateQuestTaskProps(( string taskItem )) {}
        virtual Script questTasks_setQuestItemName(( string questNameCtrl, string isActiveQuest )) {}
        virtual Script getCurrentQuestTaskNameText(( string textId, string textWidth )) {}
        virtual Script getIncompletedQuestTaskNameText(( string textId, string textWidth )) {}
        virtual Script getCompletedQuestTaskNameText(( string textId, string textWidth )) {}
        virtual Script getHighlightedQuestNameText(( string textId )) {}
        virtual Script getInactiveQuestNameText(( string textId )) {}
        virtual Script getActiveQuestNameText(( string textId )) {}
        virtual Script closeQuestTaskDescriptionWindow(()) {}
        virtual Script questTask_ShowQuestTaskDescription(( string description )) {}
        virtual Script questTask_ShowQuestTaskTutorialHint(( string questId, string taskId )) {}
        virtual Script questTasks_TaskOnMapButtonToggleFromCode(( string questId, string taskId, string isOn )) {}
        virtual Script questTask_setFirstQuestActive(()) {}
        virtual Script questTasks_setSingleQuestActive(()) {}
        virtual Script questTasks_deleteQuest(( string questId )) {}
        virtual Script questTask_setQuestTaskStatus(( string questId, string taskId, string taskStatus )) {}
        virtual Script questTasks_setQuestActive(( string questId )) {}
        virtual Script questTask_addQuestTask(( string questId, string taskId, string taskName, string taskStatus, string taskDescription, string hasMapButton, string hasTutorialHint )) {}
        virtual Script questTask_addQuest(( string questId, string questName, string questIcon )) {}
        virtual Script deleteQuestTasksWindowProfiles(()) {}
        virtual Script createQuestTasksWindowProfiles(()) {}
        virtual Script closeQuestTasksWindow(()) {}
        virtual Script createQuestTasksWindow(()) {}
        virtual Script getQuestAnswerTypeIcon(( string answerType )) {}
        virtual Script getQuestAnswerHighlightText(( string textId )) {}
        virtual Script getQuestAnswerNormalText(( string textId )) {}
        virtual Script getQuestGiverNameText(( string textId )) {}
        virtual Script clearQuestDialogAnswers(()) {}
        virtual Script addQuestDialogAnswer(( string answerId, string textId, string answerType )) {}
        virtual Script setQuestDialogParameters(( string questSubject, string questGiverName, string questGiverType, string questGiverAvatar, string prevQuestText, string currentQuestText, string answersHeaderMsgId )) {}
        virtual Script deleteQuestDialogWindowProfiles(()) {}
        virtual Script createQuestDialogWindowProfiles(()) {}
        virtual Script closeQuestDialogWindow(()) {}
        virtual Script createQuestDialogWindow(()) {}
        virtual Script QuestFerryManSelectionSelected(()) {}
        virtual Script QuestFerryManSelectionDownPressed(()) {}
        virtual Script QuestFerryManSelectionUpPressed(()) {}
        virtual Script closeQuestFerryManSelectionDialog(()) {}
        virtual Script openQuestFerryManSelectionDialog(()) {}
        virtual Script QuestFerryManAnswer(( string number )) {}
        virtual Script closeQuestFerryManDialog(()) {}
        virtual Script openQuestFerryManDialog(()) {}
        virtual Script horseTrainingDlgSetScore(( string score )) {}
        virtual Script closeHorseTrainingDlg(()) {}
        virtual Script openHorseTrainingDlg(( string timer )) {}
        virtual Script createHorseTrainingDlg(()) {}
        virtual Script runMoveBySpline(( string index )) {}
        virtual Script getRecordPointText(( string pt )) {}
        virtual Script addPlayerPosAndCameraRotationAsPoint(( string dialogStack, string pos, string rot )) {}
        virtual Script deleteRecordPointsProfiles(()) {}
        virtual Script createRecordPointsProfiles(()) {}
        virtual Script showRecordSplineKnotsDialog(()) {}
        virtual Script showRecordPointsDialog(()) {}
        virtual Script createChangeStoreSizeDialog(( string storeWeight, string storeSize )) {}
        virtual Script createPayForStorePopUpScroll(()) {}
        virtual Script showSplitSupportCoinsDialog(()) {}
        virtual Script addInfoToSplitSupportCoinsDialog(( string coinTypeName, string coinTypeId )) {}
        virtual Script createPayForStoreDialog(()) {}
        virtual Script showChangeStoreSizeDialog(( string storeWeight, string storeSize )) {}
        virtual Script closePayForStoreDialog(()) {}
        virtual Script closeChangeStoreSizeDialog(()) {}
        virtual Script createSplitSupportCoinsDialog(()) {}
        virtual Script deleteTradePostProfiles(()) {}
        virtual Script createTradePostProfiles(()) {}
        virtual Script createTradePostWindow(()) {}
        virtual Script applyGameSettingsShowTutorialChanged(()) {}
        virtual Script onTutorialScrollDownButtonClick(()) {}
        virtual Script closeTutorialInfoHint(()) {}
        virtual Script closeTutorialSimpleHint(()) {}
        virtual Script closeTutorialHintWindow(()) {}
        virtual Script addTutorialHintImage(( string picPath )) {}
        virtual Script addTutorialHintSpacing(( string pixels )) {}
        virtual Script addTutorialHintTextContent(( string textId )) {}
        virtual Script getTutorialContentControl(()) {}
        virtual Script updateTutorialHintContent(()) {}
        virtual Script showTutorialHintWindow(()) {}
        virtual Script createTutorialInfoHintWindow(()) {}
        virtual Script createTutorialSimpleHintWindow(()) {}
        virtual Script deleteTutorialHintProfiles(()) {}
        virtual Script createTutorialHintProfiles(()) {}
        virtual Script createTutorialHintWindow(()) {}
        virtual Script UpdateHeraldryTimer(( string HeraldryButton )) {}
        virtual Script StopHeraldryTimer(( string HeraldryButton )) {}
        virtual Script StartHeraldryTimer(( string HeraldryButton )) {}
        virtual Script closeResizeClaimWindow(()) {}
        virtual Script showResizeClaimWindow(()) {}
        virtual Script findStatValText(( string parent )) {}
        virtual Script addStatInfo(( string val, string txt )) {}
        virtual Script addItemDescription(( string informer )) {}
        virtual Script addSkillInfo(( string colName, string colVal, string informer )) {}
        virtual Script createItemRegion(( string informer )) {}
        virtual Script findExeconTimer(( string parent )) {}
        virtual Script createEffectCtrl(( string pnl, string effect, string magnitude, string positive )) {}
        virtual Script addItemEffects(( string informer, string effectGroup, string effectGroupMagnitude, string effectGroupPositive )) {}
        virtual Script createItemsFeatureEffect(( string informer )) {}
        virtual Script createItemsDurability(( string parent, string imageIndex, string informer )) {}
        virtual Script createItemsQWD(( string informer )) {}
        virtual Script createItemsQuantityWeight(( string informer )) {}
        virtual Script createItemsQualityWeight(( string informer )) {}
        virtual Script createItemsWeight(( string informer )) {}
        virtual Script createItemsQQW(( string informer )) {}
        virtual Script createIconText(( string parent, string imageIndex, string text )) {}
        virtual Script createIconPnl(( string parent, string imageIndex )) {}
        virtual Script addRowTooltipinfo(( string colName, string colVal, string name, string val )) {}
        virtual Script createContainersWeight(( string informer )) {}
        virtual Script createContainersName(( string informer )) {}
        virtual Script createObjectsTypesName(( string informer )) {}
        virtual Script createDoubleTextCtrl(( string profile )) {}
        virtual Script createVerticalStackControl(()) {}
        virtual Script createHorizontalStackControl(()) {}
        virtual Script createTextCtrl(( string profile, string text )) {}
        virtual Script createCaptionTextCtrl(()) {}
        virtual Script createMLTextCtrl(()) {}
        virtual Script createImageCtrl(( string imageIndex )) {}
        virtual Script calcTooltipPosition(( string cursorPosX, string cursorPosY, string windowSizeX, string windowSizeY )) {}
        virtual Script createBaseTooltip(()) {}
        virtual Script PersonalClaimShowBuyButton(( string val )) {}
        virtual Script createPersonalClaimWindow(()) {}
        virtual Script userWantsToExit(( string type )) {}
        virtual Script closeExitTimerDlg(()) {}
        virtual Script openExitTimerDlg(( string seconds, string finishCommand )) {}
        virtual Script onControlObjectDead(()) {}
        virtual Script onExitTimerAutoclose(()) {}
        virtual Script onExitTimerCancelPressed(()) {}
        virtual Script onExitTimerExitPressed(()) {}
        virtual Script applyNewGameSettings(()) {}
        virtual Script showGameSettingsDlg(()) {}
        virtual Script createGameSettingsDlg(()) {}
        virtual Script selectRegionGuiAddWorld(( string worldID, string worldName, string populLvl, string worldIsUp, string charCount )) {}
        virtual Script selectRegionWorldReset(()) {}
        virtual Script HeraldryDialogSetCharge(( string num, string imageIndex, string position, string size, string color )) {}
        virtual Script HeraldryDialogSetBackground(( string fillTypeIndex, string color1, string color2 )) {}
        virtual Script HeraldryShowLog(()) {}
        virtual Script createHeraldrySettingDialogProfiles(()) {}
        virtual Script createHeraldrySettingDialog(()) {}
        virtual Script addHeraldrySymbolInTable(( string parent, string imageIndex, string nameIndex, string stateOn )) {}
        virtual Script getHeraldrySymbolName(( string imageName )) {}
        virtual Script addHeraldryFillTypeInTable(( string parent, string imageIndex, string stateOn )) {}
        virtual Script getHeraldryFillTypeName(( string imageName )) {}
        virtual Script createHeraldrySymbolPanel(( string name )) {}
        virtual Script createFillTypePanel(( string name )) {}
        virtual Script onColorClick(( string this )) {}
        virtual Script hideHeraldry(()) {}
        virtual Script showHeraldry(()) {}
        virtual Script showSymbols(()) {}
        virtual Script showfillType(()) {}
        virtual Script addEmblemColorButton(( string pnl, string pos, string colorIndex, string colorName, string pnlIndex )) {}
        virtual Script deleteHeraldryWindowProfiles(()) {}
        virtual Script createHeraldryWindowProfiles(()) {}
        virtual Script createHeraldry(()) {}
        virtual Script applyRenamePreset(( string new_preset_name, string cur_name_preset, string cur_name_menu )) {}
        virtual Script setNewPresetName(( string renameDialog, string new_preset_name )) {}
        virtual Script createNewPreset(( string name_preset, string name_menu )) {}
        virtual Script createNewPresetCopyFrom(( string new_preset, string cur_preset, string name_menu )) {}
        virtual Script copyObjToPath(( string old_path, string new_path )) {}
        virtual Script deleteAllPresetFile(( string preset_path )) {}
        virtual Script checkDefHotBarPresetPath(()) {}
        virtual Script setStateCheckBox(( string old_check_box, string new_check_box )) {}
        virtual Script setDefaultHotBarPreset(( string name_preset )) {}
        virtual Script checkHotBarPresetCheckBox(( string name_preset )) {}
        virtual Script setDefaultHUDPreset(( string name_preset )) {}
        virtual Script checkDefaultHUDPreset(( string name_preset )) {}
        virtual Script setCheckBoxHUDPreset(( string name_preset )) {}
        virtual Script resetPreset(( string name_preset, string name_menu )) {}
        virtual Script deletePreset(( string name_preset, string name_menu )) {}
        virtual Script loadObjectPropertyXml(( string object, string file_name )) {}
        virtual Script saveObjectPropertyXml(( string object, string file_name )) {}
        virtual Script saveGui(()) {}
        virtual Script saveHotBar(()) {}
        virtual Script loadAllGuiProperty(( string only_pos )) {}
        virtual Script loadHotBarData(()) {}
        virtual Script loadGui(()) {}
        virtual Script createClaimTileLegendItems(( string stackCtrl )) {}
        virtual Script createTileLegendItems(( string stackCtrl )) {}
        virtual Script createTilesLegendItem(( string tileImageIndex, string tileDescrText )) {}
        virtual Script openResetConfirmationDialog(()) {}
        virtual Script resetSettingsToDefault(()) {}
        virtual Script renamePreset(( string menu_name, string preset_name )) {}
        virtual Script ApplyBindQueue(()) {}
        virtual Script CancelOptionsControlsDlg(()) {}
        virtual Script ShowOptionsControls(()) {}
        virtual Script createOptionsControlsDlg(()) {}
        virtual Script restartMusic(()) {}
        virtual Script OptAudioUpdateVoiceChatVolume(( string volume )) {}
        virtual Script OptAudioUpdateChannelVolume(( string description, string volume )) {}
        virtual Script OptAudioUpdateMasterVolume(( string volume )) {}
        virtual Script addOptionsAudiArrowSlider(( string id_label, string slider_range, string slider_name, string slider_command )) {}
        virtual Script createOptionsAudioDlg(()) {}
        virtual Script addArrowSlider(( string id_label, string slider_range, string slider_name, string slider_command, string text_edit_name, string text_edit_command, string id_descrip )) {}
        virtual Script addCheckBox(( string id_label, string id_descrip, string name_check_box, string command_check_box )) {}
        virtual Script addCheckBoxRow(( string id_label_left, string id_descrip_left, string name_check_box_left, string command_check_box_left, string id_label_right, string id_descrip_right, string name_check_box_right, string command_check_box_right )) {}
        virtual Script addDropDown(( string id_label, string popup_name, string popup_command )) {}
        virtual Script changePreset(( string preset )) {}
        virtual Script toggleBorderlessWindow(()) {}
        virtual Script _makePrettyResString(( string resString )) {}
        virtual Script createOptionsVideoDlg(()) {}
        virtual Script updateTrebuchetRopeAngle(()) {}
        virtual Script createTrebuchetWindow(()) {}
        virtual Script createBarterWindow(()) {}
        virtual Script CreateCharacterIsAcceptLosePoints(()) {}
        virtual Script CreateCharacterAcceptLosePoints(()) {}
        virtual Script CharSelectionCreatePressed(()) {}
        virtual Script checkChilSkillSlider(( string parentSlider, string childSlider )) {}
        virtual Script clearSliders(()) {}
        virtual Script SetAssaulterRange(( string min, string max )) {}
        virtual Script SetSlingerRange(( string min, string max )) {}
        virtual Script SetFootmanRange(( string min, string max )) {}
        virtual Script SetMilitiaRange(( string min, string max )) {}
        virtual Script SetCavalrymanRange(( string min, string max )) {}
        virtual Script SetHuntingRange(( string min, string max )) {}
        virtual Script SetNatureloreRange(( string min, string max )) {}
        virtual Script SetConstructRange(( string min, string max )) {}
        virtual Script SetArtisanRange(( string min, string max )) {}
        virtual Script SetIntelligenceRange(( string min, string max )) {}
        virtual Script SetWillpowerRange(( string min, string max )) {}
        virtual Script SetConstitutionRange(( string min, string max )) {}
        virtual Script SetAgilityRange(( string min, string max )) {}
        virtual Script SetStrenghtRange(( string min, string max )) {}
        virtual Script createRandomizeButton(( string command )) {}
        virtual Script createDropBox(( string popUpMenuName, string caption )) {}
        virtual Script createColorSlider(( string sliderName, string colorName, string caption )) {}
        virtual Script createTextEditSlider(( string caption, string slider_name, string text_value_name )) {}
        virtual Script createSimpleSlider(( string sliderName, string caption, string range )) {}
        virtual Script createEditBox(( string editBoxName, string caption, string maxLength )) {}
        virtual Script createNamedStackControl(( string caption )) {}
        virtual Script createPopUpScroll(()) {}
        virtual Script createComboStackCombatSkills(( string combo_stack_ctrl, string group_num )) {}
        virtual Script createComboStackCraftingSkills(( string combo_stack_ctrl, string group_num )) {}
        virtual Script createComboStackAttributes(( string combo_stack_ctrl, string group_num )) {}
        virtual Script createComboStackSettingAppearance(( string combo_stack_ctrl, string group_num )) {}
        virtual Script createComboStackRace(( string combo_stack_ctrl, string group_num )) {}
        virtual Script createCharRaceButton(( string name, string text, string defaultState )) {}
        virtual Script createComboStackSex(( string combo_stack_ctrl, string group_num )) {}
        virtual Script createComboStackName(( string combo_stack_ctrl, string group_num )) {}
        virtual Script createComboStackItem(( string combo_stack_ctrl, string name, string pnl_height, string group_num, string image, string is_race )) {}
        virtual Script createWindowCreateCharacter(()) {}
        virtual Script fadeScreen(( string fade )) {}
        virtual Script togglSettingsMenu(( string show )) {}
        virtual Script toggleEscMenu(( string show )) {}
        virtual Script hideEscMenu(()) {}
        virtual Script showEscMenuOptions(()) {}
        virtual Script showEscMenu(()) {}
        virtual Script setBuildName(( string name )) {}
        virtual Script createBuildComponentsItem(( string key )) {}
        virtual Script hideCharacterSelectionDialog(()) {}
        virtual Script showCharacterSelectionDialog(()) {}
        virtual Script initManagersOnCreatePlayer(()) {}
        virtual Script createStatFrame(( string handle, string nameId, string icon )) {}
        virtual Script createCharSlotButton(( string internalName )) {}
        virtual Script endIntro(()) {}
        virtual Script showLifeIsFeudalIntro(()) {}
        virtual Script showXsollaIntro(()) {}
        virtual Script showBitboxIntro(()) {}
        virtual Script createIntroWindow(( string videoFile, string command )) {}
        virtual Script createBuildWindow(()) {}
        virtual Script createAuthorityWindowProfiles(()) {}
        virtual Script createAuthorityWindow(( string is_manager, string typeid )) {}
        virtual Script MessageBoxYesNoOld(( string title, string message, string yesCallback, string noCallback )) {}
        virtual Script MessageBoxOKCancelOld(( string title, string message, string callback, string cancelCallback )) {}
        virtual Script MessageBoxOKOld(( string title, string message, string callback )) {}
        virtual Script CmTerminateMessageDialogue(( string messageIDToDelete )) {}
        virtual Script CmSetDialogueMessageID(( string messageID )) {}
        virtual Script MessageIDBoxDlg(( string dialog, string title, string message, string btn1Callback, string btn1Caption, string btn2Callback, string btn2Caption, string btn3Callback, string btn3Caption, string timer )) {}
        virtual Script CmMessageIDBoxClose(()) {}
        virtual Script CmMessageIDBox(( string title, string message, string btnCallback, string btn1Caption, string btn2Caption, string btn3Caption, string closeBtnIndex, string timer )) {}
        virtual Script setBtnCenterXPos(( string btn )) {}
        virtual Script setBtnPos(( string btn, string x )) {}
        virtual Script MBIDSetText(( string text, string frame, string msg )) {}
        virtual Script MessageBoxYesNoCancel(( string title, string message, string yesCallback, string noCallback, string cancelCallback )) {}
        virtual Script MessageBoxYesNo(( string title, string message, string yesCallback, string noCallback )) {}
        virtual Script MessageBoxOKCancel(( string title, string message, string callback, string cancelCallback )) {}
        virtual Script MessageBoxOK(( string title, string message, string callback )) {}
        virtual Script MBSetText(( string text, string frame, string msg )) {}
        virtual Script messageCallback(( string dlg, string callback )) {}
        virtual Script createRenameComplexObjectDialog(( string objectTypeName, string currentObjectName )) {}
        virtual Script MessageBoxRenameContainer(()) {}
        virtual Script MessageBoxDelchar(( string slot )) {}
        virtual Script CharSelectionDelcharSlot(( string charSlotId, string givenText )) {}
        virtual Script CharSelectionDelcharOK(( string dialog, string givenText )) {}
        virtual Script CharSelectionDelcharDoubleCheck(( string dialog, string givenText )) {}
        virtual Script ShowNameBoxInput(( string command_name )) {}
        virtual Script createMessageBoxInputText(( string command_name, string cancelCommandName, string caption, string label )) {}
        virtual Script createMessageIDBoxDlg(( string MessageBoxName )) {}
        virtual Script createSlaveSlots(()) {}
        virtual Script createSlaveSlot(( string name, string pos )) {}
        virtual Script CreateOutpostDialog(()) {}
        virtual Script CloseAnimalHusbandryDlg(()) {}
        virtual Script createBreedingHorizontalStack(( string mainStack )) {}
        virtual Script createBreedingVerticalStack(( string mainStack )) {}
        virtual Script createAnimalHusbandryVerticalSplitter(( string parent )) {}
        virtual Script createAnimalHusbandryHorizontalSplitter(( string parent )) {}
        virtual Script createAnimalHusbandryBreedingSlot(( string index )) {}
        virtual Script createAnimalHusbandryDeed(()) {}
        virtual Script createAnimalHusbandryBreedingPanel(()) {}
        virtual Script createAnimalHusbandry(()) {}
        virtual Script testStackMsg(( string count )) {}
        virtual Script addEventMsgInfoWindow(( string text, string type )) {}
        virtual Script createMsgEventWindow(()) {}
        virtual Script msgEventWindowDefaultProperty(()) {}
        virtual Script MsgStackCommand(( string ctrl )) {}
        virtual Script addMsgStackInfoWindow(( string text, string type, string infoHint )) {}
        virtual Script createMsgStackInfoWindow(()) {}
        virtual Script msgStackInfoWindowDefaultProperty(()) {}
        virtual Script addMsgInfoWindow(( string text, string important, string type, string infoHint )) {}
        virtual Script createMessageWindow(( string pos, string ext, string saveFileName, string autoWidth, string msgCount, string msgTime )) {}
        virtual Script onContextMenuDown(( string container )) {}
        virtual Script onContextMenuUp(( string container )) {}
        virtual Script showMenuDecor(( string decor, string menu_item, string is_left, string is_def, string is_sub )) {}
        virtual Script createContextMenuDecor(( string parent, string is_left, string is_sub )) {}
        virtual Script createGroupWidgetButton(( string menu, string text, string group )) {}
        virtual Script addInGroupAbilityWidgetButton(( string menu, string text, string skillID, string image )) {}
        virtual Script createSingleAbilityWidgetButton(( string menu, string text, string image )) {}
        virtual Script createDefaultAbilityWidgetButton(( string menu, string text )) {}
        virtual Script createAbilityWidgetButton(( string menu )) {}
        virtual Script createGroupAbilitysStack(( string skillID, string image )) {}
        virtual Script createContextMenuContainer(( string main_pnl, string pos )) {}
        virtual Script createContextSubMenuContainer(( string main_pnl, string pos )) {}
        virtual Script createAbilityWidget(( string menu_pos, string full_screen )) {}
        virtual Script Lif_ContextMenu_OnPressedContext(( string val )) {}
        virtual Script Lif_ContextMenu_OnPressedDefault(( string val )) {}
        virtual Script RecipesClick(( string skillInfo )) {}
        virtual Script UsableItemsClick(( string skillInfo )) {}
        virtual Script SkillLvl100Click(( string skillPnl )) {}
        virtual Script SkillLvl90Click(( string skillPnl )) {}
        virtual Script SkillLvl60Click(( string skillPnl )) {}
        virtual Script SkillLvl30Click(( string skillPnl )) {}
        virtual Script SkillLvl0Click(( string skillPnl )) {}
        virtual Script setUnknownSkillBorder(( string btnSkillLvl )) {}
        virtual Script setKnownSkillBorder(( string btnSkillLvl )) {}
        virtual Script createSkillInfo(()) {}
        virtual Script createSkillLvlControl(( string skillInfo )) {}
        virtual Script createAbilityInfoControl(( string skillInfo, string id, string icon, string name, string desc )) {}
        virtual Script createRecipeItemsTable(( string skillInfo )) {}
        virtual Script SkillInfoAddItem(( string skillInfo, string icon )) {}
        virtual Script createSkillMapPnl(( string parent, string skillGroup )) {}
        virtual Script GetBoosterSku(( string type )) {}
        virtual Script showAlignmentBar(()) {}
        virtual Script showHungerBar(()) {}
        virtual Script showStaminaBar(()) {}
        virtual Script showHealthBar(()) {}
        virtual Script updateMaxSkillcap(( string max_val1, string max_val2, string max_val3 )) {}
        virtual Script updateSkillcap(( string cur_val, string max_val, string skill_group )) {}
        virtual Script showGuild(()) {}
        virtual Script showSkills(()) {}
        virtual Script showStats(()) {}
        virtual Script addSkill(( string skillPanel, string skillTypeId, string skillInfo )) {}
        virtual Script addSkills(( string skillPanel, string groupSkill, string skillInfo )) {}
        virtual Script getSkillItemPosition(( string skill_type_id )) {}
        virtual Script getSkillLinePosition(( string skillPanel, string skillCtrl, string skillTypeId )) {}
        virtual Script createSkillItem(( string skillInfo )) {}
        virtual Script addSkillLine(( string parent, string pos, string len )) {}
        virtual Script createCraftingComponentsPanel(()) {}
        virtual Script createCraftingComponentPanel(( string name )) {}
        virtual Script toggleGuiCraftWindow(( string val )) {}
        virtual Script createCraftWindow(()) {}
        virtual Script setEquipCountText(( string textCtrl, string val )) {}
        virtual Script resetHighlightSlot(( string slot_ctrl, string slot )) {}
        virtual Script setHighlightSlot(( string slot_ctrl, string slot )) {}
        virtual Script showSkinsList(()) {}
        virtual Script showSkinsWindow(( string slotId )) {}
        virtual Script showHideMiniCharWindow(()) {}
        virtual Script createEquipmentWindow(()) {}
        virtual Script createCharParamStatsPnl(()) {}
        virtual Script closeCharacterWindow(()) {}
        virtual Script setTabIcon(( string tabBitmap, string iconName )) {}
        virtual Script showSocial(()) {}
        virtual Script showStatEqip(()) {}
        virtual Script showMinorSkills(()) {}
        virtual Script showCombatSkills(()) {}
        virtual Script showCraftingSkills(()) {}
        virtual Script socialClick(()) {}
        virtual Script equipStatsClick(()) {}
        virtual Script MinorSkillsClick(()) {}
        virtual Script combatSkillsClick(()) {}
        virtual Script craftingSkillsClick(()) {}
        virtual Script showCharacterWindowSelectedTabDecor(( string selectTab )) {}
        virtual Script createCharacterWindow(()) {}
        virtual Script toggleMap(( string val )) {}
        virtual Script createGuiMapWindow(()) {}
        virtual Script createHotBarWindow(()) {}
        virtual Script createHotBarTabBook(()) {}
        virtual Script initCraftworkBrewingTankOptionsDlg(( string maxProductCount, string bitmap )) {}
        virtual Script openProspectingRadiusDialog(( string minRadius, string maxRadius, string caption, string label, string bitmap )) {}
        virtual Script ShowInventory(( string val )) {}
        virtual Script showSplitStackItemDialog(( string quantity1, string max_stack_size1, string quantity2, string max_stack_size2, string bitmap, string name )) {}
        virtual Script updateVersionBarText(()) {}
        virtual Script refreshCenterTextCtrl(()) {}
        virtual Script refreshBottomTextCtrl(()) {}
        virtual Script onServerQueryStatus(( string status, string msg, string value )) {}
        virtual Script showDirectConnectDialog(( string maxPwdLen, string callbackFunctionName )) {}
        virtual Script createDirectConnectDialogProfiles(()) {}
        virtual Script createDirectConnectDialog(()) {}
        virtual Script showPasswordDialog(( string descr, string maxPwdLen, string callbackFunctionName )) {}
        virtual Script createPasswordDialogProfiles(()) {}
        virtual Script createPasswordDialog(()) {}
        virtual Script updateJudgementHourInfo(( string startTime, string duration, string weekShedule )) {}
        virtual Script updateAdditionalServerInfo(( string SkillsStatsMult, string Skillcap, string TerraformingSpeed, string CraftingPeriod, string AnimalBFPeriod, string DayCycle, string AnimalsCount, string ObjectDecayRate )) {}
        virtual Script updateMainServerInfo(( string pName, string bLocked, string nPlayersCount, string nMaxPlayersCount, string nLatency )) {}
        virtual Script createServerItem(( string nId, string bLocked, string pName, string nPlayersCount, string nMaxPlayersCount, string nLatency )) {}
        virtual Script updateServerListButtonSortType(( string btn, string imageSortIndex, string buttonSortType )) {}
        virtual Script setServerListSortType(( string buttonId )) {}
        virtual Script clearButtonSortType(( string buttonId )) {}
        virtual Script getSortButtonById(( string buttonId )) {}
        virtual Script createServerList(( string serverListName, string bVisible )) {}
        virtual Script deleteJoinWorldProfiles(()) {}
        virtual Script createJoinWorldProfiles(()) {}
        virtual Script createJoinWorldWindow(()) {}
        virtual Script createCreateWorldWindow(()) {}
        virtual Script createMainMenuMultiplayerWindow(()) {}
        virtual Script createSubtitlesTheoraCtrl(( string videoFile, string command, string internalName )) {}
        virtual Script showHorseBar(( string show )) {}
        virtual Script setHorseBar(( string hp, string stamina )) {}
        virtual Script createHorseGUI(()) {}
        virtual Script setOxygenBar(( string val )) {}
        virtual Script createOxygenBar(()) {}
        virtual Script setStaminaBar(( string firstVal, string secondVal, string max )) {}
        virtual Script createStaminaBar(()) {}
        virtual Script setHealthBar(( string firstVal, string secondVal, string max )) {}
        virtual Script createHPBar(()) {}
        virtual Script setHungerBar(( string val )) {}
        virtual Script createHungerBar(()) {}
        virtual Script changeBarValues(( string barCtrl, string val, string maxVal )) {}
        virtual Script updateBarLayout(( string barCtrl )) {}
        virtual Script closeGroupUnitWindow(()) {}
        virtual Script clearUnitMemberWidgets(()) {}
        virtual Script createUnitMemberBar(( string barName, string barImageIndex )) {}
        virtual Script createUnitMemberWidget(( string unitName, string unitIcon )) {}
        virtual Script createUnitWindow(()) {}
        virtual Script updateControlsComboStep(( string comboStep, string bMaximized )) {}
        virtual Script createComboStep(()) {}
        virtual Script deleteCombosWindow(()) {}
        virtual Script closeCombosWindow(()) {}
        virtual Script createCombosWindow(()) {}
        virtual Script deleteAlignmentBar(()) {}
        virtual Script closeAlignmentBar(()) {}
        virtual Script createAlignmentBar(()) {}
        virtual Script closeTargetBar(()) {}
        virtual Script createTargetBar(()) {}
        virtual Script reexec(()) {}
        virtual Script deleteCommonTooltipProfiles(()) {}
        virtual Script createCommonTooltipProfiles(()) {}
        virtual Script calcFoodValue(( string informer )) {}
        virtual Script getFoodComplexity(( string informer )) {}
        virtual Script calcCritWeaponWeight(( string informer )) {}
        virtual Script calcDefence(( string informer, string isDefault )) {}
        virtual Script calcMaxMinOHDmg(( string informer, string data_block, string isDefault )) {}
        virtual Script calcMaxMinSwingDmg(( string informer, string data_block, string isDefault )) {}
        virtual Script calcMaxMinThrustDmg(( string informer, string data_block, string isDefault )) {}
        virtual Script calcMaxMinDmg(( string informer, string data_block, string index, string factor, string isDefault )) {}
        virtual Script createUsableItemsDefaultTooltip(( string informer )) {}
        virtual Script createUsableItemsShieldsTooltip(( string informer )) {}
        virtual Script createUsableItemsArmorTooltip(( string informer )) {}
        virtual Script createUsableItemsRangedWeaponTooltip(( string informer )) {}
        virtual Script createUsableItemsMeleeWeaponTooltip(( string informer )) {}
        virtual Script createBuildItemTooltip(( string informer )) {}
        virtual Script createRecipeTooltip(( string informer )) {}
        virtual Script createWillpowerTooltip(( string informer )) {}
        virtual Script createIntelectTooltip(( string informer )) {}
        virtual Script createConstitutionTooltip(( string informer )) {}
        virtual Script createAgilityTooltip(( string informer )) {}
        virtual Script createStrengthTooltip(( string informer )) {}
        virtual Script createWoundTooltip(( string informer )) {}
        virtual Script createEffectTooltip(( string informer )) {}
        virtual Script createTextTooltip(( string informer )) {}
        virtual Script createNameTooltip(( string informer )) {}
        virtual Script createFoodItemTooltip(( string informer )) {}
        virtual Script createBlueprintTooltip(( string informer )) {}
        virtual Script createWarhorsesTooltip(( string informer )) {}
        virtual Script createSimpleHorsesTooltip(( string informer )) {}
        virtual Script createDomesticAnimalsTooltip(( string informer )) {}
        virtual Script createOutfitsTooltip(( string informer )) {}
        virtual Script createArmorTooltip(( string informer )) {}
        virtual Script createShieldsTooltip(( string informer )) {}
        virtual Script createThrowingWeaponTooltip(( string informer )) {}
        virtual Script createAmmoWeaponTooltip(( string informer )) {}
        virtual Script createRangedWeaponTooltip(( string informer )) {}
        virtual Script createMeleeWeaponTooltip(( string informer )) {}
        virtual Script createGameplayObjectsQuantityWeightTooltip(( string informer )) {}
        virtual Script createGameplayObjectsQQWTooltip(( string informer )) {}
        virtual Script createCraftToolsEquipmentTooltip(( string informer )) {}
        virtual Script createBagTooltip(( string informer )) {}
        virtual Script createAlchemyTooltip(( string informer )) {}
        virtual Script fillTooltipTemplate(()) {}
        virtual Script setAdvancedLighting(()) {}
        virtual Script onDeactivateAdvancedLM(()) {}
        virtual Script onActivateAdvancedLM(()) {}
        virtual Script unlockShadowViz(()) {}
        virtual Script lockShadowViz(()) {}
        /*!  For convenience, push the viz dialog and set the light manually from the console.
     */
        virtual Script showShadowVizForLight(( string light )) {}
        /*!  Called from the WorldEditor when an object is selected.
     */
        virtual Script _setShadowVizLight(( string light, string force )) {}
        /*!  Toggles the visualization of the pre-pass lighting buffer.
     */
        virtual Script toggleShadowViz(()) {}
        /*!  Toggles the visualization of the AL lighting specular power buffer.
     */
        virtual Script toggleLightSpecularViz(( string enable )) {}
        /*!  Toggles the visualization of the AL lighting color buffer.
     */
        virtual Script toggleLightColorViz(( string enable )) {}
        /*!  Toggles the visualization of the AL normals buffer.
     */
        virtual Script toggleNormalsViz(( string enable )) {}
        /*!  Toggles the visualization of the AL depth buffer.
     */
        virtual Script toggleDepthViz(( string enable )) {}
        virtual Script onLightManagerDeactivate(( string lmName )) {}
        virtual Script onLightManagerActivate(( string lmName )) {}
        virtual Script initLightingSystems(()) {}
        virtual Script initRenderManager(()) {}
        virtual Script clientCmdGhostAllGhostAlwaysReceived(()) {}
        virtual Script onGhostAlwaysObjectReceived(()) {}
        virtual Script onGhostAlwaysStarted(( string ghostCount )) {}
        virtual Script updateStreamingProgress(()) {}
        virtual Script onStreamingEndLoad(()) {}
        virtual Script onStreamingBeginLoad(()) {}
        virtual Script onStreamingEndFastLoad(()) {}
        virtual Script onStreamingBeginFastLoad(()) {}
        virtual Script onStreamingEndReloadWorld(( string callback )) {}
        virtual Script onStreamingBeginReloadWorld(()) {}
        virtual Script onStreamingEndInitialLoadWorld(( string callback )) {}
        virtual Script onStreamingBeginInitialLoadWorld(()) {}
        virtual Script updateGMtext(()) {}
        virtual Script clientCmdReadyStateAck(()) {}
        virtual Script clientDestroyWorld(()) {}
        virtual Script _clientReloadWorld(( string geoId, string callback )) {}
        virtual Script _clientCreateWorld(( string geoId, string callback )) {}
        virtual Script defaultMessageCallback(( string msgType, string msgString, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9, string a10 )) {}
        virtual Script onServerMessage(( string a, string b, string c, string d, string e, string f, string g, string h, string i )) {}
        virtual Script addMessageCallback(( string msgType, string func )) {}
        virtual Script clientCmdServerMessage(( string msgType, string msgString, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9, string a10 )) {}
        virtual Script clientCmdChatMessage(( string sender, string voice, string pitch, string msgString, string a1, string a2, string a3, string a4, string a5, string a6, string a7, string a8, string a9, string a10 )) {}
        virtual Script cm_config_CalcPlayerPostHitTimeScale(( string lvl )) {}
        virtual Script cm_config_CalcPlayerHitTimeScale(( string lvl )) {}
        virtual Script jettisonWriteFile(( string fileName, string type, string value )) {}
        virtual Script jettisonReadFile(( string fileName )) {}
        virtual Script JettisonArray(( string name )) {}
        virtual Script JettisonObject(()) {}
        virtual Script __jettisonParse(( string text, string index, string length )) {}
        /*!  jettisonStringify: (type: string, value: *) -> string
     Serialize an arbitrary value into a JSON string.
    
     Always returns valid JSON, unless:
      * `type` is not a valid JSON type - returns error string
      * `type == "object"` but `value` does not implement `::toJSON()` -
        missing function console error message and empty string return
     */
        virtual Script jettisonStringify(( string type, string value )) {}
        /*!  JSON type names and their respective values
    
      * `"string"` - A TorqueScript string encoded as UTF-8
      * `"number"`
      * `"boolean"` - 1 (true) or 0 (false)
      * `"null"` - Empty string
      * `"object"` - Any TorqueScript object. Should implement `::toJSON()`
        for string serialization. Use `.class` to disambiguate.
    
     jettisonParse: (text: string) -> boolean
     Deserialize the JSON string `text`.
    
     On success, returns false, setting `$JSON::Value` and `$JSON::Type`.
    
     On failure, returns true, setting `$JSON::Error` and `$JSON::Index`.
    
     Example:
    
         if (jettisonParse(%text)) {
             error("JSON error (at " @ $JSON::Index @ "): " @ $JSON::Error);
             return;
         }
    
         echo($JSON::Value @ ": " @ $JSON::Type);
     */
        virtual Script jettisonParse(( string text )) {}
        virtual Script setLoadingGuiText(( string text )) {}
        virtual Script updateLoadingTextProgress(()) {}
        virtual Script loadLoadingGui(( string text )) {}
        virtual Script changeTooltipText(()) {}
        virtual Script deleteLoadingGui(()) {}
        virtual Script createLoadingGui(()) {}
        virtual Script netSimulateLag(( string msDelay, string packetLossPercent )) {}
        /*!  A helper function which will return the ghosted client object
     from a server object when connected to a local server.
     */
        virtual Script serverToClientObject(( string serverObject )) {}
        virtual Script initBaseClient(()) {}
        virtual Script updateNetGraphData(( string obj, string name0, string val0, string name1, string val1, string name2, string val2, string name3, string val3, string name4, string val4, string name5, string val5 )) {}
        virtual Script updateNetGraphCountsStats(()) {}
        virtual Script updateNetGraphTrafficStats(()) {}
        virtual Script toggleNetGraphCounter(()) {}
        virtual Script toggleNetGraphTraffic(()) {}
        virtual Script getNextGraphPos(()) {}
        virtual Script toggleNetGraph(()) {}
        virtual Script createNetGraph(( string graphName, string pos )) {}
        virtual Script deleteNetGraphGui(()) {}
        virtual Script createNetGraphGui(()) {}
        virtual Script execNetGraphGuiGUI(()) {}
        virtual Script postVerbose(( string string )) {}
        /*!  Toggles the visualization of the AL lighting specular power buffer.
     */
        virtual Script toggleSpecMapViz(( string enable )) {}
        /*!  Toggles the visualization of the AL lighting specular power buffer.
     */
        virtual Script toggleColorBufferViz(( string enable )) {}
        virtual Script doDirtyDrop(()) {}
        virtual Script doRainDrop(()) {}
        virtual Script doBloodDrop(()) {}
        virtual Script initDrinkPostEffect(( string distQ, string refrac1, string refrac2 )) {}
        virtual Script initPostEffects(()) {}
        virtual Script imposterMetricsCallback(()) {}
        virtual Script clientCmdClearBottomPrint(()) {}
        virtual Script clientCmdClearCenterPrint(()) {}
        virtual Script clientCmdBottomPrint(( string message, string time, string size )) {}
        virtual Script clientCmdCenterPrint(( string message, string time, string size )) {}
        virtual Script metrics(( string expr )) {}
        virtual Script videoMetricsCallback(()) {}
        virtual Script audioMetricsCallback(()) {}
        virtual Script irspMetricsCallback(()) {}
        virtual Script streamingMetricsCallback(()) {}
        virtual Script detailsMetricsCallback(()) {}
        virtual Script tergenMetricsCallback(()) {}
        virtual Script termemMetricsCallback(()) {}
        virtual Script eproxyMetricsCallback(()) {}
        virtual Script partMetricsCallback(()) {}
        virtual Script particleMetricsCallback(()) {}
        virtual Script lightMetricsCallback(()) {}
        virtual Script basicShadowMetricsCallback(()) {}
        virtual Script shadowMetricsCallback(()) {}
        virtual Script renderMetricsCallback(()) {}
        virtual Script decalMetricsCallback(()) {}
        virtual Script reflectMetricsCallback(()) {}
        virtual Script timeMetricsCallback(()) {}
        virtual Script sfxStatesMetricsCallback(()) {}
        virtual Script sfxSourcesMetricsCallback(()) {}
        virtual Script sfxMetricsCallback(()) {}
        virtual Script forestMetricsCallback(()) {}
        virtual Script groundCoverMetricsCallback(()) {}
        virtual Script netMetricsCallback(()) {}
        virtual Script terrainMetricsCallback(()) {}
        virtual Script gfxMetricsCallback(()) {}
        virtual Script fpsMetricsCallback(()) {}
        virtual Script openPollVotingBrowser(()) {}
        virtual Script showPollVotingWindow(()) {}
        virtual Script clientCmdPollVoting(( string url, string timeBetweenVotes )) {}
        virtual Script parseMissionGroupForIds(( string className, string childGroup )) {}
        virtual Script parseMissionGroup(( string className, string childGroup )) {}
        virtual Script shareValueSafeDelay(( string source, string dest, string delayMs )) {}
        virtual Script shareValueSafe(( string source, string dest )) {}
        virtual Script setValueSafe(( string dest, string val )) {}
        virtual Script loadFileText(( string file )) {}
        virtual Script fieldPos(( string text, string field, string start )) {}
        virtual Script wordPos(( string text, string word, string start )) {}
        virtual Script validateDatablockName(( string name )) {}
        /*!  This will close the console and take a large format
     screenshot by tiling the current backbuffer and save
     it to the root game folder.
    
     For instance a tile setting of 4 with a window set to
     800x600 will output a 3200x2400 screenshot.
     */
        virtual Script tiledScreenShot(( string tiles, string overlap )) {}
        /*!  Internal function which generates unique filename
     and triggers a screenshot capture.
     */
        virtual Script _screenShot(( string tiles, string overlap, string hudless )) {}
        /*!  This is bound in initializeCommon() to take
     a screenshot on a keypress.
     */
        virtual Script doScreenShot(( string val )) {}
        virtual Script stopMovie(()) {}
        virtual Script recordMovie(( string movieName, string fps, string encoder )) {}
        virtual Script formatSessionNumber(( string number )) {}
        virtual Script formatImageNumber(( string number )) {}
        virtual Script InspectVarsToggleCursor(()) {}
        virtual Script InspectVars(( string filter )) {}
        virtual Script GuiEditorIsActive(()) {}
        virtual Script EditorIsActive(()) {}
        virtual Script resetCanvas(()) {}
        virtual Script initializeCanvas(()) {}
        virtual Script configureCanvas(()) {}
        /*!  Resumes the playback of paused sound sources.
     
     @param %pauseSet    An optional SimSet which contains the paused sound 
                         sources to be resumed.  If not specified the global 
                         SfxSourceGroup is used.
     @deprecated
    
     */
        virtual Script sfxResume(( string pauseSet )) {}
        /*!  Pauses the playback of active sound sources.
     
     @param %channels    An optional word list of channel indices or an empty 
                         string to pause sources on all channels.
     @param %pauseSet    An optional SimSet which is filled with the paused 
                         sources.  If not specified the global SfxSourceGroup 
                         is used.
    
     @deprecated
    
     */
        virtual Script sfxPause(( string channels, string pauseSet )) {}
        virtual Script sfxSetChannelVolume(( string channel, string volume )) {}
        virtual Script sfxGetChannelVolume(( string channel )) {}
        virtual Script sfxStopAll(( string channel )) {}
        virtual Script sfxGetVoiceChatVolume(( string volume )) {}
        virtual Script sfxSetVoiceChatVolume(( string volume )) {}
        virtual Script sfxGetMasterVolume(( string volume )) {}
        virtual Script sfxSetMasterVolume(( string volume )) {}
        virtual Script sfxGroupToOldChannel(( string group )) {}
        virtual Script sfxOldChannelToGroup(( string channel )) {}
        /*!  Try to detect and initalize the best SFX device available.
     */
        virtual Script sfxAutodetect(()) {}
        /*!  Determines which of the two SFX providers is preferable.
     */
        virtual Script sfxCompareProvider(( string providerA, string providerB )) {}
        /*!  Destroys the current sound system device.
     */
        virtual Script sfxShutdown(()) {}
        /*!  This initializes the sound system device from
     the defaults in the $pref::SFX:: globals.
     */
        virtual Script sfxInit(()) {}
        /*!  This initializes the sound system device from
     the defaults in the $pref::SFX:: globals.
     */
        virtual Script sfxStartup(()) {}
        virtual Script reloadMaterials(()) {}
        virtual Script loadMaterialsRecursivelyInFolder(( string rootFolder )) {}
        virtual Script loadMaterials(()) {}
        virtual Script reloadCoreMaterials(()) {}
        virtual Script loadCoreMaterials(()) {}
        virtual Script dumpKeybindings(()) {}
        virtual Script guiShutdown(()) {}
        virtual Script shutdownCore(()) {}
        virtual Script initializeCore(()) {}
        virtual Script GraphicsQualityAutodetect_Apply(( string shaderVer, string intel, string videoMem )) {}
        virtual Script GraphicsQualityAutodetect(()) {}
        virtual Script loadDirs(( string dirPath )) {}
        virtual Script dumpSysInfo(( string where )) {}
        virtual Script loadDir(( string dir )) {}
        virtual Script clientCmdTakeCameraPos(( string pos )) {}
        virtual Script createCanvas(( string windowTitle )) {}
        virtual Script isScriptFile(( string path )) {}
        virtual Script compileFiles(( string pattern )) {}
        virtual Script defaultParseArgs(()) {}
        virtual Script popFront(( string list, string delim )) {}
        virtual Script pushBack(( string list, string token, string delim )) {}
        virtual Script pushFront(( string list, string token, string delim )) {}
        virtual void initSoundsManager() {}
        virtual void removeSoundsManager() {}
        virtual void PlaySound2D() {}
        virtual void initCameraStateSettings(()) {}
        virtual void toggleVmode(( bool state )) {}
        virtual void setFittingModeCamera(( bool state )) {}
        virtual void ReviveCharacter(()) {}
        virtual string getSunPos(( Point3F worldPos, int hour, int minute, int seconds )) {}
        virtual void changeStreamingSpeed() {}
        virtual void _checkSimManagerValidity(()) {}
        virtual void loadAttackAnimationsXml() {}
        virtual void loadXmlDataForSpecialAttacks() {}
        virtual void InitVolley() {}
        virtual void CancelVolley() {}
        virtual void unloadComplexObjectTypes(()) {}
        /*! @brief Set the default FOV for a camera.
    @param defaultFOV The default field of view in degrees
    @ingroup CameraSystem */
        virtual void setDefaultFov(( float defaultFOV )) {}
        /*! @brief Set the zoom speed of the camera.
    This affects how quickly the camera changes from one field of view to another.
    @param speed The camera's zoom speed in ms per 90deg FOV change
    @ingroup CameraSystem */
        virtual void setZoomSpeed(( int speed )) {}
        /*! @brief Set the FOV of the camera.
    @param FOV The camera's new FOV in degrees
    @ingroup CameraSystem */
        virtual void setFov(( float FOV )) {}
        /*! @brief Prevents mouse movement from being processed
    
    In the source, whenever a mouse move event occurs GameTSCtrl::onMouseMove() is called. Whenever snapToggle() is called, it will flag a variable that can prevent this from happening: gSnapLine. This variable is not exposed to script, so you need to call this function to trigger it.
    
    @tsexample
    // Snapping is off by default, so we will toggle
    // it on first:
    PlayGui.snapToggle();
    
    // Mouse movement should be disabled
    // Let's turn it back on
    PlayGui.snapToggle();
    @endtsexample
    
    @ingroup GuiGame */
        virtual void snapToggle(()) {}
        /*! Get the MissionArea object, if any.
    
    @ingroup enviroMisc
    
     */
        virtual string getMissionAreaServerObject(()) {}
        virtual void setInteriorRenderMode() {}
        virtual float getPlayerVitality(()) {}
        virtual float oxygenRatio(()) {}
        virtual float getPoisonRate(()) {}
        virtual float getOxygen(()) {}
        virtual void setPlayerVitalityDelay(( float delay )) {}
        virtual int getHungerRate(()) {}
        virtual void dbgEnableTransitions() {}
        virtual void dbgDisableTransitions() {}
        virtual void approachBuildCamera() {}
        virtual void moveAwayBuildCamera() {}
        virtual void AskServerForEffects() {}
        virtual void askServerForHitboxRayCast() {}
        virtual void printServerHitboxRayCastResult() {}
        virtual string getFirstName() {}
        virtual string getLastName() {}
        virtual int getGender() {}
        virtual void stopAmbientSounds() {}
        virtual void startAmbientSounds() {}
        virtual string getShapeBaseImageData(( int objectTypeId )) {}
        /*! Saves the decals for the active mission in the entered filename.
    @param decalSaveFile Filename to save the decals at.
    @tsexample
    // Set the filename to save the decals in. If no filename is set, then the decals will
       default to <activeMissionName>.mis.decals
    %fileName = "./missionDecals.mis.decals";
    // Inform the decal manager to save the decals for the active mission.
    decalManagerSave(%fileName);
    @endtsexample
    @ingroup FX */
        virtual void decalManagerSave(( String decalSaveFile="" )) {}
        /*! Loads the decals from the entered filename.
    @param fileName Filename to load the decals from.
    @return True if the decal manager was able to load the requested file, false if it could not.
    @tsexample
    // Set the filename to load the decals from.
    %fileName = "./missionDecals.mis.decals";
    // Inform the decal manager to load the decals from the entered filename.
    decalManagerLoad(%fileName);
    @endtsexample
    @ingroup FX */
        virtual bool decalManagerLoad(( string fileName )) {}
        /*! Returns if the decal manager has unsaved modifications.
    @return True if the decal manager has unsaved modifications, false if everything has been saved.
    @tsexample
    // Ask the decal manager if it has unsaved modifications.
    %hasUnsavedModifications = decalManagerDirty();
    @endtsexample
    @ingroup FX */
        virtual bool decalManagerDirty(()) {}
        /*! Removes all decals currently loaded in the decalManager.
    @tsexample
    // Tell the decal manager to remove all existing decals.
    decalManagerClear();
    @endtsexample
    @ingroup FX */
        virtual void decalManagerClear(()) {}
        /*! Adds a new decal to the decal manager.
    @param position Position for new decal to be placed. 
    @param normal Up vector for the decal.  Like the axel for this decal.
    @param rot Distance for this decal to be rotated around the normal, like a tire on an axel.
    @param scale Physical scale of new decal.
    @param decalData DecalData Datablock to use for the new decal.
    @param isImmortal Whether or not this decal is immortal. If immortal, it does not age and must be removed explicitly.
    @return Returns the ID of the new decal object or -1 on failure.
    @tsexample
    // Specify the decal position
    %position = "1.0 1.0 1.0";
    
    // Specify the up vector
    %normal = "0.0 0.0 1.0";
    
    // Specify the rotation for the decal
    %rotation = "0.5";
    
    // Specify the scale for the decal
    %scale = "0.35";
    
    // Specify the decalData datablock to use for this new decal
    %decalData = "decalDatablockName";
    
    // Specify if this decal is immortal. Immortal decals don't age and must be removed explicitly.
    %immortal = "false";
    
    // Tell the decal manager to remove all existing decals.
    decalManagerAddDecal( %position, %normal, %rotation, %scale, %decalData, %immortal);
    @endtsexample
    @ingroup FX */
        virtual int decalManagerAddDecal(( Point3F position, Point3F normal, float rot, float scale, DecalData decalData, bool isImmortal=false )) {}
        /*! Remove specified decal from the scene.
    @return Returns true if successful, false if decal not found.
    @param decalID Entry ID of the decal to remove.
    @tsexample
    // Specify a decal ID to be removed
    %decalID = 1;
    
    // Tell the decal manager to remove the specified decal ID.
    decalManagerRemoveDecal( %decalId )
    @endtsexample
    @ingroup FX */
        virtual bool decalManagerRemoveDecal(( int decalID )) {}
        /*! Calculates how much an explosion effects a specific object. Use this to determine
    damage values to objects based on their distance from the explosion's center point.
    @tsexample
    // Get the position of an explosion.
    %position = ExplosionData.getPosition();
    
    // Set a list of TypeMasks (defined in gameFunctioncs.cpp), seperated by the | character.
    %TypeMasks = $TypeMasks::StaticObjectType | $TypeMasks::ItemObjectType
    
    // Call the function, and acquire the value of effect, from 0.0f - 1.0f.
    %effectValue = calcExplosionCoverage(%position , %sceneObjectToEffect , %TypeMasks);
    @endtsexample
    @ingroup FX */
        virtual float calcExplosionCoverage(( Point3F pos=Point3F(0.0f, 0.0f, 0.0f), int id=NULL, int covMask=NULL )) {}
           /*! @brief Called on the client each time a datablock has been received.
    
    This callback is typically used to notify the player of how far along in the datablock download process they are.
    
    @param index The index of the datablock just received.
    @param total The total number of datablocks to be received.
    
    @see GameConnection, GameConnection::transmitDataBlocks(), GameConnection::onDataBlocksDone()
    
    @ingroup Networking
     */
           void onDataBlockObjectReceived( int index, int total );
     
        virtual void attachTCP(( SimObject tcp )) {}
        virtual void dumpProcessList() {}
        virtual void Sprint() {}
        virtual void SprintOn() {}
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
        virtual void physicsDebugDraw() {}
        virtual void cmVoronoiTest(( Point3F pos, Point3F size, int substanceType, int count, float impulse, int delay )) {}
        virtual void cmVoronoiExplode(( PhysicsDebris debris, Point3F pos, float radius, float impulse )) {}
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
        virtual void EULA() {}
        virtual void CmConfiguration_init() {}
        virtual void initCmLangManager() {}
        virtual string getPathToTranslatedFileIfExists() {}
        virtual void initCmMessages() {}
        virtual void MessageIDBoxBtnCallback() {}
        virtual void startShowingBoxedMessages() {}
        virtual void stopShowingBoxedMessages() {}
        virtual void clearQueuedBoxedMessages() {}
        virtual void cmShowMessage() {}
        virtual string GetMessageIDText() {}
        virtual string getServerConfigFolder(()) {}
        virtual bool isPermanentDeathGame(()) {}
        virtual bool isColonizationGameMode(()) {}
        virtual bool isColonizationQuestComplete(()) {}
        virtual void initManagersListThreaded(( ArrayObject list, string callbackCmd=nullptr )) {}
        virtual void deactivateDirectInput() {}
        virtual void activateDirectInput() {}
        virtual string strToPlayerName() {}
        virtual void lockMouse() {}
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
        virtual void initBreedingManager() {}
        virtual void removeBreedingManager() {}
        virtual void CharacterNameCache_remove() {}
        virtual void loadTriggersManager(()) {}
        virtual void initCharacterInfo() {}
        virtual void removeCharacterInfo() {}
        virtual bool initTitlesManager() {}
        virtual void cmChatCreate(()) {}
        /*! connects to CmChat */
        virtual void cmChatConnect(()) {}
        virtual bool cmChatExist(()) {}
        /*! return true if connection with IRC server exists. */
        virtual bool cmChatOnline(()) {}
        /*! joins channel in CmChat */
        virtual void cmChatJoin(( String channel )) {}
        /*! sends a message to CmChat */
        virtual bool cmChatCommand(( String channel, String message )) {}
        /*! receives a local chat message */
        virtual void clientCmdLocalChatMessage(( String nickFrom1, Point3F point, String message )) {}
        virtual void onChatMessage(( String message, String voice, String pitch )) {}
        virtual void cmChat_onServerMessage(( String message )) {}
        virtual void cmChatShutdown(( String quitMessage )) {}
        virtual void cmChatLoadPropertyXml(( string filename )) {}
        virtual bool cmChatSavePropertyXml(( string filename )) {}
        virtual void cmSystemChatCommand(( String message )) {}
        virtual void CraftworkBrewingTankOptionsOk() {}
        virtual bool crAddFieldToReport(( String fieldName, String fieldValue )) {}
        virtual void CloseBuildPosition() {}
        virtual void SendBuildObject() {}
        virtual void CloseDropPosition() {}
        virtual void SendDropObject() {}
        virtual void clearBuildParams() {}
        virtual void BuildSelection_Close(()) {}
        virtual void BuildSelection_SelectSubcategory(( int abilityId, int parentObjectId )) {}
        virtual void BuildSelection_SelectListItem(( int recipeId )) {}
        virtual void BuildSelection_OnBuildClicked(( int recipeId )) {}
        virtual void CloseSiegePosition() {}
        virtual void SiegePositionDone() {}
        virtual void CloseObserve() {}
        virtual void toggleObserve() {}
        virtual void clearObserve() {}
        virtual void CloseResizeClaim(()) {}
        virtual void ApplyResizeClaim(()) {}
        virtual void initCustomisationManager() {}
        virtual void removeCustomisationManager() {}
        virtual void BodyFeaturesChangePressed() {}
        virtual int GetNumberOfBodyFeatures() {}
        virtual void FacialFeaturesChangePressed() {}
        virtual int GetNumberOfFacialFeatures() {}
        virtual void BeardChangePressed() {}
        virtual int GetNumberOfFacialHairs() {}
        virtual void GenderMalePressed() {}
        virtual void GenderFemalePressed() {}
        virtual int GetCurrentGender() {}
        virtual void HairColorChangePressed() {}
        virtual int GetNumberOfHairColors() {}
        virtual void HairChangePressed() {}
        virtual int GetNumberOfHaircuts() {}
        virtual void HeadChangePressed() {}
        virtual int GetNumberOfHeads() {}
        virtual void RandomAppearancePressed() {}
        virtual void RaceChangePressed() {}
        virtual string GetRace(()) {}
        virtual void SkinColorChangePressed() {}
        virtual int GetNumberOfSkinColors() {}
        virtual void VoiceChangePressed() {}
        virtual int GetNumberOfVoices() {}
        virtual void removeClientEquipmentSingleton() {}
        virtual void removeClientComplexObjectManager() {}
        /*! initial load of guilds */
        virtual void initLoadGuildsClient(()) {}
        /*! reset guilds upon disconnect */
        virtual void resetGuilds(()) {}
        virtual void initMixingManager() {}
        virtual void removeMixingManager() {}
        virtual bool isClientInventoryInitialized() {}
        virtual void loadInventoryPos() {}
        virtual void applySplitStackItem() {}
        virtual void cancelSplitStackItem() {}
        virtual void ShowHideInventory() {}
        virtual void showInventoryWnd() {}
        virtual bool CloseInventory() {}
        virtual bool IsJHActive(()) {}
        virtual void clearJudgementHourStatus() {}
        virtual void initLoadClaimRules() {}
        virtual void resetClaims() {}
        virtual void DebugPrintClaims(( bool includeUnmovableObjects=false )) {}
        virtual void setShowClaimsMode(( String input )) {}
        /*! initial load of lands DB */
        virtual void createLandsManager(()) {}
        /*! reset lands on disconnect */
        virtual void resetLands(()) {}
        /*! redraw guild lands - debug function */
        virtual void redrawLands(()) {}
        virtual void printBattleZones(()) {}
        virtual void recalcLands(()) {}
        virtual void DebugPrintLands(()) {}
        virtual void commandToServer() {}
        virtual void commandToPeer() {}
        virtual void removeTaggedString() {}
        virtual string addTaggedString() {}
        virtual string getTaggedString() {}
        virtual string buildTaggedString() {}
        virtual void queryLanServers() {}
        virtual void querySingleServer() {}
        virtual void cancelServerQuery() {}
        virtual void stopServerQuery() {}
        virtual int getServerCount() {}
        virtual bool setServerInfo() {}
        virtual void behaviorStart(()) {}
        virtual void behaviorGoToPosition(()) {}
        virtual void behaviorWait(( int milliseconds )) {}
        virtual void behaviorAnimation(( int animNum )) {}
        virtual void behaviorEnd(()) {}
        virtual void behaviorSaveAndSend(( string clientPath, string serverPath )) {}
        virtual void OpenGameSettings() {}
        virtual void applyGameSettingsLanguageChanged() {}
        /*! BtnUnlock() */
        virtual void BtnUnlock(()) {}
        /*! SureDoneBind() */
        virtual void SureDoneBind(()) {}
        /*! DoneBind(device, action) */
        virtual void DoneBind(( string deviceRawStr, string actionRawStr )) {}
        /*! FireBind(function, buttonName) */
        virtual void FireBind(( String function, String buttonName )) {}
        /*! OpenOptionsControls() */
        virtual void OpenOptionsControls(()) {}
        /*! ProcessBindQueue() */
        virtual void ProcessBindQueue(()) {}
        /*! reloadHUDPreset() */
        virtual void reloadHUDPreset(()) {}
        /*! reloadHotBarPreset() */
        virtual void reloadHotBarPreset(()) {}
        /*! checkPresetName(name) */
        virtual bool checkPresetName(( string name )) {}
        /*! addDeletePreset(name_preset, name_menu) */
        virtual void addDeletePreset(( String namePreset, String nameMenu )) {}
        /*! addResetPreset(name_preset, name_menu) */
        virtual void addResetPreset(( String namePreset, String nameMenu )) {}
        /*! addNewHUDPreset(dialog, name_preset) */
        virtual void addNewHUDPreset(( GuiControl , String namePreset )) {}
        /*! addNewHotBarPreset(dialog, name_preset) */
        virtual void addNewHotBarPreset(( GuiControl , String namePreset )) {}
        /*! addSetDefaultHUDPreset(name_preset) */
        virtual void addSetDefaultHUDPreset(( String namePreset )) {}
        /*! addSetDefaultHotBarPreset(name_preset) */
        virtual void addSetDefaultHotBarPreset(( String namePreset )) {}
        /*! addRenamePreset(new_name_preset, name_preset, name_menu) */
        virtual void addRenamePreset(( String newNamePreset, String namePreset, String nameMenu )) {}
        /*! applyPresetActions() */
        virtual void applyPresetActions(()) {}
        /*! CloseOptionsControlsDlg() */
        virtual void CloseOptionsControlsDlg(()) {}
        virtual void CloseOutpostDialog(()) {}
        virtual bool canShowPromoBanner(()) {}
        virtual void updateLastShowPromoBannerTime(()) {}
        virtual bool isPromoActive(()) {}
        virtual void FerrymanSelectionDialogAnswer(( string serverIDStr )) {}
        virtual void FerrymanSendRequestWorldsInfo(()) {}
        virtual void QuestAnswerPressed(( int questSubjectId, int answerId )) {}
        virtual void SetActiveTask(( int questId, int questTaskId, int isOn )) {}
        virtual bool initSkillsManager() {}
        virtual void clearSkillsManager() {}
        virtual string getSkillName() {}
        virtual int getFirstBaseSkill() {}
        virtual int getChildCount() {}
        virtual int getChildSkill() {}
        virtual int getNextBaseSkill() {}
        virtual int getFirstSecondSkill() {}
        virtual int getNextSecondSkill() {}
        virtual void getUpdateSkillcap() {}
        virtual bool isNewComplexObjectNameValid(( String name )) {}
        virtual void renameComplexObjectDone(( GuiMessageBoxInputText renameDialog, String name )) {}
        /*! reload gathering info */
        virtual void reloadGatheringInfo(()) {}
        virtual void cleanupGatherables() {}
        virtual bool checkSittingAndLayingState() {}
        virtual void RenameYesCallback(( GuiControl renameDialog, String name )) {}
        virtual void RenameNoCallback() {}
        virtual void prospectingRadiusSelected(( int radius )) {}
        virtual void prospectingRadiusReset() {}
        virtual bool IsPerformingAbility() {}
        virtual void CancelPerformingAbility() {}
        virtual void clearPerformingAbilityInfo() {}
        virtual bool SkinsLoadAvailable(( int slotId=0 )) {}
        virtual void SkinsSelectSkin(( int slotId, int skinId )) {}
        virtual void SkinsApplySkin(( int slotId, int skinId )) {}
        virtual void SkinsReset(()) {}
        virtual void initSkinManager(()) {}
        /*! Executes the given slash-command */
        virtual void doSlashCommand(( string command )) {}
        virtual void startTimeLapse(()) {}
        virtual void stopTimeLapse(()) {}
        virtual void statusTimeLapse(()) {}
        virtual void onInitClientDone(()) {}
        virtual void saveRecordPointsToXml(( string filePath, Point3F centerPoint, ArrayObject points )) {}
        virtual void movePlayerToRecordPoint(( Point3F centerPoint, Point3F recordPoint, Point3F cameraRotation )) {}
        virtual void timeLapseAddKnot(()) {}
        virtual string timeLapsePositionOnSpline(( float splineParam )) {}
        virtual string timeLapseRotationOnSpline(( float splineParam )) {}
        virtual void timeLapseClearKnots(()) {}
        virtual int timeLapseGetSplineKnotsCount(()) {}
        virtual void startTutorial(()) {}
        virtual void onCloseTutorialSimpleHint(()) {}
        virtual void onCloseTutorialInfoHint(()) {}
        virtual void resetTutorialProgress(()) {}
        /*! show tutorial */
        virtual void tutorialShowSection(()) {}
        virtual void initHelpWindow(()) {}
        virtual void showTutorialInfoHint(( string infoHintName )) {}
        virtual string getHorseDataByItemTypeId(( int objectTypeId )) {}
        virtual bool isXsollaAvaliable(()) {}
        virtual string testJavaScriptBridge() {}
        virtual string TestFunction2Args() {}
        virtual void cls() {}
        virtual string getClipboard() {}
        virtual bool setClipboard() {}
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
        /*! Compares two strings using case-<b>sensitive</b> comparison.
    @param str1 The first string.
    @param str2 The second string.
    @return 0 if both strings are equal, a value <0 if the first character different in str1 has a smaller character code value than the character at the same position in str2, and a value >1 otherwise.
    
    @tsexample
    if( strcmp( %var, "foobar" ) == 0 )
       echo( "%var is equal to 'foobar'" );
    @endtsexample
    @see stricmp
    @see strnatcmp
    @ingroup Strings */
        virtual int strcmp(( string str1, string str2 )) {}
        /*! Compares two strings using case-<b>insensitive</b> comparison.
    @param str1 The first string.
    @param str2 The second string.
    @return 0 if both strings are equal, a value <0 if the first character different in str1 has a smaller character code value than the character at the same position in str2, and a value >0 otherwise.
    
    @tsexample
    if( stricmp( "FOObar", "foobar" ) == 0 )
       echo( "this is always true" );
    @endtsexample
    @see strcmp
    @see strinatcmp
    @ingroup Strings */
        virtual int stricmp(( string str1, string str2 )) {}
        /*! Compares two strings using "natural order" case-<b>sensitive</b> comparison.
    Natural order means that rather than solely comparing single character code values, strings are ordered in a natural way.  For example, the string "hello10" is considered greater than the string "hello2" even though the first numeric character in "hello10" actually has a smaller character value than the corresponding character in "hello2".  However, since 10 is greater than 2, strnatcmp will put "hello10" after "hello2".
    @param str1 The first string.
    @param str2 The second string.
    
    @return 0 if the strings are equal, a value >0 if @a str1 comes after @a str2 in a natural order, and a value <0 if @a str1 comes before @a str2 in a natural order.
    
    @tsexample
    // Bubble sort 10 elements of %array using natural order
    do
    {
       %swapped = false;
       for( %i = 0; %i < 10 - 1; %i ++ )
          if( strnatcmp( %array[ %i ], %array[ %i + 1 ] ) > 0 )
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
        /*! Compares two strings using "natural order" case-<b>insensitive</b> comparison.
    Natural order means that rather than solely comparing single character code values, strings are ordered in a natural way.  For example, the string "hello10" is considered greater than the string "hello2" even though the first numeric character in "hello10" actually has a smaller character value than the corresponding character in "hello2".  However, since 10 is greater than 2, strnatcmp will put "hello10" after "hello2".
    @param str1 The first string.
    @param str2 The second string.
    @return 0 if the strings are equal, a value >0 if @a str1 comes after @a str2 in a natural order, and a value <0 if @a str1 comes before @a str2 in a natural order.
    
    @tsexample
    
    // Bubble sort 10 elements of %array using natural order
    do
    {
       %swapped = false;
       for( %i = 0; %i < 10 - 1; %i ++ )
          if( strnatcmp( %array[ %i ], %array[ %i + 1 ] ) > 0 )
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
    @note This does <b>not</b> return a true character count for strings with multi-byte characters!
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
    
    Prints a string of the form "<variableName> = <variable value>" to the console.
    
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
        /*! Display a startup splash window suitable for showing while the engine still starts up.
    
    @note This is currently only implemented on Windows.
    
    @return True if the splash window could be successfully initialized.
    
    @ingroup Platform */
        virtual bool displaySplashWindow(()) {}
        /*! Returns true if the splash window is currently active.
    
    @note This is currently only implemented on Windows.
    
    @return True if the splash window is active and visible.
    
    @ingroup Platform */
        virtual bool isSplashWindowActive(()) {}
        /*! Close and remove splash window.
    
    @note This is currently only implemented on Windows.
    
    @ingroup Platform */
        virtual void closeSplashWindow(()) {}
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
        virtual void clientCmdNetDebugSessionStart(( string val )) {}
        virtual void globalStartNetDebug(( string sessionName )) {}
        /*! @brief Dumps network statistics for each class to the console.
    
    @note This method only works when TORQUE_NET_STATS is defined in torqueConfig.h.
    @ingroup Networking
     */
        virtual void dumpNetStats(()) {}
        virtual void debugNetEnd(()) {}
        virtual void clientCmdNetDebugSessionStop(()) {}
        virtual void globalStopNetDebug(()) {}
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
        virtual bool savePropertyXml(( SimObject object, string filename )) {}
        virtual bool loadPropertyXml(( SimObject object, string filename )) {}
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
        virtual void AbilityWidgetRun(( bool showMenu )) {}
        virtual bool ContextMenuClose(()) {}
        virtual void ContextMenuScroll(()) {}
        virtual void ShowSubContextMenu(( string group, GuiControl ctrl )) {}
        virtual void closeSubContextMenu(()) {}
        virtual void SelectionHighlight() {}
        virtual bool isInSelectionHighlightMode() {}
        virtual void DNetSetLogging() {}
        virtual void setGameTimeScale() {}
        virtual float getGameTimeScale() {}
        virtual void setGameDayTime(( int secondsSinceMidnight )) {}
        virtual void midnight(()) {}
        virtual void morning(()) {}
        virtual void noon(()) {}
        virtual void evening(()) {}
        virtual string getGameTime(()) {}
        virtual void Forest_TestFindTree(( int valForestKey )) {}
        /*! Populate the font cache for the specified font with characters from the specified string.
    @param faceName The name of the font face.
    @param fontSize The size of the font in pixels.
    @param string The string to populate.
    @ingroup Font
     */
        virtual void populateFontCacheString(( string faceName, int fontSize, string string )) {}
        /*! Populate the font cache for the specified font with Unicode code points in the specified range.
    @param faceName The name of the font face.
    @param fontSize The size of the font in pixels.
    @param rangeStart The start Unicode point.
    @param rangeEnd The end Unicode point.
    @note We only support BMP-0, so code points range from 0 to 65535.
    @ingroup Font
     */
        virtual void populateFontCacheRange(( string faceName, int fontSize, int rangeStart, int rangeEnd )) {}
        /*! Dumps to the console a full description of all cached fonts, along with info on the codepoints each contains.
    @ingroup Font
     */
        virtual void dumpFontCacheStatus(()) {}
        /*! Force all cached fonts to serialize themselves to the cache.
    @ingroup Font
     */
        virtual void writeFontCache(()) {}
        /*! Populate the font cache for all fonts with characters from the specified string.
    @ingroup Font
     */
        virtual void populateAllFontCacheString(( string string )) {}
        /*! Populate the font cache for all fonts with Unicode code points in the specified range.
    @param rangeStart The start Unicode point.
    @param rangeEnd The end Unicode point.
    @note We only support BMP-0, so code points range from 0 to 65535.
    @ingroup Font
     */
        virtual void populateAllFontCacheRange(( int rangeStart, int rangeEnd )) {}
        /*! Export specified font to the specified filename as a PNG. The image can then be processed in Photoshop or another tool and reimported using importCachedFont. Characters in the font are exported as one long strip.
    @param faceName The name of the font face.
    @param fontSize The size of the font in pixels.
    @param fileName The file name and path for the output PNG.
    @param padding The padding between characters.
    @param kerning The kerning between characters.
    @ingroup Font
     */
        virtual void exportCachedFont(( string faceName, int fontSize, string fileName, int padding, int kerning )) {}
        /*! Import an image strip from exportCachedFont. Call with the same parameters you called exportCachedFont.
    @param faceName The name of the font face.
    @param fontSize The size of the font in pixels.
    @param fileName The file name and path for the input PNG.
    @param padding The padding between characters.
    @param kerning The kerning between characters.
    @ingroup Font
     */
        virtual void importCachedFont(( string faceName, int fontSize, string fileName, int padding, int kerning )) {}
        /*! Copy the specified old font to a new name. The new copy will not have a platform font backing it, and so will never have characters added to it. But this is useful for making copies of fonts to add postprocessing effects to via exportCachedFont.
    @param oldFontName The name of the font face to copy.
    @param oldFontSize The size of the font to copy.
    @param newFontName The name of the new font face.
    @ingroup Font
     */
        virtual void duplicateCachedFont(( string oldFontName, int oldFontSize, string newFontName )) {}
        virtual void registerFont(( string fontName )) {}
        /*! Returns a tab-seperated string of the detected devices across all adapters.
    @ingroup GFX
     */
        virtual string getDisplayDeviceList(()) {}
        /*! Returns a list of the unflagged GFX resources. See flagCurrentGFXResources for usage details.
    @ingroup GFX
    @see flagCurrentGFXResources, clearGFXResourceFlags, describeGFXResources */
        virtual void listGFXResources(( bool unflaggedOnly=false )) {}
        /*! @brief Flags all currently allocated GFX resources.
    Used for resource allocation and leak tracking by flagging current resources then dumping a list of unflagged resources at some later point in execution.
    @ingroup GFX
    @see listGFXResources, clearGFXResourceFlags, describeGFXResources */
        virtual void flagCurrentGFXResources(()) {}
        /*! Clears the flagged state on all allocated GFX resources. See flagCurrentGFXResources for usage details.
    @ingroup GFX
    @see flagCurrentGFXResources, listGFXResources, describeGFXResources */
        virtual void clearGFXResourceFlags(()) {}
        /*! @brief Dumps a description of GFX resources to a file or the console.
    @param resourceTypes A space seperated list of resource types or an empty string for all resources.
    @param filePath A file to dump the list to or an empty string to write to the console.
    @param unflaggedOnly If true only unflagged resources are dumped. See flagCurrentGFXResources.
    @note The resource types can be one or more of the following:
    
      - texture
      - texture target
      - window target
      - vertex buffers
      - primitive buffers
      - fences
      - cubemaps
      - shaders
      - stateblocks
    
    @ingroup GFX
     */
        virtual void describeGFXResources(( string resourceTypes, string filePath, bool unflaggedOnly=false )) {}
        /*! Dumps a description of all state blocks.
    @param filePath A file to dump the state blocks to or an empty string to write to the console.
    @ingroup GFX
     */
        virtual void describeGFXStateBlocks(( string filePath )) {}
        /*! Returns the pixel shader version for the active device.
    @ingroup GFX
     */
        virtual float getPixelShaderVersion(()) {}
        /*! @brief Sets the pixel shader version for the active device.
    This can be used to force a lower pixel shader version than is supported by the device for testing or performance optimization.
    @param version The floating point shader version number.
    @note This will only affect shaders/materials created after the call and should be used before the game begins.
    @see $pref::Video::forcedPixVersion
    @ingroup GFX
     */
        virtual void setPixelShaderVersion(( float version )) {}
        /*! Get the string describing the active GFX device.
    @ingroup GFX
     */
        virtual string getDisplayDeviceInformation(()) {}
        /*! Returns the best texture format for storage of HDR data for the active device.
    @ingroup GFX
     */
        virtual string getBestHDRFormat(()) {}
        /*! Get the maximum level of anisotropic filtering supportrf by current GFX device.
    @ingroup GFX
     */
        virtual int getMaxAnisotropy(()) {}
        /*! Returns the width, height, and bitdepth of the screen/desktop.
    
    @ingroup GFX */
        virtual string getDesktopResolution(()) {}
        virtual void rebakeTerrainAtlases() {}
        virtual void seasonsBakeImposter() {}
        virtual void seasonsSetMonth() {}
        virtual void seasonsForcedSetMonth() {}
        virtual int getCurrentSeasonNum() {}
        virtual void reloadAllShaders(()) {}
        virtual void reloadShader(( string name=NULL )) {}
        virtual void reloadWater(()) {}
        virtual void reloadRTW(()) {}
        virtual void reloadTerrain(()) {}
        /*! Adds a global shader macro which will be merged with the script defined macros on every shader.  The macro will replace the value of an existing macro of the same name.  For the new macro to take effect all the shaders in the system need to be reloaded.
    @see resetLightManager, removeGlobalShaderMacro
    @ingroup Rendering
     */
        virtual void addGlobalShaderMacro(( string name, string value=NULL )) {}
        /*! Removes an existing global macro by name.
    @see addGlobalShaderMacro
    @ingroup Rendering
     */
        virtual void removeGlobalShaderMacro(( string name )) {}
        virtual void triggerTextureMemoryWarning() {}
        virtual void reloadStreamableTextures() {}
        virtual void triggerTextureOutOfMemoryError() {}
        virtual void setAvalableTextureMemory() {}
        /*! Releases all textures and resurrects the texture manager.
    @ingroup GFX
     */
        virtual void flushTextureCache(()) {}
        /*! Release the unused pooled textures in texture manager freeing up video memory.
    @ingroup GFX
     */
        virtual void cleanupTexturePool(()) {}
        /*! Reload all the textures from disk.
    @ingroup GFX
     */
        virtual void reloadTextures(()) {}
        /*! Dump the textures from disk.
    @ingroup GFX
     */
        virtual void dumpTextures(()) {}
        /*! Returns a list of texture profiles in the format: ProfileName TextureCount TextureMB
    @ingroup GFX
     */
        virtual string getTextureProfileStats(()) {}
        virtual void printTextureProfileStats() {}
        /*! Takes a screenshot with optional tiling to produce huge screenshots.
    @param file The output image file path.
    @param format Either JPEG or PNG.
    @param tileCount If greater than 1 will tile the current screen size to take a large format screenshot.
    @param tileOverlap The amount of horizontal and vertical overlap between the tiles used to remove tile edge artifacts from post effects.
    @ingroup GFX
     */
        virtual void screenShot(( string file, string format, int tileCount=1, float tileOverlap=0, bool hudless=false )) {}
        /*! Returns the count of active DDSs files in memory.
    @ingroup Rendering
     */
        virtual int getActiveDDSFiles(()) {}
        /*! Returns image info in the following format: width TAB height TAB bytesPerPixel. It will return an empty string if the file is not found.
    @ingroup Rendering
     */
        virtual string getBitmapInfo(( string filename )) {}
        virtual void profileCameraInit() {}
        virtual void profileCameraSavePosition() {}
        virtual void profileCameraResetPosition() {}
        virtual void profileCameraStart() {}
        /*! Begins a video capture session.
    @see stopVideoCapture
    @ingroup Rendering
     */
        virtual void startVideoCapture(( GuiCanvas canvas, string filename, string encoder="THEORA", float framerate=30.0f, Point2I resolution=Point2I(0, 0) )) {}
        /*! Stops the video capture session.
    @see startVideoCapture
    @ingroup Rendering
     */
        virtual void stopVideoCapture(()) {}
        /*! Load a journal file and capture it video.
    @ingroup Rendering
     */
        virtual void playJournalToVideo(( string journalFile, string videoFile=NULL, string encoder="THEORA", float framerate=30.0f, Point2I resolution=Point2I(0, 0) )) {}
        virtual void cmHotBarLoadPropertyXml(( string filename )) {}
        virtual void cmHotBarLoadDataXml(( string filename )) {}
        virtual void cmHotBarSavePropertyXml(( string filename )) {}
        virtual void cmHotBarSaveDataXml(( string filename )) {}
        virtual void HB_SlotActivate(( int tabId, int slotId, bool pressed )) {}
        virtual void clearHotBars() {}
        virtual void dumpAtlas(()) {}
        virtual void addGlobalImageAtlas(( String atlasFileName, AtlasParserNamespace::BitmapIndicesEnum elementCount )) {}
        virtual void clearGlobalImageAtlas(()) {}
        virtual int getMessageBtnClose(()) {}
        virtual int getEscMenuButton(( int btn_idx )) {}
        virtual int getOptionsVideoButton(()) {}
        virtual int getOptionsBottomBorder(()) {}
        virtual int getEmptyUnflattenedTilesIcon() {}
        virtual int getEmptyFlattenedTilesIcon() {}
        virtual int getBlockedTilesIcon() {}
        virtual int getAltitudeAboveTileIcon() {}
        virtual int getTileIconClaimWhite() {}
        virtual int getTileIconClaimGray() {}
        virtual int getTileIconClaimDarkGreen() {}
        virtual int getTileIconClaimGreen() {}
        virtual int getTileIconClaimRed() {}
        virtual int getOptionsTopBorder(()) {}
        virtual int getCombatGnomeStartCooldown(()) {}
        virtual int getCombatGnomeEndCooldown(()) {}
        virtual int getBtnGreenhouseNormal(()) {}
        virtual int getBackgroundEmblem(()) {}
        virtual int getBtnPositionSymbol(()) {}
        virtual int getShadowPreview(()) {}
        virtual int getBackgroundPreview(()) {}
        virtual int getEmblemColorChervlenNormal(()) {}
        virtual int getEmblemColorChervlenMouseOver(()) {}
        virtual int getEmblemColorGoldNormal(()) {}
        virtual int getEmblemColorGoldMouseOver(()) {}
        virtual int getEmblemColorGreenNormal(()) {}
        virtual int getEmblemColorGreenMouseOver(()) {}
        virtual int getEmblemColorBlackNormal(()) {}
        virtual int getEmblemColorBlackMouseOver(()) {}
        virtual int getEmblemColorPurpleNormal(()) {}
        virtual int getEmblemColorPurpleMouseOver(()) {}
        virtual int getEmblemColorOrangeNormal(()) {}
        virtual int getEmblemColorOrangeMouseOver(()) {}
        virtual int getEmblemColorAzureNormal(()) {}
        virtual int getEmblemColorAzureMouseOver(()) {}
        virtual int getEmblemColorSilverNormal(()) {}
        virtual int getEmblemColorSilverMouseOver(()) {}
        virtual int getEmblemColorBlackChervlenNormal(()) {}
        virtual int getEmblemColorBlackChervlenMouseOver(()) {}
        virtual int getEmblemColorBlackOrangeNormal(()) {}
        virtual int getEmblemColorBlackOrangeMouseOver(()) {}
        virtual int getEmblemColorBlackGoldNormal(()) {}
        virtual int getEmblemColorBlackGoldMouseOver(()) {}
        virtual int getEmblemColorBlackGreenNormal(()) {}
        virtual int getEmblemColorBlackGreenMouseOver(()) {}
        virtual int getEmblemColorBlackAzureNormal(()) {}
        virtual int getEmblemColorBlackAzureMouseOver(()) {}
        virtual int getEmblemColorBlackPurpleNormal(()) {}
        virtual int getEmblemColorBlackPurpleMouseOver(()) {}
        virtual int getEmblemColorBlackBlackNormal(()) {}
        virtual int getEmblemColorBlackBlackMouseOver(()) {}
        virtual int getEmblemColorBlackSilverNormal(()) {}
        virtual int getEmblemColorBlackSilverMouseOver(()) {}
        virtual int getEmblemColorSelected(()) {}
        virtual int getBtnSymbolSizeSmall(()) {}
        virtual int getBtnSymbolSizeMedium(()) {}
        virtual int getBtnSymbolSizeLarge(()) {}
        virtual int getBorderSymbolSelected(()) {}
        virtual int getShadowBackground(()) {}
        virtual int getShadowBackgroundMouseOver(()) {}
        virtual int getShadowSymbol(()) {}
        virtual int getShadowSymbolMouseOver(()) {}
        virtual int getRelatedBackgroundIcon(()) {}
        virtual int getContrastingBackgroundIcon(()) {}
        virtual int getSymbolLargeIcon(()) {}
        virtual int getMessageBoxPasswordDlgButtonIndex(()) {}
        virtual int getMessageBoxPasswordDlgCheckBoxStateOn(()) {}
        virtual int getMessageBoxPasswordDlgCheckBoxStateOff(()) {}
        virtual int getMessageBoxPasswordDlgTextEditLeft(()) {}
        virtual int getMessageBoxPasswordDlgTextEditRight(()) {}
        virtual int getMessageBoxPasswordDlgTextEditBackground(()) {}
        virtual int getSkillStatBtnPanel(()) {}
        virtual int getSkillBtnIcon(()) {}
        virtual int getStatBtnIcon(()) {}
        virtual int getGuildBtnIcon(()) {}
        virtual int getCraftSkill(()) {}
        virtual int getCombatSkill(()) {}
        virtual int getMinorSkill(()) {}
        virtual int getSelectSkill(()) {}
        virtual int getSkillItemActiveBorder(()) {}
        virtual int getSkillBtnStatus(()) {}
        virtual int getCharacterStatusBorder(()) {}
        virtual int getGuildNameBorder(()) {}
        virtual int getGuildEditNameBorder(()) {}
        virtual int getHungerPanel(()) {}
        virtual int getHealthPanel(()) {}
        virtual int getLvlPanel(()) {}
        virtual int getSkillcapBar(()) {}
        virtual int getSkillDescriptionDecorLine(()) {}
        virtual int getSkillLine(()) {}
        virtual void changeStrengthLock() {}
        virtual void changeAgilityLock() {}
        virtual void changeWillpowerLock() {}
        virtual void changeIntellectLock() {}
        virtual void changeConstitutionLock() {}
        virtual string CmGuiChatSelectedWindow(()) {}
        virtual void activateCmChat(()) {}
        virtual void clearChatWindows() {}
        virtual void CloseSelectionList() {}
        virtual void SelectionListSelect() {}
        /*! @brief Strip TorqueML control characters from the specified string, returning a 'clean' version.
    
    @param inString String to strip TorqueML control characters from.
    @tsexample
    // Define the string to strip TorqueML control characters from
    %string = "<font:Arial:24>How Now <color:c43c12>Brown <color:000000>Cow";
    
    // Request the stripped version of the string
    %strippedString = StripMLControlChars(%string);
    @endtsexample
    
    @return Version of the inputted string with all TorqueML characters removed.
    
    @see References
    
    @ingroup GuiCore */
        virtual string StripMLControlChars(( string inString )) {}
        /*! @brief Used to exclude/prevent all other instances using the same identifier specified
    
    @note Not used on OSX, Xbox, or in Win debug builds
    
    @param appIdentifier Name of the app set up for exclusive use.
    @return False if another app is running that specified the same appIdentifier
    
    @ingroup Platform
    @ingroup GuiCore */
        virtual bool excludeOtherInstance(( string appIdentifer )) {}
        virtual bool isCanvasFocused(()) {}
        virtual void setCmFreelookMode(( bool freelookMode, bool ignorCounter )) {}
        virtual bool getCmFreelookMode() {}
        virtual void setCmEditGuiMode() {}
        virtual void toggleConsole() {}
        virtual void overridePlatformCursor() {}
        virtual void showCursor() {}
        virtual void hideCursor() {}
        virtual void setClearMode() {}
        virtual void addClearModeWindow() {}
        virtual void CloseAcceptDlg() {}
        virtual void normalCloseAcceptDlg() {}
        virtual void CheckboxClicked() {}
        virtual void AcceptSentence() {}
        virtual void OpenAcceptDlg(( string filename, string header, string checkBoxText, string callback )) {}
        virtual void debugShowSpecAttack() {}
        virtual void updateGmIndication() {}
        virtual int getComboWindowStartCooldown() {}
        virtual int getComboWindowEndCooldown() {}
        virtual void CraftOptionsClose() {}
        virtual void CraftOptionsSelect1() {}
        virtual void CraftOptionsSelect2() {}
        virtual void CraftOptionsSelect3() {}
        virtual void CraftOptionsSelect4() {}
        virtual void startLocalWorld(()) {}
        virtual int getCreateWorldWindowBackground() {}
        virtual int getCreateWorldWindowBigCheckBox() {}
        virtual int getCreateWorldWindowSmallCheckBox() {}
        virtual int getCreateWorldWindowSplitter() {}
        virtual int getCreatedWorldListSplitter() {}
        virtual int getCreateWorldButtonWorldInfo() {}
        virtual int getJoinWorldWindowBackground() {}
        virtual string getServerListTabButtonNormal(()) {}
        virtual string getServerListTabButtonDepressed(()) {}
        virtual string getServerListTabButtonMouseOver(()) {}
        virtual int getServerListSortButtonBorder() {}
        virtual int getServerListLockedIcon() {}
        virtual int getServerListTopBorder() {}
        virtual int getServerListBottomBorder() {}
        virtual int getServerListMainInfoBackground() {}
        virtual int getServerListAdditionalInfoBackground1() {}
        virtual int getServerListAdditionalInfoBackground2() {}
        virtual string getServerListButtonNormalIndexes(()) {}
        virtual string getServerListButtonMouseOverIndexes(()) {}
        virtual string getServerListButtonDepressedIndexes(()) {}
        virtual int getServerListCheckBoxStateOn() {}
        virtual int getServerListCheckBoxStateOff() {}
        virtual int getSortAscendingIcon() {}
        virtual int getSortDescendingIcon() {}
        virtual int getServerListBackground() {}
        virtual string getServerListItemMouseOver(()) {}
        virtual string getServerListItemSelected(()) {}
        virtual void cmShowMainMenuMultiplayerWindow() {}
        virtual void cmBreakIntroVideo() {}
        virtual int getMainMenuWindowBackground() {}
        virtual void openOptionsPlayers(()) {}
        virtual void closeOptionsPlayers(()) {}
        virtual void openPlayersAccount(( int charID )) {}
        virtual void kickPlayer(( int charID )) {}
        virtual void banPlayer(( int charID )) {}
        virtual void invitePlayer(( int charId )) {}
        virtual string getGuildHeraldryCooldown(()) {}
        virtual void alchemyCraftButtonClick(()) {}
        virtual int getBarterWindowWorkAreaSplitter() {}
        virtual bool CreateCraftToolWindow(()) {}
        virtual void guiGreenhouseButtonClick(()) {}
        virtual void testSmelting() {}
        virtual int getTrebuchetAngleAttackBackground() {}
        virtual int getTrebuchetAngleAttackSlider() {}
        virtual int getTrebuchetAngleAttackRotationCenter() {}
        virtual int getTrebuchetFireButton() {}
        virtual void initTooltipTemplateManager() {}
        virtual void removeTooltipTemplateManager() {}
        virtual void addTooltipTemplate(( TooltipFunctionType function, int id, String metod )) {}
        virtual int getGroupWindowHardHPBar() {}
        virtual int getGroupWindowSoftHPBar() {}
        virtual int getGroupWindowHardStamBar() {}
        virtual int getGroupWindowSoftStamBar() {}
        virtual int getGroupWindowWidgetBackground() {}
        virtual int getGroupWindowWidgetLeftBorder() {}
        virtual int getGroupWindowWidgetRightBorder() {}
        virtual int getCoreLangTable() {}
        virtual void setCoreLangTable() {}
           /*! A callback called by the engine when a light manager is activated.
    @param name The name of the light manager being activated.
    @ingroup Lighting
     */
           void onLightManagerActivate( string name );
     
           /*! A callback called by the engine when a light manager is deactivated.
    @param name The name of the light manager being deactivated.
    @ingroup Lighting
     */
           void onLightManagerDeactivate( string name );
     
        /*! Finds and activates the named light manager.
    @return Returns true if the light manager is found and activated.
    @ingroup Lighting
     */
        virtual bool setLightManager(( string name )) {}
        /*! Will generate static lighting for the scene if supported by the active light manager.
    
    If mode is "forceAlways", the lightmaps will be regenerated regardless of whether lighting cache files can be written to. If mode is "forceWritable", then the lightmaps will be regenerated only if the lighting cache files can be written.
    @param completeCallbackFn The name of the function to execute when the lighting is complete.
    @param mode One of "forceAlways",  "forceWritable" or "loadOnly".
    @return Returns true if the scene lighting process was started.
    @ingroup Lighting
     */
        virtual bool lightScene(( string completeCallbackFn=NULL, string mode=NULL )) {}
        /*! Returns a tab seperated list of light manager names.
    @ingroup Lighting
     */
        virtual string getLightManagerNames(()) {}
        /*! Returns the active light manager name.
    @ingroup Lighting
     */
        virtual string getActiveLightManager(()) {}
        /*! @brief Deactivates and then activates the currently active light manager.This causes most shaders to be regenerated and is often used when global rendering changes have occured.
    @ingroup Lighting
     */
        virtual void resetLightManager(()) {}
        virtual bool setShadowManager() {}
        virtual string setShadowVizLight() {}
        virtual void reInitMaterials() {}
        virtual void addMaterialMapping() {}
        virtual string getMaterialMapping() {}
        virtual void dumpMaterialInstances() {}
        virtual string getMapEntry() {}
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
    //     a -> b = ||( b - a )||
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
        virtual void TestMarching() {}
        virtual void TestAdvancedMarching() {}
        virtual void TestSphere() {}
        virtual void TestPrism() {}
        virtual void SwitchPoints() {}
        virtual void CleanTestMarching() {}
        virtual string getTerFilePath(( int terID, string basePath=nullptr )) {}
        virtual string getTer2FilePath_Server_Index(( int terID, string basePath=nullptr )) {}
        virtual string getTer2FilePath_Server_Data(( int terID, string basePath=nullptr )) {}
        virtual string getTer2FilePath_Client_Index(( int terID, string basePath=nullptr )) {}
        virtual string getTer2FilePath_Client_Data(( int terID, string basePath=nullptr )) {}
        virtual void recreatePatcher() {}
        virtual string getServerUuid() {}
        virtual bool initPatchConnection(( TCPConnection tcp )) {}
        virtual void stopPatchConnection(( bool cleanupFileCache=true )) {}
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
        virtual bool redbookOpen() {}
        virtual bool redbookClose() {}
        virtual bool redbookPlay() {}
        virtual bool redbookStop() {}
        virtual int redbookGetTrackCount() {}
        virtual float redbookGetVolume() {}
        virtual bool redbookSetVolume() {}
        virtual int redbookGetDeviceCount() {}
        virtual string redbookGetDeviceName() {}
        virtual string redbookGetLastError() {}
        /*! Create and start a high resolution platform timer. Returns the timer id. */
        virtual int startPrecisionTimer(()) {}
        /*! Stop and destroy timer with the passed id. Returns the elapsed milliseconds. */
        virtual int stopPrecisionTimer(( int timerId )) {}
        /*! Display a modal message box using the platform's native message box implementation.
    
    @param title The title to display on the message box window.
    @param message The text message to display in the box.
    @param buttons Which buttons to put on the message box.
    @param icons Which icon to show next to the message.
    @return One of $MROK, $MRCancel, $MRRetry, and $MRDontSave identifying the button that the user pressed.
    @tsexample
    messageBox( "Error", "" );
    @endtsexample
    
    @ingroup Platform */
        virtual int messageBox(( string title, string message, MBButtons buttons=MBOkCancel, MBIcons icons=MIInformation )) {}
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
        virtual bool enableJoystick() {}
        virtual void disableJoystick() {}
        virtual bool isJoystickEnabled() {}
        virtual bool enableXInput() {}
        virtual void disableXInput() {}
        virtual void resetXInput() {}
        virtual bool isXInputConnected() {}
        virtual int getXInputState() {}
        virtual void echoInputState() {}
        virtual void rumble() {}
        virtual bool shellExecute() {}
        virtual bool isJoystickDetected() {}
        virtual string getJoystickAxes() {}
        virtual bool checkNamedPipeOpen(( String pipeName )) {}
        virtual bool isPipedStdIO(()) {}
        virtual void askToGenerateCrashReport(( int errorCodeId, String errorCodeMsg )) {}
        virtual void ping(( int level, int timestamp )) {}
        virtual void crtEnableDebug() {}
        virtual void crtCheckMemory() {}
        virtual bool isKoreanBuild() {}
        /*! Creates a 64x64 normal map texture filled with noise. The texture is saved to randNormTex.png in the location of the game executable.
    
    @ingroup GFX */
        virtual void dumpRandomNormalMap(()) {}
        virtual void reloadWeather() {}
        virtual void toggleWeather() {}
        virtual void clearServerPaths() {}
        virtual void clearClientPaths() {}
        /*! @brief See if any objects of the given types are present in box of given extent.
    
    @note Extent parameter is last since only one radius is often needed.  If one radius is provided, the yRadius and zRadius are assumed to be the same.  Unfortunately, if you need to use the client container, you'll need to set all of the radius parameters.  Fortunately, this function is mostly used on the server.
    @param  mask   Indicates the type of objects we are checking against.
    @param  center Center of box.
    @param  xRadius Search radius in the x-axis. See note above.
    @param  yRadius Search radius in the y-axis. See note above.
    @param  zRadius Search radius in the z-axis. See note above.
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return true if the box is empty, false if any object is found.
    @ingroup Game */
        virtual bool containerBoxEmpty(( int mask, Point3F center, float xRadius, float yRadius=-1, float zRadius=-1, bool useClientContainer=false )) {}
        /*! @brief Start a search for items at the given position and within the given radius, filtering by mask.
    
    @param pos Center position for the search
    @param radius Search radius
    @param mask Bitmask of object types to include in the search
    @param useClientContainer Optionally indicates the search should be within the client container.
    @see containerSearchNext
    @ingroup Game */
        virtual void initContainerRadiusSearch(( Point3F pos, float radius, int mask, bool useClientContainer=false )) {}
        /*! @brief Start a search for all items of the types specified by the bitset mask.
    
    @param mask Bitmask of object types to include in the search
    @param useClientContainer Optionally indicates the search should be within the client container.
    @see containerSearchNext
    @ingroup Game */
        virtual void initContainerTypeSearch(( int mask, bool useClientContainer=false )) {}
        /*! @brief Get next item from a search started with initContainerRadiusSearch() or initContainerTypeSearch().
    
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return the next object found in the search, or null if no more
    @tsexample
    // print the names of all nearby ShapeBase derived objects
    %position = %obj.getPosition;
    %radius = 20;
    %mask = $TypeMasks::ShapeBaseObjectType;
    initContainerRadiusSearch( %position, %radius, %mask );
    while ( (%targetObject = containerSearchNext()) != 0 )
    {
       echo( "Found: " @ %targetObject.getName() );
    }
    @endtsexample
    @see initContainerRadiusSearch()
    @see initContainerTypeSearch()
    @ingroup Game */
        virtual string containerSearchNext(( bool useClientContainer=false )) {}
        /*! @brief Get distance of the center of the current item from the center of the current initContainerRadiusSearch.
    
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return distance from the center of the current object to the center of the search
    @see containerSearchNext
    @ingroup Game */
        virtual float containerSearchCurrDist(( bool useClientContainer=false )) {}
        /*! @brief Get the distance of the closest point of the current item from the center of the current initContainerRadiusSearch.
    
    @param useClientContainer Optionally indicates the search should be within the client container.
    @return distance from the closest point of the current object to the center of the search
    @see containerSearchNext
    @ingroup Game */
        virtual float containerSearchCurrRadiusDist(( bool useClientContainer=false )) {}
        virtual void listObjects(()) {}
        /*! @brief Cast a ray from start to end, checking for collision against items matching mask.
    
    If pExempt is specified, then it is temporarily excluded from collision checks (For instance, you might want to exclude the player if said player was firing a weapon.)
    @param start An XYZ vector containing the tail position of the ray.
    @param end An XYZ vector containing the head position of the ray
    @param mask A bitmask corresponding to the type of objects to check for
    @param pExempt An optional ID for a single object that ignored for this raycast
    @param useClientContainer Optionally indicates the search should be within the client container.
    @returns A string containing either null, if nothing was struck, or these fields:
    <ul><li>The ID of the object that was struck.</li><li>The x, y, z position that it was struck.</li><li>The x, y, z of the normal of the face that was struck.</li></ul>@ingroup Game */
        virtual string containerRayCast(( Point3F start, Point3F end, int mask, SceneObject pExempt=NULL, bool useClientContainer=false )) {}
        virtual void reloadOcclusionCulling() {}
        virtual void DbgSetVisibleDistance(( float dist=500 )) {}
        virtual int getCentralTerrain(()) {}
        virtual int getServerCentralTerrain(()) {}
        virtual void shiftWorld(( Point2F offset )) {}
        /*! @brief Load all path information from interiors.
    
    This function is usually called from the loadMissionStage2() server-side function after the mission file has loaded.
    
    @tsexample
    // Inform the engine to load all path information from interiors.
    pathOnMissionLoadDone();
    
    @endtsexample
    @ingroup Game */
        virtual void pathOnMissionLoadDone(()) {}
        /*! Return a newline-separated list of all active states.
    @return A list of the form
    @verbatim
    stateName1 NL stateName2 NL stateName3 ...
    @endverbatim
    where each element is the name of an active state object.
    
    @tsexample
    // Disable all active states.
    foreach$( %state in sfxGetActiveStates() )
       %state.disable();
    @endtsexample
    
    @ingroup SFX */
        virtual string sfxGetActiveStates(()) {}
        /*! Get a list of all available sound devices.
    The return value will be a newline-separated list of entries where each line describes one available sound device.  Each such line will have the following format:@verbatim
    provider TAB device TAB hasHardware TAB numMaxBuffers
    @endverbatim
    - provider: The name of the device provider (e.g. "FMOD").
    - device: The name of the device as returned by the device layer.
    - hasHardware: Whether the device supports hardware mixing or not.
    - numMaxBuffers: The maximum number of concurrent voices supported by the device's mixer.  If this limit limit is exceeded, i.e. if there are more active sounds playing at any one time, then voice virtualization will start culling voices and put them into virtualized playback mode.  Voice virtualization may or may not be provided by the device itself; if not provided by the device, it will be provided by Torque's sound system.
    
    @return A newline-separated list of information about all available sound devices.
    @see sfxCreateDevice
    @see sfxGetDeviceInfo
    
    @see $SFX::DEVICE_INFO_PROVIDER
    
    @see $SFX::DEVICE_INFO_NAME
    
    @see $SFX::DEVICE_INFO_USEHARDWARE
    
    @see $SFX::DEVICE_INFO_MAXBUFFERS
    
    @ref SFX_devices
    @ingroup SFX */
        virtual string sfxGetAvailableDevices(()) {}
        /*! Try to create a new sound device using the given properties.
    If a sound device is currently initialized, it will be uninitialized first.  However, be aware that in this case, if this function fails, it will not restore the previously active device but rather leave the sound system in an uninitialized state.
    
    Sounds that are already playing while the new device is created will be temporarily transitioned to virtualized playback and then resume normal playback once the device has been created.
    
    In the core scripts, sound is automatically set up during startup in the sfxStartup() function.
    
    @param provider The name of the device provider as returned by sfxGetAvailableDevices().
    @param device The name of the device as returned by sfxGetAvailableDevices().
    @param useHardware Whether to enabled hardware mixing on the device or not.  Only relevant if supported by the given device.
    @param maxBuffers The maximum number of concurrent voices for this device to use or -1 for the device to pick its own reasonable default.@return True if the initialization was successful, false if not.
    @note This function must be called before any of the sound playback functions can be used.
    @see sfxGetAvailableDevices
    @see sfxGetDeviceInfo
    @see sfxDeleteDevice
    
    @ref SFX_devices
    @ingroup SFX */
        virtual bool sfxCreateDevice(( string provider, string device, bool useHardware, int maxBuffers )) {}
        /*! Delete the currently active sound device and release all its resources.
    SFXSources that are still playing will be transitioned to virtualized playback mode. When creating a new device, they will automatically transition back to normal playback.
    
    In the core scripts, this is done automatically for you during shutdown in the sfxShutdown() function.
    
    @see sfxCreateDevice
    
    @ref SFX_devices
    @ingroup SFX */
        virtual void sfxDeleteDevice(()) {}
        /*! Return information about the currently active sound device.
    The return value is a tab-delimited string of the following format:
    @verbatim
    provider TAB device TAB hasHardware TAB numMaxBuffers TAB caps
    @endverbatim
    - provider: The name of the device provider (e.g. "FMOD").
    - device: The name of the device as returned by the device layer.
    - hasHardware: Whether the device supports hardware mixing or not.
    - numMaxBuffers: The maximum number of concurrent voices supported by the device's mixer.  If this limit limit is exceeded, i.e. if there are more active sounds playing at any one time, then voice virtualization will start culling voices and put them into virtualized playback mode.  Voice virtualization may or may not be provided by the device itself; if not provided by the device, it will be provided by Torque's sound system.
    - caps: A bitfield of capability flags.
    
    @return A tab-separated list of properties of the currently active sound device or the empty string if no sound device has been initialized.
    @see sfxCreateDevice
    @see sfxGetAvailableDevices
    
    @see $SFX::DEVICE_INFO_PROVIDER
    
    @see $SFX::DEVICE_INFO_NAME
    
    @see $SFX::DEVICE_INFO_USEHARDWARE
    
    @see $SFX::DEVICE_INFO_MAXBUFFERS
    
    @see $SFX::DEVICE_INFO_CAPS
    
    @see $SFX::DEVICE_CAPS_REVERB
    
    @see $SFX::DEVICE_CAPS_VOICEMANAGEMENT
    
    @see $SFX::DEVICE_CAPS_OCCLUSION
    
    @see $SFX::DEVICE_CAPS_DSPEFFECTS
    
    @see $SFX::DEVICE_CAPS_MULTILISTENER
    
    @see $SFX::DEVICE_CAPS_FMODDESIGNER
    
    @ref SFX_devices
    @ingroup SFX */
        virtual string sfxGetDeviceInfo(()) {}
        virtual int sfxCreateSource() {}
        virtual int sfxPlay() {}
        virtual int sfxPlayOnce() {}
        /*! Stop playback of the given @a source.
    This is equivalent to calling SFXSource::stop().
    
    @param source The source to put into stopped state.
    
    @ingroup SFX */
        virtual void sfxStop(( SFXSource source )) {}
        /*! Stop playback of the given @a source (if it is not already stopped) and delete the @a source.
    
    The advantage of this function over directly calling delete() is that it will correctly handle volume fades that may be configured on the source.  Whereas calling delete() would immediately stop playback and delete the source, this functionality will wait for the fade-out to play and only then stop the source and delete it.
    
    @param source A sound source.
    
    @ref SFXSource_fades
    
    @ingroup SFX */
        virtual void sfxStopAndDelete(( SFXSource source )) {}
        /*! Mark the given @a source for deletion as soon as it moves into stopped state.
    
    This function will retroactively turn the given @a source into a play-once source (see @ref SFXSource_playonce).
    
    @param source A sound source.
    
    @ingroup SFX */
        virtual void sfxDeleteWhenStopped(( SFXSource source )) {}
        /*! Get the falloff curve type currently being applied to 3D sounds.
    
    @return The current distance model type.
    
    @ref SFXSource_volume
    
    @ref SFX_3d
    
    @ingroup SFX */
        virtual string sfxGetDistanceModel(()) {}
        /*! Set the falloff curve type to use for distance-based volume attenuation of 3D sounds.
    
    @param model The distance model to use for 3D sound.
    
    @note This setting takes effect globally and is applied to all 3D sounds.
    
    @ingroup SFX */
        virtual void sfxSetDistanceModel(( SFXDistanceModel model )) {}
        /*! Get the current global doppler effect setting.
    
    @return The current global doppler effect scale factor (>=0).
    
    @see sfxSetDopplerFactor
    
    @ref SFXSource_doppler
    
    @ingroup SFX */
        virtual float sfxGetDopplerFactor(()) {}
        /*! Set the global doppler effect scale factor.
    @param value The new doppler shift scale factor.
    @pre @a value must be >= 0.
    @see sfxGetDopplerFactor
    
    @ref SFXSource_doppler
    
    @ingroup SFX */
        virtual void sfxSetDopplerFactor(( float value )) {}
        /*! Get the current global scale factor applied to volume attenuation of 3D sounds in the logarithmic model.
    @return The current scale factor for logarithmic 3D sound falloff curves.
    
    @see sfxGetDistanceModel
    @see SFXDistanceModel
    
    @ref SFXSource_volume
    @ref SFX_3d
    @ingroup SFX */
        virtual float sfxGetRolloffFactor(()) {}
        /*! Set the global scale factor to apply to volume attenuation of 3D sounds in the logarithmic model.
    @param value The new scale factor for logarithmic 3D sound falloff curves.
    
    @pre @a value must be > 0.
    @note This function has no effect if the currently distance model is set to SFXDistanceModel::Linear.
    
    @see sfxGetDistanceModel
    @see SFXDistanceModel
    
    @ref SFXSource_volume
    @ref SFX_3d
    @ingroup SFX */
        virtual void sfxSetRolloffFactor(( float value )) {}
        /*! Dump information about all current SFXSource instances to the console.
    The dump includes information about the playback status for each source, volume levels, virtualization, etc.
    @param includeGroups If true, direct instances of SFXSources (which represent logical sound groups) will be included. Otherwise only instances of subclasses of SFXSources are included in the dump.
    @see SFXSource
    @see sfxDumpSourcesToString
    @ingroup SFX */
        virtual void sfxDumpSources(( bool includeGroups=false )) {}
        /*! Dump information about all current SFXSource instances to a string.
    The dump includes information about the playback status for each source, volume levels, virtualization, etc.
    @param includeGroups If true, direct instances of SFXSources (which represent logical sound groups) will be included. Otherwise only instances of subclasses of SFXSources are included in the dump.
    @return A string containing a dump of information about all currently instantiated SFXSources.
    @see SFXSource
    @see sfxDumpSources
    @ingroup SFX */
        virtual string sfxDumpSourcesToString(( bool includeGroups=false )) {}
        virtual void fmodDumpDSPInfo() {}
        virtual void fmodDumpMemoryStats() {}
        /*! @brief Returns the current %ActionMap.
    @see ActionMap@ingroup Input */
        virtual string getCurrentActionMap(()) {}
        virtual void SendCharactersListReq() {}
        virtual int CreateCharacterGetMaxStatPoints(()) {}
        virtual int CreateCharacterGetMaxCraftingSkillPoints(()) {}
        virtual int CreateCharacterGetMaxFightingSkillPoints(()) {}
        virtual void normalizeStatSliders() {}
        virtual void normalizeCraftingSkillSliders() {}
        virtual void normalizeFightingSkillSliders() {}
        virtual void randomizeStatSliders() {}
        virtual void randomizeCraftingSkillSliders() {}
        virtual void randomizeFightingSkillSliders() {}
        virtual void CreateCharacterCancelPressed() {}
        virtual void CreateCharacterNextPressed() {}
        virtual void CharNameAvailableReceived() {}
        virtual void sendExitRequestToServer() {}
        virtual void sendExitCancelRequestToServer() {}
        virtual void CharSelectionSlotPressed() {}
        virtual bool CharSelectionDelcharSure(( int slot, string name )) {}
        virtual void CharSelectionDelPressed() {}
        virtual void openCharacterCreationDialog() {}
        virtual void closeCharacterSelectionDialog() {}
        virtual void CharSelectionPlayPressed() {}
        /*! Returns the maximum number of supported character slots. */
        virtual int CharSelectionGetMaxCharSlots(()) {}
        virtual string calcSha1() {}
        virtual void openSteamVoiceChatSettings() {}
        virtual string getSteamGameLanguage(()) {}
        virtual string getSteamUILanguage(()) {}
        virtual void openSteamURL(( String url )) {}
        virtual bool DebugSteamInvite(( string steamIDStr, string ip, int port )) {}
        virtual void openSteamStore(( int itemDefId=0 )) {}
        virtual void steamVoice_pushButton(()) {}
        virtual void steamVoice_popButton(()) {}
        /*! enableSteamVoiceChat() */
        virtual void enableSteamVoiceChat(()) {}
        /*! disableSteamVoiceChat() */
        virtual void disableSteamVoiceChat(()) {}
        virtual void SubstanceManager_init() {}
        virtual void SubstanceManager_clear() {}
        virtual int GetServerCentralTer(( int serverID )) {}
        virtual string GetServerTerIDList(( int serverID, bool includeSideTers=false )) {}
        virtual float getTerrainTopAtPosition() {}
        virtual void tmpHideAllNakedMans() {}
        virtual void tmpSwitchNakedMan() {}
        virtual void detachTerrains() {}
        virtual void preloadData() {}
        virtual void validateAllTerMatRemap() {}
        virtual void initGlobalRemapIndex() {}
        virtual void SaveMapFiles() {}
        virtual void currentLocalCoords(()) {}
        virtual void Tunnels_PrintBlockCount(()) {}
        virtual void Tunnels_VisualizeSrvCollision(( int terID, int x, int y, int altitude )) {}
        virtual void Tunnels_ClearSrvCollisions(()) {}
        virtual void Tunnels_VerifyManagersSync(()) {}
        virtual void tsUpdateImposterImages() {}
        virtual void setDisableSkinnedMatCheck(( bool isDisabled=true )) {}
        virtual void calculateVelocity(( bool enabled )) {}
        virtual void resetFPSTracker() {}
        virtual void beginSampling() {}
        virtual void stopSampling() {}
        virtual void enableSamples() {}
        virtual string getCmVersionString() {}
        virtual string getCmVersionStringNoPrefix() {}
        virtual int openWeb() {}
        virtual void terminate() {}
 };
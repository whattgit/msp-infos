# III.1 — Administration & infrastructure

> **FR** · [English](../../en/amf/01-admin.md)


Modération, upload contenu, logging, OS Check, tags, thèmes boutique.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `LikeAdd` | `AMFCommonService` | `fameEarned` | Oui |
| `SaveRoomWithSnapshot` | `AMFRoomService` | `entier` | Oui |

## `WebService.AMFCommonService`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFCommonService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `ActorHasLiked` | param3, param1, param2 | Endpoint AMF `ActorHasLiked`. | — |
| `LikeAdd` | entityType, entityId, selfActorId, receiver | Like générique (film, look, etc.) ; `fameEarned==-429`. | `-429` |
| `LogChat` | param1, param2, param3, InputLocations.DESTINATION_TYPE_USER | Endpoint AMF `LogChat`. | — |
| `LogInput` | roomId, actorId, roomInstanceId, message, destinationType | Endpoint AMF `LogInput`. | — |
| `SendContentEmail` | param1, param2, param3, param4, param5 | Endpoint AMF `SendContentEmail`. | — |
| `getNowAsString` | — | Endpoint AMF `getNowAsString`. | — |

### Détail endpoints

#### `ActorHasLiked`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param3, param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` |
| Fonctionnement | Endpoint AMF `ActorHasLiked`. |

#### `LikeAdd`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | entityType, entityId, selfActorId, receiver |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `fameEarned` (popup) |
| Codes retour | Champ `fameEarned` == −429 (popup) |
| Client AMF | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` (+1) |
| UI / appelants | `MyLooksEditor.as`, `ChatRoomFlexApps.as`, `LikeDesignCommand.as`, `WAYDListItemRenderer.as` (+2) |
| Fonctionnement | Like générique (film, look, etc.) ; `fameEarned==-429`. |

#### `LogChat`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, InputLocations.DESTINATION_TYPE_USER |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` |
| Fonctionnement | Endpoint AMF `LogChat`. |

#### `LogInput`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | roomId, actorId, roomInstanceId, message, destinationType |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` (+2) |
| UI / appelants | `ManageClub.as`, `CommentNewComponent.as`, `MonsterPopup.as`, `MyLooksEditor.as` (+21) |
| Fonctionnement | Endpoint AMF `LogInput`. |

#### `SendContentEmail`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` (+1) |
| UI / appelants | `SendContentAsMailPopup.as` |
| Fonctionnement | Endpoint AMF `SendContentEmail`. |

#### `getNowAsString`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` |
| Fonctionnement | Endpoint AMF `getNowAsString`. |

## `WebService.Admin.AMFAdminService`

**Chemin AMF :** `MovieStarPlanet.WebService.Admin.AMFAdminService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BlockName` | param1, param2, param3 | Endpoint AMF `BlockName`. | — |
| `ClearCache` | param1, param2, true | Endpoint AMF `ClearCache`. | — |
| `ClearNewMarkings` | param1, param2 | Endpoint AMF `ClearNewMarkings`. | — |
| `DeleteTwitterText` | param1, param2, param3 | Supprime e twitter text. | — |
| `GetActorLocale` | param1 | Récupère actor locale. | — |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize | Récupère all gifts given. | — |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize | Récupère all gifts received. | — |
| `GetBadWordActorList` | pageIndex, pageSize | Récupère bad word actor list. | — |
| `GetBlockedIP` | ipAsInt, moderatorName, moderatorPass | Récupère blocked ip. | — |
| `GetBlockedInfo` | ipAsInt, moderatorName, moderatorPass | Récupère blocked info. | — |
| `GetBlockedNames` | searchphrase | Récupère blocked names. | — |
| `GetChatLogList` | actorId, pageIndex, pageSize | Récupère chat log list. | — |
| `GetChatLogListByReportTime` | paramObj.actorId, paramObj.reportId, pageIndex, pageSize | Récupère chat log list by report time. | — |
| `GetChatLogListLocked` | actorId | Récupère chat log list locked. | — |
| `GetIPLoginType` | ipAsIntToUse, moderatorName, moderatorPass | Récupère iplogin type. | — |
| `GetIPUsers` | ipAsIntToUse, moderatorName, moderatorPass | Récupère ipusers. | — |
| `GetIPWarnings` | ipAsIntToUse, moderatorName, moderatorPass | Récupère ipwarnings. | — |
| `GetLocaleResources` | param1, param2, param3, param4, param5 | Récupère locale resources. | — |
| `GetLoginHistory` | param1, param2, param3 | Récupère login history. | — |
| `GetModeratorList` | pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass | Récupère moderator list. | — |
| `GetModeratorWarningCount` | paramObj.moderatorId, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass | Récupère moderator warning count. | — |
| `GetModeratorWarnings` | paramObj.moderatorId, paramObj.date, pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword | Récupère moderator warnings. | — |
| `GetReportList` | onlyGetNotHandled, pageIndex, pageSize | Récupère report list. | — |
| `GetReportOverview` | — | Récupère report overview. | — |
| `GetSecureModuleUrl` | — | Récupère secure module url. | — |
| `GetTotalModeratorActivitiesDone` | actorId, moderatorName, moderatorPass | Récupère total moderator activities done. | — |
| `GetWarnedIPListNew` | paramObj.blocked, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass, paramObj.specificIp ? paramObj.specificIp : 0 | Récupère warned iplist new. | — |
| `GetWarningLog` | pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword | Récupère warning log. | — |
| `GiveAutoWarning` | param1, param2, param3, param4 | Endpoint AMF `GiveAutoWarning`. | — |
| `IsAdminSite` | param1, param2 | Endpoint AMF `IsAdminSite`. | — |
| `IsUploadSite` | — | Endpoint AMF `IsUploadSite`. | — |
| `LockOutUser` | param1, param2, param3, param4, param5 | Endpoint AMF `LockOutUser`. | — |
| `RemoveRoboBlastContent` | actorId, contentType, contentId, reporterId, site | Supprime e robo blast content. | — |
| `ReportHandled` | reportId, handledByActorId | Endpoint AMF `ReportHandled`. | — |
| `SaveLocaleResources` | param1 | Sauvegarde / crée save locale resources. | — |
| `UnblockName` | param1, param2, param3 | Endpoint AMF `UnblockName`. | — |
| `blockIP` | ipAsIntToBlock, moderatorActorId, moderatorName, moderatorPass, blockingDaysCount, comment | Endpoint AMF `blockIP`. | — |
| `deleteMovieViaProfile` | movieId, moderatorName, moderatorPass | Endpoint AMF `deleteMovieViaProfile`. | — |
| `getChatRoomOpenCloseTimes` | — | Endpoint AMF `getChatRoomOpenCloseTimes`. | — |
| `isIPBlockedNew` | ipAsIntToFind, moderatorName, moderatorPass | Endpoint AMF `isIPBlockedNew`. | — |
| `markIpAsPublic` | ipAsIntToMark, moderatorName, moderatorPass | Endpoint AMF `markIpAsPublic`. | — |
| `saveSpamReport` | spamtext, moderatorActorId, moderatorName, moderatorPass | Endpoint AMF `saveSpamReport`. | — |
| `setChatRoomOpenCloseTimes` | open, close | Endpoint AMF `setChatRoomOpenCloseTimes`. | — |
| `unblockIP` | ipAsIntToUnblock, moderatorID, moderatorName, moderatorPass, comment | Endpoint AMF `unblockIP`. | — |
| `unmarkIpAsPublic` | ipAsIntToUnmark, moderatorName, moderatorPass | Endpoint AMF `unmarkIpAsPublic`. | — |

### Détail endpoints

#### `BlockName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `BlockedNames.as` |
| Fonctionnement | Endpoint AMF `BlockName`. |

#### `ClearCache`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, true |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `CommentsComponent.as`, `UploadClothes.as`, `MSP_InventoryContainer.as`, `Admin.as` (+11) |
| Fonctionnement | Endpoint AMF `ClearCache`. |

#### `ClearNewMarkings`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Endpoint AMF `ClearNewMarkings`. |

#### `DeleteTwitterText`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `AdminDeleteButton.as` |
| Fonctionnement | Supprime e twitter text. |

#### `GetActorLocale`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `UserAdmin.as` |
| Fonctionnement | Récupère actor locale. |

#### `GetAllGiftsGiven`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` (+1) |
| UI / appelants | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Fonctionnement | Récupère all gifts given. |

#### `GetAllGiftsReceived`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` (+1) |
| UI / appelants | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Fonctionnement | Récupère all gifts received. |

#### `GetBadWordActorList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère bad word actor list. |

#### `GetBlockedIP`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsInt, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère blocked ip. |

#### `GetBlockedInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsInt, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `BlockedIPInfoForm.as` |
| Fonctionnement | Récupère blocked info. |

#### `GetBlockedNames`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | searchphrase |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `BlockedNames.as` |
| Fonctionnement | Récupère blocked names. |

#### `GetChatLogList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère chat log list. |

#### `GetChatLogListByReportTime`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | paramObj.actorId, paramObj.reportId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère chat log list by report time. |

#### `GetChatLogListLocked`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère chat log list locked. |

#### `GetIPLoginType`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToUse, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as` |
| Fonctionnement | Récupère iplogin type. |

#### `GetIPUsers`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToUse, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as` |
| Fonctionnement | Récupère ipusers. |

#### `GetIPWarnings`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToUse, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as` |
| Fonctionnement | Récupère ipwarnings. |

#### `GetLocaleResources`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `LocaleEditor.as`, `LocaleProvider.as`, `MovieCompetitionPublisherItem.as`, `PollEditorItem.as` |
| Fonctionnement | Récupère locale resources. |

#### `GetLoginHistory`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère login history. |

#### `GetModeratorList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère moderator list. |

#### `GetModeratorWarningCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | paramObj.moderatorId, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `ModeratorList.as` |
| Fonctionnement | Récupère moderator warning count. |

#### `GetModeratorWarnings`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | paramObj.moderatorId, paramObj.date, pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `ModeratorList.as` |
| Fonctionnement | Récupère moderator warnings. |

#### `GetReportList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | onlyGetNotHandled, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère report list. |

#### `GetReportOverview`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `UpdateReportOverviewCommand.as` |
| Fonctionnement | Récupère report overview. |

#### `GetSecureModuleUrl`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Récupère secure module url. |

#### `GetTotalModeratorActivitiesDone`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `ModeratorList.as` |
| Fonctionnement | Récupère total moderator activities done. |

#### `GetWarnedIPListNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | paramObj.blocked, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass, paramObj.specificIp ? paramObj.specificIp : 0 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as` |
| Fonctionnement | Récupère warned iplist new. |

#### `GetWarningLog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `WarningListForm.as` |
| Fonctionnement | Récupère warning log. |

#### `GiveAutoWarning`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `ClubView.as`, `AdminDeleteButton.as`, `MovieHighScoreComponent.as`, `LookCommentItemComponent.as` (+18) |
| Fonctionnement | Endpoint AMF `GiveAutoWarning`. |

#### `IsAdminSite`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `Admin.as`, `SpendingServiceSettings.as`, `AnimationShopView.as`, `ClothesShopModel.as` (+4) |
| Fonctionnement | Endpoint AMF `IsAdminSite`. |

#### `IsUploadSite`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `Admin.as` |
| Fonctionnement | Endpoint AMF `IsUploadSite`. |

#### `LockOutUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` (+1) |
| UI / appelants | `AdminManager.as`, `UserBehaviorServiceSettings.as` |
| Fonctionnement | Endpoint AMF `LockOutUser`. |

#### `RemoveRoboBlastContent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, contentType, contentId, reporterId, site |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Fonctionnement | Supprime e robo blast content. |

#### `ReportHandled`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | reportId, handledByActorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `NebulaMsgServiceMessageTypes.as` |
| Fonctionnement | Endpoint AMF `ReportHandled`. |

#### `SaveLocaleResources`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `LocaleEditor.as`, `LocaleProvider.as`, `PollEditorItem.as` |
| Fonctionnement | Sauvegarde / crée save locale resources. |

#### `UnblockName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `BlockedNames.as` |
| Fonctionnement | Endpoint AMF `UnblockName`. |

#### `blockIP`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToBlock, moderatorActorId, moderatorName, moderatorPass, blockingDaysCount, comment |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as`, `TempIPBlockingForm.as` |
| Fonctionnement | Endpoint AMF `blockIP`. |

#### `deleteMovieViaProfile`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `MovieHighScoreComponent.as`, `MovieContentListItemRenderer.as`, `MovieSocialListItemRenderer.as` |
| Fonctionnement | Endpoint AMF `deleteMovieViaProfile`. |

#### `getChatRoomOpenCloseTimes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `ChatRoomCloseTimePanel.as` |
| Fonctionnement | Endpoint AMF `getChatRoomOpenCloseTimes`. |

#### `isIPBlockedNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToFind, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as` |
| Fonctionnement | Endpoint AMF `isIPBlockedNew`. |

#### `markIpAsPublic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToMark, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as` |
| Fonctionnement | Endpoint AMF `markIpAsPublic`. |

#### `saveSpamReport`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | spamtext, moderatorActorId, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `ReportSpamForm.as` |
| Fonctionnement | Endpoint AMF `saveSpamReport`. |

#### `setChatRoomOpenCloseTimes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | open, close |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `ChatRoomCloseTimePanel.as` |
| Fonctionnement | Endpoint AMF `setChatRoomOpenCloseTimes`. |

#### `unblockIP`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToUnblock, moderatorID, moderatorName, moderatorPass, comment |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as`, `TempIPBlockingForm.as` |
| Fonctionnement | Endpoint AMF `unblockIP`. |

#### `unmarkIpAsPublic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ipAsIntToUnmark, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / appelants | `IPWarnedList.as` |
| Fonctionnement | Endpoint AMF `unmarkIpAsPublic`. |

## `WebService.AnimationSnapshot.AMFAnimationSnapshotService`

**Chemin AMF :** `MovieStarPlanet.WebService.AnimationSnapshot.AMFAnimationSnapshotService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `getAnimationNames` | — | Endpoint AMF `getAnimationNames`. | — |
| `saveImage` | data, name | Endpoint AMF `saveImage`. | — |

### Détail endpoints

#### `getAnimationNames`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/controller/SaveAnimationSnapshotCommand.as` |
| UI / appelants | `TestingForm.as` |
| Fonctionnement | Endpoint AMF `getAnimationNames`. |

#### `saveImage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | data, name |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/controller/SaveAnimationSnapshotCommand.as` |
| Fonctionnement | Endpoint AMF `saveImage`. |

## `WebService.Common.AMFCommonWebService`

**Chemin AMF :** `MovieStarPlanet.WebService.Common.AMFCommonWebService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetEntityName` | param1, param2 | Récupère entity name. | — |
| `GetPlaylistExternalRef` | param1 | Récupère playlist external ref. | — |
| `LikeAdd` | entityType, entityId, actorId, receiverId | Like générique (film, look, etc.) ; `fameEarned==-429`. | `-429` |
| `SaveRoomWithSnapshot` | actorId, roomData, snapshots[3] | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. | `-429` |
| `SendContentEmail` | param1, param2, param3, param4, param5 | Endpoint AMF `SendContentEmail`. | — |

### Détail endpoints

#### `GetEntityName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` |
| UI / appelants | `Favorites.as` |
| Fonctionnement | Récupère entity name. |

#### `GetPlaylistExternalRef`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` |
| UI / appelants | `Favorites.as` |
| Fonctionnement | Récupère playlist external ref. |

#### `LikeAdd`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | entityType, entityId, actorId, receiverId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `fameEarned` (popup) |
| Codes retour | Champ `fameEarned` == −429 (popup) |
| Client AMF | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` (+1) |
| UI / appelants | `MyLooksEditor.as`, `ChatRoomFlexApps.as`, `LikeDesignCommand.as`, `WAYDListItemRenderer.as` (+2) |
| Fonctionnement | Like générique (film, look, etc.) ; `fameEarned==-429`. |

#### `SaveRoomWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, roomData, snapshots[3] |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `entier` (popup) |
| Codes retour | Champ `entier` == −429 (popup) |
| Client AMF | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` (+1) |
| UI / appelants | `EditMyRoom.as`, `StuffView.as`, `SaveMyRoomCommand.as` |
| Fonctionnement | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. |

#### `SendContentEmail`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` (+1) |
| UI / appelants | `SendContentAsMailPopup.as` |
| Fonctionnement | Endpoint AMF `SendContentEmail`. |

## `WebService.Logging.AMFLoggingService`

**Chemin AMF :** `MovieStarPlanet.WebService.Logging.AMFLoggingService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `ClientLog` | param1, param2 | Endpoint AMF `ClientLog`. | — |
| `CreateTestException` | — | Sauvegarde / crée create test exception. | — |
| `GetLatestServerException` | — | Récupère latest server exception. | — |
| `LogClient` | param1, param2 | Endpoint AMF `LogClient`. | — |

### Détail endpoints

#### `ClientLog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| Fonctionnement | Endpoint AMF `ClientLog`. |

#### `CreateTestException`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| Fonctionnement | Sauvegarde / crée create test exception. |

#### `GetLatestServerException`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| UI / appelants | `GetLatestErrorCommand.as` |
| Fonctionnement | Récupère latest server exception. |

#### `LogClient`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| UI / appelants | `ChecksumCalculator.as`, `SetupAppSettingsCommand.as`, `Log.as`, `PlaybackSession.as` |
| Fonctionnement | Endpoint AMF `LogClient`. |

## `WebService.Moderation.AMFModeration`

**Chemin AMF :** `MovieStarPlanet.WebService.Moderation.AMFModeration`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CheckNewUsername` | userName, this._site | Vérifie new username. | — |
| `FilterText` | (param1, param5, param4, param2, param3) · (param1, param5, param4, param2, param3, param8, param9) | Endpoint AMF `FilterText`. | — |
| `LoginEvent` | param1 | Endpoint AMF `LoginEvent`. | — |
| `ReportUser` | param2, param3, param4, param6, this._site, param7 | Endpoint AMF `ReportUser`. | — |
| `ReportUserNeb` | param2, param5, param4, param6 | Endpoint AMF `ReportUserNeb`. | — |

### Détail endpoints

#### `CheckNewUsername`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | userName, this._site |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| Fonctionnement | Vérifie new username. |

#### `FilterText`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (param1, param5, param4, param2, param3) · (param1, param5, param4, param2, param3, param8, param9) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| UI / appelants | `TwitterConfig.as`, `ChatListener.as`, `Censor.as`, `YTBlackListUtil.as` (+8) |
| Fonctionnement | Endpoint AMF `FilterText`. |

#### `LoginEvent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| UI / appelants | `ChatListener.as`, `LoginRequiredSetupCommand.as`, `TextModerationHandler.as`, `FriendNotificationChannel.as` (+2) |
| Fonctionnement | Endpoint AMF `LoginEvent`. |

#### `ReportUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param3, param4, param6, this._site, param7 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| UI / appelants | `CharacterPopUp.as`, `NewReport.as`, `SetupAnalyticsAfterLoginCommand.as`, `TextModerationHandler.as` |
| Fonctionnement | Endpoint AMF `ReportUser`. |

#### `ReportUserNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param5, param4, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| Fonctionnement | Endpoint AMF `ReportUserNeb`. |

## `WebService.Os.AMFOs`

**Chemin AMF :** `MovieStarPlanet.WebService.Os.AMFOs`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CreateOsRef` | — | Démarre OS Check ; exempt checksum requête. | — |
| `RunOsCheck` | refId, hist.join(":") | Valide histogramme environnement ; exempt checksum. | — |

### Détail endpoints

#### `CreateOsRef`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/snapshot/SnapLoader.as` |
| UI / appelants | `AmfCaller.as`, `ChecksumCalculator.as` |
| Fonctionnement | Démarre OS Check ; exempt checksum requête. |

#### `RunOsCheck`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | refId, hist.join(":") |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/snapshot/SnapLoader.as` |
| UI / appelants | `AmfCaller.as`, `ChecksumCalculator.as` |
| Fonctionnement | Valide histogramme environnement ; exempt checksum. |

## `WebService.PerformanceTracking.AMFPerformanceTrackingService`

**Chemin AMF :** `MovieStarPlanet.WebService.PerformanceTracking.AMFPerformanceTrackingService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AddEntry` | param1, param2 | Endpoint AMF `AddEntry`. | — |

### Détail endpoints

#### `AddEntry`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/utils/performance/PerformanceTrackingAmfService.as` |
| UI / appelants | `SquigglyDictionary.as`, `PerformanceLogger.as` |
| Fonctionnement | Endpoint AMF `AddEntry`. |

## `WebService.Snapshots.AMFGenericSnapshotService`

**Chemin AMF :** `MovieStarPlanet.WebService.Snapshots.AMFGenericSnapshotService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CreateSnapshot` | (param1, param2, param3, param4) · (param1, param2, param3, param4, param5) | Sauvegarde / crée create snapshot. | — |
| `CreateSnapshotSmallAndBig` | param1, param2, param3, param4, param5, param6 | Sauvegarde / crée create snapshot small and big. | — |

### Détail endpoints

#### `CreateSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (param1, param2, param3, param4) · (param1, param2, param3, param4, param5) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/snapshotservice/GenericSnapshotAMFService.as` |
| UI / appelants | `PublicProfile.as`, `ChatRoomFlexApps.as`, `RegisterNewUserComponent.as`, `UserInfoInteractionTheme.as` (+9) |
| Fonctionnement | Sauvegarde / crée create snapshot. |

#### `CreateSnapshotSmallAndBig`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/snapshotservice/GenericSnapshotAMFService.as` |
| UI / appelants | `SaveClothesCommand.as`, `BeautyClinicBuyCommand.as`, `BeautyClinicWearCommand.as` |
| Fonctionnement | Sauvegarde / crée create snapshot small and big. |

## `WebService.TagManager.AMFTagManager`

**Chemin AMF :** `MovieStarPlanet.WebService.TagManager.AMFTagManager`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `DeleteTag` | param1 | Supprime e tag. | — |
| `GetAllTags` | — | Récupère all tags. | — |
| `GetBackgroundTags` | — | Récupère background tags. | — |
| `GetTagsForSkinClothes` | param2 | Récupère tags for skin clothes. | — |
| `GetTagsInCategorySkin` | param2, param3 | Récupère tags in category skin. | — |
| `SaveTag` | param1 | Sauvegarde / crée save tag. | — |

### Détail endpoints

#### `DeleteTag`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / appelants | `TagManager.as` |
| Fonctionnement | Supprime e tag. |

#### `GetAllTags`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / appelants | `TagManager.as`, `UploadClothes.as`, `SettingsManager.as` |
| Fonctionnement | Récupère all tags. |

#### `GetBackgroundTags`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / appelants | `BackgroundTagService.as`, `BackgroundUtil.as` |
| Fonctionnement | Récupère background tags. |

#### `GetTagsForSkinClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| Fonctionnement | Récupère tags for skin clothes. |

#### `GetTagsInCategorySkin`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / appelants | `TagSelector.as` |
| Fonctionnement | Récupère tags in category skin. |

#### `SaveTag`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / appelants | `TagManager.as` |
| Fonctionnement | Sauvegarde / crée save tag. |

## `WebService.ThemeManager.AMFThemeManagerService`

**Chemin AMF :** `MovieStarPlanet.WebService.ThemeManager.AMFThemeManagerService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `DeleteTheme` | param1 | Supprime e theme. | — |
| `GetAllCampaigns` | — | Récupère all campaigns. | — |
| `GetAllThemes` | — | Récupère all themes. | — |
| `GetCurrectNewCategorySortIndex` | — | Récupère currect new category sort index. | — |
| `InsertTheme` | param1, param2, param3, param4 | Endpoint AMF `InsertTheme`. | — |
| `LabelClothesWithTheme` | param1, param2 | Endpoint AMF `LabelClothesWithTheme`. | — |
| `RetrieveThemeID` | param1, param2 | Endpoint AMF `RetrieveThemeID`. | — |
| `SortShoppingItems` | param1, param2, param3 | Endpoint AMF `SortShoppingItems`. | — |
| `UpdateTheme` | param1 | Met à jour ate theme. | — |

### Détail endpoints

#### `DeleteTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `ThemeManagerForm.as`, `WorldThemeManager.as` |
| Fonctionnement | Supprime e theme. |

#### `GetAllCampaigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| Fonctionnement | Récupère all campaigns. |

#### `GetAllThemes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `ClothSortingList.as`, `FacepartUploader.as`, `ThemeManagerForm.as`, `TreeBasedShopEditor.as` (+7) |
| Fonctionnement | Récupère all themes. |

#### `GetCurrectNewCategorySortIndex`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `Admin.as` |
| Fonctionnement | Récupère currect new category sort index. |

#### `InsertTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `CreateThemeForm.as` |
| Fonctionnement | Endpoint AMF `InsertTheme`. |

#### `LabelClothesWithTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `ClothSortingList.as` |
| Fonctionnement | Endpoint AMF `LabelClothesWithTheme`. |

#### `RetrieveThemeID`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `TreeBasedShopEditor.as`, `EditOrDeleteAnimation.as` |
| Fonctionnement | Endpoint AMF `RetrieveThemeID`. |

#### `SortShoppingItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `ClothSortingList.as` |
| Fonctionnement | Endpoint AMF `SortShoppingItems`. |

#### `UpdateTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / appelants | `CreateThemeForm.as`, `ThemeManagerForm.as`, `FlashHiddenShop.as` |
| Fonctionnement | Met à jour ate theme. |

## `WebService.Upload.AMFUploadService`

**Chemin AMF :** `MovieStarPlanet.WebService.Upload.AMFUploadService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CheckAnimationExists` | animationName | Vérifie animation exists. | — |
| `DeleteClipArt` | clipart, subpath | Supprime e clip art. | — |
| `DeleteFacepart` | facepartId, type | Supprime e facepart. | — |
| `DeleteWallpaper` | wallpaperId | Supprime e wallpaper. | — |
| `EditAnimation` | animationId, name, price, discount, checkVip, checkNew, checkDeleted, animCategoryId, themeID, priceDiamonds | Endpoint AMF `EditAnimation`. | — |
| `EditClipArt` | clipart, subpath, sort, checkvip, checknew, price, diamondsPrice | Endpoint AMF `EditClipArt`. | — |
| `EditFacepart` | facepartId, type, gender, name, fileName, price, checkvip, checknew, checkreg, discount, sortorder, themeID, priceDiamonds | Endpoint AMF `EditFacepart`. | — |
| `FileExistsCheck` | key | Endpoint AMF `FileExistsCheck`. | — |
| `GetAnimationCategories` | — | Récupère animation categories. | — |
| `GetClipArtPath` | clipart | Récupère clip art path. | — |
| `InsertAnimation` | name, price, diamondsprice, animCategory, vip, fileName, themeID | Endpoint AMF `InsertAnimation`. | — |
| `InsertBackground` | name, price, backgroundCategory, vip, fileName, themeID | Endpoint AMF `InsertBackground`. | — |
| `InsertClipArt` | type, category, fileName, checkvip, checkNew, sortorder, price, diamondPrice, colorScheme | Endpoint AMF `InsertClipArt`. | — |
| `InsertFacepart` | type, gender, name, fileName, price, diamondPrice, checkvip, dragonBone, defaultColors, checknew, checkreg, discount, sortorder, themeID, date, hidden | Endpoint AMF `InsertFacepart`. | — |
| `InsertWallpaper` | type, roomtype, name, filepath | Endpoint AMF `InsertWallpaper`. | — |
| `getAllColorschemelessClothes` | pageIdx, pageSize | Endpoint AMF `getAllColorschemelessClothes`. | — |
| `getBonsterInfo` | templateName | Endpoint AMF `getBonsterInfo`. | — |
| `getClipArtCategoryNames` | paramid | Endpoint AMF `getClipArtCategoryNames`. | — |
| `getClipArtTypes` | — | Endpoint AMF `getClipArtTypes`. | — |
| `giveBonster` | templateName | Endpoint AMF `giveBonster`. | — |
| `saveClothUpdater` | cloth, themeID | Endpoint AMF `saveClothUpdater`. | — |
| `setClothColorSchemes` | ([colorSchemeObject) · (clothColorSchemes) | Endpoint AMF `setClothColorSchemes`. | — |
| `updateAnimation` | copy, themeID | Endpoint AMF `updateAnimation`. | — |
| `updateBackground` | copy, themeID | Endpoint AMF `updateBackground`. | — |
| `updateBonsterColors` | bonsterId, colorMatrix | Endpoint AMF `updateBonsterColors`. | — |
| `updateBonsterScale` | bonsterId, mobScale, webScale | Endpoint AMF `updateBonsterScale`. | — |
| `updateCloth` | clothUpdater | Endpoint AMF `updateCloth`. | — |
| `updateMusic` | copy | Endpoint AMF `updateMusic`. | — |
| `uploadBonster` | templateName, templateId, armatureName, price, diamondsPrice, isVIP, deleted, specialEggCrate, scale, scaleWeb | Endpoint AMF `uploadBonster`. | — |

### Détail endpoints

#### `CheckAnimationExists`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | animationName |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `UploadAnimation.as` |
| Fonctionnement | Vérifie animation exists. |

#### `DeleteClipArt`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clipart, subpath |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `EditOrDeleteClipArt.as` |
| Fonctionnement | Supprime e clip art. |

#### `DeleteFacepart`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | facepartId, type |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Fonctionnement | Supprime e facepart. |

#### `DeleteWallpaper`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | wallpaperId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `DeleteWallpaper.as`, `UploadWallpaper.as` |
| Fonctionnement | Supprime e wallpaper. |

#### `EditAnimation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | animationId, name, price, discount, checkVip, checkNew, checkDeleted, animCategoryId, themeID, priceDiamonds |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `EditOrDeleteAnimation.as` |
| Fonctionnement | Endpoint AMF `EditAnimation`. |

#### `EditClipArt`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clipart, subpath, sort, checkvip, checknew, price, diamondsPrice |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `EditOrDeleteClipArt.as`, `ArtBookCreatorFrame.as` |
| Fonctionnement | Endpoint AMF `EditClipArt`. |

#### `EditFacepart`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | facepartId, type, gender, name, fileName, price, checkvip, checknew, checkreg, discount, sortorder, themeID, priceDiamonds |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `AdminManager.as`, `AdminManagerEntry.as`, `ShoppingOperator.as` |
| Fonctionnement | Endpoint AMF `EditFacepart`. |

#### `FileExistsCheck`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | key |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `BonsterUploader.as`, `CreateThemeForm.as`, `FacepartUploader.as`, `EditOrDeleteClipArt.as` (+8) |
| Fonctionnement | Endpoint AMF `FileExistsCheck`. |

#### `GetAnimationCategories`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `EditOrDeleteAnimation.as`, `UploadAnimation.as`, `ChatRoomAnimationSelector.as` |
| Fonctionnement | Récupère animation categories. |

#### `GetClipArtPath`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clipart |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Fonctionnement | Récupère clip art path. |

#### `InsertAnimation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | name, price, diamondsprice, animCategory, vip, fileName, themeID |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `UploadAnimation.as` |
| Fonctionnement | Endpoint AMF `InsertAnimation`. |

#### `InsertBackground`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | name, price, backgroundCategory, vip, fileName, themeID |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `UploadBackgroundLogic.as`, `ScrapBlogNewsEditor.as`, `ShopContentAmfService.as`, `ShopContentProvider.as` |
| Fonctionnement | Endpoint AMF `InsertBackground`. |

#### `InsertClipArt`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | type, category, fileName, checkvip, checkNew, sortorder, price, diamondPrice, colorScheme |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `UploadClipArt.as` |
| Fonctionnement | Endpoint AMF `InsertClipArt`. |

#### `InsertFacepart`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | type, gender, name, fileName, price, diamondPrice, checkvip, dragonBone, defaultColors, checknew, checkreg, discount, sortorder, themeID, date, hidden |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `FacepartUploader.as` |
| Fonctionnement | Endpoint AMF `InsertFacepart`. |

#### `InsertWallpaper`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | type, roomtype, name, filepath |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `UploadWallpaper.as` |
| Fonctionnement | Endpoint AMF `InsertWallpaper`. |

#### `getAllColorschemelessClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIdx, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `ClothColorParser.as` |
| Fonctionnement | Endpoint AMF `getAllColorschemelessClothes`. |

#### `getBonsterInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | templateName |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `BonsterTester.as` |
| Fonctionnement | Endpoint AMF `getBonsterInfo`. |

#### `getClipArtCategoryNames`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | paramid |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `UploadClipArt.as` |
| Fonctionnement | Endpoint AMF `getClipArtCategoryNames`. |

#### `getClipArtTypes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `UploadClipArt.as` |
| Fonctionnement | Endpoint AMF `getClipArtTypes`. |

#### `giveBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | templateName |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Fonctionnement | Endpoint AMF `giveBonster`. |

#### `saveClothUpdater`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | cloth, themeID |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Fonctionnement | Endpoint AMF `saveClothUpdater`. |

#### `setClothColorSchemes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ([colorSchemeObject) · (clothColorSchemes) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `ClothColorParser.as`, `ClothesShopController.as`, `ClothColorSchemeObject.as` |
| Fonctionnement | Endpoint AMF `setClothColorSchemes`. |

#### `updateAnimation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | copy, themeID |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `TreeBasedShopEditor.as`, `CategoryViewMediator.as`, `PreviewAnimation.as`, `Armature.as` |
| Fonctionnement | Endpoint AMF `updateAnimation`. |

#### `updateBackground`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | copy, themeID |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `TreeBasedShopEditor.as`, `UploadBackgroundLogic.as`, `FrameViewMediator.as`, `DynamicPopup.as` (+3) |
| Fonctionnement | Endpoint AMF `updateBackground`. |

#### `updateBonsterColors`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | bonsterId, colorMatrix |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Fonctionnement | Endpoint AMF `updateBonsterColors`. |

#### `updateBonsterScale`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | bonsterId, mobScale, webScale |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Fonctionnement | Endpoint AMF `updateBonsterScale`. |

#### `updateCloth`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clothUpdater |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Fonctionnement | Endpoint AMF `updateCloth`. |

#### `updateMusic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | copy |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `TreeBasedShopEditor.as` |
| Fonctionnement | Endpoint AMF `updateMusic`. |

#### `uploadBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | templateName, templateId, armatureName, price, diamondsPrice, isVIP, deleted, specialEggCrate, scale, scaleWeb |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / appelants | `BonsterUploader.as` |
| Fonctionnement | Endpoint AMF `uploadBonster`. |

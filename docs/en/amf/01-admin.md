# III.1 — Administration & infrastructure

> **EN** · [Français](../../fr/amf/01-admin.md)


Moderation, content upload, logging, OS Check, shop tags/themes.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `LikeAdd` | `AMFCommonService` | `fameEarned` | Yes |
| `SaveRoomWithSnapshot` | `AMFRoomService` | `entier` | Yes |

## `WebService.AMFCommonService`

**AMF path:** `MovieStarPlanet.WebService.AMFCommonService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `ActorHasLiked` | param3, param1, param2 | AMF endpoint `ActorHasLiked`. | — |
| `LikeAdd` | entityType, entityId, selfActorId, receiver | Like générique (film, look, etc.) ; `fameEarned==-429`. | `-429` |
| `LogChat` | param1, param2, param3, InputLocations.DESTINATION_TYPE_USER | AMF endpoint `LogChat`. | — |
| `LogInput` | roomId, actorId, roomInstanceId, message, destinationType | AMF endpoint `LogInput`. | — |
| `SendContentEmail` | param1, param2, param3, param4, param5 | AMF endpoint `SendContentEmail`. | — |
| `getNowAsString` | — | AMF endpoint `getNowAsString`. | — |

### Endpoint details

#### `ActorHasLiked`

| Property | Value |
|----------|-------|
| Parameters | param3, param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` |
| Behavior | AMF endpoint `ActorHasLiked`. |

#### `LikeAdd`

| Property | Value |
|----------|-------|
| Parameters | entityType, entityId, selfActorId, receiver |
| AMF ticket | Yes |
| Rate limit | `-429` on `fameEarned` (popup) |
| Return codes | Champ `fameEarned` == −429 (popup) |
| AMF client | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` (+1) |
| UI / callers | `MyLooksEditor.as`, `ChatRoomFlexApps.as`, `LikeDesignCommand.as`, `WAYDListItemRenderer.as` (+2) |
| Behavior | Like générique (film, look, etc.) ; `fameEarned==-429`. |

#### `LogChat`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, InputLocations.DESTINATION_TYPE_USER |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` |
| Behavior | AMF endpoint `LogChat`. |

#### `LogInput`

| Property | Value |
|----------|-------|
| Parameters | roomId, actorId, roomInstanceId, message, destinationType |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` (+2) |
| UI / callers | `ManageClub.as`, `CommentNewComponent.as`, `MonsterPopup.as`, `MyLooksEditor.as` (+21) |
| Behavior | AMF endpoint `LogInput`. |

#### `SendContentEmail`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` (+1) |
| UI / callers | `SendContentAsMailPopup.as` |
| Behavior | AMF endpoint `SendContentEmail`. |

#### `getNowAsString`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/mobileservices/CommonAmfService.as` |
| Behavior | AMF endpoint `getNowAsString`. |

## `WebService.Admin.AMFAdminService`

**AMF path:** `MovieStarPlanet.WebService.Admin.AMFAdminService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BlockName` | param1, param2, param3 | AMF endpoint `BlockName`. | — |
| `ClearCache` | param1, param2, true | AMF endpoint `ClearCache`. | — |
| `ClearNewMarkings` | param1, param2 | AMF endpoint `ClearNewMarkings`. | — |
| `DeleteTwitterText` | param1, param2, param3 | Deletes e twitter text. | — |
| `GetActorLocale` | param1 | Fetches actor locale. | — |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize | Fetches all gifts given. | — |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize | Fetches all gifts received. | — |
| `GetBadWordActorList` | pageIndex, pageSize | Fetches bad word actor list. | — |
| `GetBlockedIP` | ipAsInt, moderatorName, moderatorPass | Fetches blocked ip. | — |
| `GetBlockedInfo` | ipAsInt, moderatorName, moderatorPass | Fetches blocked info. | — |
| `GetBlockedNames` | searchphrase | Fetches blocked names. | — |
| `GetChatLogList` | actorId, pageIndex, pageSize | Fetches chat log list. | — |
| `GetChatLogListByReportTime` | paramObj.actorId, paramObj.reportId, pageIndex, pageSize | Fetches chat log list by report time. | — |
| `GetChatLogListLocked` | actorId | Fetches chat log list locked. | — |
| `GetIPLoginType` | ipAsIntToUse, moderatorName, moderatorPass | Fetches iplogin type. | — |
| `GetIPUsers` | ipAsIntToUse, moderatorName, moderatorPass | Fetches ipusers. | — |
| `GetIPWarnings` | ipAsIntToUse, moderatorName, moderatorPass | Fetches ipwarnings. | — |
| `GetLocaleResources` | param1, param2, param3, param4, param5 | Fetches locale resources. | — |
| `GetLoginHistory` | param1, param2, param3 | Fetches login history. | — |
| `GetModeratorList` | pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass | Fetches moderator list. | — |
| `GetModeratorWarningCount` | paramObj.moderatorId, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass | Fetches moderator warning count. | — |
| `GetModeratorWarnings` | paramObj.moderatorId, paramObj.date, pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword | Fetches moderator warnings. | — |
| `GetReportList` | onlyGetNotHandled, pageIndex, pageSize | Fetches report list. | — |
| `GetReportOverview` | — | Fetches report overview. | — |
| `GetSecureModuleUrl` | — | Fetches secure module url. | — |
| `GetTotalModeratorActivitiesDone` | actorId, moderatorName, moderatorPass | Fetches total moderator activities done. | — |
| `GetWarnedIPListNew` | paramObj.blocked, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass, paramObj.specificIp ? paramObj.specificIp : 0 | Fetches warned iplist new. | — |
| `GetWarningLog` | pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword | Fetches warning log. | — |
| `GiveAutoWarning` | param1, param2, param3, param4 | AMF endpoint `GiveAutoWarning`. | — |
| `IsAdminSite` | param1, param2 | AMF endpoint `IsAdminSite`. | — |
| `IsUploadSite` | — | AMF endpoint `IsUploadSite`. | — |
| `LockOutUser` | param1, param2, param3, param4, param5 | AMF endpoint `LockOutUser`. | — |
| `RemoveRoboBlastContent` | actorId, contentType, contentId, reporterId, site | Deletes e robo blast content. | — |
| `ReportHandled` | reportId, handledByActorId | AMF endpoint `ReportHandled`. | — |
| `SaveLocaleResources` | param1 | Saves / creates save locale resources. | — |
| `UnblockName` | param1, param2, param3 | AMF endpoint `UnblockName`. | — |
| `blockIP` | ipAsIntToBlock, moderatorActorId, moderatorName, moderatorPass, blockingDaysCount, comment | AMF endpoint `blockIP`. | — |
| `deleteMovieViaProfile` | movieId, moderatorName, moderatorPass | AMF endpoint `deleteMovieViaProfile`. | — |
| `getChatRoomOpenCloseTimes` | — | AMF endpoint `getChatRoomOpenCloseTimes`. | — |
| `isIPBlockedNew` | ipAsIntToFind, moderatorName, moderatorPass | AMF endpoint `isIPBlockedNew`. | — |
| `markIpAsPublic` | ipAsIntToMark, moderatorName, moderatorPass | AMF endpoint `markIpAsPublic`. | — |
| `saveSpamReport` | spamtext, moderatorActorId, moderatorName, moderatorPass | AMF endpoint `saveSpamReport`. | — |
| `setChatRoomOpenCloseTimes` | open, close | AMF endpoint `setChatRoomOpenCloseTimes`. | — |
| `unblockIP` | ipAsIntToUnblock, moderatorID, moderatorName, moderatorPass, comment | AMF endpoint `unblockIP`. | — |
| `unmarkIpAsPublic` | ipAsIntToUnmark, moderatorName, moderatorPass | AMF endpoint `unmarkIpAsPublic`. | — |

### Endpoint details

#### `BlockName`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `BlockedNames.as` |
| Behavior | AMF endpoint `BlockName`. |

#### `ClearCache`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, true |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `CommentsComponent.as`, `UploadClothes.as`, `MSP_InventoryContainer.as`, `Admin.as` (+11) |
| Behavior | AMF endpoint `ClearCache`. |

#### `ClearNewMarkings`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | AMF endpoint `ClearNewMarkings`. |

#### `DeleteTwitterText`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `AdminDeleteButton.as` |
| Behavior | Deletes e twitter text. |

#### `GetActorLocale`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `UserAdmin.as` |
| Behavior | Fetches actor locale. |

#### `GetAllGiftsGiven`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` (+1) |
| UI / callers | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Behavior | Fetches all gifts given. |

#### `GetAllGiftsReceived`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` (+1) |
| UI / callers | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Behavior | Fetches all gifts received. |

#### `GetBadWordActorList`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches bad word actor list. |

#### `GetBlockedIP`

| Property | Value |
|----------|-------|
| Parameters | ipAsInt, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches blocked ip. |

#### `GetBlockedInfo`

| Property | Value |
|----------|-------|
| Parameters | ipAsInt, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `BlockedIPInfoForm.as` |
| Behavior | Fetches blocked info. |

#### `GetBlockedNames`

| Property | Value |
|----------|-------|
| Parameters | searchphrase |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `BlockedNames.as` |
| Behavior | Fetches blocked names. |

#### `GetChatLogList`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches chat log list. |

#### `GetChatLogListByReportTime`

| Property | Value |
|----------|-------|
| Parameters | paramObj.actorId, paramObj.reportId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches chat log list by report time. |

#### `GetChatLogListLocked`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches chat log list locked. |

#### `GetIPLoginType`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToUse, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as` |
| Behavior | Fetches iplogin type. |

#### `GetIPUsers`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToUse, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as` |
| Behavior | Fetches ipusers. |

#### `GetIPWarnings`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToUse, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as` |
| Behavior | Fetches ipwarnings. |

#### `GetLocaleResources`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `LocaleEditor.as`, `LocaleProvider.as`, `MovieCompetitionPublisherItem.as`, `PollEditorItem.as` |
| Behavior | Fetches locale resources. |

#### `GetLoginHistory`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches login history. |

#### `GetModeratorList`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches moderator list. |

#### `GetModeratorWarningCount`

| Property | Value |
|----------|-------|
| Parameters | paramObj.moderatorId, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `ModeratorList.as` |
| Behavior | Fetches moderator warning count. |

#### `GetModeratorWarnings`

| Property | Value |
|----------|-------|
| Parameters | paramObj.moderatorId, paramObj.date, pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `ModeratorList.as` |
| Behavior | Fetches moderator warnings. |

#### `GetReportList`

| Property | Value |
|----------|-------|
| Parameters | onlyGetNotHandled, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches report list. |

#### `GetReportOverview`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `UpdateReportOverviewCommand.as` |
| Behavior | Fetches report overview. |

#### `GetSecureModuleUrl`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Fetches secure module url. |

#### `GetTotalModeratorActivitiesDone`

| Property | Value |
|----------|-------|
| Parameters | actorId, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `ModeratorList.as` |
| Behavior | Fetches total moderator activities done. |

#### `GetWarnedIPListNew`

| Property | Value |
|----------|-------|
| Parameters | paramObj.blocked, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass, paramObj.specificIp ? paramObj.specificIp : 0 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as` |
| Behavior | Fetches warned iplist new. |

#### `GetWarningLog`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `WarningListForm.as` |
| Behavior | Fetches warning log. |

#### `GiveAutoWarning`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `ClubView.as`, `AdminDeleteButton.as`, `MovieHighScoreComponent.as`, `LookCommentItemComponent.as` (+18) |
| Behavior | AMF endpoint `GiveAutoWarning`. |

#### `IsAdminSite`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `Admin.as`, `SpendingServiceSettings.as`, `AnimationShopView.as`, `ClothesShopModel.as` (+4) |
| Behavior | AMF endpoint `IsAdminSite`. |

#### `IsUploadSite`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `Admin.as` |
| Behavior | AMF endpoint `IsUploadSite`. |

#### `LockOutUser`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` (+1) |
| UI / callers | `AdminManager.as`, `UserBehaviorServiceSettings.as` |
| Behavior | AMF endpoint `LockOutUser`. |

#### `RemoveRoboBlastContent`

| Property | Value |
|----------|-------|
| Parameters | actorId, contentType, contentId, reporterId, site |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| Behavior | Deletes e robo blast content. |

#### `ReportHandled`

| Property | Value |
|----------|-------|
| Parameters | reportId, handledByActorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `NebulaMsgServiceMessageTypes.as` |
| Behavior | AMF endpoint `ReportHandled`. |

#### `SaveLocaleResources`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `LocaleEditor.as`, `LocaleProvider.as`, `PollEditorItem.as` |
| Behavior | Saves / creates save locale resources. |

#### `UnblockName`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `BlockedNames.as` |
| Behavior | AMF endpoint `UnblockName`. |

#### `blockIP`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToBlock, moderatorActorId, moderatorName, moderatorPass, blockingDaysCount, comment |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as`, `TempIPBlockingForm.as` |
| Behavior | AMF endpoint `blockIP`. |

#### `deleteMovieViaProfile`

| Property | Value |
|----------|-------|
| Parameters | movieId, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `MovieHighScoreComponent.as`, `MovieContentListItemRenderer.as`, `MovieSocialListItemRenderer.as` |
| Behavior | AMF endpoint `deleteMovieViaProfile`. |

#### `getChatRoomOpenCloseTimes`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `ChatRoomCloseTimePanel.as` |
| Behavior | AMF endpoint `getChatRoomOpenCloseTimes`. |

#### `isIPBlockedNew`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToFind, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as` |
| Behavior | AMF endpoint `isIPBlockedNew`. |

#### `markIpAsPublic`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToMark, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as` |
| Behavior | AMF endpoint `markIpAsPublic`. |

#### `saveSpamReport`

| Property | Value |
|----------|-------|
| Parameters | spamtext, moderatorActorId, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `ReportSpamForm.as` |
| Behavior | AMF endpoint `saveSpamReport`. |

#### `setChatRoomOpenCloseTimes`

| Property | Value |
|----------|-------|
| Parameters | open, close |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `ChatRoomCloseTimePanel.as` |
| Behavior | AMF endpoint `setChatRoomOpenCloseTimes`. |

#### `unblockIP`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToUnblock, moderatorID, moderatorName, moderatorPass, comment |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as`, `TempIPBlockingForm.as` |
| Behavior | AMF endpoint `unblockIP`. |

#### `unmarkIpAsPublic`

| Property | Value |
|----------|-------|
| Parameters | ipAsIntToUnmark, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/service/AdminAMFService.as` |
| UI / callers | `IPWarnedList.as` |
| Behavior | AMF endpoint `unmarkIpAsPublic`. |

## `WebService.AnimationSnapshot.AMFAnimationSnapshotService`

**AMF path:** `MovieStarPlanet.WebService.AnimationSnapshot.AMFAnimationSnapshotService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `getAnimationNames` | — | AMF endpoint `getAnimationNames`. | — |
| `saveImage` | data, name | AMF endpoint `saveImage`. | — |

### Endpoint details

#### `getAnimationNames`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/controller/SaveAnimationSnapshotCommand.as` |
| UI / callers | `TestingForm.as` |
| Behavior | AMF endpoint `getAnimationNames`. |

#### `saveImage`

| Property | Value |
|----------|-------|
| Parameters | data, name |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/controller/SaveAnimationSnapshotCommand.as` |
| Behavior | AMF endpoint `saveImage`. |

## `WebService.Common.AMFCommonWebService`

**AMF path:** `MovieStarPlanet.WebService.Common.AMFCommonWebService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetEntityName` | param1, param2 | Fetches entity name. | — |
| `GetPlaylistExternalRef` | param1 | Fetches playlist external ref. | — |
| `LikeAdd` | entityType, entityId, actorId, receiverId | Like générique (film, look, etc.) ; `fameEarned==-429`. | `-429` |
| `SaveRoomWithSnapshot` | actorId, roomData, snapshots[3] | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. | `-429` |
| `SendContentEmail` | param1, param2, param3, param4, param5 | AMF endpoint `SendContentEmail`. | — |

### Endpoint details

#### `GetEntityName`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` |
| UI / callers | `Favorites.as` |
| Behavior | Fetches entity name. |

#### `GetPlaylistExternalRef`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` |
| UI / callers | `Favorites.as` |
| Behavior | Fetches playlist external ref. |

#### `LikeAdd`

| Property | Value |
|----------|-------|
| Parameters | entityType, entityId, actorId, receiverId |
| AMF ticket | Yes |
| Rate limit | `-429` on `fameEarned` (popup) |
| Return codes | Champ `fameEarned` == −429 (popup) |
| AMF client | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` (+1) |
| UI / callers | `MyLooksEditor.as`, `ChatRoomFlexApps.as`, `LikeDesignCommand.as`, `WAYDListItemRenderer.as` (+2) |
| Behavior | Like générique (film, look, etc.) ; `fameEarned==-429`. |

#### `SaveRoomWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | actorId, roomData, snapshots[3] |
| AMF ticket | Yes |
| Rate limit | `-429` on `entier` (popup) |
| Return codes | Champ `entier` == −429 (popup) |
| AMF client | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` (+1) |
| UI / callers | `EditMyRoom.as`, `StuffView.as`, `SaveMyRoomCommand.as` |
| Behavior | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. |

#### `SendContentEmail`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/commonservice/CommonAmfWebService.as` (+1) |
| UI / callers | `SendContentAsMailPopup.as` |
| Behavior | AMF endpoint `SendContentEmail`. |

## `WebService.Logging.AMFLoggingService`

**AMF path:** `MovieStarPlanet.WebService.Logging.AMFLoggingService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `ClientLog` | param1, param2 | AMF endpoint `ClientLog`. | — |
| `CreateTestException` | — | Saves / creates create test exception. | — |
| `GetLatestServerException` | — | Fetches latest server exception. | — |
| `LogClient` | param1, param2 | AMF endpoint `LogClient`. | — |

### Endpoint details

#### `ClientLog`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| Behavior | AMF endpoint `ClientLog`. |

#### `CreateTestException`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| Behavior | Saves / creates create test exception. |

#### `GetLatestServerException`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| UI / callers | `GetLatestErrorCommand.as` |
| Behavior | Fetches latest server exception. |

#### `LogClient`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/logging/services/loggingservice/LoggingAmfService.as` |
| UI / callers | `ChecksumCalculator.as`, `SetupAppSettingsCommand.as`, `Log.as`, `PlaybackSession.as` |
| Behavior | AMF endpoint `LogClient`. |

## `WebService.Moderation.AMFModeration`

**AMF path:** `MovieStarPlanet.WebService.Moderation.AMFModeration`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CheckNewUsername` | userName, this._site | Checks new username. | — |
| `FilterText` | (param1, param5, param4, param2, param3) · (param1, param5, param4, param2, param3, param8, param9) | AMF endpoint `FilterText`. | — |
| `LoginEvent` | param1 | AMF endpoint `LoginEvent`. | — |
| `ReportUser` | param2, param3, param4, param6, this._site, param7 | AMF endpoint `ReportUser`. | — |
| `ReportUserNeb` | param2, param5, param4, param6 | AMF endpoint `ReportUserNeb`. | — |

### Endpoint details

#### `CheckNewUsername`

| Property | Value |
|----------|-------|
| Parameters | userName, this._site |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| Behavior | Checks new username. |

#### `FilterText`

| Property | Value |
|----------|-------|
| Parameters | (param1, param5, param4, param2, param3) · (param1, param5, param4, param2, param3, param8, param9) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| UI / callers | `TwitterConfig.as`, `ChatListener.as`, `Censor.as`, `YTBlackListUtil.as` (+8) |
| Behavior | AMF endpoint `FilterText`. |

#### `LoginEvent`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| UI / callers | `ChatListener.as`, `LoginRequiredSetupCommand.as`, `TextModerationHandler.as`, `FriendNotificationChannel.as` (+2) |
| Behavior | AMF endpoint `LoginEvent`. |

#### `ReportUser`

| Property | Value |
|----------|-------|
| Parameters | param2, param3, param4, param6, this._site, param7 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| UI / callers | `CharacterPopUp.as`, `NewReport.as`, `SetupAnalyticsAfterLoginCommand.as`, `TextModerationHandler.as` |
| Behavior | AMF endpoint `ReportUser`. |

#### `ReportUserNeb`

| Property | Value |
|----------|-------|
| Parameters | param2, param5, param4, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/UserBehaviorAmfService.as` |
| Behavior | AMF endpoint `ReportUserNeb`. |

## `WebService.Os.AMFOs`

**AMF path:** `MovieStarPlanet.WebService.Os.AMFOs`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CreateOsRef` | — | Démarre OS Check ; exempt checksum requête. | — |
| `RunOsCheck` | refId, hist.join(":") | Valide histogramme environnement ; exempt checksum. | — |

### Endpoint details

#### `CreateOsRef`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/snapshot/SnapLoader.as` |
| UI / callers | `AmfCaller.as`, `ChecksumCalculator.as` |
| Behavior | Démarre OS Check ; exempt checksum requête. |

#### `RunOsCheck`

| Property | Value |
|----------|-------|
| Parameters | refId, hist.join(":") |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/snapshot/SnapLoader.as` |
| UI / callers | `AmfCaller.as`, `ChecksumCalculator.as` |
| Behavior | Valide histogramme environnement ; exempt checksum. |

## `WebService.PerformanceTracking.AMFPerformanceTrackingService`

**AMF path:** `MovieStarPlanet.WebService.PerformanceTracking.AMFPerformanceTrackingService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AddEntry` | param1, param2 | AMF endpoint `AddEntry`. | — |

### Endpoint details

#### `AddEntry`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/utils/performance/PerformanceTrackingAmfService.as` |
| UI / callers | `SquigglyDictionary.as`, `PerformanceLogger.as` |
| Behavior | AMF endpoint `AddEntry`. |

## `WebService.Snapshots.AMFGenericSnapshotService`

**AMF path:** `MovieStarPlanet.WebService.Snapshots.AMFGenericSnapshotService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CreateSnapshot` | (param1, param2, param3, param4) · (param1, param2, param3, param4, param5) | Saves / creates create snapshot. | — |
| `CreateSnapshotSmallAndBig` | param1, param2, param3, param4, param5, param6 | Saves / creates create snapshot small and big. | — |

### Endpoint details

#### `CreateSnapshot`

| Property | Value |
|----------|-------|
| Parameters | (param1, param2, param3, param4) · (param1, param2, param3, param4, param5) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/snapshotservice/GenericSnapshotAMFService.as` |
| UI / callers | `PublicProfile.as`, `ChatRoomFlexApps.as`, `RegisterNewUserComponent.as`, `UserInfoInteractionTheme.as` (+9) |
| Behavior | Saves / creates create snapshot. |

#### `CreateSnapshotSmallAndBig`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/snapshotservice/GenericSnapshotAMFService.as` |
| UI / callers | `SaveClothesCommand.as`, `BeautyClinicBuyCommand.as`, `BeautyClinicWearCommand.as` |
| Behavior | Saves / creates create snapshot small and big. |

## `WebService.TagManager.AMFTagManager`

**AMF path:** `MovieStarPlanet.WebService.TagManager.AMFTagManager`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `DeleteTag` | param1 | Deletes e tag. | — |
| `GetAllTags` | — | Fetches all tags. | — |
| `GetBackgroundTags` | — | Fetches background tags. | — |
| `GetTagsForSkinClothes` | param2 | Fetches tags for skin clothes. | — |
| `GetTagsInCategorySkin` | param2, param3 | Fetches tags in category skin. | — |
| `SaveTag` | param1 | Saves / creates save tag. | — |

### Endpoint details

#### `DeleteTag`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / callers | `TagManager.as` |
| Behavior | Deletes e tag. |

#### `GetAllTags`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / callers | `TagManager.as`, `UploadClothes.as`, `SettingsManager.as` |
| Behavior | Fetches all tags. |

#### `GetBackgroundTags`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / callers | `BackgroundTagService.as`, `BackgroundUtil.as` |
| Behavior | Fetches background tags. |

#### `GetTagsForSkinClothes`

| Property | Value |
|----------|-------|
| Parameters | param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| Behavior | Fetches tags for skin clothes. |

#### `GetTagsInCategorySkin`

| Property | Value |
|----------|-------|
| Parameters | param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / callers | `TagSelector.as` |
| Behavior | Fetches tags in category skin. |

#### `SaveTag`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/TagAMFManager.as` |
| UI / callers | `TagManager.as` |
| Behavior | Saves / creates save tag. |

## `WebService.ThemeManager.AMFThemeManagerService`

**AMF path:** `MovieStarPlanet.WebService.ThemeManager.AMFThemeManagerService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `DeleteTheme` | param1 | Deletes e theme. | — |
| `GetAllCampaigns` | — | Fetches all campaigns. | — |
| `GetAllThemes` | — | Fetches all themes. | — |
| `GetCurrectNewCategorySortIndex` | — | Fetches currect new category sort index. | — |
| `InsertTheme` | param1, param2, param3, param4 | AMF endpoint `InsertTheme`. | — |
| `LabelClothesWithTheme` | param1, param2 | AMF endpoint `LabelClothesWithTheme`. | — |
| `RetrieveThemeID` | param1, param2 | AMF endpoint `RetrieveThemeID`. | — |
| `SortShoppingItems` | param1, param2, param3 | AMF endpoint `SortShoppingItems`. | — |
| `UpdateTheme` | param1 | Updates ate theme. | — |

### Endpoint details

#### `DeleteTheme`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `ThemeManagerForm.as`, `WorldThemeManager.as` |
| Behavior | Deletes e theme. |

#### `GetAllCampaigns`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| Behavior | Fetches all campaigns. |

#### `GetAllThemes`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `ClothSortingList.as`, `FacepartUploader.as`, `ThemeManagerForm.as`, `TreeBasedShopEditor.as` (+7) |
| Behavior | Fetches all themes. |

#### `GetCurrectNewCategorySortIndex`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `Admin.as` |
| Behavior | Fetches currect new category sort index. |

#### `InsertTheme`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `CreateThemeForm.as` |
| Behavior | AMF endpoint `InsertTheme`. |

#### `LabelClothesWithTheme`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `ClothSortingList.as` |
| Behavior | AMF endpoint `LabelClothesWithTheme`. |

#### `RetrieveThemeID`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `TreeBasedShopEditor.as`, `EditOrDeleteAnimation.as` |
| Behavior | AMF endpoint `RetrieveThemeID`. |

#### `SortShoppingItems`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `ClothSortingList.as` |
| Behavior | AMF endpoint `SortShoppingItems`. |

#### `UpdateTheme`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Forms/upload/worldthememanager/ThemeManagerAmfService.as` |
| UI / callers | `CreateThemeForm.as`, `ThemeManagerForm.as`, `FlashHiddenShop.as` |
| Behavior | Updates ate theme. |

## `WebService.Upload.AMFUploadService`

**AMF path:** `MovieStarPlanet.WebService.Upload.AMFUploadService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CheckAnimationExists` | animationName | Checks animation exists. | — |
| `DeleteClipArt` | clipart, subpath | Deletes e clip art. | — |
| `DeleteFacepart` | facepartId, type | Deletes e facepart. | — |
| `DeleteWallpaper` | wallpaperId | Deletes e wallpaper. | — |
| `EditAnimation` | animationId, name, price, discount, checkVip, checkNew, checkDeleted, animCategoryId, themeID, priceDiamonds | AMF endpoint `EditAnimation`. | — |
| `EditClipArt` | clipart, subpath, sort, checkvip, checknew, price, diamondsPrice | AMF endpoint `EditClipArt`. | — |
| `EditFacepart` | facepartId, type, gender, name, fileName, price, checkvip, checknew, checkreg, discount, sortorder, themeID, priceDiamonds | AMF endpoint `EditFacepart`. | — |
| `FileExistsCheck` | key | AMF endpoint `FileExistsCheck`. | — |
| `GetAnimationCategories` | — | Fetches animation categories. | — |
| `GetClipArtPath` | clipart | Fetches clip art path. | — |
| `InsertAnimation` | name, price, diamondsprice, animCategory, vip, fileName, themeID | AMF endpoint `InsertAnimation`. | — |
| `InsertBackground` | name, price, backgroundCategory, vip, fileName, themeID | AMF endpoint `InsertBackground`. | — |
| `InsertClipArt` | type, category, fileName, checkvip, checkNew, sortorder, price, diamondPrice, colorScheme | AMF endpoint `InsertClipArt`. | — |
| `InsertFacepart` | type, gender, name, fileName, price, diamondPrice, checkvip, dragonBone, defaultColors, checknew, checkreg, discount, sortorder, themeID, date, hidden | AMF endpoint `InsertFacepart`. | — |
| `InsertWallpaper` | type, roomtype, name, filepath | AMF endpoint `InsertWallpaper`. | — |
| `getAllColorschemelessClothes` | pageIdx, pageSize | AMF endpoint `getAllColorschemelessClothes`. | — |
| `getBonsterInfo` | templateName | AMF endpoint `getBonsterInfo`. | — |
| `getClipArtCategoryNames` | paramid | AMF endpoint `getClipArtCategoryNames`. | — |
| `getClipArtTypes` | — | AMF endpoint `getClipArtTypes`. | — |
| `giveBonster` | templateName | AMF endpoint `giveBonster`. | — |
| `saveClothUpdater` | cloth, themeID | AMF endpoint `saveClothUpdater`. | — |
| `setClothColorSchemes` | ([colorSchemeObject) · (clothColorSchemes) | AMF endpoint `setClothColorSchemes`. | — |
| `updateAnimation` | copy, themeID | AMF endpoint `updateAnimation`. | — |
| `updateBackground` | copy, themeID | AMF endpoint `updateBackground`. | — |
| `updateBonsterColors` | bonsterId, colorMatrix | AMF endpoint `updateBonsterColors`. | — |
| `updateBonsterScale` | bonsterId, mobScale, webScale | AMF endpoint `updateBonsterScale`. | — |
| `updateCloth` | clothUpdater | AMF endpoint `updateCloth`. | — |
| `updateMusic` | copy | AMF endpoint `updateMusic`. | — |
| `uploadBonster` | templateName, templateId, armatureName, price, diamondsPrice, isVIP, deleted, specialEggCrate, scale, scaleWeb | AMF endpoint `uploadBonster`. | — |

### Endpoint details

#### `CheckAnimationExists`

| Property | Value |
|----------|-------|
| Parameters | animationName |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `UploadAnimation.as` |
| Behavior | Checks animation exists. |

#### `DeleteClipArt`

| Property | Value |
|----------|-------|
| Parameters | clipart, subpath |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `EditOrDeleteClipArt.as` |
| Behavior | Deletes e clip art. |

#### `DeleteFacepart`

| Property | Value |
|----------|-------|
| Parameters | facepartId, type |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Behavior | Deletes e facepart. |

#### `DeleteWallpaper`

| Property | Value |
|----------|-------|
| Parameters | wallpaperId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `DeleteWallpaper.as`, `UploadWallpaper.as` |
| Behavior | Deletes e wallpaper. |

#### `EditAnimation`

| Property | Value |
|----------|-------|
| Parameters | animationId, name, price, discount, checkVip, checkNew, checkDeleted, animCategoryId, themeID, priceDiamonds |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `EditOrDeleteAnimation.as` |
| Behavior | AMF endpoint `EditAnimation`. |

#### `EditClipArt`

| Property | Value |
|----------|-------|
| Parameters | clipart, subpath, sort, checkvip, checknew, price, diamondsPrice |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `EditOrDeleteClipArt.as`, `ArtBookCreatorFrame.as` |
| Behavior | AMF endpoint `EditClipArt`. |

#### `EditFacepart`

| Property | Value |
|----------|-------|
| Parameters | facepartId, type, gender, name, fileName, price, checkvip, checknew, checkreg, discount, sortorder, themeID, priceDiamonds |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `AdminManager.as`, `AdminManagerEntry.as`, `ShoppingOperator.as` |
| Behavior | AMF endpoint `EditFacepart`. |

#### `FileExistsCheck`

| Property | Value |
|----------|-------|
| Parameters | key |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `BonsterUploader.as`, `CreateThemeForm.as`, `FacepartUploader.as`, `EditOrDeleteClipArt.as` (+8) |
| Behavior | AMF endpoint `FileExistsCheck`. |

#### `GetAnimationCategories`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `EditOrDeleteAnimation.as`, `UploadAnimation.as`, `ChatRoomAnimationSelector.as` |
| Behavior | Fetches animation categories. |

#### `GetClipArtPath`

| Property | Value |
|----------|-------|
| Parameters | clipart |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Behavior | Fetches clip art path. |

#### `InsertAnimation`

| Property | Value |
|----------|-------|
| Parameters | name, price, diamondsprice, animCategory, vip, fileName, themeID |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `UploadAnimation.as` |
| Behavior | AMF endpoint `InsertAnimation`. |

#### `InsertBackground`

| Property | Value |
|----------|-------|
| Parameters | name, price, backgroundCategory, vip, fileName, themeID |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `UploadBackgroundLogic.as`, `ScrapBlogNewsEditor.as`, `ShopContentAmfService.as`, `ShopContentProvider.as` |
| Behavior | AMF endpoint `InsertBackground`. |

#### `InsertClipArt`

| Property | Value |
|----------|-------|
| Parameters | type, category, fileName, checkvip, checkNew, sortorder, price, diamondPrice, colorScheme |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `UploadClipArt.as` |
| Behavior | AMF endpoint `InsertClipArt`. |

#### `InsertFacepart`

| Property | Value |
|----------|-------|
| Parameters | type, gender, name, fileName, price, diamondPrice, checkvip, dragonBone, defaultColors, checknew, checkreg, discount, sortorder, themeID, date, hidden |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `FacepartUploader.as` |
| Behavior | AMF endpoint `InsertFacepart`. |

#### `InsertWallpaper`

| Property | Value |
|----------|-------|
| Parameters | type, roomtype, name, filepath |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `UploadWallpaper.as` |
| Behavior | AMF endpoint `InsertWallpaper`. |

#### `getAllColorschemelessClothes`

| Property | Value |
|----------|-------|
| Parameters | pageIdx, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `ClothColorParser.as` |
| Behavior | AMF endpoint `getAllColorschemelessClothes`. |

#### `getBonsterInfo`

| Property | Value |
|----------|-------|
| Parameters | templateName |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `BonsterTester.as` |
| Behavior | AMF endpoint `getBonsterInfo`. |

#### `getClipArtCategoryNames`

| Property | Value |
|----------|-------|
| Parameters | paramid |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `UploadClipArt.as` |
| Behavior | AMF endpoint `getClipArtCategoryNames`. |

#### `getClipArtTypes`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `UploadClipArt.as` |
| Behavior | AMF endpoint `getClipArtTypes`. |

#### `giveBonster`

| Property | Value |
|----------|-------|
| Parameters | templateName |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Behavior | AMF endpoint `giveBonster`. |

#### `saveClothUpdater`

| Property | Value |
|----------|-------|
| Parameters | cloth, themeID |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Behavior | AMF endpoint `saveClothUpdater`. |

#### `setClothColorSchemes`

| Property | Value |
|----------|-------|
| Parameters | ([colorSchemeObject) · (clothColorSchemes) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `ClothColorParser.as`, `ClothesShopController.as`, `ClothColorSchemeObject.as` |
| Behavior | AMF endpoint `setClothColorSchemes`. |

#### `updateAnimation`

| Property | Value |
|----------|-------|
| Parameters | copy, themeID |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `TreeBasedShopEditor.as`, `CategoryViewMediator.as`, `PreviewAnimation.as`, `Armature.as` |
| Behavior | AMF endpoint `updateAnimation`. |

#### `updateBackground`

| Property | Value |
|----------|-------|
| Parameters | copy, themeID |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `TreeBasedShopEditor.as`, `UploadBackgroundLogic.as`, `FrameViewMediator.as`, `DynamicPopup.as` (+3) |
| Behavior | AMF endpoint `updateBackground`. |

#### `updateBonsterColors`

| Property | Value |
|----------|-------|
| Parameters | bonsterId, colorMatrix |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Behavior | AMF endpoint `updateBonsterColors`. |

#### `updateBonsterScale`

| Property | Value |
|----------|-------|
| Parameters | bonsterId, mobScale, webScale |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Behavior | AMF endpoint `updateBonsterScale`. |

#### `updateCloth`

| Property | Value |
|----------|-------|
| Parameters | clothUpdater |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| Behavior | AMF endpoint `updateCloth`. |

#### `updateMusic`

| Property | Value |
|----------|-------|
| Parameters | copy |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `TreeBasedShopEditor.as` |
| Behavior | AMF endpoint `updateMusic`. |

#### `uploadBonster`

| Property | Value |
|----------|-------|
| Parameters | templateName, templateId, armatureName, price, diamondsPrice, isVIP, deleted, specialEggCrate, scale, scaleWeb |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/admin/uploadservice/AMFUploadService.as` |
| UI / callers | `BonsterUploader.as` |
| Behavior | AMF endpoint `uploadBonster`. |

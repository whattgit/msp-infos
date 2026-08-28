# III.10 — Social

> **EN** · [Français](../../fr/amf/10-social.md)


Friends, profile, messaging, school, anchor characters.

## Response codes

| Code `GetFriendShipStatus` | Meaning |
|---------------------------|---------------|
| `0` | Same user |
| `1` | Not friends |
| `2` | Amis |
| `3` | Request sent, pending |
| `4` | Request received |
| `5–6` | Boyfriend/girlfriend |
| `9` | Best friend |

## `WebService.AMFMessageService`

**AMF path:** `MovieStarPlanet.WebService.AMFMessageService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetMessagingActors` | ([id) · (param1) | Fetches messaging actors. | — |
| `IsCommunicationAllowedWith` | param1, param2 | AMF endpoint `IsCommunicationAllowedWith`. | — |
| `SendChatMessageWithModerationCall` | param1, param2, param3, param4, param5, param6 | AMF endpoint `SendChatMessageWithModerationCall`. | — |
| `SendOneToOneOrGroupChatMessage` | Number(param2), param8, param3, param6, _loc13_, param4 | AMF endpoint `SendOneToOneOrGroupChatMessage`. | — |
| `SetMessengerSession` | param1 | Updates messenger session. | — |

### Endpoint details

#### `GetMessagingActors`

| Property | Value |
|----------|-------|
| Parameters | ([id) · (param1) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/messaging/module/moduleparts/cache/MessagingCacheRequest.as` (+1) |
| UI / callers | `SendChatMessageService.as`, `MessagingCache.as`, `ChatView.as`, `MessagingController.as` (+5) |
| Behavior | Fetches messaging actors. |

#### `IsCommunicationAllowedWith`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` (+1) |
| UI / callers | `MessagingFacade.as`, `OneToOneChatDataItem.as`, `Wall.as` |
| Behavior | AMF endpoint `IsCommunicationAllowedWith`. |

#### `SendChatMessageWithModerationCall`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` |
| UI / callers | `SendChatMessageService.as` |
| Behavior | AMF endpoint `SendChatMessageWithModerationCall`. |

#### `SendOneToOneOrGroupChatMessage`

| Property | Value |
|----------|-------|
| Parameters | Number(param2), param8, param3, param6, _loc13_, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` |
| Behavior | AMF endpoint `SendOneToOneOrGroupChatMessage`. |

#### `SetMessengerSession`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` (+1) |
| UI / callers | `SharedRegistrator.as`, `MessagingProvider.as`, `MessengerSessionNotifier.as` |
| Behavior | Updates messenger session. |

## `WebService.AMFMobileFriendshipService`

**AMF path:** `MovieStarPlanet.WebService.AMFMobileFriendshipService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AcceptBoyfriend` | param1, param2, param3 | AMF endpoint `AcceptBoyfriend`. | — |
| `AcceptMySpecialFriend` | param1 | AMF endpoint `AcceptMySpecialFriend`. | — |
| `ApproveDefaultAnchorFriendship` | param1 | AMF endpoint `ApproveDefaultAnchorFriendship`. | — |
| `ApproveFriendship` | param1, param2 | Accepte demande d'ami. | — |
| `ApproveFriendshipNeb` | param1, param2 | AMF endpoint `ApproveFriendshipNeb`. | — |
| `AskToBeBoyFriend` | param1, param2, param3 | AMF endpoint `AskToBeBoyFriend`. | — |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 | AMF endpoint `AskToBeBoyFriendFromSchoolmate`. | — |
| `AskToBeMySpecialFriend` | param1 | AMF endpoint `AskToBeMySpecialFriend`. | — |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 | AMF endpoint `AskToBeMySpecialFriendFromSchoolmate`. | — |
| `BreakUp` | param1, param2, param3 | AMF endpoint `BreakUp`. | — |
| `DeleteFriendship` | param1, param2 | Deletes e friendship. | — |
| `DeleteFriendshipNeb` | param1, param2 | Deletes e friendship neb. | — |
| `GetActorSpecialSummary` | param1, param2 | Fetches actor special summary. | — |
| `GetFriendListWithNameAndScore` | param1 | Fetches friend list with name and score. | — |
| `GetMspRelationshipStatus` | param3, param1, param4 | Fetches msp relationship status. | — |
| `GetPagedFriendRequests` | actorId, pageIndex, pageSize | Paged list — Paged Friend Requests. | — |
| `GetRelationshipStatusNeb` | param2, param3, param4 | Fetches relationship status neb. | — |
| `RejectBoyfriend` | param1, param2, param3 | AMF endpoint `RejectBoyfriend`. | — |
| `RejectFriendShip` | param1, param2 | AMF endpoint `RejectFriendShip`. | — |
| `RejectFriendShipNeb` | param1, param2 | AMF endpoint `RejectFriendShipNeb`. | — |
| `RejectMySpecialFriend` | param1 | AMF endpoint `RejectMySpecialFriend`. | — |
| `RequestFriendship` | param1, param2 | Envoie demande d'ami ; statut via GetFriendShipStatus. | — |
| `RequestFriendshipFromSchoolmate` | param1, param2 | AMF endpoint `RequestFriendshipFromSchoolmate`. | — |
| `RequestFriendshipNeb` | param1, param2 | AMF endpoint `RequestFriendshipNeb`. | — |

### Endpoint details

#### `AcceptBoyfriend`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `BoyfriendButton.as`, `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as` (+2) |
| Behavior | AMF endpoint `AcceptBoyfriend`. |

#### `AcceptMySpecialFriend`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `AcceptMySpecialFriend`. |

#### `ApproveDefaultAnchorFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `Introduction.as` |
| Behavior | AMF endpoint `ApproveDefaultAnchorFriendship`. |

#### `ApproveFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Behavior | Accepte demande d'ami. |

#### `ApproveFriendshipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipManager.as` |
| Behavior | AMF endpoint `ApproveFriendshipNeb`. |

#### `AskToBeBoyFriend`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `BoyfriendButton.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `AskToBeBoyFriend`. |

#### `AskToBeBoyFriendFromSchoolmate`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| Behavior | AMF endpoint `AskToBeBoyFriendFromSchoolmate`. |

#### `AskToBeMySpecialFriend`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `BestFriendButton.as`, `BestFriendSelector.as`, `FriendshipManager.as`, `FriendshipRegistrator.as` (+2) |
| Behavior | AMF endpoint `AskToBeMySpecialFriend`. |

#### `AskToBeMySpecialFriendFromSchoolmate`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| Behavior | AMF endpoint `AskToBeMySpecialFriendFromSchoolmate`. |

#### `BreakUp`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `BestFriendButton.as`, `BoyfriendButton.as`, `FriendshipStatusUpdater.as`, `FriendInviter.as` |
| Behavior | AMF endpoint `BreakUp`. |

#### `DeleteFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Behavior | Deletes e friendship. |

#### `DeleteFriendshipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipManager.as` |
| Behavior | Deletes e friendship neb. |

#### `GetActorSpecialSummary`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| UI / callers | `CharacterPopUp.as` |
| Behavior | Fetches actor special summary. |

#### `GetFriendListWithNameAndScore`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `MiscRegistrator.as`, `FriendsManager.as` |
| Behavior | Fetches friend list with name and score. |

#### `GetMspRelationshipStatus`

| Property | Value |
|----------|-------|
| Parameters | param3, param1, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| Behavior | Fetches msp relationship status. |

#### `GetPagedFriendRequests`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| Behavior | Paged list — Paged Friend Requests. |

#### `GetRelationshipStatusNeb`

| Property | Value |
|----------|-------|
| Parameters | param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| Behavior | Fetches relationship status neb. |

#### `RejectBoyfriend`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as`, `FriendshipStatusUpdater.as` (+1) |
| Behavior | AMF endpoint `RejectBoyfriend`. |

#### `RejectFriendShip`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `TodoSub.as`, `FriendshipStatusUpdater.as`, `FriendRequestForm.as`, `FriendRequestSponsoredCharacterForm.as` (+1) |
| Behavior | AMF endpoint `RejectFriendShip`. |

#### `RejectFriendShipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `TodoSub.as`, `FriendRequestForm.as`, `FriendInviter.as` |
| Behavior | AMF endpoint `RejectFriendShipNeb`. |

#### `RejectMySpecialFriend`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipRegistrator.as`, `IFriendshipService.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `RejectMySpecialFriend`. |

#### `RequestFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+2) |
| UI / callers | `FriendButtonSponsorCharacter.as`, `ChatRoomDragonBonesAvatarMediator.as`, `SponsorCharacterNoneFriendSub.as`, `FriendshipStatusUpdater.as` (+1) |
| Behavior | Envoie demande d'ami ; statut via GetFriendShipStatus. |

#### `RequestFriendshipFromSchoolmate`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| Behavior | AMF endpoint `RequestFriendshipFromSchoolmate`. |

#### `RequestFriendshipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / callers | `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `RequestFriendshipNeb`. |

## `WebService.AnchorCharacter.AMFAnchorCharacterService`

**AMF path:** `MovieStarPlanet.WebService.AnchorCharacter.AMFAnchorCharacterService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AcceptFriendship` | anchorCharacterId | AMF endpoint `AcceptFriendship`. | — |
| `AcceptGifts` | anchorCharacterId | AMF endpoint `AcceptGifts`. | — |
| `CancelFriendship` | anchorCharacterId | AMF endpoint `CancelFriendship`. | — |
| `GetAnchorCharacterList` | — | Fetches anchor character list. | — |
| `RequestFriendship` | anchorCharacterId | Envoie demande d'ami ; statut via GetFriendShipStatus. | — |
| `UpdateLastInviteSent` | param1, param2 | Updates ate last invite sent. | — |
| `UpdateLastStatusSeen` | param1 | Updates ate last status seen. | — |

### Endpoint details

#### `AcceptFriendship`

| Property | Value |
|----------|-------|
| Parameters | anchorCharacterId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / callers | `FriendRequestSponsoredCharacterForm.as` |
| Behavior | AMF endpoint `AcceptFriendship`. |

#### `AcceptGifts`

| Property | Value |
|----------|-------|
| Parameters | anchorCharacterId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / callers | `HandleSponsoredReactivationCommand.as` |
| Behavior | AMF endpoint `AcceptGifts`. |

#### `CancelFriendship`

| Property | Value |
|----------|-------|
| Parameters | anchorCharacterId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / callers | `FriendButtonSponsorCharacter.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `CancelFriendship`. |

#### `GetAnchorCharacterList`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| Behavior | Fetches anchor character list. |

#### `RequestFriendship`

| Property | Value |
|----------|-------|
| Parameters | anchorCharacterId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` (+2) |
| UI / callers | `FriendButtonSponsorCharacter.as`, `ChatRoomDragonBonesAvatarMediator.as`, `SponsorCharacterNoneFriendSub.as`, `FriendshipStatusUpdater.as` (+1) |
| Behavior | Envoie demande d'ami ; statut via GetFriendShipStatus. |

#### `UpdateLastInviteSent`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / callers | `AnchorActivityManager.as` |
| Behavior | Updates ate last invite sent. |

#### `UpdateLastStatusSeen`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / callers | `AnchorActivityManager.as` |
| Behavior | Updates ate last status seen. |

## `WebService.Friendships.AMFFriendshipService`

**AMF path:** `MovieStarPlanet.WebService.Friendships.AMFFriendshipService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AcceptBoyfriend` | param1, param2, param3 | AMF endpoint `AcceptBoyfriend`. | — |
| `AcceptMySpecialFriend` | param1 | AMF endpoint `AcceptMySpecialFriend`. | — |
| `ApproveDefaultAnchorFriendship` | param1 | AMF endpoint `ApproveDefaultAnchorFriendship`. | — |
| `ApproveFriendship` | param1, param2 | Accepte demande d'ami. | — |
| `ApproveFriendshipNeb` | param1, param2 | AMF endpoint `ApproveFriendshipNeb`. | — |
| `AskToBeBoyFriend` | param1, param2, param3 | AMF endpoint `AskToBeBoyFriend`. | — |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 | AMF endpoint `AskToBeBoyFriendFromSchoolmate`. | — |
| `AskToBeMySpecialFriend` | param1 | AMF endpoint `AskToBeMySpecialFriend`. | — |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 | AMF endpoint `AskToBeMySpecialFriendFromSchoolmate`. | — |
| `BreakUp` | userId, friendId, friendType | AMF endpoint `BreakUp`. | — |
| `DeleteFriendship` | param1, param2 | Deletes e friendship. | — |
| `DeleteFriendshipNeb` | param1, param2 | Deletes e friendship neb. | — |
| `FindUserForFriendBrowser` | params.actorId, params.includeDeleted, params.searchString, pageIndex, pageSize | AMF endpoint `FindUserForFriendBrowser`. | — |
| `GetFriendList` | param1 | Fetches friend list. | — |
| `GetFriendListWithNameAndScore` | actor.actorId, false | Fetches friend list with name and score. | — |
| `GetFriendListWithNameAndScoreV2` | userId, isLoadingTopFriendsOnly | Fetches friend list with name and score v2. | — |
| `GetFriendShipStatus` | param1, param2 | Fetches friend ship status. | — |
| `GetMspActorSpecialSummary` | param1, param4, param3 | Fetches msp actor special summary. | — |
| `GetNebNonFriendStatus` | param2, param4 | Fetches neb non friend status. | — |
| `GetPagedProfileTodos` | actorId, pageId, pageSize | Paged list — Paged Profile Todos. | — |
| `GetProfileTodos` | param1 | Fetches profile todos. | — |
| `GetProfileTodosCount` | param1 | Fetches profile todos count. | — |
| `GetSpecialRelationship` | param1 | Fetches special relationship. | — |
| `RejectBoyfriend` | param1, param2, param3 | AMF endpoint `RejectBoyfriend`. | — |
| `RejectFriendShip` | param1, param2 | AMF endpoint `RejectFriendShip`. | — |
| `RejectFriendShipNeb` | param1, param2 | AMF endpoint `RejectFriendShipNeb`. | — |
| `RejectMySpecialFriend` | param1 | AMF endpoint `RejectMySpecialFriend`. | — |
| `RequestFriendship` | param1, param2, param3 | Envoie demande d'ami ; statut via GetFriendShipStatus. | — |
| `RequestFriendshipFromSchoolmate` | param1, param2, param3 | AMF endpoint `RequestFriendshipFromSchoolmate`. | — |
| `RequestFriendshipNeb` | param1, param2 | AMF endpoint `RequestFriendshipNeb`. | — |
| `SendInvitation` | param1, param2, param3 | AMF endpoint `SendInvitation`. | — |

### Endpoint details

#### `AcceptBoyfriend`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `BoyfriendButton.as`, `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as` (+2) |
| Behavior | AMF endpoint `AcceptBoyfriend`. |

#### `AcceptMySpecialFriend`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `AcceptMySpecialFriend`. |

#### `ApproveDefaultAnchorFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `Introduction.as` |
| Behavior | AMF endpoint `ApproveDefaultAnchorFriendship`. |

#### `ApproveFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Behavior | Accepte demande d'ami. |

#### `ApproveFriendshipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipManager.as` |
| Behavior | AMF endpoint `ApproveFriendshipNeb`. |

#### `AskToBeBoyFriend`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `BoyfriendButton.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `AskToBeBoyFriend`. |

#### `AskToBeBoyFriendFromSchoolmate`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| Behavior | AMF endpoint `AskToBeBoyFriendFromSchoolmate`. |

#### `AskToBeMySpecialFriend`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `BestFriendButton.as`, `BestFriendSelector.as`, `FriendshipManager.as`, `FriendshipRegistrator.as` (+2) |
| Behavior | AMF endpoint `AskToBeMySpecialFriend`. |

#### `AskToBeMySpecialFriendFromSchoolmate`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| Behavior | AMF endpoint `AskToBeMySpecialFriendFromSchoolmate`. |

#### `BreakUp`

| Property | Value |
|----------|-------|
| Parameters | userId, friendId, friendType |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `BestFriendButton.as`, `BoyfriendButton.as`, `FriendshipStatusUpdater.as`, `FriendInviter.as` |
| Behavior | AMF endpoint `BreakUp`. |

#### `DeleteFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Behavior | Deletes e friendship. |

#### `DeleteFriendshipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipManager.as` |
| Behavior | Deletes e friendship neb. |

#### `FindUserForFriendBrowser`

| Property | Value |
|----------|-------|
| Parameters | params.actorId, params.includeDeleted, params.searchString, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / callers | `FriendBrowserView.as` |
| Behavior | AMF endpoint `FindUserForFriendBrowser`. |

#### `GetFriendList`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / callers | `FriendListPopup.as`, `MiscRegistrator.as`, `FriendsManager.as` |
| Behavior | Fetches friend list. |

#### `GetFriendListWithNameAndScore`

| Property | Value |
|----------|-------|
| Parameters | actor.actorId, false |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+1) |
| UI / callers | `MiscRegistrator.as`, `FriendsManager.as` |
| Behavior | Fetches friend list with name and score. |

#### `GetFriendListWithNameAndScoreV2`

| Property | Value |
|----------|-------|
| Parameters | userId, isLoadingTopFriendsOnly |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Behavior | Fetches friend list with name and score v2. |

#### `GetFriendShipStatus`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / callers | `CharacterPopUp.as`, `WinnerBoard.as` |
| Behavior | Fetches friend ship status. |

#### `GetMspActorSpecialSummary`

| Property | Value |
|----------|-------|
| Parameters | param1, param4, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Behavior | Fetches msp actor special summary. |

#### `GetNebNonFriendStatus`

| Property | Value |
|----------|-------|
| Parameters | param2, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Behavior | Fetches neb non friend status. |

#### `GetPagedProfileTodos`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageId, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / callers | `FriendBrowserView.as` |
| Behavior | Paged list — Paged Profile Todos. |

#### `GetProfileTodos`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / callers | `FriendsFrameIcon.as` |
| Behavior | Fetches profile todos. |

#### `GetProfileTodosCount`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / callers | `FriendsFrameIcon.as` |
| Behavior | Fetches profile todos count. |

#### `GetSpecialRelationship`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Behavior | Fetches special relationship. |

#### `RejectBoyfriend`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as`, `FriendshipStatusUpdater.as` (+1) |
| Behavior | AMF endpoint `RejectBoyfriend`. |

#### `RejectFriendShip`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `TodoSub.as`, `FriendshipStatusUpdater.as`, `FriendRequestForm.as`, `FriendRequestSponsoredCharacterForm.as` (+1) |
| Behavior | AMF endpoint `RejectFriendShip`. |

#### `RejectFriendShipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `TodoSub.as`, `FriendRequestForm.as`, `FriendInviter.as` |
| Behavior | AMF endpoint `RejectFriendShipNeb`. |

#### `RejectMySpecialFriend`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipManager.as`, `FriendshipRegistrator.as`, `IFriendshipService.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `RejectMySpecialFriend`. |

#### `RequestFriendship`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+2) |
| UI / callers | `FriendButtonSponsorCharacter.as`, `ChatRoomDragonBonesAvatarMediator.as`, `SponsorCharacterNoneFriendSub.as`, `FriendshipStatusUpdater.as` (+1) |
| Behavior | Envoie demande d'ami ; statut via GetFriendShipStatus. |

#### `RequestFriendshipFromSchoolmate`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| Behavior | AMF endpoint `RequestFriendshipFromSchoolmate`. |

#### `RequestFriendshipNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / callers | `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `RequestFriendshipNeb`. |

#### `SendInvitation`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / callers | `MoviestarInfoUpdatedHandler.as` |
| Behavior | AMF endpoint `SendInvitation`. |

## `WebService.Messaging.AMFMessagingService`

**AMF path:** `MovieStarPlanet.WebService.Messaging.AMFMessagingService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `SetMessengerSession` | param1 | Updates messenger session. | — |

### Endpoint details

#### `SetMessengerSession`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/chatutils/messagingservice/MessagingAmfService.as` (+1) |
| UI / callers | `SharedRegistrator.as`, `MessagingProvider.as`, `MessengerSessionNotifier.as` |
| Behavior | Updates messenger session. |

## `WebService.Profile.AMFProfileService`

**AMF path:** `MovieStarPlanet.WebService.Profile.AMFProfileService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CollectRecycleGift` | param1 | AMF endpoint `CollectRecycleGift`. | — |
| `DeleteWallPost` | param1, param2, param3 | Deletes e wall post. | — |
| `GetWallPost` | param1 | Fetches wall post. | — |
| `GetWallPosts` | param1, param2, param3 | Fetches wall posts. | — |
| `LoadProfileSummary` | param1, ActorSession.getActorId() | Loads résumé profil (bio, stats, mood, wall preview). | — |
| `LoadProfileSummaryNeb` | param2, ActorSession.getActorId() | Loads profile summary neb. | — |
| `PostToWallWithModerationCall` | param1, param2, param3, param4, param5, param6, param7, param8 | Publie sur le mur avec modération MARS. | — |
| `RecycleItem` | param1, param2, param3 | AMF endpoint `RecycleItem`. | — |
| `SetFavorite` | param1, param2, param3 | Updates favorite. | — |
| `loadActorRoom` | param1, param2 | AMF endpoint `loadActorRoom`. | — |

### Endpoint details

#### `CollectRecycleGift`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / callers | `RecycleController.as` |
| Behavior | AMF endpoint `CollectRecycleGift`. |

#### `DeleteWallPost`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| Behavior | Deletes e wall post. |

#### `GetWallPost`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / callers | `MyProfileAvatarContainer.as`, `WallList.as` |
| Behavior | Fetches wall post. |

#### `GetWallPosts`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / callers | `WallList.as` |
| Behavior | Fetches wall posts. |

#### `LoadProfileSummary`

| Property | Value |
|----------|-------|
| Parameters | param1, ActorSession.getActorId() |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / callers | `BestFriendSelector.as`, `ProfileLoader.as`, `Cache.as` |
| Behavior | Loads résumé profil (bio, stats, mood, wall preview). |

#### `LoadProfileSummaryNeb`

| Property | Value |
|----------|-------|
| Parameters | param2, ActorSession.getActorId() |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| Behavior | Loads profile summary neb. |

#### `PostToWallWithModerationCall`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6, param7, param8 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| Behavior | Publie sur le mur avec modération MARS. |

#### `RecycleItem`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / callers | `RecycleController.as` |
| Behavior | AMF endpoint `RecycleItem`. |

#### `SetFavorite`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / callers | `DressingRoom.as`, `DressingRoomClothesRenderer.as`, `DressingRoomView.as`, `MoviesItemRenderer.as` (+1) |
| Behavior | Updates favorite. |

#### `loadActorRoom`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / callers | `EditMyRoom.as`, `PublicProfile.as`, `MyRoom.as` |
| Behavior | AMF endpoint `loadActorRoom`. |

## `WebService.School.AMFSchoolService`

**AMF path:** `MovieStarPlanet.WebService.School.AMFSchoolService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `DeleteSchool` | actorId | Deletes e school. | — |
| `FindFriendsOnSameSchool` | params.actorId, pageIndex, pageSize, params.includeNames | AMF endpoint `FindFriendsOnSameSchool`. | — |
| `RetrieveMySchoolInformation` | actorId | AMF endpoint `RetrieveMySchoolInformation`. | — |
| `UpdateMySchool` | actorId, schoolId, schoolYear, schoolClass, firstName | Updates ate my school. | — |

### Endpoint details

#### `DeleteSchool`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` |
| Behavior | Deletes e school. |

#### `FindFriendsOnSameSchool`

| Property | Value |
|----------|-------|
| Parameters | params.actorId, pageIndex, pageSize, params.includeNames |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` |
| UI / callers | `FriendBrowserView.as` |
| Behavior | AMF endpoint `FindFriendsOnSameSchool`. |

#### `RetrieveMySchoolInformation`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` |
| UI / callers | `SchoolSettingsController.as`, `LoadMySchoolInfo.as` |
| Behavior | AMF endpoint `RetrieveMySchoolInformation`. |

#### `UpdateMySchool`

| Property | Value |
|----------|-------|
| Parameters | actorId, schoolId, schoolYear, schoolClass, firstName |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` (+1) |
| UI / callers | `SchoolSettingsController.as` |
| Behavior | Updates ate my school. |

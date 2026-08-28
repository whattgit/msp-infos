# V.10 — Social

Amis, profil, messagerie, école, anchor characters.

## Codes de réponse

| Code `GetFriendShipStatus` | Signification |
|---------------------------|---------------|
| `0` | Même utilisateur |
| `1` | Pas amis |
| `2` | Amis |
| `3` | Demande envoyée, en attente |
| `4` | Demande reçue |
| `5–6` | Petit(e) ami(e) |
| `9` | Best friend |

## `WebService.AMFMessageService`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFMessageService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetMessagingActors` | ([id) · (param1) | Récupère messaging actors. | — |
| `IsCommunicationAllowedWith` | param1, param2 | Endpoint AMF `IsCommunicationAllowedWith`. | — |
| `SendChatMessageWithModerationCall` | param1, param2, param3, param4, param5, param6 | Endpoint AMF `SendChatMessageWithModerationCall`. | — |
| `SendOneToOneOrGroupChatMessage` | Number(param2), param8, param3, param6, _loc13_, param4 | Endpoint AMF `SendOneToOneOrGroupChatMessage`. | — |
| `SetMessengerSession` | param1 | Met à jour messenger session. | — |

### Détail endpoints

#### `GetMessagingActors`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ([id) · (param1) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/messaging/module/moduleparts/cache/MessagingCacheRequest.as` (+1) |
| UI / appelants | `SendChatMessageService.as`, `MessagingCache.as`, `ChatView.as`, `MessagingController.as` (+5) |
| Fonctionnement | Récupère messaging actors. |

#### `IsCommunicationAllowedWith`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` (+1) |
| UI / appelants | `MessagingFacade.as`, `OneToOneChatDataItem.as`, `Wall.as` |
| Fonctionnement | Endpoint AMF `IsCommunicationAllowedWith`. |

#### `SendChatMessageWithModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` |
| UI / appelants | `SendChatMessageService.as` |
| Fonctionnement | Endpoint AMF `SendChatMessageWithModerationCall`. |

#### `SendOneToOneOrGroupChatMessage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | Number(param2), param8, param3, param6, _loc13_, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` |
| Fonctionnement | Endpoint AMF `SendOneToOneOrGroupChatMessage`. |

#### `SetMessengerSession`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/messaging/module/moduleparts/messagingwindow/service/MessageAmfService.as` (+1) |
| UI / appelants | `SharedRegistrator.as`, `MessagingProvider.as`, `MessengerSessionNotifier.as` |
| Fonctionnement | Met à jour messenger session. |

## `WebService.AMFMobileFriendshipService`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFMobileFriendshipService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AcceptBoyfriend` | param1, param2, param3 | Endpoint AMF `AcceptBoyfriend`. | — |
| `AcceptMySpecialFriend` | param1 | Endpoint AMF `AcceptMySpecialFriend`. | — |
| `ApproveDefaultAnchorFriendship` | param1 | Endpoint AMF `ApproveDefaultAnchorFriendship`. | — |
| `ApproveFriendship` | param1, param2 | Accepte demande d'ami. | — |
| `ApproveFriendshipNeb` | param1, param2 | Endpoint AMF `ApproveFriendshipNeb`. | — |
| `AskToBeBoyFriend` | param1, param2, param3 | Endpoint AMF `AskToBeBoyFriend`. | — |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 | Endpoint AMF `AskToBeBoyFriendFromSchoolmate`. | — |
| `AskToBeMySpecialFriend` | param1 | Endpoint AMF `AskToBeMySpecialFriend`. | — |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 | Endpoint AMF `AskToBeMySpecialFriendFromSchoolmate`. | — |
| `BreakUp` | param1, param2, param3 | Endpoint AMF `BreakUp`. | — |
| `DeleteFriendship` | param1, param2 | Supprime e friendship. | — |
| `DeleteFriendshipNeb` | param1, param2 | Supprime e friendship neb. | — |
| `GetActorSpecialSummary` | param1, param2 | Récupère actor special summary. | — |
| `GetFriendListWithNameAndScore` | param1 | Récupère friend list with name and score. | — |
| `GetMspRelationshipStatus` | param3, param1, param4 | Récupère msp relationship status. | — |
| `GetPagedFriendRequests` | actorId, pageIndex, pageSize | Liste paginée — Paged Friend Requests. | — |
| `GetRelationshipStatusNeb` | param2, param3, param4 | Récupère relationship status neb. | — |
| `RejectBoyfriend` | param1, param2, param3 | Endpoint AMF `RejectBoyfriend`. | — |
| `RejectFriendShip` | param1, param2 | Endpoint AMF `RejectFriendShip`. | — |
| `RejectFriendShipNeb` | param1, param2 | Endpoint AMF `RejectFriendShipNeb`. | — |
| `RejectMySpecialFriend` | param1 | Endpoint AMF `RejectMySpecialFriend`. | — |
| `RequestFriendship` | param1, param2 | Envoie demande d'ami ; statut via GetFriendShipStatus. | — |
| `RequestFriendshipFromSchoolmate` | param1, param2 | Endpoint AMF `RequestFriendshipFromSchoolmate`. | — |
| `RequestFriendshipNeb` | param1, param2 | Endpoint AMF `RequestFriendshipNeb`. | — |

### Détail endpoints

#### `AcceptBoyfriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `BoyfriendButton.as`, `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as` (+2) |
| Fonctionnement | Endpoint AMF `AcceptBoyfriend`. |

#### `AcceptMySpecialFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `AcceptMySpecialFriend`. |

#### `ApproveDefaultAnchorFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `Introduction.as` |
| Fonctionnement | Endpoint AMF `ApproveDefaultAnchorFriendship`. |

#### `ApproveFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Accepte demande d'ami. |

#### `ApproveFriendshipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipManager.as` |
| Fonctionnement | Endpoint AMF `ApproveFriendshipNeb`. |

#### `AskToBeBoyFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `BoyfriendButton.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `AskToBeBoyFriend`. |

#### `AskToBeBoyFriendFromSchoolmate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| Fonctionnement | Endpoint AMF `AskToBeBoyFriendFromSchoolmate`. |

#### `AskToBeMySpecialFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `BestFriendButton.as`, `BestFriendSelector.as`, `FriendshipManager.as`, `FriendshipRegistrator.as` (+2) |
| Fonctionnement | Endpoint AMF `AskToBeMySpecialFriend`. |

#### `AskToBeMySpecialFriendFromSchoolmate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| Fonctionnement | Endpoint AMF `AskToBeMySpecialFriendFromSchoolmate`. |

#### `BreakUp`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `BestFriendButton.as`, `BoyfriendButton.as`, `FriendshipStatusUpdater.as`, `FriendInviter.as` |
| Fonctionnement | Endpoint AMF `BreakUp`. |

#### `DeleteFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Supprime e friendship. |

#### `DeleteFriendshipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipManager.as` |
| Fonctionnement | Supprime e friendship neb. |

#### `GetActorSpecialSummary`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| UI / appelants | `CharacterPopUp.as` |
| Fonctionnement | Récupère actor special summary. |

#### `GetFriendListWithNameAndScore`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `MiscRegistrator.as`, `FriendsManager.as` |
| Fonctionnement | Récupère friend list with name and score. |

#### `GetMspRelationshipStatus`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param3, param1, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| Fonctionnement | Récupère msp relationship status. |

#### `GetPagedFriendRequests`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| Fonctionnement | Liste paginée — Paged Friend Requests. |

#### `GetRelationshipStatusNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` |
| Fonctionnement | Récupère relationship status neb. |

#### `RejectBoyfriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as`, `FriendshipStatusUpdater.as` (+1) |
| Fonctionnement | Endpoint AMF `RejectBoyfriend`. |

#### `RejectFriendShip`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `TodoSub.as`, `FriendshipStatusUpdater.as`, `FriendRequestForm.as`, `FriendRequestSponsoredCharacterForm.as` (+1) |
| Fonctionnement | Endpoint AMF `RejectFriendShip`. |

#### `RejectFriendShipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `TodoSub.as`, `FriendRequestForm.as`, `FriendInviter.as` |
| Fonctionnement | Endpoint AMF `RejectFriendShipNeb`. |

#### `RejectMySpecialFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipRegistrator.as`, `IFriendshipService.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `RejectMySpecialFriend`. |

#### `RequestFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+2) |
| UI / appelants | `FriendButtonSponsorCharacter.as`, `ChatRoomDragonBonesAvatarMediator.as`, `SponsorCharacterNoneFriendSub.as`, `FriendshipStatusUpdater.as` (+1) |
| Fonctionnement | Envoie demande d'ami ; statut via GetFriendShipStatus. |

#### `RequestFriendshipFromSchoolmate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| Fonctionnement | Endpoint AMF `RequestFriendshipFromSchoolmate`. |

#### `RequestFriendshipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceMobile.as` (+1) |
| UI / appelants | `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `RequestFriendshipNeb`. |

## `WebService.AnchorCharacter.AMFAnchorCharacterService`

**Chemin AMF :** `MovieStarPlanet.WebService.AnchorCharacter.AMFAnchorCharacterService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AcceptFriendship` | anchorCharacterId | Endpoint AMF `AcceptFriendship`. | — |
| `AcceptGifts` | anchorCharacterId | Endpoint AMF `AcceptGifts`. | — |
| `CancelFriendship` | anchorCharacterId | Endpoint AMF `CancelFriendship`. | — |
| `GetAnchorCharacterList` | — | Récupère anchor character list. | — |
| `RequestFriendship` | anchorCharacterId | Envoie demande d'ami ; statut via GetFriendShipStatus. | — |
| `UpdateLastInviteSent` | param1, param2 | Met à jour ate last invite sent. | — |
| `UpdateLastStatusSeen` | param1 | Met à jour ate last status seen. | — |

### Détail endpoints

#### `AcceptFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | anchorCharacterId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / appelants | `FriendRequestSponsoredCharacterForm.as` |
| Fonctionnement | Endpoint AMF `AcceptFriendship`. |

#### `AcceptGifts`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | anchorCharacterId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / appelants | `HandleSponsoredReactivationCommand.as` |
| Fonctionnement | Endpoint AMF `AcceptGifts`. |

#### `CancelFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | anchorCharacterId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / appelants | `FriendButtonSponsorCharacter.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `CancelFriendship`. |

#### `GetAnchorCharacterList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| Fonctionnement | Récupère anchor character list. |

#### `RequestFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | anchorCharacterId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` (+2) |
| UI / appelants | `FriendButtonSponsorCharacter.as`, `ChatRoomDragonBonesAvatarMediator.as`, `SponsorCharacterNoneFriendSub.as`, `FriendshipStatusUpdater.as` (+1) |
| Fonctionnement | Envoie demande d'ami ; statut via GetFriendShipStatus. |

#### `UpdateLastInviteSent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / appelants | `AnchorActivityManager.as` |
| Fonctionnement | Met à jour ate last invite sent. |

#### `UpdateLastStatusSeen`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/anchorCharacters/service/AMFSponsoredCharacterService.as` |
| UI / appelants | `AnchorActivityManager.as` |
| Fonctionnement | Met à jour ate last status seen. |

## `WebService.Friendships.AMFFriendshipService`

**Chemin AMF :** `MovieStarPlanet.WebService.Friendships.AMFFriendshipService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AcceptBoyfriend` | param1, param2, param3 | Endpoint AMF `AcceptBoyfriend`. | — |
| `AcceptMySpecialFriend` | param1 | Endpoint AMF `AcceptMySpecialFriend`. | — |
| `ApproveDefaultAnchorFriendship` | param1 | Endpoint AMF `ApproveDefaultAnchorFriendship`. | — |
| `ApproveFriendship` | param1, param2 | Accepte demande d'ami. | — |
| `ApproveFriendshipNeb` | param1, param2 | Endpoint AMF `ApproveFriendshipNeb`. | — |
| `AskToBeBoyFriend` | param1, param2, param3 | Endpoint AMF `AskToBeBoyFriend`. | — |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 | Endpoint AMF `AskToBeBoyFriendFromSchoolmate`. | — |
| `AskToBeMySpecialFriend` | param1 | Endpoint AMF `AskToBeMySpecialFriend`. | — |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 | Endpoint AMF `AskToBeMySpecialFriendFromSchoolmate`. | — |
| `BreakUp` | userId, friendId, friendType | Endpoint AMF `BreakUp`. | — |
| `DeleteFriendship` | param1, param2 | Supprime e friendship. | — |
| `DeleteFriendshipNeb` | param1, param2 | Supprime e friendship neb. | — |
| `FindUserForFriendBrowser` | params.actorId, params.includeDeleted, params.searchString, pageIndex, pageSize | Endpoint AMF `FindUserForFriendBrowser`. | — |
| `GetFriendList` | param1 | Récupère friend list. | — |
| `GetFriendListWithNameAndScore` | actor.actorId, false | Récupère friend list with name and score. | — |
| `GetFriendListWithNameAndScoreV2` | userId, isLoadingTopFriendsOnly | Récupère friend list with name and score v2. | — |
| `GetFriendShipStatus` | param1, param2 | Récupère friend ship status. | — |
| `GetMspActorSpecialSummary` | param1, param4, param3 | Récupère msp actor special summary. | — |
| `GetNebNonFriendStatus` | param2, param4 | Récupère neb non friend status. | — |
| `GetPagedProfileTodos` | actorId, pageId, pageSize | Liste paginée — Paged Profile Todos. | — |
| `GetProfileTodos` | param1 | Récupère profile todos. | — |
| `GetProfileTodosCount` | param1 | Récupère profile todos count. | — |
| `GetSpecialRelationship` | param1 | Récupère special relationship. | — |
| `RejectBoyfriend` | param1, param2, param3 | Endpoint AMF `RejectBoyfriend`. | — |
| `RejectFriendShip` | param1, param2 | Endpoint AMF `RejectFriendShip`. | — |
| `RejectFriendShipNeb` | param1, param2 | Endpoint AMF `RejectFriendShipNeb`. | — |
| `RejectMySpecialFriend` | param1 | Endpoint AMF `RejectMySpecialFriend`. | — |
| `RequestFriendship` | param1, param2, param3 | Envoie demande d'ami ; statut via GetFriendShipStatus. | — |
| `RequestFriendshipFromSchoolmate` | param1, param2, param3 | Endpoint AMF `RequestFriendshipFromSchoolmate`. | — |
| `RequestFriendshipNeb` | param1, param2 | Endpoint AMF `RequestFriendshipNeb`. | — |
| `SendInvitation` | param1, param2, param3 | Endpoint AMF `SendInvitation`. | — |

### Détail endpoints

#### `AcceptBoyfriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `BoyfriendButton.as`, `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as` (+2) |
| Fonctionnement | Endpoint AMF `AcceptBoyfriend`. |

#### `AcceptMySpecialFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `AcceptMySpecialFriend`. |

#### `ApproveDefaultAnchorFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `Introduction.as` |
| Fonctionnement | Endpoint AMF `ApproveDefaultAnchorFriendship`. |

#### `ApproveFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Accepte demande d'ami. |

#### `ApproveFriendshipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipManager.as` |
| Fonctionnement | Endpoint AMF `ApproveFriendshipNeb`. |

#### `AskToBeBoyFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `BoyfriendButton.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `AskToBeBoyFriend`. |

#### `AskToBeBoyFriendFromSchoolmate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| Fonctionnement | Endpoint AMF `AskToBeBoyFriendFromSchoolmate`. |

#### `AskToBeMySpecialFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `BestFriendButton.as`, `BestFriendSelector.as`, `FriendshipManager.as`, `FriendshipRegistrator.as` (+2) |
| Fonctionnement | Endpoint AMF `AskToBeMySpecialFriend`. |

#### `AskToBeMySpecialFriendFromSchoolmate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| Fonctionnement | Endpoint AMF `AskToBeMySpecialFriendFromSchoolmate`. |

#### `BreakUp`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | userId, friendId, friendType |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `BestFriendButton.as`, `BoyfriendButton.as`, `FriendshipStatusUpdater.as`, `FriendInviter.as` |
| Fonctionnement | Endpoint AMF `BreakUp`. |

#### `DeleteFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Supprime e friendship. |

#### `DeleteFriendshipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipManager.as` |
| Fonctionnement | Supprime e friendship neb. |

#### `FindUserForFriendBrowser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params.actorId, params.includeDeleted, params.searchString, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / appelants | `FriendBrowserView.as` |
| Fonctionnement | Endpoint AMF `FindUserForFriendBrowser`. |

#### `GetFriendList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / appelants | `FriendListPopup.as`, `MiscRegistrator.as`, `FriendsManager.as` |
| Fonctionnement | Récupère friend list. |

#### `GetFriendListWithNameAndScore`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actor.actorId, false |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+1) |
| UI / appelants | `MiscRegistrator.as`, `FriendsManager.as` |
| Fonctionnement | Récupère friend list with name and score. |

#### `GetFriendListWithNameAndScoreV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | userId, isLoadingTopFriendsOnly |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Fonctionnement | Récupère friend list with name and score v2. |

#### `GetFriendShipStatus`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / appelants | `CharacterPopUp.as`, `WinnerBoard.as` |
| Fonctionnement | Récupère friend ship status. |

#### `GetMspActorSpecialSummary`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param4, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Fonctionnement | Récupère msp actor special summary. |

#### `GetNebNonFriendStatus`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Fonctionnement | Récupère neb non friend status. |

#### `GetPagedProfileTodos`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageId, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / appelants | `FriendBrowserView.as` |
| Fonctionnement | Liste paginée — Paged Profile Todos. |

#### `GetProfileTodos`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / appelants | `FriendsFrameIcon.as` |
| Fonctionnement | Récupère profile todos. |

#### `GetProfileTodosCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / appelants | `FriendsFrameIcon.as` |
| Fonctionnement | Récupère profile todos count. |

#### `GetSpecialRelationship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| Fonctionnement | Récupère special relationship. |

#### `RejectBoyfriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `TodoSub.as`, `FriendshipNotificationListener.as`, `FriendshipStatusUpdater.as` (+1) |
| Fonctionnement | Endpoint AMF `RejectBoyfriend`. |

#### `RejectFriendShip`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `TodoSub.as`, `FriendshipStatusUpdater.as`, `FriendRequestForm.as`, `FriendRequestSponsoredCharacterForm.as` (+1) |
| Fonctionnement | Endpoint AMF `RejectFriendShip`. |

#### `RejectFriendShipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `TodoSub.as`, `FriendRequestForm.as`, `FriendInviter.as` |
| Fonctionnement | Endpoint AMF `RejectFriendShipNeb`. |

#### `RejectMySpecialFriend`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipManager.as`, `FriendshipRegistrator.as`, `IFriendshipService.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `RejectMySpecialFriend`. |

#### `RequestFriendship`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+2) |
| UI / appelants | `FriendButtonSponsorCharacter.as`, `ChatRoomDragonBonesAvatarMediator.as`, `SponsorCharacterNoneFriendSub.as`, `FriendshipStatusUpdater.as` (+1) |
| Fonctionnement | Envoie demande d'ami ; statut via GetFriendShipStatus. |

#### `RequestFriendshipFromSchoolmate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| Fonctionnement | Endpoint AMF `RequestFriendshipFromSchoolmate`. |

#### `RequestFriendshipNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `GetFriendShipStatus` : 0 même user · 1 pas amis · 2 amis · 3 envoyée · 4 reçue · 5/6 BF · 9 best friend |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` (+1) |
| UI / appelants | `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `RequestFriendshipNeb`. |

#### `SendInvitation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/friendship/service/FriendshipServiceWeb.as` |
| UI / appelants | `MoviestarInfoUpdatedHandler.as` |
| Fonctionnement | Endpoint AMF `SendInvitation`. |

## `WebService.Messaging.AMFMessagingService`

**Chemin AMF :** `MovieStarPlanet.WebService.Messaging.AMFMessagingService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `SetMessengerSession` | param1 | Met à jour messenger session. | — |

### Détail endpoints

#### `SetMessengerSession`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/chatutils/messagingservice/MessagingAmfService.as` (+1) |
| UI / appelants | `SharedRegistrator.as`, `MessagingProvider.as`, `MessengerSessionNotifier.as` |
| Fonctionnement | Met à jour messenger session. |

## `WebService.Profile.AMFProfileService`

**Chemin AMF :** `MovieStarPlanet.WebService.Profile.AMFProfileService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CollectRecycleGift` | param1 | Endpoint AMF `CollectRecycleGift`. | — |
| `DeleteWallPost` | param1, param2, param3 | Supprime e wall post. | — |
| `GetWallPost` | param1 | Récupère wall post. | — |
| `GetWallPosts` | param1, param2, param3 | Récupère wall posts. | — |
| `LoadProfileSummary` | param1, ActorSession.getActorId() | Charge résumé profil (bio, stats, mood, wall preview). | — |
| `LoadProfileSummaryNeb` | param2, ActorSession.getActorId() | Charge profile summary neb. | — |
| `PostToWallWithModerationCall` | param1, param2, param3, param4, param5, param6, param7, param8 | Publie sur le mur avec modération MARS. | — |
| `RecycleItem` | param1, param2, param3 | Endpoint AMF `RecycleItem`. | — |
| `SetFavorite` | param1, param2, param3 | Met à jour favorite. | — |
| `loadActorRoom` | param1, param2 | Endpoint AMF `loadActorRoom`. | — |

### Détail endpoints

#### `CollectRecycleGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / appelants | `RecycleController.as` |
| Fonctionnement | Endpoint AMF `CollectRecycleGift`. |

#### `DeleteWallPost`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| Fonctionnement | Supprime e wall post. |

#### `GetWallPost`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / appelants | `MyProfileAvatarContainer.as`, `WallList.as` |
| Fonctionnement | Récupère wall post. |

#### `GetWallPosts`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / appelants | `WallList.as` |
| Fonctionnement | Récupère wall posts. |

#### `LoadProfileSummary`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, ActorSession.getActorId() |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / appelants | `BestFriendSelector.as`, `ProfileLoader.as`, `Cache.as` |
| Fonctionnement | Charge résumé profil (bio, stats, mood, wall preview). |

#### `LoadProfileSummaryNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, ActorSession.getActorId() |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| Fonctionnement | Charge profile summary neb. |

#### `PostToWallWithModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6, param7, param8 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| Fonctionnement | Publie sur le mur avec modération MARS. |

#### `RecycleItem`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / appelants | `RecycleController.as` |
| Fonctionnement | Endpoint AMF `RecycleItem`. |

#### `SetFavorite`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / appelants | `DressingRoom.as`, `DressingRoomClothesRenderer.as`, `DressingRoomView.as`, `MoviesItemRenderer.as` (+1) |
| Fonctionnement | Met à jour favorite. |

#### `loadActorRoom`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/profile/service/ProfileAmfService.as` |
| UI / appelants | `EditMyRoom.as`, `PublicProfile.as`, `MyRoom.as` |
| Fonctionnement | Endpoint AMF `loadActorRoom`. |

## `WebService.School.AMFSchoolService`

**Chemin AMF :** `MovieStarPlanet.WebService.School.AMFSchoolService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `DeleteSchool` | actorId | Supprime e school. | — |
| `FindFriendsOnSameSchool` | params.actorId, pageIndex, pageSize, params.includeNames | Endpoint AMF `FindFriendsOnSameSchool`. | — |
| `RetrieveMySchoolInformation` | actorId | Endpoint AMF `RetrieveMySchoolInformation`. | — |
| `UpdateMySchool` | actorId, schoolId, schoolYear, schoolClass, firstName | Met à jour ate my school. | — |

### Détail endpoints

#### `DeleteSchool`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` |
| Fonctionnement | Supprime e school. |

#### `FindFriendsOnSameSchool`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params.actorId, pageIndex, pageSize, params.includeNames |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` |
| UI / appelants | `FriendBrowserView.as` |
| Fonctionnement | Endpoint AMF `FindFriendsOnSameSchool`. |

#### `RetrieveMySchoolInformation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` |
| UI / appelants | `SchoolSettingsController.as`, `LoadMySchoolInfo.as` |
| Fonctionnement | Endpoint AMF `RetrieveMySchoolInformation`. |

#### `UpdateMySchool`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, schoolId, schoolYear, schoolClass, firstName |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/schoolfriends/service/SchoolFriendsService.as` (+1) |
| UI / appelants | `SchoolSettingsController.as` |
| Fonctionnement | Met à jour ate my school. |

# V.2 — Authentification & session

Login, compte, Nebula, parental consent, paiements.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `GiveAutographAndCalculateTimestamp` | `AMFUserSessionService` | `Fame` | Oui |
| `GiveAutographAndCalculateTimestampNeb` | `AMFActorService` | `Fame` | Oui |
| `PickupGuidePresent` | `AMFActorService` | `Code` | Oui |

## `WebService.AMFActorService`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFActorService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BlockActor` | param1, param2 | Endpoint AMF `BlockActor`. | — |
| `BlockActorNeb` | param1, param2 | Endpoint AMF `BlockActorNeb`. | — |
| `BulkLoadActors` | param1 | Endpoint AMF `BulkLoadActors`. | — |
| `BuyClothesNew` | actorId, clothes[] | Achat vêtements variante mobile (`AMFActorService`) sans lookId. | — |
| `CreateNewUserWithSecureSnapshotV2` | newActorCreationData, checksum, store, deviceId, snapshotSmall, snapshotBig | Sauvegarde / crée create new user with secure snapshot v2. | — |
| `GetActorIdByName` | param1 | Récupère actor id by name. | — |
| `GetActorZooItems` | param1 | Récupère actor zoo items. | — |
| `GetClothesFromNewestClothesSection` | param1, param2, param3 | Récupère clothes from newest clothes section. | — |
| `GetPagedClothByCategoryGroups` | param1, _loc5_ | Liste paginée — Paged Cloth By Category Groups. | — |
| `GetPagedClothByCategoryGroups_14` | param1, _loc5_ | Liste paginée — Paged Cloth By Category Groups 14. | — |
| `GetPostLoginBundle` | actorId | Données post-login : tenue, settings, candy prices, todos. | — |
| `IsActorNameUsed` | param1 | Endpoint AMF `IsActorNameUsed`. | — |
| `IsNameBlocked` | param1 | Endpoint AMF `IsNameBlocked`. | — |
| `LoadActorDetails` | param1, param2 | Charge actor details. | — |
| `LoadActorDetailsExtended` | param1 | Charge actor details extended. | — |
| `LoadActorItems` | param1 | Charge actor items. | — |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 | Charge actor with current clothes and spritesheet. | — |
| `LoadActorWithCurrentClothesBasicDataOnlyRevised` | param1 | Charge actor with current clothes basic data only revised. | — |
| `LoadActorsVipDetails` | param1 | Charge actors vip details. | — |
| `LoadBlockedAndBlockingActors` | param1 | Charge blocked and blocking actors. | — |
| `LoadBlockedAndBlockingActorsNeb` | param1 | Charge blocked and blocking actors neb. | — |
| `LoadDataForRegisterNewUser` | — | Charge data for register new user. | — |
| `LoadModeratorInformation` | param1 | Charge moderator information. | — |
| `LoadMood` | param1 | Charge mood. | — |
| `LoadMovieStarListRevised` | param1 | Charge movie star list revised. | — |
| `LockOutUser` | param1, param2, param3, param4, param5 | Endpoint AMF `LockOutUser`. | — |
| `LoginMobile` | userId, redirectToken, version, store, deviceId | Endpoint AMF `LoginMobile`. | — |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 | Endpoint AMF `ModerationSearchActorByName`. | — |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 | Endpoint AMF `ModerationSearchMassDeleteActorByName`. | — |
| `PickupGuidePresent` | actorId, type, index | Endpoint AMF `PickupGuidePresent`. | `-429` |
| `ReportActor` | param1 | Endpoint AMF `ReportActor`. | — |
| `ReportTabletAndroidConversion` | param1, param2 | Endpoint AMF `ReportTabletAndroidConversion`. | — |
| `ReportTabletIOSConversion` | param1, param2 | Endpoint AMF `ReportTabletIOSConversion`. | — |
| `RequestMobileStartupReward` | param1 | Endpoint AMF `RequestMobileStartupReward`. | — |
| `SaveAlertWordsCount` | param1, param2 | Sauvegarde / crée save alert words count. | — |
| `SaveBirthInfoWithTicket` | param1, param2, param3 | Sauvegarde / crée save birth info with ticket. | — |
| `SearchActorByNameNeb` | param1, param2 | Recherche actor by name neb. | — |
| `SearchActorByNameWithRequestStatus` | param1, param2 | Recherche actor by name with request status. | — |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 | Met à jour mood with moderation call. | — |
| `SubmitMobileStartupReward` | param1, param2, param3 | Endpoint AMF `SubmitMobileStartupReward`. | — |
| `ThirdPartyLoginDesktopV2` | param1, param2, param3, param4, param5 | Endpoint AMF `ThirdPartyLoginDesktopV2`. | — |
| `ThirdPartyLoginMobileV2` | nacd, snapshotBig, snapshotSmall, username, password, version, store, deviceId | Endpoint AMF `ThirdPartyLoginMobileV2`. | — |
| `UnblockActor` | param1, param2 | Endpoint AMF `UnblockActor`. | — |
| `UnblockActorNeb` | param1, param2 | Endpoint AMF `UnblockActorNeb`. | — |
| `UpdateClothes` | actorId, actorClothesRelIds[] | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. | — |
| `ValidateCaptcha` | param1, param2 | Endpoint AMF `ValidateCaptcha`. | — |
| `fameOverhaul` | param1 | Endpoint AMF `fameOverhaul`. | — |
| `loginMobileV2` | userName, password, version, store, deviceId, dfp | Connexion mobile. | — |

### Détail endpoints

#### `BlockActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `BlockActor`. |

#### `BlockActorNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `BlockActorNeb`. |

#### `BulkLoadActors`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `BulkLoadActors`. |

#### `BuyClothesNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clothes[] |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Achat vêtements variante mobile (`AMFActorService`) sans lookId. |

#### `CreateNewUserWithSecureSnapshotV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | newActorCreationData, checksum, store, deviceId, snapshotSmall, snapshotBig |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Fonctionnement | Sauvegarde / crée create new user with secure snapshot v2. |

#### `GetActorIdByName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Récupère actor id by name. |

#### `GetActorZooItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Récupère actor zoo items. |

#### `GetClothesFromNewestClothesSection`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| UI / appelants | `SpendingRegistrator.as`, `ShopContentAmfService.as`, `ClothesShopModel.as`, `ClothesShopModel.as` (+1) |
| Fonctionnement | Récupère clothes from newest clothes section. |

#### `GetPagedClothByCategoryGroups`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, _loc5_ |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Liste paginée — Paged Cloth By Category Groups. |

#### `GetPagedClothByCategoryGroups_14`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, _loc5_ |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Liste paginée — Paged Cloth By Category Groups 14. |

#### `GetPostLoginBundle`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `PostLoginHandler.as` |
| Fonctionnement | Données post-login : tenue, settings, candy prices, todos. |

#### `IsActorNameUsed`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `ActorNameService.as` |
| Fonctionnement | Endpoint AMF `IsActorNameUsed`. |

#### `IsNameBlocked`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `ActorNameService.as` |
| Fonctionnement | Endpoint AMF `IsNameBlocked`. |

#### `LoadActorDetails`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `ActorAdmin.as`, `UpdateModerationStatusCommand.as`, `ActorReload.as`, `AbstractContentListItemRenderer.as` (+3) |
| Fonctionnement | Charge actor details. |

#### `LoadActorDetailsExtended`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+2) |
| UI / appelants | `UpdateModerationStatusCommand.as`, `ActorReload.as`, `ActorDetailsReloadingMob.as` |
| Fonctionnement | Charge actor details extended. |

#### `LoadActorItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Charge actor items. |

#### `LoadActorWithCurrentClothesAndSpritesheet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Fonctionnement | Charge actor with current clothes and spritesheet. |

#### `LoadActorWithCurrentClothesBasicDataOnlyRevised`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| UI / appelants | `FriendshipStatusUpdater.as` |
| Fonctionnement | Charge actor with current clothes basic data only revised. |

#### `LoadActorsVipDetails`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Charge actors vip details. |

#### `LoadBlockedAndBlockingActors`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `ActorBlocking.as` |
| Fonctionnement | Charge blocked and blocking actors. |

#### `LoadBlockedAndBlockingActorsNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `ActorBlocking.as` |
| Fonctionnement | Charge blocked and blocking actors neb. |

#### `LoadDataForRegisterNewUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `RegisterNewUserComponent.as` |
| Fonctionnement | Charge data for register new user. |

#### `LoadModeratorInformation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `CombatProfileUpdaterWeb.as` |
| Fonctionnement | Charge moderator information. |

#### `LoadMood`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `TwitterConfig.as`, `MainViewMoviestarContainer.as` |
| Fonctionnement | Charge mood. |

#### `LoadMovieStarListRevised`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `ActorCache.as` |
| Fonctionnement | Charge movie star list revised. |

#### `LockOutUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `AdminManager.as`, `UserBehaviorServiceSettings.as` |
| Fonctionnement | Endpoint AMF `LockOutUser`. |

#### `LoginMobile`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | userId, redirectToken, version, store, deviceId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `LoginMobile`. |

#### `ModerationSearchActorByName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params.searchString, pageIndex, pageSize + 1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Fonctionnement | Endpoint AMF `ModerationSearchActorByName`. |

#### `ModerationSearchMassDeleteActorByName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params.searchString, pageIndex, pageSize + 1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `FriendBrowserView.as` |
| Fonctionnement | Endpoint AMF `ModerationSearchMassDeleteActorByName`. |

#### `PickupGuidePresent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, type, index |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `Code` (popup) |
| Codes retour | Champ `Code` == −429 (popup) |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `GiftHuntManager.as` |
| Fonctionnement | Endpoint AMF `PickupGuidePresent`. |

#### `ReportActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `CoreReloadListeners.as` |
| Fonctionnement | Endpoint AMF `ReportActor`. |

#### `ReportTabletAndroidConversion`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `ReportTabletAndroidConversion`. |

#### `ReportTabletIOSConversion`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `ReportTabletIOSConversion`. |

#### `RequestMobileStartupReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `RequestMobileStartupReward`. |

#### `SaveAlertWordsCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Sauvegarde / crée save alert words count. |

#### `SaveBirthInfoWithTicket`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Fonctionnement | Sauvegarde / crée save birth info with ticket. |

#### `SearchActorByNameNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Fonctionnement | Recherche actor by name neb. |

#### `SearchActorByNameWithRequestStatus`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Recherche actor by name with request status. |

#### `SetMoodWithModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Fonctionnement | Met à jour mood with moderation call. |

#### `SubmitMobileStartupReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `SubmitMobileStartupReward`. |

#### `ThirdPartyLoginDesktopV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `ThirdPartyLoginDesktopV2`. |

#### `ThirdPartyLoginMobileV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | nacd, snapshotBig, snapshotSmall, username, password, version, store, deviceId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Endpoint AMF `ThirdPartyLoginMobileV2`. |

#### `UnblockActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Fonctionnement | Endpoint AMF `UnblockActor`. |

#### `UnblockActorNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Fonctionnement | Endpoint AMF `UnblockActorNeb`. |

#### `UpdateClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorClothesRelIds[] |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `SaveClothesCommand.as` |
| Fonctionnement | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. |

#### `ValidateCaptcha`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `RegisterNewUserComponent.as` |
| Fonctionnement | Endpoint AMF `ValidateCaptcha`. |

#### `fameOverhaul`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / appelants | `LoginRequiredSetupCommand.as`, `PostLoginSequence.as` |
| Fonctionnement | Endpoint AMF `fameOverhaul`. |

#### `loginMobileV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | userName, password, version, store, deviceId, dfp |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Fonctionnement | Connexion mobile. |

## `WebService.AMFUserService`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFUserService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `LogInput` | param1, param2, param3, param5, param4 | Endpoint AMF `LogInput`. | — |
| `LogInputGroupChat` | param1, param2, param3, param5, param4 | Endpoint AMF `LogInputGroupChat`. | — |
| `LogInputWithConditionalModerationCall` | param1, param2, param3, param4, param5, param6 | Endpoint AMF `LogInputWithConditionalModerationCall`. | — |

### Détail endpoints

#### `LogInput`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param5, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceMobile.as` (+2) |
| UI / appelants | `ManageClub.as`, `CommentNewComponent.as`, `MonsterPopup.as`, `MyLooksEditor.as` (+21) |
| Fonctionnement | Endpoint AMF `LogInput`. |

#### `LogInputGroupChat`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param5, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceMobile.as` (+1) |
| UI / appelants | `InputLoggingHandler.as` |
| Fonctionnement | Endpoint AMF `LogInputGroupChat`. |

#### `LogInputWithConditionalModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceMobile.as` (+1) |
| UI / appelants | `InputLoggingHandler.as` |
| Fonctionnement | Endpoint AMF `LogInputWithConditionalModerationCall`. |

## `WebService.ActorService.AMFActorServiceForWeb`

**Chemin AMF :** `MovieStarPlanet.WebService.ActorService.AMFActorServiceForWeb`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BlockActor` | param1, param2 | Endpoint AMF `BlockActor`. | — |
| `BlockActorNeb` | param1, param2 | Endpoint AMF `BlockActorNeb`. | — |
| `BlockedActors` | param1 | Endpoint AMF `BlockedActors`. | — |
| `ClaimAllLevelUpGifts` | param1, param2 | Endpoint AMF `ClaimAllLevelUpGifts`. | — |
| `ClaimSingleLevelUpGift` | param1, param2, param3 | Endpoint AMF `ClaimSingleLevelUpGift`. | — |
| `GetActorAddress` | actorId | Récupère actor address. | — |
| `GetLevelUpGiftChoices` | actorId | Récupère level up gift choices. | — |
| `GetLevelUpGiftSelects` | actorId | Récupère level up gift selects. | — |
| `GetLevelUps` | — | Récupère level ups. | — |
| `GetPostLoginBundle` | actorId | Données post-login : tenue, settings, candy prices, todos. | — |
| `GetPostLoginBundleStandalone` | param1 | Récupère post login bundle standalone. | — |
| `IsActorNameUsed` | param1 | Endpoint AMF `IsActorNameUsed`. | — |
| `IsNameBlocked` | param1 | Endpoint AMF `IsNameBlocked`. | — |
| `LoadActorDetails` | param1, param2 | Charge actor details. | — |
| `LoadActorDetailsExtended` | param1 | Charge actor details extended. | — |
| `LoadBlockedAndBlockingActors` | param1 | Charge blocked and blocking actors. | — |
| `LoadBlockedAndBlockingActorsNeb` | param1 | Charge blocked and blocking actors neb. | — |
| `LoadModeratorInformation` | param1 | Charge moderator information. | — |
| `LoadMood` | param1 | Charge mood. | — |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 | Endpoint AMF `ModerationSearchActorByName`. | — |
| `ModerationSearchActorId` | actorId | Endpoint AMF `ModerationSearchActorId`. | — |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 | Endpoint AMF `ModerationSearchMassDeleteActorByName`. | — |
| `PickupGuidePresent` | actorId, type, index | Endpoint AMF `PickupGuidePresent`. | `-429` |
| `PurchaseRecoloring` | param1, param2, param3, param4, param5 | Endpoint AMF `PurchaseRecoloring`. | — |
| `ReportActor` | param1 | Endpoint AMF `ReportActor`. | — |
| `SaveActorAddress` | param1 | Sauvegarde / crée save actor address. | — |
| `SaveActorSoundMuted` | param1, param2 | Sauvegarde / crée save actor sound muted. | — |
| `SaveBirthInfoWithTicket` | param1, param2, param3 | Sauvegarde / crée save birth info with ticket. | — |
| `SaveLevelUpGiftSelect` | param1, param2, param3 | Sauvegarde / crée save level up gift select. | — |
| `SearchActorByNameNeb` | param1, param2 | Recherche actor by name neb. | — |
| `SetColorOnActorItemNew` | param1, param2, param3, param4, param5 | Met à jour color on actor item new. | — |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 | Met à jour mood with moderation call. | — |
| `UnblockActor` | param1, param2 | Endpoint AMF `UnblockActor`. | — |
| `UnblockActorNeb` | param1, param2 | Endpoint AMF `UnblockActorNeb`. | — |
| `ValidateCaptcha` | param1, param2 | Endpoint AMF `ValidateCaptcha`. | — |
| `fameOverhaul` | param1 | Endpoint AMF `fameOverhaul`. | — |
| `getWallActivitiesForActor` | pagingOptions.actorId, pagingOptions.activityType, pagingOptions.pageIndex, pagingOptions.pageSize | Endpoint AMF `getWallActivitiesForActor`. | — |

### Détail endpoints

#### `BlockActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `BlockActor`. |

#### `BlockActorNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Fonctionnement | Endpoint AMF `BlockActorNeb`. |

#### `BlockedActors`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `BlockedActorsListPopup.as`, `Settings.as`, `ActorBlocking.as`, `MessageSecurity.as` (+1) |
| Fonctionnement | Endpoint AMF `BlockedActors`. |

#### `ClaimAllLevelUpGifts`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `CongratsGiftPopupAnimation.as` |
| Fonctionnement | Endpoint AMF `ClaimAllLevelUpGifts`. |

#### `ClaimSingleLevelUpGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Fonctionnement | Endpoint AMF `ClaimSingleLevelUpGift`. |

#### `GetActorAddress`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `SelectPaymentView.as` |
| Fonctionnement | Récupère actor address. |

#### `GetLevelUpGiftChoices`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Fonctionnement | Récupère level up gift choices. |

#### `GetLevelUpGiftSelects`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Fonctionnement | Récupère level up gift selects. |

#### `GetLevelUps`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `LevelUpPopupController.as` |
| Fonctionnement | Récupère level ups. |

#### `GetPostLoginBundle`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `PostLoginHandler.as` |
| Fonctionnement | Données post-login : tenue, settings, candy prices, todos. |

#### `GetPostLoginBundleStandalone`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Fonctionnement | Récupère post login bundle standalone. |

#### `IsActorNameUsed`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `ActorNameService.as` |
| Fonctionnement | Endpoint AMF `IsActorNameUsed`. |

#### `IsNameBlocked`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `ActorNameService.as` |
| Fonctionnement | Endpoint AMF `IsNameBlocked`. |

#### `LoadActorDetails`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `ActorAdmin.as`, `UpdateModerationStatusCommand.as`, `ActorReload.as`, `AbstractContentListItemRenderer.as` (+3) |
| Fonctionnement | Charge actor details. |

#### `LoadActorDetailsExtended`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+2) |
| UI / appelants | `UpdateModerationStatusCommand.as`, `ActorReload.as`, `ActorDetailsReloadingMob.as` |
| Fonctionnement | Charge actor details extended. |

#### `LoadBlockedAndBlockingActors`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `ActorBlocking.as` |
| Fonctionnement | Charge blocked and blocking actors. |

#### `LoadBlockedAndBlockingActorsNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `ActorBlocking.as` |
| Fonctionnement | Charge blocked and blocking actors neb. |

#### `LoadModeratorInformation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `CombatProfileUpdaterWeb.as` |
| Fonctionnement | Charge moderator information. |

#### `LoadMood`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `TwitterConfig.as`, `MainViewMoviestarContainer.as` |
| Fonctionnement | Charge mood. |

#### `ModerationSearchActorByName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params.searchString, pageIndex, pageSize + 1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Fonctionnement | Endpoint AMF `ModerationSearchActorByName`. |

#### `ModerationSearchActorId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `FriendBrowserView.as` |
| Fonctionnement | Endpoint AMF `ModerationSearchActorId`. |

#### `ModerationSearchMassDeleteActorByName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params.searchString, pageIndex, pageSize + 1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `FriendBrowserView.as` |
| Fonctionnement | Endpoint AMF `ModerationSearchMassDeleteActorByName`. |

#### `PickupGuidePresent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, type, index |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `Code` (popup) |
| Codes retour | Champ `Code` == −429 (popup) |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `GiftHuntManager.as` |
| Fonctionnement | Endpoint AMF `PickupGuidePresent`. |

#### `PurchaseRecoloring`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `PopupRecolor.as` |
| Fonctionnement | Endpoint AMF `PurchaseRecoloring`. |

#### `ReportActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `CoreReloadListeners.as` |
| Fonctionnement | Endpoint AMF `ReportActor`. |

#### `SaveActorAddress`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `PaymentOverviewController.as` |
| Fonctionnement | Sauvegarde / crée save actor address. |

#### `SaveActorSoundMuted`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `TopBar.as` |
| Fonctionnement | Sauvegarde / crée save actor sound muted. |

#### `SaveBirthInfoWithTicket`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Fonctionnement | Sauvegarde / crée save birth info with ticket. |

#### `SaveLevelUpGiftSelect`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Fonctionnement | Sauvegarde / crée save level up gift select. |

#### `SearchActorByNameNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Fonctionnement | Recherche actor by name neb. |

#### `SetColorOnActorItemNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Fonctionnement | Met à jour color on actor item new. |

#### `SetMoodWithModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Fonctionnement | Met à jour mood with moderation call. |

#### `UnblockActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Fonctionnement | Endpoint AMF `UnblockActor`. |

#### `UnblockActorNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Fonctionnement | Endpoint AMF `UnblockActorNeb`. |

#### `ValidateCaptcha`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `RegisterNewUserComponent.as` |
| Fonctionnement | Endpoint AMF `ValidateCaptcha`. |

#### `fameOverhaul`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / appelants | `LoginRequiredSetupCommand.as`, `PostLoginSequence.as` |
| Fonctionnement | Endpoint AMF `fameOverhaul`. |

#### `getWallActivitiesForActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pagingOptions.actorId, pagingOptions.activityType, pagingOptions.pageIndex, pagingOptions.pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / appelants | `WallList.as` |
| Fonctionnement | Endpoint AMF `getWallActivitiesForActor`. |

## `WebService.AppSettings.AMFAppSettingsService`

**Chemin AMF :** `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetAppSetting` | param1 | Récupère app setting. | — |
| `GetAppSettings` | param1 | Récupère app settings. | — |

### Détail endpoints

#### `GetAppSetting`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/configurations/service/AMFAppSettingsService.as` (+1) |
| UI / appelants | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as`, `SessionAmfServiceForWeb.as` |
| Fonctionnement | Récupère app setting. |

#### `GetAppSettings`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/configurations/service/AMFAppSettingsService.as` (+1) |
| UI / appelants | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as` |
| Fonctionnement | Récupère app settings. |

## `WebService.AppSettings.AMFAppSettingsServiceMobile`

**Chemin AMF :** `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsServiceMobile`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetAppSetting` | param1 | Récupère app setting. | — |
| `GetAppSettings` | param1 | Récupère app settings. | — |

### Détail endpoints

#### `GetAppSetting`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/configurations/service/AMFAppSettingsServiceMobile.as` (+1) |
| UI / appelants | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as`, `SessionAmfServiceForWeb.as` |
| Fonctionnement | Récupère app setting. |

#### `GetAppSettings`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/configurations/service/AMFAppSettingsServiceMobile.as` (+1) |
| UI / appelants | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as` |
| Fonctionnement | Récupère app settings. |

## `WebService.Nebula.AMFNebulaService`

**Chemin AMF :** `MovieStarPlanet.WebService.Nebula.AMFNebulaService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetProfileId` | param1 | Récupère profile id. | — |
| `GetProfileIds` | missing | Récupère profile ids. | — |
| `GetProfiles` | param1 | Récupère profiles. | — |

### Détail endpoints

#### `GetProfileId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/service/rest/nebula/NebulaProfileAMFService.as` |
| UI / appelants | `FriendConnectedActivityFilter.as`, `FriendshipManager.as`, `FriendActivityListComponent.as`, `ChecksumCalculator.as` (+11) |
| Fonctionnement | Récupère profile id. |

#### `GetProfileIds`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | missing |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/service/rest/nebula/NebulaProfileAMFService.as` |
| UI / appelants | `ChecksumCalculator.as` |
| Fonctionnement | Récupère profile ids. |

#### `GetProfiles`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/service/rest/nebula/NebulaProfileAMFService.as` |
| Fonctionnement | Récupère profiles. |

## `WebService.ParentalConsent.AMFParentalConsentService`

**Chemin AMF :** `MovieStarPlanet.WebService.ParentalConsent.AMFParentalConsentService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetActorParentalConsent` | param1 | Récupère actor parental consent. | — |
| `GetUserType` | param1 | Récupère user type. | — |
| `GrantParentalConsent` | param1, param2 | Endpoint AMF `GrantParentalConsent`. | — |
| `HasVisibleParentalConsentCode` | param1 | Endpoint AMF `HasVisibleParentalConsentCode`. | — |
| `HideParentalConsentCode` | param1 | Endpoint AMF `HideParentalConsentCode`. | — |
| `MatchActorIdToParentalConsentConfirmCode` | param1, param2 | Endpoint AMF `MatchActorIdToParentalConsentConfirmCode`. | — |
| `ReSendParentalConsentCode` | param1 | Endpoint AMF `ReSendParentalConsentCode`. | — |
| `RememberParentalConsentCode` | param1 | Endpoint AMF `RememberParentalConsentCode`. | — |
| `RequestParentalConsent` | param1 | Endpoint AMF `RequestParentalConsent`. | — |
| `SaveParentEmailAddress` | param1, param2 | Sauvegarde / crée save parent email address. | — |
| `SetActorsParentalConsent` | param1, param2 | Met à jour actors parental consent. | — |

### Détail endpoints

#### `GetActorParentalConsent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `TestingForm.as`, `EnterParentalCodePopup.as` |
| Fonctionnement | Récupère actor parental consent. |

#### `GetUserType`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `ParentalConsentHandler.as` |
| Fonctionnement | Récupère user type. |

#### `GrantParentalConsent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `ConfirmParentalConsentPopup.as` |
| Fonctionnement | Endpoint AMF `GrantParentalConsent`. |

#### `HasVisibleParentalConsentCode`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `PaymentsViewBase.as` |
| Fonctionnement | Endpoint AMF `HasVisibleParentalConsentCode`. |

#### `HideParentalConsentCode`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `RemoveParentalConsentCodePopup.as` |
| Fonctionnement | Endpoint AMF `HideParentalConsentCode`. |

#### `MatchActorIdToParentalConsentConfirmCode`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `ParentalConsentHandler.as` |
| Fonctionnement | Endpoint AMF `MatchActorIdToParentalConsentConfirmCode`. |

#### `ReSendParentalConsentCode`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `EnterParentalCodePopup.as` |
| Fonctionnement | Endpoint AMF `ReSendParentalConsentCode`. |

#### `RememberParentalConsentCode`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `EnterParentalCodePopup.as` |
| Fonctionnement | Endpoint AMF `RememberParentalConsentCode`. |

#### `RequestParentalConsent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `ParentalConsentPopup.as` |
| Fonctionnement | Endpoint AMF `RequestParentalConsent`. |

#### `SaveParentEmailAddress`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `ParentalConsentPopup.as` |
| Fonctionnement | Sauvegarde / crée save parent email address. |

#### `SetActorsParentalConsent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / appelants | `TestingForm.as` |
| Fonctionnement | Met à jour actors parental consent. |

## `WebService.Payment.AMFPaymentService`

**Chemin AMF :** `MovieStarPlanet.WebService.Payment.AMFPaymentService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `DisableAutomaticRenewal` | param1 | Endpoint AMF `DisableAutomaticRenewal`. | — |
| `GetAvailablePurchaseTypes` | actorId | Récupère available purchase types. | — |
| `GetBokuBuyUrlNew` | param1, param2, param3, param4, param5 | Récupère boku buy url new. | — |
| `GetBokuPricePoints` | — | Récupère boku price points. | — |
| `GetCurrentPaymentPossibilities` | types | Récupère current payment possibilities. | — |
| `GetRecurringPaymentSubscription` | param1 | Récupère recurring payment subscription. | — |
| `GetTimeLimitedPurchaseType` | actorId | Récupère time limited purchase type. | — |
| `GetTransactionPurchaseInfo` | param1, param2 | Récupère transaction purchase info. | — |
| `GetTransactionPurchaseInfoWeb` | param1, param2 | Récupère transaction purchase info web. | — |
| `GetTransactionPurchaseList` | param1, param2, param3 | Récupère transaction purchase list. | — |
| `GetTransactionPurchaseListIncludingManual` | param1, param2, param3 | Récupère transaction purchase list including manual. | — |
| `VerifyBokuTransaction` | param1 | Endpoint AMF `VerifyBokuTransaction`. | — |

### Détail endpoints

#### `DisableAutomaticRenewal`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `IndigenousServiceInteraciton.as`, `UnifiedRecurringPaymentServiceProxy.as` |
| Fonctionnement | Endpoint AMF `DisableAutomaticRenewal`. |

#### `GetAvailablePurchaseTypes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `PaymentManagerPesos.as`, `IndigenousServiceInteraciton.as`, `PesosServiceInteraction.as` |
| Fonctionnement | Récupère available purchase types. |

#### `GetBokuBuyUrlNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| Fonctionnement | Récupère boku buy url new. |

#### `GetBokuPricePoints`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `GiftCertificatePaymentManager.as`, `PaymentCaching.as`, `IndigenousServiceInteraciton.as` |
| Fonctionnement | Récupère boku price points. |

#### `GetCurrentPaymentPossibilities`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | types |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `AbstractCertificateWindow.as`, `ChecksumCalculator.as`, `PurchaseTopUpAndVipButton.as`, `OffersView.as` (+4) |
| Fonctionnement | Récupère current payment possibilities. |

#### `GetRecurringPaymentSubscription`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `PaymentsViewBase.as`, `DisableRecurringPaymentLoginPopup.as`, `SelectPaymentView.as`, `IndigenousServiceInteraciton.as` (+1) |
| Fonctionnement | Récupère recurring payment subscription. |

#### `GetTimeLimitedPurchaseType`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| Fonctionnement | Récupère time limited purchase type. |

#### `GetTransactionPurchaseInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `PaymentManager.as`, `PaymentActorReloadListener.as`, `PaymentManagerPesos.as`, `IndigenousServiceInteraciton.as` (+1) |
| Fonctionnement | Récupère transaction purchase info. |

#### `GetTransactionPurchaseInfoWeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| Fonctionnement | Récupère transaction purchase info web. |

#### `GetTransactionPurchaseList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `PaymentsView.as`, `IndigenousServiceInteraciton.as` |
| Fonctionnement | Récupère transaction purchase list. |

#### `GetTransactionPurchaseListIncludingManual`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `PaymentsView.as`, `IndigenousServiceInteraciton.as` |
| Fonctionnement | Récupère transaction purchase list including manual. |

#### `VerifyBokuTransaction`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / appelants | `MiscRegistrator.as`, `IndigenousServiceInteraciton.as` |
| Fonctionnement | Endpoint AMF `VerifyBokuTransaction`. |

## `WebService.User.AMFUserServiceWeb`

**Chemin AMF :** `MovieStarPlanet.WebService.User.AMFUserServiceWeb`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CommentEntity` | entityComment | Endpoint AMF `CommentEntity`. | — |
| `CreateNewUserWithSecureSnapshotV2` | param1, param2, null, param3, param4 | Sauvegarde / crée create new user with secure snapshot v2. | — |
| `EntityCommentDelete` | param1, param2 | Endpoint AMF `EntityCommentDelete`. | — |
| `GetActorPersonalInfo` | param1, "" | Récupère actor personal info. | — |
| `GetEntityComments` | entityType, entityId, pageIndex, pageSize | Récupère entity comments. | — |
| `IsCommunicationAllowedWith` | communicationType, actorid | Endpoint AMF `IsCommunicationAllowedWith`. | — |
| `IsCommunicationAllowedWithNeb` | communicationType, profileId | Endpoint AMF `IsCommunicationAllowedWithNeb`. | — |
| `LogInput` | locationId, actorId, roomInstanceId, message, destinationType | Endpoint AMF `LogInput`. | — |
| `LogInputGroupChat` | locationId, actorId, roomInstanceId, message, destinationType | Endpoint AMF `LogInputGroupChat`. | — |
| `LogInputWithConditionalModerationCall` | locationId, actorId, roomInstanceId, message, destinationType, isUserRestricted | Endpoint AMF `LogInputWithConditionalModerationCall`. | — |
| `Login` | userName, password, null, null, deviceId, dfp | Endpoint AMF `Login`. | — |
| `LoginModeratorV2` | username, password, userIps, otp, null, null | Endpoint AMF `LoginModeratorV2`. | — |
| `LoginV2` | username, passwordHash, deviceInfo, ... | Connexion web credentials + fingerprint ; retourne session + actor bundle. | — |
| `SaveChatAllowed` | param1, param2 | Sauvegarde / crée save chat allowed. | — |
| `UpdateActorPersonalInfo` | param1, param2 | Met à jour ate actor personal info. | — |

### Détail endpoints

#### `CommentEntity`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | entityComment |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/comments/CommentComponents/AmfCommentService.as` |
| UI / appelants | `CommentNewComponent.as`, `CommentUtils.as`, `CommentsComponent.as`, `CommentCreator.as` (+1) |
| Fonctionnement | Endpoint AMF `CommentEntity`. |

#### `CreateNewUserWithSecureSnapshotV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, null, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` (+1) |
| Fonctionnement | Sauvegarde / crée create new user with secure snapshot v2. |

#### `EntityCommentDelete`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/comments/CommentComponents/AmfCommentService.as` |
| UI / appelants | `LookCommentItemComponent.as`, `CommentListItemRenderer.as`, `EntityCommentDataItem.as`, `DropDownPanelItemRenderer.as` |
| Fonctionnement | Endpoint AMF `EntityCommentDelete`. |

#### `GetActorPersonalInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, "" |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| UI / appelants | `ConfirmParentalConsentPopup.as` |
| Fonctionnement | Récupère actor personal info. |

#### `GetEntityComments`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | entityType, entityId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/comments/CommentComponents/AmfCommentService.as` |
| UI / appelants | `CommentsComponent.as`, `Pager.as`, `CommentsList.as`, `CommentsList.as` |
| Fonctionnement | Récupère entity comments. |

#### `IsCommunicationAllowedWith`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | communicationType, actorid |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` (+1) |
| UI / appelants | `MessagingFacade.as`, `OneToOneChatDataItem.as`, `Wall.as` |
| Fonctionnement | Endpoint AMF `IsCommunicationAllowedWith`. |

#### `IsCommunicationAllowedWithNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | communicationType, profileId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Fonctionnement | Endpoint AMF `IsCommunicationAllowedWithNeb`. |

#### `LogInput`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | locationId, actorId, roomInstanceId, message, destinationType |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceWeb.as` (+2) |
| UI / appelants | `ManageClub.as`, `CommentNewComponent.as`, `MonsterPopup.as`, `MyLooksEditor.as` (+21) |
| Fonctionnement | Endpoint AMF `LogInput`. |

#### `LogInputGroupChat`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | locationId, actorId, roomInstanceId, message, destinationType |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceWeb.as` (+1) |
| UI / appelants | `InputLoggingHandler.as` |
| Fonctionnement | Endpoint AMF `LogInputGroupChat`. |

#### `LogInputWithConditionalModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | locationId, actorId, roomInstanceId, message, destinationType, isUserRestricted |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceWeb.as` (+1) |
| UI / appelants | `InputLoggingHandler.as` |
| Fonctionnement | Endpoint AMF `LogInputWithConditionalModerationCall`. |

#### `Login`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | userName, password, null, null, deviceId, dfp |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| UI / appelants | `Main.as`, `MainLogic.as`, `Remoting.as`, `MainPanel.as` (+91) |
| Fonctionnement | Endpoint AMF `Login`. |

#### `LoginModeratorV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | username, password, userIps, otp, null, null |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Fonctionnement | Endpoint AMF `LoginModeratorV2`. |

#### `LoginV2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | username, passwordHash, deviceInfo, ... |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Fonctionnement | Connexion web credentials + fingerprint ; retourne session + actor bundle. |

#### `SaveChatAllowed`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| UI / appelants | `TestingForm.as` |
| Fonctionnement | Sauvegarde / crée save chat allowed. |

#### `UpdateActorPersonalInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Fonctionnement | Met à jour ate actor personal info. |

## `WebService.UserSession.AMFUserSessionService`

**Chemin AMF :** `MovieStarPlanet.WebService.UserSession.AMFUserSessionService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AwardStartupReward` | param1 | Endpoint AMF `AwardStartupReward`. | — |
| `BadWordCountAdd` | param1, param2 | Endpoint AMF `BadWordCountAdd`. | — |
| `BadWordCountClear` | param1 | Endpoint AMF `BadWordCountClear`. | — |
| `ChangePasswordNew` | param1, param2, param3 | Endpoint AMF `ChangePasswordNew`. | — |
| `DeleteUser` | param1, param2, param3 | Supprime e user. | — |
| `EmailChanged` | actorId, mail, username, password, emailSettings | Endpoint AMF `EmailChanged`. | — |
| `EmailValidated` | actorId | Endpoint AMF `EmailValidated`. | — |
| `EmailValidatedCancel` | param1 | Endpoint AMF `EmailValidatedCancel`. | — |
| `GetActorEmail` | actorId | Récupère actor email. | — |
| `GetActorIdFromName` | name | Récupère actor id from name. | — |
| `GetActorNameFromId` | actorId | Récupère actor name from id. | — |
| `GetMarketingStepGift` | param1 | Récupère marketing step gift. | — |
| `GiveAutographAndCalculateTimestamp` | actorId, receiverId | Donne un autographe ; cooldown 1h non-VIP ; `Fame==-429` rate limit. | `-429` |
| `GiveAutographAndCalculateTimestampNeb` | actorId, receiverProfileId | Endpoint AMF `GiveAutographAndCalculateTimestampNeb`. | `-429` |
| `LoadActorDetails2` | actorId, updateProfileDisplayCount, callerId | Charge actor details2. | — |
| `LoadActorDetailsExtended` | actorId | Charge actor details extended. | — |
| `LoadActorDetailsVersion` | actorId, updateProfileDisplayCount | Charge actor details version. | — |
| `MassDeleteUsers` | usersIdsTobeDeleted, userName, password | Endpoint AMF `MassDeleteUsers`. | — |
| `RecoverUserFromEmailHistory` | actorName, email | Endpoint AMF `RecoverUserFromEmailHistory`. | — |
| `RenameUser` | actorId, newActorName, moderatorName, moderatorPass | Endpoint AMF `RenameUser`. | — |
| `ResyncLogin` | actorId | Endpoint AMF `ResyncLogin`. | — |
| `SendEmailValidation` | param1, param2, param3, param4, param5 | Endpoint AMF `SendEmailValidation`. | — |
| `SendNewEmailValidation` | param1, param2, param3, param4, param5, param6 | Endpoint AMF `SendNewEmailValidation`. | — |
| `SendUserParentEmailValidation` | param1, param2, param3, param4, param5, param6 | Endpoint AMF `SendUserParentEmailValidation`. | — |
| `SetEmailSettings` | actorId, actorName, emailSettings | Met à jour email settings. | — |
| `SetFacebookId` | param1, param2 | Met à jour facebook id. | — |
| `SetMarketingStep` | param1, param2, param3 | Met à jour marketing step. | — |
| `UndeleteUser` | userIdTobeDeleted, userName, password | Endpoint AMF `UndeleteUser`. | — |
| `UpdateBehaviourStatusNew` | actorId, behaviourStatus, lockedText, chatLogId, handledByActorId | Met à jour ate behaviour status new. | — |
| `UpdateGift` | actorId | Met à jour ate gift. | — |
| `UpdateMySchool` | actorId, passwordHash, schoolId, schoolYear | Met à jour ate my school. | — |
| `UpdateRetention` | actorId | Met à jour ate retention. | — |
| `deleteBioText` | actorId, moderatorName, moderatorPass | Endpoint AMF `deleteBioText`. | — |
| `eraseEmail` | email, moderatorName, moderatorPass | Endpoint AMF `eraseEmail`. | — |

### Détail endpoints

#### `AwardStartupReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| Fonctionnement | Endpoint AMF `AwardStartupReward`. |

#### `BadWordCountAdd`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `BadWordCountAdd`. |

#### `BadWordCountClear`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `BadWordsActorForm.as`, `AdminManager.as` |
| Fonctionnement | Endpoint AMF `BadWordCountClear`. |

#### `ChangePasswordNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `ChangePasswordNew`. |

#### `DeleteUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `_com_moviestarplanet_Forms_DeleteUserWatcherSetupUtil.as`, `DeleteUser.as`, `Help.as`, `GraphQueryLanguageUtil.as` |
| Fonctionnement | Supprime e user. |

#### `EmailChanged`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, mail, username, password, emailSettings |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `EmailChanged`. |

#### `EmailValidated`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `ValidateEmailNew.as`, `ChecksumCalculator.as`, `BasePopupFlowController.as`, `PostLoginHandler.as` (+2) |
| Fonctionnement | Endpoint AMF `EmailValidated`. |

#### `EmailValidatedCancel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `EmailValidatedCancel`. |

#### `GetActorEmail`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `TagInterpreterLayoutPopup.as` |
| Fonctionnement | Récupère actor email. |

#### `GetActorIdFromName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | name |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Récupère actor id from name. |

#### `GetActorNameFromId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `ConfirmParentalConsentPopup.as` |
| Fonctionnement | Récupère actor name from id. |

#### `GetMarketingStepGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| Fonctionnement | Récupère marketing step gift. |

#### `GiveAutographAndCalculateTimestamp`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, receiverId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `Fame` (popup) |
| Codes retour | Champ `Fame` == −429 (popup) |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `GiveAutographButton.as`, `AutographController.as` |
| Fonctionnement | Donne un autographe ; cooldown 1h non-VIP ; `Fame==-429` rate limit. |

#### `GiveAutographAndCalculateTimestampNeb`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, receiverProfileId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `Fame` (popup) |
| Codes retour | Champ `Fame` == −429 (popup) |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `GiveAutographAndCalculateTimestampNeb`. |

#### `LoadActorDetails2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, updateProfileDisplayCount, callerId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `ActorAdmin.as` |
| Fonctionnement | Charge actor details2. |

#### `LoadActorDetailsExtended`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+2) |
| UI / appelants | `UpdateModerationStatusCommand.as`, `ActorReload.as`, `ActorDetailsReloadingMob.as` |
| Fonctionnement | Charge actor details extended. |

#### `LoadActorDetailsVersion`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, updateProfileDisplayCount |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Charge actor details version. |

#### `MassDeleteUsers`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | usersIdsTobeDeleted, userName, password |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `FriendBrowserView.as` |
| Fonctionnement | Endpoint AMF `MassDeleteUsers`. |

#### `RecoverUserFromEmailHistory`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorName, email |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `_com_moviestarplanet_Forms_RecoverUserFromEmailHistoryWatcherSetupUtil.as`, `Help.as`, `RecoverUserFromEmailHistory.as` |
| Fonctionnement | Endpoint AMF `RecoverUserFromEmailHistory`. |

#### `RenameUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, newActorName, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `ActorAdmin.as` |
| Fonctionnement | Endpoint AMF `RenameUser`. |

#### `ResyncLogin`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `LoginCommand.as` |
| Fonctionnement | Endpoint AMF `ResyncLogin`. |

#### `SendEmailValidation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `ValidateEmailNew.as`, `BasePopupFlowController.as` |
| Fonctionnement | Endpoint AMF `SendEmailValidation`. |

#### `SendNewEmailValidation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `SendNewEmailValidation`. |

#### `SendUserParentEmailValidation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `SendUserParentEmailValidation`. |

#### `SetEmailSettings`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorName, emailSettings |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `ChangeEmailSettings.as` |
| Fonctionnement | Met à jour email settings. |

#### `SetFacebookId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Met à jour facebook id. |

#### `SetMarketingStep`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / appelants | `PostLoginSequence.as` |
| Fonctionnement | Met à jour marketing step. |

#### `UndeleteUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | userIdTobeDeleted, userName, password |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `ActorAdmin.as` |
| Fonctionnement | Endpoint AMF `UndeleteUser`. |

#### `UpdateBehaviourStatusNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, behaviourStatus, lockedText, chatLogId, handledByActorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Met à jour ate behaviour status new. |

#### `UpdateGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / appelants | `OverviewMap.as`, `HandleFreeGiftsCommand.as`, `PostLoginSequence.as` |
| Fonctionnement | Met à jour ate gift. |

#### `UpdateMySchool`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, passwordHash, schoolId, schoolYear |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / appelants | `SchoolSettingsController.as` |
| Fonctionnement | Met à jour ate my school. |

#### `UpdateRetention`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / appelants | `PostLoginSequence.as` |
| Fonctionnement | Met à jour ate retention. |

#### `deleteBioText`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Fonctionnement | Endpoint AMF `deleteBioText`. |

#### `eraseEmail`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | email, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / appelants | `EraseEmailForm.as` |
| Fonctionnement | Endpoint AMF `eraseEmail`. |

## `WebService.UserSession.AMFUserSessionServiceForMobile`

**Chemin AMF :** `MovieStarPlanet.WebService.UserSession.AMFUserSessionServiceForMobile`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `UpdateGift` | actorId | Met à jour ate gift. | — |

### Détail endpoints

#### `UpdateGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / appelants | `OverviewMap.as`, `HandleFreeGiftsCommand.as`, `PostLoginSequence.as` |
| Fonctionnement | Met à jour ate gift. |

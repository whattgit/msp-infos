# III.2 — Authentication & session

> **EN** · [Français](../../fr/amf/02-auth.md)


Login, account, Nebula, parental consent, payments.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `GiveAutographAndCalculateTimestamp` | `AMFUserSessionService` | `Fame` | Yes |
| `GiveAutographAndCalculateTimestampNeb` | `AMFActorService` | `Fame` | Yes |
| `PickupGuidePresent` | `AMFActorService` | `Code` | Yes |

## `WebService.AMFActorService`

**AMF path:** `MovieStarPlanet.WebService.AMFActorService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BlockActor` | param1, param2 | AMF endpoint `BlockActor`. | — |
| `BlockActorNeb` | param1, param2 | AMF endpoint `BlockActorNeb`. | — |
| `BulkLoadActors` | param1 | AMF endpoint `BulkLoadActors`. | — |
| `BuyClothesNew` | actorId, clothes[] | Achat vêtements variante mobile (`AMFActorService`) sans lookId. | — |
| `CreateNewUserWithSecureSnapshotV2` | newActorCreationData, checksum, store, deviceId, snapshotSmall, snapshotBig | Saves / creates create new user with secure snapshot v2. | — |
| `GetActorIdByName` | param1 | Fetches actor id by name. | — |
| `GetActorZooItems` | param1 | Fetches actor zoo items. | — |
| `GetClothesFromNewestClothesSection` | param1, param2, param3 | Fetches clothes from newest clothes section. | — |
| `GetPagedClothByCategoryGroups` | param1, _loc5_ | Paged list — Paged Cloth By Category Groups. | — |
| `GetPagedClothByCategoryGroups_14` | param1, _loc5_ | Paged list — Paged Cloth By Category Groups 14. | — |
| `GetPostLoginBundle` | actorId | Données post-login : tenue, settings, candy prices, todos. | — |
| `IsActorNameUsed` | param1 | AMF endpoint `IsActorNameUsed`. | — |
| `IsNameBlocked` | param1 | AMF endpoint `IsNameBlocked`. | — |
| `LoadActorDetails` | param1, param2 | Loads actor details. | — |
| `LoadActorDetailsExtended` | param1 | Loads actor details extended. | — |
| `LoadActorItems` | param1 | Loads actor items. | — |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 | Loads actor with current clothes and spritesheet. | — |
| `LoadActorWithCurrentClothesBasicDataOnlyRevised` | param1 | Loads actor with current clothes basic data only revised. | — |
| `LoadActorsVipDetails` | param1 | Loads actors vip details. | — |
| `LoadBlockedAndBlockingActors` | param1 | Loads blocked and blocking actors. | — |
| `LoadBlockedAndBlockingActorsNeb` | param1 | Loads blocked and blocking actors neb. | — |
| `LoadDataForRegisterNewUser` | — | Loads data for register new user. | — |
| `LoadModeratorInformation` | param1 | Loads moderator information. | — |
| `LoadMood` | param1 | Loads mood. | — |
| `LoadMovieStarListRevised` | param1 | Loads movie star list revised. | — |
| `LockOutUser` | param1, param2, param3, param4, param5 | AMF endpoint `LockOutUser`. | — |
| `LoginMobile` | userId, redirectToken, version, store, deviceId | AMF endpoint `LoginMobile`. | — |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 | AMF endpoint `ModerationSearchActorByName`. | — |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 | AMF endpoint `ModerationSearchMassDeleteActorByName`. | — |
| `PickupGuidePresent` | actorId, type, index | AMF endpoint `PickupGuidePresent`. | `-429` |
| `ReportActor` | param1 | AMF endpoint `ReportActor`. | — |
| `ReportTabletAndroidConversion` | param1, param2 | AMF endpoint `ReportTabletAndroidConversion`. | — |
| `ReportTabletIOSConversion` | param1, param2 | AMF endpoint `ReportTabletIOSConversion`. | — |
| `RequestMobileStartupReward` | param1 | AMF endpoint `RequestMobileStartupReward`. | — |
| `SaveAlertWordsCount` | param1, param2 | Saves / creates save alert words count. | — |
| `SaveBirthInfoWithTicket` | param1, param2, param3 | Saves / creates save birth info with ticket. | — |
| `SearchActorByNameNeb` | param1, param2 | Searches actor by name neb. | — |
| `SearchActorByNameWithRequestStatus` | param1, param2 | Searches actor by name with request status. | — |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 | Updates mood with moderation call. | — |
| `SubmitMobileStartupReward` | param1, param2, param3 | AMF endpoint `SubmitMobileStartupReward`. | — |
| `ThirdPartyLoginDesktopV2` | param1, param2, param3, param4, param5 | AMF endpoint `ThirdPartyLoginDesktopV2`. | — |
| `ThirdPartyLoginMobileV2` | nacd, snapshotBig, snapshotSmall, username, password, version, store, deviceId | AMF endpoint `ThirdPartyLoginMobileV2`. | — |
| `UnblockActor` | param1, param2 | AMF endpoint `UnblockActor`. | — |
| `UnblockActorNeb` | param1, param2 | AMF endpoint `UnblockActorNeb`. | — |
| `UpdateClothes` | actorId, actorClothesRelIds[] | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. | — |
| `ValidateCaptcha` | param1, param2 | AMF endpoint `ValidateCaptcha`. | — |
| `fameOverhaul` | param1 | AMF endpoint `fameOverhaul`. | — |
| `loginMobileV2` | userName, password, version, store, deviceId, dfp | Connexion mobile. | — |

### Endpoint details

#### `BlockActor`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `BlockActor`. |

#### `BlockActorNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `BlockActorNeb`. |

#### `BulkLoadActors`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `BulkLoadActors`. |

#### `BuyClothesNew`

| Property | Value |
|----------|-------|
| Parameters | actorId, clothes[] |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Achat vêtements variante mobile (`AMFActorService`) sans lookId. |

#### `CreateNewUserWithSecureSnapshotV2`

| Property | Value |
|----------|-------|
| Parameters | newActorCreationData, checksum, store, deviceId, snapshotSmall, snapshotBig |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Behavior | Saves / creates create new user with secure snapshot v2. |

#### `GetActorIdByName`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Fetches actor id by name. |

#### `GetActorZooItems`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Fetches actor zoo items. |

#### `GetClothesFromNewestClothesSection`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| UI / callers | `SpendingRegistrator.as`, `ShopContentAmfService.as`, `ClothesShopModel.as`, `ClothesShopModel.as` (+1) |
| Behavior | Fetches clothes from newest clothes section. |

#### `GetPagedClothByCategoryGroups`

| Property | Value |
|----------|-------|
| Parameters | param1, _loc5_ |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Paged list — Paged Cloth By Category Groups. |

#### `GetPagedClothByCategoryGroups_14`

| Property | Value |
|----------|-------|
| Parameters | param1, _loc5_ |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Paged list — Paged Cloth By Category Groups 14. |

#### `GetPostLoginBundle`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `PostLoginHandler.as` |
| Behavior | Données post-login : tenue, settings, candy prices, todos. |

#### `IsActorNameUsed`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `ActorNameService.as` |
| Behavior | AMF endpoint `IsActorNameUsed`. |

#### `IsNameBlocked`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `ActorNameService.as` |
| Behavior | AMF endpoint `IsNameBlocked`. |

#### `LoadActorDetails`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `ActorAdmin.as`, `UpdateModerationStatusCommand.as`, `ActorReload.as`, `AbstractContentListItemRenderer.as` (+3) |
| Behavior | Loads actor details. |

#### `LoadActorDetailsExtended`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+2) |
| UI / callers | `UpdateModerationStatusCommand.as`, `ActorReload.as`, `ActorDetailsReloadingMob.as` |
| Behavior | Loads actor details extended. |

#### `LoadActorItems`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Loads actor items. |

#### `LoadActorWithCurrentClothesAndSpritesheet`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Behavior | Loads actor with current clothes and spritesheet. |

#### `LoadActorWithCurrentClothesBasicDataOnlyRevised`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| UI / callers | `FriendshipStatusUpdater.as` |
| Behavior | Loads actor with current clothes basic data only revised. |

#### `LoadActorsVipDetails`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Loads actors vip details. |

#### `LoadBlockedAndBlockingActors`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `ActorBlocking.as` |
| Behavior | Loads blocked and blocking actors. |

#### `LoadBlockedAndBlockingActorsNeb`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `ActorBlocking.as` |
| Behavior | Loads blocked and blocking actors neb. |

#### `LoadDataForRegisterNewUser`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `RegisterNewUserComponent.as` |
| Behavior | Loads data for register new user. |

#### `LoadModeratorInformation`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `CombatProfileUpdaterWeb.as` |
| Behavior | Loads moderator information. |

#### `LoadMood`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `TwitterConfig.as`, `MainViewMoviestarContainer.as` |
| Behavior | Loads mood. |

#### `LoadMovieStarListRevised`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `ActorCache.as` |
| Behavior | Loads movie star list revised. |

#### `LockOutUser`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `AdminManager.as`, `UserBehaviorServiceSettings.as` |
| Behavior | AMF endpoint `LockOutUser`. |

#### `LoginMobile`

| Property | Value |
|----------|-------|
| Parameters | userId, redirectToken, version, store, deviceId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `LoginMobile`. |

#### `ModerationSearchActorByName`

| Property | Value |
|----------|-------|
| Parameters | params.searchString, pageIndex, pageSize + 1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Behavior | AMF endpoint `ModerationSearchActorByName`. |

#### `ModerationSearchMassDeleteActorByName`

| Property | Value |
|----------|-------|
| Parameters | params.searchString, pageIndex, pageSize + 1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `FriendBrowserView.as` |
| Behavior | AMF endpoint `ModerationSearchMassDeleteActorByName`. |

#### `PickupGuidePresent`

| Property | Value |
|----------|-------|
| Parameters | actorId, type, index |
| AMF ticket | Yes |
| Rate limit | `-429` on `Code` (popup) |
| Return codes | Champ `Code` == −429 (popup) |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `GiftHuntManager.as` |
| Behavior | AMF endpoint `PickupGuidePresent`. |

#### `ReportActor`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `CoreReloadListeners.as` |
| Behavior | AMF endpoint `ReportActor`. |

#### `ReportTabletAndroidConversion`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `ReportTabletAndroidConversion`. |

#### `ReportTabletIOSConversion`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `ReportTabletIOSConversion`. |

#### `RequestMobileStartupReward`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `RequestMobileStartupReward`. |

#### `SaveAlertWordsCount`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Saves / creates save alert words count. |

#### `SaveBirthInfoWithTicket`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Behavior | Saves / creates save birth info with ticket. |

#### `SearchActorByNameNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Behavior | Searches actor by name neb. |

#### `SearchActorByNameWithRequestStatus`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Searches actor by name with request status. |

#### `SetMoodWithModerationCall`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| Behavior | Updates mood with moderation call. |

#### `SubmitMobileStartupReward`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `SubmitMobileStartupReward`. |

#### `ThirdPartyLoginDesktopV2`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `ThirdPartyLoginDesktopV2`. |

#### `ThirdPartyLoginMobileV2`

| Property | Value |
|----------|-------|
| Parameters | nacd, snapshotBig, snapshotSmall, username, password, version, store, deviceId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | AMF endpoint `ThirdPartyLoginMobileV2`. |

#### `UnblockActor`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Behavior | AMF endpoint `UnblockActor`. |

#### `UnblockActorNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Behavior | AMF endpoint `UnblockActorNeb`. |

#### `UpdateClothes`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorClothesRelIds[] |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `SaveClothesCommand.as` |
| Behavior | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. |

#### `ValidateCaptcha`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `RegisterNewUserComponent.as` |
| Behavior | AMF endpoint `ValidateCaptcha`. |

#### `fameOverhaul`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` (+1) |
| UI / callers | `LoginRequiredSetupCommand.as`, `PostLoginSequence.as` |
| Behavior | AMF endpoint `fameOverhaul`. |

#### `loginMobileV2`

| Property | Value |
|----------|-------|
| Parameters | userName, password, version, store, deviceId, dfp |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| Behavior | Connexion mobile. |

## `WebService.AMFUserService`

**AMF path:** `MovieStarPlanet.WebService.AMFUserService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `LogInput` | param1, param2, param3, param5, param4 | AMF endpoint `LogInput`. | — |
| `LogInputGroupChat` | param1, param2, param3, param5, param4 | AMF endpoint `LogInputGroupChat`. | — |
| `LogInputWithConditionalModerationCall` | param1, param2, param3, param4, param5, param6 | AMF endpoint `LogInputWithConditionalModerationCall`. | — |

### Endpoint details

#### `LogInput`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param5, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceMobile.as` (+2) |
| UI / callers | `ManageClub.as`, `CommentNewComponent.as`, `MonsterPopup.as`, `MyLooksEditor.as` (+21) |
| Behavior | AMF endpoint `LogInput`. |

#### `LogInputGroupChat`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param5, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceMobile.as` (+1) |
| UI / callers | `InputLoggingHandler.as` |
| Behavior | AMF endpoint `LogInputGroupChat`. |

#### `LogInputWithConditionalModerationCall`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceMobile.as` (+1) |
| UI / callers | `InputLoggingHandler.as` |
| Behavior | AMF endpoint `LogInputWithConditionalModerationCall`. |

## `WebService.ActorService.AMFActorServiceForWeb`

**AMF path:** `MovieStarPlanet.WebService.ActorService.AMFActorServiceForWeb`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BlockActor` | param1, param2 | AMF endpoint `BlockActor`. | — |
| `BlockActorNeb` | param1, param2 | AMF endpoint `BlockActorNeb`. | — |
| `BlockedActors` | param1 | AMF endpoint `BlockedActors`. | — |
| `ClaimAllLevelUpGifts` | param1, param2 | AMF endpoint `ClaimAllLevelUpGifts`. | — |
| `ClaimSingleLevelUpGift` | param1, param2, param3 | AMF endpoint `ClaimSingleLevelUpGift`. | — |
| `GetActorAddress` | actorId | Fetches actor address. | — |
| `GetLevelUpGiftChoices` | actorId | Fetches level up gift choices. | — |
| `GetLevelUpGiftSelects` | actorId | Fetches level up gift selects. | — |
| `GetLevelUps` | — | Fetches level ups. | — |
| `GetPostLoginBundle` | actorId | Données post-login : tenue, settings, candy prices, todos. | — |
| `GetPostLoginBundleStandalone` | param1 | Fetches post login bundle standalone. | — |
| `IsActorNameUsed` | param1 | AMF endpoint `IsActorNameUsed`. | — |
| `IsNameBlocked` | param1 | AMF endpoint `IsNameBlocked`. | — |
| `LoadActorDetails` | param1, param2 | Loads actor details. | — |
| `LoadActorDetailsExtended` | param1 | Loads actor details extended. | — |
| `LoadBlockedAndBlockingActors` | param1 | Loads blocked and blocking actors. | — |
| `LoadBlockedAndBlockingActorsNeb` | param1 | Loads blocked and blocking actors neb. | — |
| `LoadModeratorInformation` | param1 | Loads moderator information. | — |
| `LoadMood` | param1 | Loads mood. | — |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 | AMF endpoint `ModerationSearchActorByName`. | — |
| `ModerationSearchActorId` | actorId | AMF endpoint `ModerationSearchActorId`. | — |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 | AMF endpoint `ModerationSearchMassDeleteActorByName`. | — |
| `PickupGuidePresent` | actorId, type, index | AMF endpoint `PickupGuidePresent`. | `-429` |
| `PurchaseRecoloring` | param1, param2, param3, param4, param5 | AMF endpoint `PurchaseRecoloring`. | — |
| `ReportActor` | param1 | AMF endpoint `ReportActor`. | — |
| `SaveActorAddress` | param1 | Saves / creates save actor address. | — |
| `SaveActorSoundMuted` | param1, param2 | Saves / creates save actor sound muted. | — |
| `SaveBirthInfoWithTicket` | param1, param2, param3 | Saves / creates save birth info with ticket. | — |
| `SaveLevelUpGiftSelect` | param1, param2, param3 | Saves / creates save level up gift select. | — |
| `SearchActorByNameNeb` | param1, param2 | Searches actor by name neb. | — |
| `SetColorOnActorItemNew` | param1, param2, param3, param4, param5 | Updates color on actor item new. | — |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 | Updates mood with moderation call. | — |
| `UnblockActor` | param1, param2 | AMF endpoint `UnblockActor`. | — |
| `UnblockActorNeb` | param1, param2 | AMF endpoint `UnblockActorNeb`. | — |
| `ValidateCaptcha` | param1, param2 | AMF endpoint `ValidateCaptcha`. | — |
| `fameOverhaul` | param1 | AMF endpoint `fameOverhaul`. | — |
| `getWallActivitiesForActor` | pagingOptions.actorId, pagingOptions.activityType, pagingOptions.pageIndex, pagingOptions.pageSize | AMF endpoint `getWallActivitiesForActor`. | — |

### Endpoint details

#### `BlockActor`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `BlockActor`. |

#### `BlockActorNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `CharacterPopUp.as`, `FriendshipStatusUpdater.as` |
| Behavior | AMF endpoint `BlockActorNeb`. |

#### `BlockedActors`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `BlockedActorsListPopup.as`, `Settings.as`, `ActorBlocking.as`, `MessageSecurity.as` (+1) |
| Behavior | AMF endpoint `BlockedActors`. |

#### `ClaimAllLevelUpGifts`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `CongratsGiftPopupAnimation.as` |
| Behavior | AMF endpoint `ClaimAllLevelUpGifts`. |

#### `ClaimSingleLevelUpGift`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Behavior | AMF endpoint `ClaimSingleLevelUpGift`. |

#### `GetActorAddress`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `SelectPaymentView.as` |
| Behavior | Fetches actor address. |

#### `GetLevelUpGiftChoices`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Behavior | Fetches level up gift choices. |

#### `GetLevelUpGiftSelects`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Behavior | Fetches level up gift selects. |

#### `GetLevelUps`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `LevelUpPopupController.as` |
| Behavior | Fetches level ups. |

#### `GetPostLoginBundle`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `PostLoginHandler.as` |
| Behavior | Données post-login : tenue, settings, candy prices, todos. |

#### `GetPostLoginBundleStandalone`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Behavior | Fetches post login bundle standalone. |

#### `IsActorNameUsed`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `ActorNameService.as` |
| Behavior | AMF endpoint `IsActorNameUsed`. |

#### `IsNameBlocked`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `ActorNameService.as` |
| Behavior | AMF endpoint `IsNameBlocked`. |

#### `LoadActorDetails`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `ActorAdmin.as`, `UpdateModerationStatusCommand.as`, `ActorReload.as`, `AbstractContentListItemRenderer.as` (+3) |
| Behavior | Loads actor details. |

#### `LoadActorDetailsExtended`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+2) |
| UI / callers | `UpdateModerationStatusCommand.as`, `ActorReload.as`, `ActorDetailsReloadingMob.as` |
| Behavior | Loads actor details extended. |

#### `LoadBlockedAndBlockingActors`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `ActorBlocking.as` |
| Behavior | Loads blocked and blocking actors. |

#### `LoadBlockedAndBlockingActorsNeb`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `ActorBlocking.as` |
| Behavior | Loads blocked and blocking actors neb. |

#### `LoadModeratorInformation`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `CombatProfileUpdaterWeb.as` |
| Behavior | Loads moderator information. |

#### `LoadMood`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `TwitterConfig.as`, `MainViewMoviestarContainer.as` |
| Behavior | Loads mood. |

#### `ModerationSearchActorByName`

| Property | Value |
|----------|-------|
| Parameters | params.searchString, pageIndex, pageSize + 1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Behavior | AMF endpoint `ModerationSearchActorByName`. |

#### `ModerationSearchActorId`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `FriendBrowserView.as` |
| Behavior | AMF endpoint `ModerationSearchActorId`. |

#### `ModerationSearchMassDeleteActorByName`

| Property | Value |
|----------|-------|
| Parameters | params.searchString, pageIndex, pageSize + 1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `FriendBrowserView.as` |
| Behavior | AMF endpoint `ModerationSearchMassDeleteActorByName`. |

#### `PickupGuidePresent`

| Property | Value |
|----------|-------|
| Parameters | actorId, type, index |
| AMF ticket | Yes |
| Rate limit | `-429` on `Code` (popup) |
| Return codes | Champ `Code` == −429 (popup) |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `GiftHuntManager.as` |
| Behavior | AMF endpoint `PickupGuidePresent`. |

#### `PurchaseRecoloring`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `PopupRecolor.as` |
| Behavior | AMF endpoint `PurchaseRecoloring`. |

#### `ReportActor`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `CoreReloadListeners.as` |
| Behavior | AMF endpoint `ReportActor`. |

#### `SaveActorAddress`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `PaymentOverviewController.as` |
| Behavior | Saves / creates save actor address. |

#### `SaveActorSoundMuted`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `TopBar.as` |
| Behavior | Saves / creates save actor sound muted. |

#### `SaveBirthInfoWithTicket`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Behavior | Saves / creates save birth info with ticket. |

#### `SaveLevelUpGiftSelect`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Behavior | Saves / creates save level up gift select. |

#### `SearchActorByNameNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Behavior | Searches actor by name neb. |

#### `SetColorOnActorItemNew`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| Behavior | Updates color on actor item new. |

#### `SetMoodWithModerationCall`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| Behavior | Updates mood with moderation call. |

#### `UnblockActor`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Behavior | AMF endpoint `UnblockActor`. |

#### `UnblockActorNeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `BlockedActorComponent.as`, `CharacterPopUp.as` |
| Behavior | AMF endpoint `UnblockActorNeb`. |

#### `ValidateCaptcha`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `RegisterNewUserComponent.as` |
| Behavior | AMF endpoint `ValidateCaptcha`. |

#### `fameOverhaul`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` (+1) |
| UI / callers | `LoginRequiredSetupCommand.as`, `PostLoginSequence.as` |
| Behavior | AMF endpoint `fameOverhaul`. |

#### `getWallActivitiesForActor`

| Property | Value |
|----------|-------|
| Parameters | pagingOptions.actorId, pagingOptions.activityType, pagingOptions.pageIndex, pagingOptions.pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/ActorAmfServiceForWeb.as` |
| UI / callers | `WallList.as` |
| Behavior | AMF endpoint `getWallActivitiesForActor`. |

## `WebService.AppSettings.AMFAppSettingsService`

**AMF path:** `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetAppSetting` | param1 | Fetches app setting. | — |
| `GetAppSettings` | param1 | Fetches app settings. | — |

### Endpoint details

#### `GetAppSetting`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/configurations/service/AMFAppSettingsService.as` (+1) |
| UI / callers | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as`, `SessionAmfServiceForWeb.as` |
| Behavior | Fetches app setting. |

#### `GetAppSettings`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/configurations/service/AMFAppSettingsService.as` (+1) |
| UI / callers | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as` |
| Behavior | Fetches app settings. |

## `WebService.AppSettings.AMFAppSettingsServiceMobile`

**AMF path:** `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsServiceMobile`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetAppSetting` | param1 | Fetches app setting. | — |
| `GetAppSettings` | param1 | Fetches app settings. | — |

### Endpoint details

#### `GetAppSetting`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/configurations/service/AMFAppSettingsServiceMobile.as` (+1) |
| UI / callers | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as`, `SessionAmfServiceForWeb.as` |
| Behavior | Fetches app setting. |

#### `GetAppSettings`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/configurations/service/AMFAppSettingsServiceMobile.as` (+1) |
| UI / callers | `ChecksumCalculator.as`, `AppSettings.as`, `SessionAmfService.as` |
| Behavior | Fetches app settings. |

## `WebService.Nebula.AMFNebulaService`

**AMF path:** `MovieStarPlanet.WebService.Nebula.AMFNebulaService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetProfileId` | param1 | Fetches profile id. | — |
| `GetProfileIds` | missing | Fetches profile ids. | — |
| `GetProfiles` | param1 | Fetches profiles. | — |

### Endpoint details

#### `GetProfileId`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/service/rest/nebula/NebulaProfileAMFService.as` |
| UI / callers | `FriendConnectedActivityFilter.as`, `FriendshipManager.as`, `FriendActivityListComponent.as`, `ChecksumCalculator.as` (+11) |
| Behavior | Fetches profile id. |

#### `GetProfileIds`

| Property | Value |
|----------|-------|
| Parameters | missing |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/service/rest/nebula/NebulaProfileAMFService.as` |
| UI / callers | `ChecksumCalculator.as` |
| Behavior | Fetches profile ids. |

#### `GetProfiles`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/service/rest/nebula/NebulaProfileAMFService.as` |
| Behavior | Fetches profiles. |

## `WebService.ParentalConsent.AMFParentalConsentService`

**AMF path:** `MovieStarPlanet.WebService.ParentalConsent.AMFParentalConsentService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetActorParentalConsent` | param1 | Fetches actor parental consent. | — |
| `GetUserType` | param1 | Fetches user type. | — |
| `GrantParentalConsent` | param1, param2 | AMF endpoint `GrantParentalConsent`. | — |
| `HasVisibleParentalConsentCode` | param1 | AMF endpoint `HasVisibleParentalConsentCode`. | — |
| `HideParentalConsentCode` | param1 | AMF endpoint `HideParentalConsentCode`. | — |
| `MatchActorIdToParentalConsentConfirmCode` | param1, param2 | AMF endpoint `MatchActorIdToParentalConsentConfirmCode`. | — |
| `ReSendParentalConsentCode` | param1 | AMF endpoint `ReSendParentalConsentCode`. | — |
| `RememberParentalConsentCode` | param1 | AMF endpoint `RememberParentalConsentCode`. | — |
| `RequestParentalConsent` | param1 | AMF endpoint `RequestParentalConsent`. | — |
| `SaveParentEmailAddress` | param1, param2 | Saves / creates save parent email address. | — |
| `SetActorsParentalConsent` | param1, param2 | Updates actors parental consent. | — |

### Endpoint details

#### `GetActorParentalConsent`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `TestingForm.as`, `EnterParentalCodePopup.as` |
| Behavior | Fetches actor parental consent. |

#### `GetUserType`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `ParentalConsentHandler.as` |
| Behavior | Fetches user type. |

#### `GrantParentalConsent`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `ConfirmParentalConsentPopup.as` |
| Behavior | AMF endpoint `GrantParentalConsent`. |

#### `HasVisibleParentalConsentCode`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `PaymentsViewBase.as` |
| Behavior | AMF endpoint `HasVisibleParentalConsentCode`. |

#### `HideParentalConsentCode`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `RemoveParentalConsentCodePopup.as` |
| Behavior | AMF endpoint `HideParentalConsentCode`. |

#### `MatchActorIdToParentalConsentConfirmCode`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `ParentalConsentHandler.as` |
| Behavior | AMF endpoint `MatchActorIdToParentalConsentConfirmCode`. |

#### `ReSendParentalConsentCode`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `EnterParentalCodePopup.as` |
| Behavior | AMF endpoint `ReSendParentalConsentCode`. |

#### `RememberParentalConsentCode`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `EnterParentalCodePopup.as` |
| Behavior | AMF endpoint `RememberParentalConsentCode`. |

#### `RequestParentalConsent`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `ParentalConsentPopup.as` |
| Behavior | AMF endpoint `RequestParentalConsent`. |

#### `SaveParentEmailAddress`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `ParentalConsentPopup.as` |
| Behavior | Saves / creates save parent email address. |

#### `SetActorsParentalConsent`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/parentalconsent/service/ParentalAmfService.as` |
| UI / callers | `TestingForm.as` |
| Behavior | Updates actors parental consent. |

## `WebService.Payment.AMFPaymentService`

**AMF path:** `MovieStarPlanet.WebService.Payment.AMFPaymentService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `DisableAutomaticRenewal` | param1 | AMF endpoint `DisableAutomaticRenewal`. | — |
| `GetAvailablePurchaseTypes` | actorId | Fetches available purchase types. | — |
| `GetBokuBuyUrlNew` | param1, param2, param3, param4, param5 | Fetches boku buy url new. | — |
| `GetBokuPricePoints` | — | Fetches boku price points. | — |
| `GetCurrentPaymentPossibilities` | types | Fetches current payment possibilities. | — |
| `GetRecurringPaymentSubscription` | param1 | Fetches recurring payment subscription. | — |
| `GetTimeLimitedPurchaseType` | actorId | Fetches time limited purchase type. | — |
| `GetTransactionPurchaseInfo` | param1, param2 | Fetches transaction purchase info. | — |
| `GetTransactionPurchaseInfoWeb` | param1, param2 | Fetches transaction purchase info web. | — |
| `GetTransactionPurchaseList` | param1, param2, param3 | Fetches transaction purchase list. | — |
| `GetTransactionPurchaseListIncludingManual` | param1, param2, param3 | Fetches transaction purchase list including manual. | — |
| `VerifyBokuTransaction` | param1 | AMF endpoint `VerifyBokuTransaction`. | — |

### Endpoint details

#### `DisableAutomaticRenewal`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `IndigenousServiceInteraciton.as`, `UnifiedRecurringPaymentServiceProxy.as` |
| Behavior | AMF endpoint `DisableAutomaticRenewal`. |

#### `GetAvailablePurchaseTypes`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `PaymentManagerPesos.as`, `IndigenousServiceInteraciton.as`, `PesosServiceInteraction.as` |
| Behavior | Fetches available purchase types. |

#### `GetBokuBuyUrlNew`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| Behavior | Fetches boku buy url new. |

#### `GetBokuPricePoints`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `GiftCertificatePaymentManager.as`, `PaymentCaching.as`, `IndigenousServiceInteraciton.as` |
| Behavior | Fetches boku price points. |

#### `GetCurrentPaymentPossibilities`

| Property | Value |
|----------|-------|
| Parameters | types |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `AbstractCertificateWindow.as`, `ChecksumCalculator.as`, `PurchaseTopUpAndVipButton.as`, `OffersView.as` (+4) |
| Behavior | Fetches current payment possibilities. |

#### `GetRecurringPaymentSubscription`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `PaymentsViewBase.as`, `DisableRecurringPaymentLoginPopup.as`, `SelectPaymentView.as`, `IndigenousServiceInteraciton.as` (+1) |
| Behavior | Fetches recurring payment subscription. |

#### `GetTimeLimitedPurchaseType`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| Behavior | Fetches time limited purchase type. |

#### `GetTransactionPurchaseInfo`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `PaymentManager.as`, `PaymentActorReloadListener.as`, `PaymentManagerPesos.as`, `IndigenousServiceInteraciton.as` (+1) |
| Behavior | Fetches transaction purchase info. |

#### `GetTransactionPurchaseInfoWeb`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| Behavior | Fetches transaction purchase info web. |

#### `GetTransactionPurchaseList`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `PaymentsView.as`, `IndigenousServiceInteraciton.as` |
| Behavior | Fetches transaction purchase list. |

#### `GetTransactionPurchaseListIncludingManual`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `PaymentsView.as`, `IndigenousServiceInteraciton.as` |
| Behavior | Fetches transaction purchase list including manual. |

#### `VerifyBokuTransaction`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/payment/services/PaymentAmfService.as` |
| UI / callers | `MiscRegistrator.as`, `IndigenousServiceInteraciton.as` |
| Behavior | AMF endpoint `VerifyBokuTransaction`. |

## `WebService.User.AMFUserServiceWeb`

**AMF path:** `MovieStarPlanet.WebService.User.AMFUserServiceWeb`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CommentEntity` | entityComment | AMF endpoint `CommentEntity`. | — |
| `CreateNewUserWithSecureSnapshotV2` | param1, param2, null, param3, param4 | Saves / creates create new user with secure snapshot v2. | — |
| `EntityCommentDelete` | param1, param2 | AMF endpoint `EntityCommentDelete`. | — |
| `GetActorPersonalInfo` | param1, "" | Fetches actor personal info. | — |
| `GetEntityComments` | entityType, entityId, pageIndex, pageSize | Fetches entity comments. | — |
| `IsCommunicationAllowedWith` | communicationType, actorid | AMF endpoint `IsCommunicationAllowedWith`. | — |
| `IsCommunicationAllowedWithNeb` | communicationType, profileId | AMF endpoint `IsCommunicationAllowedWithNeb`. | — |
| `LogInput` | locationId, actorId, roomInstanceId, message, destinationType | AMF endpoint `LogInput`. | — |
| `LogInputGroupChat` | locationId, actorId, roomInstanceId, message, destinationType | AMF endpoint `LogInputGroupChat`. | — |
| `LogInputWithConditionalModerationCall` | locationId, actorId, roomInstanceId, message, destinationType, isUserRestricted | AMF endpoint `LogInputWithConditionalModerationCall`. | — |
| `Login` | userName, password, null, null, deviceId, dfp | AMF endpoint `Login`. | — |
| `LoginModeratorV2` | username, password, userIps, otp, null, null | AMF endpoint `LoginModeratorV2`. | — |
| `LoginV2` | username, passwordHash, deviceInfo, ... | Connexion web credentials + fingerprint ; retourne session + actor bundle. | — |
| `SaveChatAllowed` | param1, param2 | Saves / creates save chat allowed. | — |
| `UpdateActorPersonalInfo` | param1, param2 | Updates ate actor personal info. | — |

### Endpoint details

#### `CommentEntity`

| Property | Value |
|----------|-------|
| Parameters | entityComment |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/comments/CommentComponents/AmfCommentService.as` |
| UI / callers | `CommentNewComponent.as`, `CommentUtils.as`, `CommentsComponent.as`, `CommentCreator.as` (+1) |
| Behavior | AMF endpoint `CommentEntity`. |

#### `CreateNewUserWithSecureSnapshotV2`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, null, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` (+1) |
| Behavior | Saves / creates create new user with secure snapshot v2. |

#### `EntityCommentDelete`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/comments/CommentComponents/AmfCommentService.as` |
| UI / callers | `LookCommentItemComponent.as`, `CommentListItemRenderer.as`, `EntityCommentDataItem.as`, `DropDownPanelItemRenderer.as` |
| Behavior | AMF endpoint `EntityCommentDelete`. |

#### `GetActorPersonalInfo`

| Property | Value |
|----------|-------|
| Parameters | param1, "" |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| UI / callers | `ConfirmParentalConsentPopup.as` |
| Behavior | Fetches actor personal info. |

#### `GetEntityComments`

| Property | Value |
|----------|-------|
| Parameters | entityType, entityId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/comments/CommentComponents/AmfCommentService.as` |
| UI / callers | `CommentsComponent.as`, `Pager.as`, `CommentsList.as`, `CommentsList.as` |
| Behavior | Fetches entity comments. |

#### `IsCommunicationAllowedWith`

| Property | Value |
|----------|-------|
| Parameters | communicationType, actorid |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` (+1) |
| UI / callers | `MessagingFacade.as`, `OneToOneChatDataItem.as`, `Wall.as` |
| Behavior | AMF endpoint `IsCommunicationAllowedWith`. |

#### `IsCommunicationAllowedWithNeb`

| Property | Value |
|----------|-------|
| Parameters | communicationType, profileId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Behavior | AMF endpoint `IsCommunicationAllowedWithNeb`. |

#### `LogInput`

| Property | Value |
|----------|-------|
| Parameters | locationId, actorId, roomInstanceId, message, destinationType |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceWeb.as` (+2) |
| UI / callers | `ManageClub.as`, `CommentNewComponent.as`, `MonsterPopup.as`, `MyLooksEditor.as` (+21) |
| Behavior | AMF endpoint `LogInput`. |

#### `LogInputGroupChat`

| Property | Value |
|----------|-------|
| Parameters | locationId, actorId, roomInstanceId, message, destinationType |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceWeb.as` (+1) |
| UI / callers | `InputLoggingHandler.as` |
| Behavior | AMF endpoint `LogInputGroupChat`. |

#### `LogInputWithConditionalModerationCall`

| Property | Value |
|----------|-------|
| Parameters | locationId, actorId, roomInstanceId, message, destinationType, isUserRestricted |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/userbehavior/services/InputLoggingUserServiceWeb.as` (+1) |
| UI / callers | `InputLoggingHandler.as` |
| Behavior | AMF endpoint `LogInputWithConditionalModerationCall`. |

#### `Login`

| Property | Value |
|----------|-------|
| Parameters | userName, password, null, null, deviceId, dfp |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/mobileservice/ActorAmfService.as` |
| UI / callers | `Main.as`, `MainLogic.as`, `Remoting.as`, `MainPanel.as` (+91) |
| Behavior | AMF endpoint `Login`. |

#### `LoginModeratorV2`

| Property | Value |
|----------|-------|
| Parameters | username, password, userIps, otp, null, null |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Behavior | AMF endpoint `LoginModeratorV2`. |

#### `LoginV2`

| Property | Value |
|----------|-------|
| Parameters | username, passwordHash, deviceInfo, ... |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Behavior | Connexion web credentials + fingerprint ; retourne session + actor bundle. |

#### `SaveChatAllowed`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| UI / callers | `TestingForm.as` |
| Behavior | Saves / creates save chat allowed. |

#### `UpdateActorPersonalInfo`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/actorservice/service/UserAmfServiceWeb.as` |
| Behavior | Updates ate actor personal info. |

## `WebService.UserSession.AMFUserSessionService`

**AMF path:** `MovieStarPlanet.WebService.UserSession.AMFUserSessionService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AwardStartupReward` | param1 | AMF endpoint `AwardStartupReward`. | — |
| `BadWordCountAdd` | param1, param2 | AMF endpoint `BadWordCountAdd`. | — |
| `BadWordCountClear` | param1 | AMF endpoint `BadWordCountClear`. | — |
| `ChangePasswordNew` | param1, param2, param3 | AMF endpoint `ChangePasswordNew`. | — |
| `DeleteUser` | param1, param2, param3 | Deletes e user. | — |
| `EmailChanged` | actorId, mail, username, password, emailSettings | AMF endpoint `EmailChanged`. | — |
| `EmailValidated` | actorId | AMF endpoint `EmailValidated`. | — |
| `EmailValidatedCancel` | param1 | AMF endpoint `EmailValidatedCancel`. | — |
| `GetActorEmail` | actorId | Fetches actor email. | — |
| `GetActorIdFromName` | name | Fetches actor id from name. | — |
| `GetActorNameFromId` | actorId | Fetches actor name from id. | — |
| `GetMarketingStepGift` | param1 | Fetches marketing step gift. | — |
| `GiveAutographAndCalculateTimestamp` | actorId, receiverId | Donne un autographe ; cooldown 1h non-VIP ; `Fame==-429` rate limit. | `-429` |
| `GiveAutographAndCalculateTimestampNeb` | actorId, receiverProfileId | AMF endpoint `GiveAutographAndCalculateTimestampNeb`. | `-429` |
| `LoadActorDetails2` | actorId, updateProfileDisplayCount, callerId | Loads actor details2. | — |
| `LoadActorDetailsExtended` | actorId | Loads actor details extended. | — |
| `LoadActorDetailsVersion` | actorId, updateProfileDisplayCount | Loads actor details version. | — |
| `MassDeleteUsers` | usersIdsTobeDeleted, userName, password | AMF endpoint `MassDeleteUsers`. | — |
| `RecoverUserFromEmailHistory` | actorName, email | AMF endpoint `RecoverUserFromEmailHistory`. | — |
| `RenameUser` | actorId, newActorName, moderatorName, moderatorPass | AMF endpoint `RenameUser`. | — |
| `ResyncLogin` | actorId | AMF endpoint `ResyncLogin`. | — |
| `SendEmailValidation` | param1, param2, param3, param4, param5 | AMF endpoint `SendEmailValidation`. | — |
| `SendNewEmailValidation` | param1, param2, param3, param4, param5, param6 | AMF endpoint `SendNewEmailValidation`. | — |
| `SendUserParentEmailValidation` | param1, param2, param3, param4, param5, param6 | AMF endpoint `SendUserParentEmailValidation`. | — |
| `SetEmailSettings` | actorId, actorName, emailSettings | Updates email settings. | — |
| `SetFacebookId` | param1, param2 | Updates facebook id. | — |
| `SetMarketingStep` | param1, param2, param3 | Updates marketing step. | — |
| `UndeleteUser` | userIdTobeDeleted, userName, password | AMF endpoint `UndeleteUser`. | — |
| `UpdateBehaviourStatusNew` | actorId, behaviourStatus, lockedText, chatLogId, handledByActorId | Updates ate behaviour status new. | — |
| `UpdateGift` | actorId | Updates ate gift. | — |
| `UpdateMySchool` | actorId, passwordHash, schoolId, schoolYear | Updates ate my school. | — |
| `UpdateRetention` | actorId | Updates ate retention. | — |
| `deleteBioText` | actorId, moderatorName, moderatorPass | AMF endpoint `deleteBioText`. | — |
| `eraseEmail` | email, moderatorName, moderatorPass | AMF endpoint `eraseEmail`. | — |

### Endpoint details

#### `AwardStartupReward`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| Behavior | AMF endpoint `AwardStartupReward`. |

#### `BadWordCountAdd`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `BadWordCountAdd`. |

#### `BadWordCountClear`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `BadWordsActorForm.as`, `AdminManager.as` |
| Behavior | AMF endpoint `BadWordCountClear`. |

#### `ChangePasswordNew`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `ChangePasswordNew`. |

#### `DeleteUser`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `_com_moviestarplanet_Forms_DeleteUserWatcherSetupUtil.as`, `DeleteUser.as`, `Help.as`, `GraphQueryLanguageUtil.as` |
| Behavior | Deletes e user. |

#### `EmailChanged`

| Property | Value |
|----------|-------|
| Parameters | actorId, mail, username, password, emailSettings |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `EmailChanged`. |

#### `EmailValidated`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `ValidateEmailNew.as`, `ChecksumCalculator.as`, `BasePopupFlowController.as`, `PostLoginHandler.as` (+2) |
| Behavior | AMF endpoint `EmailValidated`. |

#### `EmailValidatedCancel`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `EmailValidatedCancel`. |

#### `GetActorEmail`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `TagInterpreterLayoutPopup.as` |
| Behavior | Fetches actor email. |

#### `GetActorIdFromName`

| Property | Value |
|----------|-------|
| Parameters | name |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | Fetches actor id from name. |

#### `GetActorNameFromId`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `ConfirmParentalConsentPopup.as` |
| Behavior | Fetches actor name from id. |

#### `GetMarketingStepGift`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| Behavior | Fetches marketing step gift. |

#### `GiveAutographAndCalculateTimestamp`

| Property | Value |
|----------|-------|
| Parameters | actorId, receiverId |
| AMF ticket | Yes |
| Rate limit | `-429` on `Fame` (popup) |
| Return codes | Champ `Fame` == −429 (popup) |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `GiveAutographButton.as`, `AutographController.as` |
| Behavior | Donne un autographe ; cooldown 1h non-VIP ; `Fame==-429` rate limit. |

#### `GiveAutographAndCalculateTimestampNeb`

| Property | Value |
|----------|-------|
| Parameters | actorId, receiverProfileId |
| AMF ticket | Yes |
| Rate limit | `-429` on `Fame` (popup) |
| Return codes | Champ `Fame` == −429 (popup) |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `GiveAutographAndCalculateTimestampNeb`. |

#### `LoadActorDetails2`

| Property | Value |
|----------|-------|
| Parameters | actorId, updateProfileDisplayCount, callerId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `ActorAdmin.as` |
| Behavior | Loads actor details2. |

#### `LoadActorDetailsExtended`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+2) |
| UI / callers | `UpdateModerationStatusCommand.as`, `ActorReload.as`, `ActorDetailsReloadingMob.as` |
| Behavior | Loads actor details extended. |

#### `LoadActorDetailsVersion`

| Property | Value |
|----------|-------|
| Parameters | actorId, updateProfileDisplayCount |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | Loads actor details version. |

#### `MassDeleteUsers`

| Property | Value |
|----------|-------|
| Parameters | usersIdsTobeDeleted, userName, password |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `FriendBrowserView.as` |
| Behavior | AMF endpoint `MassDeleteUsers`. |

#### `RecoverUserFromEmailHistory`

| Property | Value |
|----------|-------|
| Parameters | actorName, email |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `_com_moviestarplanet_Forms_RecoverUserFromEmailHistoryWatcherSetupUtil.as`, `Help.as`, `RecoverUserFromEmailHistory.as` |
| Behavior | AMF endpoint `RecoverUserFromEmailHistory`. |

#### `RenameUser`

| Property | Value |
|----------|-------|
| Parameters | actorId, newActorName, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `ActorAdmin.as` |
| Behavior | AMF endpoint `RenameUser`. |

#### `ResyncLogin`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `LoginCommand.as` |
| Behavior | AMF endpoint `ResyncLogin`. |

#### `SendEmailValidation`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `ValidateEmailNew.as`, `BasePopupFlowController.as` |
| Behavior | AMF endpoint `SendEmailValidation`. |

#### `SendNewEmailValidation`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `SendNewEmailValidation`. |

#### `SendUserParentEmailValidation`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `SendUserParentEmailValidation`. |

#### `SetEmailSettings`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorName, emailSettings |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `ChangeEmailSettings.as` |
| Behavior | Updates email settings. |

#### `SetFacebookId`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | Updates facebook id. |

#### `SetMarketingStep`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / callers | `PostLoginSequence.as` |
| Behavior | Updates marketing step. |

#### `UndeleteUser`

| Property | Value |
|----------|-------|
| Parameters | userIdTobeDeleted, userName, password |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `ActorAdmin.as` |
| Behavior | AMF endpoint `UndeleteUser`. |

#### `UpdateBehaviourStatusNew`

| Property | Value |
|----------|-------|
| Parameters | actorId, behaviourStatus, lockedText, chatLogId, handledByActorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | Updates ate behaviour status new. |

#### `UpdateGift`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / callers | `OverviewMap.as`, `HandleFreeGiftsCommand.as`, `PostLoginSequence.as` |
| Behavior | Updates ate gift. |

#### `UpdateMySchool`

| Property | Value |
|----------|-------|
| Parameters | actorId, passwordHash, schoolId, schoolYear |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / callers | `SchoolSettingsController.as` |
| Behavior | Updates ate my school. |

#### `UpdateRetention`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / callers | `PostLoginSequence.as` |
| Behavior | Updates ate retention. |

#### `deleteBioText`

| Property | Value |
|----------|-------|
| Parameters | actorId, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| Behavior | AMF endpoint `deleteBioText`. |

#### `eraseEmail`

| Property | Value |
|----------|-------|
| Parameters | email, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` |
| UI / callers | `EraseEmailForm.as` |
| Behavior | AMF endpoint `eraseEmail`. |

## `WebService.UserSession.AMFUserSessionServiceForMobile`

**AMF path:** `MovieStarPlanet.WebService.UserSession.AMFUserSessionServiceForMobile`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `UpdateGift` | actorId | Updates ate gift. | — |

### Endpoint details

#### `UpdateGift`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/usersession/service/UserSessionAMFService.as` (+1) |
| UI / callers | `OverviewMap.as`, `HandleFreeGiftsCommand.as`, `PostLoginSequence.as` |
| Behavior | Updates ate gift. |

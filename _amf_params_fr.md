## Référence AMF — services, endpoints & paramètres

Chaque ligne = un appel `callFunction("Méthode", [paramètres])` trouvé dans le client.
Les noms de paramètres reprennent les **variables ActionScript** (pas toujours les types serveur).
Si plusieurs variantes existent, le client appelle la même méthode avec des signatures différentes.

### Auth, session & compte

#### `WebService.AMFActorService`

Chemin AMF : `MovieStarPlanet.WebService.AMFActorService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BlockActor` | param1, param2 |  |
| `BlockActorNeb` | param1, param2 |  |
| `BulkLoadActors` | param1 |  |
| `BuyClothesNew` | param1, param2 |  |
| `CreateNewUserWithSecureSnapshotV2` | newActorCreationData, checksum, store, deviceId, snapshotSmall, snapshotBig |  |
| `GetActorIdByName` | param1 |  |
| `GetActorZooItems` | param1 |  |
| `GetClothesFromNewestClothesSection` | param1, param2, param3 |  |
| `GetPagedClothByCategoryGroups` | param1, _loc5_ |  |
| `GetPagedClothByCategoryGroups_14` | param1, _loc5_ |  |
| `GetPostLoginBundle` | param1 |  |
| `IsActorNameUsed` | param1 |  |
| `IsNameBlocked` | param1 |  |
| `LoadActorDetails` | param1, param2 |  |
| `LoadActorDetailsExtended` | param1 |  |
| `LoadActorItems` | param1 |  |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 |  |
| `LoadActorWithCurrentClothesBasicDataOnlyRevised` | param1 |  |
| `LoadActorsVipDetails` | param1 |  |
| `LoadBlockedAndBlockingActors` | param1 |  |
| `LoadBlockedAndBlockingActorsNeb` | param1 |  |
| `LoadDataForRegisterNewUser` | — |  |
| `LoadModeratorInformation` | param1 |  |
| `LoadMood` | param1 |  |
| `LoadMovieStarListRevised` | param1 |  |
| `LockOutUser` | param1, param2, param3, param4, param5 |  |
| `LoginMobile` | userId, redirectToken, version, store, deviceId |  |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `PickupGuidePresent` | actorId, type, index |  |
| `ReportActor` | param1 |  |
| `ReportTabletAndroidConversion` | param1, param2 |  |
| `ReportTabletIOSConversion` | param1, param2 |  |
| `RequestMobileStartupReward` | param1 |  |
| `SaveAlertWordsCount` | param1, param2 |  |
| `SaveBirthInfoWithTicket` | param1, param2, param3 |  |
| `SearchActorByNameNeb` | param1, param2 |  |
| `SearchActorByNameWithRequestStatus` | param1, param2 |  |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 |  |
| `SubmitMobileStartupReward` | param1, param2, param3 |  |
| `ThirdPartyLoginDesktopV2` | param1, param2, param3, param4, param5 |  |
| `ThirdPartyLoginMobileV2` | nacd, snapshotBig, snapshotSmall, username, password, version, store, deviceId |  |
| `UnblockActor` | param1, param2 |  |
| `UnblockActorNeb` | param1, param2 |  |
| `UpdateClothes` | param1, param2 |  |
| `ValidateCaptcha` | param1, param2 |  |
| `fameOverhaul` | param1 |  |
| `loginMobileV2` | userName, password, version, store, deviceId, dfp |  |

#### `WebService.AMFUserService`

Chemin AMF : `MovieStarPlanet.WebService.AMFUserService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `LogInput` | param1, param2, param3, param5, param4 |  |
| `LogInputGroupChat` | param1, param2, param3, param5, param4 |  |
| `LogInputWithConditionalModerationCall` | param1, param2, param3, param4, param5, param6 |  |

#### `WebService.ActorService.AMFActorServiceForWeb`

Chemin AMF : `MovieStarPlanet.WebService.ActorService.AMFActorServiceForWeb`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BlockActor` | param1, param2 |  |
| `BlockActorNeb` | param1, param2 |  |
| `BlockedActors` | param1 |  |
| `ClaimAllLevelUpGifts` | param1, param2 |  |
| `ClaimSingleLevelUpGift` | param1, param2, param3 |  |
| `GetActorAddress` | actorId |  |
| `GetLevelUpGiftChoices` | actorId |  |
| `GetLevelUpGiftSelects` | actorId |  |
| `GetLevelUps` | — |  |
| `GetPostLoginBundle` | param1 |  |
| `GetPostLoginBundleStandalone` | param1 |  |
| `IsActorNameUsed` | param1 |  |
| `IsNameBlocked` | param1 |  |
| `LoadActorDetails` | param1, param2 |  |
| `LoadActorDetailsExtended` | param1 |  |
| `LoadBlockedAndBlockingActors` | param1 |  |
| `LoadBlockedAndBlockingActorsNeb` | param1 |  |
| `LoadModeratorInformation` | param1 |  |
| `LoadMood` | param1 |  |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `ModerationSearchActorId` | actorId |  |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `PickupGuidePresent` | actorId, type, index |  |
| `PurchaseRecoloring` | param1, param2, param3, param4, param5 |  |
| `ReportActor` | param1 |  |
| `SaveActorAddress` | param1 |  |
| `SaveActorSoundMuted` | param1, param2 |  |
| `SaveBirthInfoWithTicket` | param1, param2, param3 |  |
| `SaveLevelUpGiftSelect` | param1, param2, param3 |  |
| `SearchActorByNameNeb` | param1, param2 |  |
| `SetColorOnActorItemNew` | param1, param2, param3, param4, param5 |  |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 |  |
| `UnblockActor` | param1, param2 |  |
| `UnblockActorNeb` | param1, param2 |  |
| `ValidateCaptcha` | param1, param2 |  |
| `fameOverhaul` | param1 |  |
| `getWallActivitiesForActor` | pagingOptions.actorId, pagingOptions.activityType, pagingOptions.pageIndex, pagingOptions.pageSize |  |

#### `WebService.AppSettings.AMFAppSettingsService`

Chemin AMF : `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetAppSetting` | param1 |  |
| `GetAppSettings` | param1 |  |

#### `WebService.AppSettings.AMFAppSettingsServiceMobile`

Chemin AMF : `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsServiceMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetAppSetting` | param1 |  |
| `GetAppSettings` | param1 |  |

#### `WebService.Nebula.AMFNebulaService`

Chemin AMF : `MovieStarPlanet.WebService.Nebula.AMFNebulaService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetProfileId` | param1 |  |
| `GetProfileIds` | missing |  |
| `GetProfiles` | param1 |  |

#### `WebService.ParentalConsent.AMFParentalConsentService`

Chemin AMF : `MovieStarPlanet.WebService.ParentalConsent.AMFParentalConsentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorParentalConsent` | param1 |  |
| `GetUserType` | param1 |  |
| `GrantParentalConsent` | param1, param2 |  |
| `HasVisibleParentalConsentCode` | param1 |  |
| `HideParentalConsentCode` | param1 |  |
| `MatchActorIdToParentalConsentConfirmCode` | param1, param2 |  |
| `ReSendParentalConsentCode` | param1 |  |
| `RememberParentalConsentCode` | param1 |  |
| `RequestParentalConsent` | param1 |  |
| `SaveParentEmailAddress` | param1, param2 |  |
| `SetActorsParentalConsent` | param1, param2 |  |

#### `WebService.Payment.AMFPaymentService`

Chemin AMF : `MovieStarPlanet.WebService.Payment.AMFPaymentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DisableAutomaticRenewal` | param1 |  |
| `GetAvailablePurchaseTypes` | actorId |  |
| `GetBokuBuyUrlNew` | param1, param2, param3, param4, param5 |  |
| `GetBokuPricePoints` | — |  |
| `GetCurrentPaymentPossibilities` | types |  |
| `GetRecurringPaymentSubscription` | param1 |  |
| `GetTimeLimitedPurchaseType` | actorId |  |
| `GetTransactionPurchaseInfo` | param1, param2 |  |
| `GetTransactionPurchaseInfoWeb` | param1, param2 |  |
| `GetTransactionPurchaseList` | param1, param2, param3 |  |
| `GetTransactionPurchaseListIncludingManual` | param1, param2, param3 |  |
| `VerifyBokuTransaction` | param1 |  |

#### `WebService.User.AMFUserServiceWeb`

Chemin AMF : `MovieStarPlanet.WebService.User.AMFUserServiceWeb`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CommentEntity` | entityComment |  |
| `CreateNewUserWithSecureSnapshotV2` | param1, param2, null, param3, param4 |  |
| `EntityCommentDelete` | param1, param2 |  |
| `GetActorPersonalInfo` | param1, "" |  |
| `GetEntityComments` | entityType, entityId, pageIndex, pageSize |  |
| `IsCommunicationAllowedWith` | communicationType, actorid |  |
| `IsCommunicationAllowedWithNeb` | communicationType, profileId |  |
| `LogInput` | locationId, actorId, roomInstanceId, message, destinationType |  |
| `LogInputGroupChat` | locationId, actorId, roomInstanceId, message, destinationType |  |
| `LogInputWithConditionalModerationCall` | locationId, actorId, roomInstanceId, message, destinationType, isUserRestricted |  |
| `Login` | userName, password, null, null, deviceId, dfp |  |
| `LoginModeratorV2` | username, password, userIps, otp, null, null |  |
| `LoginV2` | variante 1: param1, param2, null, null, null, null<br>variante 2: username, password, userIps, null, null, browserFingerprint<br>variante 3: username, password, userIps, null, null, null | 3 variantes |
| `SaveChatAllowed` | param1, param2 |  |
| `UpdateActorPersonalInfo` | param1, param2 |  |

#### `WebService.UserSession.AMFUserSessionService`

Chemin AMF : `MovieStarPlanet.WebService.UserSession.AMFUserSessionService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AwardStartupReward` | param1 |  |
| `BadWordCountAdd` | param1, param2 |  |
| `BadWordCountClear` | param1 |  |
| `ChangePasswordNew` | param1, param2, param3 |  |
| `DeleteUser` | param1, param2, param3 |  |
| `EmailChanged` | actorId, mail, username, password, emailSettings |  |
| `EmailValidated` | actorId |  |
| `EmailValidatedCancel` | param1 |  |
| `GetActorEmail` | actorId |  |
| `GetActorIdFromName` | name |  |
| `GetActorNameFromId` | actorId |  |
| `GetMarketingStepGift` | param1 |  |
| `GiveAutographAndCalculateTimestamp` | actorId, receiverId |  |
| `GiveAutographAndCalculateTimestampNeb` | actorId, receiverProfileId |  |
| `LoadActorDetails2` | actorId, updateProfileDisplayCount, callerId |  |
| `LoadActorDetailsExtended` | actorId |  |
| `LoadActorDetailsVersion` | actorId, updateProfileDisplayCount |  |
| `MassDeleteUsers` | usersIdsTobeDeleted, userName, password |  |
| `RecoverUserFromEmailHistory` | actorName, email |  |
| `RenameUser` | actorId, newActorName, moderatorName, moderatorPass |  |
| `ResyncLogin` | actorId |  |
| `SendEmailValidation` | param1, param2, param3, param4, param5 |  |
| `SendNewEmailValidation` | param1, param2, param3, param4, param5, param6 |  |
| `SendUserParentEmailValidation` | param1, param2, param3, param4, param5, param6 |  |
| `SetEmailSettings` | actorId, actorName, emailSettings |  |
| `SetFacebookId` | param1, param2 |  |
| `SetMarketingStep` | param1, param2, param3 |  |
| `UndeleteUser` | userIdTobeDeleted, userName, password |  |
| `UpdateBehaviourStatusNew` | actorId, behaviourStatus, lockedText, chatLogId, handledByActorId |  |
| `UpdateGift` | actorId |  |
| `UpdateMySchool` | actorId, passwordHash, schoolId, schoolYear |  |
| `UpdateRetention` | actorId |  |
| `deleteBioText` | actorId, moderatorName, moderatorPass |  |
| `eraseEmail` | email, moderatorName, moderatorPass |  |

#### `WebService.UserSession.AMFUserSessionServiceForMobile`

Chemin AMF : `MovieStarPlanet.WebService.UserSession.AMFUserSessionServiceForMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `UpdateGift` | actorId |  |

### Avatar & vêtements (MovieStar)

#### `WebService.BeautyClinic.AMFBeautyClinicService`

Chemin AMF : `MovieStarPlanet.WebService.BeautyClinic.AMFBeautyClinicService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyBeautyClinicItems` | actorId, eyeId, eyeShadowId, noseId, mouthId, eyeColors, eyeShadowColors, mouthColors, skinColor, removeEyeShadow |  |
| `BuyManyBeautyClinicItems` | actorId, itemsArray |  |
| `GetMyBeautyClinicItems` | actorId |  |
| `GetMyBeautyClinicItemsWithHiddenOption` | actorId, includeHidden |  |
| `LoadDataForBeautyClinic` | — |  |
| `LoadModeratorDataForBeautyClinic` | — |  |
| `WearItems` | actorId, inventoryIdArray |  |

#### `WebService.MovieStar.AMFMovieStarService`

Chemin AMF : `MovieStarPlanet.WebService.MovieStar.AMFMovieStarService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorClothesRel` | relId |  |
| `GetActorClothesRelList` | rels |  |
| `GetContextClothes` | actorId, contextId |  |
| `LoadActorBonstersPaged` | actorId, pageIndex, pageSize |  |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 |  |
| `LoadClothes` | skinId, shopId |  |
| `LoadClothesByIds` | clothesIds |  |
| `LoadClothesFromThemeId` | themeId |  |
| `LoadClothesWithThemeByIds` | clothesIds |  |
| `LoadDataForRegisterNewUser` | — |  |
| `LoadFaceParts` | — |  |
| `LoadMovieStarFlatMinimum` | actorId |  |
| `LoadMovieStarFlatRevised` | actorId |  |
| `LoadMovieStarListRevised` | actorIds |  |
| `LoadMovieStarRevised` | actorId |  |
| `LoadPagedActorClothes` | param1, param2, param3 |  |
| `LoadPagedActorGiftableClothes` | param1, param2, param3 |  |
| `LoadPagedActorGiftableItems` | param1, param2, param3 |  |
| `LoadPagedActorItems` | actorId, pageIndex, pageSize |  |
| `LoadRoomItems` | actorId |  |
| `UpdateClothes` | actorId, actorClothesRelIds |  |
| `getRandomClothesByType` | slotType, isFemale, amount |  |

### Looks (tenues)

#### `WebService.Looks.AMFLookService`

Chemin AMF : `MovieStarPlanet.WebService.Looks.AMFLookService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CanWearOwnLook` | param1, param2 |  |
| `GetLookById` | variante 1: lookId<br>variante 2: lookId, this.actorModel.actorId | 2 variantes |
| `GetLooksByOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksCreatedBy` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksForActor` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksForOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksLatest` | pageIndex, pageSize |  |
| `GetLooksLatestByFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksLatestByMeAndFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksLikedByMe` | actorId, pageIndex, pageSize |  |
| `GetLooksTopAll` | pageIndex, pageSize |  |
| `GetLooksTopByFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksTopByMeAndFriends` | actorId, pageIndex, pageSize |  |
| `GetRandomLookByLikes` | poolSize |  |
| `LookDelete` | lookId, this.actorModel.actorId |  |
| `SaveLookAndData` | look, clotheIds, lookSnapshot, fullSizeSnapshot |  |
| `SaveSmallLookSnapshot` | look, lookSnapshot |  |

### Boutique & dépenses

#### `WebService.Shopping.AMFShopContentService`

Chemin AMF : `MovieStarPlanet.WebService.Shopping.AMFShopContentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddTag` | param1, param2 |  |
| `AddTheme` | param1, param2 |  |
| `BuyItems` | param1, ActorSession.loggedInActor.actorId |  |
| `GetPage` | pageIndex, pageSize, params.shopId, params.genderId, params.themeId, params.categoryId, params.tagToUse, params.vipToUse, params.currencyToUse, params.search |  |
| `RemoveTag` | param1, param2 |  |
| `RemoveTheme` | param1, param2 |  |
| `SetShopIds` | param1, param2 |  |

#### `WebService.Spending.AMFSpendingService`

Chemin AMF : `MovieStarPlanet.WebService.Spending.AMFSpendingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyAnimation` | param1, param2 |  |
| `BuyBackground` | param1, param2 |  |
| `BuyChangePet` | param1, param2, param3, param4 |  |
| `BuyCharacterPopUp` | param1 |  |
| `BuyClothes` | param1, param2, param3 |  |
| `BuyDiamondCharacterEffect` | param1 |  |
| `BuyDiamondTwit` | param1 |  |
| `BuyEmoticonPackage` | param1, param2 |  |
| `BuyFameBooster` | param1 |  |
| `BuyFameWheelSpin` | param1 |  |
| `BuyInstantPetGrow` | param1, param2 |  |
| `BuyMusic` | param1, param2 |  |
| `BuyShoppingSpree` | param1 |  |
| `BuySpecialGreeting` | actorId, friendId, greetingTypeId |  |
| `BuyStarcoinShooter` | param1 |  |
| `BuyStarcoinsWheelSpin` | param1 |  |
| `ClaimFreeDownloadableFameWheelSpin` | param1 |  |
| `GetActiveSpecialsItems` | param1 |  |
| `GetEmoticonPackages` | param1 |  |
| `GetGreetingIndices` | param1 |  |
| `GetPagedShopSpecials` | param1, param2, param3 |  |
| `GetSpecialsGreetingItem` | param1, param2 |  |
| `GetSpecialsItemPrice` | param1, param2 |  |
| `IsValidSpecialGreeting` | param1, param2 |  |

### Salles & chambres

#### `WebService.AMFRoomServiceForMobile`

Chemin AMF : `MovieStarPlanet.WebService.AMFRoomServiceForMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorBonsterList` | param1, param2 |  |
| `GetActorClickItemList` | param1, param2 |  |
| `GetActorClothesByShopId` | param1, param2, param3 |  |
| `GetWallpapers` | param1, param2 |  |
| `LoadHouse` | houseId, callingActorId |  |
| `LoadHouseAndSpecificRoom` | callingActorId, houseId, roomId |  |
| `LoveRoom` | param1, param2 |  |
| `SaveRoomWithSnapshot` | data, roomSnapshotProfile, roomSnapshotMedium, roomSnapshotSmall |  |

#### `WebService.Room.AMFRoomService`

Chemin AMF : `MovieStarPlanet.WebService.Room.AMFRoomService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorBonsterList` | param1, param2 |  |
| `GetActorClickItemList` | param1, param2 |  |
| `GetActorClothesByShopId` | param1, param2, param3 |  |
| `GetWallpapers` | param1, param2 |  |

### Pets & Bonsters

#### `WebService.AMFMobilePetService`

Chemin AMF : `MovieStarPlanet.WebService.AMFMobilePetService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CurePet` | param1 |  |
| `FeedPet` | param1, param2 |  |
| `GetActorClickItem` | param1 |  |
| `GetClickItems` | — |  |
| `GetClickItemsForActor` | param1 |  |
| `HatchPet` | param1, param2 |  |
| `PetFriendPet` | param1, param2 |  |
| `PurchaseClickItem` | param1, param2 |  |
| `SavePetName` | param1, param2 |  |
| `WashPet` | param1, param2 |  |

#### `WebService.Bonster.AMFBonsterService`

Chemin AMF : `MovieStarPlanet.WebService.Bonster.AMFBonsterService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AnimationUsed` | actorBonsterRelId, animationId, actorId |  |
| `CheckInBonsterAtPetHotel` | actorBonsterRelId, bookTimeAmount, actorId |  |
| `CheckOutBonsterFromPetHotel` | actorBonsterRelId, actorId |  |
| `DeleteBonsterName` | actorBonsterRelId |  |
| `FeedBonster` | actorBonsterRelId, foodId, actorId |  |
| `GetBonsterAnimations` | param1, param2 |  |
| `GetBonsterById` | actorBonsterRelId |  |
| `GetBonsterCandyPrices` | — |  |
| `GetBonsterListByActor` | actorId, loadAnimations, excludeHotel |  |
| `GetBonsterTemplateList` | — |  |
| `HatchBonster` | actorBonsterRelId, actorId |  |
| `InstantEvolveBonster` | actorId, actorBonsterRelId |  |
| `PetFriendBonster` | actorId, actorBonsterRelId |  |
| `PlayWithBonster` | actorBonsterRelId, playPoints, actorId |  |
| `RenameBonster` | actorBonsterRelId, name, actorId |  |
| `SaveNewAndOldPetsPositionsInMyRoom` | actorId, bonsterPositionsList, clickItemsList |  |
| `WashBonster` | actorBonsterRelId, washPoints, actorId |  |

#### `WebService.Bonster.AMFBonsterShopService`

Chemin AMF : `MovieStarPlanet.WebService.Bonster.AMFBonsterShopService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyBonster` | actorId, bonsterId |  |
| `GetCampaignBonster` | — |  |
| `GetListOfAllBonstersAndBoonies` | — |  |
| `GetListOfBonsters` | — |  |
| `GetListOfBoonies` | — |  |
| `GetPagedListOfBonsters` | pageId, pageSize |  |
| `GetPagedListOfBoonies` | pageId, pageSize |  |
| `GetPagedListOfFriendsPets` | pageId, pageSize |  |
| `GetPagedListOfNewPets` | pageId, pageSize |  |
| `GetPagedListOfTopPets` | pageId, pageSize |  |

#### `WebService.Pets.AMFPetService`

Chemin AMF : `MovieStarPlanet.WebService.Pets.AMFPetService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyClickItem` | actorId, clickItemId |  |
| `CheckInPetHotel` | actorId, clickItemRelId, stayPeriod |  |
| `CheckOutPetHotel` | actorId, clickItemRelId |  |
| `CurePet` | actorClickItemRelId |  |
| `DeletePetName` | clickItemId, moderatorName, moderatorPass |  |
| `FeedPet` | actorClickItemRelId, foodPoints |  |
| `GetActorClickItem` | actorClickItemRelId |  |
| `GetClickItems` | — |  |
| `GetClickItemsForActor` | variante 1: actorid<br>variante 2: param1 | 2 variantes |
| `GetClickItemsForActorThatCanStillGrow` | actorid |  |
| `GetClickItemsForActorWithPrice` | actorid |  |
| `GetClickItemsForPetHotel` | actorId |  |
| `HarvestPlant` | actorId, actorClickItemRelId |  |
| `HatchPet` | actorClickItemRelId, configuration |  |
| `PetFriendPet` | actorId, actorClickItemRelId |  |
| `PlayedPetGame` | actorClickItemRelId, playPoints |  |
| `SaveClickItemLocations` | locations |  |
| `SavePetName` | actorClickItemRelId, name |  |
| `WashPet` | actorId, actorClickItemRelId |  |

### Films & favoris mobile

#### `MobileServices.AMFFavs`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFFavs`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddActorFav` | param1, param2 |  |
| `GetActorMovieFavs` | param1, param2 |  |
| `RemoveActorFav` | param1, param2 |  |

#### `MobileServices.AMFMovieService`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFMovieService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `DeleteMovie` | param1, param2 |  |
| `GetMovie` | movieId |  |
| `GetUnifiedMoviesByFriendsStarringMe` | param1, param2 |  |
| `GetUnifiedMoviesByMePrivate` | param1, param2 |  |
| `GetUnifiedMoviesLatestByAll` | param1, param2 |  |
| `GetUnifiedMoviesLatestByFriends` | param1, param2 |  |
| `GetUnifiedMoviesMinePublic` | param1, param2 |  |
| `GetUnifiedMoviesTopAll` | param1, param2 |  |
| `GetUnifiedMoviesTopByMeAndFriends` | param1, param2 |  |
| `MovieWatched` | movieId |  |
| `RateMovie` | param1, param2 |  |
| `UpdateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8, param9 |  |

#### `WebService.Favourites.AMFFavs`

Chemin AMF : `MovieStarPlanet.WebService.Favourites.AMFFavs`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddActorFav` | actorId, entityType, entityId |  |
| `GetActorMovieFavs` | actorId, byRating, pageIndex, pageSize |  |
| `RemoveActorFav` | actorId, entityType, entityId |  |

#### `WebService.MovieService.AMFMovieService`

Chemin AMF : `MovieStarPlanet.WebService.MovieService.AMFMovieService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CommentMovie` | rateMovie |  |
| `DeleteMovie` | movieId, actorId |  |
| `DeleteMovieComment` | movieId, commentId |  |
| `GetActorMovieCount` | actorId |  |
| `GetAutoSavedMovieId` | actorId |  |
| `GetMovieByGuid` | movieGuid |  |
| `GetMovieById` | movieId |  |
| `GetMovieListForActor` | pagingOptions.params.actorId, pagingOptions.params.type, pagingOptions.pageIndex, pagingOptions.pageSize |  |
| `GetMovieRatings` | movie.MovieId, pageIndex, pageSize |  |
| `MovieWatched` | movieId, actorId |  |
| `PublishMovie` | movieId |  |
| `RateMovie` | rateMovie |  |
| `SaveMovieWithSnapshot` | movie, snapshotSmall, snapshotBig |  |
| `SearchMovie` | searchString, pageIndex, pageSize |  |
| `SendMovieAsMail` | movieId, toAddress |  |

### Vidéo / YouTube

#### `WebService.Video.AMFVideoService`

Chemin AMF : `MovieStarPlanet.WebService.Video.AMFVideoService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddVideoToMspTv` | param1, param2, param3, param4, param5 |  |
| `AutoSaveVideoFromFeed` | param1, param2, param3, param4, param5, _loc9_ |  |
| `CreateBlankPlaylist` | param1, param2 |  |
| `DeleteExternalVideoPlaylistRel` | param1, param2, param3 |  |
| `DeletePlaylist` | param1, param2, param3 |  |
| `GetCategoryExternalVideosForPlayback` | param1, param2 |  |
| `GetExternalVideoForChatRoom` | param1 |  |
| `GetMspTvExternalVideosForPlayback` | param1 |  |
| `GetMyPlaylistsForVideo` | param1 |  |
| `GetPagedBlockedExternalVideos` | param1, param2, param3, param4 |  |
| `GetPagedCategoryExternalVideos` | param1, param2, param3 |  |
| `GetPagedExternalVideos` | param1, param2, param3 |  |
| `GetPagedMspTvExternalVideos` | param1, param2 |  |
| `GetPagedNewestExternalVideos` | param1, param2 |  |
| `GetPagedPlaylists` | param1, param2, param3, param4 |  |
| `GetPagedPlaylistsBySearch` | param1, param2, param3, param4 |  |
| `GetPagedVideoListObjects` | param1, param2, param3 |  |
| `GetPagedVideoListObjectsByAddTime` | variante 1: actorId, 0, 50<br>variante 2: param1, param2, param3 | 2 variantes |
| `GetPlaylist` | param1, param2 |  |
| `GetPlaylistForPlayback` | param1, param2, param3 |  |
| `GetPlaylistsForDropdown` | param1 |  |
| `GetTopExternalVideosForPlayback` | param1 |  |
| `GetYouTubeVideo` | param1, param2 |  |
| `GetYouTubeVideoInfo` | param1 |  |
| `IncrementReportCount` | param1 |  |
| `IncrementViewsExternalVideo` | param1 |  |
| `LikePlaylist` | param1, param2, param3 |  |
| `LikeYouTube` | param1, param2 |  |
| `MoveVideoInPlaylist` | param1, param2, param3, param4, param5 |  |
| `RenamePlaylist` | param1, param2, param3 |  |
| `ReportErrorOnVideo` | param1 |  |
| `SaveToNewPlaylist` | param1, param2, param3, param4, param5 |  |
| `SaveToPlaylist` | param1, param2, param3, param4 |  |
| `YouTubeBlock` | param1, param2, param3, param4 |  |
| `YouTubePopulateViewsAndLikes` | param1, param2 |  |

### Social (amis, profil, messagerie)

#### `WebService.AMFMessageService`

Chemin AMF : `MovieStarPlanet.WebService.AMFMessageService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetMessagingActors` | variante 1: [id<br>variante 2: param1 | 2 variantes |
| `IsCommunicationAllowedWith` | param1, param2 |  |
| `SendChatMessageWithModerationCall` | param1, param2, param3, param4, param5, param6 |  |
| `SendOneToOneOrGroupChatMessage` | Number(param2), param8, param3, param6, _loc13_, param4 |  |
| `SetMessengerSession` | param1 |  |

#### `WebService.AMFMobileFriendshipService`

Chemin AMF : `MovieStarPlanet.WebService.AMFMobileFriendshipService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AcceptBoyfriend` | param1, param2, param3 |  |
| `AcceptMySpecialFriend` | param1 |  |
| `ApproveDefaultAnchorFriendship` | param1 |  |
| `ApproveFriendship` | param1, param2 |  |
| `ApproveFriendshipNeb` | param1, param2 |  |
| `AskToBeBoyFriend` | param1, param2, param3 |  |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 |  |
| `AskToBeMySpecialFriend` | param1 |  |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 |  |
| `BreakUp` | param1, param2, param3 |  |
| `DeleteFriendship` | param1, param2 |  |
| `DeleteFriendshipNeb` | param1, param2 |  |
| `GetActorSpecialSummary` | param1, param2 |  |
| `GetFriendListWithNameAndScore` | param1 |  |
| `GetMspRelationshipStatus` | param3, param1, param4 |  |
| `GetPagedFriendRequests` | actorId, pageIndex, pageSize |  |
| `GetRelationshipStatusNeb` | param2, param3, param4 |  |
| `RejectBoyfriend` | param1, param2, param3 |  |
| `RejectFriendShip` | param1, param2 |  |
| `RejectFriendShipNeb` | param1, param2 |  |
| `RejectMySpecialFriend` | param1 |  |
| `RequestFriendship` | param1, param2 |  |
| `RequestFriendshipFromSchoolmate` | param1, param2 |  |
| `RequestFriendshipNeb` | param1, param2 |  |

#### `WebService.AnchorCharacter.AMFAnchorCharacterService`

Chemin AMF : `MovieStarPlanet.WebService.AnchorCharacter.AMFAnchorCharacterService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AcceptFriendship` | anchorCharacterId |  |
| `AcceptGifts` | anchorCharacterId |  |
| `CancelFriendship` | anchorCharacterId |  |
| `GetAnchorCharacterList` | — |  |
| `RequestFriendship` | anchorCharacterId |  |
| `UpdateLastInviteSent` | param1, param2 |  |
| `UpdateLastStatusSeen` | param1 |  |

#### `WebService.Friendships.AMFFriendshipService`

Chemin AMF : `MovieStarPlanet.WebService.Friendships.AMFFriendshipService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AcceptBoyfriend` | param1, param2, param3 |  |
| `AcceptMySpecialFriend` | param1 |  |
| `ApproveDefaultAnchorFriendship` | param1 |  |
| `ApproveFriendship` | param1, param2 |  |
| `ApproveFriendshipNeb` | param1, param2 |  |
| `AskToBeBoyFriend` | param1, param2, param3 |  |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 |  |
| `AskToBeMySpecialFriend` | param1 |  |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 |  |
| `BreakUp` | userId, friendId, friendType |  |
| `DeleteFriendship` | param1, param2 |  |
| `DeleteFriendshipNeb` | param1, param2 |  |
| `FindUserForFriendBrowser` | params.actorId, params.includeDeleted, params.searchString, pageIndex, pageSize |  |
| `GetFriendList` | param1 |  |
| `GetFriendListWithNameAndScore` | actor.actorId, false |  |
| `GetFriendListWithNameAndScoreV2` | userId, isLoadingTopFriendsOnly |  |
| `GetFriendShipStatus` | param1, param2 |  |
| `GetMspActorSpecialSummary` | param1, param4, param3 |  |
| `GetNebNonFriendStatus` | param2, param4 |  |
| `GetPagedProfileTodos` | actorId, pageId, pageSize |  |
| `GetProfileTodos` | param1 |  |
| `GetProfileTodosCount` | param1 |  |
| `GetSpecialRelationship` | param1 |  |
| `RejectBoyfriend` | param1, param2, param3 |  |
| `RejectFriendShip` | param1, param2 |  |
| `RejectFriendShipNeb` | param1, param2 |  |
| `RejectMySpecialFriend` | param1 |  |
| `RequestFriendship` | param1, param2, param3 |  |
| `RequestFriendshipFromSchoolmate` | param1, param2, param3 |  |
| `RequestFriendshipNeb` | param1, param2 |  |
| `SendInvitation` | param1, param2, param3 |  |

#### `WebService.Messaging.AMFMessagingService`

Chemin AMF : `MovieStarPlanet.WebService.Messaging.AMFMessagingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `SetMessengerSession` | param1 |  |

#### `WebService.Profile.AMFProfileService`

Chemin AMF : `MovieStarPlanet.WebService.Profile.AMFProfileService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CollectRecycleGift` | param1 |  |
| `DeleteWallPost` | param1, param2, param3 |  |
| `GetWallPost` | param1 |  |
| `GetWallPosts` | param1, param2, param3 |  |
| `LoadProfileSummary` | param1, ActorSession.getActorId() |  |
| `LoadProfileSummaryNeb` | param2, ActorSession.getActorId() |  |
| `PostToWallWithModerationCall` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `RecycleItem` | param1, param2, param3 |  |
| `SetFavorite` | param1, param2, param3 |  |
| `loadActorRoom` | param1, param2 |  |

#### `WebService.School.AMFSchoolService`

Chemin AMF : `MovieStarPlanet.WebService.School.AMFSchoolService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DeleteSchool` | actorId |  |
| `FindFriendsOnSameSchool` | params.actorId, pageIndex, pageSize, params.includeNames |  |
| `RetrieveMySchoolInformation` | actorId |  |
| `UpdateMySchool` | actorId, schoolId, schoolYear, schoolClass, firstName |  |

### Cadeaux & wishlist

#### `MobileServices.AMFGiftsService+Version2`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFGiftsService+Version2`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyGift` | senderId, receiverId, giftId, SWF |  |
| `GetUnifiedActorClothItems` | param1, param2, param3 |  |
| `GetUnifiedActorClothesByType` | param1, param2, param3 |  |
| `GetUnifiedGiftsGiven` | param1, param2 |  |
| `GetUnifiedGiftsNew` | param1, param2 |  |
| `GetUnifiedGiftsReceived` | param1, param2 |  |
| `GetWishListPaged` | actorId, pageIndex, pageSize |  |
| `GiveGiftOfCategory` | senderActorId, receiverActorId, relId, giftId, giftCategory, swf, wrappingColor, msg |  |
| `OpenGift` | actorId, giftId |  |
| `removeFromWishlist` | actorId, giftId |  |

#### `WebService.Gifts.AMFGiftableMembershipService`

Chemin AMF : `MovieStarPlanet.WebService.Gifts.AMFGiftableMembershipService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetGiftableMemberships` | variante 1: VipCertificateStatus.GIVABLE<br>variante 2: VipCertificateStatus.OFFERED<br>variante 3: VipCertificateStatus.REDEEMED | 3 variantes |
| `GetMembershipsForUser` | variante 1: param1, -1, param2, param3<br>variante 2: param1, 1, param2, param3 | 2 variantes |
| `GetNumberOfUnredeemedMemberships` | — |  |
| `GetReceivedGiftableMemberships` | variante 1: VipCertificateStatus.OFFERED<br>variante 2: VipCertificateStatus.REDEEMED | 2 variantes |
| `GiveGiftableMembership` | param1, param2, "", "" |  |
| `HasMembershipActivity` | — |  |
| `RedeemGiftableMembership` | param1 |  |
| `RejectGiftedMembership` | param1 |  |

#### `WebService.Gifts.AMFGiftsService+Version2`

Chemin AMF : `MovieStarPlanet.WebService.Gifts.AMFGiftsService+Version2`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddItemToWishlist` | clothIds, clothColors |  |
| `AwardStartupReward` | actorId |  |
| `BuyGift` | senderId, receiverId, giftId, SWF |  |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize |  |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize |  |
| `GetGift` | giftId |  |
| `GetGiftLog` | variante 1: giftLogId<br>variante 2: param1 | 2 variantes |
| `GetMarketingStepGift` | actorId |  |
| `GiveGiftOfCategory` | senderActorId, receiverActorId, relId, giftId, contentCategory, swf |  |
| `HandleGift` | — |  |
| `IsInUseInRooms` | actorClothesRelId |  |
| `OpenGift` | receiverId, giftId |  |
| `ReturnMassGifts` | singleActorId, multipleActorIds, received |  |
| `RevertTrade` | giftLogId |  |
| `SetMarketingStep` | param1, param2, param3 |  |
| `UpdateGift` | actorId |  |
| `UpdateRetention` | actorId |  |
| `refundGift` | giftLogId, giftId |  |
| `removeFromWishlist` | actorId, giftId |  |
| `returnGift` | giftLogId, giftId |  |

### Scrapblog, photos, design

#### `MobileServices.AMFDesignService`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFDesignService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AutoRenameDesign` | param1 |  |
| `BuyDesignCopy` | actorId, designId |  |
| `CancelDesignSale` | actorId, desginId |  |
| `DeleteDesign` | actorId, designId |  |
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds |  |
| `GetDesignTemplatesPage` | skindId, categories, pageIndex, pageSize |  |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageid, pagesize |  |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageid, pagesize |  |
| `GetPagedListOfMyDesigns` | actorId, pageid, pagesize |  |
| `GetPagedListOfNewestDesigns` | skinId, pageid, pagesize |  |
| `GetPagedListOfTopDesigns` | skinId, pageIndex, pageSize |  |
| `ModeratorDeleteDesigns` | actorId, designId |  |
| `NumberOfDesignsForSale` | actorId |  |
| `ProduceDesign` | actorId, designId |  |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `SearchDesign` | searchString, pageid, pagesize |  |
| `SearchDesigner` | searchString, pageid, pagesize |  |
| `SellDesign` | actorId, designId, amount |  |

#### `WebService.DesignStudio.AMFDesignShopWebService`

Chemin AMF : `MovieStarPlanet.WebService.DesignStudio.AMFDesignShopWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyDesignCopy` | actorId, designId |  |
| `CancelDesignSale` | param1, param2 |  |
| `GetDesignsForSale` | param1, param2, param3 |  |
| `NumberOfDesignsForSale` | param1 |  |
| `SellDesign` | param1, param2, param3 |  |

#### `WebService.DesignStudio.AMFDesignStudioWebService`

Chemin AMF : `MovieStarPlanet.WebService.DesignStudio.AMFDesignStudioWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AutoRenameDesign` | param1 |  |
| `DeleteDesign` | actorId, designId |  |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageID, pageSize |  |
| `GetPagedListOfDesignsFromUser` | actorId, pageId, pageSize |  |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageID, pageSize |  |
| `GetPagedListOfMyDesigns` | actorId, pageID, pageSize |  |
| `GetPagedListOfNewestDesigns` | skinId, pageID, pageSize |  |
| `GetPagedListOfTopDesigns` | skinId, pageID, pageSize |  |
| `ModeratorDeleteDesigns` | actorId, designId |  |
| `ProduceDesign` | actorId, designId |  |
| `RenameDesign` | param1, param2, param3 |  |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `SearchDesign` | searchString, pageID, pageSize |  |
| `SearchDesigner` | searchString, pageID, pageSize |  |

#### `WebService.ImageUpload.AMFImageUpload`

Chemin AMF : `MovieStarPlanet.WebService.ImageUpload.AMFImageUpload`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddView` | param1, param2 |  |
| `DeleteImage` | param1, param2 |  |
| `EditHeadline` | param1, param2, param3, param4 |  |
| `EditHeadlineMod` | param1, param2 |  |
| `EditStatusMod` | variante 1: id, -2<br>variante 2: param1, param2 | 2 variantes |
| `GetFriendsUploads` | param1, param2, param3 |  |
| `GetModSearch` | param1, param2, param3 |  |
| `GetMyUploads` | param1, param2, param3 |  |
| `GetMyUploadsForArtbook` | param1 |  |
| `GetNewUploads` | param1, param2, param3 |  |
| `GetRemainingUploadCount` | param1, param2 |  |
| `GetSingleImage` | param1, param2 |  |
| `GetSingleImageModerator` | param1 |  |
| `GetSingleImageWithGuid` | param1, param2 |  |
| `GetSingleImageWithGuidModerator` | param1 |  |
| `GetTopUploads` | param1, param2, param3 |  |
| `GetUploadsFromUser` | param1, param2, param3 |  |
| `GetUserUploads` | param1, param2, param3 |  |
| `LikeImage` | actorId, imageUploadId |  |
| `PollImages` | param1 |  |
| `PurchaseUpload` | param1 |  |
| `SearchFriendsUploads` | param1, param2, param3, param4 |  |
| `SetPhotoUploadRulesAccepted` | param1 |  |
| `UploadImageWithSnapshot` | param1, param2, _loc5_, param3 |  |

#### `WebService.ScrapBlog.AMFClipArtService`

Chemin AMF : `MovieStarPlanet.WebService.ScrapBlog.AMFClipArtService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds |  |

#### `WebService.ScrapBlog.AMFScrapBlogService`

Chemin AMF : `MovieStarPlanet.WebService.ScrapBlog.AMFScrapBlogService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AdminDeleteScrapBlog` | param1, param2, param3 |  |
| `DeleteScrapBlog` | param1, param2 |  |
| `GetClipArtCategories` | — |  |
| `GetClipArtNew` | param1, param2 |  |
| `GetFriendsScrapBlogs` | param1, param2, param3 |  |
| `GetFriendsScrapBlogsBatched` | param1, param2 |  |
| `GetHighscoreScrapBlogs` | param1, param2, param3, param4, param5, param6 |  |
| `GetNewestScrapBlogs` | param1, param2 |  |
| `GetPrivateScrapBlogs` | param1, param2, param3 |  |
| `GetScrapBlogsBySearch` | _loc3_, _loc5_, _loc6_, _loc4_ |  |
| `GetScrapBlogsByType` | param1, param2, param3 |  |
| `GetScrapBlogsByUser` | param1, param2, param3 |  |
| `GetScrapBlogsFriendsLiked` | param1, param2, param3 |  |
| `GetSubmissibleScrapBlogs` | param1, param2, param3 |  |
| `LikeScrapBlog` | actorId, scrapBlogId, ownerId |  |
| `LoadScrapBlog` | param1, param2 |  |
| `LoadTemplateByType` | param1 |  |
| `ReplicateScrapblog` | param1, param2 |  |
| `SaveScrapBlogWithSnapshot` | actorId, scrapBlog, snapshotSmall, snapshotBig |  |
| `SetArtbookRulesAccepted` | param1 |  |

### Média (animations, fonds, musique)

#### `MobileServices.AMFAnimationsServiceForMobile`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFAnimationsServiceForMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorAnimationsByCategory` | param1 |  |
| `GetAnimationsByFrameLabels` | param1 |  |

#### `WebService.Media.AMFMediaService`

Chemin AMF : `MovieStarPlanet.WebService.Media.AMFMediaService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetAnimations` | — |  |
| `GetBackgrounds` | false |  |
| `GetBackgroundsPaged` | false, pageIndex, pageSize |  |
| `GetMusic` | false |  |
| `GetMyAnimations` | param1 |  |
| `GetMyBackgrounds` | param1 |  |
| `GetMyMusic` | param1 |  |
| `getAnimationCount` | param1 |  |
| `getClothesCount` | param1 |  |
| `getPropsCount` | param1 |  |

### Quêtes, succès, récompenses

#### `WebService.AMFAwardService`

Chemin AMF : `MovieStarPlanet.WebService.AMFAwardService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `RequestAnchorCharacterIntroductionAward` | actorId |  |

#### `WebService.Achievement.AMFAchievementWebService`

Chemin AMF : `MovieStarPlanet.WebService.Achievement.AMFAchievementWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CheckLoginAchievements` | param1 |  |
| `ClaimReward` | param1, param2 |  |
| `GetAchievementData` | — |  |
| `GetActorAchievementProgressAll` | actorId |  |
| `GetArtbookStickers` | param1 |  |
| `GetClaimableCategories` | param1 |  |
| `GetPagedAchievements` | actorId, category, pageIndex, pageSize |  |
| `GetTotalProgress` | actorId, category |  |

#### `WebService.Awarding.AMFAwardingService`

Chemin AMF : `MovieStarPlanet.WebService.Awarding.AMFAwardingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyDiamondRespin` | — |  |
| `GetWheelData` | — |  |
| `RequestIntroductionAward` | actorId |  |
| `SpinWheel` | wheelId |  |
| `awardActor` | actorId, amount, type, winSpendType |  |
| `claimAdvertAwardByCampaign` | campaignId |  |
| `claimAdvertViewAward` | type, amount, actorId |  |
| `claimDailyAward` | awardStr, amnt, loggedInActorId |  |
| `countAwardsLeft` | awardStr, actorId |  |
| `hasAllDailyAwardLeft` | awardStr, actorId |  |
| `hasAnyDailyAwardLeft` | awardStr, actorId |  |
| `hasSomeDailyAwardLeft` | awardStr, actorId |  |

#### `WebService.Holiday.AMFHolidayService`

Chemin AMF : `MovieStarPlanet.WebService.Holiday.AMFHolidayService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetReceivedChristmasPresents` | param1, param2 |  |
| `RequestChristmasPresent` | param1, param2, param3 |  |

#### `WebService.PiggyBank.AMFPiggyBankService`

Chemin AMF : `MovieStarPlanet.WebService.PiggyBank.AMFPiggyBankService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CanDestroyPiggyBank` | — |  |
| `DestroyPiggyBank` | — |  |
| `GetPiggyBank` | — |  |

#### `WebService.Quest.AMFQuestService`

Chemin AMF : `MovieStarPlanet.WebService.Quest.AMFQuestService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BeginQuest` | param1, param2 |  |
| `BeginSpecialQuest` | param1, param2 |  |
| `ClaimReward` | param1, param2, param3 |  |
| `ClaimRewardForDownloadableClient` | param1, param2, param3 |  |
| `ClaimSpecialQuestBaseReward` | param1, param2 |  |
| `ClaimSpecialQuestSubOrFinalReward` | param1, param2 |  |
| `DiamondSkip` | param1, param2 |  |
| `ForceCompleteCurrentQuest` | param1, param2 |  |
| `ForceCompleteCurrentQuestForDownloadableClient` | param1, param2 |  |
| `GetAllQuestStatus` | param1 |  |
| `GetAllQuestStatusForDownloadableClient` | param1 |  |
| `GetGiftHuntQuestData` | param1, param2 |  |
| `ResetNotifications` | param1, param2 |  |
| `UpdateDoTaskObjectiveAndGetStatus` | param1, param2, param3, param4 |  |
| `UpdateGotoObjectiveAndGetStatus` | param1, param2, param3 |  |
| `UpdateSpecialQuestObjectiveOld` | param1, param2, param3 |  |
| `UpdateSpecialQuestObjectives` | param1, param2, param3 |  |

### Compétitions

#### `WebService.Competition.AMFCompetitionService`

Chemin AMF : `MovieStarPlanet.WebService.Competition.AMFCompetitionService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetMovieCompetition` | id |  |
| `GetMovieCompetitionList` | params[0 |  |
| `GetMovieCompetitionListById` | params[0 |  |
| `GetMovieCompetitionListByNewsId` | newsId |  |
| `GetNewsById` | param1, param2, param3 |  |
| `GetParticipatingLooks` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingMovies` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingRooms` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingScrapBlogs` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetSubmittedMovieCompetitionLook` | movieCompetitionId, actorId |  |
| `GetSubmittedMovieCompetitionMovie` | movieCompetitionId, actorId |  |
| `GetSubmittedMovieCompetitionRoom` | movieCompetitionId, actorId |  |
| `GetSubmittedScrapBlog` | competitionId, actorId |  |
| `HasActorVotedInCompetition` | movieCompetitionId, actorId |  |
| `LinkCompetitionToTheme` | newsId, themeId |  |
| `MovieCompetitionPublish` | param1, param2, param3 |  |
| `SaveMovieCompetition` | competition, awardPrizes |  |
| `SubmitEntityToCompetition` | movieCompetitionId, entityId, actorId |  |
| `VoteInMovieCompetition` | movieCompetitionId, movieId, actorId |  |

#### `WebService.DailyCompetition.AMFDailyCompetitionService`

Chemin AMF : `MovieStarPlanet.WebService.DailyCompetition.AMFDailyCompetitionService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `IncrementSubmissionResets` | — |  |
| `addToComp` | param2, param3, param4 |  |
| `canSubmit` | param2, param3 |  |
| `getRandomItem` | param2 |  |
| `getTodaysTheme` | — |  |
| `getVoteScore` | param2 |  |
| `voteFor` | param2, param3, param4, param5, param6 |  |

### Forum, sondages, news, activités

#### `Polls.AMFPollService`

Chemin AMF : `MovieStarPlanet.Polls.AMFPollService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetPoll` | pollId, actorId |  |
| `GetPollLatest` | actorId |  |
| `GetPolls` | pageindex, pagesize |  |
| `GetPollsUnused` | — |  |
| `LinkPolls` | pollId, nextPollId |  |
| `NewPoll` | question, answer1, answer2, answer3, answer4 |  |
| `NewPollPublish` | pollId, locale, siteDomain |  |
| `VotePoll` | pollId, actorId, answer |  |

#### `WebService.Campaign.AMFCampaignService`

Chemin AMF : `MovieStarPlanet.WebService.Campaign.AMFCampaignService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `UseCampaign` | param1, param2 |  |

#### `WebService.Forums.AMFForumService`

Chemin AMF : `MovieStarPlanet.WebService.Forums.AMFForumService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AdminCreateTopic` | actorName, actorPassword, forumId, subject, type, message, colorCode, subjectChatLogId, messageChatLogId |  |
| `AdminCreateTopicPoll` | actorId, forumId, filteredQuestion, filteredAnsers, topicType, adminUserName, adminPassword, -1 |  |
| `CheckAllowedCreateTopic` | actorId |  |
| `CreatePostWithModerationCall` | actorId, actorName, topicId, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `CreateTopicPollWithModerationCall` | actorId, actorName, forumId, pollQuestion, pollAnswers, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `CreateTopicWithModerationCall` | actorId, actorName, forumId, forumSubject, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `DeletePost` | postId, actorName, actorPassword |  |
| `DeleteTopic` | topicId, actorName, actorPassword |  |
| `GetFilteredTopics` | params.forumId, params.filterId, params.actorId, pageIndex, pageSize |  |
| `GetForums` | — |  |
| `GetPostAmount` | topicId |  |
| `GetPostData` | postId |  |
| `GetPosts` | topicID, pageIndex, pageSize |  |
| `GetTopic` | topicId, actorId |  |
| `ToggleSticky` | actorName, actorPassword, topicId, type |  |
| `UpdatePost` | actorId |  |
| `UpdateTopic` | topic.TopicId |  |
| `UserDeletePost` | actorId, postId |  |

#### `WebService.NewsService.AMFNewsService`

Chemin AMF : `MovieStarPlanet.WebService.NewsService.AMFNewsService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActiveNewsScrapBlog` | param1 |  |
| `GetActiveNewsSlides` | param1 |  |
| `GetNewsById` | param1 |  |
| `NewsClicked` | param1, param2 |  |
| `SaveNews` | param1 |  |
| `SaveThemeSnapshot` | param1, param2, param3, param4, param5, param6 |  |
| `SetNewsUsage` | param1 |  |

#### `WebService.NotificationCenter.AMFNotificationCenterService`

Chemin AMF : `MovieStarPlanet.WebService.NotificationCenter.AMFNotificationCenterService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `ClaimBonus2` | actorId, contentTypes |  |
| `GetNotificationCount` | param1 |  |
| `GetNotificationsWithImageGuid` | param1 |  |
| `GetThirdPatyAppNotifications` | param1 |  |
| `GetTotalFameAward` | — |  |

### Highscores & thèmes

#### `WebService.Content.AmfContentService`

Chemin AMF : `MovieStarPlanet.WebService.Content.AmfContentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetItemsInCurrentTheme` | ticket, themeId, hash |  |
| `GetLastEditedDate` | param1, param2, param3, param4 |  |

#### `WebService.ExternalApps.AMFExternalAppsService`

Chemin AMF : `MovieStarPlanet.WebService.ExternalApps.AMFExternalAppsService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetExternalAppsInCountry` | variante 1: _loc2_, "ALL"<br>variante 2: countryCode, "Android"<br>variante 3: countryCode, "IOS" | 3 variantes |

#### `WebService.Highscore.AMFHighscoreService`

Chemin AMF : `MovieStarPlanet.WebService.Highscore.AMFHighscoreService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetHighscoreActor` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreAnimations` | pageIndex, pageSize |  |
| `GetHighscoreBackgrounds` | pageIndex, pageSize |  |
| `GetHighscoreBonster` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreClothes` | pageIndex, pageSize |  |
| `GetHighscoreItems` | pageIndex, pageSize |  |
| `GetHighscoreLook` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreMovie` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscorePet` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreScrapBlog` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreYouTube` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |

#### `WebService.WorldTheme.AMFWorldThemeService`

Chemin AMF : `MovieStarPlanet.WebService.WorldTheme.AMFWorldThemeService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateNewWorldTheme` | themeName, folderName, themeId |  |
| `CreateNewWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |  |
| `DeleteWorldTheme` | worldThemeId |  |
| `EditWorldTheme` | worldThemeId, themeName, themeId |  |
| `EditWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |  |
| `GetAllWorldThemes` | — |  |
| `GetOldWorldThemes` | — |  |
| `GetPresentFutureWorldThemes` | — |  |
| `GetWorldThemeAreasByWorldThemeId` | worldThemeId |  |
| `GetWorldThemeChatRoom` | worldThemeId |  |
| `GetWorldThemeInfo` | — |  |
| `SaveWorldThemeChatRoomInfo` | worldThemeId, roomName, backgroundFileName, requiredItemType, requiredItemId |  |

### Admin, upload, modération, infra

#### `WebService.AMFCommonService`

Chemin AMF : `MovieStarPlanet.WebService.AMFCommonService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `ActorHasLiked` | param3, param1, param2 |  |
| `LikeAdd` | entityType, entityId, selfActorId, receiver |  |
| `LogChat` | param1, param2, param3, InputLocations.DESTINATION_TYPE_USER |  |
| `LogInput` | roomId, actorId, roomInstanceId, message, destinationType |  |
| `SendContentEmail` | param1, param2, param3, param4, param5 |  |
| `getNowAsString` | — |  |

#### `WebService.Admin.AMFAdminService`

Chemin AMF : `MovieStarPlanet.WebService.Admin.AMFAdminService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BlockName` | param1, param2, param3 |  |
| `ClearCache` | param1, param2, true |  |
| `ClearNewMarkings` | param1, param2 |  |
| `DeleteTwitterText` | param1, param2, param3 |  |
| `GetActorLocale` | param1 |  |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize |  |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize |  |
| `GetBadWordActorList` | pageIndex, pageSize |  |
| `GetBlockedIP` | ipAsInt, moderatorName, moderatorPass |  |
| `GetBlockedInfo` | ipAsInt, moderatorName, moderatorPass |  |
| `GetBlockedNames` | searchphrase |  |
| `GetChatLogList` | actorId, pageIndex, pageSize |  |
| `GetChatLogListByReportTime` | paramObj.actorId, paramObj.reportId, pageIndex, pageSize |  |
| `GetChatLogListLocked` | actorId |  |
| `GetIPLoginType` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetIPUsers` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetIPWarnings` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetLocaleResources` | param1, param2, param3, param4, param5 |  |
| `GetLoginHistory` | param1, param2, param3 |  |
| `GetModeratorList` | pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |  |
| `GetModeratorWarningCount` | paramObj.moderatorId, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |  |
| `GetModeratorWarnings` | paramObj.moderatorId, paramObj.date, pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |  |
| `GetReportList` | onlyGetNotHandled, pageIndex, pageSize |  |
| `GetReportOverview` | — |  |
| `GetSecureModuleUrl` | — |  |
| `GetTotalModeratorActivitiesDone` | actorId, moderatorName, moderatorPass |  |
| `GetWarnedIPListNew` | paramObj.blocked, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass, paramObj.specificIp ? paramObj.specificIp : 0 |  |
| `GetWarningLog` | pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |  |
| `GiveAutoWarning` | param1, param2, param3, param4 |  |
| `IsAdminSite` | param1, param2 |  |
| `IsUploadSite` | — |  |
| `LockOutUser` | param1, param2, param3, param4, param5 |  |
| `RemoveRoboBlastContent` | actorId, contentType, contentId, reporterId, site |  |
| `ReportHandled` | reportId, handledByActorId |  |
| `SaveLocaleResources` | param1 |  |
| `UnblockName` | param1, param2, param3 |  |
| `blockIP` | ipAsIntToBlock, moderatorActorId, moderatorName, moderatorPass, blockingDaysCount, comment |  |
| `deleteMovieViaProfile` | movieId, moderatorName, moderatorPass |  |
| `getChatRoomOpenCloseTimes` | — |  |
| `isIPBlockedNew` | ipAsIntToFind, moderatorName, moderatorPass |  |
| `markIpAsPublic` | ipAsIntToMark, moderatorName, moderatorPass |  |
| `saveSpamReport` | spamtext, moderatorActorId, moderatorName, moderatorPass |  |
| `setChatRoomOpenCloseTimes` | open, close |  |
| `unblockIP` | ipAsIntToUnblock, moderatorID, moderatorName, moderatorPass, comment |  |
| `unmarkIpAsPublic` | ipAsIntToUnmark, moderatorName, moderatorPass |  |

#### `WebService.AnimationSnapshot.AMFAnimationSnapshotService`

Chemin AMF : `MovieStarPlanet.WebService.AnimationSnapshot.AMFAnimationSnapshotService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `getAnimationNames` | — |  |
| `saveImage` | data, name |  |

#### `WebService.Common.AMFCommonWebService`

Chemin AMF : `MovieStarPlanet.WebService.Common.AMFCommonWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetEntityName` | param1, param2 |  |
| `GetPlaylistExternalRef` | param1 |  |
| `LikeAdd` | entityType, entityId, actorId, receiverId |  |
| `SaveRoomWithSnapshot` | wallpaper, floor, arrayOfMyRoomInstances, roomSnapshotProfile, roomSnapshotMedium, roomSnapshotSmall |  |
| `SendContentEmail` | param1, param2, param3, param4, param5 |  |

#### `WebService.Logging.AMFLoggingService`

Chemin AMF : `MovieStarPlanet.WebService.Logging.AMFLoggingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `ClientLog` | param1, param2 |  |
| `CreateTestException` | — |  |
| `GetLatestServerException` | — |  |
| `LogClient` | param1, param2 |  |

#### `WebService.Moderation.AMFModeration`

Chemin AMF : `MovieStarPlanet.WebService.Moderation.AMFModeration`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CheckNewUsername` | userName, this._site |  |
| `FilterText` | variante 1: param1, param5, param4, param2, param3<br>variante 2: param1, param5, param4, param2, param3, param8, param9 | 2 variantes |
| `LoginEvent` | param1 |  |
| `ReportUser` | param2, param3, param4, param6, this._site, param7 |  |
| `ReportUserNeb` | param2, param5, param4, param6 |  |

#### `WebService.Os.AMFOs`

Chemin AMF : `MovieStarPlanet.WebService.Os.AMFOs`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateOsRef` | — |  |
| `RunOsCheck` | refId, hist.join(":") |  |

#### `WebService.PerformanceTracking.AMFPerformanceTrackingService`

Chemin AMF : `MovieStarPlanet.WebService.PerformanceTracking.AMFPerformanceTrackingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddEntry` | param1, param2 |  |

#### `WebService.Snapshots.AMFGenericSnapshotService`

Chemin AMF : `MovieStarPlanet.WebService.Snapshots.AMFGenericSnapshotService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateSnapshot` | variante 1: param1, param2, param3, param4<br>variante 2: param1, param2, param3, param4, param5 | 2 variantes |
| `CreateSnapshotSmallAndBig` | param1, param2, param3, param4, param5, param6 |  |

#### `WebService.TagManager.AMFTagManager`

Chemin AMF : `MovieStarPlanet.WebService.TagManager.AMFTagManager`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DeleteTag` | param1 |  |
| `GetAllTags` | — |  |
| `GetBackgroundTags` | — |  |
| `GetTagsForSkinClothes` | param2 |  |
| `GetTagsInCategorySkin` | param2, param3 |  |
| `SaveTag` | param1 |  |

#### `WebService.ThemeManager.AMFThemeManagerService`

Chemin AMF : `MovieStarPlanet.WebService.ThemeManager.AMFThemeManagerService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DeleteTheme` | param1 |  |
| `GetAllCampaigns` | — |  |
| `GetAllThemes` | — |  |
| `GetCurrectNewCategorySortIndex` | — |  |
| `InsertTheme` | param1, param2, param3, param4 |  |
| `LabelClothesWithTheme` | param1, param2 |  |
| `RetrieveThemeID` | param1, param2 |  |
| `SortShoppingItems` | param1, param2, param3 |  |
| `UpdateTheme` | param1 |  |

#### `WebService.Upload.AMFUploadService`

Chemin AMF : `MovieStarPlanet.WebService.Upload.AMFUploadService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CheckAnimationExists` | animationName |  |
| `DeleteClipArt` | clipart, subpath |  |
| `DeleteFacepart` | facepartId, type |  |
| `DeleteWallpaper` | wallpaperId |  |
| `EditAnimation` | animationId, name, price, discount, checkVip, checkNew, checkDeleted, animCategoryId, themeID, priceDiamonds |  |
| `EditClipArt` | clipart, subpath, sort, checkvip, checknew, price, diamondsPrice |  |
| `EditFacepart` | facepartId, type, gender, name, fileName, price, checkvip, checknew, checkreg, discount, sortorder, themeID, priceDiamonds |  |
| `FileExistsCheck` | key |  |
| `GetAnimationCategories` | — |  |
| `GetClipArtPath` | clipart |  |
| `InsertAnimation` | name, price, diamondsprice, animCategory, vip, fileName, themeID |  |
| `InsertBackground` | name, price, backgroundCategory, vip, fileName, themeID |  |
| `InsertClipArt` | type, category, fileName, checkvip, checkNew, sortorder, price, diamondPrice, colorScheme |  |
| `InsertFacepart` | type, gender, name, fileName, price, diamondPrice, checkvip, dragonBone, defaultColors, checknew, checkreg, discount, sortorder, themeID, date, hidden |  |
| `InsertWallpaper` | type, roomtype, name, filepath |  |
| `getAllColorschemelessClothes` | pageIdx, pageSize |  |
| `getBonsterInfo` | templateName |  |
| `getClipArtCategoryNames` | paramid |  |
| `getClipArtTypes` | — |  |
| `giveBonster` | templateName |  |
| `saveClothUpdater` | cloth, themeID |  |
| `setClothColorSchemes` | variante 1: [colorSchemeObject<br>variante 2: clothColorSchemes | 2 variantes |
| `updateAnimation` | copy, themeID |  |
| `updateBackground` | copy, themeID |  |
| `updateBonsterColors` | bonsterId, colorMatrix |  |
| `updateBonsterScale` | bonsterId, mobScale, webScale |  |
| `updateCloth` | clothUpdater |  |
| `updateMusic` | copy |  |
| `uploadBonster` | templateName, templateId, armatureName, price, diamondsPrice, isVIP, deleted, specialEggCrate, scale, scaleWeb |  |

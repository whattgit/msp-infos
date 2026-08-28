# III.7 — Pets AMF

> **EN** · [Français](../../fr/amf/07-pets.md)


Bonsters and legacy pets — server endpoints.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `PetFriendBonster` | `AMFBonsterService` | `entier SC` | No |
| `PetFriendPet` | `AMFPetService` | `—` | — |

## Response codes

| Code | Meaning | Client context |
|------|---------------|-----------------|
| `0` | Success | Interaction OK |
| `−1` | Server exception | Generic error popup |
| `−2` | Not VIP | VIP food/booster required |
| `−3` | Not enough SC | Food purchase |
| `−4` | Not enough diamonds | Bonbon |
| `−5` | Pet sick | Nourrir sans médicament d'abord |
| `−429` | Rate limited | Pet / interaction |

## `WebService.AMFMobilePetService`

**AMF path:** `MovieStarPlanet.WebService.AMFMobilePetService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CurePet` | param1 | AMF endpoint `CurePet`. | — |
| `FeedPet` | param1, param2 | AMF endpoint `FeedPet`. | — |
| `GetActorClickItem` | param1 | Fetches actor click item. | — |
| `GetClickItems` | — | Fetches click items. | — |
| `GetClickItemsForActor` | param1 | Fetches click items for actor. | — |
| `HatchPet` | param1, param2 | AMF endpoint `HatchPet`. | — |
| `PetFriendPet` | param1, param2 | AMF endpoint `PetFriendPet`. | `-429` |
| `PurchaseClickItem` | param1, param2 | AMF endpoint `PurchaseClickItem`. | — |
| `SavePetName` | param1, param2 | Saves / creates save pet name. | — |
| `WashPet` | param1, param2 | AMF endpoint `WashPet`. | — |

### Endpoint details

#### `CurePet`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `Monster.as`, `MonsterPopup.as` |
| Behavior | AMF endpoint `CurePet`. |

#### `FeedPet`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `Monster.as` |
| Behavior | AMF endpoint `FeedPet`. |

#### `GetActorClickItem`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `Monster.as`, `StarlingMonster.as`, `ContentLoaderMyRoom.as`, `AddClickItemToMovieStarCommand.as` (+2) |
| Behavior | Fetches actor click item. |

#### `GetClickItems`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ClickItemCatalog.as` (+6) |
| Behavior | Fetches click items. |

#### `GetClickItemsForActor`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+3) |
| UI / callers | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ChatRoomCommands.as` (+4) |
| Behavior | Fetches click items for actor. |

#### `HatchPet`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `Monster.as` |
| Behavior | AMF endpoint `HatchPet`. |

#### `PetFriendPet`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | `-429` on `—` (silent) |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `MonsterPopup.as`, `PetCommandsService.as` |
| Behavior | AMF endpoint `PetFriendPet`. |

#### `PurchaseClickItem`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+1) |
| Behavior | AMF endpoint `PurchaseClickItem`. |

#### `SavePetName`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `WebConfiguration.as` |
| Behavior | Saves / creates save pet name. |

#### `WashPet`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / callers | `Pet.as` |
| Behavior | AMF endpoint `WashPet`. |

## `WebService.Bonster.AMFBonsterService`

**AMF path:** `MovieStarPlanet.WebService.Bonster.AMFBonsterService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AnimationUsed` | actorBonsterRelId, animationId, actorId | AMF endpoint `AnimationUsed`. | — |
| `CheckInBonsterAtPetHotel` | actorBonsterRelId, bookTimeAmount, actorId | Place Bonster à l'hôtel (7/14/28 j, SC ou VIP). | — |
| `CheckOutBonsterFromPetHotel` | actorBonsterRelId, actorId | Fetches Bonster de l'hôtel. | — |
| `DeleteBonsterName` | actorBonsterRelId | Deletes e bonster name. | — |
| `FeedBonster` | actorBonsterRelId, foodId, actorId | Nourrit le Bonster ; retourne `BonsterInteractionResponse` (XP, barres, resultCode). | — |
| `GetBonsterAnimations` | param1, param2 | Fetches bonster animations. | — |
| `GetBonsterById` | actorBonsterRelId | Fetches bonster by id. | — |
| `GetBonsterCandyPrices` | — | Loads les paliers prix bonbon `{LevelFloor, LevelCeil, CandyPrice}` au login. | — |
| `GetBonsterListByActor` | actorId, loadAnimations, excludeHotel | Fetches bonster list by actor. | — |
| `GetBonsterTemplateList` | — | Fetches bonster template list. | — |
| `HatchBonster` | actorBonsterRelId, actorId | Fait éclore œuf/caisse ; `WashPoints=50` à l'éclosion. | — |
| `InstantEvolveBonster` | actorId, actorBonsterRelId | Évolution immédiate (booster `INSTANT_PET_GROW`). | — |
| `PetFriendBonster` | actorId, actorBonsterRelId | Caresse le pet d'un ami ; retourne **int SC** (pas d'objet). Rate limit `-429` silent. | `-429` |
| `PlayWithBonster` | actorBonsterRelId, playPoints, actorId | Joue avec le pet ; consomme playPoints (max 100 en UI). | — |
| `RenameBonster` | actorBonsterRelId, name, actorId | AMF endpoint `RenameBonster`. | — |
| `SaveNewAndOldPetsPositionsInMyRoom` | actorId, bonsterPositionsList, clickItemsList | Saves / creates save new and old pets positions in my room. | — |
| `WashBonster` | actorBonsterRelId, washPoints, actorId | Lave le pet ; consomme les washPoints accumulés en mini-jeu UI. | — |

### Endpoint details

#### `AnimationUsed`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, animationId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `AnimListItemRendererMediator.as` |
| Behavior | AMF endpoint `AnimationUsed`. |

#### `CheckInBonsterAtPetHotel`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, bookTimeAmount, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `PetHotel.as` |
| Behavior | Place Bonster à l'hôtel (7/14/28 j, SC ou VIP). |

#### `CheckOutBonsterFromPetHotel`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `PetHotel.as` |
| Behavior | Fetches Bonster de l'hôtel. |

#### `DeleteBonsterName`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Behavior | Deletes e bonster name. |

#### `FeedBonster`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, foodId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `BuyPetFoodCommand.as` |
| Behavior | Nourrit le Bonster ; retourne `BonsterInteractionResponse` (XP, barres, resultCode). |

#### `GetBonsterAnimations`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Behavior | Fetches bonster animations. |

#### `GetBonsterById`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `ChatRoomDragonBonesAvatar.as`, `AddClickItemToMovieStarCommand.as`, `MovieStudioLogic.as`, `GetPetDataCommand.as` (+1) |
| Behavior | Fetches bonster by id. |

#### `GetBonsterCandyPrices`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `LoginRequiredSetupCommand.as` |
| Behavior | Loads les paliers prix bonbon `{LevelFloor, LevelCeil, CandyPrice}` au login. |

#### `GetBonsterListByActor`

| Property | Value |
|----------|-------|
| Parameters | actorId, loadAnimations, excludeHotel |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `MSP_InventoryContainer.as`, `StuffView.as`, `InventoryLoader.as`, `ChatRoomCommands.as` (+2) |
| Behavior | Fetches bonster list by actor. |

#### `GetBonsterTemplateList`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `LoginRequiredSetupCommand.as`, `MovieStudioLogic.as` |
| Behavior | Fetches bonster template list. |

#### `HatchBonster`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `BonsterClickItem.as` |
| Behavior | Fait éclore œuf/caisse ; `WashPoints=50` à l'éclosion. |

#### `InstantEvolveBonster`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorBonsterRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `BonsterService.as`, `InstantPetGrowDiamondShopPreview.as` |
| Behavior | Évolution immédiate (booster `INSTANT_PET_GROW`). |

#### `PetFriendBonster`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorBonsterRelId |
| AMF ticket | Yes |
| Rate limit | `-429` on `entier SC` (silent) |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Behavior | Caresse le pet d'un ami ; retourne **int SC** (pas d'objet). Rate limit `-429` silent. |

#### `PlayWithBonster`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, playPoints, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Behavior | Joue avec le pet ; consomme playPoints (max 100 en UI). |

#### `RenameBonster`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, name, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `SavePetNameCommand.as` |
| Behavior | AMF endpoint `RenameBonster`. |

#### `SaveNewAndOldPetsPositionsInMyRoom`

| Property | Value |
|----------|-------|
| Parameters | actorId, bonsterPositionsList, clickItemsList |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `StuffView.as` |
| Behavior | Saves / creates save new and old pets positions in my room. |

#### `WashBonster`

| Property | Value |
|----------|-------|
| Parameters | actorBonsterRelId, washPoints, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / callers | `WashCommand.as` |
| Behavior | Lave le pet ; consomme les washPoints accumulés en mini-jeu UI. |

## `WebService.Bonster.AMFBonsterShopService`

**AMF path:** `MovieStarPlanet.WebService.Bonster.AMFBonsterShopService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BuyBonster` | actorId, bonsterId | Buys bonster. | — |
| `GetCampaignBonster` | — | Fetches campaign bonster. | — |
| `GetListOfAllBonstersAndBoonies` | — | Fetches list of all bonsters and boonies. | — |
| `GetListOfBonsters` | — | Fetches list of bonsters. | — |
| `GetListOfBoonies` | — | Fetches list of boonies. | — |
| `GetPagedListOfBonsters` | pageId, pageSize | Paged list — Paged List Of Bonsters. | — |
| `GetPagedListOfBoonies` | pageId, pageSize | Paged list — Paged List Of Boonies. | — |
| `GetPagedListOfFriendsPets` | pageId, pageSize | Paged list — Paged List Of Friends Pets. | — |
| `GetPagedListOfNewPets` | pageId, pageSize | Paged list — Paged List Of New Pets. | — |
| `GetPagedListOfTopPets` | pageId, pageSize | Paged list — Paged List Of Top Pets. | — |

### Endpoint details

#### `BuyBonster`

| Property | Value |
|----------|-------|
| Parameters | actorId, bonsterId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `BuyCommand.as`, `PetShopContentService.as` |
| Behavior | Buys bonster. |

#### `GetCampaignBonster`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopModel.as`, `PetShopContentService.as` |
| Behavior | Fetches campaign bonster. |

#### `GetListOfAllBonstersAndBoonies`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `BonsterTester.as` |
| Behavior | Fetches list of all bonsters and boonies. |

#### `GetListOfBonsters`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopContentService.as` |
| Behavior | Fetches list of bonsters. |

#### `GetListOfBoonies`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopContentService.as` |
| Behavior | Fetches list of boonies. |

#### `GetPagedListOfBonsters`

| Property | Value |
|----------|-------|
| Parameters | pageId, pageSize |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopModel.as`, `PetShopContentService.as` |
| Behavior | Paged list — Paged List Of Bonsters. |

#### `GetPagedListOfBoonies`

| Property | Value |
|----------|-------|
| Parameters | pageId, pageSize |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopModel.as`, `PetShopContentService.as` |
| Behavior | Paged list — Paged List Of Boonies. |

#### `GetPagedListOfFriendsPets`

| Property | Value |
|----------|-------|
| Parameters | pageId, pageSize |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopModel.as`, `PetShopContentService.as` |
| Behavior | Paged list — Paged List Of Friends Pets. |

#### `GetPagedListOfNewPets`

| Property | Value |
|----------|-------|
| Parameters | pageId, pageSize |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopModel.as`, `PetShopContentService.as` |
| Behavior | Paged list — Paged List Of New Pets. |

#### `GetPagedListOfTopPets`

| Property | Value |
|----------|-------|
| Parameters | pageId, pageSize |
| AMF ticket | No |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / callers | `PetShopModel.as`, `PetShopContentService.as` |
| Behavior | Paged list — Paged List Of Top Pets. |

## `WebService.Pets.AMFPetService`

**AMF path:** `MovieStarPlanet.WebService.Pets.AMFPetService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BuyClickItem` | actorId, clickItemId | Buys click item. | — |
| `CheckInPetHotel` | actorId, clickItemRelId, stayPeriod | Checks in pet hotel. | — |
| `CheckOutPetHotel` | actorId, clickItemRelId | Checks out pet hotel. | — |
| `CurePet` | actorClickItemRelId | AMF endpoint `CurePet`. | — |
| `DeletePetName` | clickItemId, moderatorName, moderatorPass | Deletes e pet name. | — |
| `FeedPet` | actorClickItemRelId, foodPoints | AMF endpoint `FeedPet`. | — |
| `GetActorClickItem` | actorClickItemRelId | Fetches actor click item. | — |
| `GetClickItems` | — | Fetches click items. | — |
| `GetClickItemsForActor` | (actorid) · (param1) | Fetches click items for actor. | — |
| `GetClickItemsForActorThatCanStillGrow` | actorid | Fetches click items for actor that can still grow. | — |
| `GetClickItemsForActorWithPrice` | actorid | Fetches click items for actor with price. | — |
| `GetClickItemsForPetHotel` | actorId | Fetches click items for pet hotel. | — |
| `HarvestPlant` | actorId, actorClickItemRelId | AMF endpoint `HarvestPlant`. | — |
| `HatchPet` | actorClickItemRelId, configuration | AMF endpoint `HatchPet`. | — |
| `PetFriendPet` | actorId, actorClickItemRelId | AMF endpoint `PetFriendPet`. | `-429` |
| `PlayedPetGame` | actorClickItemRelId, playPoints | AMF endpoint `PlayedPetGame`. | — |
| `SaveClickItemLocations` | locations | Saves / creates save click item locations. | — |
| `SavePetName` | actorClickItemRelId, name | Saves / creates save pet name. | — |
| `WashPet` | actorId, actorClickItemRelId | AMF endpoint `WashPet`. | — |

### Endpoint details

#### `BuyClickItem`

| Property | Value |
|----------|-------|
| Parameters | actorId, clickItemId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `ClickItemShop.as` |
| Behavior | Buys click item. |

#### `CheckInPetHotel`

| Property | Value |
|----------|-------|
| Parameters | actorId, clickItemRelId, stayPeriod |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `PetHotel.as` |
| Behavior | Checks in pet hotel. |

#### `CheckOutPetHotel`

| Property | Value |
|----------|-------|
| Parameters | actorId, clickItemRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `PetHotel.as` |
| Behavior | Checks out pet hotel. |

#### `CurePet`

| Property | Value |
|----------|-------|
| Parameters | actorClickItemRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `Monster.as`, `MonsterPopup.as` |
| Behavior | AMF endpoint `CurePet`. |

#### `DeletePetName`

| Property | Value |
|----------|-------|
| Parameters | clickItemId, moderatorName, moderatorPass |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `MonsterPopup.as` |
| Behavior | Deletes e pet name. |

#### `FeedPet`

| Property | Value |
|----------|-------|
| Parameters | actorClickItemRelId, foodPoints |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `Monster.as` |
| Behavior | AMF endpoint `FeedPet`. |

#### `GetActorClickItem`

| Property | Value |
|----------|-------|
| Parameters | actorClickItemRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `Monster.as`, `StarlingMonster.as`, `ContentLoaderMyRoom.as`, `AddClickItemToMovieStarCommand.as` (+2) |
| Behavior | Fetches actor click item. |

#### `GetClickItems`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ClickItemCatalog.as` (+6) |
| Behavior | Fetches click items. |

#### `GetClickItemsForActor`

| Property | Value |
|----------|-------|
| Parameters | (actorid) · (param1) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+3) |
| UI / callers | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ChatRoomCommands.as` (+4) |
| Behavior | Fetches click items for actor. |

#### `GetClickItemsForActorThatCanStillGrow`

| Property | Value |
|----------|-------|
| Parameters | actorid |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| Behavior | Fetches click items for actor that can still grow. |

#### `GetClickItemsForActorWithPrice`

| Property | Value |
|----------|-------|
| Parameters | actorid |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `InventoryPagingUtils.as` |
| Behavior | Fetches click items for actor with price. |

#### `GetClickItemsForPetHotel`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `PetHotel.as` |
| Behavior | Fetches click items for pet hotel. |

#### `HarvestPlant`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorClickItemRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `MonsterPopup.as` |
| Behavior | AMF endpoint `HarvestPlant`. |

#### `HatchPet`

| Property | Value |
|----------|-------|
| Parameters | actorClickItemRelId, configuration |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `Monster.as` |
| Behavior | AMF endpoint `HatchPet`. |

#### `PetFriendPet`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorClickItemRelId |
| AMF ticket | Yes |
| Rate limit | `-429` on `—` (silent) |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `MonsterPopup.as`, `PetCommandsService.as` |
| Behavior | AMF endpoint `PetFriendPet`. |

#### `PlayedPetGame`

| Property | Value |
|----------|-------|
| Parameters | actorClickItemRelId, playPoints |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / callers | `Pet.as` |
| Behavior | AMF endpoint `PlayedPetGame`. |

#### `SaveClickItemLocations`

| Property | Value |
|----------|-------|
| Parameters | locations |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` |
| Behavior | Saves / creates save click item locations. |

#### `SavePetName`

| Property | Value |
|----------|-------|
| Parameters | actorClickItemRelId, name |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `WebConfiguration.as` |
| Behavior | Saves / creates save pet name. |

#### `WashPet`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorClickItemRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| AMF client | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / callers | `Pet.as` |
| Behavior | AMF endpoint `WashPet`. |

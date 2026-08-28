# III.3 — Avatar & clothes

> **EN** · [Français](../../fr/amf/03-avatar.md)


Wardrobe, equipment, clothes purchase, MovieStar loader.

## `WebService.BeautyClinic.AMFBeautyClinicService`

**AMF path:** `MovieStarPlanet.WebService.BeautyClinic.AMFBeautyClinicService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BuyBeautyClinicItems` | actorId, eyeId, eyeShadowId, noseId, mouthId, eyeColors, eyeShadowColors, mouthColors, skinColor, removeEyeShadow | Buys beauty clinic items. | — |
| `BuyManyBeautyClinicItems` | actorId, itemsArray | Buys many beauty clinic items. | — |
| `GetMyBeautyClinicItems` | actorId | Fetches my beauty clinic items. | — |
| `GetMyBeautyClinicItemsWithHiddenOption` | actorId, includeHidden | Fetches my beauty clinic items with hidden option. | — |
| `LoadDataForBeautyClinic` | — | Loads data for beauty clinic. | — |
| `LoadModeratorDataForBeautyClinic` | — | Loads moderator data for beauty clinic. | — |
| `WearItems` | actorId, inventoryIdArray | AMF endpoint `WearItems`. | — |

### Endpoint details

#### `BuyBeautyClinicItems`

| Property | Value |
|----------|-------|
| Parameters | actorId, eyeId, eyeShadowId, noseId, mouthId, eyeColors, eyeShadowColors, mouthColors, skinColor, removeEyeShadow |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| Behavior | Buys beauty clinic items. |

#### `BuyManyBeautyClinicItems`

| Property | Value |
|----------|-------|
| Parameters | actorId, itemsArray |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / callers | `BeautyClinicBuyCommand.as` |
| Behavior | Buys many beauty clinic items. |

#### `GetMyBeautyClinicItems`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / callers | `BeautyClinicModel.as` |
| Behavior | Fetches my beauty clinic items. |

#### `GetMyBeautyClinicItemsWithHiddenOption`

| Property | Value |
|----------|-------|
| Parameters | actorId, includeHidden |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / callers | `BeautyClinicModel.as` |
| Behavior | Fetches my beauty clinic items with hidden option. |

#### `LoadDataForBeautyClinic`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| Behavior | Loads data for beauty clinic. |

#### `LoadModeratorDataForBeautyClinic`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| Behavior | Loads moderator data for beauty clinic. |

#### `WearItems`

| Property | Value |
|----------|-------|
| Parameters | actorId, inventoryIdArray |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / callers | `BeautyClinicWearCommand.as` |
| Behavior | AMF endpoint `WearItems`. |

## `WebService.MovieStar.AMFMovieStarService`

**AMF path:** `MovieStarPlanet.WebService.MovieStar.AMFMovieStarService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetActorClothesRel` | relId | Fetches actor clothes rel. | — |
| `GetActorClothesRelList` | rels | Fetches actor clothes rel list. | — |
| `GetContextClothes` | actorId, contextId | Fetches context clothes. | — |
| `LoadActorBonstersPaged` | actorId, pageIndex, pageSize | Loads actor bonsters paged. | — |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 | Loads actor with current clothes and spritesheet. | — |
| `LoadClothes` | skinId, shopId | Loads clothes. | — |
| `LoadClothesByIds` | clothesIds | Loads clothes by ids. | — |
| `LoadClothesFromThemeId` | themeId | Loads clothes from theme id. | — |
| `LoadClothesWithThemeByIds` | clothesIds | Loads clothes with theme by ids. | — |
| `LoadDataForRegisterNewUser` | — | Loads data for register new user. | — |
| `LoadFaceParts` | — | Loads face parts. | — |
| `LoadMovieStarFlatMinimum` | actorId | Loads movie star flat minimum. | — |
| `LoadMovieStarFlatRevised` | actorId | Loads movie star flat revised. | — |
| `LoadMovieStarListRevised` | actorIds | Loads movie star list revised. | — |
| `LoadMovieStarRevised` | actorId | Loads movie star revised. | — |
| `LoadPagedActorClothes` | param1, param2, param3 | Loads paged actor clothes. | — |
| `LoadPagedActorGiftableClothes` | param1, param2, param3 | Loads paged actor giftable clothes. | — |
| `LoadPagedActorGiftableItems` | param1, param2, param3 | Loads paged actor giftable items. | — |
| `LoadPagedActorItems` | actorId, pageIndex, pageSize | Loads paged actor items. | — |
| `LoadRoomItems` | actorId | Loads room items. | — |
| `UpdateClothes` | actorId, actorClothesRelIds[] | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. | — |
| `getRandomClothesByType` | slotType, isFemale, amount | AMF endpoint `getRandomClothesByType`. | — |

### Endpoint details

#### `GetActorClothesRel`

| Property | Value |
|----------|-------|
| Parameters | relId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `ActivityItemTradeCompleted.as`, `ActivityItemTradeRequest.as`, `FinalizeTrade.as`, `DesignerBrowserPreviewViewWeb.as` (+8) |
| Behavior | Fetches actor clothes rel. |

#### `GetActorClothesRelList`

| Property | Value |
|----------|-------|
| Parameters | rels |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `MovieStudioLogic.as` |
| Behavior | Fetches actor clothes rel list. |

#### `GetContextClothes`

| Property | Value |
|----------|-------|
| Parameters | actorId, contextId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Fetches context clothes. |

#### `LoadActorBonstersPaged`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads actor bonsters paged. |

#### `LoadActorWithCurrentClothesAndSpritesheet`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| Behavior | Loads actor with current clothes and spritesheet. |

#### `LoadClothes`

| Property | Value |
|----------|-------|
| Parameters | skinId, shopId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `DressingPanel.as`, `StuffShop.as`, `DressingRoomClothesRenderer.as`, `NewsItemBrowser.as` (+1) |
| Behavior | Loads clothes. |

#### `LoadClothesByIds`

| Property | Value |
|----------|-------|
| Parameters | clothesIds |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `ShopContentProvider.as` |
| Behavior | Loads clothes by ids. |

#### `LoadClothesFromThemeId`

| Property | Value |
|----------|-------|
| Parameters | themeId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads clothes from theme id. |

#### `LoadClothesWithThemeByIds`

| Property | Value |
|----------|-------|
| Parameters | clothesIds |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `ShopContentProvider.as` |
| Behavior | Loads clothes with theme by ids. |

#### `LoadDataForRegisterNewUser`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| UI / callers | `RegisterNewUserComponent.as` |
| Behavior | Loads data for register new user. |

#### `LoadFaceParts`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `DragonStarBase.as`, `MovieStarSpriteMobile.as` |
| Behavior | Loads face parts. |

#### `LoadMovieStarFlatMinimum`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads movie star flat minimum. |

#### `LoadMovieStarFlatRevised`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads movie star flat revised. |

#### `LoadMovieStarListRevised`

| Property | Value |
|----------|-------|
| Parameters | actorIds |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| UI / callers | `ActorCache.as` |
| Behavior | Loads movie star list revised. |

#### `LoadMovieStarRevised`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads movie star revised. |

#### `LoadPagedActorClothes`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads paged actor clothes. |

#### `LoadPagedActorGiftableClothes`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads paged actor giftable clothes. |

#### `LoadPagedActorGiftableItems`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `MSP_InventoryContainer.as` |
| Behavior | Loads paged actor giftable items. |

#### `LoadPagedActorItems`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Behavior | Loads paged actor items. |

#### `LoadRoomItems`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `StuffView.as` |
| Behavior | Loads room items. |

#### `UpdateClothes`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorClothesRelIds[] |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| UI / callers | `SaveClothesCommand.as` |
| Behavior | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. |

#### `getRandomClothesByType`

| Property | Value |
|----------|-------|
| Parameters | slotType, isFemale, amount |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / callers | `DressupGameBoard.as`, `DressupGameBoardNodeJs.as` |
| Behavior | AMF endpoint `getRandomClothesByType`. |

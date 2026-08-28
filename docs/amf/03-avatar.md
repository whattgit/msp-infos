# V.3 — Avatar & vêtements

Garde-robe, équipement, achat clothes, MovieStar loader.

## `WebService.BeautyClinic.AMFBeautyClinicService`

**Chemin AMF :** `MovieStarPlanet.WebService.BeautyClinic.AMFBeautyClinicService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BuyBeautyClinicItems` | actorId, eyeId, eyeShadowId, noseId, mouthId, eyeColors, eyeShadowColors, mouthColors, skinColor, removeEyeShadow | Achète beauty clinic items. | — |
| `BuyManyBeautyClinicItems` | actorId, itemsArray | Achète many beauty clinic items. | — |
| `GetMyBeautyClinicItems` | actorId | Récupère my beauty clinic items. | — |
| `GetMyBeautyClinicItemsWithHiddenOption` | actorId, includeHidden | Récupère my beauty clinic items with hidden option. | — |
| `LoadDataForBeautyClinic` | — | Charge data for beauty clinic. | — |
| `LoadModeratorDataForBeautyClinic` | — | Charge moderator data for beauty clinic. | — |
| `WearItems` | actorId, inventoryIdArray | Endpoint AMF `WearItems`. | — |

### Détail endpoints

#### `BuyBeautyClinicItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, eyeId, eyeShadowId, noseId, mouthId, eyeColors, eyeShadowColors, mouthColors, skinColor, removeEyeShadow |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| Fonctionnement | Achète beauty clinic items. |

#### `BuyManyBeautyClinicItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, itemsArray |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / appelants | `BeautyClinicBuyCommand.as` |
| Fonctionnement | Achète many beauty clinic items. |

#### `GetMyBeautyClinicItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / appelants | `BeautyClinicModel.as` |
| Fonctionnement | Récupère my beauty clinic items. |

#### `GetMyBeautyClinicItemsWithHiddenOption`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, includeHidden |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / appelants | `BeautyClinicModel.as` |
| Fonctionnement | Récupère my beauty clinic items with hidden option. |

#### `LoadDataForBeautyClinic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| Fonctionnement | Charge data for beauty clinic. |

#### `LoadModeratorDataForBeautyClinic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| Fonctionnement | Charge moderator data for beauty clinic. |

#### `WearItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, inventoryIdArray |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/module/beautyclinic/service/BeautyClinicService.as` |
| UI / appelants | `BeautyClinicWearCommand.as` |
| Fonctionnement | Endpoint AMF `WearItems`. |

## `WebService.MovieStar.AMFMovieStarService`

**Chemin AMF :** `MovieStarPlanet.WebService.MovieStar.AMFMovieStarService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetActorClothesRel` | relId | Récupère actor clothes rel. | — |
| `GetActorClothesRelList` | rels | Récupère actor clothes rel list. | — |
| `GetContextClothes` | actorId, contextId | Récupère context clothes. | — |
| `LoadActorBonstersPaged` | actorId, pageIndex, pageSize | Charge actor bonsters paged. | — |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 | Charge actor with current clothes and spritesheet. | — |
| `LoadClothes` | skinId, shopId | Charge clothes. | — |
| `LoadClothesByIds` | clothesIds | Charge clothes by ids. | — |
| `LoadClothesFromThemeId` | themeId | Charge clothes from theme id. | — |
| `LoadClothesWithThemeByIds` | clothesIds | Charge clothes with theme by ids. | — |
| `LoadDataForRegisterNewUser` | — | Charge data for register new user. | — |
| `LoadFaceParts` | — | Charge face parts. | — |
| `LoadMovieStarFlatMinimum` | actorId | Charge movie star flat minimum. | — |
| `LoadMovieStarFlatRevised` | actorId | Charge movie star flat revised. | — |
| `LoadMovieStarListRevised` | actorIds | Charge movie star list revised. | — |
| `LoadMovieStarRevised` | actorId | Charge movie star revised. | — |
| `LoadPagedActorClothes` | param1, param2, param3 | Charge paged actor clothes. | — |
| `LoadPagedActorGiftableClothes` | param1, param2, param3 | Charge paged actor giftable clothes. | — |
| `LoadPagedActorGiftableItems` | param1, param2, param3 | Charge paged actor giftable items. | — |
| `LoadPagedActorItems` | actorId, pageIndex, pageSize | Charge paged actor items. | — |
| `LoadRoomItems` | actorId | Charge room items. | — |
| `UpdateClothes` | actorId, actorClothesRelIds[] | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. | — |
| `getRandomClothesByType` | slotType, isFemale, amount | Endpoint AMF `getRandomClothesByType`. | — |

### Détail endpoints

#### `GetActorClothesRel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | relId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `ActivityItemTradeCompleted.as`, `ActivityItemTradeRequest.as`, `FinalizeTrade.as`, `DesignerBrowserPreviewViewWeb.as` (+8) |
| Fonctionnement | Récupère actor clothes rel. |

#### `GetActorClothesRelList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | rels |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `MovieStudioLogic.as` |
| Fonctionnement | Récupère actor clothes rel list. |

#### `GetContextClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, contextId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Récupère context clothes. |

#### `LoadActorBonstersPaged`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge actor bonsters paged. |

#### `LoadActorWithCurrentClothesAndSpritesheet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| Fonctionnement | Charge actor with current clothes and spritesheet. |

#### `LoadClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, shopId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `DressingPanel.as`, `StuffShop.as`, `DressingRoomClothesRenderer.as`, `NewsItemBrowser.as` (+1) |
| Fonctionnement | Charge clothes. |

#### `LoadClothesByIds`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clothesIds |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `ShopContentProvider.as` |
| Fonctionnement | Charge clothes by ids. |

#### `LoadClothesFromThemeId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | themeId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge clothes from theme id. |

#### `LoadClothesWithThemeByIds`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clothesIds |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `ShopContentProvider.as` |
| Fonctionnement | Charge clothes with theme by ids. |

#### `LoadDataForRegisterNewUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| UI / appelants | `RegisterNewUserComponent.as` |
| Fonctionnement | Charge data for register new user. |

#### `LoadFaceParts`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `DragonStarBase.as`, `MovieStarSpriteMobile.as` |
| Fonctionnement | Charge face parts. |

#### `LoadMovieStarFlatMinimum`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge movie star flat minimum. |

#### `LoadMovieStarFlatRevised`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge movie star flat revised. |

#### `LoadMovieStarListRevised`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorIds |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| UI / appelants | `ActorCache.as` |
| Fonctionnement | Charge movie star list revised. |

#### `LoadMovieStarRevised`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge movie star revised. |

#### `LoadPagedActorClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge paged actor clothes. |

#### `LoadPagedActorGiftableClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge paged actor giftable clothes. |

#### `LoadPagedActorGiftableItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `MSP_InventoryContainer.as` |
| Fonctionnement | Charge paged actor giftable items. |

#### `LoadPagedActorItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| Fonctionnement | Charge paged actor items. |

#### `LoadRoomItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `StuffView.as` |
| Fonctionnement | Charge room items. |

#### `UpdateClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorClothesRelIds[] |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` (+1) |
| UI / appelants | `SaveClothesCommand.as` |
| Fonctionnement | Persiste la tenue portée (`ActorClothesRelId[]`) ; déclenche snapshot avatar. |

#### `getRandomClothesByType`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | slotType, isFemale, amount |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/moviestar/service/MovieStarService.as` |
| UI / appelants | `DressupGameBoard.as`, `DressupGameBoardNodeJs.as` |
| Fonctionnement | Endpoint AMF `getRandomClothesByType`. |

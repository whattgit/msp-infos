# III.7 — Pets AMF

> **FR** · [English](../../en/amf/07-pets.md)


Bonsters et legacy pets — endpoints serveur.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `PetFriendBonster` | `AMFBonsterService` | `entier SC` | Non |
| `PetFriendPet` | `AMFPetService` | `—` | — |

## Codes de réponse

| Code | Signification | Contexte client |
|------|---------------|-----------------|
| `0` | Succès | Interaction OK |
| `−1` | Exception serveur | Popup erreur générique |
| `−2` | Pas VIP | Nourriture/booster VIP requis |
| `−3` | Pas assez SC | Achat nourriture |
| `−4` | Pas assez diamants | Bonbon |
| `−5` | Pet malade | Nourrir sans médicament d'abord |
| `−429` | Rate limited | Caresse / interaction |

## `WebService.AMFMobilePetService`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFMobilePetService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CurePet` | param1 | Endpoint AMF `CurePet`. | — |
| `FeedPet` | param1, param2 | Endpoint AMF `FeedPet`. | — |
| `GetActorClickItem` | param1 | Récupère actor click item. | — |
| `GetClickItems` | — | Récupère click items. | — |
| `GetClickItemsForActor` | param1 | Récupère click items for actor. | — |
| `HatchPet` | param1, param2 | Endpoint AMF `HatchPet`. | — |
| `PetFriendPet` | param1, param2 | Endpoint AMF `PetFriendPet`. | `-429` |
| `PurchaseClickItem` | param1, param2 | Endpoint AMF `PurchaseClickItem`. | — |
| `SavePetName` | param1, param2 | Sauvegarde / crée save pet name. | — |
| `WashPet` | param1, param2 | Endpoint AMF `WashPet`. | — |

### Détail endpoints

#### `CurePet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `Monster.as`, `MonsterPopup.as` |
| Fonctionnement | Endpoint AMF `CurePet`. |

#### `FeedPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `Monster.as` |
| Fonctionnement | Endpoint AMF `FeedPet`. |

#### `GetActorClickItem`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `Monster.as`, `StarlingMonster.as`, `ContentLoaderMyRoom.as`, `AddClickItemToMovieStarCommand.as` (+2) |
| Fonctionnement | Récupère actor click item. |

#### `GetClickItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ClickItemCatalog.as` (+6) |
| Fonctionnement | Récupère click items. |

#### `GetClickItemsForActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+3) |
| UI / appelants | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ChatRoomCommands.as` (+4) |
| Fonctionnement | Récupère click items for actor. |

#### `HatchPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `Monster.as` |
| Fonctionnement | Endpoint AMF `HatchPet`. |

#### `PetFriendPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `—` (silencieux) |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `MonsterPopup.as`, `PetCommandsService.as` |
| Fonctionnement | Endpoint AMF `PetFriendPet`. |

#### `PurchaseClickItem`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+1) |
| Fonctionnement | Endpoint AMF `PurchaseClickItem`. |

#### `SavePetName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `WebConfiguration.as` |
| Fonctionnement | Sauvegarde / crée save pet name. |

#### `WashPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/clickitems/mobileservices/PetAmfServiceClickItem.as` (+2) |
| UI / appelants | `Pet.as` |
| Fonctionnement | Endpoint AMF `WashPet`. |

## `WebService.Bonster.AMFBonsterService`

**Chemin AMF :** `MovieStarPlanet.WebService.Bonster.AMFBonsterService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AnimationUsed` | actorBonsterRelId, animationId, actorId | Endpoint AMF `AnimationUsed`. | — |
| `CheckInBonsterAtPetHotel` | actorBonsterRelId, bookTimeAmount, actorId | Place Bonster à l'hôtel (7/14/28 j, SC ou VIP). | — |
| `CheckOutBonsterFromPetHotel` | actorBonsterRelId, actorId | Récupère Bonster de l'hôtel. | — |
| `DeleteBonsterName` | actorBonsterRelId | Supprime e bonster name. | — |
| `FeedBonster` | actorBonsterRelId, foodId, actorId | Nourrit le Bonster ; retourne `BonsterInteractionResponse` (XP, barres, resultCode). | — |
| `GetBonsterAnimations` | param1, param2 | Récupère bonster animations. | — |
| `GetBonsterById` | actorBonsterRelId | Récupère bonster by id. | — |
| `GetBonsterCandyPrices` | — | Charge les paliers prix bonbon `{LevelFloor, LevelCeil, CandyPrice}` au login. | — |
| `GetBonsterListByActor` | actorId, loadAnimations, excludeHotel | Récupère bonster list by actor. | — |
| `GetBonsterTemplateList` | — | Récupère bonster template list. | — |
| `HatchBonster` | actorBonsterRelId, actorId | Fait éclore œuf/caisse ; `WashPoints=50` à l'éclosion. | — |
| `InstantEvolveBonster` | actorId, actorBonsterRelId | Évolution immédiate (booster `INSTANT_PET_GROW`). | — |
| `PetFriendBonster` | actorId, actorBonsterRelId | Caresse le pet d'un ami ; retourne **int SC** (pas d'objet). Rate limit `-429` silencieux. | `-429` |
| `PlayWithBonster` | actorBonsterRelId, playPoints, actorId | Joue avec le pet ; consomme playPoints (max 100 en UI). | — |
| `RenameBonster` | actorBonsterRelId, name, actorId | Endpoint AMF `RenameBonster`. | — |
| `SaveNewAndOldPetsPositionsInMyRoom` | actorId, bonsterPositionsList, clickItemsList | Sauvegarde / crée save new and old pets positions in my room. | — |
| `WashBonster` | actorBonsterRelId, washPoints, actorId | Lave le pet ; consomme les washPoints accumulés en mini-jeu UI. | — |

### Détail endpoints

#### `AnimationUsed`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, animationId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `AnimListItemRendererMediator.as` |
| Fonctionnement | Endpoint AMF `AnimationUsed`. |

#### `CheckInBonsterAtPetHotel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, bookTimeAmount, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `PetHotel.as` |
| Fonctionnement | Place Bonster à l'hôtel (7/14/28 j, SC ou VIP). |

#### `CheckOutBonsterFromPetHotel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `PetHotel.as` |
| Fonctionnement | Récupère Bonster de l'hôtel. |

#### `DeleteBonsterName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Fonctionnement | Supprime e bonster name. |

#### `FeedBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, foodId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `BuyPetFoodCommand.as` |
| Fonctionnement | Nourrit le Bonster ; retourne `BonsterInteractionResponse` (XP, barres, resultCode). |

#### `GetBonsterAnimations`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Fonctionnement | Récupère bonster animations. |

#### `GetBonsterById`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `ChatRoomDragonBonesAvatar.as`, `AddClickItemToMovieStarCommand.as`, `MovieStudioLogic.as`, `GetPetDataCommand.as` (+1) |
| Fonctionnement | Récupère bonster by id. |

#### `GetBonsterCandyPrices`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `LoginRequiredSetupCommand.as` |
| Fonctionnement | Charge les paliers prix bonbon `{LevelFloor, LevelCeil, CandyPrice}` au login. |

#### `GetBonsterListByActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, loadAnimations, excludeHotel |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `MSP_InventoryContainer.as`, `StuffView.as`, `InventoryLoader.as`, `ChatRoomCommands.as` (+2) |
| Fonctionnement | Récupère bonster list by actor. |

#### `GetBonsterTemplateList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `LoginRequiredSetupCommand.as`, `MovieStudioLogic.as` |
| Fonctionnement | Récupère bonster template list. |

#### `HatchBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `BonsterClickItem.as` |
| Fonctionnement | Fait éclore œuf/caisse ; `WashPoints=50` à l'éclosion. |

#### `InstantEvolveBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorBonsterRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `BonsterService.as`, `InstantPetGrowDiamondShopPreview.as` |
| Fonctionnement | Évolution immédiate (booster `INSTANT_PET_GROW`). |

#### `PetFriendBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorBonsterRelId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `entier SC` (silencieux) |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Fonctionnement | Caresse le pet d'un ami ; retourne **int SC** (pas d'objet). Rate limit `-429` silencieux. |

#### `PlayWithBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, playPoints, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| Fonctionnement | Joue avec le pet ; consomme playPoints (max 100 en UI). |

#### `RenameBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, name, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `SavePetNameCommand.as` |
| Fonctionnement | Endpoint AMF `RenameBonster`. |

#### `SaveNewAndOldPetsPositionsInMyRoom`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, bonsterPositionsList, clickItemsList |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `StuffView.as` |
| Fonctionnement | Sauvegarde / crée save new and old pets positions in my room. |

#### `WashBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorBonsterRelId, washPoints, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterAMFService.as` |
| UI / appelants | `WashCommand.as` |
| Fonctionnement | Lave le pet ; consomme les washPoints accumulés en mini-jeu UI. |

## `WebService.Bonster.AMFBonsterShopService`

**Chemin AMF :** `MovieStarPlanet.WebService.Bonster.AMFBonsterShopService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BuyBonster` | actorId, bonsterId | Achète bonster. | — |
| `GetCampaignBonster` | — | Récupère campaign bonster. | — |
| `GetListOfAllBonstersAndBoonies` | — | Récupère list of all bonsters and boonies. | — |
| `GetListOfBonsters` | — | Récupère list of bonsters. | — |
| `GetListOfBoonies` | — | Récupère list of boonies. | — |
| `GetPagedListOfBonsters` | pageId, pageSize | Liste paginée — Paged List Of Bonsters. | — |
| `GetPagedListOfBoonies` | pageId, pageSize | Liste paginée — Paged List Of Boonies. | — |
| `GetPagedListOfFriendsPets` | pageId, pageSize | Liste paginée — Paged List Of Friends Pets. | — |
| `GetPagedListOfNewPets` | pageId, pageSize | Liste paginée — Paged List Of New Pets. | — |
| `GetPagedListOfTopPets` | pageId, pageSize | Liste paginée — Paged List Of Top Pets. | — |

### Détail endpoints

#### `BuyBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, bonsterId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `BuyCommand.as`, `PetShopContentService.as` |
| Fonctionnement | Achète bonster. |

#### `GetCampaignBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopModel.as`, `PetShopContentService.as` |
| Fonctionnement | Récupère campaign bonster. |

#### `GetListOfAllBonstersAndBoonies`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `BonsterTester.as` |
| Fonctionnement | Récupère list of all bonsters and boonies. |

#### `GetListOfBonsters`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopContentService.as` |
| Fonctionnement | Récupère list of bonsters. |

#### `GetListOfBoonies`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopContentService.as` |
| Fonctionnement | Récupère list of boonies. |

#### `GetPagedListOfBonsters`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageId, pageSize |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopModel.as`, `PetShopContentService.as` |
| Fonctionnement | Liste paginée — Paged List Of Bonsters. |

#### `GetPagedListOfBoonies`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageId, pageSize |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopModel.as`, `PetShopContentService.as` |
| Fonctionnement | Liste paginée — Paged List Of Boonies. |

#### `GetPagedListOfFriendsPets`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageId, pageSize |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopModel.as`, `PetShopContentService.as` |
| Fonctionnement | Liste paginée — Paged List Of Friends Pets. |

#### `GetPagedListOfNewPets`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageId, pageSize |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopModel.as`, `PetShopContentService.as` |
| Fonctionnement | Liste paginée — Paged List Of New Pets. |

#### `GetPagedListOfTopPets`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageId, pageSize |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/bonster/service/BonsterShopAMFService.as` |
| UI / appelants | `PetShopModel.as`, `PetShopContentService.as` |
| Fonctionnement | Liste paginée — Paged List Of Top Pets. |

## `WebService.Pets.AMFPetService`

**Chemin AMF :** `MovieStarPlanet.WebService.Pets.AMFPetService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BuyClickItem` | actorId, clickItemId | Achète click item. | — |
| `CheckInPetHotel` | actorId, clickItemRelId, stayPeriod | Vérifie in pet hotel. | — |
| `CheckOutPetHotel` | actorId, clickItemRelId | Vérifie out pet hotel. | — |
| `CurePet` | actorClickItemRelId | Endpoint AMF `CurePet`. | — |
| `DeletePetName` | clickItemId, moderatorName, moderatorPass | Supprime e pet name. | — |
| `FeedPet` | actorClickItemRelId, foodPoints | Endpoint AMF `FeedPet`. | — |
| `GetActorClickItem` | actorClickItemRelId | Récupère actor click item. | — |
| `GetClickItems` | — | Récupère click items. | — |
| `GetClickItemsForActor` | (actorid) · (param1) | Récupère click items for actor. | — |
| `GetClickItemsForActorThatCanStillGrow` | actorid | Récupère click items for actor that can still grow. | — |
| `GetClickItemsForActorWithPrice` | actorid | Récupère click items for actor with price. | — |
| `GetClickItemsForPetHotel` | actorId | Récupère click items for pet hotel. | — |
| `HarvestPlant` | actorId, actorClickItemRelId | Endpoint AMF `HarvestPlant`. | — |
| `HatchPet` | actorClickItemRelId, configuration | Endpoint AMF `HatchPet`. | — |
| `PetFriendPet` | actorId, actorClickItemRelId | Endpoint AMF `PetFriendPet`. | `-429` |
| `PlayedPetGame` | actorClickItemRelId, playPoints | Endpoint AMF `PlayedPetGame`. | — |
| `SaveClickItemLocations` | locations | Sauvegarde / crée save click item locations. | — |
| `SavePetName` | actorClickItemRelId, name | Sauvegarde / crée save pet name. | — |
| `WashPet` | actorId, actorClickItemRelId | Endpoint AMF `WashPet`. | — |

### Détail endpoints

#### `BuyClickItem`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clickItemId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `ClickItemShop.as` |
| Fonctionnement | Achète click item. |

#### `CheckInPetHotel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clickItemRelId, stayPeriod |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `PetHotel.as` |
| Fonctionnement | Vérifie in pet hotel. |

#### `CheckOutPetHotel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clickItemRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `PetHotel.as` |
| Fonctionnement | Vérifie out pet hotel. |

#### `CurePet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorClickItemRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `Monster.as`, `MonsterPopup.as` |
| Fonctionnement | Endpoint AMF `CurePet`. |

#### `DeletePetName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clickItemId, moderatorName, moderatorPass |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `MonsterPopup.as` |
| Fonctionnement | Supprime e pet name. |

#### `FeedPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorClickItemRelId, foodPoints |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `Monster.as` |
| Fonctionnement | Endpoint AMF `FeedPet`. |

#### `GetActorClickItem`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorClickItemRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `Monster.as`, `StarlingMonster.as`, `ContentLoaderMyRoom.as`, `AddClickItemToMovieStarCommand.as` (+2) |
| Fonctionnement | Récupère actor click item. |

#### `GetClickItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ClickItemCatalog.as` (+6) |
| Fonctionnement | Récupère click items. |

#### `GetClickItemsForActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (actorid) · (param1) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+3) |
| UI / appelants | `ClickItemShop.as`, `MSP_InventoryContainer.as`, `StuffView.as`, `ChatRoomCommands.as` (+4) |
| Fonctionnement | Récupère click items for actor. |

#### `GetClickItemsForActorThatCanStillGrow`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorid |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| Fonctionnement | Récupère click items for actor that can still grow. |

#### `GetClickItemsForActorWithPrice`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorid |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `InventoryPagingUtils.as` |
| Fonctionnement | Récupère click items for actor with price. |

#### `GetClickItemsForPetHotel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `PetHotel.as` |
| Fonctionnement | Récupère click items for pet hotel. |

#### `HarvestPlant`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorClickItemRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `MonsterPopup.as` |
| Fonctionnement | Endpoint AMF `HarvestPlant`. |

#### `HatchPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorClickItemRelId, configuration |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `Monster.as` |
| Fonctionnement | Endpoint AMF `HatchPet`. |

#### `PetFriendPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorClickItemRelId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `—` (silencieux) |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `MonsterPopup.as`, `PetCommandsService.as` |
| Fonctionnement | Endpoint AMF `PetFriendPet`. |

#### `PlayedPetGame`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorClickItemRelId, playPoints |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| UI / appelants | `Pet.as` |
| Fonctionnement | Endpoint AMF `PlayedPetGame`. |

#### `SaveClickItemLocations`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | locations |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` |
| Fonctionnement | Sauvegarde / crée save click item locations. |

#### `SavePetName`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorClickItemRelId, name |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `WebConfiguration.as` |
| Fonctionnement | Sauvegarde / crée save pet name. |

#### `WashPet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorClickItemRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `BonsterInteractionResponse.resultCode` : 0 · −1 · −2 VIP · −3 SC · −4 💎 · −5 malade · −429 |
| Client AMF | `com/moviestarplanet/pet/service/PetAMFService.as` (+2) |
| UI / appelants | `Pet.as` |
| Fonctionnement | Endpoint AMF `WashPet`. |

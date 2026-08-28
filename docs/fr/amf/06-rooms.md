# III.6 — Salles & chambres

> **FR** · [English](../../en/amf/06-rooms.md)


MyRoom load/save, wallpapers, love room.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `SaveRoomWithSnapshot` | `AMFRoomService` | `entier` | Oui |

## `WebService.AMFRoomServiceForMobile`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFRoomServiceForMobile`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetActorBonsterList` | param1, param2 | Récupère actor bonster list. | — |
| `GetActorClickItemList` | param1, param2 | Récupère actor click item list. | — |
| `GetActorClothesByShopId` | param1, param2, param3 | Récupère actor clothes by shop id. | — |
| `GetWallpapers` | param1, param2 | Récupère wallpapers. | — |
| `LoadHouse` | houseId, callingActorId | Charge chambre acteur (wallpaper, items, positions pets). | — |
| `LoadHouseAndSpecificRoom` | callingActorId, houseId, roomId | Charge house and specific room. | — |
| `LoveRoom` | actorId, roomOwnerId | Endpoint AMF `LoveRoom`. | — |
| `SaveRoomWithSnapshot` | actorId, roomData, snapshots[3] | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. | `-429` |

### Détail endpoints

#### `GetActorBonsterList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / appelants | `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère actor bonster list. |

#### `GetActorClickItemList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / appelants | `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère actor click item list. |

#### `GetActorClothesByShopId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / appelants | `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère actor clothes by shop id. |

#### `GetWallpapers`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / appelants | `EditMyRoom.as`, `DeleteWallpaper.as`, `InventoryLoader.as`, `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère wallpapers. |

#### `LoadHouse`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | houseId, callingActorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/roomService/service/MyRoomServices.as` |
| UI / appelants | `MyRoom.as` |
| Fonctionnement | Charge chambre acteur (wallpaper, items, positions pets). |

#### `LoadHouseAndSpecificRoom`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | callingActorId, houseId, roomId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/roomService/service/MyRoomServices.as` |
| Fonctionnement | Charge house and specific room. |

#### `LoveRoom`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, roomOwnerId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/roomService/service/MyRoomServices.as` |
| UI / appelants | `QuestEvent.as`, `LoveMyroomCommand.as` |
| Fonctionnement | Endpoint AMF `LoveRoom`. |

#### `SaveRoomWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, roomData, snapshots[3] |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `entier` (popup) |
| Codes retour | Champ `entier` == −429 (popup) |
| Client AMF | `com/moviestarplanet/roomService/service/MyRoomServices.as` (+1) |
| UI / appelants | `EditMyRoom.as`, `StuffView.as`, `SaveMyRoomCommand.as` |
| Fonctionnement | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. |

## `WebService.Room.AMFRoomService`

**Chemin AMF :** `MovieStarPlanet.WebService.Room.AMFRoomService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetActorBonsterList` | param1, param2 | Récupère actor bonster list. | — |
| `GetActorClickItemList` | param1, param2 | Récupère actor click item list. | — |
| `GetActorClothesByShopId` | param1, param2, param3 | Récupère actor clothes by shop id. | — |
| `GetWallpapers` | param1, param2 | Récupère wallpapers. | — |

### Détail endpoints

#### `GetActorBonsterList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / appelants | `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère actor bonster list. |

#### `GetActorClickItemList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / appelants | `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère actor click item list. |

#### `GetActorClothesByShopId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / appelants | `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère actor clothes by shop id. |

#### `GetWallpapers`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / appelants | `EditMyRoom.as`, `DeleteWallpaper.as`, `InventoryLoader.as`, `ContentLoaderMyRoom.as` |
| Fonctionnement | Récupère wallpapers. |

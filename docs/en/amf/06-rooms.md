# III.6 — Rooms

> **EN** · [Français](../../fr/amf/06-rooms.md)


MyRoom load/save, wallpapers, love room.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `SaveRoomWithSnapshot` | `AMFRoomService` | `entier` | Yes |

## `WebService.AMFRoomServiceForMobile`

**AMF path:** `MovieStarPlanet.WebService.AMFRoomServiceForMobile`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetActorBonsterList` | param1, param2 | Fetches actor bonster list. | — |
| `GetActorClickItemList` | param1, param2 | Fetches actor click item list. | — |
| `GetActorClothesByShopId` | param1, param2, param3 | Fetches actor clothes by shop id. | — |
| `GetWallpapers` | param1, param2 | Fetches wallpapers. | — |
| `LoadHouse` | houseId, callingActorId | Loads chambre acteur (wallpaper, items, positions pets). | — |
| `LoadHouseAndSpecificRoom` | callingActorId, houseId, roomId | Loads house and specific room. | — |
| `LoveRoom` | actorId, roomOwnerId | AMF endpoint `LoveRoom`. | — |
| `SaveRoomWithSnapshot` | actorId, roomData, snapshots[3] | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. | `-429` |

### Endpoint details

#### `GetActorBonsterList`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / callers | `ContentLoaderMyRoom.as` |
| Behavior | Fetches actor bonster list. |

#### `GetActorClickItemList`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / callers | `ContentLoaderMyRoom.as` |
| Behavior | Fetches actor click item list. |

#### `GetActorClothesByShopId`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / callers | `ContentLoaderMyRoom.as` |
| Behavior | Fetches actor clothes by shop id. |

#### `GetWallpapers`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfService.as` (+1) |
| UI / callers | `EditMyRoom.as`, `DeleteWallpaper.as`, `InventoryLoader.as`, `ContentLoaderMyRoom.as` |
| Behavior | Fetches wallpapers. |

#### `LoadHouse`

| Property | Value |
|----------|-------|
| Parameters | houseId, callingActorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/roomService/service/MyRoomServices.as` |
| UI / callers | `MyRoom.as` |
| Behavior | Loads chambre acteur (wallpaper, items, positions pets). |

#### `LoadHouseAndSpecificRoom`

| Property | Value |
|----------|-------|
| Parameters | callingActorId, houseId, roomId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/roomService/service/MyRoomServices.as` |
| Behavior | Loads house and specific room. |

#### `LoveRoom`

| Property | Value |
|----------|-------|
| Parameters | actorId, roomOwnerId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/roomService/service/MyRoomServices.as` |
| UI / callers | `QuestEvent.as`, `LoveMyroomCommand.as` |
| Behavior | AMF endpoint `LoveRoom`. |

#### `SaveRoomWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | actorId, roomData, snapshots[3] |
| AMF ticket | Yes |
| Rate limit | `-429` on `entier` (popup) |
| Return codes | Champ `entier` == −429 (popup) |
| AMF client | `com/moviestarplanet/roomService/service/MyRoomServices.as` (+1) |
| UI / callers | `EditMyRoom.as`, `StuffView.as`, `SaveMyRoomCommand.as` |
| Behavior | Sauvegarde chambre + 3 snapshots PNG ; retour entier ou -429. |

## `WebService.Room.AMFRoomService`

**AMF path:** `MovieStarPlanet.WebService.Room.AMFRoomService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetActorBonsterList` | param1, param2 | Fetches actor bonster list. | — |
| `GetActorClickItemList` | param1, param2 | Fetches actor click item list. | — |
| `GetActorClothesByShopId` | param1, param2, param3 | Fetches actor clothes by shop id. | — |
| `GetWallpapers` | param1, param2 | Fetches wallpapers. | — |

### Endpoint details

#### `GetActorBonsterList`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / callers | `ContentLoaderMyRoom.as` |
| Behavior | Fetches actor bonster list. |

#### `GetActorClickItemList`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / callers | `ContentLoaderMyRoom.as` |
| Behavior | Fetches actor click item list. |

#### `GetActorClothesByShopId`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / callers | `ContentLoaderMyRoom.as` |
| Behavior | Fetches actor clothes by shop id. |

#### `GetWallpapers`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/mobileservices/RoomAmfServiceForWeb.as` (+1) |
| UI / callers | `EditMyRoom.as`, `DeleteWallpaper.as`, `InventoryLoader.as`, `ContentLoaderMyRoom.as` |
| Behavior | Fetches wallpapers. |

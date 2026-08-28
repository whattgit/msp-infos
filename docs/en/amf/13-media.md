# III.13 — Media

> **EN** · [Français](../../fr/amf/13-media.md)


Owned animations, backgrounds, music.

## `MobileServices.AMFAnimationsServiceForMobile`

**AMF path:** `MovieStarPlanet.MobileServices.AMFAnimationsServiceForMobile`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetActorAnimationsByCategory` | param1 | Fetches actor animations by category. | — |
| `GetAnimationsByFrameLabels` | param1 | Fetches animations by frame labels. | — |

### Endpoint details

#### `GetActorAnimationsByCategory`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/animations/AMFAnimationsServiceForMobile.as` |
| UI / callers | `AnimationsServiceUtils.as` |
| Behavior | Fetches actor animations by category. |

#### `GetAnimationsByFrameLabels`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/animations/AMFAnimationsServiceForMobile.as` |
| Behavior | Fetches animations by frame labels. |

## `WebService.Media.AMFMediaService`

**AMF path:** `MovieStarPlanet.WebService.Media.AMFMediaService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetAnimations` | — | Fetches animations. | — |
| `GetBackgrounds` | false | Fetches backgrounds. | — |
| `GetBackgroundsPaged` | false, pageIndex, pageSize | Paged list — Backgrounds Paged. | — |
| `GetMusic` | false | Fetches music. | — |
| `GetMyAnimations` | param1 | Fetches my animations. | — |
| `GetMyBackgrounds` | param1 | Fetches my backgrounds. | — |
| `GetMyMusic` | param1 | Fetches my music. | — |
| `getAnimationCount` | param1 | AMF endpoint `getAnimationCount`. | — |
| `getClothesCount` | param1 | AMF endpoint `getClothesCount`. | — |
| `getPropsCount` | param1 | AMF endpoint `getPropsCount`. | — |

### Endpoint details

#### `GetAnimations`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / callers | `MSP_InventoryContainer.as`, `HighscoreAnimation.as`, `AnimationSelector.as`, `ChatRoomAnimationSelector.as` (+6) |
| Behavior | Fetches animations. |

#### `GetBackgrounds`

| Property | Value |
|----------|-------|
| Parameters | false |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / callers | `BackgroundSelector.as`, `CreateThemeForm.as`, `MSP_InventoryContainer.as`, `UploadBackgroundLogic.as` (+6) |
| Behavior | Fetches backgrounds. |

#### `GetBackgroundsPaged`

| Property | Value |
|----------|-------|
| Parameters | false, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / callers | `NewsItemBrowser.as` |
| Behavior | Paged list — Backgrounds Paged. |

#### `GetMusic`

| Property | Value |
|----------|-------|
| Parameters | false |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / callers | `MusicSelector.as`, `MusicShop.as` |
| Behavior | Fetches music. |

#### `GetMyAnimations`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / callers | `MediaListUtils.as` |
| Behavior | Fetches my animations. |

#### `GetMyBackgrounds`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / callers | `MediaListUtils.as` |
| Behavior | Fetches my backgrounds. |

#### `GetMyMusic`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / callers | `MediaListUtils.as` |
| Behavior | Fetches my music. |

#### `getAnimationCount`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| Behavior | AMF endpoint `getAnimationCount`. |

#### `getClothesCount`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| Behavior | AMF endpoint `getClothesCount`. |

#### `getPropsCount`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/MediaAMFService.as` |
| Behavior | AMF endpoint `getPropsCount`. |

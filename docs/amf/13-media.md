# V.13 — Média

Animations, backgrounds, musiques possédées.

## `MobileServices.AMFAnimationsServiceForMobile`

**Chemin AMF :** `MovieStarPlanet.MobileServices.AMFAnimationsServiceForMobile`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetActorAnimationsByCategory` | param1 | Récupère actor animations by category. | — |
| `GetAnimationsByFrameLabels` | param1 | Récupère animations by frame labels. | — |

### Détail endpoints

#### `GetActorAnimationsByCategory`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/animations/AMFAnimationsServiceForMobile.as` |
| UI / appelants | `AnimationsServiceUtils.as` |
| Fonctionnement | Récupère actor animations by category. |

#### `GetAnimationsByFrameLabels`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/animations/AMFAnimationsServiceForMobile.as` |
| Fonctionnement | Récupère animations by frame labels. |

## `WebService.Media.AMFMediaService`

**Chemin AMF :** `MovieStarPlanet.WebService.Media.AMFMediaService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetAnimations` | — | Récupère animations. | — |
| `GetBackgrounds` | false | Récupère backgrounds. | — |
| `GetBackgroundsPaged` | false, pageIndex, pageSize | Liste paginée — Backgrounds Paged. | — |
| `GetMusic` | false | Récupère music. | — |
| `GetMyAnimations` | param1 | Récupère my animations. | — |
| `GetMyBackgrounds` | param1 | Récupère my backgrounds. | — |
| `GetMyMusic` | param1 | Récupère my music. | — |
| `getAnimationCount` | param1 | Endpoint AMF `getAnimationCount`. | — |
| `getClothesCount` | param1 | Endpoint AMF `getClothesCount`. | — |
| `getPropsCount` | param1 | Endpoint AMF `getPropsCount`. | — |

### Détail endpoints

#### `GetAnimations`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / appelants | `MSP_InventoryContainer.as`, `HighscoreAnimation.as`, `AnimationSelector.as`, `ChatRoomAnimationSelector.as` (+6) |
| Fonctionnement | Récupère animations. |

#### `GetBackgrounds`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | false |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / appelants | `BackgroundSelector.as`, `CreateThemeForm.as`, `MSP_InventoryContainer.as`, `UploadBackgroundLogic.as` (+6) |
| Fonctionnement | Récupère backgrounds. |

#### `GetBackgroundsPaged`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | false, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / appelants | `NewsItemBrowser.as` |
| Fonctionnement | Liste paginée — Backgrounds Paged. |

#### `GetMusic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | false |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / appelants | `MusicSelector.as`, `MusicShop.as` |
| Fonctionnement | Récupère music. |

#### `GetMyAnimations`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / appelants | `MediaListUtils.as` |
| Fonctionnement | Récupère my animations. |

#### `GetMyBackgrounds`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / appelants | `MediaListUtils.as` |
| Fonctionnement | Récupère my backgrounds. |

#### `GetMyMusic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| UI / appelants | `MediaListUtils.as` |
| Fonctionnement | Récupère my music. |

#### `getAnimationCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| Fonctionnement | Endpoint AMF `getAnimationCount`. |

#### `getClothesCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| Fonctionnement | Endpoint AMF `getClothesCount`. |

#### `getPropsCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/MediaAMFService.as` |
| Fonctionnement | Endpoint AMF `getPropsCount`. |

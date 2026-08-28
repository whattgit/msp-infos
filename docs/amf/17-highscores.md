# V.17 — Highscores & thèmes

Classements, world themes.

## `WebService.Content.AmfContentService`

**Chemin AMF :** `MovieStarPlanet.WebService.Content.AmfContentService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetItemsInCurrentTheme` | ticket, themeId, hash | Récupère items in current theme. | — |
| `GetLastEditedDate` | param1, param2, param3, param4 | Récupère last edited date. | — |

### Détail endpoints

#### `GetItemsInCurrentTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ticket, themeId, hash |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/AMFContentService.as` |
| UI / appelants | `ThemeChatRoomUtils.as` |
| Fonctionnement | Récupère items in current theme. |

#### `GetLastEditedDate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/contentservices/AMFContentService.as` |
| Fonctionnement | Récupère last edited date. |

## `WebService.ExternalApps.AMFExternalAppsService`

**Chemin AMF :** `MovieStarPlanet.WebService.ExternalApps.AMFExternalAppsService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetExternalAppsInCountry` | (_loc2_, "ALL") · (countryCode, "Android") · (countryCode, "IOS") | Récupère external apps in country. | — |

### Détail endpoints

#### `GetExternalAppsInCountry`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (_loc2_, "ALL") · (countryCode, "Android") · (countryCode, "IOS") |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/MobileAdd/MobileAdView.as` (+1) |
| Fonctionnement | Récupère external apps in country. |

## `WebService.Highscore.AMFHighscoreService`

**Chemin AMF :** `MovieStarPlanet.WebService.Highscore.AMFHighscoreService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetHighscoreActor` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Récupère highscore actor. | — |
| `GetHighscoreAnimations` | pageIndex, pageSize | Récupère highscore animations. | — |
| `GetHighscoreBackgrounds` | pageIndex, pageSize | Récupère highscore backgrounds. | — |
| `GetHighscoreBonster` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Récupère highscore bonster. | — |
| `GetHighscoreClothes` | pageIndex, pageSize | Récupère highscore clothes. | — |
| `GetHighscoreItems` | pageIndex, pageSize | Récupère highscore items. | — |
| `GetHighscoreLook` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Récupère highscore look. | — |
| `GetHighscoreMovie` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Récupère highscore movie. | — |
| `GetHighscorePet` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Récupère highscore pet. | — |
| `GetHighscoreScrapBlog` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Récupère highscore scrap blog. | — |
| `GetHighscoreYouTube` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Récupère highscore you tube. | — |

### Détail endpoints

#### `GetHighscoreActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreMoviestar.as`, `HighscoreRoom.as` |
| Fonctionnement | Récupère highscore actor. |

#### `GetHighscoreAnimations`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| Fonctionnement | Récupère highscore animations. |

#### `GetHighscoreBackgrounds`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreBackground.as` |
| Fonctionnement | Récupère highscore backgrounds. |

#### `GetHighscoreBonster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreClickItem.as` |
| Fonctionnement | Récupère highscore bonster. |

#### `GetHighscoreClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreCloth.as` |
| Fonctionnement | Récupère highscore clothes. |

#### `GetHighscoreItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreCloth.as` |
| Fonctionnement | Récupère highscore items. |

#### `GetHighscoreLook`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreLook.as` |
| Fonctionnement | Récupère highscore look. |

#### `GetHighscoreMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreMovie.as`, `HighScoreMovieCache.as` |
| Fonctionnement | Récupère highscore movie. |

#### `GetHighscorePet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| Fonctionnement | Récupère highscore pet. |

#### `GetHighscoreScrapBlog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `ArtBookBrowserHelpers.as`, `HighscoreScrapBlog.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère highscore scrap blog. |

#### `GetHighscoreYouTube`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / appelants | `HighscoreYouTube.as` |
| Fonctionnement | Récupère highscore you tube. |

## `WebService.WorldTheme.AMFWorldThemeService`

**Chemin AMF :** `MovieStarPlanet.WebService.WorldTheme.AMFWorldThemeService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CreateNewWorldTheme` | themeName, folderName, themeId | Sauvegarde / crée create new world theme. | — |
| `CreateNewWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName | Sauvegarde / crée create new world theme areas. | — |
| `DeleteWorldTheme` | worldThemeId | Supprime e world theme. | — |
| `EditWorldTheme` | worldThemeId, themeName, themeId | Endpoint AMF `EditWorldTheme`. | — |
| `EditWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName | Endpoint AMF `EditWorldThemeAreas`. | — |
| `GetAllWorldThemes` | — | Récupère all world themes. | — |
| `GetOldWorldThemes` | — | Récupère old world themes. | — |
| `GetPresentFutureWorldThemes` | — | Récupère present future world themes. | — |
| `GetWorldThemeAreasByWorldThemeId` | worldThemeId | Récupère world theme areas by world theme id. | — |
| `GetWorldThemeChatRoom` | worldThemeId | Récupère world theme chat room. | — |
| `GetWorldThemeInfo` | — | Récupère world theme info. | — |
| `SaveWorldThemeChatRoomInfo` | worldThemeId, roomName, backgroundFileName, requiredItemType, requiredItemId | Sauvegarde / crée save world theme chat room info. | — |

### Détail endpoints

#### `CreateNewWorldTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | themeName, folderName, themeId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `NewWorldTheme.as` |
| Fonctionnement | Sauvegarde / crée create new world theme. |

#### `CreateNewWorldThemeAreas`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `NewWorldTheme.as` |
| Fonctionnement | Sauvegarde / crée create new world theme areas. |

#### `DeleteWorldTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | worldThemeId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `WorldThemeManager.as` |
| Fonctionnement | Supprime e world theme. |

#### `EditWorldTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | worldThemeId, themeName, themeId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `Admin.as`, `EditWorldTheme.as` |
| Fonctionnement | Endpoint AMF `EditWorldTheme`. |

#### `EditWorldThemeAreas`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `EditWorldTheme.as` |
| Fonctionnement | Endpoint AMF `EditWorldThemeAreas`. |

#### `GetAllWorldThemes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `EditWorldThemeChatRoom.as` |
| Fonctionnement | Récupère all world themes. |

#### `GetOldWorldThemes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `WorldThemeManager.as` |
| Fonctionnement | Récupère old world themes. |

#### `GetPresentFutureWorldThemes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `WorldThemeManager.as` |
| Fonctionnement | Récupère present future world themes. |

#### `GetWorldThemeAreasByWorldThemeId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | worldThemeId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `EditWorldTheme.as` |
| Fonctionnement | Récupère world theme areas by world theme id. |

#### `GetWorldThemeChatRoom`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | worldThemeId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `EditWorldThemeChatRoom.as` |
| Fonctionnement | Récupère world theme chat room. |

#### `GetWorldThemeInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `ChatRoomStageView.as`, `LoginRequiredSetupCommand.as` |
| Fonctionnement | Récupère world theme info. |

#### `SaveWorldThemeChatRoomInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | worldThemeId, roomName, backgroundFileName, requiredItemType, requiredItemId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / appelants | `EditWorldThemeChatRoom.as` |
| Fonctionnement | Sauvegarde / crée save world theme chat room info. |

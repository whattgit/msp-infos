# III.17 — Highscores & themes

> **EN** · [Français](../../fr/amf/17-highscores.md)


Leaderboards, world themes.

## `WebService.Content.AmfContentService`

**AMF path:** `MovieStarPlanet.WebService.Content.AmfContentService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetItemsInCurrentTheme` | ticket, themeId, hash | Fetches items in current theme. | — |
| `GetLastEditedDate` | param1, param2, param3, param4 | Fetches last edited date. | — |

### Endpoint details

#### `GetItemsInCurrentTheme`

| Property | Value |
|----------|-------|
| Parameters | ticket, themeId, hash |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/AMFContentService.as` |
| UI / callers | `ThemeChatRoomUtils.as` |
| Behavior | Fetches items in current theme. |

#### `GetLastEditedDate`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/contentservices/AMFContentService.as` |
| Behavior | Fetches last edited date. |

## `WebService.ExternalApps.AMFExternalAppsService`

**AMF path:** `MovieStarPlanet.WebService.ExternalApps.AMFExternalAppsService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetExternalAppsInCountry` | (_loc2_, "ALL") · (countryCode, "Android") · (countryCode, "IOS") | Fetches external apps in country. | — |

### Endpoint details

#### `GetExternalAppsInCountry`

| Property | Value |
|----------|-------|
| Parameters | (_loc2_, "ALL") · (countryCode, "Android") · (countryCode, "IOS") |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/MobileAdd/MobileAdView.as` (+1) |
| Behavior | Fetches external apps in country. |

## `WebService.Highscore.AMFHighscoreService`

**AMF path:** `MovieStarPlanet.WebService.Highscore.AMFHighscoreService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetHighscoreActor` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Fetches highscore actor. | — |
| `GetHighscoreAnimations` | pageIndex, pageSize | Fetches highscore animations. | — |
| `GetHighscoreBackgrounds` | pageIndex, pageSize | Fetches highscore backgrounds. | — |
| `GetHighscoreBonster` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Fetches highscore bonster. | — |
| `GetHighscoreClothes` | pageIndex, pageSize | Fetches highscore clothes. | — |
| `GetHighscoreItems` | pageIndex, pageSize | Fetches highscore items. | — |
| `GetHighscoreLook` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Fetches highscore look. | — |
| `GetHighscoreMovie` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Fetches highscore movie. | — |
| `GetHighscorePet` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Fetches highscore pet. | — |
| `GetHighscoreScrapBlog` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Fetches highscore scrap blog. | — |
| `GetHighscoreYouTube` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize | Fetches highscore you tube. | — |

### Endpoint details

#### `GetHighscoreActor`

| Property | Value |
|----------|-------|
| Parameters | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreMoviestar.as`, `HighscoreRoom.as` |
| Behavior | Fetches highscore actor. |

#### `GetHighscoreAnimations`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| Behavior | Fetches highscore animations. |

#### `GetHighscoreBackgrounds`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreBackground.as` |
| Behavior | Fetches highscore backgrounds. |

#### `GetHighscoreBonster`

| Property | Value |
|----------|-------|
| Parameters | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreClickItem.as` |
| Behavior | Fetches highscore bonster. |

#### `GetHighscoreClothes`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreCloth.as` |
| Behavior | Fetches highscore clothes. |

#### `GetHighscoreItems`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreCloth.as` |
| Behavior | Fetches highscore items. |

#### `GetHighscoreLook`

| Property | Value |
|----------|-------|
| Parameters | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreLook.as` |
| Behavior | Fetches highscore look. |

#### `GetHighscoreMovie`

| Property | Value |
|----------|-------|
| Parameters | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreMovie.as`, `HighScoreMovieCache.as` |
| Behavior | Fetches highscore movie. |

#### `GetHighscorePet`

| Property | Value |
|----------|-------|
| Parameters | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| Behavior | Fetches highscore pet. |

#### `GetHighscoreScrapBlog`

| Property | Value |
|----------|-------|
| Parameters | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `ArtBookBrowserHelpers.as`, `HighscoreScrapBlog.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches highscore scrap blog. |

#### `GetHighscoreYouTube`

| Property | Value |
|----------|-------|
| Parameters | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/highscore/service/HighscoreAMFService.as` |
| UI / callers | `HighscoreYouTube.as` |
| Behavior | Fetches highscore you tube. |

## `WebService.WorldTheme.AMFWorldThemeService`

**AMF path:** `MovieStarPlanet.WebService.WorldTheme.AMFWorldThemeService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CreateNewWorldTheme` | themeName, folderName, themeId | Saves / creates create new world theme. | — |
| `CreateNewWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName | Saves / creates create new world theme areas. | — |
| `DeleteWorldTheme` | worldThemeId | Deletes e world theme. | — |
| `EditWorldTheme` | worldThemeId, themeName, themeId | AMF endpoint `EditWorldTheme`. | — |
| `EditWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName | AMF endpoint `EditWorldThemeAreas`. | — |
| `GetAllWorldThemes` | — | Fetches all world themes. | — |
| `GetOldWorldThemes` | — | Fetches old world themes. | — |
| `GetPresentFutureWorldThemes` | — | Fetches present future world themes. | — |
| `GetWorldThemeAreasByWorldThemeId` | worldThemeId | Fetches world theme areas by world theme id. | — |
| `GetWorldThemeChatRoom` | worldThemeId | Fetches world theme chat room. | — |
| `GetWorldThemeInfo` | — | Fetches world theme info. | — |
| `SaveWorldThemeChatRoomInfo` | worldThemeId, roomName, backgroundFileName, requiredItemType, requiredItemId | Saves / creates save world theme chat room info. | — |

### Endpoint details

#### `CreateNewWorldTheme`

| Property | Value |
|----------|-------|
| Parameters | themeName, folderName, themeId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `NewWorldTheme.as` |
| Behavior | Saves / creates create new world theme. |

#### `CreateNewWorldThemeAreas`

| Property | Value |
|----------|-------|
| Parameters | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `NewWorldTheme.as` |
| Behavior | Saves / creates create new world theme areas. |

#### `DeleteWorldTheme`

| Property | Value |
|----------|-------|
| Parameters | worldThemeId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `WorldThemeManager.as` |
| Behavior | Deletes e world theme. |

#### `EditWorldTheme`

| Property | Value |
|----------|-------|
| Parameters | worldThemeId, themeName, themeId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `Admin.as`, `EditWorldTheme.as` |
| Behavior | AMF endpoint `EditWorldTheme`. |

#### `EditWorldThemeAreas`

| Property | Value |
|----------|-------|
| Parameters | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `EditWorldTheme.as` |
| Behavior | AMF endpoint `EditWorldThemeAreas`. |

#### `GetAllWorldThemes`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `EditWorldThemeChatRoom.as` |
| Behavior | Fetches all world themes. |

#### `GetOldWorldThemes`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `WorldThemeManager.as` |
| Behavior | Fetches old world themes. |

#### `GetPresentFutureWorldThemes`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `WorldThemeManager.as` |
| Behavior | Fetches present future world themes. |

#### `GetWorldThemeAreasByWorldThemeId`

| Property | Value |
|----------|-------|
| Parameters | worldThemeId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `EditWorldTheme.as` |
| Behavior | Fetches world theme areas by world theme id. |

#### `GetWorldThemeChatRoom`

| Property | Value |
|----------|-------|
| Parameters | worldThemeId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `EditWorldThemeChatRoom.as` |
| Behavior | Fetches world theme chat room. |

#### `GetWorldThemeInfo`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `ChatRoomStageView.as`, `LoginRequiredSetupCommand.as` |
| Behavior | Fetches world theme info. |

#### `SaveWorldThemeChatRoomInfo`

| Property | Value |
|----------|-------|
| Parameters | worldThemeId, roomName, backgroundFileName, requiredItemType, requiredItemId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/worldtheme/WorldThemeService.as` |
| UI / callers | `EditWorldThemeChatRoom.as` |
| Behavior | Saves / creates save world theme chat room info. |

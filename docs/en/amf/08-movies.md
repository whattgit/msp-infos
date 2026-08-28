# III.8 — Movies

> **EN** · [Français](../../fr/amf/08-movies.md)


Movie maker, watch, favourites.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `MovieWatched` | `AMFMovieService` | `awardedFame` | Yes |

## `MobileServices.AMFFavs`

**AMF path:** `MovieStarPlanet.MobileServices.AMFFavs`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AddActorFav` | param1, param2 | AMF endpoint `AddActorFav`. | — |
| `GetActorMovieFavs` | param1, param2 | Fetches actor movie favs. | — |
| `RemoveActorFav` | param1, param2 | Deletes e actor fav. | — |

### Endpoint details

#### `AddActorFav`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| Behavior | AMF endpoint `AddActorFav`. |

#### `GetActorMovieFavs`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| Behavior | Fetches actor movie favs. |

#### `RemoveActorFav`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| Behavior | Deletes e actor fav. |

## `MobileServices.AMFMovieService`

**AMF path:** `MovieStarPlanet.MobileServices.AMFMovieService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CreateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 | Crée un nouveau film avec snapshots initiaux. | — |
| `DeleteMovie` | param1, param2 | Deletes e movie. | — |
| `GetMovie` | movieId | Fetches movie. | — |
| `GetUnifiedMoviesByFriendsStarringMe` | param1, param2 | Fetches unified movies by friends starring me. | — |
| `GetUnifiedMoviesByMePrivate` | param1, param2 | Fetches unified movies by me private. | — |
| `GetUnifiedMoviesLatestByAll` | param1, param2 | Fetches unified movies latest by all. | — |
| `GetUnifiedMoviesLatestByFriends` | param1, param2 | Fetches unified movies latest by friends. | — |
| `GetUnifiedMoviesMinePublic` | param1, param2 | Fetches unified movies mine public. | — |
| `GetUnifiedMoviesTopAll` | param1, param2 | Fetches unified movies top all. | — |
| `GetUnifiedMoviesTopByMeAndFriends` | param1, param2 | Fetches unified movies top by me and friends. | — |
| `MovieWatched` | movieId, actorId, returnType | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit on `awardedFame`. | `-429` |
| `RateMovie` | param1, param2 | Note un film ; peut créditer fame + SC au votant. | — |
| `UpdateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8, param9 | Updates ate movie with snapshot. | — |

### Endpoint details

#### `CreateMovieWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6, param7, param8 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Codes film standard ; fame/SC via champs réponse |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Crée un nouveau film avec snapshots initiaux. |

#### `DeleteMovie`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| UI / callers | `MovieHighScoreComponent.as`, `MovieContentListItemRenderer.as`, `MovieSocialListItemRenderer.as`, `MovieManager.as` (+3) |
| Behavior | Deletes e movie. |

#### `GetMovie`

| Property | Value |
|----------|-------|
| Parameters | movieId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| UI / callers | `MovieCompetitionPublisherItem.as`, `MovieCompetitionOverview.as`, `SubmitMovieToCompetition.as`, `FriendListPopup.as` (+22) |
| Behavior | Fetches movie. |

#### `GetUnifiedMoviesByFriendsStarringMe`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Fetches unified movies by friends starring me. |

#### `GetUnifiedMoviesByMePrivate`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Fetches unified movies by me private. |

#### `GetUnifiedMoviesLatestByAll`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Fetches unified movies latest by all. |

#### `GetUnifiedMoviesLatestByFriends`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Fetches unified movies latest by friends. |

#### `GetUnifiedMoviesMinePublic`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Fetches unified movies mine public. |

#### `GetUnifiedMoviesTopAll`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Fetches unified movies top all. |

#### `GetUnifiedMoviesTopByMeAndFriends`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Fetches unified movies top by me and friends. |

#### `MovieWatched`

| Property | Value |
|----------|-------|
| Parameters | movieId, actorId, returnType |
| AMF ticket | Yes |
| Rate limit | `-429` on `awardedFame` (popup) |
| Return codes | `returnType` 0/1/2 · `awardedFame` −429 rate limit |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| UI / callers | `MovieStudioLogic.as` |
| Behavior | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit on `awardedFame`. |

#### `RateMovie`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Codes film standard ; fame/SC via champs réponse |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| UI / callers | `_com_moviestarplanet_Forms_RateMovieComponentWatcherSetupUtil.as`, `CommentMovieComponent.as`, `MovieReviews.as`, `RateMovieComponent.as` (+5) |
| Behavior | Note un film ; peut créditer fame + SC au votant. |

#### `UpdateMovieWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6, param7, param8, param9 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Behavior | Updates ate movie with snapshot. |

## `WebService.Favourites.AMFFavs`

**AMF path:** `MovieStarPlanet.WebService.Favourites.AMFFavs`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AddActorFav` | actorId, entityType, entityId | AMF endpoint `AddActorFav`. | — |
| `GetActorMovieFavs` | actorId, byRating, pageIndex, pageSize | Fetches actor movie favs. | — |
| `RemoveActorFav` | actorId, entityType, entityId | Deletes e actor fav. | — |

### Endpoint details

#### `AddActorFav`

| Property | Value |
|----------|-------|
| Parameters | actorId, entityType, entityId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/commonservice/FavouritesAMFService.as` (+1) |
| Behavior | AMF endpoint `AddActorFav`. |

#### `GetActorMovieFavs`

| Property | Value |
|----------|-------|
| Parameters | actorId, byRating, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/commonservice/FavouritesAMFService.as` (+1) |
| Behavior | Fetches actor movie favs. |

#### `RemoveActorFav`

| Property | Value |
|----------|-------|
| Parameters | actorId, entityType, entityId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/commonservice/FavouritesAMFService.as` (+1) |
| Behavior | Deletes e actor fav. |

## `WebService.MovieService.AMFMovieService`

**AMF path:** `MovieStarPlanet.WebService.MovieService.AMFMovieService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CommentMovie` | rateMovie | AMF endpoint `CommentMovie`. | — |
| `DeleteMovie` | movieId, actorId | Deletes e movie. | — |
| `DeleteMovieComment` | movieId, commentId | Deletes e movie comment. | — |
| `GetActorMovieCount` | actorId | Fetches actor movie count. | — |
| `GetAutoSavedMovieId` | actorId | Fetches auto saved movie id. | — |
| `GetMovieByGuid` | movieGuid | Fetches movie by guid. | — |
| `GetMovieById` | movieId | Fetches movie by id. | — |
| `GetMovieListForActor` | pagingOptions.params.actorId, pagingOptions.params.type, pagingOptions.pageIndex, pagingOptions.pageSize | Fetches movie list for actor. | — |
| `GetMovieRatings` | movie.MovieId, pageIndex, pageSize | Fetches movie ratings. | — |
| `MovieWatched` | movieId, actorId, returnType | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit on `awardedFame`. | `-429` |
| `PublishMovie` | movieId | AMF endpoint `PublishMovie`. | — |
| `RateMovie` | rateMovie | Note un film ; peut créditer fame + SC au votant. | — |
| `SaveMovieWithSnapshot` | movie, snapshotSmall, snapshotBig | Sauvegarde film + snapshots ; `movieId==-1` = échec quota/validation. | — |
| `SearchMovie` | searchString, pageIndex, pageSize | Searches movie. | — |
| `SendMovieAsMail` | movieId, toAddress | AMF endpoint `SendMovieAsMail`. | — |

### Endpoint details

#### `CommentMovie`

| Property | Value |
|----------|-------|
| Parameters | rateMovie |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `_com_moviestarplanet_Forms_CommentMovieComponentWatcherSetupUtil.as`, `CommentMovieComponent.as`, `MovieReviews.as`, `QuestEvent.as` |
| Behavior | AMF endpoint `CommentMovie`. |

#### `DeleteMovie`

| Property | Value |
|----------|-------|
| Parameters | movieId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` (+1) |
| UI / callers | `MovieHighScoreComponent.as`, `MovieContentListItemRenderer.as`, `MovieSocialListItemRenderer.as`, `MovieManager.as` (+3) |
| Behavior | Deletes e movie. |

#### `DeleteMovieComment`

| Property | Value |
|----------|-------|
| Parameters | movieId, commentId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `MovieCommentDataItem.as` |
| Behavior | Deletes e movie comment. |

#### `GetActorMovieCount`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `MovieDetailsLogic.as` |
| Behavior | Fetches actor movie count. |

#### `GetAutoSavedMovieId`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `ContinueSettingUpCommand.as` |
| Behavior | Fetches auto saved movie id. |

#### `GetMovieByGuid`

| Property | Value |
|----------|-------|
| Parameters | movieGuid |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `MovieStudioLogic.as` |
| Behavior | Fetches movie by guid. |

#### `GetMovieById`

| Property | Value |
|----------|-------|
| Parameters | movieId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `SubmitMovieToCompetition.as`, `MovieSocialListItemRenderer.as`, `FavoriteMovieCache.as`, `HighScoreMovieCache.as` (+3) |
| Behavior | Fetches movie by id. |

#### `GetMovieListForActor`

| Property | Value |
|----------|-------|
| Parameters | pagingOptions.params.actorId, pagingOptions.params.type, pagingOptions.pageIndex, pagingOptions.pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `SubmitMovieToCompetition.as`, `PersonalContentList.as`, `Pager.as`, `MovieBrowserHelpers.as` (+2) |
| Behavior | Fetches movie list for actor. |

#### `GetMovieRatings`

| Property | Value |
|----------|-------|
| Parameters | movie.MovieId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `MovieReviews.as` |
| Behavior | Fetches movie ratings. |

#### `MovieWatched`

| Property | Value |
|----------|-------|
| Parameters | movieId, actorId, returnType |
| AMF ticket | Yes |
| Rate limit | `-429` on `awardedFame` (popup) |
| Return codes | `returnType` 0/1/2 · `awardedFame` −429 rate limit |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` (+1) |
| UI / callers | `MovieStudioLogic.as` |
| Behavior | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit on `awardedFame`. |

#### `PublishMovie`

| Property | Value |
|----------|-------|
| Parameters | movieId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Codes film standard ; fame/SC via champs réponse |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `SubmitMovieToCompetition.as`, `MovieDetailsLogic.as` |
| Behavior | AMF endpoint `PublishMovie`. |

#### `RateMovie`

| Property | Value |
|----------|-------|
| Parameters | rateMovie |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Codes film standard ; fame/SC via champs réponse |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` (+1) |
| UI / callers | `_com_moviestarplanet_Forms_RateMovieComponentWatcherSetupUtil.as`, `CommentMovieComponent.as`, `MovieReviews.as`, `RateMovieComponent.as` (+5) |
| Behavior | Note un film ; peut créditer fame + SC au votant. |

#### `SaveMovieWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | movie, snapshotSmall, snapshotBig |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Codes film standard ; fame/SC via champs réponse |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `MovieDetailsLogic.as`, `MovieStudioLogic.as` |
| Behavior | Sauvegarde film + snapshots ; `movieId==-1` = échec quota/validation. |

#### `SearchMovie`

| Property | Value |
|----------|-------|
| Parameters | searchString, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / callers | `MovieBrowserView.as` |
| Behavior | Searches movie. |

#### `SendMovieAsMail`

| Property | Value |
|----------|-------|
| Parameters | movieId, toAddress |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| Behavior | AMF endpoint `SendMovieAsMail`. |

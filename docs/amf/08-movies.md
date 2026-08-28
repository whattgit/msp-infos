# V.8 — Films

Movie maker, visionnage, favoris.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `MovieWatched` | `AMFMovieService` | `awardedFame` | Oui |

## `MobileServices.AMFFavs`

**Chemin AMF :** `MovieStarPlanet.MobileServices.AMFFavs`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AddActorFav` | param1, param2 | Endpoint AMF `AddActorFav`. | — |
| `GetActorMovieFavs` | param1, param2 | Récupère actor movie favs. | — |
| `RemoveActorFav` | param1, param2 | Supprime e actor fav. | — |

### Détail endpoints

#### `AddActorFav`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| Fonctionnement | Endpoint AMF `AddActorFav`. |

#### `GetActorMovieFavs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| Fonctionnement | Récupère actor movie favs. |

#### `RemoveActorFav`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| Fonctionnement | Supprime e actor fav. |

## `MobileServices.AMFMovieService`

**Chemin AMF :** `MovieStarPlanet.MobileServices.AMFMovieService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CreateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 | Crée un nouveau film avec snapshots initiaux. | — |
| `DeleteMovie` | param1, param2 | Supprime e movie. | — |
| `GetMovie` | movieId | Récupère movie. | — |
| `GetUnifiedMoviesByFriendsStarringMe` | param1, param2 | Récupère unified movies by friends starring me. | — |
| `GetUnifiedMoviesByMePrivate` | param1, param2 | Récupère unified movies by me private. | — |
| `GetUnifiedMoviesLatestByAll` | param1, param2 | Récupère unified movies latest by all. | — |
| `GetUnifiedMoviesLatestByFriends` | param1, param2 | Récupère unified movies latest by friends. | — |
| `GetUnifiedMoviesMinePublic` | param1, param2 | Récupère unified movies mine public. | — |
| `GetUnifiedMoviesTopAll` | param1, param2 | Récupère unified movies top all. | — |
| `GetUnifiedMoviesTopByMeAndFriends` | param1, param2 | Récupère unified movies top by me and friends. | — |
| `MovieWatched` | movieId, actorId, returnType | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit sur `awardedFame`. | `-429` |
| `RateMovie` | param1, param2 | Note un film ; peut créditer fame + SC au votant. | — |
| `UpdateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8, param9 | Met à jour ate movie with snapshot. | — |

### Détail endpoints

#### `CreateMovieWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6, param7, param8 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Codes film standard ; fame/SC via champs réponse |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Crée un nouveau film avec snapshots initiaux. |

#### `DeleteMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| UI / appelants | `MovieHighScoreComponent.as`, `MovieContentListItemRenderer.as`, `MovieSocialListItemRenderer.as`, `MovieManager.as` (+3) |
| Fonctionnement | Supprime e movie. |

#### `GetMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| UI / appelants | `MovieCompetitionPublisherItem.as`, `MovieCompetitionOverview.as`, `SubmitMovieToCompetition.as`, `FriendListPopup.as` (+22) |
| Fonctionnement | Récupère movie. |

#### `GetUnifiedMoviesByFriendsStarringMe`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Récupère unified movies by friends starring me. |

#### `GetUnifiedMoviesByMePrivate`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Récupère unified movies by me private. |

#### `GetUnifiedMoviesLatestByAll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Récupère unified movies latest by all. |

#### `GetUnifiedMoviesLatestByFriends`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Récupère unified movies latest by friends. |

#### `GetUnifiedMoviesMinePublic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Récupère unified movies mine public. |

#### `GetUnifiedMoviesTopAll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Récupère unified movies top all. |

#### `GetUnifiedMoviesTopByMeAndFriends`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Récupère unified movies top by me and friends. |

#### `MovieWatched`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId, actorId, returnType |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `awardedFame` (popup) |
| Codes retour | `returnType` 0/1/2 · `awardedFame` −429 rate limit |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| UI / appelants | `MovieStudioLogic.as` |
| Fonctionnement | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit sur `awardedFame`. |

#### `RateMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Codes film standard ; fame/SC via champs réponse |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` (+1) |
| UI / appelants | `_com_moviestarplanet_Forms_RateMovieComponentWatcherSetupUtil.as`, `CommentMovieComponent.as`, `MovieReviews.as`, `RateMovieComponent.as` (+5) |
| Fonctionnement | Note un film ; peut créditer fame + SC au votant. |

#### `UpdateMovieWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6, param7, param8, param9 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieMobileAMFService.as` |
| Fonctionnement | Met à jour ate movie with snapshot. |

## `WebService.Favourites.AMFFavs`

**Chemin AMF :** `MovieStarPlanet.WebService.Favourites.AMFFavs`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AddActorFav` | actorId, entityType, entityId | Endpoint AMF `AddActorFav`. | — |
| `GetActorMovieFavs` | actorId, byRating, pageIndex, pageSize | Récupère actor movie favs. | — |
| `RemoveActorFav` | actorId, entityType, entityId | Supprime e actor fav. | — |

### Détail endpoints

#### `AddActorFav`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, entityType, entityId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/commonservice/FavouritesAMFService.as` (+1) |
| Fonctionnement | Endpoint AMF `AddActorFav`. |

#### `GetActorMovieFavs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, byRating, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/commonservice/FavouritesAMFService.as` (+1) |
| Fonctionnement | Récupère actor movie favs. |

#### `RemoveActorFav`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, entityType, entityId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/commonservice/FavouritesAMFService.as` (+1) |
| Fonctionnement | Supprime e actor fav. |

## `WebService.MovieService.AMFMovieService`

**Chemin AMF :** `MovieStarPlanet.WebService.MovieService.AMFMovieService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CommentMovie` | rateMovie | Endpoint AMF `CommentMovie`. | — |
| `DeleteMovie` | movieId, actorId | Supprime e movie. | — |
| `DeleteMovieComment` | movieId, commentId | Supprime e movie comment. | — |
| `GetActorMovieCount` | actorId | Récupère actor movie count. | — |
| `GetAutoSavedMovieId` | actorId | Récupère auto saved movie id. | — |
| `GetMovieByGuid` | movieGuid | Récupère movie by guid. | — |
| `GetMovieById` | movieId | Récupère movie by id. | — |
| `GetMovieListForActor` | pagingOptions.params.actorId, pagingOptions.params.type, pagingOptions.pageIndex, pagingOptions.pageSize | Récupère movie list for actor. | — |
| `GetMovieRatings` | movie.MovieId, pageIndex, pageSize | Récupère movie ratings. | — |
| `MovieWatched` | movieId, actorId, returnType | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit sur `awardedFame`. | `-429` |
| `PublishMovie` | movieId | Endpoint AMF `PublishMovie`. | — |
| `RateMovie` | rateMovie | Note un film ; peut créditer fame + SC au votant. | — |
| `SaveMovieWithSnapshot` | movie, snapshotSmall, snapshotBig | Sauvegarde film + snapshots ; `movieId==-1` = échec quota/validation. | — |
| `SearchMovie` | searchString, pageIndex, pageSize | Recherche movie. | — |
| `SendMovieAsMail` | movieId, toAddress | Endpoint AMF `SendMovieAsMail`. | — |

### Détail endpoints

#### `CommentMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | rateMovie |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `_com_moviestarplanet_Forms_CommentMovieComponentWatcherSetupUtil.as`, `CommentMovieComponent.as`, `MovieReviews.as`, `QuestEvent.as` |
| Fonctionnement | Endpoint AMF `CommentMovie`. |

#### `DeleteMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` (+1) |
| UI / appelants | `MovieHighScoreComponent.as`, `MovieContentListItemRenderer.as`, `MovieSocialListItemRenderer.as`, `MovieManager.as` (+3) |
| Fonctionnement | Supprime e movie. |

#### `DeleteMovieComment`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId, commentId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `MovieCommentDataItem.as` |
| Fonctionnement | Supprime e movie comment. |

#### `GetActorMovieCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `MovieDetailsLogic.as` |
| Fonctionnement | Récupère actor movie count. |

#### `GetAutoSavedMovieId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `ContinueSettingUpCommand.as` |
| Fonctionnement | Récupère auto saved movie id. |

#### `GetMovieByGuid`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieGuid |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `MovieStudioLogic.as` |
| Fonctionnement | Récupère movie by guid. |

#### `GetMovieById`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `SubmitMovieToCompetition.as`, `MovieSocialListItemRenderer.as`, `FavoriteMovieCache.as`, `HighScoreMovieCache.as` (+3) |
| Fonctionnement | Récupère movie by id. |

#### `GetMovieListForActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pagingOptions.params.actorId, pagingOptions.params.type, pagingOptions.pageIndex, pagingOptions.pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `SubmitMovieToCompetition.as`, `PersonalContentList.as`, `Pager.as`, `MovieBrowserHelpers.as` (+2) |
| Fonctionnement | Récupère movie list for actor. |

#### `GetMovieRatings`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movie.MovieId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `MovieReviews.as` |
| Fonctionnement | Récupère movie ratings. |

#### `MovieWatched`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId, actorId, returnType |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `awardedFame` (popup) |
| Codes retour | `returnType` 0/1/2 · `awardedFame` −429 rate limit |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` (+1) |
| UI / appelants | `MovieStudioLogic.as` |
| Fonctionnement | Crédite fame après visionnage ; `returnType` 0/1/2 ; rate limit sur `awardedFame`. |

#### `PublishMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Codes film standard ; fame/SC via champs réponse |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `SubmitMovieToCompetition.as`, `MovieDetailsLogic.as` |
| Fonctionnement | Endpoint AMF `PublishMovie`. |

#### `RateMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | rateMovie |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Codes film standard ; fame/SC via champs réponse |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` (+1) |
| UI / appelants | `_com_moviestarplanet_Forms_RateMovieComponentWatcherSetupUtil.as`, `CommentMovieComponent.as`, `MovieReviews.as`, `RateMovieComponent.as` (+5) |
| Fonctionnement | Note un film ; peut créditer fame + SC au votant. |

#### `SaveMovieWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movie, snapshotSmall, snapshotBig |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Codes film standard ; fame/SC via champs réponse |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `MovieDetailsLogic.as`, `MovieStudioLogic.as` |
| Fonctionnement | Sauvegarde film + snapshots ; `movieId==-1` = échec quota/validation. |

#### `SearchMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | searchString, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| UI / appelants | `MovieBrowserView.as` |
| Fonctionnement | Recherche movie. |

#### `SendMovieAsMail`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieId, toAddress |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/movie/service/MovieAMFService.as` |
| Fonctionnement | Endpoint AMF `SendMovieAsMail`. |

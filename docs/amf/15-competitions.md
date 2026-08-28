# V.15 — Compétitions

Compétitions film et quotidienne.

## `WebService.Competition.AMFCompetitionService`

**Chemin AMF :** `MovieStarPlanet.WebService.Competition.AMFCompetitionService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetMovieCompetition` | id | Récupère movie competition. | — |
| `GetMovieCompetitionList` | params[0 | Récupère movie competition list. | — |
| `GetMovieCompetitionListById` | params[0 | Récupère movie competition list by id. | — |
| `GetMovieCompetitionListByNewsId` | newsId | Récupère movie competition list by news id. | — |
| `GetNewsById` | param1, param2, param3 | Récupère news by id. | — |
| `GetParticipatingLooks` | competitionId, params.moderatormode, pageIndex, pageSize | Récupère participating looks. | — |
| `GetParticipatingMovies` | competitionId, params.moderatormode, pageIndex, pageSize | Récupère participating movies. | — |
| `GetParticipatingRooms` | competitionId, params.moderatormode, pageIndex, pageSize | Récupère participating rooms. | — |
| `GetParticipatingScrapBlogs` | competitionId, params.moderatormode, pageIndex, pageSize | Récupère participating scrap blogs. | — |
| `GetSubmittedMovieCompetitionLook` | movieCompetitionId, actorId | Récupère submitted movie competition look. | — |
| `GetSubmittedMovieCompetitionMovie` | movieCompetitionId, actorId | Récupère submitted movie competition movie. | — |
| `GetSubmittedMovieCompetitionRoom` | movieCompetitionId, actorId | Récupère submitted movie competition room. | — |
| `GetSubmittedScrapBlog` | competitionId, actorId | Récupère submitted scrap blog. | — |
| `HasActorVotedInCompetition` | movieCompetitionId, actorId | Endpoint AMF `HasActorVotedInCompetition`. | — |
| `LinkCompetitionToTheme` | newsId, themeId | Endpoint AMF `LinkCompetitionToTheme`. | — |
| `MovieCompetitionPublish` | param1, param2, param3 | Endpoint AMF `MovieCompetitionPublish`. | — |
| `SaveMovieCompetition` | competition, awardPrizes | Sauvegarde / crée save movie competition. | — |
| `SubmitEntityToCompetition` | movieCompetitionId, entityId, actorId | Endpoint AMF `SubmitEntityToCompetition`. | — |
| `VoteInMovieCompetition` | movieCompetitionId, movieId, actorId | Endpoint AMF `VoteInMovieCompetition`. | — |

### Détail endpoints

#### `GetMovieCompetition`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | id |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `MovieCompetitionPublisherItem.as`, `MovieCompetitionOverview.as`, `ChatRoomTypeLobby.as` |
| Fonctionnement | Récupère movie competition. |

#### `GetMovieCompetitionList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params[0 |
| Ticket AMF | — |
| Rate limit | — |
| Codes retour | — |
| Fonctionnement | Récupère movie competition list. |

#### `GetMovieCompetitionListById`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params[0 |
| Ticket AMF | — |
| Rate limit | — |
| Codes retour | — |
| Fonctionnement | Récupère movie competition list by id. |

#### `GetMovieCompetitionListByNewsId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | newsId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `MovieCompetitionPublisherItem.as`, `MovieCompetitionOverview.as` |
| Fonctionnement | Récupère movie competition list by news id. |

#### `GetNewsById`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` (+1) |
| UI / appelants | `MovieCompetitionNew.as`, `MovieCompetitionOverview.as` |
| Fonctionnement | Récupère news by id. |

#### `GetParticipatingLooks`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | competitionId, params.moderatormode, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `ParticipatingMovies.as` |
| Fonctionnement | Récupère participating looks. |

#### `GetParticipatingMovies`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | competitionId, params.moderatormode, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `ParticipatingMovies.as` |
| Fonctionnement | Récupère participating movies. |

#### `GetParticipatingRooms`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | competitionId, params.moderatormode, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `ParticipatingMovies.as` |
| Fonctionnement | Récupère participating rooms. |

#### `GetParticipatingScrapBlogs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | competitionId, params.moderatormode, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `ParticipatingMovies.as` |
| Fonctionnement | Récupère participating scrap blogs. |

#### `GetSubmittedMovieCompetitionLook`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieCompetitionId, actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `SubmittedEntities.as` |
| Fonctionnement | Récupère submitted movie competition look. |

#### `GetSubmittedMovieCompetitionMovie`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieCompetitionId, actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `SubmittedEntities.as` |
| Fonctionnement | Récupère submitted movie competition movie. |

#### `GetSubmittedMovieCompetitionRoom`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieCompetitionId, actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `SubmittedEntities.as` |
| Fonctionnement | Récupère submitted movie competition room. |

#### `GetSubmittedScrapBlog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | competitionId, actorId |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `SubmittedEntities.as` |
| Fonctionnement | Récupère submitted scrap blog. |

#### `HasActorVotedInCompetition`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieCompetitionId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `MovieCompetitionOverview.as`, `ParticipatingMovies.as` |
| Fonctionnement | Endpoint AMF `HasActorVotedInCompetition`. |

#### `LinkCompetitionToTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | newsId, themeId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `MovieCompetitionOverview.as` |
| Fonctionnement | Endpoint AMF `LinkCompetitionToTheme`. |

#### `MovieCompetitionPublish`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `MovieCompetitionPublisherItem.as`, `AdminManager.as` |
| Fonctionnement | Endpoint AMF `MovieCompetitionPublish`. |

#### `SaveMovieCompetition`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | competition, awardPrizes |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `MovieCompetitionNew.as`, `MovieCompetitionOverview.as`, `ParticipatingMovies.as` |
| Fonctionnement | Sauvegarde / crée save movie competition. |

#### `SubmitEntityToCompetition`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieCompetitionId, entityId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `SubmitLookToCompetition.as`, `SubmitMovieToCompetition.as`, `SubmittedEntities.as`, `MyRoomEntitiesView.as` (+1) |
| Fonctionnement | Endpoint AMF `SubmitEntityToCompetition`. |

#### `VoteInMovieCompetition`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | movieCompetitionId, movieId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / appelants | `ParticipatingEntityListItem.as` |
| Fonctionnement | Endpoint AMF `VoteInMovieCompetition`. |

## `WebService.DailyCompetition.AMFDailyCompetitionService`

**Chemin AMF :** `MovieStarPlanet.WebService.DailyCompetition.AMFDailyCompetitionService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `IncrementSubmissionResets` | — | Endpoint AMF `IncrementSubmissionResets`. | — |
| `addToComp` | param2, param3, param4 | Endpoint AMF `addToComp`. | — |
| `canSubmit` | param2, param3 | Endpoint AMF `canSubmit`. | — |
| `getRandomItem` | param2 | Endpoint AMF `getRandomItem`. | — |
| `getTodaysTheme` | — | Endpoint AMF `getTodaysTheme`. | — |
| `getVoteScore` | param2 | Endpoint AMF `getVoteScore`. | — |
| `voteFor` | param2, param3, param4, param5, param6 | Endpoint AMF `voteFor`. | — |

### Détail endpoints

#### `IncrementSubmissionResets`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / appelants | `DailyCompetitionVoteController.as` |
| Fonctionnement | Endpoint AMF `IncrementSubmissionResets`. |

#### `addToComp`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / appelants | `SubmitToCompetitionPopup.as` |
| Fonctionnement | Endpoint AMF `addToComp`. |

#### `canSubmit`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param3 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / appelants | `CreateAndRatePopup.as`, `DailyCompetitionThemeIndicator.as`, `DailyCompetitionVoteController.as` |
| Fonctionnement | Endpoint AMF `canSubmit`. |

#### `getRandomItem`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / appelants | `DailyCompetition.as` |
| Fonctionnement | Endpoint AMF `getRandomItem`. |

#### `getTodaysTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / appelants | `Countdown.as`, `CreateAndRatePopup.as`, `DailyCompetitionThemeIndicator.as`, `SubmitToCompetitionPopup.as` |
| Fonctionnement | Endpoint AMF `getTodaysTheme`. |

#### `getVoteScore`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / appelants | `DailyCompetition.as`, `DailyCompetitionVoteController.as`, `LevelBar.as` |
| Fonctionnement | Endpoint AMF `getVoteScore`. |

#### `voteFor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / appelants | `VoteMiniGame.as`, `WordRelationMinigame.as`, `DesignBattle.as`, `VoteFrame.as` |
| Fonctionnement | Endpoint AMF `voteFor`. |

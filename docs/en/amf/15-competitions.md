# III.15 — Competitions

> **EN** · [Français](../../fr/amf/15-competitions.md)


Competitions film et quotidienne.

## `WebService.Competition.AMFCompetitionService`

**AMF path:** `MovieStarPlanet.WebService.Competition.AMFCompetitionService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetMovieCompetition` | id | Fetches movie competition. | — |
| `GetMovieCompetitionList` | params[0 | Fetches movie competition list. | — |
| `GetMovieCompetitionListById` | params[0 | Fetches movie competition list by id. | — |
| `GetMovieCompetitionListByNewsId` | newsId | Fetches movie competition list by news id. | — |
| `GetNewsById` | param1, param2, param3 | Fetches news by id. | — |
| `GetParticipatingLooks` | competitionId, params.moderatormode, pageIndex, pageSize | Fetches participating looks. | — |
| `GetParticipatingMovies` | competitionId, params.moderatormode, pageIndex, pageSize | Fetches participating movies. | — |
| `GetParticipatingRooms` | competitionId, params.moderatormode, pageIndex, pageSize | Fetches participating rooms. | — |
| `GetParticipatingScrapBlogs` | competitionId, params.moderatormode, pageIndex, pageSize | Fetches participating scrap blogs. | — |
| `GetSubmittedMovieCompetitionLook` | movieCompetitionId, actorId | Fetches submitted movie competition look. | — |
| `GetSubmittedMovieCompetitionMovie` | movieCompetitionId, actorId | Fetches submitted movie competition movie. | — |
| `GetSubmittedMovieCompetitionRoom` | movieCompetitionId, actorId | Fetches submitted movie competition room. | — |
| `GetSubmittedScrapBlog` | competitionId, actorId | Fetches submitted scrap blog. | — |
| `HasActorVotedInCompetition` | movieCompetitionId, actorId | AMF endpoint `HasActorVotedInCompetition`. | — |
| `LinkCompetitionToTheme` | newsId, themeId | AMF endpoint `LinkCompetitionToTheme`. | — |
| `MovieCompetitionPublish` | param1, param2, param3 | AMF endpoint `MovieCompetitionPublish`. | — |
| `SaveMovieCompetition` | competition, awardPrizes | Saves / creates save movie competition. | — |
| `SubmitEntityToCompetition` | movieCompetitionId, entityId, actorId | AMF endpoint `SubmitEntityToCompetition`. | — |
| `VoteInMovieCompetition` | movieCompetitionId, movieId, actorId | AMF endpoint `VoteInMovieCompetition`. | — |

### Endpoint details

#### `GetMovieCompetition`

| Property | Value |
|----------|-------|
| Parameters | id |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `MovieCompetitionPublisherItem.as`, `MovieCompetitionOverview.as`, `ChatRoomTypeLobby.as` |
| Behavior | Fetches movie competition. |

#### `GetMovieCompetitionList`

| Property | Value |
|----------|-------|
| Parameters | params[0 |
| AMF ticket | — |
| Rate limit | — |
| Return codes | — |
| Behavior | Fetches movie competition list. |

#### `GetMovieCompetitionListById`

| Property | Value |
|----------|-------|
| Parameters | params[0 |
| AMF ticket | — |
| Rate limit | — |
| Return codes | — |
| Behavior | Fetches movie competition list by id. |

#### `GetMovieCompetitionListByNewsId`

| Property | Value |
|----------|-------|
| Parameters | newsId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `MovieCompetitionPublisherItem.as`, `MovieCompetitionOverview.as` |
| Behavior | Fetches movie competition list by news id. |

#### `GetNewsById`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` (+1) |
| UI / callers | `MovieCompetitionNew.as`, `MovieCompetitionOverview.as` |
| Behavior | Fetches news by id. |

#### `GetParticipatingLooks`

| Property | Value |
|----------|-------|
| Parameters | competitionId, params.moderatormode, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `ParticipatingMovies.as` |
| Behavior | Fetches participating looks. |

#### `GetParticipatingMovies`

| Property | Value |
|----------|-------|
| Parameters | competitionId, params.moderatormode, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `ParticipatingMovies.as` |
| Behavior | Fetches participating movies. |

#### `GetParticipatingRooms`

| Property | Value |
|----------|-------|
| Parameters | competitionId, params.moderatormode, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `ParticipatingMovies.as` |
| Behavior | Fetches participating rooms. |

#### `GetParticipatingScrapBlogs`

| Property | Value |
|----------|-------|
| Parameters | competitionId, params.moderatormode, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `ParticipatingMovies.as` |
| Behavior | Fetches participating scrap blogs. |

#### `GetSubmittedMovieCompetitionLook`

| Property | Value |
|----------|-------|
| Parameters | movieCompetitionId, actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `SubmittedEntities.as` |
| Behavior | Fetches submitted movie competition look. |

#### `GetSubmittedMovieCompetitionMovie`

| Property | Value |
|----------|-------|
| Parameters | movieCompetitionId, actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `SubmittedEntities.as` |
| Behavior | Fetches submitted movie competition movie. |

#### `GetSubmittedMovieCompetitionRoom`

| Property | Value |
|----------|-------|
| Parameters | movieCompetitionId, actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `SubmittedEntities.as` |
| Behavior | Fetches submitted movie competition room. |

#### `GetSubmittedScrapBlog`

| Property | Value |
|----------|-------|
| Parameters | competitionId, actorId |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `SubmittedEntities.as` |
| Behavior | Fetches submitted scrap blog. |

#### `HasActorVotedInCompetition`

| Property | Value |
|----------|-------|
| Parameters | movieCompetitionId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `MovieCompetitionOverview.as`, `ParticipatingMovies.as` |
| Behavior | AMF endpoint `HasActorVotedInCompetition`. |

#### `LinkCompetitionToTheme`

| Property | Value |
|----------|-------|
| Parameters | newsId, themeId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `MovieCompetitionOverview.as` |
| Behavior | AMF endpoint `LinkCompetitionToTheme`. |

#### `MovieCompetitionPublish`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `MovieCompetitionPublisherItem.as`, `AdminManager.as` |
| Behavior | AMF endpoint `MovieCompetitionPublish`. |

#### `SaveMovieCompetition`

| Property | Value |
|----------|-------|
| Parameters | competition, awardPrizes |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `MovieCompetitionNew.as`, `MovieCompetitionOverview.as`, `ParticipatingMovies.as` |
| Behavior | Saves / creates save movie competition. |

#### `SubmitEntityToCompetition`

| Property | Value |
|----------|-------|
| Parameters | movieCompetitionId, entityId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `SubmitLookToCompetition.as`, `SubmitMovieToCompetition.as`, `SubmittedEntities.as`, `MyRoomEntitiesView.as` (+1) |
| Behavior | AMF endpoint `SubmitEntityToCompetition`. |

#### `VoteInMovieCompetition`

| Property | Value |
|----------|-------|
| Parameters | movieCompetitionId, movieId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/competition/service/CompetitionAMFService.as` |
| UI / callers | `ParticipatingEntityListItem.as` |
| Behavior | AMF endpoint `VoteInMovieCompetition`. |

## `WebService.DailyCompetition.AMFDailyCompetitionService`

**AMF path:** `MovieStarPlanet.WebService.DailyCompetition.AMFDailyCompetitionService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `IncrementSubmissionResets` | — | AMF endpoint `IncrementSubmissionResets`. | — |
| `addToComp` | param2, param3, param4 | AMF endpoint `addToComp`. | — |
| `canSubmit` | param2, param3 | AMF endpoint `canSubmit`. | — |
| `getRandomItem` | param2 | AMF endpoint `getRandomItem`. | — |
| `getTodaysTheme` | — | AMF endpoint `getTodaysTheme`. | — |
| `getVoteScore` | param2 | AMF endpoint `getVoteScore`. | — |
| `voteFor` | param2, param3, param4, param5, param6 | AMF endpoint `voteFor`. | — |

### Endpoint details

#### `IncrementSubmissionResets`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / callers | `DailyCompetitionVoteController.as` |
| Behavior | AMF endpoint `IncrementSubmissionResets`. |

#### `addToComp`

| Property | Value |
|----------|-------|
| Parameters | param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / callers | `SubmitToCompetitionPopup.as` |
| Behavior | AMF endpoint `addToComp`. |

#### `canSubmit`

| Property | Value |
|----------|-------|
| Parameters | param2, param3 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / callers | `CreateAndRatePopup.as`, `DailyCompetitionThemeIndicator.as`, `DailyCompetitionVoteController.as` |
| Behavior | AMF endpoint `canSubmit`. |

#### `getRandomItem`

| Property | Value |
|----------|-------|
| Parameters | param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / callers | `DailyCompetition.as` |
| Behavior | AMF endpoint `getRandomItem`. |

#### `getTodaysTheme`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / callers | `Countdown.as`, `CreateAndRatePopup.as`, `DailyCompetitionThemeIndicator.as`, `SubmitToCompetitionPopup.as` |
| Behavior | AMF endpoint `getTodaysTheme`. |

#### `getVoteScore`

| Property | Value |
|----------|-------|
| Parameters | param2 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / callers | `DailyCompetition.as`, `DailyCompetitionVoteController.as`, `LevelBar.as` |
| Behavior | AMF endpoint `getVoteScore`. |

#### `voteFor`

| Property | Value |
|----------|-------|
| Parameters | param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/dailyCompetition/service/DailyCompetitionAmfService.as` |
| UI / callers | `VoteMiniGame.as`, `WordRelationMinigame.as`, `DesignBattle.as`, `VoteFrame.as` |
| Behavior | AMF endpoint `voteFor`. |

# V.16 — Forum, news & activités

Forums, sondages, notifications, fil activité.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `ClaimBonus2` | `AMFNotificationCenterService` | `ErrorCode` | Oui |

## Codes de réponse

| Code | Signification |
|------|---------------|
| `0` | Topic/post créé |
| `1` | Erreur |
| `2` | Chaîne interdite (modération) |

## `Polls.AMFPollService`

**Chemin AMF :** `MovieStarPlanet.Polls.AMFPollService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetPoll` | pollId, actorId | Récupère poll. | — |
| `GetPollLatest` | actorId | Récupère poll latest. | — |
| `GetPolls` | pageindex, pagesize | Récupère polls. | — |
| `GetPollsUnused` | — | Récupère polls unused. | — |
| `LinkPolls` | pollId, nextPollId | Endpoint AMF `LinkPolls`. | — |
| `NewPoll` | question, answer1, answer2, answer3, answer4 | Endpoint AMF `NewPoll`. | — |
| `NewPollPublish` | pollId, locale, siteDomain | Endpoint AMF `NewPollPublish`. | — |
| `VotePoll` | pollId, actorId, answer | Endpoint AMF `VotePoll`. | — |

### Détail endpoints

#### `GetPoll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pollId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollEditor.as`, `PollCtrls.as` |
| Fonctionnement | Récupère poll. |

#### `GetPollLatest`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollCtrls.as` |
| Fonctionnement | Récupère poll latest. |

#### `GetPolls`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageindex, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollEditor.as` |
| Fonctionnement | Récupère polls. |

#### `GetPollsUnused`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollEditor.as` |
| Fonctionnement | Récupère polls unused. |

#### `LinkPolls`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pollId, nextPollId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollEditor.as` |
| Fonctionnement | Endpoint AMF `LinkPolls`. |

#### `NewPoll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | question, answer1, answer2, answer3, answer4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollEditor.as`, `PollEditorItem.as`, `NewTopic.as` |
| Fonctionnement | Endpoint AMF `NewPoll`. |

#### `NewPollPublish`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pollId, locale, siteDomain |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollEditorItem.as` |
| Fonctionnement | Endpoint AMF `NewPollPublish`. |

#### `VotePoll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pollId, actorId, answer |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / appelants | `PollCtrls.as` |
| Fonctionnement | Endpoint AMF `VotePoll`. |

## `WebService.Campaign.AMFCampaignService`

**Chemin AMF :** `MovieStarPlanet.WebService.Campaign.AMFCampaignService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `UseCampaign` | param1, param2 | Endpoint AMF `UseCampaign`. | — |

### Détail endpoints

#### `UseCampaign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/campaign/CampaignAmfService.as` |
| UI / appelants | `CampaignHandlerBase.as` |
| Fonctionnement | Endpoint AMF `UseCampaign`. |

## `WebService.Forums.AMFForumService`

**Chemin AMF :** `MovieStarPlanet.WebService.Forums.AMFForumService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AdminCreateTopic` | actorName, actorPassword, forumId, subject, type, message, colorCode, subjectChatLogId, messageChatLogId | Endpoint AMF `AdminCreateTopic`. | — |
| `AdminCreateTopicPoll` | actorId, forumId, filteredQuestion, filteredAnsers, topicType, adminUserName, adminPassword, -1 | Endpoint AMF `AdminCreateTopicPoll`. | — |
| `CheckAllowedCreateTopic` | actorId | Vérifie allowed create topic. | — |
| `CreatePostWithModerationCall` | actorId, actorName, topicId, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() | Sauvegarde / crée create post with moderation call. | — |
| `CreateTopicPollWithModerationCall` | actorId, actorName, forumId, pollQuestion, pollAnswers, TextModerationHandler.getInstance().isRestrictedUser() | Sauvegarde / crée create topic poll with moderation call. | — |
| `CreateTopicWithModerationCall` | actorId, actorName, forumId, forumSubject, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() | Sauvegarde / crée create topic with moderation call. | — |
| `DeletePost` | postId, actorName, actorPassword | Supprime e post. | — |
| `DeleteTopic` | topicId, actorName, actorPassword | Supprime e topic. | — |
| `GetFilteredTopics` | params.forumId, params.filterId, params.actorId, pageIndex, pageSize | Récupère filtered topics. | — |
| `GetForums` | — | Récupère forums. | — |
| `GetPostAmount` | topicId | Récupère post amount. | — |
| `GetPostData` | postId | Récupère post data. | — |
| `GetPosts` | topicID, pageIndex, pageSize | Récupère posts. | — |
| `GetTopic` | topicId, actorId | Récupère topic. | — |
| `ToggleSticky` | actorName, actorPassword, topicId, type | Endpoint AMF `ToggleSticky`. | — |
| `UpdatePost` | actorId | Met à jour ate post. | — |
| `UpdateTopic` | topic.TopicId | Met à jour ate topic. | — |
| `UserDeletePost` | actorId, postId | Endpoint AMF `UserDeletePost`. | — |

### Détail endpoints

#### `AdminCreateTopic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorName, actorPassword, forumId, subject, type, message, colorCode, subjectChatLogId, messageChatLogId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / appelants | `NewTopic.as` |
| Fonctionnement | Endpoint AMF `AdminCreateTopic`. |

#### `AdminCreateTopicPoll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, forumId, filteredQuestion, filteredAnsers, topicType, adminUserName, adminPassword, -1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / appelants | `NewTopic.as` |
| Fonctionnement | Endpoint AMF `AdminCreateTopicPoll`. |

#### `CheckAllowedCreateTopic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / appelants | `ForumBrowserView.as` |
| Fonctionnement | Vérifie allowed create topic. |

#### `CreatePostWithModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorName, topicId, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Sauvegarde / crée create post with moderation call. |

#### `CreateTopicPollWithModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorName, forumId, pollQuestion, pollAnswers, TextModerationHandler.getInstance().isRestrictedUser() |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Sauvegarde / crée create topic poll with moderation call. |

#### `CreateTopicWithModerationCall`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, actorName, forumId, forumSubject, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Sauvegarde / crée create topic with moderation call. |

#### `DeletePost`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | postId, actorName, actorPassword |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | 0 OK · 1 erreur · 2 chaîne interdite (modération) |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Supprime e post. |

#### `DeleteTopic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | topicId, actorName, actorPassword |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / appelants | `ForumTopicThinListItemRenderer.as` |
| Fonctionnement | Supprime e topic. |

#### `GetFilteredTopics`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | params.forumId, params.filterId, params.actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / appelants | `ForumBrowserView.as`, `NewsBrowserHelpers.as` |
| Fonctionnement | Récupère filtered topics. |

#### `GetForums`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Récupère forums. |

#### `GetPostAmount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | topicId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Récupère post amount. |

#### `GetPostData`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | postId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Récupère post data. |

#### `GetPosts`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | topicID, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Récupère posts. |

#### `GetTopic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | topicId, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / appelants | `ForumManager.as` |
| Fonctionnement | Récupère topic. |

#### `ToggleSticky`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorName, actorPassword, topicId, type |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / appelants | `ForumTopicThinListItemRenderer.as` |
| Fonctionnement | Endpoint AMF `ToggleSticky`. |

#### `UpdatePost`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Met à jour ate post. |

#### `UpdateTopic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | topic.TopicId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Met à jour ate topic. |

#### `UserDeletePost`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, postId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Fonctionnement | Endpoint AMF `UserDeletePost`. |

## `WebService.NewsService.AMFNewsService`

**Chemin AMF :** `MovieStarPlanet.WebService.NewsService.AMFNewsService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetActiveNewsScrapBlog` | param1 | Récupère active news scrap blog. | — |
| `GetActiveNewsSlides` | param1 | Récupère active news slides. | — |
| `GetNewsById` | param1 | Récupère news by id. | — |
| `NewsClicked` | param1, param2 | Endpoint AMF `NewsClicked`. | — |
| `SaveNews` | param1 | Sauvegarde / crée save news. | — |
| `SaveThemeSnapshot` | param1, param2, param3, param4, param5, param6 | Sauvegarde / crée save theme snapshot. | — |
| `SetNewsUsage` | param1 | Met à jour news usage. | — |

### Détail endpoints

#### `GetActiveNewsScrapBlog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| Fonctionnement | Récupère active news scrap blog. |

#### `GetActiveNewsSlides`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / appelants | `NewsCtrls.as` |
| Fonctionnement | Récupère active news slides. |

#### `GetNewsById`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` (+1) |
| UI / appelants | `MovieCompetitionNew.as`, `MovieCompetitionOverview.as` |
| Fonctionnement | Récupère news by id. |

#### `NewsClicked`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / appelants | `NewsCtrls.as` |
| Fonctionnement | Endpoint AMF `NewsClicked`. |

#### `SaveNews`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / appelants | `MovieCompetitionOverview.as`, `UploadNews.as`, `ScrapBlogNewsEditor.as` |
| Fonctionnement | Sauvegarde / crée save news. |

#### `SaveThemeSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / appelants | `NewsEditor.as` |
| Fonctionnement | Sauvegarde / crée save theme snapshot. |

#### `SetNewsUsage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / appelants | `NewsCtrls.as` |
| Fonctionnement | Met à jour news usage. |

## `WebService.NotificationCenter.AMFNotificationCenterService`

**Chemin AMF :** `MovieStarPlanet.WebService.NotificationCenter.AMFNotificationCenterService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `ClaimBonus2` | actorId, contentTypes[] | Endpoint AMF `ClaimBonus2`. | `-429` |
| `GetNotificationCount` | param1 | Récupère notification count. | — |
| `GetNotificationsWithImageGuid` | param1 | Récupère notifications with image guid. | — |
| `GetThirdPatyAppNotifications` | param1 | Récupère third paty app notifications. | — |
| `GetTotalFameAward` | — | Récupère total fame award. | — |

### Détail endpoints

#### `ClaimBonus2`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, contentTypes[] |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `ErrorCode` (popup) |
| Codes retour | Champ `ErrorCode` == −429 (popup) |
| Client AMF | `com/moviestarplanet/featurespecificcontentbrowser/fame/control/valueobjects/NotificationCenterAmfService.as` (+1) |
| Fonctionnement | Endpoint AMF `ClaimBonus2`. |

#### `GetNotificationCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/activitiesbar/NotificationCenterAmfService.as` (+1) |
| UI / appelants | `ActivitiesBar.as`, `NotificationCenterManager.as`, `NotificationCenterModuleManager.as` |
| Fonctionnement | Récupère notification count. |

#### `GetNotificationsWithImageGuid`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/featurespecificcontentbrowser/fame/control/valueobjects/NotificationCenterAmfService.as` (+1) |
| Fonctionnement | Récupère notifications with image guid. |

#### `GetThirdPatyAppNotifications`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Non |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/notificationcenter/service/NotificationCenterAmfService.as` |
| UI / appelants | `Stub.as` |
| Fonctionnement | Récupère third paty app notifications. |

#### `GetTotalFameAward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/featurespecificcontentbrowser/fame/control/valueobjects/NotificationCenterAmfService.as` |
| Fonctionnement | Récupère total fame award. |

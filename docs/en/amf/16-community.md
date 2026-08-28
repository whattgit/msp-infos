# III.16 — Forum, news & activities

> **EN** · [Français](../../fr/amf/16-community.md)


Forums, polls, notifications, activity feed.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `ClaimBonus2` | `AMFNotificationCenterService` | `ErrorCode` | Yes |

## Response codes

| Code | Meaning |
|------|---------------|
| `0` | Topic/post created |
| `1` | Erreur |
| `2` | Forbidden string (moderation) |

## `Polls.AMFPollService`

**AMF path:** `MovieStarPlanet.Polls.AMFPollService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetPoll` | pollId, actorId | Fetches poll. | — |
| `GetPollLatest` | actorId | Fetches poll latest. | — |
| `GetPolls` | pageindex, pagesize | Fetches polls. | — |
| `GetPollsUnused` | — | Fetches polls unused. | — |
| `LinkPolls` | pollId, nextPollId | AMF endpoint `LinkPolls`. | — |
| `NewPoll` | question, answer1, answer2, answer3, answer4 | AMF endpoint `NewPoll`. | — |
| `NewPollPublish` | pollId, locale, siteDomain | AMF endpoint `NewPollPublish`. | — |
| `VotePoll` | pollId, actorId, answer | AMF endpoint `VotePoll`. | — |

### Endpoint details

#### `GetPoll`

| Property | Value |
|----------|-------|
| Parameters | pollId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollEditor.as`, `PollCtrls.as` |
| Behavior | Fetches poll. |

#### `GetPollLatest`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollCtrls.as` |
| Behavior | Fetches poll latest. |

#### `GetPolls`

| Property | Value |
|----------|-------|
| Parameters | pageindex, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollEditor.as` |
| Behavior | Fetches polls. |

#### `GetPollsUnused`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollEditor.as` |
| Behavior | Fetches polls unused. |

#### `LinkPolls`

| Property | Value |
|----------|-------|
| Parameters | pollId, nextPollId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollEditor.as` |
| Behavior | AMF endpoint `LinkPolls`. |

#### `NewPoll`

| Property | Value |
|----------|-------|
| Parameters | question, answer1, answer2, answer3, answer4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollEditor.as`, `PollEditorItem.as`, `NewTopic.as` |
| Behavior | AMF endpoint `NewPoll`. |

#### `NewPollPublish`

| Property | Value |
|----------|-------|
| Parameters | pollId, locale, siteDomain |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollEditorItem.as` |
| Behavior | AMF endpoint `NewPollPublish`. |

#### `VotePoll`

| Property | Value |
|----------|-------|
| Parameters | pollId, actorId, answer |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/pollservice/PollAmfService.as` |
| UI / callers | `PollCtrls.as` |
| Behavior | AMF endpoint `VotePoll`. |

## `WebService.Campaign.AMFCampaignService`

**AMF path:** `MovieStarPlanet.WebService.Campaign.AMFCampaignService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `UseCampaign` | param1, param2 | AMF endpoint `UseCampaign`. | — |

### Endpoint details

#### `UseCampaign`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/campaign/CampaignAmfService.as` |
| UI / callers | `CampaignHandlerBase.as` |
| Behavior | AMF endpoint `UseCampaign`. |

## `WebService.Forums.AMFForumService`

**AMF path:** `MovieStarPlanet.WebService.Forums.AMFForumService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AdminCreateTopic` | actorName, actorPassword, forumId, subject, type, message, colorCode, subjectChatLogId, messageChatLogId | AMF endpoint `AdminCreateTopic`. | — |
| `AdminCreateTopicPoll` | actorId, forumId, filteredQuestion, filteredAnsers, topicType, adminUserName, adminPassword, -1 | AMF endpoint `AdminCreateTopicPoll`. | — |
| `CheckAllowedCreateTopic` | actorId | Checks allowed create topic. | — |
| `CreatePostWithModerationCall` | actorId, actorName, topicId, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() | Saves / creates create post with moderation call. | — |
| `CreateTopicPollWithModerationCall` | actorId, actorName, forumId, pollQuestion, pollAnswers, TextModerationHandler.getInstance().isRestrictedUser() | Saves / creates create topic poll with moderation call. | — |
| `CreateTopicWithModerationCall` | actorId, actorName, forumId, forumSubject, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() | Saves / creates create topic with moderation call. | — |
| `DeletePost` | postId, actorName, actorPassword | Deletes e post. | — |
| `DeleteTopic` | topicId, actorName, actorPassword | Deletes e topic. | — |
| `GetFilteredTopics` | params.forumId, params.filterId, params.actorId, pageIndex, pageSize | Fetches filtered topics. | — |
| `GetForums` | — | Fetches forums. | — |
| `GetPostAmount` | topicId | Fetches post amount. | — |
| `GetPostData` | postId | Fetches post data. | — |
| `GetPosts` | topicID, pageIndex, pageSize | Fetches posts. | — |
| `GetTopic` | topicId, actorId | Fetches topic. | — |
| `ToggleSticky` | actorName, actorPassword, topicId, type | AMF endpoint `ToggleSticky`. | — |
| `UpdatePost` | actorId | Updates ate post. | — |
| `UpdateTopic` | topic.TopicId | Updates ate topic. | — |
| `UserDeletePost` | actorId, postId | AMF endpoint `UserDeletePost`. | — |

### Endpoint details

#### `AdminCreateTopic`

| Property | Value |
|----------|-------|
| Parameters | actorName, actorPassword, forumId, subject, type, message, colorCode, subjectChatLogId, messageChatLogId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / callers | `NewTopic.as` |
| Behavior | AMF endpoint `AdminCreateTopic`. |

#### `AdminCreateTopicPoll`

| Property | Value |
|----------|-------|
| Parameters | actorId, forumId, filteredQuestion, filteredAnsers, topicType, adminUserName, adminPassword, -1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / callers | `NewTopic.as` |
| Behavior | AMF endpoint `AdminCreateTopicPoll`. |

#### `CheckAllowedCreateTopic`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / callers | `ForumBrowserView.as` |
| Behavior | Checks allowed create topic. |

#### `CreatePostWithModerationCall`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorName, topicId, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Saves / creates create post with moderation call. |

#### `CreateTopicPollWithModerationCall`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorName, forumId, pollQuestion, pollAnswers, TextModerationHandler.getInstance().isRestrictedUser() |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Saves / creates create topic poll with moderation call. |

#### `CreateTopicWithModerationCall`

| Property | Value |
|----------|-------|
| Parameters | actorId, actorName, forumId, forumSubject, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Saves / creates create topic with moderation call. |

#### `DeletePost`

| Property | Value |
|----------|-------|
| Parameters | postId, actorName, actorPassword |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | 0 OK · 1 erreur · 2 chaîne interdite (modération) |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Deletes e post. |

#### `DeleteTopic`

| Property | Value |
|----------|-------|
| Parameters | topicId, actorName, actorPassword |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / callers | `ForumTopicThinListItemRenderer.as` |
| Behavior | Deletes e topic. |

#### `GetFilteredTopics`

| Property | Value |
|----------|-------|
| Parameters | params.forumId, params.filterId, params.actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / callers | `ForumBrowserView.as`, `NewsBrowserHelpers.as` |
| Behavior | Fetches filtered topics. |

#### `GetForums`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Fetches forums. |

#### `GetPostAmount`

| Property | Value |
|----------|-------|
| Parameters | topicId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Fetches post amount. |

#### `GetPostData`

| Property | Value |
|----------|-------|
| Parameters | postId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Fetches post data. |

#### `GetPosts`

| Property | Value |
|----------|-------|
| Parameters | topicID, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Fetches posts. |

#### `GetTopic`

| Property | Value |
|----------|-------|
| Parameters | topicId, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / callers | `ForumManager.as` |
| Behavior | Fetches topic. |

#### `ToggleSticky`

| Property | Value |
|----------|-------|
| Parameters | actorName, actorPassword, topicId, type |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| UI / callers | `ForumTopicThinListItemRenderer.as` |
| Behavior | AMF endpoint `ToggleSticky`. |

#### `UpdatePost`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Updates ate post. |

#### `UpdateTopic`

| Property | Value |
|----------|-------|
| Parameters | topic.TopicId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | Updates ate topic. |

#### `UserDeletePost`

| Property | Value |
|----------|-------|
| Parameters | actorId, postId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/forum/service/ForumAmfService.as` |
| Behavior | AMF endpoint `UserDeletePost`. |

## `WebService.NewsService.AMFNewsService`

**AMF path:** `MovieStarPlanet.WebService.NewsService.AMFNewsService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetActiveNewsScrapBlog` | param1 | Fetches active news scrap blog. | — |
| `GetActiveNewsSlides` | param1 | Fetches active news slides. | — |
| `GetNewsById` | param1 | Fetches news by id. | — |
| `NewsClicked` | param1, param2 | AMF endpoint `NewsClicked`. | — |
| `SaveNews` | param1 | Saves / creates save news. | — |
| `SaveThemeSnapshot` | param1, param2, param3, param4, param5, param6 | Saves / creates save theme snapshot. | — |
| `SetNewsUsage` | param1 | Updates news usage. | — |

### Endpoint details

#### `GetActiveNewsScrapBlog`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| Behavior | Fetches active news scrap blog. |

#### `GetActiveNewsSlides`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / callers | `NewsCtrls.as` |
| Behavior | Fetches active news slides. |

#### `GetNewsById`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` (+1) |
| UI / callers | `MovieCompetitionNew.as`, `MovieCompetitionOverview.as` |
| Behavior | Fetches news by id. |

#### `NewsClicked`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / callers | `NewsCtrls.as` |
| Behavior | AMF endpoint `NewsClicked`. |

#### `SaveNews`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / callers | `MovieCompetitionOverview.as`, `UploadNews.as`, `ScrapBlogNewsEditor.as` |
| Behavior | Saves / creates save news. |

#### `SaveThemeSnapshot`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / callers | `NewsEditor.as` |
| Behavior | Saves / creates save theme snapshot. |

#### `SetNewsUsage`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/news/service/NewsAmfServiceForWeb.as` |
| UI / callers | `NewsCtrls.as` |
| Behavior | Updates news usage. |

## `WebService.NotificationCenter.AMFNotificationCenterService`

**AMF path:** `MovieStarPlanet.WebService.NotificationCenter.AMFNotificationCenterService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `ClaimBonus2` | actorId, contentTypes[] | AMF endpoint `ClaimBonus2`. | `-429` |
| `GetNotificationCount` | param1 | Fetches notification count. | — |
| `GetNotificationsWithImageGuid` | param1 | Fetches notifications with image guid. | — |
| `GetThirdPatyAppNotifications` | param1 | Fetches third paty app notifications. | — |
| `GetTotalFameAward` | — | Fetches total fame award. | — |

### Endpoint details

#### `ClaimBonus2`

| Property | Value |
|----------|-------|
| Parameters | actorId, contentTypes[] |
| AMF ticket | Yes |
| Rate limit | `-429` on `ErrorCode` (popup) |
| Return codes | Champ `ErrorCode` == −429 (popup) |
| AMF client | `com/moviestarplanet/featurespecificcontentbrowser/fame/control/valueobjects/NotificationCenterAmfService.as` (+1) |
| Behavior | AMF endpoint `ClaimBonus2`. |

#### `GetNotificationCount`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/activitiesbar/NotificationCenterAmfService.as` (+1) |
| UI / callers | `ActivitiesBar.as`, `NotificationCenterManager.as`, `NotificationCenterModuleManager.as` |
| Behavior | Fetches notification count. |

#### `GetNotificationsWithImageGuid`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/featurespecificcontentbrowser/fame/control/valueobjects/NotificationCenterAmfService.as` (+1) |
| Behavior | Fetches notifications with image guid. |

#### `GetThirdPatyAppNotifications`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | No |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/notificationcenter/service/NotificationCenterAmfService.as` |
| UI / callers | `Stub.as` |
| Behavior | Fetches third paty app notifications. |

#### `GetTotalFameAward`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/featurespecificcontentbrowser/fame/control/valueobjects/NotificationCenterAmfService.as` |
| Behavior | Fetches total fame award. |

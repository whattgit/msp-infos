# III.9 — Video & YouTube

> **EN** · [Français](../../fr/amf/09-video.md)


MSP TV, playlists, likes.

## `WebService.Video.AMFVideoService`

**AMF path:** `MovieStarPlanet.WebService.Video.AMFVideoService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AddVideoToMspTv` | param1, param2, param3, param4, param5 | AMF endpoint `AddVideoToMspTv`. | — |
| `AutoSaveVideoFromFeed` | param1, param2, param3, param4, param5, _loc9_ | AMF endpoint `AutoSaveVideoFromFeed`. | — |
| `CreateBlankPlaylist` | param1, param2 | Saves / creates create blank playlist. | — |
| `DeleteExternalVideoPlaylistRel` | param1, param2, param3 | Deletes e external video playlist rel. | — |
| `DeletePlaylist` | param1, param2, param3 | Deletes e playlist. | — |
| `GetCategoryExternalVideosForPlayback` | param1, param2 | Fetches category external videos for playback. | — |
| `GetExternalVideoForChatRoom` | param1 | Fetches external video for chat room. | — |
| `GetMspTvExternalVideosForPlayback` | param1 | Fetches msp tv external videos for playback. | — |
| `GetMyPlaylistsForVideo` | param1 | Fetches my playlists for video. | — |
| `GetPagedBlockedExternalVideos` | param1, param2, param3, param4 | Paged list — Paged Blocked External Videos. | — |
| `GetPagedCategoryExternalVideos` | param1, param2, param3 | Paged list — Paged Category External Videos. | — |
| `GetPagedExternalVideos` | param1, param2, param3 | Paged list — Paged External Videos. | — |
| `GetPagedMspTvExternalVideos` | param1, param2 | Paged list — Paged Msp Tv External Videos. | — |
| `GetPagedNewestExternalVideos` | param1, param2 | Paged list — Paged Newest External Videos. | — |
| `GetPagedPlaylists` | param1, param2, param3, param4 | Paged list — Paged Playlists. | — |
| `GetPagedPlaylistsBySearch` | param1, param2, param3, param4 | Paged list — Paged Playlists By Search. | — |
| `GetPagedVideoListObjects` | param1, param2, param3 | Paged list — Paged Video List Objects. | — |
| `GetPagedVideoListObjectsByAddTime` | (actorId, 0, 50) · (param1, param2, param3) | Paged list — Paged Video List Objects By Add Time. | — |
| `GetPlaylist` | param1, param2 | Fetches playlist. | — |
| `GetPlaylistForPlayback` | param1, param2, param3 | Fetches playlist for playback. | — |
| `GetPlaylistsForDropdown` | param1 | Fetches playlists for dropdown. | — |
| `GetTopExternalVideosForPlayback` | param1 | Fetches top external videos for playback. | — |
| `GetYouTubeVideo` | param1, param2 | Fetches you tube video. | — |
| `GetYouTubeVideoInfo` | param1 | Fetches you tube video info. | — |
| `IncrementReportCount` | param1 | AMF endpoint `IncrementReportCount`. | — |
| `IncrementViewsExternalVideo` | param1 | AMF endpoint `IncrementViewsExternalVideo`. | — |
| `LikePlaylist` | param1, param2, param3 | AMF endpoint `LikePlaylist`. | — |
| `LikeYouTube` | param1, param2 | AMF endpoint `LikeYouTube`. | — |
| `MoveVideoInPlaylist` | param1, param2, param3, param4, param5 | AMF endpoint `MoveVideoInPlaylist`. | — |
| `RenamePlaylist` | param1, param2, param3 | AMF endpoint `RenamePlaylist`. | — |
| `ReportErrorOnVideo` | param1 | AMF endpoint `ReportErrorOnVideo`. | — |
| `SaveToNewPlaylist` | param1, param2, param3, param4, param5 | Saves / creates save to new playlist. | — |
| `SaveToPlaylist` | param1, param2, param3, param4 | Saves / creates save to playlist. | — |
| `YouTubeBlock` | param1, param2, param3, param4 | AMF endpoint `YouTubeBlock`. | — |
| `YouTubePopulateViewsAndLikes` | param1, param2 | AMF endpoint `YouTubePopulateViewsAndLikes`. | — |

### Endpoint details

#### `AddVideoToMspTv`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | AMF endpoint `AddVideoToMspTv`. |

#### `AutoSaveVideoFromFeed`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, _loc9_ |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `VideoListItemRenderer.as`, `YouTubePlayerController.as` |
| Behavior | AMF endpoint `AutoSaveVideoFromFeed`. |

#### `CreateBlankPlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `NewPlaylist.as` |
| Behavior | Saves / creates create blank playlist. |

#### `DeleteExternalVideoPlaylistRel`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoSocialListItemRenderer.as`, `VideoServiceProvider.as`, `VideoListItemRenderer.as` |
| Behavior | Deletes e external video playlist rel. |

#### `DeletePlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `PlaylistSubRenderer.as` |
| Behavior | Deletes e playlist. |

#### `GetCategoryExternalVideosForPlayback`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Fetches category external videos for playback. |

#### `GetExternalVideoForChatRoom`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as` |
| Behavior | Fetches external video for chat room. |

#### `GetMspTvExternalVideosForPlayback`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Fetches msp tv external videos for playback. |

#### `GetMyPlaylistsForVideo`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `YouTubePlayerController.as` |
| Behavior | Fetches my playlists for video. |

#### `GetPagedBlockedExternalVideos`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `BlockedVideosForm.as`, `VideoServiceProvider.as` |
| Behavior | Paged list — Paged Blocked External Videos. |

#### `GetPagedCategoryExternalVideos`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Paged list — Paged Category External Videos. |

#### `GetPagedExternalVideos`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `PersonalContentList.as`, `VideoServiceProvider.as` |
| Behavior | Paged list — Paged External Videos. |

#### `GetPagedMspTvExternalVideos`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubeBrowserHelpers.as` |
| Behavior | Paged list — Paged Msp Tv External Videos. |

#### `GetPagedNewestExternalVideos`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as` |
| Behavior | Paged list — Paged Newest External Videos. |

#### `GetPagedPlaylists`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as` |
| Behavior | Paged list — Paged Playlists. |

#### `GetPagedPlaylistsBySearch`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as` |
| Behavior | Paged list — Paged Playlists By Search. |

#### `GetPagedVideoListObjects`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as` |
| Behavior | Paged list — Paged Video List Objects. |

#### `GetPagedVideoListObjectsByAddTime`

| Property | Value |
|----------|-------|
| Parameters | (actorId, 0, 50) · (param1, param2, param3) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+1) |
| UI / callers | `VideoServiceProvider.as` |
| Behavior | Paged list — Paged Video List Objects By Add Time. |

#### `GetPlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `InventoryLoader.as`, `ContentLoader.as`, `Favorites.as`, `VideoServiceProvider.as` (+1) |
| Behavior | Fetches playlist. |

#### `GetPlaylistForPlayback`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Fetches playlist for playback. |

#### `GetPlaylistsForDropdown`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Fetches playlists for dropdown. |

#### `GetTopExternalVideosForPlayback`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Fetches top external videos for playback. |

#### `GetYouTubeVideo`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `ScrapBlogYouTubeItem.as`, `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Fetches you tube video. |

#### `GetYouTubeVideoInfo`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| Behavior | Fetches you tube video info. |

#### `IncrementReportCount`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| Behavior | AMF endpoint `IncrementReportCount`. |

#### `IncrementViewsExternalVideo`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `YouTubePlayerController.as` |
| Behavior | AMF endpoint `IncrementViewsExternalVideo`. |

#### `LikePlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `PlaylistSubRenderer.as` |
| Behavior | AMF endpoint `LikePlaylist`. |

#### `LikeYouTube`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | AMF endpoint `LikeYouTube`. |

#### `MoveVideoInPlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `VideoListItemRenderer.as` |
| Behavior | AMF endpoint `MoveVideoInPlaylist`. |

#### `RenamePlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `PlaylistSubRenderer.as` |
| Behavior | AMF endpoint `RenamePlaylist`. |

#### `ReportErrorOnVideo`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | AMF endpoint `ReportErrorOnVideo`. |

#### `SaveToNewPlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Saves / creates save to new playlist. |

#### `SaveToPlaylist`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Behavior | Saves / creates save to playlist. |

#### `YouTubeBlock`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoSocialListItemRenderer.as`, `VideoServiceProvider.as`, `VideoListItemRenderer.as`, `ListItemHighscore.as` (+1) |
| Behavior | AMF endpoint `YouTubeBlock`. |

#### `YouTubePopulateViewsAndLikes`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / callers | `VideoServiceProvider.as`, `YouTubeBrowserHelpers.as`, `YouTubePlayerController.as` |
| Behavior | AMF endpoint `YouTubePopulateViewsAndLikes`. |

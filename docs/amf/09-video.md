# V.9 — Vidéo & YouTube

MSP TV, playlists, likes.

## `WebService.Video.AMFVideoService`

**Chemin AMF :** `MovieStarPlanet.WebService.Video.AMFVideoService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AddVideoToMspTv` | param1, param2, param3, param4, param5 | Endpoint AMF `AddVideoToMspTv`. | — |
| `AutoSaveVideoFromFeed` | param1, param2, param3, param4, param5, _loc9_ | Endpoint AMF `AutoSaveVideoFromFeed`. | — |
| `CreateBlankPlaylist` | param1, param2 | Sauvegarde / crée create blank playlist. | — |
| `DeleteExternalVideoPlaylistRel` | param1, param2, param3 | Supprime e external video playlist rel. | — |
| `DeletePlaylist` | param1, param2, param3 | Supprime e playlist. | — |
| `GetCategoryExternalVideosForPlayback` | param1, param2 | Récupère category external videos for playback. | — |
| `GetExternalVideoForChatRoom` | param1 | Récupère external video for chat room. | — |
| `GetMspTvExternalVideosForPlayback` | param1 | Récupère msp tv external videos for playback. | — |
| `GetMyPlaylistsForVideo` | param1 | Récupère my playlists for video. | — |
| `GetPagedBlockedExternalVideos` | param1, param2, param3, param4 | Liste paginée — Paged Blocked External Videos. | — |
| `GetPagedCategoryExternalVideos` | param1, param2, param3 | Liste paginée — Paged Category External Videos. | — |
| `GetPagedExternalVideos` | param1, param2, param3 | Liste paginée — Paged External Videos. | — |
| `GetPagedMspTvExternalVideos` | param1, param2 | Liste paginée — Paged Msp Tv External Videos. | — |
| `GetPagedNewestExternalVideos` | param1, param2 | Liste paginée — Paged Newest External Videos. | — |
| `GetPagedPlaylists` | param1, param2, param3, param4 | Liste paginée — Paged Playlists. | — |
| `GetPagedPlaylistsBySearch` | param1, param2, param3, param4 | Liste paginée — Paged Playlists By Search. | — |
| `GetPagedVideoListObjects` | param1, param2, param3 | Liste paginée — Paged Video List Objects. | — |
| `GetPagedVideoListObjectsByAddTime` | (actorId, 0, 50) · (param1, param2, param3) | Liste paginée — Paged Video List Objects By Add Time. | — |
| `GetPlaylist` | param1, param2 | Récupère playlist. | — |
| `GetPlaylistForPlayback` | param1, param2, param3 | Récupère playlist for playback. | — |
| `GetPlaylistsForDropdown` | param1 | Récupère playlists for dropdown. | — |
| `GetTopExternalVideosForPlayback` | param1 | Récupère top external videos for playback. | — |
| `GetYouTubeVideo` | param1, param2 | Récupère you tube video. | — |
| `GetYouTubeVideoInfo` | param1 | Récupère you tube video info. | — |
| `IncrementReportCount` | param1 | Endpoint AMF `IncrementReportCount`. | — |
| `IncrementViewsExternalVideo` | param1 | Endpoint AMF `IncrementViewsExternalVideo`. | — |
| `LikePlaylist` | param1, param2, param3 | Endpoint AMF `LikePlaylist`. | — |
| `LikeYouTube` | param1, param2 | Endpoint AMF `LikeYouTube`. | — |
| `MoveVideoInPlaylist` | param1, param2, param3, param4, param5 | Endpoint AMF `MoveVideoInPlaylist`. | — |
| `RenamePlaylist` | param1, param2, param3 | Endpoint AMF `RenamePlaylist`. | — |
| `ReportErrorOnVideo` | param1 | Endpoint AMF `ReportErrorOnVideo`. | — |
| `SaveToNewPlaylist` | param1, param2, param3, param4, param5 | Sauvegarde / crée save to new playlist. | — |
| `SaveToPlaylist` | param1, param2, param3, param4 | Sauvegarde / crée save to playlist. | — |
| `YouTubeBlock` | param1, param2, param3, param4 | Endpoint AMF `YouTubeBlock`. | — |
| `YouTubePopulateViewsAndLikes` | param1, param2 | Endpoint AMF `YouTubePopulateViewsAndLikes`. | — |

### Détail endpoints

#### `AddVideoToMspTv`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Endpoint AMF `AddVideoToMspTv`. |

#### `AutoSaveVideoFromFeed`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, _loc9_ |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `VideoListItemRenderer.as`, `YouTubePlayerController.as` |
| Fonctionnement | Endpoint AMF `AutoSaveVideoFromFeed`. |

#### `CreateBlankPlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `NewPlaylist.as` |
| Fonctionnement | Sauvegarde / crée create blank playlist. |

#### `DeleteExternalVideoPlaylistRel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoSocialListItemRenderer.as`, `VideoServiceProvider.as`, `VideoListItemRenderer.as` |
| Fonctionnement | Supprime e external video playlist rel. |

#### `DeletePlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `PlaylistSubRenderer.as` |
| Fonctionnement | Supprime e playlist. |

#### `GetCategoryExternalVideosForPlayback`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Récupère category external videos for playback. |

#### `GetExternalVideoForChatRoom`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as` |
| Fonctionnement | Récupère external video for chat room. |

#### `GetMspTvExternalVideosForPlayback`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Récupère msp tv external videos for playback. |

#### `GetMyPlaylistsForVideo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `YouTubePlayerController.as` |
| Fonctionnement | Récupère my playlists for video. |

#### `GetPagedBlockedExternalVideos`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `BlockedVideosForm.as`, `VideoServiceProvider.as` |
| Fonctionnement | Liste paginée — Paged Blocked External Videos. |

#### `GetPagedCategoryExternalVideos`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Liste paginée — Paged Category External Videos. |

#### `GetPagedExternalVideos`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `PersonalContentList.as`, `VideoServiceProvider.as` |
| Fonctionnement | Liste paginée — Paged External Videos. |

#### `GetPagedMspTvExternalVideos`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubeBrowserHelpers.as` |
| Fonctionnement | Liste paginée — Paged Msp Tv External Videos. |

#### `GetPagedNewestExternalVideos`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as` |
| Fonctionnement | Liste paginée — Paged Newest External Videos. |

#### `GetPagedPlaylists`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as` |
| Fonctionnement | Liste paginée — Paged Playlists. |

#### `GetPagedPlaylistsBySearch`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as` |
| Fonctionnement | Liste paginée — Paged Playlists By Search. |

#### `GetPagedVideoListObjects`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as` |
| Fonctionnement | Liste paginée — Paged Video List Objects. |

#### `GetPagedVideoListObjectsByAddTime`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (actorId, 0, 50) · (param1, param2, param3) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+1) |
| UI / appelants | `VideoServiceProvider.as` |
| Fonctionnement | Liste paginée — Paged Video List Objects By Add Time. |

#### `GetPlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `InventoryLoader.as`, `ContentLoader.as`, `Favorites.as`, `VideoServiceProvider.as` (+1) |
| Fonctionnement | Récupère playlist. |

#### `GetPlaylistForPlayback`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Récupère playlist for playback. |

#### `GetPlaylistsForDropdown`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Récupère playlists for dropdown. |

#### `GetTopExternalVideosForPlayback`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Récupère top external videos for playback. |

#### `GetYouTubeVideo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `ScrapBlogYouTubeItem.as`, `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Récupère you tube video. |

#### `GetYouTubeVideoInfo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| Fonctionnement | Récupère you tube video info. |

#### `IncrementReportCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| Fonctionnement | Endpoint AMF `IncrementReportCount`. |

#### `IncrementViewsExternalVideo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `YouTubePlayerController.as` |
| Fonctionnement | Endpoint AMF `IncrementViewsExternalVideo`. |

#### `LikePlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `PlaylistSubRenderer.as` |
| Fonctionnement | Endpoint AMF `LikePlaylist`. |

#### `LikeYouTube`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Endpoint AMF `LikeYouTube`. |

#### `MoveVideoInPlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `VideoListItemRenderer.as` |
| Fonctionnement | Endpoint AMF `MoveVideoInPlaylist`. |

#### `RenamePlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `PlaylistSubRenderer.as` |
| Fonctionnement | Endpoint AMF `RenamePlaylist`. |

#### `ReportErrorOnVideo`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Endpoint AMF `ReportErrorOnVideo`. |

#### `SaveToNewPlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Sauvegarde / crée save to new playlist. |

#### `SaveToPlaylist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubePlayerController.as` |
| Fonctionnement | Sauvegarde / crée save to playlist. |

#### `YouTubeBlock`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoSocialListItemRenderer.as`, `VideoServiceProvider.as`, `VideoListItemRenderer.as`, `ListItemHighscore.as` (+1) |
| Fonctionnement | Endpoint AMF `YouTubeBlock`. |

#### `YouTubePopulateViewsAndLikes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/videoservice/VideoAmfService.as` |
| UI / appelants | `VideoServiceProvider.as`, `YouTubeBrowserHelpers.as`, `YouTubePlayerController.as` |
| Fonctionnement | Endpoint AMF `YouTubePopulateViewsAndLikes`. |

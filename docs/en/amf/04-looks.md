# III.4 — Looks

> **EN** · [Français](../../fr/amf/04-looks.md)


Saved outfits, sharing, community pagination.

## `WebService.Looks.AMFLookService`

**AMF path:** `MovieStarPlanet.WebService.Looks.AMFLookService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CanWearOwnLook` | param1, param2 | Checks possession de tous les vêtements du look avant port. | — |
| `GetLookById` | (lookId) · (lookId, this.actorModel.actorId) | Loads un look ; enrichissement blob si créé après 2013. | — |
| `GetLooksByOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Fetches looks by others. | — |
| `GetLooksCreatedBy` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Fetches looks created by. | — |
| `GetLooksForActor` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Liste paginée des looks d'un acteur ; enrichissement blob post-réponse. | — |
| `GetLooksForOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Fetches looks for others. | — |
| `GetLooksLatest` | pageIndex, pageSize | Fetches looks latest. | — |
| `GetLooksLatestByFriends` | actorId, pageIndex, pageSize | Fetches looks latest by friends. | — |
| `GetLooksLatestByMeAndFriends` | actorId, pageIndex, pageSize | Fetches looks latest by me and friends. | — |
| `GetLooksLikedByMe` | actorId, pageIndex, pageSize | Fetches looks liked by me. | — |
| `GetLooksTopAll` | pageIndex, pageSize | Top looks communauté paginé (10/page). | — |
| `GetLooksTopByFriends` | actorId, pageIndex, pageSize | Fetches looks top by friends. | — |
| `GetLooksTopByMeAndFriends` | actorId, pageIndex, pageSize | Fetches looks top by me and friends. | — |
| `GetRandomLookByLikes` | poolSize | Fetches random look by likes. | — |
| `LookDelete` | lookId, this.actorModel.actorId | Deletes un look. | — |
| `SaveLookAndData` | look, clotheIds[], snapshot, fullSnapshot | Crée/met à jour un look + snapshots + IDs vêtements ; retourne `lookId`, `awardedFame`. | — |
| `SaveSmallLookSnapshot` | look, lookSnapshot | Saves / creates save small look snapshot. | — |

### Endpoint details

#### `CanWearOwnLook`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Success objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `MyLooksEditor.as`, `DressingRoomPreviewView.as`, `LooksViewerFrame.as` |
| Behavior | Checks possession de tous les vêtements du look avant port. |

#### `GetLookById`

| Property | Value |
|----------|-------|
| Parameters | (lookId) · (lookId, this.actorModel.actorId) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Success objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `MyLooks.as`, `MyLooksEditor.as`, `EditOrDeleteAnimation.as`, `UploadAnimation.as` (+7) |
| Behavior | Loads un look ; enrichissement blob si créé après 2013. |

#### `GetLooksByOthers`

| Property | Value |
|----------|-------|
| Parameters | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksOverview.as`, `Pager.as`, `LooksListsView.as` |
| Behavior | Fetches looks by others. |

#### `GetLooksCreatedBy`

| Property | Value |
|----------|-------|
| Parameters | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `SubmitLookToCompetition.as`, `Pager.as`, `LooksContentService.as` |
| Behavior | Fetches looks created by. |

#### `GetLooksForActor`

| Property | Value |
|----------|-------|
| Parameters | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksOverview.as`, `PersonalContentList.as`, `Pager.as`, `DressingRoomPagers.as` (+4) |
| Behavior | Liste paginée des looks d'un acteur ; enrichissement blob post-réponse. |

#### `GetLooksForOthers`

| Property | Value |
|----------|-------|
| Parameters | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksOverview.as`, `Pager.as`, `LooksListsView.as` |
| Behavior | Fetches looks for others. |

#### `GetLooksLatest`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksPagerContainer.as`, `LooksContentService.as` |
| Behavior | Fetches looks latest. |

#### `GetLooksLatestByFriends`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksPagerContainer.as`, `LooksContentService.as` |
| Behavior | Fetches looks latest by friends. |

#### `GetLooksLatestByMeAndFriends`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| Behavior | Fetches looks latest by me and friends. |

#### `GetLooksLikedByMe`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksPagerContainer.as`, `LooksContentService.as` |
| Behavior | Fetches looks liked by me. |

#### `GetLooksTopAll`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksPagerContainer.as`, `LooksContentService.as` |
| Behavior | Top looks communauté paginé (10/page). |

#### `GetLooksTopByFriends`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksContentService.as` |
| Behavior | Fetches looks top by friends. |

#### `GetLooksTopByMeAndFriends`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksPagerContainer.as`, `LooksContentService.as` |
| Behavior | Fetches looks top by me and friends. |

#### `GetRandomLookByLikes`

| Property | Value |
|----------|-------|
| Parameters | poolSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `ChecksumCalculator.as`, `FrontPage2.as` |
| Behavior | Fetches random look by likes. |

#### `LookDelete`

| Property | Value |
|----------|-------|
| Parameters | lookId, this.actorModel.actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Success objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LookListItemComponent.as`, `LookSocialListItemRenderer.as`, `LooksGridItemRenderer.as`, `LooksViewerDeleteCommand.as` |
| Behavior | Deletes un look. |

#### `SaveLookAndData`

| Property | Value |
|----------|-------|
| Parameters | look, clotheIds[], snapshot, fullSnapshot |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Success objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| Behavior | Crée/met à jour un look + snapshots + IDs vêtements ; retourne `lookId`, `awardedFame`. |

#### `SaveSmallLookSnapshot`

| Property | Value |
|----------|-------|
| Parameters | look, lookSnapshot |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / callers | `LooksDisplayView.as` |
| Behavior | Saves / creates save small look snapshot. |

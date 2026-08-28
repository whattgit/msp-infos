# III.18 — Clubs

> **EN** · [Français](../../fr/amf/18-clubs.md)


MSP club creation and management.

## `WebService.Clubs.AMFClubService`

**AMF path:** `MovieStarPlanet.WebService.Clubs.AMFClubService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `ApproveClubMembership` | ownerId, approveeId, clubId | AMF endpoint `ApproveClubMembership`. | — |
| `CreateClubEntityRel` | actorId, clubId, entityType, entityId | Saves / creates create club entity rel. | — |
| `GetBadgeScrapBlogId` | param1 | Fetches badge scrap blog id. | — |
| `GetClub` | param1 | Fetches club. | — |
| `GetClubActor` | param1 | Fetches club actor. | — |
| `GetClubActorRel` | param1, param2 | Fetches club actor rel. | — |
| `GetClubEntityContent` | actorId, clubId, filter, pageindex, pagesize | Fetches club entity content. | — |
| `GetPagedClubMembersList` | clubId, memberTypes, pageindex, pagesize | Paged list — Paged Club Members List. | — |
| `GetPagedClubsList` | actorId, filter, sort, category, searchString, pageIndex, pageSize | Paged list — Paged Clubs List. | — |
| `KickClubMember` | ownerId, kickeeId, clubId | AMF endpoint `KickClubMember`. | — |
| `LeaveClub` | actorId, clubId | AMF endpoint `LeaveClub`. | — |
| `RemoveClubEntityRel` | actorId, clubId, clubEntityRelId | Deletes e club entity rel. | — |
| `RequestJoinClub` | actorId, clubId | AMF endpoint `RequestJoinClub`. | — |
| `ResetClub` | clubId, type | AMF endpoint `ResetClub`. | — |
| `SaveClub` | actorId, club | Saves / creates save club. | — |

### Endpoint details

#### `ApproveClubMembership`

| Property | Value |
|----------|-------|
| Parameters | ownerId, approveeId, clubId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubMemberList.as` |
| Behavior | AMF endpoint `ApproveClubMembership`. |

#### `CreateClubEntityRel`

| Property | Value |
|----------|-------|
| Parameters | actorId, clubId, entityType, entityId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubContentList.as` |
| Behavior | Saves / creates create club entity rel. |

#### `GetBadgeScrapBlogId`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| Behavior | Fetches badge scrap blog id. |

#### `GetClub`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ActionOpenClub.as`, `ClubsManager.as`, `ClubList.as`, `ClubSelector.as` (+8) |
| Behavior | Fetches club. |

#### `GetClubActor`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubsManager.as`, `ClubSelector.as`, `ContentOpenerWeb.as` |
| Behavior | Fetches club actor. |

#### `GetClubActorRel`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubsManager.as` |
| Behavior | Fetches club actor rel. |

#### `GetClubEntityContent`

| Property | Value |
|----------|-------|
| Parameters | actorId, clubId, filter, pageindex, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubContentList.as` |
| Behavior | Fetches club entity content. |

#### `GetPagedClubMembersList`

| Property | Value |
|----------|-------|
| Parameters | clubId, memberTypes, pageindex, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubMemberList.as`, `ClubView.as`, `Pager.as` |
| Behavior | Paged list — Paged Club Members List. |

#### `GetPagedClubsList`

| Property | Value |
|----------|-------|
| Parameters | actorId, filter, sort, category, searchString, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubList.as`, `Pager.as` |
| Behavior | Paged list — Paged Clubs List. |

#### `KickClubMember`

| Property | Value |
|----------|-------|
| Parameters | ownerId, kickeeId, clubId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubMemberList.as` |
| Behavior | AMF endpoint `KickClubMember`. |

#### `LeaveClub`

| Property | Value |
|----------|-------|
| Parameters | actorId, clubId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubView.as` |
| Behavior | AMF endpoint `LeaveClub`. |

#### `RemoveClubEntityRel`

| Property | Value |
|----------|-------|
| Parameters | actorId, clubId, clubEntityRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubContentList.as` |
| Behavior | Deletes e club entity rel. |

#### `RequestJoinClub`

| Property | Value |
|----------|-------|
| Parameters | actorId, clubId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubView.as` |
| Behavior | AMF endpoint `RequestJoinClub`. |

#### `ResetClub`

| Property | Value |
|----------|-------|
| Parameters | clubId, type |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubView.as` |
| Behavior | AMF endpoint `ResetClub`. |

#### `SaveClub`

| Property | Value |
|----------|-------|
| Parameters | actorId, club |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / callers | `ClubView.as`, `ManageClub.as` |
| Behavior | Saves / creates save club. |

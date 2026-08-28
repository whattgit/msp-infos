# V.18 — Clubs

Création et gestion clubs MSP.

## `WebService.Clubs.AMFClubService`

**Chemin AMF :** `MovieStarPlanet.WebService.Clubs.AMFClubService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `ApproveClubMembership` | ownerId, approveeId, clubId | Endpoint AMF `ApproveClubMembership`. | — |
| `CreateClubEntityRel` | actorId, clubId, entityType, entityId | Sauvegarde / crée create club entity rel. | — |
| `GetBadgeScrapBlogId` | param1 | Récupère badge scrap blog id. | — |
| `GetClub` | param1 | Récupère club. | — |
| `GetClubActor` | param1 | Récupère club actor. | — |
| `GetClubActorRel` | param1, param2 | Récupère club actor rel. | — |
| `GetClubEntityContent` | actorId, clubId, filter, pageindex, pagesize | Récupère club entity content. | — |
| `GetPagedClubMembersList` | clubId, memberTypes, pageindex, pagesize | Liste paginée — Paged Club Members List. | — |
| `GetPagedClubsList` | actorId, filter, sort, category, searchString, pageIndex, pageSize | Liste paginée — Paged Clubs List. | — |
| `KickClubMember` | ownerId, kickeeId, clubId | Endpoint AMF `KickClubMember`. | — |
| `LeaveClub` | actorId, clubId | Endpoint AMF `LeaveClub`. | — |
| `RemoveClubEntityRel` | actorId, clubId, clubEntityRelId | Supprime e club entity rel. | — |
| `RequestJoinClub` | actorId, clubId | Endpoint AMF `RequestJoinClub`. | — |
| `ResetClub` | clubId, type | Endpoint AMF `ResetClub`. | — |
| `SaveClub` | actorId, club | Sauvegarde / crée save club. | — |

### Détail endpoints

#### `ApproveClubMembership`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ownerId, approveeId, clubId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubMemberList.as` |
| Fonctionnement | Endpoint AMF `ApproveClubMembership`. |

#### `CreateClubEntityRel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clubId, entityType, entityId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubContentList.as` |
| Fonctionnement | Sauvegarde / crée create club entity rel. |

#### `GetBadgeScrapBlogId`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| Fonctionnement | Récupère badge scrap blog id. |

#### `GetClub`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ActionOpenClub.as`, `ClubsManager.as`, `ClubList.as`, `ClubSelector.as` (+8) |
| Fonctionnement | Récupère club. |

#### `GetClubActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubsManager.as`, `ClubSelector.as`, `ContentOpenerWeb.as` |
| Fonctionnement | Récupère club actor. |

#### `GetClubActorRel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubsManager.as` |
| Fonctionnement | Récupère club actor rel. |

#### `GetClubEntityContent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clubId, filter, pageindex, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubContentList.as` |
| Fonctionnement | Récupère club entity content. |

#### `GetPagedClubMembersList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clubId, memberTypes, pageindex, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubMemberList.as`, `ClubView.as`, `Pager.as` |
| Fonctionnement | Liste paginée — Paged Club Members List. |

#### `GetPagedClubsList`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, filter, sort, category, searchString, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubList.as`, `Pager.as` |
| Fonctionnement | Liste paginée — Paged Clubs List. |

#### `KickClubMember`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | ownerId, kickeeId, clubId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubMemberList.as` |
| Fonctionnement | Endpoint AMF `KickClubMember`. |

#### `LeaveClub`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clubId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubView.as` |
| Fonctionnement | Endpoint AMF `LeaveClub`. |

#### `RemoveClubEntityRel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clubId, clubEntityRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubContentList.as` |
| Fonctionnement | Supprime e club entity rel. |

#### `RequestJoinClub`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clubId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubView.as` |
| Fonctionnement | Endpoint AMF `RequestJoinClub`. |

#### `ResetClub`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clubId, type |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubView.as` |
| Fonctionnement | Endpoint AMF `ResetClub`. |

#### `SaveClub`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, club |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/club/service/ClubAMFService.as` |
| UI / appelants | `ClubView.as`, `ManageClub.as` |
| Fonctionnement | Sauvegarde / crée save club. |

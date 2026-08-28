# III.4 — Looks

> **FR** · [English](../../en/amf/04-looks.md)


Tenues sauvegardées, partage, pagination communautaire.

## `WebService.Looks.AMFLookService`

**Chemin AMF :** `MovieStarPlanet.WebService.Looks.AMFLookService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CanWearOwnLook` | param1, param2 | Vérifie possession de tous les vêtements du look avant port. | — |
| `GetLookById` | (lookId) · (lookId, this.actorModel.actorId) | Charge un look ; enrichissement blob si créé après 2013. | — |
| `GetLooksByOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Récupère looks by others. | — |
| `GetLooksCreatedBy` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Récupère looks created by. | — |
| `GetLooksForActor` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Liste paginée des looks d'un acteur ; enrichissement blob post-réponse. | — |
| `GetLooksForOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize | Récupère looks for others. | — |
| `GetLooksLatest` | pageIndex, pageSize | Récupère looks latest. | — |
| `GetLooksLatestByFriends` | actorId, pageIndex, pageSize | Récupère looks latest by friends. | — |
| `GetLooksLatestByMeAndFriends` | actorId, pageIndex, pageSize | Récupère looks latest by me and friends. | — |
| `GetLooksLikedByMe` | actorId, pageIndex, pageSize | Récupère looks liked by me. | — |
| `GetLooksTopAll` | pageIndex, pageSize | Top looks communauté paginé (10/page). | — |
| `GetLooksTopByFriends` | actorId, pageIndex, pageSize | Récupère looks top by friends. | — |
| `GetLooksTopByMeAndFriends` | actorId, pageIndex, pageSize | Récupère looks top by me and friends. | — |
| `GetRandomLookByLikes` | poolSize | Récupère random look by likes. | — |
| `LookDelete` | lookId, this.actorModel.actorId | Supprime un look. | — |
| `SaveLookAndData` | look, clotheIds[], snapshot, fullSnapshot | Crée/met à jour un look + snapshots + IDs vêtements ; retourne `lookId`, `awardedFame`. | — |
| `SaveSmallLookSnapshot` | look, lookSnapshot | Sauvegarde / crée save small look snapshot. | — |

### Détail endpoints

#### `CanWearOwnLook`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Succès objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `MyLooksEditor.as`, `DressingRoomPreviewView.as`, `LooksViewerFrame.as` |
| Fonctionnement | Vérifie possession de tous les vêtements du look avant port. |

#### `GetLookById`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (lookId) · (lookId, this.actorModel.actorId) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Succès objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `MyLooks.as`, `MyLooksEditor.as`, `EditOrDeleteAnimation.as`, `UploadAnimation.as` (+7) |
| Fonctionnement | Charge un look ; enrichissement blob si créé après 2013. |

#### `GetLooksByOthers`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksOverview.as`, `Pager.as`, `LooksListsView.as` |
| Fonctionnement | Récupère looks by others. |

#### `GetLooksCreatedBy`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `SubmitLookToCompetition.as`, `Pager.as`, `LooksContentService.as` |
| Fonctionnement | Récupère looks created by. |

#### `GetLooksForActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksOverview.as`, `PersonalContentList.as`, `Pager.as`, `DressingRoomPagers.as` (+4) |
| Fonctionnement | Liste paginée des looks d'un acteur ; enrichissement blob post-réponse. |

#### `GetLooksForOthers`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksOverview.as`, `Pager.as`, `LooksListsView.as` |
| Fonctionnement | Récupère looks for others. |

#### `GetLooksLatest`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksPagerContainer.as`, `LooksContentService.as` |
| Fonctionnement | Récupère looks latest. |

#### `GetLooksLatestByFriends`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksPagerContainer.as`, `LooksContentService.as` |
| Fonctionnement | Récupère looks latest by friends. |

#### `GetLooksLatestByMeAndFriends`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| Fonctionnement | Récupère looks latest by me and friends. |

#### `GetLooksLikedByMe`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksPagerContainer.as`, `LooksContentService.as` |
| Fonctionnement | Récupère looks liked by me. |

#### `GetLooksTopAll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksPagerContainer.as`, `LooksContentService.as` |
| Fonctionnement | Top looks communauté paginé (10/page). |

#### `GetLooksTopByFriends`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksContentService.as` |
| Fonctionnement | Récupère looks top by friends. |

#### `GetLooksTopByMeAndFriends`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksPagerContainer.as`, `LooksContentService.as` |
| Fonctionnement | Récupère looks top by me and friends. |

#### `GetRandomLookByLikes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | poolSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `ChecksumCalculator.as`, `FrontPage2.as` |
| Fonctionnement | Récupère random look by likes. |

#### `LookDelete`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | lookId, this.actorModel.actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Succès objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LookListItemComponent.as`, `LookSocialListItemRenderer.as`, `LooksGridItemRenderer.as`, `LooksViewerDeleteCommand.as` |
| Fonctionnement | Supprime un look. |

#### `SaveLookAndData`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | look, clotheIds[], snapshot, fullSnapshot |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Succès objet `{lookId, awardedFame}` ; CanWearOwnLook → booléen |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| Fonctionnement | Crée/met à jour un look + snapshots + IDs vêtements ; retourne `lookId`, `awardedFame`. |

#### `SaveSmallLookSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | look, lookSnapshot |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/look/service/LookAMFService.as` |
| UI / appelants | `LooksDisplayView.as` |
| Fonctionnement | Sauvegarde / crée save small look snapshot. |

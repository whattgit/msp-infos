# V.12 — Scrapblog, photos & design

Artbooks, upload photos, design studio.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `LikeScrapBlog` | `AMFScrapBlogService` | `fameEarned` | Oui |
| `LikeImage` | `AMFImageUpload` | `Code` | Oui |

## Codes de réponse

| Code | Signification |
|------|---------------|
| `0` | OK |
| `−1` | Exception |
| `−2` | Quota upload épuisé |
| `−3` | Pas assez diamants |
| `−4` | Image manquante |
| `−5` | Statut invalide |
| `−6` | Like impossible |

## `MobileServices.AMFDesignService`

**Chemin AMF :** `MovieStarPlanet.MobileServices.AMFDesignService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AutoRenameDesign` | param1 | Endpoint AMF `AutoRenameDesign`. | — |
| `BuyDesignCopy` | actorId, designId | Achète design copy. | — |
| `CancelDesignSale` | actorId, desginId | Endpoint AMF `CancelDesignSale`. | — |
| `DeleteDesign` | actorId, designId | Supprime e design. | — |
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds | Récupère clip art new. | — |
| `GetDesignTemplatesPage` | skindId, categories, pageIndex, pageSize | Récupère design templates page. | — |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageid, pagesize | Liste paginée — Paged List Of Category Designs. | — |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageid, pagesize | Liste paginée — Paged List Of Friends Designs. | — |
| `GetPagedListOfMyDesigns` | actorId, pageid, pagesize | Liste paginée — Paged List Of My Designs. | — |
| `GetPagedListOfNewestDesigns` | skinId, pageid, pagesize | Liste paginée — Paged List Of Newest Designs. | — |
| `GetPagedListOfTopDesigns` | skinId, pageIndex, pageSize | Liste paginée — Paged List Of Top Designs. | — |
| `ModeratorDeleteDesigns` | actorId, designId | Endpoint AMF `ModeratorDeleteDesigns`. | — |
| `NumberOfDesignsForSale` | actorId | Endpoint AMF `NumberOfDesignsForSale`. | — |
| `ProduceDesign` | actorId, designId | Endpoint AMF `ProduceDesign`. | — |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 | Sauvegarde / crée save design secure with snapshot. | — |
| `SearchDesign` | searchString, pageid, pagesize | Recherche design. | — |
| `SearchDesigner` | searchString, pageid, pagesize | Recherche designer. | — |
| `SellDesign` | actorId, designId, amount | Endpoint AMF `SellDesign`. | — |

### Détail endpoints

#### `AutoRenameDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `AutoRenameCommand.as` |
| Fonctionnement | Endpoint AMF `AutoRenameDesign`. |

#### `BuyDesignCopy`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyCopyDesignCommand.as` |
| Fonctionnement | Achète design copy. |

#### `CancelDesignSale`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, desginId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `CancelDesignCommand.as` |
| Fonctionnement | Endpoint AMF `CancelDesignSale`. |

#### `DeleteDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as`, `DeleteDesignCommand.as` (+3) |
| Fonctionnement | Supprime e design. |

#### `GetClipArtNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clipArtCategoryId, filterDiamonds |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+2) |
| UI / appelants | `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère clip art new. |

#### `GetDesignTemplatesPage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skindId, categories, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` |
| UI / appelants | `DesignCreatorService.as`, `ShopContentAmfService.as`, `ShopContentProvider.as` |
| Fonctionnement | Récupère design templates page. |

#### `GetPagedListOfCategoryDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, categoryId, pageid, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Category Designs. |

#### `GetPagedListOfFriendsDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, actorId, pageid, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Friends Designs. |

#### `GetPagedListOfMyDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageid, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of My Designs. |

#### `GetPagedListOfNewestDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, pageid, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Newest Designs. |

#### `GetPagedListOfTopDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Top Designs. |

#### `ModeratorDeleteDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DeleteDesignCommand.as`, `ClothesShopDeleteDesignCommand.as` |
| Fonctionnement | Endpoint AMF `ModeratorDeleteDesigns`. |

#### `NumberOfDesignsForSale`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `SellDesignPopupCommand.as` |
| Fonctionnement | Endpoint AMF `NumberOfDesignsForSale`. |

#### `ProduceDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyDesignCommand.as` |
| Fonctionnement | Endpoint AMF `ProduceDesign`. |

#### `SaveDesignSecureWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6, param7, param8 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignCreatorService.as` |
| Fonctionnement | Sauvegarde / crée save design secure with snapshot. |

#### `SearchDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | searchString, pageid, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as` |
| Fonctionnement | Recherche design. |

#### `SearchDesigner`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | searchString, pageid, pagesize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as` |
| Fonctionnement | Recherche designer. |

#### `SellDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId, amount |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerBrowserAppConfig.as`, `SellDesignCommand.as`, `DesignerBrowserPreviewViewMediator.as` (+5) |
| Fonctionnement | Endpoint AMF `SellDesign`. |

## `WebService.DesignStudio.AMFDesignShopWebService`

**Chemin AMF :** `MovieStarPlanet.WebService.DesignStudio.AMFDesignShopWebService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BuyDesignCopy` | actorId, designId | Achète design copy. | — |
| `CancelDesignSale` | param1, param2 | Endpoint AMF `CancelDesignSale`. | — |
| `GetDesignsForSale` | param1, param2, param3 | Récupère designs for sale. | — |
| `NumberOfDesignsForSale` | param1 | Endpoint AMF `NumberOfDesignsForSale`. | — |
| `SellDesign` | param1, param2, param3 | Endpoint AMF `SellDesign`. | — |

### Détail endpoints

#### `BuyDesignCopy`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyCopyDesignCommand.as` |
| Fonctionnement | Achète design copy. |

#### `CancelDesignSale`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `CancelDesignCommand.as` |
| Fonctionnement | Endpoint AMF `CancelDesignSale`. |

#### `GetDesignsForSale`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/designshop/DesignShopAmfService.as` |
| UI / appelants | `ShopContentProvider.as` |
| Fonctionnement | Récupère designs for sale. |

#### `NumberOfDesignsForSale`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `SellDesignPopupCommand.as` |
| Fonctionnement | Endpoint AMF `NumberOfDesignsForSale`. |

#### `SellDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerBrowserAppConfig.as`, `SellDesignCommand.as`, `DesignerBrowserPreviewViewMediator.as` (+5) |
| Fonctionnement | Endpoint AMF `SellDesign`. |

## `WebService.DesignStudio.AMFDesignStudioWebService`

**Chemin AMF :** `MovieStarPlanet.WebService.DesignStudio.AMFDesignStudioWebService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AutoRenameDesign` | param1 | Endpoint AMF `AutoRenameDesign`. | — |
| `DeleteDesign` | actorId, designId | Supprime e design. | — |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageID, pageSize | Liste paginée — Paged List Of Category Designs. | — |
| `GetPagedListOfDesignsFromUser` | actorId, pageId, pageSize | Liste paginée — Paged List Of Designs From User. | — |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageID, pageSize | Liste paginée — Paged List Of Friends Designs. | — |
| `GetPagedListOfMyDesigns` | actorId, pageID, pageSize | Liste paginée — Paged List Of My Designs. | — |
| `GetPagedListOfNewestDesigns` | skinId, pageID, pageSize | Liste paginée — Paged List Of Newest Designs. | — |
| `GetPagedListOfTopDesigns` | skinId, pageID, pageSize | Liste paginée — Paged List Of Top Designs. | — |
| `ModeratorDeleteDesigns` | actorId, designId | Endpoint AMF `ModeratorDeleteDesigns`. | — |
| `ProduceDesign` | actorId, designId | Endpoint AMF `ProduceDesign`. | — |
| `RenameDesign` | param1, param2, param3 | Endpoint AMF `RenameDesign`. | — |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 | Sauvegarde / crée save design secure with snapshot. | — |
| `SearchDesign` | searchString, pageID, pageSize | Recherche design. | — |
| `SearchDesigner` | searchString, pageID, pageSize | Recherche designer. | — |

### Détail endpoints

#### `AutoRenameDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `AutoRenameCommand.as` |
| Fonctionnement | Endpoint AMF `AutoRenameDesign`. |

#### `DeleteDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as`, `DeleteDesignCommand.as` (+3) |
| Fonctionnement | Supprime e design. |

#### `GetPagedListOfCategoryDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, categoryId, pageID, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Category Designs. |

#### `GetPagedListOfDesignsFromUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageId, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` |
| UI / appelants | `WallList.as` |
| Fonctionnement | Liste paginée — Paged List Of Designs From User. |

#### `GetPagedListOfFriendsDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, actorId, pageID, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Friends Designs. |

#### `GetPagedListOfMyDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageID, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of My Designs. |

#### `GetPagedListOfNewestDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, pageID, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Newest Designs. |

#### `GetPagedListOfTopDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | skinId, pageID, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Fonctionnement | Liste paginée — Paged List Of Top Designs. |

#### `ModeratorDeleteDesigns`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DeleteDesignCommand.as`, `ClothesShopDeleteDesignCommand.as` |
| Fonctionnement | Endpoint AMF `ModeratorDeleteDesigns`. |

#### `ProduceDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, designId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyDesignCommand.as` |
| Fonctionnement | Endpoint AMF `ProduceDesign`. |

#### `RenameDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` |
| UI / appelants | `DesignerBrowserPreviewViewBase.as` |
| Fonctionnement | Endpoint AMF `RenameDesign`. |

#### `SaveDesignSecureWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6, param7, param8 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignCreatorService.as` |
| Fonctionnement | Sauvegarde / crée save design secure with snapshot. |

#### `SearchDesign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | searchString, pageID, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as` |
| Fonctionnement | Recherche design. |

#### `SearchDesigner`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | searchString, pageID, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / appelants | `DesignerContentService.as`, `DesignerContentServiceTablet.as` |
| Fonctionnement | Recherche designer. |

## `WebService.ImageUpload.AMFImageUpload`

**Chemin AMF :** `MovieStarPlanet.WebService.ImageUpload.AMFImageUpload`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AddView` | param1, param2 | Endpoint AMF `AddView`. | — |
| `DeleteImage` | param1, param2 | Supprime e image. | — |
| `EditHeadline` | param1, param2, param3, param4 | Endpoint AMF `EditHeadline`. | — |
| `EditHeadlineMod` | param1, param2 | Endpoint AMF `EditHeadlineMod`. | — |
| `EditStatusMod` | (id, -2) · (param1, param2) | Endpoint AMF `EditStatusMod`. | — |
| `GetFriendsUploads` | param1, param2, param3 | Récupère friends uploads. | — |
| `GetModSearch` | param1, param2, param3 | Récupère mod search. | — |
| `GetMyUploads` | param1, param2, param3 | Récupère my uploads. | — |
| `GetMyUploadsForArtbook` | param1 | Récupère my uploads for artbook. | — |
| `GetNewUploads` | param1, param2, param3 | Récupère new uploads. | — |
| `GetRemainingUploadCount` | param1, param2 | Quota photos restantes (VIP/non-VIP). | — |
| `GetSingleImage` | param1, param2 | Récupère single image. | — |
| `GetSingleImageModerator` | param1 | Récupère single image moderator. | — |
| `GetSingleImageWithGuid` | param1, param2 | Récupère single image with guid. | — |
| `GetSingleImageWithGuidModerator` | param1 | Récupère single image with guid moderator. | — |
| `GetTopUploads` | param1, param2, param3 | Récupère top uploads. | — |
| `GetUploadsFromUser` | param1, param2, param3 | Récupère uploads from user. | — |
| `GetUserUploads` | param1, param2, param3 | Récupère user uploads. | — |
| `LikeImage` | actorId, imageUploadId | Like photo ; `Code==-429` rate limit. | `-429` |
| `PollImages` | param1 | Endpoint AMF `PollImages`. | — |
| `PurchaseUpload` | param1 | Endpoint AMF `PurchaseUpload`. | — |
| `SearchFriendsUploads` | param1, param2, param3, param4 | Recherche friends uploads. | — |
| `SetPhotoUploadRulesAccepted` | param1 | Met à jour photo upload rules accepted. | — |
| `UploadImageWithSnapshot` | param1, param2, _loc5_, param3 | Upload photo modérée ; quota GetRemainingUploadCount ; codes -2/-3. | — |

### Détail endpoints

#### `AddView`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `MessagingController.as`, `AddImageView.as`, `MediatorMapExtension.as`, `ViewProcessorMapExtension.as` |
| Fonctionnement | Endpoint AMF `AddView`. |

#### `DeleteImage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `ReportsForm.as`, `PhotoSocialListItemRenderer.as`, `BaseConfiguration.as`, `DeleteImageCommand.as` (+1) |
| Fonctionnement | Supprime e image. |

#### `EditHeadline`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PicturePresentationView.as`, `PlaylistSubRenderer.as` |
| Fonctionnement | Endpoint AMF `EditHeadline`. |

#### `EditHeadlineMod`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| Fonctionnement | Endpoint AMF `EditHeadlineMod`. |

#### `EditStatusMod`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (id, -2) · (param1, param2) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/Components/Profile/ReportsFormLogic.as` (+1) |
| UI / appelants | `PhotoSocialListItemRenderer.as`, `DeleteImageCommand.as` |
| Fonctionnement | Endpoint AMF `EditStatusMod`. |

#### `GetFriendsUploads`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureContentProvider.as` |
| Fonctionnement | Récupère friends uploads. |

#### `GetModSearch`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureContentProvider.as`, `PictureUploadModel.as` |
| Fonctionnement | Récupère mod search. |

#### `GetMyUploads`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `InventoryLoader.as`, `ContentLoader.as`, `PictureContentProvider.as` |
| Fonctionnement | Récupère my uploads. |

#### `GetMyUploadsForArtbook`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `InventoryLoader.as`, `ContentLoader.as` |
| Fonctionnement | Récupère my uploads for artbook. |

#### `GetNewUploads`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureContentProvider.as`, `PictureUploadModel.as` |
| Fonctionnement | Récupère new uploads. |

#### `GetRemainingUploadCount`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureUploadModel.as` |
| Fonctionnement | Quota photos restantes (VIP/non-VIP). |

#### `GetSingleImage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PendingPicturesChecker.as`, `ApplicationView.as`, `Favorites.as` |
| Fonctionnement | Récupère single image. |

#### `GetSingleImageModerator`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `ApplicationView.as` |
| Fonctionnement | Récupère single image moderator. |

#### `GetSingleImageWithGuid`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `ApplicationView.as` |
| Fonctionnement | Récupère single image with guid. |

#### `GetSingleImageWithGuidModerator`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `ApplicationView.as` |
| Fonctionnement | Récupère single image with guid moderator. |

#### `GetTopUploads`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureContentProvider.as`, `PictureUploadModel.as` |
| Fonctionnement | Récupère top uploads. |

#### `GetUploadsFromUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureContentProvider.as` |
| Fonctionnement | Récupère uploads from user. |

#### `GetUserUploads`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureContentProvider.as` |
| Fonctionnement | Récupère user uploads. |

#### `LikeImage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, imageUploadId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `Code` (popup) |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PicturePresentationView.as` |
| Fonctionnement | Like photo ; `Code==-429` rate limit. |

#### `PollImages`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PendingPicturesChecker.as` |
| Fonctionnement | Endpoint AMF `PollImages`. |

#### `PurchaseUpload`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| Fonctionnement | Endpoint AMF `PurchaseUpload`. |

#### `SearchFriendsUploads`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PictureContentProvider.as` |
| Fonctionnement | Recherche friends uploads. |

#### `SetPhotoUploadRulesAccepted`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `PhotoSourceSelectorWeb.as`, `PictureUploadUtils.as` |
| Fonctionnement | Met à jour photo upload rules accepted. |

#### `UploadImageWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, _loc5_, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| Client AMF | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / appelants | `UploadImageCommand.as` |
| Fonctionnement | Upload photo modérée ; quota GetRemainingUploadCount ; codes -2/-3. |

## `WebService.ScrapBlog.AMFClipArtService`

**Chemin AMF :** `MovieStarPlanet.WebService.ScrapBlog.AMFClipArtService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds | Récupère clip art new. | — |

### Détail endpoints

#### `GetClipArtNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clipArtCategoryId, filterDiamonds |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapitems/service/ClipArtAMFService.as` (+2) |
| UI / appelants | `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère clip art new. |

## `WebService.ScrapBlog.AMFScrapBlogService`

**Chemin AMF :** `MovieStarPlanet.WebService.ScrapBlog.AMFScrapBlogService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AdminDeleteScrapBlog` | param1, param2, param3 | Endpoint AMF `AdminDeleteScrapBlog`. | — |
| `DeleteScrapBlog` | param1, param2 | Supprime e scrap blog. | — |
| `GetClipArtCategories` | — | Récupère clip art categories. | — |
| `GetClipArtNew` | param1, param2 | Récupère clip art new. | — |
| `GetFriendsScrapBlogs` | param1, param2, param3 | Récupère friends scrap blogs. | — |
| `GetFriendsScrapBlogsBatched` | param1, param2 | Récupère friends scrap blogs batched. | — |
| `GetHighscoreScrapBlogs` | param1, param2, param3, param4, param5, param6 | Récupère highscore scrap blogs. | — |
| `GetNewestScrapBlogs` | param1, param2 | Récupère newest scrap blogs. | — |
| `GetPrivateScrapBlogs` | param1, param2, param3 | Récupère private scrap blogs. | — |
| `GetScrapBlogsBySearch` | _loc3_, _loc5_, _loc6_, _loc4_ | Récupère scrap blogs by search. | — |
| `GetScrapBlogsByType` | param1, param2, param3 | Récupère scrap blogs by type. | — |
| `GetScrapBlogsByUser` | param1, param2, param3 | Récupère scrap blogs by user. | — |
| `GetScrapBlogsFriendsLiked` | param1, param2, param3 | Récupère scrap blogs friends liked. | — |
| `GetSubmissibleScrapBlogs` | param1, param2, param3 | Récupère submissible scrap blogs. | — |
| `LikeScrapBlog` | actorId, scrapBlogId, ownerId | Like artbook ; `fameEarned==-429` rate limit. | `-429` |
| `LoadScrapBlog` | param1, param2 | Charge scrap blog. | — |
| `LoadTemplateByType` | param1 | Charge template by type. | — |
| `ReplicateScrapblog` | param1, param2 | Endpoint AMF `ReplicateScrapblog`. | — |
| `SaveScrapBlogWithSnapshot` | actorId, scrapBlog, snapshotSmall, snapshotBig | Sauvegarde artbook + snapshots ; modération titre/contenu. | — |
| `SetArtbookRulesAccepted` | param1 | Met à jour artbook rules accepted. | — |

### Détail endpoints

#### `AdminDeleteScrapBlog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtbookGridItemRenderer.as`, `ArtBookViewerDeleteCommand.as`, `ArtbookContentListItemRenderer.as`, `ScrapBlogSocialListItemRenderer.as` (+5) |
| Fonctionnement | Endpoint AMF `AdminDeleteScrapBlog`. |

#### `DeleteScrapBlog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ReportsForm.as`, `ArtBookViewerFrame.as`, `ArtbookContentListItemRenderer.as`, `ScrapBlogSocialListItemRenderer.as` (+4) |
| Fonctionnement | Supprime e scrap blog. |

#### `GetClipArtCategories`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ScrapBlogItemBrowser.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère clip art categories. |

#### `GetClipArtNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` (+2) |
| UI / appelants | `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère clip art new. |

#### `GetFriendsScrapBlogs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowserHelpers.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère friends scrap blogs. |

#### `GetFriendsScrapBlogsBatched`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère friends scrap blogs batched. |

#### `GetHighscoreScrapBlogs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4, param5, param6 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookBrowserHelpers.as`, `HighscoreScrapBlog.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère highscore scrap blogs. |

#### `GetNewestScrapBlogs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère newest scrap blogs. |

#### `GetPrivateScrapBlogs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowserHelpers.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère private scrap blogs. |

#### `GetScrapBlogsBySearch`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | _loc3_, _loc5_, _loc6_, _loc4_ |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowser.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère scrap blogs by search. |

#### `GetScrapBlogsByType`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère scrap blogs by type. |

#### `GetScrapBlogsByUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `PersonalContentList.as`, `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `Pager.as` (+4) |
| Fonctionnement | Récupère scrap blogs by user. |

#### `GetScrapBlogsFriendsLiked`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowserHelpers.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère scrap blogs friends liked. |

#### `GetSubmissibleScrapBlogs`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `SubmitScrapBlogToCompetition.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Récupère submissible scrap blogs. |

#### `LikeScrapBlog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, scrapBlogId, ownerId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `fameEarned` (popup) |
| Codes retour | Champ `fameEarned` == −429 (popup) |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookViewerFrame.as`, `ScrapBlogEditor.as`, `ScrapBlogController.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Like artbook ; `fameEarned==-429` rate limit. |

#### `LoadScrapBlog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ClubUtils.as`, `ArtBookLoader.as`, `NewsLoader.as`, `ScrapBlogEditor.as` (+6) |
| Fonctionnement | Charge scrap blog. |

#### `LoadTemplateByType`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ArtBookManager.as`, `ArtBookContentService.as`, `ScrapBlogEditor.as`, `ScrapBlogProvider.as` (+1) |
| Fonctionnement | Charge template by type. |

#### `ReplicateScrapblog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ScrapBlogPublisher.as`, `ScrapBlogAMFHelper.as` |
| Fonctionnement | Endpoint AMF `ReplicateScrapblog`. |

#### `SaveScrapBlogWithSnapshot`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, scrapBlog, snapshotSmall, snapshotBig |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ClubUtils.as`, `ArtBookCreatorSaveCommand.as`, `ArtBookContentService.as`, `ScrapBlogEditor.as` (+2) |
| Fonctionnement | Sauvegarde artbook + snapshots ; modération titre/contenu. |

#### `SetArtbookRulesAccepted`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / appelants | `ScrapBlogAMFHelper.as` |
| Fonctionnement | Met à jour artbook rules accepted. |

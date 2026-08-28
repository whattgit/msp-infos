# III.12 — Scrapblog, photos & design

> **EN** · [Français](../../fr/amf/12-content.md)


Artbooks, photo upload, design studio.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `LikeScrapBlog` | `AMFScrapBlogService` | `fameEarned` | Yes |
| `LikeImage` | `AMFImageUpload` | `Code` | Yes |

## Response codes

| Code | Meaning |
|------|---------------|
| `0` | OK |
| `−1` | Exception |
| `−2` | Upload quota exhausted |
| `−3` | Not enough diamonds |
| `−4` | Missing image |
| `−5` | Invalid status |
| `−6` | Like impossible |

## `MobileServices.AMFDesignService`

**AMF path:** `MovieStarPlanet.MobileServices.AMFDesignService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AutoRenameDesign` | param1 | AMF endpoint `AutoRenameDesign`. | — |
| `BuyDesignCopy` | actorId, designId | Buys design copy. | — |
| `CancelDesignSale` | actorId, desginId | AMF endpoint `CancelDesignSale`. | — |
| `DeleteDesign` | actorId, designId | Deletes e design. | — |
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds | Fetches clip art new. | — |
| `GetDesignTemplatesPage` | skindId, categories, pageIndex, pageSize | Fetches design templates page. | — |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageid, pagesize | Paged list — Paged List Of Category Designs. | — |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageid, pagesize | Paged list — Paged List Of Friends Designs. | — |
| `GetPagedListOfMyDesigns` | actorId, pageid, pagesize | Paged list — Paged List Of My Designs. | — |
| `GetPagedListOfNewestDesigns` | skinId, pageid, pagesize | Paged list — Paged List Of Newest Designs. | — |
| `GetPagedListOfTopDesigns` | skinId, pageIndex, pageSize | Paged list — Paged List Of Top Designs. | — |
| `ModeratorDeleteDesigns` | actorId, designId | AMF endpoint `ModeratorDeleteDesigns`. | — |
| `NumberOfDesignsForSale` | actorId | AMF endpoint `NumberOfDesignsForSale`. | — |
| `ProduceDesign` | actorId, designId | AMF endpoint `ProduceDesign`. | — |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 | Saves / creates save design secure with snapshot. | — |
| `SearchDesign` | searchString, pageid, pagesize | Searches design. | — |
| `SearchDesigner` | searchString, pageid, pagesize | Searches designer. | — |
| `SellDesign` | actorId, designId, amount | AMF endpoint `SellDesign`. | — |

### Endpoint details

#### `AutoRenameDesign`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `AutoRenameCommand.as` |
| Behavior | AMF endpoint `AutoRenameDesign`. |

#### `BuyDesignCopy`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyCopyDesignCommand.as` |
| Behavior | Buys design copy. |

#### `CancelDesignSale`

| Property | Value |
|----------|-------|
| Parameters | actorId, desginId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `CancelDesignCommand.as` |
| Behavior | AMF endpoint `CancelDesignSale`. |

#### `DeleteDesign`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as`, `DeleteDesignCommand.as` (+3) |
| Behavior | Deletes e design. |

#### `GetClipArtNew`

| Property | Value |
|----------|-------|
| Parameters | clipArtCategoryId, filterDiamonds |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+2) |
| UI / callers | `ScrapBlogAMFHelper.as` |
| Behavior | Fetches clip art new. |

#### `GetDesignTemplatesPage`

| Property | Value |
|----------|-------|
| Parameters | skindId, categories, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` |
| UI / callers | `DesignCreatorService.as`, `ShopContentAmfService.as`, `ShopContentProvider.as` |
| Behavior | Fetches design templates page. |

#### `GetPagedListOfCategoryDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, categoryId, pageid, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Category Designs. |

#### `GetPagedListOfFriendsDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, actorId, pageid, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Friends Designs. |

#### `GetPagedListOfMyDesigns`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageid, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of My Designs. |

#### `GetPagedListOfNewestDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, pageid, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Newest Designs. |

#### `GetPagedListOfTopDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Top Designs. |

#### `ModeratorDeleteDesigns`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DeleteDesignCommand.as`, `ClothesShopDeleteDesignCommand.as` |
| Behavior | AMF endpoint `ModeratorDeleteDesigns`. |

#### `NumberOfDesignsForSale`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `SellDesignPopupCommand.as` |
| Behavior | AMF endpoint `NumberOfDesignsForSale`. |

#### `ProduceDesign`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyDesignCommand.as` |
| Behavior | AMF endpoint `ProduceDesign`. |

#### `SaveDesignSecureWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6, param7, param8 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignCreatorService.as` |
| Behavior | Saves / creates save design secure with snapshot. |

#### `SearchDesign`

| Property | Value |
|----------|-------|
| Parameters | searchString, pageid, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as` |
| Behavior | Searches design. |

#### `SearchDesigner`

| Property | Value |
|----------|-------|
| Parameters | searchString, pageid, pagesize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as` |
| Behavior | Searches designer. |

#### `SellDesign`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId, amount |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignAMFServiceMobile.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerBrowserAppConfig.as`, `SellDesignCommand.as`, `DesignerBrowserPreviewViewMediator.as` (+5) |
| Behavior | AMF endpoint `SellDesign`. |

## `WebService.DesignStudio.AMFDesignShopWebService`

**AMF path:** `MovieStarPlanet.WebService.DesignStudio.AMFDesignShopWebService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BuyDesignCopy` | actorId, designId | Buys design copy. | — |
| `CancelDesignSale` | param1, param2 | AMF endpoint `CancelDesignSale`. | — |
| `GetDesignsForSale` | param1, param2, param3 | Fetches designs for sale. | — |
| `NumberOfDesignsForSale` | param1 | AMF endpoint `NumberOfDesignsForSale`. | — |
| `SellDesign` | param1, param2, param3 | AMF endpoint `SellDesign`. | — |

### Endpoint details

#### `BuyDesignCopy`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyCopyDesignCommand.as` |
| Behavior | Buys design copy. |

#### `CancelDesignSale`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `CancelDesignCommand.as` |
| Behavior | AMF endpoint `CancelDesignSale`. |

#### `GetDesignsForSale`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/designshop/DesignShopAmfService.as` |
| UI / callers | `ShopContentProvider.as` |
| Behavior | Fetches designs for sale. |

#### `NumberOfDesignsForSale`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `SellDesignPopupCommand.as` |
| Behavior | AMF endpoint `NumberOfDesignsForSale`. |

#### `SellDesign`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignShopAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerBrowserAppConfig.as`, `SellDesignCommand.as`, `DesignerBrowserPreviewViewMediator.as` (+5) |
| Behavior | AMF endpoint `SellDesign`. |

## `WebService.DesignStudio.AMFDesignStudioWebService`

**AMF path:** `MovieStarPlanet.WebService.DesignStudio.AMFDesignStudioWebService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AutoRenameDesign` | param1 | AMF endpoint `AutoRenameDesign`. | — |
| `DeleteDesign` | actorId, designId | Deletes e design. | — |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageID, pageSize | Paged list — Paged List Of Category Designs. | — |
| `GetPagedListOfDesignsFromUser` | actorId, pageId, pageSize | Paged list — Paged List Of Designs From User. | — |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageID, pageSize | Paged list — Paged List Of Friends Designs. | — |
| `GetPagedListOfMyDesigns` | actorId, pageID, pageSize | Paged list — Paged List Of My Designs. | — |
| `GetPagedListOfNewestDesigns` | skinId, pageID, pageSize | Paged list — Paged List Of Newest Designs. | — |
| `GetPagedListOfTopDesigns` | skinId, pageID, pageSize | Paged list — Paged List Of Top Designs. | — |
| `ModeratorDeleteDesigns` | actorId, designId | AMF endpoint `ModeratorDeleteDesigns`. | — |
| `ProduceDesign` | actorId, designId | AMF endpoint `ProduceDesign`. | — |
| `RenameDesign` | param1, param2, param3 | AMF endpoint `RenameDesign`. | — |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 | Saves / creates save design secure with snapshot. | — |
| `SearchDesign` | searchString, pageID, pageSize | Searches design. | — |
| `SearchDesigner` | searchString, pageID, pageSize | Searches designer. | — |

### Endpoint details

#### `AutoRenameDesign`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `AutoRenameCommand.as` |
| Behavior | AMF endpoint `AutoRenameDesign`. |

#### `DeleteDesign`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as`, `DeleteDesignCommand.as` (+3) |
| Behavior | Deletes e design. |

#### `GetPagedListOfCategoryDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, categoryId, pageID, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Category Designs. |

#### `GetPagedListOfDesignsFromUser`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageId, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` |
| UI / callers | `WallList.as` |
| Behavior | Paged list — Paged List Of Designs From User. |

#### `GetPagedListOfFriendsDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, actorId, pageID, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Friends Designs. |

#### `GetPagedListOfMyDesigns`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageID, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of My Designs. |

#### `GetPagedListOfNewestDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, pageID, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Newest Designs. |

#### `GetPagedListOfTopDesigns`

| Property | Value |
|----------|-------|
| Parameters | skinId, pageID, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserPagers.as` |
| Behavior | Paged list — Paged List Of Top Designs. |

#### `ModeratorDeleteDesigns`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DeleteDesignCommand.as`, `ClothesShopDeleteDesignCommand.as` |
| Behavior | AMF endpoint `ModeratorDeleteDesigns`. |

#### `ProduceDesign`

| Property | Value |
|----------|-------|
| Parameters | actorId, designId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `BuyDesignCommand.as` |
| Behavior | AMF endpoint `ProduceDesign`. |

#### `RenameDesign`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` |
| UI / callers | `DesignerBrowserPreviewViewBase.as` |
| Behavior | AMF endpoint `RenameDesign`. |

#### `SaveDesignSecureWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6, param7, param8 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignCreatorService.as` |
| Behavior | Saves / creates save design secure with snapshot. |

#### `SearchDesign`

| Property | Value |
|----------|-------|
| Parameters | searchString, pageID, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as`, `DesignerBrowserAppConfig.as` |
| Behavior | Searches design. |

#### `SearchDesigner`

| Property | Value |
|----------|-------|
| Parameters | searchString, pageID, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/design/service/DesignStudioAmfServiceWeb.as` (+1) |
| UI / callers | `DesignerContentService.as`, `DesignerContentServiceTablet.as` |
| Behavior | Searches designer. |

## `WebService.ImageUpload.AMFImageUpload`

**AMF path:** `MovieStarPlanet.WebService.ImageUpload.AMFImageUpload`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AddView` | param1, param2 | AMF endpoint `AddView`. | — |
| `DeleteImage` | param1, param2 | Deletes e image. | — |
| `EditHeadline` | param1, param2, param3, param4 | AMF endpoint `EditHeadline`. | — |
| `EditHeadlineMod` | param1, param2 | AMF endpoint `EditHeadlineMod`. | — |
| `EditStatusMod` | (id, -2) · (param1, param2) | AMF endpoint `EditStatusMod`. | — |
| `GetFriendsUploads` | param1, param2, param3 | Fetches friends uploads. | — |
| `GetModSearch` | param1, param2, param3 | Fetches mod search. | — |
| `GetMyUploads` | param1, param2, param3 | Fetches my uploads. | — |
| `GetMyUploadsForArtbook` | param1 | Fetches my uploads for artbook. | — |
| `GetNewUploads` | param1, param2, param3 | Fetches new uploads. | — |
| `GetRemainingUploadCount` | param1, param2 | Quota photos restantes (VIP/non-VIP). | — |
| `GetSingleImage` | param1, param2 | Fetches single image. | — |
| `GetSingleImageModerator` | param1 | Fetches single image moderator. | — |
| `GetSingleImageWithGuid` | param1, param2 | Fetches single image with guid. | — |
| `GetSingleImageWithGuidModerator` | param1 | Fetches single image with guid moderator. | — |
| `GetTopUploads` | param1, param2, param3 | Fetches top uploads. | — |
| `GetUploadsFromUser` | param1, param2, param3 | Fetches uploads from user. | — |
| `GetUserUploads` | param1, param2, param3 | Fetches user uploads. | — |
| `LikeImage` | actorId, imageUploadId | Like photo ; `Code==-429` rate limit. | `-429` |
| `PollImages` | param1 | AMF endpoint `PollImages`. | — |
| `PurchaseUpload` | param1 | AMF endpoint `PurchaseUpload`. | — |
| `SearchFriendsUploads` | param1, param2, param3, param4 | Searches friends uploads. | — |
| `SetPhotoUploadRulesAccepted` | param1 | Updates photo upload rules accepted. | — |
| `UploadImageWithSnapshot` | param1, param2, _loc5_, param3 | Upload photo modérée ; quota GetRemainingUploadCount ; codes -2/-3. | — |

### Endpoint details

#### `AddView`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `MessagingController.as`, `AddImageView.as`, `MediatorMapExtension.as`, `ViewProcessorMapExtension.as` |
| Behavior | AMF endpoint `AddView`. |

#### `DeleteImage`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `ReportsForm.as`, `PhotoSocialListItemRenderer.as`, `BaseConfiguration.as`, `DeleteImageCommand.as` (+1) |
| Behavior | Deletes e image. |

#### `EditHeadline`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PicturePresentationView.as`, `PlaylistSubRenderer.as` |
| Behavior | AMF endpoint `EditHeadline`. |

#### `EditHeadlineMod`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| Behavior | AMF endpoint `EditHeadlineMod`. |

#### `EditStatusMod`

| Property | Value |
|----------|-------|
| Parameters | (id, -2) · (param1, param2) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/Components/Profile/ReportsFormLogic.as` (+1) |
| UI / callers | `PhotoSocialListItemRenderer.as`, `DeleteImageCommand.as` |
| Behavior | AMF endpoint `EditStatusMod`. |

#### `GetFriendsUploads`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureContentProvider.as` |
| Behavior | Fetches friends uploads. |

#### `GetModSearch`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureContentProvider.as`, `PictureUploadModel.as` |
| Behavior | Fetches mod search. |

#### `GetMyUploads`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `InventoryLoader.as`, `ContentLoader.as`, `PictureContentProvider.as` |
| Behavior | Fetches my uploads. |

#### `GetMyUploadsForArtbook`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `InventoryLoader.as`, `ContentLoader.as` |
| Behavior | Fetches my uploads for artbook. |

#### `GetNewUploads`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureContentProvider.as`, `PictureUploadModel.as` |
| Behavior | Fetches new uploads. |

#### `GetRemainingUploadCount`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureUploadModel.as` |
| Behavior | Quota photos restantes (VIP/non-VIP). |

#### `GetSingleImage`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PendingPicturesChecker.as`, `ApplicationView.as`, `Favorites.as` |
| Behavior | Fetches single image. |

#### `GetSingleImageModerator`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `ApplicationView.as` |
| Behavior | Fetches single image moderator. |

#### `GetSingleImageWithGuid`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `ApplicationView.as` |
| Behavior | Fetches single image with guid. |

#### `GetSingleImageWithGuidModerator`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `ApplicationView.as` |
| Behavior | Fetches single image with guid moderator. |

#### `GetTopUploads`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureContentProvider.as`, `PictureUploadModel.as` |
| Behavior | Fetches top uploads. |

#### `GetUploadsFromUser`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureContentProvider.as` |
| Behavior | Fetches uploads from user. |

#### `GetUserUploads`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureContentProvider.as` |
| Behavior | Fetches user uploads. |

#### `LikeImage`

| Property | Value |
|----------|-------|
| Parameters | actorId, imageUploadId |
| AMF ticket | Yes |
| Rate limit | `-429` on `Code` (popup) |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PicturePresentationView.as` |
| Behavior | Like photo ; `Code==-429` rate limit. |

#### `PollImages`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PendingPicturesChecker.as` |
| Behavior | AMF endpoint `PollImages`. |

#### `PurchaseUpload`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| Behavior | AMF endpoint `PurchaseUpload`. |

#### `SearchFriendsUploads`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PictureContentProvider.as` |
| Behavior | Searches friends uploads. |

#### `SetPhotoUploadRulesAccepted`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `PhotoSourceSelectorWeb.as`, `PictureUploadUtils.as` |
| Behavior | Updates photo upload rules accepted. |

#### `UploadImageWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, _loc5_, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `ImageUploadResponse.Code` : 0 · −1 · −2 quota · −3 💎 · −4 image · −5 statut · −6 like · −429 |
| AMF client | `com/moviestarplanet/imageupload/service/AMFPictureUploadService.as` |
| UI / callers | `UploadImageCommand.as` |
| Behavior | Upload photo modérée ; quota GetRemainingUploadCount ; codes -2/-3. |

## `WebService.ScrapBlog.AMFClipArtService`

**AMF path:** `MovieStarPlanet.WebService.ScrapBlog.AMFClipArtService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds | Fetches clip art new. | — |

### Endpoint details

#### `GetClipArtNew`

| Property | Value |
|----------|-------|
| Parameters | clipArtCategoryId, filterDiamonds |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapitems/service/ClipArtAMFService.as` (+2) |
| UI / callers | `ScrapBlogAMFHelper.as` |
| Behavior | Fetches clip art new. |

## `WebService.ScrapBlog.AMFScrapBlogService`

**AMF path:** `MovieStarPlanet.WebService.ScrapBlog.AMFScrapBlogService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AdminDeleteScrapBlog` | param1, param2, param3 | AMF endpoint `AdminDeleteScrapBlog`. | — |
| `DeleteScrapBlog` | param1, param2 | Deletes e scrap blog. | — |
| `GetClipArtCategories` | — | Fetches clip art categories. | — |
| `GetClipArtNew` | param1, param2 | Fetches clip art new. | — |
| `GetFriendsScrapBlogs` | param1, param2, param3 | Fetches friends scrap blogs. | — |
| `GetFriendsScrapBlogsBatched` | param1, param2 | Fetches friends scrap blogs batched. | — |
| `GetHighscoreScrapBlogs` | param1, param2, param3, param4, param5, param6 | Fetches highscore scrap blogs. | — |
| `GetNewestScrapBlogs` | param1, param2 | Fetches newest scrap blogs. | — |
| `GetPrivateScrapBlogs` | param1, param2, param3 | Fetches private scrap blogs. | — |
| `GetScrapBlogsBySearch` | _loc3_, _loc5_, _loc6_, _loc4_ | Fetches scrap blogs by search. | — |
| `GetScrapBlogsByType` | param1, param2, param3 | Fetches scrap blogs by type. | — |
| `GetScrapBlogsByUser` | param1, param2, param3 | Fetches scrap blogs by user. | — |
| `GetScrapBlogsFriendsLiked` | param1, param2, param3 | Fetches scrap blogs friends liked. | — |
| `GetSubmissibleScrapBlogs` | param1, param2, param3 | Fetches submissible scrap blogs. | — |
| `LikeScrapBlog` | actorId, scrapBlogId, ownerId | Like artbook ; `fameEarned==-429` rate limit. | `-429` |
| `LoadScrapBlog` | param1, param2 | Loads scrap blog. | — |
| `LoadTemplateByType` | param1 | Loads template by type. | — |
| `ReplicateScrapblog` | param1, param2 | AMF endpoint `ReplicateScrapblog`. | — |
| `SaveScrapBlogWithSnapshot` | actorId, scrapBlog, snapshotSmall, snapshotBig | Sauvegarde artbook + snapshots ; modération titre/contenu. | — |
| `SetArtbookRulesAccepted` | param1 | Updates artbook rules accepted. | — |

### Endpoint details

#### `AdminDeleteScrapBlog`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtbookGridItemRenderer.as`, `ArtBookViewerDeleteCommand.as`, `ArtbookContentListItemRenderer.as`, `ScrapBlogSocialListItemRenderer.as` (+5) |
| Behavior | AMF endpoint `AdminDeleteScrapBlog`. |

#### `DeleteScrapBlog`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ReportsForm.as`, `ArtBookViewerFrame.as`, `ArtbookContentListItemRenderer.as`, `ScrapBlogSocialListItemRenderer.as` (+4) |
| Behavior | Deletes e scrap blog. |

#### `GetClipArtCategories`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ScrapBlogItemBrowser.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches clip art categories. |

#### `GetClipArtNew`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` (+2) |
| UI / callers | `ScrapBlogAMFHelper.as` |
| Behavior | Fetches clip art new. |

#### `GetFriendsScrapBlogs`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowserHelpers.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches friends scrap blogs. |

#### `GetFriendsScrapBlogsBatched`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ScrapBlogAMFHelper.as` |
| Behavior | Fetches friends scrap blogs batched. |

#### `GetHighscoreScrapBlogs`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4, param5, param6 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookBrowserHelpers.as`, `HighscoreScrapBlog.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches highscore scrap blogs. |

#### `GetNewestScrapBlogs`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches newest scrap blogs. |

#### `GetPrivateScrapBlogs`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowserHelpers.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches private scrap blogs. |

#### `GetScrapBlogsBySearch`

| Property | Value |
|----------|-------|
| Parameters | _loc3_, _loc5_, _loc6_, _loc4_ |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowser.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches scrap blogs by search. |

#### `GetScrapBlogsByType`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ScrapBlogAMFHelper.as` |
| Behavior | Fetches scrap blogs by type. |

#### `GetScrapBlogsByUser`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `PersonalContentList.as`, `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `Pager.as` (+4) |
| Behavior | Fetches scrap blogs by user. |

#### `GetScrapBlogsFriendsLiked`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookPagerContainer.as`, `ArtBookContentService.as`, `ArtBookBrowserHelpers.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches scrap blogs friends liked. |

#### `GetSubmissibleScrapBlogs`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `SubmitScrapBlogToCompetition.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Fetches submissible scrap blogs. |

#### `LikeScrapBlog`

| Property | Value |
|----------|-------|
| Parameters | actorId, scrapBlogId, ownerId |
| AMF ticket | Yes |
| Rate limit | `-429` on `fameEarned` (popup) |
| Return codes | Champ `fameEarned` == −429 (popup) |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookViewerFrame.as`, `ScrapBlogEditor.as`, `ScrapBlogController.as`, `ScrapBlogAMFHelper.as` |
| Behavior | Like artbook ; `fameEarned==-429` rate limit. |

#### `LoadScrapBlog`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ClubUtils.as`, `ArtBookLoader.as`, `NewsLoader.as`, `ScrapBlogEditor.as` (+6) |
| Behavior | Loads scrap blog. |

#### `LoadTemplateByType`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ArtBookManager.as`, `ArtBookContentService.as`, `ScrapBlogEditor.as`, `ScrapBlogProvider.as` (+1) |
| Behavior | Loads template by type. |

#### `ReplicateScrapblog`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ScrapBlogPublisher.as`, `ScrapBlogAMFHelper.as` |
| Behavior | AMF endpoint `ReplicateScrapblog`. |

#### `SaveScrapBlogWithSnapshot`

| Property | Value |
|----------|-------|
| Parameters | actorId, scrapBlog, snapshotSmall, snapshotBig |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ClubUtils.as`, `ArtBookCreatorSaveCommand.as`, `ArtBookContentService.as`, `ScrapBlogEditor.as` (+2) |
| Behavior | Sauvegarde artbook + snapshots ; modération titre/contenu. |

#### `SetArtbookRulesAccepted`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/scrapblog/service/ScrapBlogAMFService.as` |
| UI / callers | `ScrapBlogAMFHelper.as` |
| Behavior | Updates artbook rules accepted. |

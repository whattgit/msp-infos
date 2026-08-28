# III.11 — Gifts

> **EN** · [Français](../../fr/amf/11-gifts.md)


Send, open, wishlist, trades.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `OpenGift` | `AMFGiftsService` | `GiftLogId` | Yes |

## Response codes

| Code | Meaning |
|------|---------------|
| `0` | OK |
| `−1` | Erreur |
| `−10` | Non-VIP level 6 required |
| `−20` | Daily limit (25/day UI) |
| `−30` | Already owns item |
| `−40` | Cooldown too early |

## `MobileServices.AMFGiftsService+Version2`

**AMF path:** `MovieStarPlanet.MobileServices.AMFGiftsService+Version2`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BuyGift` | senderId, receiverId, giftId, SWF | Buys gift. | — |
| `GetUnifiedActorClothItems` | param1, param2, param3 | Fetches unified actor cloth items. | — |
| `GetUnifiedActorClothesByType` | param1, param2, param3 | Fetches unified actor clothes by type. | — |
| `GetUnifiedGiftsGiven` | param1, param2 | Fetches unified gifts given. | — |
| `GetUnifiedGiftsNew` | param1, param2 | Fetches unified gifts new. | — |
| `GetUnifiedGiftsReceived` | param1, param2 | Fetches unified gifts received. | — |
| `GetWishListPaged` | actorId, pageIndex, pageSize | Paged list — Wish List Paged. | — |
| `GiveGiftOfCategory` | senderId, receiverId, relId, category, giftId, swf | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. | — |
| `OpenGift` | receiverId, giftId | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. | `-429` |
| `removeFromWishlist` | actorId, giftId | AMF endpoint `removeFromWishlist`. | — |

### Endpoint details

#### `BuyGift`

| Property | Value |
|----------|-------|
| Parameters | senderId, receiverId, giftId, SWF |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| UI / callers | `CertificateDetails.as`, `CertificateSignup.as`, `GiftManager.as`, `PurchaseCertificateBuyCommand.as` |
| Behavior | Buys gift. |

#### `GetUnifiedActorClothItems`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Behavior | Fetches unified actor cloth items. |

#### `GetUnifiedActorClothesByType`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Behavior | Fetches unified actor clothes by type. |

#### `GetUnifiedGiftsGiven`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Behavior | Fetches unified gifts given. |

#### `GetUnifiedGiftsNew`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Behavior | Fetches unified gifts new. |

#### `GetUnifiedGiftsReceived`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Behavior | Fetches unified gifts received. |

#### `GetWishListPaged`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| UI / callers | `WishListModelOther.as`, `WishListModelSelf.as` |
| Behavior | Paged list — Wish List Paged. |

#### `GiveGiftOfCategory`

| Property | Value |
|----------|-------|
| Parameters | senderId, receiverId, relId, category, giftId, swf |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | 0 · −1 · −10 VIP niv.6 · −20 limite/jour · −30 déjà possédé · −40 cooldown |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| Behavior | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. |

#### `OpenGift`

| Property | Value |
|----------|-------|
| Parameters | receiverId, giftId |
| AMF ticket | Yes |
| Rate limit | `-429` on `GiftLogId` (popup) |
| Return codes | `GiftLogId` : ID succès · −429 rate limit |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| UI / callers | `GiftManager.as`, `WishListController.as`, `WishListGiftRenderer.as` |
| Behavior | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. |

#### `removeFromWishlist`

| Property | Value |
|----------|-------|
| Parameters | actorId, giftId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| UI / callers | `WishListController.as` |
| Behavior | AMF endpoint `removeFromWishlist`. |

## `WebService.Gifts.AMFGiftableMembershipService`

**AMF path:** `MovieStarPlanet.WebService.Gifts.AMFGiftableMembershipService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetGiftableMemberships` | (VipCertificateStatus.GIVABLE) · (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) | Fetches giftable memberships. | — |
| `GetMembershipsForUser` | (param1, -1, param2, param3) · (param1, 1, param2, param3) | Fetches memberships for user. | — |
| `GetNumberOfUnredeemedMemberships` | — | Fetches number of unredeemed memberships. | — |
| `GetReceivedGiftableMemberships` | (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) | Fetches received giftable memberships. | — |
| `GiveGiftableMembership` | param1, param2, "", "" | AMF endpoint `GiveGiftableMembership`. | — |
| `HasMembershipActivity` | — | AMF endpoint `HasMembershipActivity`. | — |
| `RedeemGiftableMembership` | param1 | AMF endpoint `RedeemGiftableMembership`. | — |
| `RejectGiftedMembership` | param1 | AMF endpoint `RejectGiftedMembership`. | — |

### Endpoint details

#### `GetGiftableMemberships`

| Property | Value |
|----------|-------|
| Parameters | (VipCertificateStatus.GIVABLE) · (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Behavior | Fetches giftable memberships. |

#### `GetMembershipsForUser`

| Property | Value |
|----------|-------|
| Parameters | (param1, -1, param2, param3) · (param1, 1, param2, param3) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Behavior | Fetches memberships for user. |

#### `GetNumberOfUnredeemedMemberships`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Behavior | Fetches number of unredeemed memberships. |

#### `GetReceivedGiftableMemberships`

| Property | Value |
|----------|-------|
| Parameters | (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Behavior | Fetches received giftable memberships. |

#### `GiveGiftableMembership`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, "", "" |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | 0 · −1 · −10 VIP niv.6 · −20 limite/jour · −30 déjà possédé · −40 cooldown |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Behavior | AMF endpoint `GiveGiftableMembership`. |

#### `HasMembershipActivity`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Behavior | AMF endpoint `HasMembershipActivity`. |

#### `RedeemGiftableMembership`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| UI / callers | `WishListController.as` |
| Behavior | AMF endpoint `RedeemGiftableMembership`. |

#### `RejectGiftedMembership`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Behavior | AMF endpoint `RejectGiftedMembership`. |

## `WebService.Gifts.AMFGiftsService+Version2`

**AMF path:** `MovieStarPlanet.WebService.Gifts.AMFGiftsService+Version2`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AddItemToWishlist` | clothIds, clothColors | AMF endpoint `AddItemToWishlist`. | — |
| `AwardStartupReward` | actorId | AMF endpoint `AwardStartupReward`. | — |
| `BuyGift` | senderId, receiverId, giftId, SWF | Buys gift. | — |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize | Fetches all gifts given. | — |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize | Fetches all gifts received. | — |
| `GetGift` | giftId | Fetches gift. | — |
| `GetGiftLog` | (giftLogId) · (param1) | Fetches gift log. | — |
| `GetMarketingStepGift` | actorId | Fetches marketing step gift. | — |
| `GiveGiftOfCategory` | senderId, receiverId, relId, category, giftId, swf | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. | — |
| `HandleGift` | — | AMF endpoint `HandleGift`. | — |
| `IsInUseInRooms` | actorClothesRelId | AMF endpoint `IsInUseInRooms`. | — |
| `OpenGift` | receiverId, giftId | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. | `-429` |
| `ReturnMassGifts` | singleActorId, multipleActorIds, received | AMF endpoint `ReturnMassGifts`. | — |
| `RevertTrade` | giftLogId | AMF endpoint `RevertTrade`. | — |
| `SetMarketingStep` | param1, param2, param3 | Updates marketing step. | — |
| `UpdateGift` | actorId | Updates ate gift. | — |
| `UpdateRetention` | actorId | Updates ate retention. | — |
| `refundGift` | giftLogId, giftId | AMF endpoint `refundGift`. | — |
| `removeFromWishlist` | actorId, giftId | AMF endpoint `removeFromWishlist`. | — |
| `returnGift` | giftLogId, giftId | AMF endpoint `returnGift`. | — |

### Endpoint details

#### `AddItemToWishlist`

| Property | Value |
|----------|-------|
| Parameters | clothIds, clothColors |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| Behavior | AMF endpoint `AddItemToWishlist`. |

#### `AwardStartupReward`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| Behavior | AMF endpoint `AwardStartupReward`. |

#### `BuyGift`

| Property | Value |
|----------|-------|
| Parameters | senderId, receiverId, giftId, SWF |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / callers | `CertificateDetails.as`, `CertificateSignup.as`, `GiftManager.as`, `PurchaseCertificateBuyCommand.as` |
| Behavior | Buys gift. |

#### `GetAllGiftsGiven`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfService.as` (+1) |
| UI / callers | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Behavior | Fetches all gifts given. |

#### `GetAllGiftsReceived`

| Property | Value |
|----------|-------|
| Parameters | actorId, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfService.as` (+1) |
| UI / callers | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Behavior | Fetches all gifts received. |

#### `GetGift`

| Property | Value |
|----------|-------|
| Parameters | giftId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / callers | `ActivityItemTradeCompleted.as`, `ActivityItemTradeRequest.as`, `ChatRoomFlexApps.as`, `LocalMap.as` (+15) |
| Behavior | Fetches gift. |

#### `GetGiftLog`

| Property | Value |
|----------|-------|
| Parameters | (giftLogId) · (param1) |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / callers | `ActivityItemTradeCompleted.as`, `Trade.as` |
| Behavior | Fetches gift log. |

#### `GetMarketingStepGift`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| Behavior | Fetches marketing step gift. |

#### `GiveGiftOfCategory`

| Property | Value |
|----------|-------|
| Parameters | senderId, receiverId, relId, category, giftId, swf |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | 0 · −1 · −10 VIP niv.6 · −20 limite/jour · −30 déjà possédé · −40 cooldown |
| AMF client | `com/moviestarplanet/services/gifts/GiftsAmfService.as` (+1) |
| Behavior | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. |

#### `HandleGift`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / callers | `MessagingSpeechBubble.as`, `PostLoginHandler.as` |
| Behavior | AMF endpoint `HandleGift`. |

#### `IsInUseInRooms`

| Property | Value |
|----------|-------|
| Parameters | actorClothesRelId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| Behavior | AMF endpoint `IsInUseInRooms`. |

#### `OpenGift`

| Property | Value |
|----------|-------|
| Parameters | receiverId, giftId |
| AMF ticket | Yes |
| Rate limit | `-429` on `GiftLogId` (popup) |
| Return codes | `GiftLogId` : ID succès · −429 rate limit |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / callers | `GiftManager.as`, `WishListController.as`, `WishListGiftRenderer.as` |
| Behavior | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. |

#### `ReturnMassGifts`

| Property | Value |
|----------|-------|
| Parameters | singleActorId, multipleActorIds, received |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / callers | `ActorGiftLog.as` |
| Behavior | AMF endpoint `ReturnMassGifts`. |

#### `RevertTrade`

| Property | Value |
|----------|-------|
| Parameters | giftLogId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / callers | `TradeLogListItem.as` |
| Behavior | AMF endpoint `RevertTrade`. |

#### `SetMarketingStep`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / callers | `PostLoginSequence.as` |
| Behavior | Updates marketing step. |

#### `UpdateGift`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / callers | `OverviewMap.as`, `HandleFreeGiftsCommand.as`, `PostLoginSequence.as` |
| Behavior | Updates ate gift. |

#### `UpdateRetention`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / callers | `PostLoginSequence.as` |
| Behavior | Updates ate retention. |

#### `refundGift`

| Property | Value |
|----------|-------|
| Parameters | giftLogId, giftId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / callers | `ModeratorGiftListItem.as` |
| Behavior | AMF endpoint `refundGift`. |

#### `removeFromWishlist`

| Property | Value |
|----------|-------|
| Parameters | actorId, giftId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / callers | `WishListController.as` |
| Behavior | AMF endpoint `removeFromWishlist`. |

#### `returnGift`

| Property | Value |
|----------|-------|
| Parameters | giftLogId, giftId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / callers | `ModeratorGiftListItem.as` |
| Behavior | AMF endpoint `returnGift`. |

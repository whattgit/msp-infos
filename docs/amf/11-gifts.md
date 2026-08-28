# V.11 — Cadeaux

Envoi, ouverture, wishlist, trades.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `OpenGift` | `AMFGiftsService` | `GiftLogId` | Oui |

## Codes de réponse

| Code | Signification |
|------|---------------|
| `0` | OK |
| `−1` | Erreur |
| `−10` | Non-VIP niveau 6 requis |
| `−20` | Limite quotidienne (25/jour UI) |
| `−30` | Possède déjà l'objet |
| `−40` | Cooldown trop tôt |

## `MobileServices.AMFGiftsService+Version2`

**Chemin AMF :** `MovieStarPlanet.MobileServices.AMFGiftsService+Version2`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BuyGift` | senderId, receiverId, giftId, SWF | Achète gift. | — |
| `GetUnifiedActorClothItems` | param1, param2, param3 | Récupère unified actor cloth items. | — |
| `GetUnifiedActorClothesByType` | param1, param2, param3 | Récupère unified actor clothes by type. | — |
| `GetUnifiedGiftsGiven` | param1, param2 | Récupère unified gifts given. | — |
| `GetUnifiedGiftsNew` | param1, param2 | Récupère unified gifts new. | — |
| `GetUnifiedGiftsReceived` | param1, param2 | Récupère unified gifts received. | — |
| `GetWishListPaged` | actorId, pageIndex, pageSize | Liste paginée — Wish List Paged. | — |
| `GiveGiftOfCategory` | senderId, receiverId, relId, category, giftId, swf | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. | — |
| `OpenGift` | receiverId, giftId | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. | `-429` |
| `removeFromWishlist` | actorId, giftId | Endpoint AMF `removeFromWishlist`. | — |

### Détail endpoints

#### `BuyGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | senderId, receiverId, giftId, SWF |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| UI / appelants | `CertificateDetails.as`, `CertificateSignup.as`, `GiftManager.as`, `PurchaseCertificateBuyCommand.as` |
| Fonctionnement | Achète gift. |

#### `GetUnifiedActorClothItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Fonctionnement | Récupère unified actor cloth items. |

#### `GetUnifiedActorClothesByType`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Fonctionnement | Récupère unified actor clothes by type. |

#### `GetUnifiedGiftsGiven`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Fonctionnement | Récupère unified gifts given. |

#### `GetUnifiedGiftsNew`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Fonctionnement | Récupère unified gifts new. |

#### `GetUnifiedGiftsReceived`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| Fonctionnement | Récupère unified gifts received. |

#### `GetWishListPaged`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` |
| UI / appelants | `WishListModelOther.as`, `WishListModelSelf.as` |
| Fonctionnement | Liste paginée — Wish List Paged. |

#### `GiveGiftOfCategory`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | senderId, receiverId, relId, category, giftId, swf |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | 0 · −1 · −10 VIP niv.6 · −20 limite/jour · −30 déjà possédé · −40 cooldown |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| Fonctionnement | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. |

#### `OpenGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | receiverId, giftId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `GiftLogId` (popup) |
| Codes retour | `GiftLogId` : ID succès · −429 rate limit |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| UI / appelants | `GiftManager.as`, `WishListController.as`, `WishListGiftRenderer.as` |
| Fonctionnement | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. |

#### `removeFromWishlist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, giftId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfMobileService.as` (+1) |
| UI / appelants | `WishListController.as` |
| Fonctionnement | Endpoint AMF `removeFromWishlist`. |

## `WebService.Gifts.AMFGiftableMembershipService`

**Chemin AMF :** `MovieStarPlanet.WebService.Gifts.AMFGiftableMembershipService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetGiftableMemberships` | (VipCertificateStatus.GIVABLE) · (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) | Récupère giftable memberships. | — |
| `GetMembershipsForUser` | (param1, -1, param2, param3) · (param1, 1, param2, param3) | Récupère memberships for user. | — |
| `GetNumberOfUnredeemedMemberships` | — | Récupère number of unredeemed memberships. | — |
| `GetReceivedGiftableMemberships` | (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) | Récupère received giftable memberships. | — |
| `GiveGiftableMembership` | param1, param2, "", "" | Endpoint AMF `GiveGiftableMembership`. | — |
| `HasMembershipActivity` | — | Endpoint AMF `HasMembershipActivity`. | — |
| `RedeemGiftableMembership` | param1 | Endpoint AMF `RedeemGiftableMembership`. | — |
| `RejectGiftedMembership` | param1 | Endpoint AMF `RejectGiftedMembership`. | — |

### Détail endpoints

#### `GetGiftableMemberships`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (VipCertificateStatus.GIVABLE) · (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Fonctionnement | Récupère giftable memberships. |

#### `GetMembershipsForUser`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (param1, -1, param2, param3) · (param1, 1, param2, param3) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Fonctionnement | Récupère memberships for user. |

#### `GetNumberOfUnredeemedMemberships`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Fonctionnement | Récupère number of unredeemed memberships. |

#### `GetReceivedGiftableMemberships`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (VipCertificateStatus.OFFERED) · (VipCertificateStatus.REDEEMED) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Fonctionnement | Récupère received giftable memberships. |

#### `GiveGiftableMembership`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, "", "" |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | 0 · −1 · −10 VIP niv.6 · −20 limite/jour · −30 déjà possédé · −40 cooldown |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Fonctionnement | Endpoint AMF `GiveGiftableMembership`. |

#### `HasMembershipActivity`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Fonctionnement | Endpoint AMF `HasMembershipActivity`. |

#### `RedeemGiftableMembership`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| UI / appelants | `WishListController.as` |
| Fonctionnement | Endpoint AMF `RedeemGiftableMembership`. |

#### `RejectGiftedMembership`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/media/GiftableMembershipAMFService.as` |
| Fonctionnement | Endpoint AMF `RejectGiftedMembership`. |

## `WebService.Gifts.AMFGiftsService+Version2`

**Chemin AMF :** `MovieStarPlanet.WebService.Gifts.AMFGiftsService+Version2`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AddItemToWishlist` | clothIds, clothColors | Endpoint AMF `AddItemToWishlist`. | — |
| `AwardStartupReward` | actorId | Endpoint AMF `AwardStartupReward`. | — |
| `BuyGift` | senderId, receiverId, giftId, SWF | Achète gift. | — |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize | Récupère all gifts given. | — |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize | Récupère all gifts received. | — |
| `GetGift` | giftId | Récupère gift. | — |
| `GetGiftLog` | (giftLogId) · (param1) | Récupère gift log. | — |
| `GetMarketingStepGift` | actorId | Récupère marketing step gift. | — |
| `GiveGiftOfCategory` | senderId, receiverId, relId, category, giftId, swf | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. | — |
| `HandleGift` | — | Endpoint AMF `HandleGift`. | — |
| `IsInUseInRooms` | actorClothesRelId | Endpoint AMF `IsInUseInRooms`. | — |
| `OpenGift` | receiverId, giftId | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. | `-429` |
| `ReturnMassGifts` | singleActorId, multipleActorIds, received | Endpoint AMF `ReturnMassGifts`. | — |
| `RevertTrade` | giftLogId | Endpoint AMF `RevertTrade`. | — |
| `SetMarketingStep` | param1, param2, param3 | Met à jour marketing step. | — |
| `UpdateGift` | actorId | Met à jour ate gift. | — |
| `UpdateRetention` | actorId | Met à jour ate retention. | — |
| `refundGift` | giftLogId, giftId | Endpoint AMF `refundGift`. | — |
| `removeFromWishlist` | actorId, giftId | Endpoint AMF `removeFromWishlist`. | — |
| `returnGift` | giftLogId, giftId | Endpoint AMF `returnGift`. | — |

### Détail endpoints

#### `AddItemToWishlist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | clothIds, clothColors |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| Fonctionnement | Endpoint AMF `AddItemToWishlist`. |

#### `AwardStartupReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| Fonctionnement | Endpoint AMF `AwardStartupReward`. |

#### `BuyGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | senderId, receiverId, giftId, SWF |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / appelants | `CertificateDetails.as`, `CertificateSignup.as`, `GiftManager.as`, `PurchaseCertificateBuyCommand.as` |
| Fonctionnement | Achète gift. |

#### `GetAllGiftsGiven`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfService.as` (+1) |
| UI / appelants | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Fonctionnement | Récupère all gifts given. |

#### `GetAllGiftsReceived`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfService.as` (+1) |
| UI / appelants | `GenericGiftsLog.as`, `GiftableMemershipAmfWrapper.as` |
| Fonctionnement | Récupère all gifts received. |

#### `GetGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | giftId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / appelants | `ActivityItemTradeCompleted.as`, `ActivityItemTradeRequest.as`, `ChatRoomFlexApps.as`, `LocalMap.as` (+15) |
| Fonctionnement | Récupère gift. |

#### `GetGiftLog`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | (giftLogId) · (param1) |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / appelants | `ActivityItemTradeCompleted.as`, `Trade.as` |
| Fonctionnement | Récupère gift log. |

#### `GetMarketingStepGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| Fonctionnement | Récupère marketing step gift. |

#### `GiveGiftOfCategory`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | senderId, receiverId, relId, category, giftId, swf |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | 0 · −1 · −10 VIP niv.6 · −20 limite/jour · −30 déjà possédé · −40 cooldown |
| Client AMF | `com/moviestarplanet/services/gifts/GiftsAmfService.as` (+1) |
| Fonctionnement | Envoie cadeau depuis inventaire ; max 25/jour UI ; codes -10/-20/-30/-40. |

#### `HandleGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / appelants | `MessagingSpeechBubble.as`, `PostLoginHandler.as` |
| Fonctionnement | Endpoint AMF `HandleGift`. |

#### `IsInUseInRooms`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorClothesRelId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| Fonctionnement | Endpoint AMF `IsInUseInRooms`. |

#### `OpenGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | receiverId, giftId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `GiftLogId` (popup) |
| Codes retour | `GiftLogId` : ID succès · −429 rate limit |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / appelants | `GiftManager.as`, `WishListController.as`, `WishListGiftRenderer.as` |
| Fonctionnement | Ouvre un cadeau reçu ; `GiftLogId==-429` = rate limit. |

#### `ReturnMassGifts`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | singleActorId, multipleActorIds, received |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / appelants | `ActorGiftLog.as` |
| Fonctionnement | Endpoint AMF `ReturnMassGifts`. |

#### `RevertTrade`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | giftLogId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / appelants | `TradeLogListItem.as` |
| Fonctionnement | Endpoint AMF `RevertTrade`. |

#### `SetMarketingStep`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / appelants | `PostLoginSequence.as` |
| Fonctionnement | Met à jour marketing step. |

#### `UpdateGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / appelants | `OverviewMap.as`, `HandleFreeGiftsCommand.as`, `PostLoginSequence.as` |
| Fonctionnement | Met à jour ate gift. |

#### `UpdateRetention`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / appelants | `PostLoginSequence.as` |
| Fonctionnement | Met à jour ate retention. |

#### `refundGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | giftLogId, giftId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / appelants | `ModeratorGiftListItem.as` |
| Fonctionnement | Endpoint AMF `refundGift`. |

#### `removeFromWishlist`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, giftId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` (+1) |
| UI / appelants | `WishListController.as` |
| Fonctionnement | Endpoint AMF `removeFromWishlist`. |

#### `returnGift`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | giftLogId, giftId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/gifts/GiftService.as` |
| UI / appelants | `ModeratorGiftListItem.as` |
| Fonctionnement | Endpoint AMF `returnGift`. |

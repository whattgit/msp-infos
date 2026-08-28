# V.5 — Boutique & spending

Catalogue shop, achats SC/diamants, boosters.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `BuySpecialGreeting` | `AMFSpendingService` | `Code` | Oui |

## Codes de réponse

| Code | Signification |
|------|---------------|
| `0` | Succès |
| `−1` | Exception |
| `−2` | Pas assez diamants |
| `−3` | Déjà acheté aujourd'hui |
| `−4` | Pas assez SC |
| `−5` | Créateur ne peut pas acheter (design) |

## `WebService.Shopping.AMFShopContentService`

**Chemin AMF :** `MovieStarPlanet.WebService.Shopping.AMFShopContentService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `AddTag` | param1, param2 | Endpoint AMF `AddTag`. | — |
| `AddTheme` | param1, param2 | Endpoint AMF `AddTheme`. | — |
| `BuyItems` | param1, ActorSession.loggedInActor.actorId | Achète items. | — |
| `GetPage` | pageIndex, pageSize, params.shopId, params.genderId, params.themeId, params.categoryId, params.tagToUse, params.vipToUse, params.currencyToUse, params.search | Récupère page. | — |
| `RemoveTag` | param1, param2 | Supprime e tag. | — |
| `RemoveTheme` | param1, param2 | Supprime e theme. | — |
| `SetShopIds` | param1, param2 | Met à jour shop ids. | — |

### Détail endpoints

#### `AddTag`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / appelants | `FlashHiddenShop.as` |
| Fonctionnement | Endpoint AMF `AddTag`. |

#### `AddTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / appelants | `FacepartUploader.as`, `UploadClothes.as`, `ChatRoomGraphicsHandler.as`, `FlashHiddenShop.as` |
| Fonctionnement | Endpoint AMF `AddTheme`. |

#### `BuyItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, ActorSession.loggedInActor.actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / appelants | `FlashHiddenShop.as`, `BeautyClinicBuyCommand.as` |
| Fonctionnement | Achète items. |

#### `GetPage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | pageIndex, pageSize, params.shopId, params.genderId, params.themeId, params.categoryId, params.tagToUse, params.vipToUse, params.currencyToUse, params.search |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / appelants | `ClubList.as`, `ClubMemberList.as`, `ClubView.as`, `EditMyRoom.as` (+33) |
| Fonctionnement | Récupère page. |

#### `RemoveTag`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / appelants | `FlashHiddenShop.as`, `DebuggerTextfield.as` |
| Fonctionnement | Supprime e tag. |

#### `RemoveTheme`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / appelants | `FlashHiddenShop.as` |
| Fonctionnement | Supprime e theme. |

#### `SetShopIds`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / appelants | `FlashHiddenShop.as` |
| Fonctionnement | Met à jour shop ids. |

## `WebService.Spending.AMFSpendingService`

**Chemin AMF :** `MovieStarPlanet.WebService.Spending.AMFSpendingService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BuyAnimation` | param1, param2 | Achète animation. | — |
| `BuyBackground` | param1, param2 | Achète background. | — |
| `BuyChangePet` | param1, param2, param3, param4 | Achète change pet. | — |
| `BuyCharacterPopUp` | param1 | Achète character pop up. | — |
| `BuyClothes` | actorId, clothes[], lookId | Achète vêtements depuis le shop ; param `lookId` si achat depuis un look. | — |
| `BuyDiamondCharacterEffect` | param1 | Achète diamond character effect. | — |
| `BuyDiamondTwit` | param1 | Achète diamond twit. | — |
| `BuyEmoticonPackage` | param1, param2 | Achète emoticon package. | — |
| `BuyFameBooster` | param1 | Achète fame booster. | — |
| `BuyFameWheelSpin` | param1 | Achète fame wheel spin. | — |
| `BuyInstantPetGrow` | param1, param2 | Achète instant pet grow. | — |
| `BuyMusic` | param1, param2 | Achète music. | — |
| `BuyShoppingSpree` | param1 | Achète shopping spree. | — |
| `BuySpecialGreeting` | actorId, friendId, greetingTypeId | Achète special greeting. | `-429` |
| `BuyStarcoinShooter` | param1 | Achète starcoin shooter. | — |
| `BuyStarcoinsWheelSpin` | param1 | Achète starcoins wheel spin. | — |
| `ClaimFreeDownloadableFameWheelSpin` | param1 | Endpoint AMF `ClaimFreeDownloadableFameWheelSpin`. | — |
| `GetActiveSpecialsItems` | param1 | Récupère active specials items. | — |
| `GetEmoticonPackages` | param1 | Récupère emoticon packages. | — |
| `GetGreetingIndices` | param1 | Récupère greeting indices. | — |
| `GetPagedShopSpecials` | param1, param2, param3 | Items diamants boutique paginés. | — |
| `GetSpecialsGreetingItem` | param1, param2 | Récupère specials greeting item. | — |
| `GetSpecialsItemPrice` | param1, param2 | Récupère specials item price. | — |
| `IsValidSpecialGreeting` | param1, param2 | Endpoint AMF `IsValidSpecialGreeting`. | — |

### Détail endpoints

#### `BuyAnimation`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `HighscoreAnimation.as`, `AnimationDiamondShopPreview.as`, `AnimationShopModel.as`, `PreviewAnimation.as` (+1) |
| Fonctionnement | Achète animation. |

#### `BuyBackground`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `BuyBackgroundCommand.as`, `BackgroundRendererBig.as`, `SpendingProvider.as` |
| Fonctionnement | Achète background. |

#### `BuyChangePet`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `ChangePetDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète change pet. |

#### `BuyCharacterPopUp`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `CharacterPopUpShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète character pop up. |

#### `BuyClothes`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, clothes[], lookId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `StuffShop.as`, `WishListController.as`, `ClothesDiamondShopPreview.as`, `ItemsDiamondShopPreview.as` (+5) |
| Fonctionnement | Achète vêtements depuis le shop ; param `lookId` si achat depuis un look. |

#### `BuyDiamondCharacterEffect`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `DiamondCharacterEffectShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète diamond character effect. |

#### `BuyDiamondTwit`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `DiamondTwitShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète diamond twit. |

#### `BuyEmoticonPackage`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/emoticon/service/EmoticonService.as` |
| UI / appelants | `EmoticonPurchasePopup.as`, `EmoticonSelectorModelWeb.as`, `EmojiSelectorController.as` |
| Fonctionnement | Achète emoticon package. |

#### `BuyFameBooster`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `FameBoosterDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète fame booster. |

#### `BuyFameWheelSpin`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `FameWheelDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète fame wheel spin. |

#### `BuyInstantPetGrow`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `FoodSelector.as`, `InstantPetGrowDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète instant pet grow. |

#### `BuyMusic`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `MusicShop.as`, `SpendingProvider.as` |
| Fonctionnement | Achète music. |

#### `BuyShoppingSpree`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `ShoppingSpreeDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète shopping spree. |

#### `BuySpecialGreeting`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, friendId, greetingTypeId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `Code` (popup) |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `SpecialGreetingDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Achète special greeting. |

#### `BuyStarcoinShooter`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `StarcoinShooterPopup.as`, `SpendingProvider.as` |
| Fonctionnement | Achète starcoin shooter. |

#### `BuyStarcoinsWheelSpin`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `SpinTheWheel.as`, `SpendingProvider.as` |
| Fonctionnement | Achète starcoins wheel spin. |

#### `ClaimFreeDownloadableFameWheelSpin`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `FameWheelDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Endpoint AMF `ClaimFreeDownloadableFameWheelSpin`. |

#### `GetActiveSpecialsItems`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `ActiveSpecialsHandler.as`, `DiamondCoinFame.as`, `DiamondCharacterEffectShopPreview.as`, `CharacterPopUpShopPreview.as` (+3) |
| Fonctionnement | Récupère active specials items. |

#### `GetEmoticonPackages`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/emoticon/service/EmoticonService.as` |
| UI / appelants | `EmoticonLibrary.as`, `MangroveEmoticonInteractionStatus.as`, `EmoticonSelectorModelWeb.as`, `EmoticonUtility.as` |
| Fonctionnement | Récupère emoticon packages. |

#### `GetGreetingIndices`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `SpecialGreetingDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Récupère greeting indices. |

#### `GetPagedShopSpecials`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `DiamondShopView.as`, `SpendingProvider.as` |
| Fonctionnement | Items diamants boutique paginés. |

#### `GetSpecialsGreetingItem`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `SpecialGreetingPopupController.as`, `SpecialGreetingDiamondShopPreview.as`, `SpendingProvider.as` |
| Fonctionnement | Récupère specials greeting item. |

#### `GetSpecialsItemPrice`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `FoodSelector.as`, `StarcoinShooterPopup.as`, `SpendingProvider.as` |
| Fonctionnement | Récupère specials item price. |

#### `IsValidSpecialGreeting`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | — |
| Client AMF | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / appelants | `SpecialGreetingPopupController.as` |
| Fonctionnement | Endpoint AMF `IsValidSpecialGreeting`. |

# III.5 — Shop & spending

> **EN** · [Français](../../fr/amf/05-shop.md)


Shop catalogue, SC/diamond purchases, boosters.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `BuySpecialGreeting` | `AMFSpendingService` | `Code` | Yes |

## Response codes

| Code | Meaning |
|------|---------------|
| `0` | Success |
| `−1` | Exception |
| `−2` | Not enough diamonds |
| `−3` | Already bought today |
| `−4` | Not enough SC |
| `−5` | Creator cannot buy (design) |

## `WebService.Shopping.AMFShopContentService`

**AMF path:** `MovieStarPlanet.WebService.Shopping.AMFShopContentService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `AddTag` | param1, param2 | AMF endpoint `AddTag`. | — |
| `AddTheme` | param1, param2 | AMF endpoint `AddTheme`. | — |
| `BuyItems` | param1, ActorSession.loggedInActor.actorId | Buys items. | — |
| `GetPage` | pageIndex, pageSize, params.shopId, params.genderId, params.themeId, params.categoryId, params.tagToUse, params.vipToUse, params.currencyToUse, params.search | Fetches page. | — |
| `RemoveTag` | param1, param2 | Deletes e tag. | — |
| `RemoveTheme` | param1, param2 | Deletes e theme. | — |
| `SetShopIds` | param1, param2 | Updates shop ids. | — |

### Endpoint details

#### `AddTag`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / callers | `FlashHiddenShop.as` |
| Behavior | AMF endpoint `AddTag`. |

#### `AddTheme`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / callers | `FacepartUploader.as`, `UploadClothes.as`, `ChatRoomGraphicsHandler.as`, `FlashHiddenShop.as` |
| Behavior | AMF endpoint `AddTheme`. |

#### `BuyItems`

| Property | Value |
|----------|-------|
| Parameters | param1, ActorSession.loggedInActor.actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / callers | `FlashHiddenShop.as`, `BeautyClinicBuyCommand.as` |
| Behavior | Buys items. |

#### `GetPage`

| Property | Value |
|----------|-------|
| Parameters | pageIndex, pageSize, params.shopId, params.genderId, params.themeId, params.categoryId, params.tagToUse, params.vipToUse, params.currencyToUse, params.search |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / callers | `ClubList.as`, `ClubMemberList.as`, `ClubView.as`, `EditMyRoom.as` (+33) |
| Behavior | Fetches page. |

#### `RemoveTag`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / callers | `FlashHiddenShop.as`, `DebuggerTextfield.as` |
| Behavior | Deletes e tag. |

#### `RemoveTheme`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / callers | `FlashHiddenShop.as` |
| Behavior | Deletes e theme. |

#### `SetShopIds`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/shopping/hiddenShop/service/HiddenAMFShopService.as` |
| UI / callers | `FlashHiddenShop.as` |
| Behavior | Updates shop ids. |

## `WebService.Spending.AMFSpendingService`

**AMF path:** `MovieStarPlanet.WebService.Spending.AMFSpendingService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BuyAnimation` | param1, param2 | Buys animation. | — |
| `BuyBackground` | param1, param2 | Buys background. | — |
| `BuyChangePet` | param1, param2, param3, param4 | Buys change pet. | — |
| `BuyCharacterPopUp` | param1 | Buys character pop up. | — |
| `BuyClothes` | actorId, clothes[], lookId | Buys vêtements depuis le shop ; param `lookId` si achat depuis un look. | — |
| `BuyDiamondCharacterEffect` | param1 | Buys diamond character effect. | — |
| `BuyDiamondTwit` | param1 | Buys diamond twit. | — |
| `BuyEmoticonPackage` | param1, param2 | Buys emoticon package. | — |
| `BuyFameBooster` | param1 | Buys fame booster. | — |
| `BuyFameWheelSpin` | param1 | Buys fame wheel spin. | — |
| `BuyInstantPetGrow` | param1, param2 | Buys instant pet grow. | — |
| `BuyMusic` | param1, param2 | Buys music. | — |
| `BuyShoppingSpree` | param1 | Buys shopping spree. | — |
| `BuySpecialGreeting` | actorId, friendId, greetingTypeId | Buys special greeting. | `-429` |
| `BuyStarcoinShooter` | param1 | Buys starcoin shooter. | — |
| `BuyStarcoinsWheelSpin` | param1 | Buys starcoins wheel spin. | — |
| `ClaimFreeDownloadableFameWheelSpin` | param1 | AMF endpoint `ClaimFreeDownloadableFameWheelSpin`. | — |
| `GetActiveSpecialsItems` | param1 | Fetches active specials items. | — |
| `GetEmoticonPackages` | param1 | Fetches emoticon packages. | — |
| `GetGreetingIndices` | param1 | Fetches greeting indices. | — |
| `GetPagedShopSpecials` | param1, param2, param3 | Items diamants boutique paginés. | — |
| `GetSpecialsGreetingItem` | param1, param2 | Fetches specials greeting item. | — |
| `GetSpecialsItemPrice` | param1, param2 | Fetches specials item price. | — |
| `IsValidSpecialGreeting` | param1, param2 | AMF endpoint `IsValidSpecialGreeting`. | — |

### Endpoint details

#### `BuyAnimation`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `HighscoreAnimation.as`, `AnimationDiamondShopPreview.as`, `AnimationShopModel.as`, `PreviewAnimation.as` (+1) |
| Behavior | Buys animation. |

#### `BuyBackground`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `BuyBackgroundCommand.as`, `BackgroundRendererBig.as`, `SpendingProvider.as` |
| Behavior | Buys background. |

#### `BuyChangePet`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `ChangePetDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys change pet. |

#### `BuyCharacterPopUp`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `CharacterPopUpShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys character pop up. |

#### `BuyClothes`

| Property | Value |
|----------|-------|
| Parameters | actorId, clothes[], lookId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `StuffShop.as`, `WishListController.as`, `ClothesDiamondShopPreview.as`, `ItemsDiamondShopPreview.as` (+5) |
| Behavior | Buys vêtements depuis le shop ; param `lookId` si achat depuis un look. |

#### `BuyDiamondCharacterEffect`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `DiamondCharacterEffectShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys diamond character effect. |

#### `BuyDiamondTwit`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `DiamondTwitShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys diamond twit. |

#### `BuyEmoticonPackage`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/emoticon/service/EmoticonService.as` |
| UI / callers | `EmoticonPurchasePopup.as`, `EmoticonSelectorModelWeb.as`, `EmojiSelectorController.as` |
| Behavior | Buys emoticon package. |

#### `BuyFameBooster`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `FameBoosterDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys fame booster. |

#### `BuyFameWheelSpin`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `FameWheelDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys fame wheel spin. |

#### `BuyInstantPetGrow`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `FoodSelector.as`, `InstantPetGrowDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys instant pet grow. |

#### `BuyMusic`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `MusicShop.as`, `SpendingProvider.as` |
| Behavior | Buys music. |

#### `BuyShoppingSpree`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `ShoppingSpreeDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys shopping spree. |

#### `BuySpecialGreeting`

| Property | Value |
|----------|-------|
| Parameters | actorId, friendId, greetingTypeId |
| AMF ticket | Yes |
| Rate limit | `-429` on `Code` (popup) |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `SpecialGreetingDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Buys special greeting. |

#### `BuyStarcoinShooter`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `StarcoinShooterPopup.as`, `SpendingProvider.as` |
| Behavior | Buys starcoin shooter. |

#### `BuyStarcoinsWheelSpin`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `SpinTheWheel.as`, `SpendingProvider.as` |
| Behavior | Buys starcoins wheel spin. |

#### `ClaimFreeDownloadableFameWheelSpin`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `FameWheelDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | AMF endpoint `ClaimFreeDownloadableFameWheelSpin`. |

#### `GetActiveSpecialsItems`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `ActiveSpecialsHandler.as`, `DiamondCoinFame.as`, `DiamondCharacterEffectShopPreview.as`, `CharacterPopUpShopPreview.as` (+3) |
| Behavior | Fetches active specials items. |

#### `GetEmoticonPackages`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/emoticon/service/EmoticonService.as` |
| UI / callers | `EmoticonLibrary.as`, `MangroveEmoticonInteractionStatus.as`, `EmoticonSelectorModelWeb.as`, `EmoticonUtility.as` |
| Behavior | Fetches emoticon packages. |

#### `GetGreetingIndices`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `SpecialGreetingDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Fetches greeting indices. |

#### `GetPagedShopSpecials`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `DiamondShopView.as`, `SpendingProvider.as` |
| Behavior | Items diamants boutique paginés. |

#### `GetSpecialsGreetingItem`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `SpecialGreetingPopupController.as`, `SpecialGreetingDiamondShopPreview.as`, `SpendingProvider.as` |
| Behavior | Fetches specials greeting item. |

#### `GetSpecialsItemPrice`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `FoodSelector.as`, `StarcoinShooterPopup.as`, `SpendingProvider.as` |
| Behavior | Fetches specials item price. |

#### `IsValidSpecialGreeting`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | — |
| AMF client | `com/moviestarplanet/services/spendingservice/SpendingAmfService.as` |
| UI / callers | `SpecialGreetingPopupController.as` |
| Behavior | AMF endpoint `IsValidSpecialGreeting`. |

# II.5 — Rooms, Profile & Rewards

> **EN** · [Français](../fr/09-rooms-profile-awards.md)


## I. Rooms (`AMFRoomServiceForMobile`)

AMF service: `MovieStarPlanet.WebService.AMFRoomServiceForMobile`  
Client: `MyRoomServices.as`

### Endpoints

| Endpoint | Parameters | Return | Rate limit |
|----------|------------|--------|------------|
| `LoadHouse` | `houseId`, `callingActorId` | `HouseInformation` | — |
| `LoadHouseAndSpecificRoom` | `callingActorId`, `houseId`, `roomId` | Room data | — |
| `SaveRoomWithSnapshot` | `RoomSaveInformation`, snapshot profile/medium/small (3× ByteArray) | `int` roomId ou **−429** | **Yes** (popup) |
| `LoveRoom` | `actorId`, `roomOwnerId` | — | — |

### `RoomSaveInformation` (save payload)

| Field | Type | Role |
|-------|------|------|
| `Wallpaper` | String | ID wallpaper |
| `Floor` | String | Floor ID |
| `ItemsAdded` | Array | Placed click items |
| `ItemsEdited` | Array | Edited items |
| `ItemsRemoved` | Array | Removed items |
| `PetsAdded` | Array | Legacy pets added |
| `PetsEdited` | Array | Legacy pets moved |
| `PetsRemoved` | Array | Legacy pets removed |
| `BonstersAdded` | Array | Bonsters added |
| `BonstersEdited` | Array | Bonsters moved |
| `BonstersRemoved` | Array | Bonsters removed |

Client limit: **10 pets max / room**.

---

## II. Rewards — `AMFAwardingService`

Service : `MovieStarPlanet.WebService.Awarding.AMFAwardingService`  
Client: `AwardingAmfService.as` · Wheel UI: `SpinTheWheel.as`

### II.1 `claimDailyAward(awardStr, amnt, loggedInActorId)`

Claims a daily reward after a wheel spin or mini-game.

| Param | Type | Description |
|-------|------|-------------|
| `awardStr` | String | Reward type ID (see AwardingType table below) |
| `amnt` | int | SC amount won on the wheel (segment value) |
| `loggedInActorId` | int | Logged-in actor ID |

**Client transform:** `AppSettings.getStarWheelAwardEndpoint(awardStr)` remaps wheel types to `*Dwl` variants when downloadable + config enabled.

| Response | Meaning |
|---------|---------------|
| `{amount, currencyType}` | Success — e.g. `currencyType: "money"` |
| `amount == -429` | Rate limit (popup) |

**Post-success event:** `MSPDataEvent.AWARD_DISTRUBTED`.

### II.2 `AwardingType` IDs (awardStr)

Source : `awarding/valueobjects/AwardingType.as`

#### Normal wheel types

| Client constant | Server string (`awardStr`) | Required vipTier | Downloadable remap |
|------------------|----------------------------|----------------|----------------------|
| `WHEEL_AWARD_TYPE` | `"wheel"` | NON_VIP (−1) | → `"wheelDwl"` |
| `WHEEL_BASIC_AWARD_TYPE` | `"basicwheel"` | NORMAL_VIP (0) | → `"basicwheelDwl"` |
| `WHEEL_SUPER_AWARD_TYPE` | `"superwheel"` | SUPER_VIP (1) | → `"superwheelDwl"` |
| `WHEEL_ELITE_AWARD_TYPE` | `"elitewheel"` | ELITE_VIP (2) | → `"elitewheelDwl"` |
| `WHEEL_STAR_AWARD_TYPE` | `"starwheel"` | STAR_VIP (3) | → `"starwheelDwl"` |

#### VIP wheel types

| Constant | Server string | vipTier |
|-----------|---------------|---------|
| `VIP_WHEEL_AWARD_TYPE` | `"vipWheel"` | (legacy) |
| `VIP_WHEEL_BASIC_AWARD_TYPE` | `"basicvipWheel"` | NORMAL_VIP |
| `VIP_WHEEL_SUPER_AWARD_TYPE` | `"supervipWheel"` | SUPER_VIP |
| `VIP_WHEEL_ELITE_AWARD_TYPE` | `"eliteVipWheel"` | ELITE_VIP |
| `VIP_WHEEL_STAR_AWARD_TYPE` | `"starVipWheel"` | STAR_VIP |

#### Wheel video ads

| Constant | Server string | Usage |
|-----------|---------------|-------|
| `ADVERT_WHEEL_SPIN` | `"advertWheel"` | Normal spin after ad |
| `ADVERT_VIP_WHEEL_SPIN` | `"advertWheelVip"` | VIP spin after ad |

#### Other daily types

| Constant | Server string | Client usage |
|-----------|---------------|--------------|
| `TWOPLAYER_FAME` | `"twoPlayerFame"` | 2-player mini-game — fame |
| `TWOPLAYER_MONEY` | `"twoPlayerMoney"` | 2-player mini-game — SC |
| `RETENTION_1_MONEY` | `"firstRetentionSC"` | URL retention — **300 SC** fixed |
| `DAILY_VIP_COINS` | `"dailyVIPCoins"` | Defined constant (no UI call found) |
| `DAILY_VIP_DIAMONDS` | `"dailyVIPDiamonds"` | Defined constant (no UI call found) |
| `ADVERT_VIEW` | `"advertView"` | Pub générique |
| `ADVERT_VIEW_FAME` | `"advertViewFame"` | Pub fame |

#### Intro gift types (int, not string)

| Constant | Value | Usage |
|-----------|--------|-------|
| `Clothes` | 1 | Intro gift clothes |
| `StarCoins` | 2 | Intro gift SC |

#### `awardActor` types

| Constant | Value | Meaning |
|-----------|--------|---------------|
| `AWARD_TYPE_MONEY` | 0 | StarCoins |
| `AWARD_TYPE_FAME` | 1 | Fame |
| `AWARD_TYPE_MEMBERSHIP_STARCOINS` | 2 | SC membership |
| `WIN_SPEND_TYPE_DAILY_WHEEL` | 11 | Daily wheel source |

### II.3 VIP tiers (`VipTierConstants`)

| ID | Constant | Normal wheel | VIP wheel |
|----|-----------|--------------|----------|
| −1 | `NON_VIP` | `wheel` | — (VIP wheel disabled) |
| 0 | `NORMAL_VIP` | `basicwheel` | `basicvipWheel` |
| 1 | `SUPER_VIP` | `superwheel` | `supervipWheel` |
| 2 | `ELITE_VIP` | `elitewheel` | `eliteVipWheel` |
| 3 | `STAR_VIP` | `starwheel` | `starVipWheel` |

At login, `PostLoginSequence` calls `countAwardsLeft([types by tier], actorId)` to show remaining spins.

### II.4 Wheel segments (`amnt` amounts)

Source: `SpinTheWheel.as` — `winnings` per segment (8 segments).

| Mode | Normal wheel | VIP wheel |
|------|--------------|----------|
| Standard | `[40,20,80,20,40,20,120,20]` | `[50,25,100,25,50,25,200,25]` |
| Higher prizes (downloadable) | Server config `HigherSpinWheelPrizesOnDownloadable` (CSV) ou `[80,40,160,40,80,40,240,40]` | `[50,25,100,25,50,25,200,25]` |

Diamond respin (`BuyStarcoinsWheelSpin`) : server returns `regularWheelReward` + `vipWheelReward` directly.

### II.5 `claimAdvertViewAward(type, amount, actorId)`

Called when the user watches an ad for a respin (`adWatched == true`).

| Param | Example |
|-------|---------|
| `type` | `"advertWheel"` ou `"advertWheelVip"` |
| `amount` | SC segment won |
| `actorId` | Actor ID |

Rate limit : `amount == -429`.

### II.6 `claimAdvertAwardByCampaign(campaignId)`

Incentivized ad campaign reward (`CampaignIncentivizedVideoAdHandler.obtainReward`).

| Param | Description |
|-------|-------------|
| `campaignId` | Ad campaign ID (handler) |

Rate limit : `amount == -429`.

### II.7 Auxiliary endpoints

| Endpoint | Parameters | Role |
|----------|------------|------|
| `countAwardsLeft` | `awardStr[]`, `actorId` | Spins left by type |
| `hasAnyDailyAwardLeft` | `awardStr`, `actorId` | Is one type still available? |
| `hasAllDailyAwardLeft` | `awardStr[]`, `actorId` | Are all types available? |
| `hasSomeDailyAwardLeft` | `awardStr[]`, `actorId` | Is at least one available? |
| `awardActor` | `actorId, amount, type, winSpendType` | Direct credit |
| `RequestIntroductionAward` | `actorId` | New player gift |
| `GetWheelData` | — | Server wheel config (unused by UI) |
| `SpinWheel` | `wheelId` | Legacy — **unused** by SpinTheWheel.as |
| `BuyDiamondRespin` | — | Legacy Awarding — **UI uses** `BuyStarcoinsWheelSpin` |

### II.8 Diamond respin (Spending, pas Awarding)

| Property | Value |
|-----------|--------|
| Endpoint | `AMFSpendingService.BuyStarcoinsWheelSpin(actorId)` |
| UI price | **1 💎** (`SPIN_AGAIN_PRICE`) |
| Codes | `0` OK · `−2` not enough 💎 · `−3` recurring payment ineligible |
| Retour | `{regularWheelReward, vipWheelReward}` |

---

## III. Piggy bank (`AMFPiggyBankService`)

| Endpoint | Params | Role |
|----------|--------|------|
| `GetPiggyBank` | — | Sync `{StarCoins, Fame, Diamonds}` |
| `DestroyPiggyBank` | — | Break piggy |
| `CanDestroyPiggyBank` | — | Check if breakable |

Non-VIP limits : **2500 SC** · **5000 fame** (VIP = illimité).

Daily login bonus (`DailyBonusType` post-login) → piggy fame by tier :

| vipTier | Fame added |
|---------|--------------|
| NORMAL_VIP | 10 |
| SUPER_VIP / ELITE_VIP | 30 |
| STAR_VIP | 60 |

---

## IV. Notification center — `ClaimBonus2`

Service : `AMFNotificationCenterService`  
Client: `NotificationCenterAmfService.as` · UI : `FameChestPopup.as`

```
ClaimBonus2(actorId, contentTypes[])
```

| Param | Type | Description |
|-------|------|-------------|
| `actorId` | int | Actor |
| `contentTypes` | int[] | `FameTypeUtils` IDs of selected bonuses |

Rate limit : `ErrorCode == -429` (popup).

### `contentTypes` IDs (`FameTypeUtils`)

| ID | Constant | Feature |
|----|-----------|---------|
| 1 | `ARTBOOK` | Artbooks |
| 2 | `MOVIE_WATCH` | Watched movies |
| 3 | `LOOK` | Looks |
| 4 | `LOOK_BOUGHT` | Bought looks |
| 5 | `AUTOGRAPH` | Autographs |
| 6 | `MOVIE_STARRED` | Movie starring |
| 7 | `DESIGN` | Designs |
| 8 | `ROOM` | Rooms |
| 9 | `YOUTUBE` | YouTube videos |
| 10 | `WAYD` | WAYD statuses |
| 13 | `CREATE_RATE` | Create & rate |
| 14 | `APP` | Apps |
| 15 | `PHOTO` | Photos |
| 16 | `PET` | Petted pets |
| 17 | `DESIGN_BOUGHT` | Bought designs |

Chaque `NotificationValueObject` contient `BonusFame`, `BonusStarCoins`, `ContentType`, `Claimed`.

---

## V. Quests (`AMFQuestService`)

| Endpoint | Parameters | Notes |
|----------|------------|-------|
| `GetAllQuestStatus` | `actorId` | Downloadable variant : `GetAllQuestStatusForDownloadableClient` |
| `BeginQuest` | `actorId`, `questId` | Starts quest |
| `UpdateGotoObjectiveAndGetStatus` | `actorId`, `questId`, `objectiveId` | Goto objective |
| `UpdateDoTaskObjectiveAndGetStatus` | `actorId`, `questId`, `objectiveId`, `progress` | Task objective |
| `ClaimReward` | `actorId`, `questId`, `rewardIndex` | Downloadable variant available |
| `DiamondSkip` | `actorId`, `questId` | Diamond skip |
| `BeginSpecialQuest` | `actorId`, `specialQuestId` | Event quest |
| `ForceCompleteCurrentQuest` | `actorId`, `questId` | Debug/force |

---

## VI. Achievements (`AMFAchievementWebService`)

| Constant | Value |
|-----------|--------|
| `MAX_ACHIEVEMENT_LEVEL` | 4 |
| `CATEGORIES_MAX` | 4 |

Endpoints : `GetAchievementData`, `GetPagedAchievements`, `ClaimReward`, `GetTotalProgress`, `GetFriendAchievementDetails`.

---

## VII. Profile (`AMFProfileService`)

| Endpoint | Parameters | Notes |
|----------|------------|-------|
| `LoadProfileSummary` | `actorId`, `loggedInActorId` | Or `LoadProfileSummaryNeb` (Nebula name) |
| `PostToWallWithModerationCall` | 8 params | MARS required ; codes 0/1/2 |
| `GetWallPosts` | `actorId`, page, size | Paged wall |
| `SetFavouritete` | `actorId`, entityId, type | Favourite |
| `RecycleItem` | `actorId`, relId, category | Recycle |
| `loadActorRoom` | `actorId`, roomId` | Profile room preview |

→ [amf/06-rooms.md](amf/06-rooms.md) · [amf/14-rewards.md](amf/14-rewards.md) · [amf/16-community.md](amf/16-community.md)

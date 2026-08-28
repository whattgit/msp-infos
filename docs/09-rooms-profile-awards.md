# II.5 — Chambres, Profil & Récompenses

## I. Chambres (`AMFRoomServiceForMobile`)

Service AMF : `MovieStarPlanet.WebService.AMFRoomServiceForMobile`  
Client : `MyRoomServices.as`

### Endpoints

| Endpoint | Paramètres | Retour | Rate limit |
|----------|------------|--------|------------|
| `LoadHouse` | `houseId`, `callingActorId` | `HouseInformation` | — |
| `LoadHouseAndSpecificRoom` | `callingActorId`, `houseId`, `roomId` | Données room | — |
| `SaveRoomWithSnapshot` | `RoomSaveInformation`, snapshot profile/medium/small (3× ByteArray) | `int` roomId ou **−429** | **Oui** (popup) |
| `LoveRoom` | `actorId`, `roomOwnerId` | — | — |

### `RoomSaveInformation` (corps sauvegarde)

| Champ | Type | Rôle |
|-------|------|------|
| `Wallpaper` | String | ID wallpaper |
| `Floor` | String | ID sol |
| `ItemsAdded` | Array | Click items placés |
| `ItemsEdited` | Array | Items modifiés |
| `ItemsRemoved` | Array | Items retirés |
| `PetsAdded` | Array | Legacy pets ajoutés |
| `PetsEdited` | Array | Legacy pets déplacés |
| `PetsRemoved` | Array | Legacy pets retirés |
| `BonstersAdded` | Array | Bonsters ajoutés |
| `BonstersEdited` | Array | Bonsters déplacés |
| `BonstersRemoved` | Array | Bonsters retirés |

Limite client : **10 pets max / salle**.

---

## II. Récompenses — `AMFAwardingService`

Service : `MovieStarPlanet.WebService.Awarding.AMFAwardingService`  
Client : `AwardingAmfService.as` · UI roue : `SpinTheWheel.as`

### II.1 `claimDailyAward(awardStr, amnt, loggedInActorId)`

Réclame une récompense quotidienne après spin roue ou mini-jeu.

| Param | Type | Description |
|-------|------|-------------|
| `awardStr` | String | Identifiant type récompense (voir table AwardingType ci-dessous) |
| `amnt` | int | Montant SC gagné sur la roue (valeur segment) |
| `loggedInActorId` | int | ID acteur connecté |

**Transformation client :** `AppSettings.getStarWheelAwardEndpoint(awardStr)` remappe les types roue en variantes `*Dwl` si client downloadable + config activée.

| Réponse | Signification |
|---------|---------------|
| `{amount, currencyType}` | Succès — ex. `currencyType: "money"` |
| `amount == -429` | Rate limit (popup) |

**Événement post-succès :** `MSPDataEvent.AWARD_DISTRUBTED`.

### II.2 Identifiants `AwardingType` (awardStr)

Source : `awarding/valueobjects/AwardingType.as`

#### Types roue — roue normale (non-VIP wheel)

| Constante client | String serveur (`awardStr`) | vipTier requis | Remap downloadable |
|------------------|----------------------------|----------------|----------------------|
| `WHEEL_AWARD_TYPE` | `"wheel"` | NON_VIP (−1) | → `"wheelDwl"` |
| `WHEEL_BASIC_AWARD_TYPE` | `"basicwheel"` | NORMAL_VIP (0) | → `"basicwheelDwl"` |
| `WHEEL_SUPER_AWARD_TYPE` | `"superwheel"` | SUPER_VIP (1) | → `"superwheelDwl"` |
| `WHEEL_ELITE_AWARD_TYPE` | `"elitewheel"` | ELITE_VIP (2) | → `"elitewheelDwl"` |
| `WHEEL_STAR_AWARD_TYPE` | `"starwheel"` | STAR_VIP (3) | → `"starwheelDwl"` |

#### Types roue — roue VIP (membership wheel)

| Constante | String serveur | vipTier |
|-----------|---------------|---------|
| `VIP_WHEEL_AWARD_TYPE` | `"vipWheel"` | (legacy) |
| `VIP_WHEEL_BASIC_AWARD_TYPE` | `"basicvipWheel"` | NORMAL_VIP |
| `VIP_WHEEL_SUPER_AWARD_TYPE` | `"supervipWheel"` | SUPER_VIP |
| `VIP_WHEEL_ELITE_AWARD_TYPE` | `"eliteVipWheel"` | ELITE_VIP |
| `VIP_WHEEL_STAR_AWARD_TYPE` | `"starVipWheel"` | STAR_VIP |

#### Pub vidéo roue

| Constante | String serveur | Usage |
|-----------|---------------|-------|
| `ADVERT_WHEEL_SPIN` | `"advertWheel"` | Spin normal après pub |
| `ADVERT_VIP_WHEEL_SPIN` | `"advertWheelVip"` | Spin VIP après pub |

#### Autres types daily

| Constante | String serveur | Usage client |
|-----------|---------------|--------------|
| `TWOPLAYER_FAME` | `"twoPlayerFame"` | Mini-jeu 2 joueurs — fame |
| `TWOPLAYER_MONEY` | `"twoPlayerMoney"` | Mini-jeu 2 joueurs — SC |
| `RETENTION_1_MONEY` | `"firstRetentionSC"` | Retention URL — **300 SC** fixe |
| `DAILY_VIP_COINS` | `"dailyVIPCoins"` | Constante définie (pas d'appel UI trouvé) |
| `DAILY_VIP_DIAMONDS` | `"dailyVIPDiamonds"` | Constante définie (pas d'appel UI trouvé) |
| `ADVERT_VIEW` | `"advertView"` | Pub générique |
| `ADVERT_VIEW_FAME` | `"advertViewFame"` | Pub fame |

#### Types intro cadeau (int, pas string)

| Constante | Valeur | Usage |
|-----------|--------|-------|
| `Clothes` | 1 | Cadeau intro vêtement |
| `StarCoins` | 2 | Cadeau intro SC |

#### Types `awardActor`

| Constante | Valeur | Signification |
|-----------|--------|---------------|
| `AWARD_TYPE_MONEY` | 0 | StarCoins |
| `AWARD_TYPE_FAME` | 1 | Fame |
| `AWARD_TYPE_MEMBERSHIP_STARCOINS` | 2 | SC membership |
| `WIN_SPEND_TYPE_DAILY_WHEEL` | 11 | Source roue daily |

### II.3 Tiers VIP (`VipTierConstants`)

| ID | Constante | Roue normale | Roue VIP |
|----|-----------|--------------|----------|
| −1 | `NON_VIP` | `wheel` | — (wheel VIP désactivée) |
| 0 | `NORMAL_VIP` | `basicwheel` | `basicvipWheel` |
| 1 | `SUPER_VIP` | `superwheel` | `supervipWheel` |
| 2 | `ELITE_VIP` | `elitewheel` | `eliteVipWheel` |
| 3 | `STAR_VIP` | `starwheel` | `starVipWheel` |

Au login, `PostLoginSequence` appelle `countAwardsLeft([types selon tier], actorId)` pour afficher spins restants.

### II.4 Segments roue (montants `amnt`)

Source : `SpinTheWheel.as` — `winnings` par segment (8 segments).

| Mode | Roue normale | Roue VIP |
|------|--------------|----------|
| Standard | `[40,20,80,20,40,20,120,20]` | `[50,25,100,25,50,25,200,25]` |
| Higher prizes (downloadable) | Config serveur `HigherSpinWheelPrizesOnDownloadable` (CSV) ou `[80,40,160,40,80,40,240,40]` | `[50,25,100,25,50,25,200,25]` |

Respin diamant (`BuyStarcoinsWheelSpin`) : serveur retourne `regularWheelReward` + `vipWheelReward` directement.

### II.5 `claimAdvertViewAward(type, amount, actorId)`

Appelé quand l'utilisateur regarde une pub pour respin (`adWatched == true`).

| Param | Exemple |
|-------|---------|
| `type` | `"advertWheel"` ou `"advertWheelVip"` |
| `amount` | Segment SC gagné |
| `actorId` | ID acteur |

Rate limit : `amount == -429`.

### II.6 `claimAdvertAwardByCampaign(campaignId)`

Récompense campagne pub incentivée (`CampaignIncentivizedVideoAdHandler.obtainReward`).

| Param | Description |
|-------|-------------|
| `campaignId` | ID campagne pub (handler) |

Rate limit : `amount == -429`.

### II.7 Endpoints auxiliaires

| Endpoint | Paramètres | Rôle |
|----------|------------|------|
| `countAwardsLeft` | `awardStr[]`, `actorId` | Spins restants par type |
| `hasAnyDailyAwardLeft` | `awardStr`, `actorId` | Un type encore dispo ? |
| `hasAllDailyAwardLeft` | `awardStr[]`, `actorId` | Tous types dispo ? |
| `hasSomeDailyAwardLeft` | `awardStr[]`, `actorId` | Au moins un dispo ? |
| `awardActor` | `actorId, amount, type, winSpendType` | Crédit direct |
| `RequestIntroductionAward` | `actorId` | Cadeau nouveau joueur |
| `GetWheelData` | — | Config roue serveur (non appelé UI) |
| `SpinWheel` | `wheelId` | Legacy — **non utilisé** par SpinTheWheel.as |
| `BuyDiamondRespin` | — | Legacy Awarding — **UI utilise** `BuyStarcoinsWheelSpin` |

### II.8 Respin diamant (Spending, pas Awarding)

| Propriété | Valeur |
|-----------|--------|
| Endpoint | `AMFSpendingService.BuyStarcoinsWheelSpin(actorId)` |
| Prix UI | **1 💎** (`SPIN_AGAIN_PRICE`) |
| Codes | `0` OK · `−2` pas assez 💎 · `−3` paiement récurrent inéligible |
| Retour | `{regularWheelReward, vipWheelReward}` |

---

## III. Tirelire (`AMFPiggyBankService`)

| Endpoint | Params | Rôle |
|----------|--------|------|
| `GetPiggyBank` | — | Sync `{StarCoins, Fame, Diamonds}` |
| `DestroyPiggyBank` | — | Casse tirelire |
| `CanDestroyPiggyBank` | — | Vérifie possibilité |

Limites non-VIP : **2500 SC** · **5000 fame** (VIP = illimité).

Bonus daily login (`DailyBonusType` post-login) → fame tirelire selon tier :

| vipTier | Fame ajoutée |
|---------|--------------|
| NORMAL_VIP | 10 |
| SUPER_VIP / ELITE_VIP | 30 |
| STAR_VIP | 60 |

---

## IV. Notification center — `ClaimBonus2`

Service : `AMFNotificationCenterService`  
Client : `NotificationCenterAmfService.as` · UI : `FameChestPopup.as`

```
ClaimBonus2(actorId, contentTypes[])
```

| Param | Type | Description |
|-------|------|-------------|
| `actorId` | int | Acteur |
| `contentTypes` | int[] | IDs `FameTypeUtils` des bonus cochés |

Rate limit : `ErrorCode == -429` (popup).

### IDs `contentTypes` (`FameTypeUtils`)

| ID | Constante | Feature |
|----|-----------|---------|
| 1 | `ARTBOOK` | Artbooks |
| 2 | `MOVIE_WATCH` | Films visionnés |
| 3 | `LOOK` | Looks |
| 4 | `LOOK_BOUGHT` | Looks achetés |
| 5 | `AUTOGRAPH` | Autographes |
| 6 | `MOVIE_STARRED` | Films starring |
| 7 | `DESIGN` | Designs |
| 8 | `ROOM` | Chambres |
| 9 | `YOUTUBE` | Vidéos YouTube |
| 10 | `WAYD` | Statuts WAYD |
| 13 | `CREATE_RATE` | Create & rate |
| 14 | `APP` | Apps |
| 15 | `PHOTO` | Photos |
| 16 | `PET` | Pets caressés |
| 17 | `DESIGN_BOUGHT` | Designs achetés |

Chaque `NotificationValueObject` contient `BonusFame`, `BonusStarCoins`, `ContentType`, `Claimed`.

---

## V. Quêtes (`AMFQuestService`)

| Endpoint | Paramètres | Notes |
|----------|------------|-------|
| `GetAllQuestStatus` | `actorId` | Variante downloadable : `GetAllQuestStatusForDownloadableClient` |
| `BeginQuest` | `actorId`, `questId` | Démarre quête |
| `UpdateGotoObjectiveAndGetStatus` | `actorId`, `questId`, `objectiveId` | Objectif « aller à » |
| `UpdateDoTaskObjectiveAndGetStatus` | `actorId`, `questId`, `objectiveId`, `progress` | Objectif tâche |
| `ClaimReward` | `actorId`, `questId`, `rewardIndex` | Variante downloadable disponible |
| `DiamondSkip` | `actorId`, `questId` | Skip diamant |
| `BeginSpecialQuest` | `actorId`, `specialQuestId` | Quête événement |
| `ForceCompleteCurrentQuest` | `actorId`, `questId` | Debug/force |

---

## VI. Achievements (`AMFAchievementWebService`)

| Constante | Valeur |
|-----------|--------|
| `MAX_ACHIEVEMENT_LEVEL` | 4 |
| `CATEGORIES_MAX` | 4 |

Endpoints : `GetAchievementData`, `GetPagedAchievements`, `ClaimReward`, `GetTotalProgress`, `GetFriendAchievementDetails`.

---

## VII. Profil (`AMFProfileService`)

| Endpoint | Paramètres | Notes |
|----------|------------|-------|
| `LoadProfileSummary` | `actorId`, `loggedInActorId` | Ou `LoadProfileSummaryNeb` (Nebula name) |
| `PostToWallWithModerationCall` | 8 params | MARS requis ; codes 0/1/2 |
| `GetWallPosts` | `actorId`, page, size | Mur paginé |
| `SetFavorite` | `actorId`, entityId, type | Favori |
| `RecycleItem` | `actorId`, relId, category | Recycler |
| `loadActorRoom` | `actorId`, roomId` | Preview chambre profil |

→ [amf/06-rooms.md](amf/06-rooms.md) · [amf/14-rewards.md](amf/14-rewards.md) · [amf/16-community.md](amf/16-community.md)

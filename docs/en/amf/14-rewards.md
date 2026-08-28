# III.14 — Quests & rewards

> **EN** · [Français](../../fr/amf/14-rewards.md)


Quests, achievements, wheel, daily awards.

## Rate limits (this category)

| Endpoint | Service | `-429` field | Popup |
|----------|---------|--------------|-------|
| `SpinWheel` | `AMFAwardingService` | `Status` | Yes |
| `claimDailyAward` | `AMFAwardingService` | `amount` | Yes |
| `claimAdvertViewAward` | `AMFAwardingService` | `amount` | Yes |
| `claimAdvertAwardByCampaign` | `AMFAwardingService` | `amount` | Yes |

## `WebService.AMFAwardService`

**AMF path:** `MovieStarPlanet.WebService.AMFAwardService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `RequestAnchorCharacterIntroductionAward` | actorId | AMF endpoint `RequestAnchorCharacterIntroductionAward`. | — |

### Endpoint details

#### `RequestAnchorCharacterIntroductionAward`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/createuser/AnchorIntroduction.as` |
| Behavior | AMF endpoint `RequestAnchorCharacterIntroductionAward`. |

## `WebService.Achievement.AMFAchievementWebService`

**AMF path:** `MovieStarPlanet.WebService.Achievement.AMFAchievementWebService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CheckLoginAchievements` | param1 | Checks login achievements. | — |
| `ClaimReward` | param1, param2 | AMF endpoint `ClaimReward`. | — |
| `GetAchievementData` | — | Fetches achievement data. | — |
| `GetActorAchievementProgressAll` | actorId | Fetches actor achievement progress all. | — |
| `GetArtbookStickers` | param1 | Fetches artbook stickers. | — |
| `GetClaimableCategories` | param1 | Fetches claimable categories. | — |
| `GetPagedAchievements` | actorId, category, pageIndex, pageSize | Paged list — Paged Achievements. | — |
| `GetTotalProgress` | actorId, category | Fetches total progress. | — |

### Endpoint details

#### `CheckLoginAchievements`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / callers | `LoginRequiredSetupCommand.as` |
| Behavior | Checks login achievements. |

#### `ClaimReward`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/achievement/AchievementAMFWebService.as` (+1) |
| UI / callers | `AchievementsPage.as`, `CommandClaimQuestReward.as`, `SpecialEventTasksView.as` |
| Behavior | AMF endpoint `ClaimReward`. |

#### `GetAchievementData`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| Behavior | Fetches achievement data. |

#### `GetActorAchievementProgressAll`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| Behavior | Fetches actor achievement progress all. |

#### `GetArtbookStickers`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+1) |
| UI / callers | `ScrapBlogItemBrowser.as` |
| Behavior | Fetches artbook stickers. |

#### `GetClaimableCategories`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / callers | `ProfileFrameIcon.as` |
| Behavior | Fetches claimable categories. |

#### `GetPagedAchievements`

| Property | Value |
|----------|-------|
| Parameters | actorId, category, pageIndex, pageSize |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / callers | `AchievementsPage.as` |
| Behavior | Paged list — Paged Achievements. |

#### `GetTotalProgress`

| Property | Value |
|----------|-------|
| Parameters | actorId, category |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / callers | `AchievementsPage.as` |
| Behavior | Fetches total progress. |

## `WebService.Awarding.AMFAwardingService`

**AMF path:** `MovieStarPlanet.WebService.Awarding.AMFAwardingService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BuyDiamondRespin` | — | Achat respin diamant roue (endpoint Awarding). **UI utilise** `BuyStarcoinsWheelSpin` (Spending) à la place. | — |
| `GetWheelData` | — | Loads config roue serveur (segments/prix). Aucun appelant UI trouvé dans le client. | — |
| `RequestIntroductionAward` | actorId | Cadeau introduction nouveau joueur ; retour `AmfServiceResultData`. | — |
| `SpinWheel` | wheelId | Tour roue legacy par `wheelId` ; retour `{Status}` — `Status==-429` rate limit. **Non utilisé** par SpinTheWheel.as (qui appelle claimDailyAward). | `-429` |
| `awardActor` | actorId, amount, type, winSpendType | Crédite acteur directement : `[actorId, amount, type, winSpendType]` — types 0=money, 1=fame, 2=membership SC ; winSpendType 11=daily wheel. | — |
| `claimAdvertAwardByCampaign` | campaignId | Récompense campagne pub incentivée ; param `campaignId` uniquement. | `-429` |
| `claimAdvertViewAward` | type, amount, actorId | Récompense après pub vidéo roue ; params `[type, amount, actorId]` — types `advertWheel` / `advertWheelVip`. | `-429` |
| `claimDailyAward` | awardStr, amnt, loggedInActorId | Réclame une récompense daily ; `awardStr` = type AwardingType ; `amnt` = montant gagné à la roue ; retour `{amount, currencyType}`. Rate limit `amount==-429`. | `-429` |
| `countAwardsLeft` | awardStr[], actorId | Compte spins restants ; `[awardStr[], actorId]` — appelé au login PostLoginSequence selon vipTier. | — |
| `hasAllDailyAwardLeft` | awardStr[], actorId | Checks si tous les types d'un tableau sont encore disponibles. | — |
| `hasAnyDailyAwardLeft` | awardStr, actorId | Checks si un type daily reste (ex. retention `firstRetentionSC`). | — |
| `hasSomeDailyAwardLeft` | awardStr[], actorId | Variante : au moins un type du tableau disponible. | — |

### Endpoint details

#### `BuyDiamondRespin`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Behavior | Achat respin diamant roue (endpoint Awarding). **UI utilise** `BuyStarcoinsWheelSpin` (Spending) à la place. |

#### `GetWheelData`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Behavior | Loads config roue serveur (segments/prix). Aucun appelant UI trouvé dans le client. |

#### `RequestIntroductionAward`

| Property | Value |
|----------|-------|
| Parameters | actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / callers | `RequestCache.as`, `SignupPresents.as` |
| Behavior | Cadeau introduction nouveau joueur ; retour `AmfServiceResultData`. |

#### `SpinWheel`

| Property | Value |
|----------|-------|
| Parameters | wheelId |
| AMF ticket | Yes |
| Rate limit | `-429` on `Status` (popup) |
| Return codes | Réponse `{Status}` · `Status==-429` · legacy (UI utilise claimDailyAward) |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / callers | `DebugSpinButton.as` |
| Behavior | Tour roue legacy par `wheelId` ; retour `{Status}` — `Status==-429` rate limit. **Non utilisé** par SpinTheWheel.as (qui appelle claimDailyAward). |

#### `awardActor`

| Property | Value |
|----------|-------|
| Parameters | actorId, amount, type, winSpendType |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | type: 0=SC · 1=fame · 2=membership SC · winSpendType 11=daily wheel |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Behavior | Crédite acteur directement : `[actorId, amount, type, winSpendType]` — types 0=money, 1=fame, 2=membership SC ; winSpendType 11=daily wheel. |

#### `claimAdvertAwardByCampaign`

| Property | Value |
|----------|-------|
| Parameters | campaignId |
| AMF ticket | Yes |
| Rate limit | `-429` on `amount` (popup) |
| Return codes | Réponse `{amount}` · `amount==-429` · `campaignId` depuis handler pub |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / callers | `CampaignIncentivizedVideoAdHandler.as` |
| Behavior | Récompense campagne pub incentivée ; param `campaignId` uniquement. |

#### `claimAdvertViewAward`

| Property | Value |
|----------|-------|
| Parameters | type, amount, actorId |
| AMF ticket | Yes |
| Rate limit | `-429` on `amount` (popup) |
| Return codes | Réponse `{amount}` · `amount==-429` · types `advertWheel` / `advertWheelVip` |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / callers | `SpinTheWheel.as` |
| Behavior | Récompense après pub vidéo roue ; params `[type, amount, actorId]` — types `advertWheel` / `advertWheelVip`. |

#### `claimDailyAward`

| Property | Value |
|----------|-------|
| Parameters | awardStr, amnt, loggedInActorId |
| AMF ticket | Yes |
| Rate limit | `-429` on `amount` (popup) |
| Return codes | Réponse `{amount, currencyType}` · `amount==-429` rate limit · `currencyType` ex. `"money"` |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / callers | `DebugSpinButton.as`, `SpinTheWheel.as`, `ParseUrlRetentionParamsCommand.as`, `MultiPlayerGame.as` |
| Behavior | Réclame une récompense daily ; `awardStr` = type AwardingType ; `amnt` = montant gagné à la roue ; retour `{amount, currencyType}`. Rate limit `amount==-429`. |

#### `countAwardsLeft`

| Property | Value |
|----------|-------|
| Parameters | awardStr[], actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / callers | `PostLoginSequence.as` |
| Behavior | Compte spins restants ; `[awardStr[], actorId]` — appelé au login PostLoginSequence selon vipTier. |

#### `hasAllDailyAwardLeft`

| Property | Value |
|----------|-------|
| Parameters | awardStr[], actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Behavior | Checks si tous les types d'un tableau sont encore disponibles. |

#### `hasAnyDailyAwardLeft`

| Property | Value |
|----------|-------|
| Parameters | awardStr, actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / callers | `ParseUrlRetentionParamsCommand.as` |
| Behavior | Checks si un type daily reste (ex. retention `firstRetentionSC`). |

#### `hasSomeDailyAwardLeft`

| Property | Value |
|----------|-------|
| Parameters | awardStr[], actorId |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Behavior | Variante : au moins un type du tableau disponible. |

## `WebService.Holiday.AMFHolidayService`

**AMF path:** `MovieStarPlanet.WebService.Holiday.AMFHolidayService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `GetReceivedChristmasPresents` | param1, param2 | Fetches received christmas presents. | — |
| `RequestChristmasPresent` | param1, param2, param3 | AMF endpoint `RequestChristmasPresent`. | — |

### Endpoint details

#### `GetReceivedChristmasPresents`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/Holiday/ChristmasCalendar/service/HolidayAmfService.as` |
| UI / callers | `ChristmasCalendar.as`, `HolidayCache.as`, `HolidayService.as` |
| Behavior | Fetches received christmas presents. |

#### `RequestChristmasPresent`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/Holiday/ChristmasCalendar/service/HolidayAmfService.as` |
| UI / callers | `ChristmasCalendar.as`, `HolidayService.as` |
| Behavior | AMF endpoint `RequestChristmasPresent`. |

## `WebService.PiggyBank.AMFPiggyBankService`

**AMF path:** `MovieStarPlanet.WebService.PiggyBank.AMFPiggyBankService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `CanDestroyPiggyBank` | — | AMF endpoint `CanDestroyPiggyBank`. | — |
| `DestroyPiggyBank` | — | AMF endpoint `DestroyPiggyBank`. | — |
| `GetPiggyBank` | — | Fetches piggy bank. | — |

### Endpoint details

#### `CanDestroyPiggyBank`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/piggybank/service/AMFPiggyBankService.as` |
| UI / callers | `BecomeVipActorReloadListener.as` |
| Behavior | AMF endpoint `CanDestroyPiggyBank`. |

#### `DestroyPiggyBank`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/piggybank/service/AMFPiggyBankService.as` |
| UI / callers | `PiggyCollectBase.as` |
| Behavior | AMF endpoint `DestroyPiggyBank`. |

#### `GetPiggyBank`

| Property | Value |
|----------|-------|
| Parameters | — |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/piggybank/service/AMFPiggyBankService.as` |
| UI / callers | `PiggyBankAmountManager.as` |
| Behavior | Fetches piggy bank. |

## `WebService.Quest.AMFQuestService`

**AMF path:** `MovieStarPlanet.WebService.Quest.AMFQuestService`

| Endpoint | Parameters | Behavior | Rate limit |
|----------|------------|----------|------------|
| `BeginQuest` | param1, param2 | AMF endpoint `BeginQuest`. | — |
| `BeginSpecialQuest` | param1, param2 | AMF endpoint `BeginSpecialQuest`. | — |
| `ClaimReward` | param1, param2, param3 | AMF endpoint `ClaimReward`. | — |
| `ClaimRewardForDownloadableClient` | param1, param2, param3 | AMF endpoint `ClaimRewardForDownloadableClient`. | — |
| `ClaimSpecialQuestBaseReward` | param1, param2 | AMF endpoint `ClaimSpecialQuestBaseReward`. | — |
| `ClaimSpecialQuestSubOrFinalReward` | param1, param2 | AMF endpoint `ClaimSpecialQuestSubOrFinalReward`. | — |
| `DiamondSkip` | param1, param2 | AMF endpoint `DiamondSkip`. | — |
| `ForceCompleteCurrentQuest` | param1, param2 | AMF endpoint `ForceCompleteCurrentQuest`. | — |
| `ForceCompleteCurrentQuestForDownloadableClient` | param1, param2 | AMF endpoint `ForceCompleteCurrentQuestForDownloadableClient`. | — |
| `GetAllQuestStatus` | param1 | Fetches all quest status. | — |
| `GetAllQuestStatusForDownloadableClient` | param1 | Fetches all quest status for downloadable client. | — |
| `GetGiftHuntQuestData` | param1, param2 | Fetches gift hunt quest data. | — |
| `ResetNotifications` | param1, param2 | AMF endpoint `ResetNotifications`. | — |
| `UpdateDoTaskObjectiveAndGetStatus` | param1, param2, param3, param4 | Updates ate do task objective and get status. | — |
| `UpdateGotoObjectiveAndGetStatus` | param1, param2, param3 | Updates ate goto objective and get status. | — |
| `UpdateSpecialQuestObjectiveOld` | param1, param2, param3 | Updates ate special quest objective old. | — |
| `UpdateSpecialQuestObjectives` | param1, param2, param3 | Updates ate special quest objectives. | — |

### Endpoint details

#### `BeginQuest`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandBeginQuest.as` |
| Behavior | AMF endpoint `BeginQuest`. |

#### `BeginSpecialQuest`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandOpenTasksView.as` |
| Behavior | AMF endpoint `BeginSpecialQuest`. |

#### `ClaimReward`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` (+1) |
| UI / callers | `AchievementsPage.as`, `CommandClaimQuestReward.as`, `SpecialEventTasksView.as` |
| Behavior | AMF endpoint `ClaimReward`. |

#### `ClaimRewardForDownloadableClient`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| Behavior | AMF endpoint `ClaimRewardForDownloadableClient`. |

#### `ClaimSpecialQuestBaseReward`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandClaimQuestReward.as` |
| Behavior | AMF endpoint `ClaimSpecialQuestBaseReward`. |

#### `ClaimSpecialQuestSubOrFinalReward`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandClaimReward.as` |
| Behavior | AMF endpoint `ClaimSpecialQuestSubOrFinalReward`. |

#### `DiamondSkip`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandSkipForDiamond.as` |
| Behavior | AMF endpoint `DiamondSkip`. |

#### `ForceCompleteCurrentQuest`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CareerQuestObserver.as` |
| Behavior | AMF endpoint `ForceCompleteCurrentQuest`. |

#### `ForceCompleteCurrentQuestForDownloadableClient`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| Behavior | AMF endpoint `ForceCompleteCurrentQuestForDownloadableClient`. |

#### `GetAllQuestStatus`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandInitCareers.as` |
| Behavior | Fetches all quest status. |

#### `GetAllQuestStatusForDownloadableClient`

| Property | Value |
|----------|-------|
| Parameters | param1 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| Behavior | Fetches all quest status for downloadable client. |

#### `GetGiftHuntQuestData`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandBeginQuest.as`, `CommandInitCareers.as`, `CommandInitSpecialQuest.as`, `CommandOpenTasksView.as` |
| Behavior | Fetches gift hunt quest data. |

#### `ResetNotifications`

| Property | Value |
|----------|-------|
| Parameters | param1, param2 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandSelectCareer.as`, `CommandShowQuestPopup.as` |
| Behavior | AMF endpoint `ResetNotifications`. |

#### `UpdateDoTaskObjectiveAndGetStatus`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3, param4 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CareerQuestObserver.as` |
| Behavior | Updates ate do task objective and get status. |

#### `UpdateGotoObjectiveAndGetStatus`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CareerQuestObserver.as` |
| Behavior | Updates ate goto objective and get status. |

#### `UpdateSpecialQuestObjectiveOld`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandUpdateObjectives.as` |
| Behavior | Updates ate special quest objective old. |

#### `UpdateSpecialQuestObjectives`

| Property | Value |
|----------|-------|
| Parameters | param1, param2, param3 |
| AMF ticket | Yes |
| Rate limit | — |
| Return codes | Voir section II.5 — constantes AwardingType |
| AMF client | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / callers | `CommandUpdateObjectives.as` |
| Behavior | Updates ate special quest objectives. |

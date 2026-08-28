# V.14 — Quêtes & récompenses

Quests, achievements, roue, daily awards.

## Rate limits (cette catégorie)

| Endpoint | Service | Champ `-429` | Popup |
|----------|---------|--------------|-------|
| `SpinWheel` | `AMFAwardingService` | `Status` | Oui |
| `claimDailyAward` | `AMFAwardingService` | `amount` | Oui |
| `claimAdvertViewAward` | `AMFAwardingService` | `amount` | Oui |
| `claimAdvertAwardByCampaign` | `AMFAwardingService` | `amount` | Oui |

## `WebService.AMFAwardService`

**Chemin AMF :** `MovieStarPlanet.WebService.AMFAwardService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `RequestAnchorCharacterIntroductionAward` | actorId | Endpoint AMF `RequestAnchorCharacterIntroductionAward`. | — |

### Détail endpoints

#### `RequestAnchorCharacterIntroductionAward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/createuser/AnchorIntroduction.as` |
| Fonctionnement | Endpoint AMF `RequestAnchorCharacterIntroductionAward`. |

## `WebService.Achievement.AMFAchievementWebService`

**Chemin AMF :** `MovieStarPlanet.WebService.Achievement.AMFAchievementWebService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CheckLoginAchievements` | param1 | Vérifie login achievements. | — |
| `ClaimReward` | param1, param2 | Endpoint AMF `ClaimReward`. | — |
| `GetAchievementData` | — | Récupère achievement data. | — |
| `GetActorAchievementProgressAll` | actorId | Récupère actor achievement progress all. | — |
| `GetArtbookStickers` | param1 | Récupère artbook stickers. | — |
| `GetClaimableCategories` | param1 | Récupère claimable categories. | — |
| `GetPagedAchievements` | actorId, category, pageIndex, pageSize | Liste paginée — Paged Achievements. | — |
| `GetTotalProgress` | actorId, category | Récupère total progress. | — |

### Détail endpoints

#### `CheckLoginAchievements`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / appelants | `LoginRequiredSetupCommand.as` |
| Fonctionnement | Vérifie login achievements. |

#### `ClaimReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/achievement/AchievementAMFWebService.as` (+1) |
| UI / appelants | `AchievementsPage.as`, `CommandClaimQuestReward.as`, `SpecialEventTasksView.as` |
| Fonctionnement | Endpoint AMF `ClaimReward`. |

#### `GetAchievementData`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| Fonctionnement | Récupère achievement data. |

#### `GetActorAchievementProgressAll`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| Fonctionnement | Récupère actor achievement progress all. |

#### `GetArtbookStickers`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/ItemDrawer/service/ItemDrawerAMFService.as` (+1) |
| UI / appelants | `ScrapBlogItemBrowser.as` |
| Fonctionnement | Récupère artbook stickers. |

#### `GetClaimableCategories`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / appelants | `ProfileFrameIcon.as` |
| Fonctionnement | Récupère claimable categories. |

#### `GetPagedAchievements`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, category, pageIndex, pageSize |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / appelants | `AchievementsPage.as` |
| Fonctionnement | Liste paginée — Paged Achievements. |

#### `GetTotalProgress`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, category |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/achievement/AchievementAMFWebService.as` |
| UI / appelants | `AchievementsPage.as` |
| Fonctionnement | Récupère total progress. |

## `WebService.Awarding.AMFAwardingService`

**Chemin AMF :** `MovieStarPlanet.WebService.Awarding.AMFAwardingService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BuyDiamondRespin` | — | Achat respin diamant roue (endpoint Awarding). **UI utilise** `BuyStarcoinsWheelSpin` (Spending) à la place. | — |
| `GetWheelData` | — | Charge config roue serveur (segments/prix). Aucun appelant UI trouvé dans le client. | — |
| `RequestIntroductionAward` | actorId | Cadeau introduction nouveau joueur ; retour `AmfServiceResultData`. | — |
| `SpinWheel` | wheelId | Tour roue legacy par `wheelId` ; retour `{Status}` — `Status==-429` rate limit. **Non utilisé** par SpinTheWheel.as (qui appelle claimDailyAward). | `-429` |
| `awardActor` | actorId, amount, type, winSpendType | Crédite acteur directement : `[actorId, amount, type, winSpendType]` — types 0=money, 1=fame, 2=membership SC ; winSpendType 11=daily wheel. | — |
| `claimAdvertAwardByCampaign` | campaignId | Récompense campagne pub incentivée ; param `campaignId` uniquement. | `-429` |
| `claimAdvertViewAward` | type, amount, actorId | Récompense après pub vidéo roue ; params `[type, amount, actorId]` — types `advertWheel` / `advertWheelVip`. | `-429` |
| `claimDailyAward` | awardStr, amnt, loggedInActorId | Réclame une récompense daily ; `awardStr` = type AwardingType ; `amnt` = montant gagné à la roue ; retour `{amount, currencyType}`. Rate limit `amount==-429`. | `-429` |
| `countAwardsLeft` | awardStr[], actorId | Compte spins restants ; `[awardStr[], actorId]` — appelé au login PostLoginSequence selon vipTier. | — |
| `hasAllDailyAwardLeft` | awardStr[], actorId | Vérifie si tous les types d'un tableau sont encore disponibles. | — |
| `hasAnyDailyAwardLeft` | awardStr, actorId | Vérifie si un type daily reste (ex. retention `firstRetentionSC`). | — |
| `hasSomeDailyAwardLeft` | awardStr[], actorId | Variante : au moins un type du tableau disponible. | — |

### Détail endpoints

#### `BuyDiamondRespin`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | `SpendingProvider` / `Code` : 0 · −1 · −2 💎 · −3 déjà acheté · −4 SC · −5 créateur design |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Fonctionnement | Achat respin diamant roue (endpoint Awarding). **UI utilise** `BuyStarcoinsWheelSpin` (Spending) à la place. |

#### `GetWheelData`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Fonctionnement | Charge config roue serveur (segments/prix). Aucun appelant UI trouvé dans le client. |

#### `RequestIntroductionAward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / appelants | `RequestCache.as`, `SignupPresents.as` |
| Fonctionnement | Cadeau introduction nouveau joueur ; retour `AmfServiceResultData`. |

#### `SpinWheel`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | wheelId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `Status` (popup) |
| Codes retour | Réponse `{Status}` · `Status==-429` · legacy (UI utilise claimDailyAward) |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / appelants | `DebugSpinButton.as` |
| Fonctionnement | Tour roue legacy par `wheelId` ; retour `{Status}` — `Status==-429` rate limit. **Non utilisé** par SpinTheWheel.as (qui appelle claimDailyAward). |

#### `awardActor`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | actorId, amount, type, winSpendType |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | type: 0=SC · 1=fame · 2=membership SC · winSpendType 11=daily wheel |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Fonctionnement | Crédite acteur directement : `[actorId, amount, type, winSpendType]` — types 0=money, 1=fame, 2=membership SC ; winSpendType 11=daily wheel. |

#### `claimAdvertAwardByCampaign`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | campaignId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `amount` (popup) |
| Codes retour | Réponse `{amount}` · `amount==-429` · `campaignId` depuis handler pub |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / appelants | `CampaignIncentivizedVideoAdHandler.as` |
| Fonctionnement | Récompense campagne pub incentivée ; param `campaignId` uniquement. |

#### `claimAdvertViewAward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | type, amount, actorId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `amount` (popup) |
| Codes retour | Réponse `{amount}` · `amount==-429` · types `advertWheel` / `advertWheelVip` |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / appelants | `SpinTheWheel.as` |
| Fonctionnement | Récompense après pub vidéo roue ; params `[type, amount, actorId]` — types `advertWheel` / `advertWheelVip`. |

#### `claimDailyAward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | awardStr, amnt, loggedInActorId |
| Ticket AMF | Oui |
| Rate limit | `-429` sur `amount` (popup) |
| Codes retour | Réponse `{amount, currencyType}` · `amount==-429` rate limit · `currencyType` ex. `"money"` |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / appelants | `DebugSpinButton.as`, `SpinTheWheel.as`, `ParseUrlRetentionParamsCommand.as`, `MultiPlayerGame.as` |
| Fonctionnement | Réclame une récompense daily ; `awardStr` = type AwardingType ; `amnt` = montant gagné à la roue ; retour `{amount, currencyType}`. Rate limit `amount==-429`. |

#### `countAwardsLeft`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | awardStr[], actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / appelants | `PostLoginSequence.as` |
| Fonctionnement | Compte spins restants ; `[awardStr[], actorId]` — appelé au login PostLoginSequence selon vipTier. |

#### `hasAllDailyAwardLeft`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | awardStr[], actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Fonctionnement | Vérifie si tous les types d'un tableau sont encore disponibles. |

#### `hasAnyDailyAwardLeft`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | awardStr, actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| UI / appelants | `ParseUrlRetentionParamsCommand.as` |
| Fonctionnement | Vérifie si un type daily reste (ex. retention `firstRetentionSC`). |

#### `hasSomeDailyAwardLeft`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | awardStr[], actorId |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/awarding/service/AwardingAmfService.as` |
| Fonctionnement | Variante : au moins un type du tableau disponible. |

## `WebService.Holiday.AMFHolidayService`

**Chemin AMF :** `MovieStarPlanet.WebService.Holiday.AMFHolidayService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `GetReceivedChristmasPresents` | param1, param2 | Récupère received christmas presents. | — |
| `RequestChristmasPresent` | param1, param2, param3 | Endpoint AMF `RequestChristmasPresent`. | — |

### Détail endpoints

#### `GetReceivedChristmasPresents`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/Holiday/ChristmasCalendar/service/HolidayAmfService.as` |
| UI / appelants | `ChristmasCalendar.as`, `HolidayCache.as`, `HolidayService.as` |
| Fonctionnement | Récupère received christmas presents. |

#### `RequestChristmasPresent`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/Holiday/ChristmasCalendar/service/HolidayAmfService.as` |
| UI / appelants | `ChristmasCalendar.as`, `HolidayService.as` |
| Fonctionnement | Endpoint AMF `RequestChristmasPresent`. |

## `WebService.PiggyBank.AMFPiggyBankService`

**Chemin AMF :** `MovieStarPlanet.WebService.PiggyBank.AMFPiggyBankService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `CanDestroyPiggyBank` | — | Endpoint AMF `CanDestroyPiggyBank`. | — |
| `DestroyPiggyBank` | — | Endpoint AMF `DestroyPiggyBank`. | — |
| `GetPiggyBank` | — | Récupère piggy bank. | — |

### Détail endpoints

#### `CanDestroyPiggyBank`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/piggybank/service/AMFPiggyBankService.as` |
| UI / appelants | `BecomeVipActorReloadListener.as` |
| Fonctionnement | Endpoint AMF `CanDestroyPiggyBank`. |

#### `DestroyPiggyBank`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/piggybank/service/AMFPiggyBankService.as` |
| UI / appelants | `PiggyCollectBase.as` |
| Fonctionnement | Endpoint AMF `DestroyPiggyBank`. |

#### `GetPiggyBank`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | — |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/piggybank/service/AMFPiggyBankService.as` |
| UI / appelants | `PiggyBankAmountManager.as` |
| Fonctionnement | Récupère piggy bank. |

## `WebService.Quest.AMFQuestService`

**Chemin AMF :** `MovieStarPlanet.WebService.Quest.AMFQuestService`

| Endpoint | Paramètres | Fonction | Rate limit |
|----------|------------|----------|------------|
| `BeginQuest` | param1, param2 | Endpoint AMF `BeginQuest`. | — |
| `BeginSpecialQuest` | param1, param2 | Endpoint AMF `BeginSpecialQuest`. | — |
| `ClaimReward` | param1, param2, param3 | Endpoint AMF `ClaimReward`. | — |
| `ClaimRewardForDownloadableClient` | param1, param2, param3 | Endpoint AMF `ClaimRewardForDownloadableClient`. | — |
| `ClaimSpecialQuestBaseReward` | param1, param2 | Endpoint AMF `ClaimSpecialQuestBaseReward`. | — |
| `ClaimSpecialQuestSubOrFinalReward` | param1, param2 | Endpoint AMF `ClaimSpecialQuestSubOrFinalReward`. | — |
| `DiamondSkip` | param1, param2 | Endpoint AMF `DiamondSkip`. | — |
| `ForceCompleteCurrentQuest` | param1, param2 | Endpoint AMF `ForceCompleteCurrentQuest`. | — |
| `ForceCompleteCurrentQuestForDownloadableClient` | param1, param2 | Endpoint AMF `ForceCompleteCurrentQuestForDownloadableClient`. | — |
| `GetAllQuestStatus` | param1 | Récupère all quest status. | — |
| `GetAllQuestStatusForDownloadableClient` | param1 | Récupère all quest status for downloadable client. | — |
| `GetGiftHuntQuestData` | param1, param2 | Récupère gift hunt quest data. | — |
| `ResetNotifications` | param1, param2 | Endpoint AMF `ResetNotifications`. | — |
| `UpdateDoTaskObjectiveAndGetStatus` | param1, param2, param3, param4 | Met à jour ate do task objective and get status. | — |
| `UpdateGotoObjectiveAndGetStatus` | param1, param2, param3 | Met à jour ate goto objective and get status. | — |
| `UpdateSpecialQuestObjectiveOld` | param1, param2, param3 | Met à jour ate special quest objective old. | — |
| `UpdateSpecialQuestObjectives` | param1, param2, param3 | Met à jour ate special quest objectives. | — |

### Détail endpoints

#### `BeginQuest`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandBeginQuest.as` |
| Fonctionnement | Endpoint AMF `BeginQuest`. |

#### `BeginSpecialQuest`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandOpenTasksView.as` |
| Fonctionnement | Endpoint AMF `BeginSpecialQuest`. |

#### `ClaimReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` (+1) |
| UI / appelants | `AchievementsPage.as`, `CommandClaimQuestReward.as`, `SpecialEventTasksView.as` |
| Fonctionnement | Endpoint AMF `ClaimReward`. |

#### `ClaimRewardForDownloadableClient`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| Fonctionnement | Endpoint AMF `ClaimRewardForDownloadableClient`. |

#### `ClaimSpecialQuestBaseReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandClaimQuestReward.as` |
| Fonctionnement | Endpoint AMF `ClaimSpecialQuestBaseReward`. |

#### `ClaimSpecialQuestSubOrFinalReward`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandClaimReward.as` |
| Fonctionnement | Endpoint AMF `ClaimSpecialQuestSubOrFinalReward`. |

#### `DiamondSkip`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandSkipForDiamond.as` |
| Fonctionnement | Endpoint AMF `DiamondSkip`. |

#### `ForceCompleteCurrentQuest`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CareerQuestObserver.as` |
| Fonctionnement | Endpoint AMF `ForceCompleteCurrentQuest`. |

#### `ForceCompleteCurrentQuestForDownloadableClient`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| Fonctionnement | Endpoint AMF `ForceCompleteCurrentQuestForDownloadableClient`. |

#### `GetAllQuestStatus`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandInitCareers.as` |
| Fonctionnement | Récupère all quest status. |

#### `GetAllQuestStatusForDownloadableClient`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| Fonctionnement | Récupère all quest status for downloadable client. |

#### `GetGiftHuntQuestData`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandBeginQuest.as`, `CommandInitCareers.as`, `CommandInitSpecialQuest.as`, `CommandOpenTasksView.as` |
| Fonctionnement | Récupère gift hunt quest data. |

#### `ResetNotifications`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandSelectCareer.as`, `CommandShowQuestPopup.as` |
| Fonctionnement | Endpoint AMF `ResetNotifications`. |

#### `UpdateDoTaskObjectiveAndGetStatus`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3, param4 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CareerQuestObserver.as` |
| Fonctionnement | Met à jour ate do task objective and get status. |

#### `UpdateGotoObjectiveAndGetStatus`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CareerQuestObserver.as` |
| Fonctionnement | Met à jour ate goto objective and get status. |

#### `UpdateSpecialQuestObjectiveOld`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandUpdateObjectives.as` |
| Fonctionnement | Met à jour ate special quest objective old. |

#### `UpdateSpecialQuestObjectives`

| Propriété | Valeur |
|-----------|--------|
| Paramètres | param1, param2, param3 |
| Ticket AMF | Oui |
| Rate limit | — |
| Codes retour | Voir section II.5 — constantes AwardingType |
| Client AMF | `com/moviestarplanet/quest/service/QuestAMFService.as` |
| UI / appelants | `CommandUpdateObjectives.as` |
| Fonctionnement | Met à jour ate special quest objectives. |

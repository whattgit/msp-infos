# MSP Infos — Référence client MSP (pets, AMF, mécaniques)

> **Description GitHub** : Référence bilingue du client Flash MSP — pets, vêtements, looks, boutique, **74 services AMF** (846 endpoints + paramètres), rate limits, sécurité AMF, codes d'erreur.

Documentation extraite du client Flash décompilé (`msp_client/scripts/`).  
Les valeurs marquées **serveur** ne sont pas hardcodées dans le client et peuvent varier par région ou mise à jour.  
Les valeurs **empiriques** proviennent d'observations communautaires ou d'outils du repo (`pets_msp/`, `test_script/pet_caress.py`) — à valider en jeu.

---

## Table des matières

1. [Types de pets & identifiants](#types-de-pets--identifiants)
2. [Cycle de vie Bonster (œuf, caisse, stades)](#cycle-de-vie-bonster-œuf-caisse-stades)
3. [Nourriture (Bonsters)](#nourriture-bonsters)
4. [Personnalités & favoris (table complète)](#personnalités--favoris-table-complète)
5. [Bonbons (Candy) — prix par niveau](#bonbons-candy--prix-par-niveau)
6. [XP & niveaux](#xp--niveaux)
7. [Besoins : faim, lavage, jeu](#besoins--faim-lavage-jeu)
8. [Caresser un pet d'un autre joueur](#caresser-un-pet-dun-autre-joueur)
9. [Limites (salles, boutique)](#limites-salles-boutique)
10. [Hôtel pets](#hôtel-pets)
11. [Anciens pets (Monster / Boonie)](#anciens-pets-monster--boonie)
12. [Boosters & specials (boutique diamants)](#boosters--specials-boutique-diamants)
13. [Rate limits & anti-abus](#rate-limits--anti-abus)
14. [Sécurité réseau & anti-manipulation](#sécurité-réseau--anti-manipulation-charles--proxy)
15. [Codes de réponse (tous systèmes)](#codes-de-réponse-tous-systèmes)
16. [Endpoints AMF pets](#endpoints-amf-pets)
17. [Référence AMF — endpoints & paramètres](#référence-amf--services-endpoints--paramètres)

---

## Types de pets & identifiants

| Champ | Description | Source |
|-------|-------------|--------|
| `BonsterId` | ID du modèle en boutique (catalogue) | Serveur |
| `BonsterTemplateId` | ID du template visuel (squelette, palettes) | Serveur |
| `ActorBonsterRelId` | ID unique de **ton** pet (instance possédée) | Serveur |
| `ActorClickItemRelId` | ID unique d'un ancien pet (Monster/Boonie) | Serveur |
| `Personality` | 1–5 (Timide, Sportif, Souriant, Dormeur, Malin) | Serveur |

Il n'existe **pas** de liste statique de tous les `BonsterId` dans le client : elle est chargée dynamiquement via la boutique et les highscores.

**Étapes d'évolution (Bonsters)** — stades visuels aux niveaux **12** et **24**.  
Animations de récompense aux niveaux **6, 12, 18, 24, 28, 32**.  
Niveau max affiché en UI : **100** (bonbon désactivé à partir du niveau 100).  
Animations débloquées à partir du niveau **6** (`MINIMUM_LEVEL_FOR_ANIMATIONS`).  
Nom du pet : max **20** caractères, modération obligatoire.

---

## Cycle de vie Bonster (œuf, caisse, stades)

Source : `ActorBonsterRelItem.as`, `BonsterConstants.as`

| État | Condition client | Visuel |
|------|------------------|--------|
| **Œuf (Boonie)** | `EvolutionStage == 0` && `BonsterTemplateId == 0` (`isBoonie`) | scale 0.5 |
| **Caisse (crate)** | `EvolutionStage == 0` && `BonsterTemplateId != 0` | scale 0.6 |
| **Stade 1** | `EvolutionStage == 1` | scale 0.65 |
| **Stade 2** | `EvolutionStage == 2` | scale 0.85 |
| **Stade 3** | `EvolutionStage == 3` | scale 1.0 |

- **Boonie** = pet legacy en œuf (`BonsterTemplateId == 0`).
- **Hatch** : `HatchBonster` + animation ; à l'éclosion `WashPoints = 50`.
- **Évolution automatique** aux niveaux **12** et **24** (`PET_EVOLUTION_STAGE_CHANGE_LEVELS`).
- **Évolution instantanée** : booster `INSTANT_PET_GROW` → `InstantEvolveBonster` (refusé si déjà au max).

---

## Nourriture (Bonsters)

Source : `PetFood.as`

| ID | Nom | Prix SC | Prix 💎 | Type |
|----|-----|---------|---------|------|
| 1 | Poulet (Chicken) | 3 | — | normal |
| 2 | Pomme (Apple) | 3 | — | normal |
| 3 | Burger | 3 | — | normal |
| 4 | Sushi | 3 | — | normal |
| 5 | Pizza | 3 | — | normal |
| 6 | Orange | 3 | — | normal |
| 7 | Sandwich | 3 | — | normal |
| 8 | Ananas (Pineapple) | 3 | — | normal |
| 9 | Toast | 3 | — | normal |
| 10 | Banane (Banana) | 3 | — | normal |
| 11 | Médicament (Medicine) | 20 | — | médicament |
| 12 | Bonbon (Candy) | — | 1 | normal |

Constantes de type : `FOODTYPE_NORMAL = 1`, `FOODTYPE_MEDICIN = 2`.

Le **médicament** (ID 11) soigne un pet **malade** (`RESULT_CODE_PET_SICK` si on nourrit sans soigner).  
Le **bonbon** (ID 12) utilise un prix en diamants **dynamique** selon le niveau — voir section suivante.

---

## Personnalités & favoris (table complète)

Source : `PersonalityFoods.as`, `FoodListItemRenderer.as`

Chaque Bonster a une `Personality` (1–5) assignée par le **serveur**.  
Les nourritures favorites affichent des **étincelles** (sparkles) dans le menu feed.

### Constantes personnalité

| ID | Constante client | FR | EN |
|----|------------------|----|----|
| 1 | `BONSTER_PERSONALITY_SHY` | Timide | Shy |
| 2 | `BONSTER_PERSONALITY_SPORTY` | Sportif | Sporty |
| 3 | `BONSTER_PERSONALITY_SMILEY` | Souriant | Smiley |
| 4 | `BONSTER_PERSONALITY_SLEEPY` | Dormeur | Sleepy |
| 5 | `BONSTER_PERSONALITY_SMART` | Malin | Smart |

### Matrice nourriture × personnalité

| ID | Nourriture | Timide | Sportif | Souriant | Dormeur | Malin |
|----|------------|:------:|:-------:|:--------:|:-------:|:-----:|
| 1 | Poulet | ★ | | | | |
| 2 | Pomme | ★ | | | | |
| 3 | Burger | | | ★ | | |
| 4 | Sushi | | ★ | | | |
| 5 | Pizza | | | | | ★ |
| 6 | Orange | | ★ | | | |
| 7 | Sandwich | | | | ★ | |
| 8 | Ananas | | | | | ★ |
| 9 | Toast | | | | ★ | |
| 10 | Banane | | | ★ | | |
| 11 | Médicament | — | — | — | — | — |
| 12 | Bonbon | — | — | — | — | — |

★ = favori (bonus XP empirique). Médicament et bonbon ne sont pas des favoris de personnalité.

### Favoris par personnalité (résumé)

| Personnalité | IDs favoris | Noms |
|--------------|-------------|------|
| Timide (1) | 1, 2 | Poulet, Pomme |
| Sportif (2) | 4, 6 | Sushi, Orange |
| Souriant (3) | 3, 10 | Burger, Banane |
| Dormeur (4) | 7, 9 | Sandwich, Toast |
| Malin (5) | 5, 8 | Pizza, Ananas |

---

## Bonbons (Candy) — prix par niveau

Sources : `BonsterCandyPrices.as`, `BonsterCandyPriceWithLevel.as`, `GetBonsterCandyPrices`, `FoodListItemRendererMediator.as`

### Chargement

Au login, le client appelle `GetBonsterCandyPrices` et stocke le résultat dans  
`BonsterCandyPrices.candyPriceRaiseLevels` — tableau d'objets :

```
{ LevelFloor, LevelCeil, CandyPrice }
```

### Algorithme `calculateCandyPrice(niveau)`

```
pour chaque palier dans candyPriceRaiseLevels:
    si niveau >= LevelFloor ET niveau < LevelCeil:
        retourner CandyPrice
sinon:
    retourner CandyPrice du dernier palier
```

- Le prix affiché dans l'UI **remplace** le `priceDiamonds = 1` par défaut de `PetFood.CANDY`.
- Le prix est **recalculé** à chaque changement de niveau / personnalité.
- **Niveau ≥ 100** : le bonbon est **indisponible** (`isPetMaxLevel`).

### Coût total pour atteindre la prochaine évolution — `diamondsToEvolve(niveau)`

Somme des `calculateCandyPrice(i)` pour `i` de `niveau` jusqu'au prochain palier d'évolution (**12** ou **24**) exclus.  
Retourne **0** si le pet est déjà au dernier palier d'évolution (niveau ≥ 24).

### Paliers typiques (empirique — **serveur**, à capturer via `GetBonsterCandyPrices`)

Le client ne contient **pas** les valeurs numériques des paliers. En pratique sur FR (observation communautaire) :

| Niveau du pet | Prix bonbon (💎) observé |
|---------------|--------------------------|
| Bas niveaux | souvent **1** |
| Niveaux élevés | souvent **2** (par palier serveur) |

Pour obtenir la table exacte : intercepter la réponse AMF `GetBonsterCandyPrices` au login ou logger `candyPriceRaiseLevels` après connexion.

---

## XP & niveaux

| Situation | XP | Source |
|-----------|-----|--------|
| Nourriture favorite | **60** | Empirique (`pets_msp/`) |
| Nourriture normale | **40** | Empirique (`pets_msp/`) |
| Médicament | *(serveur)* | Pas de formule client |
| Bonbon | *(serveur)* | XP + possible level-up instantané |

Le client reçoit après chaque interaction (`FeedBonster`, `WashBonster`, `PlayWithBonster`) un objet `BonsterInteractionResponse` :

| Champ | Description |
|-------|-------------|
| `experience` | XP total actuel |
| `experienceToNextLevel` | XP requis niveau suivant |
| `experienceToCurrentLevel` | XP base niveau actuel |
| `level` | Niveau actuel |
| `evolutionStage` | Stade visuel (0–3) |
| `interactionPoints` | Points faim / lavage / jeu après action |
| `lastInteractionDate` | Horodatage dernière interaction |
| `fameEarned` | Fame gagnée *(champ présent, usage feed non affiché côté pets UI)* |
| `resultCode` | Code succès/erreur |

Le calcul exact de l'XP par type de nourriture est **côté serveur** — le client affiche seulement la barre de progression.

**Échelles visuelles par stade** (`BonsterConstants.as`) :

| Stade | Scale |
|-------|-------|
| Œuf | 0.5 |
| Caisse (crate) | 0.6 |
| Évolution 1 | 0.65 |
| Évolution 2 | 0.85 |
| Évolution 3 | 1.0 |

Points de lavage à l'éclosion : **50** (`WASHPOINTS_AT_HATCH`).

---

## Besoins : faim, lavage, jeu

Source : `BonsterUtils.as`, `BonsterConstants.as`, `Model.as`, `ViewConstants.as`

### Déclin temporel

| Mécanique | Valeur |
|-----------|--------|
| Déclin faim / lavage / jeu | **−1 point / 15 min** (`POINT_DECREASE_INTERVAL_MS`) |
| Maladie (sans nourrir) | après **3 jours** (`SICK_LIMIT_MS`) |
| Points max affichés (UI lavage/jeu) | **100** (plafonné côté client) |

### Barre d'état (power bar) — `ViewConstants.translateValueToPowerbarValue`

| Points | Frame barre |
|--------|-------------|
| ≥ 100 | 1 (plein) |
| ≥ 75 | 2 |
| ≥ 50 | 3 |
| ≥ 25 | 4 |
| ≥ 0 | 5 (vide) |

### Saleté (WashPoints) — seuils visuels

| WashPoints | Effet visuel |
|------------|--------------|
| ≤ 10 | 3 points de saleté |
| ≤ 25 | 2 points de saleté |
| ≤ 45 | 1 mouche |
| À l'éclosion | 50 points (`WASHPOINTS_AT_HATCH`) |

### Interactions AMF (propre pet)

| Action | Endpoint | Paramètre clé |
|--------|----------|---------------|
| Nourrir | `FeedBonster` | `foodId` (1–12) |
| Laver | `WashBonster` | `washPoints` (accumulés en mini-jeu UI) |
| Jouer | `PlayWithBonster` | `playPoints` (ticks UI, max 100) |

Chaque interaction remonte `interactionPoints` dans `BonsterInteractionResponse`.

## Caresser un pet d'un autre joueur

### Flux client (Bonster)

1. Clic sur le pet d'un autre joueur en chat room / MyRoom.
2. Appel AMF `PetFriendBonster(actorId, actorBonsterRelId)`.
3. Le serveur retourne un **entier** (pas un objet `BonsterInteractionResponse`).
4. Si entier **> 0** : animation SC + `rewardSpawner.spawnAwardsNonStatic(x, y, montant, 0, 0)`.
5. Si entier **== 0** : pas de récompense (déjà caressé ou refus serveur).
6. Si entier **== -429** : rate limit (`RateLimiterController`, popup silencieux pour Bonster).

### Flux client (ancien pet Monster/Boonie)

1. `PetFriendPet(actorId, actorClickItemRelId)` — même logique entier SC.
2. Cooldown UI local sur **son** pet : `PET_INTERVAL = 3000 ms` entre caresses (`MonsterConstants`).

### Calcul des Starcoins — ce que dit le client

| Question | Réponse |
|----------|---------|
| Formule dans le client ? | **Non** — aucune multiplication, niveau ou table locale |
| Qui calcule le montant ? | **Serveur uniquement** |
| Type de retour AMF | `int` direct (Bonster) ou cast `int` (ancien pet) |
| Affichage | Le entier retourné = SC crédités au **caresseur** |
| Récompense propriétaire | **Aucune** gestion client visible au moment du caressage |
| Analytics | `AnalyticsUtil.registerPetGive(0, montantSC)` |

### Observations empiriques (hors client, outil `test_script/pet_caress.py`)

| Observation | Détail |
|-------------|--------|
| SC typique par caresse réussie | **5 SC** (`PET_REWARD = 5` dans le script) |
| Succès | `retour AMF > 0` |
| Échec / déjà fait | `retour == 0` |
| Rate limit | `retour == -429` |

> Le script suppose **+5 SC** quand la réponse est positive — ce n'est **pas** hardcodé dans le client Flash. Le serveur peut renvoyer d'autres valeurs ; toujours utiliser l'entier AMF réel.

### Limites caressage

| Limite | Valeur | Portée |
|--------|--------|--------|
| Par pet / session client | **1×** | `petsPettedAlready[]` — rejoue sans appel ou retourne 0 |
| Rate limit serveur | `-429` | Quota global (non documenté dans le client) |
| Œuf / caisse Bonster | Interdit | `isInEgg`, `isInCrate` |
| Son propre Bonster | Popup pet | Pas de SC |
| Quête | +1 `ACTION_LOVE_PET` | Si SC > 0 |

### Tableau récapitulatif

| | Bonster | Ancien pet |
|---|---------|------------|
| Endpoint | `PetFriendBonster` | `PetFriendPet` |
| ID passé | `ActorBonsterRelId` | `ActorClickItemRelId` |
| Récompense toi | SC (entier serveur) | SC (entier serveur) |
| Récompense owner | Non (client) | Non (client) |
| Limite session | 1×/pet | 1×/pet |
| Rate limit `-429` | Oui (popup off) | Possible (pas de handler explicite) |

---

## Limites (salles, boutique)

| Contexte | Limite | Source |
|----------|--------|--------|
| Pets dans une salle de chat / room | **10 max** | `ChatRoomItemSelectorView` (`MAX_PETS_IN_ROOM`) |
| Boutique — Top pets | 10 par page | `PetShopModel` |
| Boutique — New pets | 9 par page | `PetShopModel` |
| Boutique — Bonsters | 12 par page | `PetShopModel` |
| Boutique — Boonies | 12 par page | `PetShopModel` |
| Boutique — Pets d'amis | 3 par page | `PetShopModel` |

---

## Hôtel pets

Source : `PetHotel.as`

| Séjour | Durée | Prix SC | VIP requis |
|--------|-------|---------|------------|
| Période 0 | 7 jours | 100 | Non |
| Période 1 | 14 jours | 200 | Non |
| Période 2 | 28 jours | 300 | **Oui** |

Réduction **50 %** si le booster `SHOPPING_SPREE` est actif.

Endpoints : `CheckInBonsterAtPetHotel`, `CheckOutBonsterFromPetHotel` (Bonsters) ; `CheckInPetHotel`, `CheckOutPetHotel` (anciens pets).

---

## Anciens pets (Monster / Boonie)

Source : `MonsterConstants.as`

| Constante | Valeur |
|-----------|--------|
| Prix nourriture | 10 SC |
| Prix médicament | 20 SC (ou 300 SC variante 2) |
| Points nourriture VIP | 2 |
| Intervalle caressage | 3000 ms |
| Points saleté max | 3 |
| Temps par point saleté | 3 s |
| Intervalle faim max | 24 h |
| Intervalle faim min | 8 h |
| Points nourriture par stade | 9 |
| Niveau malade | −2 |

---

## Boosters & specials (boutique diamants)

Source : `SpecialsItem.as`, `ActiveSpecialsType.as`

Identifiants string (utilisés pour achats et effets actifs) :

| Identifier | Effet connu (client) |
|------------|----------------------|
| `FAME_BOOSTER` | Fame × **2** (`ActorValueManager`) ; incompatible si déjà actif |
| `SHOPPING_SPREE` | −50 % sur achats éligibles (ex. hôtel pets) |
| `INSTANT_PET_GROW` | Évolution instantanée via `InstantEvolveBonster` |
| `CHANGE_PET` | Changer de pet actif |
| `FAME_WHEEL` | Roue de la fame |
| `DIAMOND_TWIT` | Tweet diamant |
| `DIAMOND_CLOTHES` | Vêtements diamant |
| `DIAMOND_CHARACTER_EFFECT` | Effet personnage |
| `CHARACTER_POPUP` | Popup personnage |
| `SPECIAL_GREETING` | Salutation spéciale |
| `STARCOIN_SHOOTER` | Mini-jeu starcoins |

Les `SpecialsItemId` numériques sont **serveur** (chargés via `SpendingAmfService`).

Bonus fame additionnel : **×1.1** si le joueur est célébrité (`isCeleb`), cumulable avec Fame Booster.

---

## Rate limits & anti-abus

### Deux mécanismes distincts

Le client gère le rate limiting à **deux niveaux** :

| Niveau | Détection | Source | Popup |
|--------|-----------|--------|-------|
| **1 — Corps AMF** | Valeur de retour `== -429` | `RateLimiterController` | `INTERACTION_LIMIT_REACHED_BY_DESIGN_*` (par endpoint) ou silencieux |
| **2 — Transport HTTP** | Description contient `"429"` | `AmfListener` | `MSP1_POPUP_TOO_MANY_REQUESTS_*` + log `Rate Limited` |

Code unique côté logique métier : **`CODE_IS_REQUEST_BLOCKED = -429`**.

> **Important** : le nombre exact de requêtes avant blocage (par minute, heure, jour, par endpoint ou par compte) **n'est pas dans le client**. Ces quotas sont calculés **uniquement côté serveur**. Le client ne fait que détecter `-429` ou HTTP 429 et afficher un popup.

### Table complète des endpoints rate-limités (client)

Chaque ligne = appel où `RateLimiterController.isLimitedAndPromptIfSo()` est invoqué.

| Endpoint | Service AMF | Champ vérifié pour `-429` | Popup si limité |
|----------|-------------|---------------------------|-----------------|
| `PetFriendBonster` | `AMFBonsterService` | entier retour (SC) | **Non** (`showPopup = false`) |
| `PetFriendPet` | `PetAMFService` | *(pas de check explicite)* | — |
| `MovieWatched` | `AMFMovieService` | `awardedFame` / `returnType` | Oui |
| `LikeAdd` | `AMFCommonService` | `fameEarned` | Oui |
| `LikeScrapBlog` | `ScrapBlogAMFService` | `fameEarned` | Oui |
| `LikeImage` | `AMFPictureUploadService` | `Code` | Oui |
| `SpinWheel` | `AMFAwardingService` | `Status` | Oui |
| `GiveAutographAndCalculateTimestamp` | `AMFUserSessionService` | `Fame` | Oui |
| `GiveAutographAndCalculateTimestampNeb` | `AMFActorService` | `Fame` | Oui |
| `SaveRoomWithSnapshot` | `AMFRoomService` | entier retour | Oui |
| `OpenGift` | `AMFGiftService` | `GiftLogId` | Oui |
| `ClaimBonus2` | `NotificationCenterAmfService` | `ErrorCode` | Oui |
| `claimDailyAward` | `AMFAwardingService` | `amount` | Oui |
| `claimAdvertViewAward` | `AMFAwardingService` | `amount` | Oui |
| `claimAdvertAwardByCampaign` | `AMFAwardingService` | `amount` | Oui |
| `BuySpecialGreeting` | `SpendingAmfService` | `Code` | Oui |
| `PickupGuidePresent` | `AMFActorService` | `Code` | Oui |

Tout autre endpoint peut aussi être rate-limité côté serveur via **HTTP 429** sans handler dédié dans le client.

### Limites client-side (anti-spam local, pas serveur)

Ces limites sont **hardcodées dans le client** — distinctes du rate limit serveur :

| Limite | Valeur | Fichier |
|--------|--------|---------|
| Caresses pets / session | **1× par `ActorBonsterRelId` ou `ActorClickItemRelId`** | `BonsterAMFService`, `PetAMFService` (`petsPettedAlready`) |
| Appels AMF concurrents max | **10** (configurable `MAX_CONCURRENT_AMF_CALLS`) | `AmfCaller` |
| Timeout par appel AMF | **20 000 ms** | `AmfListener.TIMEOUT_MILLIS` |
| Cadeaux par jour (UI) | **25** affiché (`DAILY_GIFT_LIMIT`) | `GiftService`, `SelectGift` |
| Code serveur cadeau quotidien | **`-20`** (`GIVE_GIFT_RETURN_CODE_DAILY_LIMIT_REACHED`) | `GiftService` |
| Pets max en salle | **10** | `ChatRoomItemSelectorView` |
| Création clubs VIP / normal | **1 / 0** | `ClubAMFService` |
| Upload photos | limité (message `PICTURE_UPLOAD_LIMIT_REACHED`) | `PictureUploadUtils` |

### Erreurs HTTP AMF (couche transport)

Source : `AmfListener.as`

| Code HTTP | Constante | Comportement |
|-----------|-----------|--------------|
| `400` | `HTTP_ERROR_BAD_REQUEST` | Pas de retry |
| `401` | `HTTP_ERROR_UNAUTHORIZED` | Refresh token Nebula ou échec |
| `427` | `HTTP_ERROR_EXPIRED_REFRESH_TOKEN` | Renouvellement token (`GetNebulaAccessTokenCommand`) |
| `429` | `HTTP_ERROR_TOO_MANY_REQUEST` | Popup too many requests |
| `500` | `HTTP_ERROR_INTERNAL_SERVER` | Pas de retry |
| `501` | `HTTP_ERROR_NOT_IMPLEMENTED` | Pas de retry |
| `505` | `HTTP_ERROR_VERSION_NOT_SUPPORTED` | Pas de retry |

Sur erreur retryable : nouveau `TicketHeader` généré (`generateAndAddNewTicketMarking`), file d'attente nettoyée des appels `LOW_IMPORTANCE`.

---

## Sécurité réseau & anti-manipulation (Charles / proxy)

> Le client Flash **ne mentionne pas Charles Proxy** explicitement. Les mécanismes ci-dessous protègent l'intégrité des appels AMF et détectent les environnements modifiés. Intercepter le trafic avec un proxy MITM casse typiquement le **checksum de réponse** si le niveau d'application est ≥ 3.

### 1. Checksum requête (client → serveur)

Source : `AmfCall.execute()`, `ChecksumCalculator.as`

- Chaque appel AMF (sauf fonctions ignorées) envoie un header persistant **`id`** = SHA1 des arguments sérialisés + sel obfusqué.
- Sel partiel : `"Yd*xX#o@B15i@!th"` + permutation dynamique de caractères.
- Si un `TicketHeader` est présent dans les args : extrait `ticketPrefix + 5 derniers chars` pour le hash.
- Fallback sans ticket : `"XSV7%!5!AX2L8@vn"`.

**Fonctions sans checksum requête** (liste `ignoredFunctions`) :

| Service complet ignoré |
|------------------------|
| `AMFLoggingService.LogClient` |
| `AMFAppSettingsService(Get/Mobile).GetAppSettings` |
| `AMFSessionServiceForMobile.CheckClientFreshness` |
| `AMFPaymentService.GetCurrentPaymentPossibilities` |
| `AMFLookService.GetRandomLookByLikes` |
| `AMFNebulaService.GetProfileIds` |
| `AMFOs.CreateOsRef` / `RunOsCheck` |
| `AMFUserSessionService.EmailValidated` |

### 2. Checksum réponse (serveur → client)

Source : `AmfCall.validateChecksum()`, `FluorineNetConnection.hashContent()`

- Le serveur renvoie un checksum via `serverChecksum` sur la connexion.
- Le client recalcule SHA1(`[TicketHeader, responseObject]`) et compare.
- Niveau d'application (`AmfCallExternalCommands`, réglé par `AppSettings.AWS_HEX_VALUE`) :

| Niveau | Comportement |
|--------|--------------|
| **1** | Checksum réponse **désactivé** |
| **2** | Validé mais **non bloquant** si mismatch |
| **3+** | **Bloquant** — l'appel échoue + log `[AMF ResponseChecksum Enforced]` |
| **4** | Bloquant + log silencieux sur échec |

Flag debug : `AmfCall.isIgnoringChecksum = true` bypass la validation.

> **Impact Charles Proxy** : modifier le corps d'une réponse AMF sans recalculer le checksum serveur → échec si niveau ≥ 3. Rejouer des requêtes nécessite un `TicketHeader` valide avec token Nebula + marking ID incrémental.

### 3. Ticket d'authentification (`TicketHeader`)

Source : `TicketGenerator.as`

Chaque appel sensible inclut un `TicketHeader` :

```
Ticket = [optional MD5 prefix_] + sessionTicket + markingId
anyAttribute.Token = Nebula access token
anyAttribute.DeviceId = device ID persistant
```

- `markingId` : compteur global incrémenté + double hash MD5/hex — **régénéré à chaque retry**.
- `sessionID` : header AMF Base64 aléatoire (46 chars hex) sur toutes les requêtes.
- Token expiré → refresh via `SharedObjectUtil.refreshNebulaAccessToken` puis retry unique.

### 4. OS Check / alignement environnement (`SnapLoader`)

Source : `SnapLoader.as`, service `AMFOs`

Anti-fraude environnement (souvent lié au fuseau horaire) :

1. `CreateOsRef` → reçoit `TjData` + `RefId`
2. Déserialise un snapshot acteur, calcule un histogramme (`SnapshotStats`)
3. `RunOsCheck(refId, histogram)` → doit retourner une `String` (nouveau refId)

- Activé via `AppSettings.ACTIVATE_TIMEZONE_ALIGNMENT` (`WEB`, `MOB`, `WEB:E`, `MOB:E`)
- Mode `:E` → échec bloquant (`ignoreFail = false`)
- Retry forcé toutes les **120 s** si pas de succès

### 5. Appels non-pausables

`CreateOsRef` et `RunOsCheck` ne sont **pas mis en pause** quand la file AMF est pausée (`AmfCaller.unPausable`).

### 6. Modération & logs

| Mécanisme | Endpoint / usage |
|-----------|------------------|
| Log chat | `LogChat`, `LogInput` (`AMFCommonService`) |
| Modération texte | `SetMoodWithModerationCall`, `TextModerationHandler` |
| User behavior | Service séparé avec host dédié + checksum réponse actif |

---

## Codes de réponse (tous systèmes)

### Bonsters / pets — `BonsterInteractionResponse`

| Code | Signification |
|------|---------------|
| `0` | Succès |
| `−1` | Exception serveur |
| `−2` | Pas VIP |
| `−3` | Pas assez de SC |
| `−4` | Pas assez de diamants |
| `−5` | Pet malade |
| `−429` | Rate limited (via `RateLimiterController`) |

### Boutique diamants — `SpendingProvider`

| Code | Signification |
|------|---------------|
| `0` | Succès |
| `−1` | Exception |
| `−2` | Pas assez de diamants |
| `−3` | Déjà acheté aujourd'hui |

### Design Studio — `DesignerContentService`

| Code | Signification |
|------|---------------|
| `0` | Succès |
| `−1` | Exception |
| `−2` | Pas VIP |
| `−3` | Pas assez de SC |
| `−4` | Pas assez de diamants |

### Cadeaux — `GiftService`

| Code | Signification |
|------|---------------|
| `0` | OK |
| `−1` | Erreur générale |
| `−10` | Non-VIP niveau 6 requis |
| `−20` | Limite quotidienne atteinte |
| `−30` | Possède déjà l'objet |
| `−40` | Trop tôt (cooldown) |

### Certificats cadeaux — `ServiceResultDataOfListOfCertificateGift`

| Code | Signification |
|------|---------------|
| `5` | Succès |
| `6` | Déjà utilisé |
| `9` | Invalidé |
| `200` | Succès en attente |
| `−1` | Inconnu |

### Forum — `NewTopic`

| Code | Signification |
|------|---------------|
| `0` | Succès |
| `1` | Erreur |
| `2` | Chaîne de topics (modération) |

### Upload photos — `UploadAvailabilityVO`

| Code | Signification |
|------|---------------|
| `0` | Disponible |
| `1` | Non disponible (limite atteinte / VIP) |

### Clubs — réponses ad hoc

| Code | Signification |
|------|---------------|
| `4` | Trop d'adhésions (`RESPONSE_TOO_MANY_MEMBERSHIPS`) |
| `−1` | Trop de clubs créés (`RESPONSE_TOO_MANY_CREATED_CLUBS`) |

### Redeem codes — `RedeemModelEvent`

| Constante | Signification |
|-----------|---------------|
| `ERROR_CODE_TOO_MANY_ATTEMPTS` | Trop de tentatives |

---

## Endpoints AMF pets

Service Bonster : `MovieStarPlanet.WebService.Bonster.AMFBonsterService`

| Méthode | Paramètres | Description |
|---------|------------|-------------|
| `FeedBonster` | relId, foodId, actorId | Nourrir |
| `WashBonster` | relId, washPoints, actorId | Laver |
| `PlayWithBonster` | relId, playPoints, actorId | Jouer |
| `PetFriendBonster` | actorId, relId | Caresser (ami) |
| `HatchBonster` | relId, actorId | Éclore |
| `InstantEvolveBonster` | actorId, relId | Évolution instantanée (booster) |
| `RenameBonster` | relId, name, actorId | Renommer |
| `DeleteBonsterName` | relId | Supprimer nom modéré |
| `GetBonsterCandyPrices` | — | Prix bonbons par niveau |
| `GetBonsterListByActor` | actorId, flag | Liste des pets |
| `GetBonsterAnimations` | — | Animations |
| `CheckInBonsterAtPetHotel` | relId, stayPeriod, actorId | Hôtel |
| `CheckOutBonsterFromPetHotel` | relId, actorId | Sortie hôtel |
| `BuyBonster` | actorId, bonsterId | Achat boutique |

Service ancien pet : `PetAMFService` — `PetFriendPet`, `WashPet`, `CheckInPetHotel`, `CheckOutPetHotel`, `HarvestPlant`, etc.

---

## Référence AMF — services, endpoints & paramètres

**74 services · 846 endpoints** — paramètres tels que le client Flash les envoie via `callFunction(...)`.

### Auth, session & compte

#### `WebService.AMFActorService`

Chemin AMF : `MovieStarPlanet.WebService.AMFActorService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BlockActor` | param1, param2 |  |
| `BlockActorNeb` | param1, param2 |  |
| `BulkLoadActors` | param1 |  |
| `BuyClothesNew` | param1, param2 |  |
| `CreateNewUserWithSecureSnapshotV2` | newActorCreationData, checksum, store, deviceId, snapshotSmall, snapshotBig |  |
| `GetActorIdByName` | param1 |  |
| `GetActorZooItems` | param1 |  |
| `GetClothesFromNewestClothesSection` | param1, param2, param3 |  |
| `GetPagedClothByCategoryGroups` | param1, _loc5_ |  |
| `GetPagedClothByCategoryGroups_14` | param1, _loc5_ |  |
| `GetPostLoginBundle` | param1 |  |
| `IsActorNameUsed` | param1 |  |
| `IsNameBlocked` | param1 |  |
| `LoadActorDetails` | param1, param2 |  |
| `LoadActorDetailsExtended` | param1 |  |
| `LoadActorItems` | param1 |  |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 |  |
| `LoadActorWithCurrentClothesBasicDataOnlyRevised` | param1 |  |
| `LoadActorsVipDetails` | param1 |  |
| `LoadBlockedAndBlockingActors` | param1 |  |
| `LoadBlockedAndBlockingActorsNeb` | param1 |  |
| `LoadDataForRegisterNewUser` | — |  |
| `LoadModeratorInformation` | param1 |  |
| `LoadMood` | param1 |  |
| `LoadMovieStarListRevised` | param1 |  |
| `LockOutUser` | param1, param2, param3, param4, param5 |  |
| `LoginMobile` | userId, redirectToken, version, store, deviceId |  |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `PickupGuidePresent` | actorId, type, index |  |
| `ReportActor` | param1 |  |
| `ReportTabletAndroidConversion` | param1, param2 |  |
| `ReportTabletIOSConversion` | param1, param2 |  |
| `RequestMobileStartupReward` | param1 |  |
| `SaveAlertWordsCount` | param1, param2 |  |
| `SaveBirthInfoWithTicket` | param1, param2, param3 |  |
| `SearchActorByNameNeb` | param1, param2 |  |
| `SearchActorByNameWithRequestStatus` | param1, param2 |  |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 |  |
| `SubmitMobileStartupReward` | param1, param2, param3 |  |
| `ThirdPartyLoginDesktopV2` | param1, param2, param3, param4, param5 |  |
| `ThirdPartyLoginMobileV2` | nacd, snapshotBig, snapshotSmall, username, password, version, store, deviceId |  |
| `UnblockActor` | param1, param2 |  |
| `UnblockActorNeb` | param1, param2 |  |
| `UpdateClothes` | param1, param2 |  |
| `ValidateCaptcha` | param1, param2 |  |
| `fameOverhaul` | param1 |  |
| `loginMobileV2` | userName, password, version, store, deviceId, dfp |  |

#### `WebService.AMFUserService`

Chemin AMF : `MovieStarPlanet.WebService.AMFUserService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `LogInput` | param1, param2, param3, param5, param4 |  |
| `LogInputGroupChat` | param1, param2, param3, param5, param4 |  |
| `LogInputWithConditionalModerationCall` | param1, param2, param3, param4, param5, param6 |  |

#### `WebService.ActorService.AMFActorServiceForWeb`

Chemin AMF : `MovieStarPlanet.WebService.ActorService.AMFActorServiceForWeb`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BlockActor` | param1, param2 |  |
| `BlockActorNeb` | param1, param2 |  |
| `BlockedActors` | param1 |  |
| `ClaimAllLevelUpGifts` | param1, param2 |  |
| `ClaimSingleLevelUpGift` | param1, param2, param3 |  |
| `GetActorAddress` | actorId |  |
| `GetLevelUpGiftChoices` | actorId |  |
| `GetLevelUpGiftSelects` | actorId |  |
| `GetLevelUps` | — |  |
| `GetPostLoginBundle` | param1 |  |
| `GetPostLoginBundleStandalone` | param1 |  |
| `IsActorNameUsed` | param1 |  |
| `IsNameBlocked` | param1 |  |
| `LoadActorDetails` | param1, param2 |  |
| `LoadActorDetailsExtended` | param1 |  |
| `LoadBlockedAndBlockingActors` | param1 |  |
| `LoadBlockedAndBlockingActorsNeb` | param1 |  |
| `LoadModeratorInformation` | param1 |  |
| `LoadMood` | param1 |  |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `ModerationSearchActorId` | actorId |  |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `PickupGuidePresent` | actorId, type, index |  |
| `PurchaseRecoloring` | param1, param2, param3, param4, param5 |  |
| `ReportActor` | param1 |  |
| `SaveActorAddress` | param1 |  |
| `SaveActorSoundMuted` | param1, param2 |  |
| `SaveBirthInfoWithTicket` | param1, param2, param3 |  |
| `SaveLevelUpGiftSelect` | param1, param2, param3 |  |
| `SearchActorByNameNeb` | param1, param2 |  |
| `SetColorOnActorItemNew` | param1, param2, param3, param4, param5 |  |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 |  |
| `UnblockActor` | param1, param2 |  |
| `UnblockActorNeb` | param1, param2 |  |
| `ValidateCaptcha` | param1, param2 |  |
| `fameOverhaul` | param1 |  |
| `getWallActivitiesForActor` | pagingOptions.actorId, pagingOptions.activityType, pagingOptions.pageIndex, pagingOptions.pageSize |  |

#### `WebService.AppSettings.AMFAppSettingsService`

Chemin AMF : `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetAppSetting` | param1 |  |
| `GetAppSettings` | param1 |  |

#### `WebService.AppSettings.AMFAppSettingsServiceMobile`

Chemin AMF : `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsServiceMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetAppSetting` | param1 |  |
| `GetAppSettings` | param1 |  |

#### `WebService.Nebula.AMFNebulaService`

Chemin AMF : `MovieStarPlanet.WebService.Nebula.AMFNebulaService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetProfileId` | param1 |  |
| `GetProfileIds` | missing |  |
| `GetProfiles` | param1 |  |

#### `WebService.ParentalConsent.AMFParentalConsentService`

Chemin AMF : `MovieStarPlanet.WebService.ParentalConsent.AMFParentalConsentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorParentalConsent` | param1 |  |
| `GetUserType` | param1 |  |
| `GrantParentalConsent` | param1, param2 |  |
| `HasVisibleParentalConsentCode` | param1 |  |
| `HideParentalConsentCode` | param1 |  |
| `MatchActorIdToParentalConsentConfirmCode` | param1, param2 |  |
| `ReSendParentalConsentCode` | param1 |  |
| `RememberParentalConsentCode` | param1 |  |
| `RequestParentalConsent` | param1 |  |
| `SaveParentEmailAddress` | param1, param2 |  |
| `SetActorsParentalConsent` | param1, param2 |  |

#### `WebService.Payment.AMFPaymentService`

Chemin AMF : `MovieStarPlanet.WebService.Payment.AMFPaymentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DisableAutomaticRenewal` | param1 |  |
| `GetAvailablePurchaseTypes` | actorId |  |
| `GetBokuBuyUrlNew` | param1, param2, param3, param4, param5 |  |
| `GetBokuPricePoints` | — |  |
| `GetCurrentPaymentPossibilities` | types |  |
| `GetRecurringPaymentSubscription` | param1 |  |
| `GetTimeLimitedPurchaseType` | actorId |  |
| `GetTransactionPurchaseInfo` | param1, param2 |  |
| `GetTransactionPurchaseInfoWeb` | param1, param2 |  |
| `GetTransactionPurchaseList` | param1, param2, param3 |  |
| `GetTransactionPurchaseListIncludingManual` | param1, param2, param3 |  |
| `VerifyBokuTransaction` | param1 |  |

#### `WebService.User.AMFUserServiceWeb`

Chemin AMF : `MovieStarPlanet.WebService.User.AMFUserServiceWeb`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CommentEntity` | entityComment |  |
| `CreateNewUserWithSecureSnapshotV2` | param1, param2, null, param3, param4 |  |
| `EntityCommentDelete` | param1, param2 |  |
| `GetActorPersonalInfo` | param1, "" |  |
| `GetEntityComments` | entityType, entityId, pageIndex, pageSize |  |
| `IsCommunicationAllowedWith` | communicationType, actorid |  |
| `IsCommunicationAllowedWithNeb` | communicationType, profileId |  |
| `LogInput` | locationId, actorId, roomInstanceId, message, destinationType |  |
| `LogInputGroupChat` | locationId, actorId, roomInstanceId, message, destinationType |  |
| `LogInputWithConditionalModerationCall` | locationId, actorId, roomInstanceId, message, destinationType, isUserRestricted |  |
| `Login` | userName, password, null, null, deviceId, dfp |  |
| `LoginModeratorV2` | username, password, userIps, otp, null, null |  |
| `LoginV2` | variante 1: param1, param2, null, null, null, null<br>variante 2: username, password, userIps, null, null, browserFingerprint<br>variante 3: username, password, userIps, null, null, null | 3 variantes |
| `SaveChatAllowed` | param1, param2 |  |
| `UpdateActorPersonalInfo` | param1, param2 |  |

#### `WebService.UserSession.AMFUserSessionService`

Chemin AMF : `MovieStarPlanet.WebService.UserSession.AMFUserSessionService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AwardStartupReward` | param1 |  |
| `BadWordCountAdd` | param1, param2 |  |
| `BadWordCountClear` | param1 |  |
| `ChangePasswordNew` | param1, param2, param3 |  |
| `DeleteUser` | param1, param2, param3 |  |
| `EmailChanged` | actorId, mail, username, password, emailSettings |  |
| `EmailValidated` | actorId |  |
| `EmailValidatedCancel` | param1 |  |
| `GetActorEmail` | actorId |  |
| `GetActorIdFromName` | name |  |
| `GetActorNameFromId` | actorId |  |
| `GetMarketingStepGift` | param1 |  |
| `GiveAutographAndCalculateTimestamp` | actorId, receiverId |  |
| `GiveAutographAndCalculateTimestampNeb` | actorId, receiverProfileId |  |
| `LoadActorDetails2` | actorId, updateProfileDisplayCount, callerId |  |
| `LoadActorDetailsExtended` | actorId |  |
| `LoadActorDetailsVersion` | actorId, updateProfileDisplayCount |  |
| `MassDeleteUsers` | usersIdsTobeDeleted, userName, password |  |
| `RecoverUserFromEmailHistory` | actorName, email |  |
| `RenameUser` | actorId, newActorName, moderatorName, moderatorPass |  |
| `ResyncLogin` | actorId |  |
| `SendEmailValidation` | param1, param2, param3, param4, param5 |  |
| `SendNewEmailValidation` | param1, param2, param3, param4, param5, param6 |  |
| `SendUserParentEmailValidation` | param1, param2, param3, param4, param5, param6 |  |
| `SetEmailSettings` | actorId, actorName, emailSettings |  |
| `SetFacebookId` | param1, param2 |  |
| `SetMarketingStep` | param1, param2, param3 |  |
| `UndeleteUser` | userIdTobeDeleted, userName, password |  |
| `UpdateBehaviourStatusNew` | actorId, behaviourStatus, lockedText, chatLogId, handledByActorId |  |
| `UpdateGift` | actorId |  |
| `UpdateMySchool` | actorId, passwordHash, schoolId, schoolYear |  |
| `UpdateRetention` | actorId |  |
| `deleteBioText` | actorId, moderatorName, moderatorPass |  |
| `eraseEmail` | email, moderatorName, moderatorPass |  |

#### `WebService.UserSession.AMFUserSessionServiceForMobile`

Chemin AMF : `MovieStarPlanet.WebService.UserSession.AMFUserSessionServiceForMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `UpdateGift` | actorId |  |

### Avatar & vêtements (MovieStar)

#### `WebService.BeautyClinic.AMFBeautyClinicService`

Chemin AMF : `MovieStarPlanet.WebService.BeautyClinic.AMFBeautyClinicService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyBeautyClinicItems` | actorId, eyeId, eyeShadowId, noseId, mouthId, eyeColors, eyeShadowColors, mouthColors, skinColor, removeEyeShadow |  |
| `BuyManyBeautyClinicItems` | actorId, itemsArray |  |
| `GetMyBeautyClinicItems` | actorId |  |
| `GetMyBeautyClinicItemsWithHiddenOption` | actorId, includeHidden |  |
| `LoadDataForBeautyClinic` | — |  |
| `LoadModeratorDataForBeautyClinic` | — |  |
| `WearItems` | actorId, inventoryIdArray |  |

#### `WebService.MovieStar.AMFMovieStarService`

Chemin AMF : `MovieStarPlanet.WebService.MovieStar.AMFMovieStarService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorClothesRel` | relId |  |
| `GetActorClothesRelList` | rels |  |
| `GetContextClothes` | actorId, contextId |  |
| `LoadActorBonstersPaged` | actorId, pageIndex, pageSize |  |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 |  |
| `LoadClothes` | skinId, shopId |  |
| `LoadClothesByIds` | clothesIds |  |
| `LoadClothesFromThemeId` | themeId |  |
| `LoadClothesWithThemeByIds` | clothesIds |  |
| `LoadDataForRegisterNewUser` | — |  |
| `LoadFaceParts` | — |  |
| `LoadMovieStarFlatMinimum` | actorId |  |
| `LoadMovieStarFlatRevised` | actorId |  |
| `LoadMovieStarListRevised` | actorIds |  |
| `LoadMovieStarRevised` | actorId |  |
| `LoadPagedActorClothes` | param1, param2, param3 |  |
| `LoadPagedActorGiftableClothes` | param1, param2, param3 |  |
| `LoadPagedActorGiftableItems` | param1, param2, param3 |  |
| `LoadPagedActorItems` | actorId, pageIndex, pageSize |  |
| `LoadRoomItems` | actorId |  |
| `UpdateClothes` | actorId, actorClothesRelIds |  |
| `getRandomClothesByType` | slotType, isFemale, amount |  |

### Looks (tenues)

#### `WebService.Looks.AMFLookService`

Chemin AMF : `MovieStarPlanet.WebService.Looks.AMFLookService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CanWearOwnLook` | param1, param2 |  |
| `GetLookById` | variante 1: lookId<br>variante 2: lookId, this.actorModel.actorId | 2 variantes |
| `GetLooksByOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksCreatedBy` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksForActor` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksForOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksLatest` | pageIndex, pageSize |  |
| `GetLooksLatestByFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksLatestByMeAndFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksLikedByMe` | actorId, pageIndex, pageSize |  |
| `GetLooksTopAll` | pageIndex, pageSize |  |
| `GetLooksTopByFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksTopByMeAndFriends` | actorId, pageIndex, pageSize |  |
| `GetRandomLookByLikes` | poolSize |  |
| `LookDelete` | lookId, this.actorModel.actorId |  |
| `SaveLookAndData` | look, clotheIds, lookSnapshot, fullSizeSnapshot |  |
| `SaveSmallLookSnapshot` | look, lookSnapshot |  |

### Boutique & dépenses

#### `WebService.Shopping.AMFShopContentService`

Chemin AMF : `MovieStarPlanet.WebService.Shopping.AMFShopContentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddTag` | param1, param2 |  |
| `AddTheme` | param1, param2 |  |
| `BuyItems` | param1, ActorSession.loggedInActor.actorId |  |
| `GetPage` | pageIndex, pageSize, params.shopId, params.genderId, params.themeId, params.categoryId, params.tagToUse, params.vipToUse, params.currencyToUse, params.search |  |
| `RemoveTag` | param1, param2 |  |
| `RemoveTheme` | param1, param2 |  |
| `SetShopIds` | param1, param2 |  |

#### `WebService.Spending.AMFSpendingService`

Chemin AMF : `MovieStarPlanet.WebService.Spending.AMFSpendingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyAnimation` | param1, param2 |  |
| `BuyBackground` | param1, param2 |  |
| `BuyChangePet` | param1, param2, param3, param4 |  |
| `BuyCharacterPopUp` | param1 |  |
| `BuyClothes` | param1, param2, param3 |  |
| `BuyDiamondCharacterEffect` | param1 |  |
| `BuyDiamondTwit` | param1 |  |
| `BuyEmoticonPackage` | param1, param2 |  |
| `BuyFameBooster` | param1 |  |
| `BuyFameWheelSpin` | param1 |  |
| `BuyInstantPetGrow` | param1, param2 |  |
| `BuyMusic` | param1, param2 |  |
| `BuyShoppingSpree` | param1 |  |
| `BuySpecialGreeting` | actorId, friendId, greetingTypeId |  |
| `BuyStarcoinShooter` | param1 |  |
| `BuyStarcoinsWheelSpin` | param1 |  |
| `ClaimFreeDownloadableFameWheelSpin` | param1 |  |
| `GetActiveSpecialsItems` | param1 |  |
| `GetEmoticonPackages` | param1 |  |
| `GetGreetingIndices` | param1 |  |
| `GetPagedShopSpecials` | param1, param2, param3 |  |
| `GetSpecialsGreetingItem` | param1, param2 |  |
| `GetSpecialsItemPrice` | param1, param2 |  |
| `IsValidSpecialGreeting` | param1, param2 |  |

### Salles & chambres

#### `WebService.AMFRoomServiceForMobile`

Chemin AMF : `MovieStarPlanet.WebService.AMFRoomServiceForMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorBonsterList` | param1, param2 |  |
| `GetActorClickItemList` | param1, param2 |  |
| `GetActorClothesByShopId` | param1, param2, param3 |  |
| `GetWallpapers` | param1, param2 |  |
| `LoadHouse` | houseId, callingActorId |  |
| `LoadHouseAndSpecificRoom` | callingActorId, houseId, roomId |  |
| `LoveRoom` | param1, param2 |  |
| `SaveRoomWithSnapshot` | data, roomSnapshotProfile, roomSnapshotMedium, roomSnapshotSmall |  |

#### `WebService.Room.AMFRoomService`

Chemin AMF : `MovieStarPlanet.WebService.Room.AMFRoomService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorBonsterList` | param1, param2 |  |
| `GetActorClickItemList` | param1, param2 |  |
| `GetActorClothesByShopId` | param1, param2, param3 |  |
| `GetWallpapers` | param1, param2 |  |

### Pets & Bonsters

#### `WebService.AMFMobilePetService`

Chemin AMF : `MovieStarPlanet.WebService.AMFMobilePetService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CurePet` | param1 |  |
| `FeedPet` | param1, param2 |  |
| `GetActorClickItem` | param1 |  |
| `GetClickItems` | — |  |
| `GetClickItemsForActor` | param1 |  |
| `HatchPet` | param1, param2 |  |
| `PetFriendPet` | param1, param2 |  |
| `PurchaseClickItem` | param1, param2 |  |
| `SavePetName` | param1, param2 |  |
| `WashPet` | param1, param2 |  |

#### `WebService.Bonster.AMFBonsterService`

Chemin AMF : `MovieStarPlanet.WebService.Bonster.AMFBonsterService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AnimationUsed` | actorBonsterRelId, animationId, actorId |  |
| `CheckInBonsterAtPetHotel` | actorBonsterRelId, bookTimeAmount, actorId |  |
| `CheckOutBonsterFromPetHotel` | actorBonsterRelId, actorId |  |
| `DeleteBonsterName` | actorBonsterRelId |  |
| `FeedBonster` | actorBonsterRelId, foodId, actorId |  |
| `GetBonsterAnimations` | param1, param2 |  |
| `GetBonsterById` | actorBonsterRelId |  |
| `GetBonsterCandyPrices` | — |  |
| `GetBonsterListByActor` | actorId, loadAnimations, excludeHotel |  |
| `GetBonsterTemplateList` | — |  |
| `HatchBonster` | actorBonsterRelId, actorId |  |
| `InstantEvolveBonster` | actorId, actorBonsterRelId |  |
| `PetFriendBonster` | actorId, actorBonsterRelId |  |
| `PlayWithBonster` | actorBonsterRelId, playPoints, actorId |  |
| `RenameBonster` | actorBonsterRelId, name, actorId |  |
| `SaveNewAndOldPetsPositionsInMyRoom` | actorId, bonsterPositionsList, clickItemsList |  |
| `WashBonster` | actorBonsterRelId, washPoints, actorId |  |

#### `WebService.Bonster.AMFBonsterShopService`

Chemin AMF : `MovieStarPlanet.WebService.Bonster.AMFBonsterShopService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyBonster` | actorId, bonsterId |  |
| `GetCampaignBonster` | — |  |
| `GetListOfAllBonstersAndBoonies` | — |  |
| `GetListOfBonsters` | — |  |
| `GetListOfBoonies` | — |  |
| `GetPagedListOfBonsters` | pageId, pageSize |  |
| `GetPagedListOfBoonies` | pageId, pageSize |  |
| `GetPagedListOfFriendsPets` | pageId, pageSize |  |
| `GetPagedListOfNewPets` | pageId, pageSize |  |
| `GetPagedListOfTopPets` | pageId, pageSize |  |

#### `WebService.Pets.AMFPetService`

Chemin AMF : `MovieStarPlanet.WebService.Pets.AMFPetService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyClickItem` | actorId, clickItemId |  |
| `CheckInPetHotel` | actorId, clickItemRelId, stayPeriod |  |
| `CheckOutPetHotel` | actorId, clickItemRelId |  |
| `CurePet` | actorClickItemRelId |  |
| `DeletePetName` | clickItemId, moderatorName, moderatorPass |  |
| `FeedPet` | actorClickItemRelId, foodPoints |  |
| `GetActorClickItem` | actorClickItemRelId |  |
| `GetClickItems` | — |  |
| `GetClickItemsForActor` | variante 1: actorid<br>variante 2: param1 | 2 variantes |
| `GetClickItemsForActorThatCanStillGrow` | actorid |  |
| `GetClickItemsForActorWithPrice` | actorid |  |
| `GetClickItemsForPetHotel` | actorId |  |
| `HarvestPlant` | actorId, actorClickItemRelId |  |
| `HatchPet` | actorClickItemRelId, configuration |  |
| `PetFriendPet` | actorId, actorClickItemRelId |  |
| `PlayedPetGame` | actorClickItemRelId, playPoints |  |
| `SaveClickItemLocations` | locations |  |
| `SavePetName` | actorClickItemRelId, name |  |
| `WashPet` | actorId, actorClickItemRelId |  |

### Films & favoris mobile

#### `MobileServices.AMFFavs`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFFavs`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddActorFav` | param1, param2 |  |
| `GetActorMovieFavs` | param1, param2 |  |
| `RemoveActorFav` | param1, param2 |  |

#### `MobileServices.AMFMovieService`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFMovieService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `DeleteMovie` | param1, param2 |  |
| `GetMovie` | movieId |  |
| `GetUnifiedMoviesByFriendsStarringMe` | param1, param2 |  |
| `GetUnifiedMoviesByMePrivate` | param1, param2 |  |
| `GetUnifiedMoviesLatestByAll` | param1, param2 |  |
| `GetUnifiedMoviesLatestByFriends` | param1, param2 |  |
| `GetUnifiedMoviesMinePublic` | param1, param2 |  |
| `GetUnifiedMoviesTopAll` | param1, param2 |  |
| `GetUnifiedMoviesTopByMeAndFriends` | param1, param2 |  |
| `MovieWatched` | movieId |  |
| `RateMovie` | param1, param2 |  |
| `UpdateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8, param9 |  |

#### `WebService.Favourites.AMFFavs`

Chemin AMF : `MovieStarPlanet.WebService.Favourites.AMFFavs`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddActorFav` | actorId, entityType, entityId |  |
| `GetActorMovieFavs` | actorId, byRating, pageIndex, pageSize |  |
| `RemoveActorFav` | actorId, entityType, entityId |  |

#### `WebService.MovieService.AMFMovieService`

Chemin AMF : `MovieStarPlanet.WebService.MovieService.AMFMovieService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CommentMovie` | rateMovie |  |
| `DeleteMovie` | movieId, actorId |  |
| `DeleteMovieComment` | movieId, commentId |  |
| `GetActorMovieCount` | actorId |  |
| `GetAutoSavedMovieId` | actorId |  |
| `GetMovieByGuid` | movieGuid |  |
| `GetMovieById` | movieId |  |
| `GetMovieListForActor` | pagingOptions.params.actorId, pagingOptions.params.type, pagingOptions.pageIndex, pagingOptions.pageSize |  |
| `GetMovieRatings` | movie.MovieId, pageIndex, pageSize |  |
| `MovieWatched` | movieId, actorId |  |
| `PublishMovie` | movieId |  |
| `RateMovie` | rateMovie |  |
| `SaveMovieWithSnapshot` | movie, snapshotSmall, snapshotBig |  |
| `SearchMovie` | searchString, pageIndex, pageSize |  |
| `SendMovieAsMail` | movieId, toAddress |  |

### Vidéo / YouTube

#### `WebService.Video.AMFVideoService`

Chemin AMF : `MovieStarPlanet.WebService.Video.AMFVideoService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddVideoToMspTv` | param1, param2, param3, param4, param5 |  |
| `AutoSaveVideoFromFeed` | param1, param2, param3, param4, param5, _loc9_ |  |
| `CreateBlankPlaylist` | param1, param2 |  |
| `DeleteExternalVideoPlaylistRel` | param1, param2, param3 |  |
| `DeletePlaylist` | param1, param2, param3 |  |
| `GetCategoryExternalVideosForPlayback` | param1, param2 |  |
| `GetExternalVideoForChatRoom` | param1 |  |
| `GetMspTvExternalVideosForPlayback` | param1 |  |
| `GetMyPlaylistsForVideo` | param1 |  |
| `GetPagedBlockedExternalVideos` | param1, param2, param3, param4 |  |
| `GetPagedCategoryExternalVideos` | param1, param2, param3 |  |
| `GetPagedExternalVideos` | param1, param2, param3 |  |
| `GetPagedMspTvExternalVideos` | param1, param2 |  |
| `GetPagedNewestExternalVideos` | param1, param2 |  |
| `GetPagedPlaylists` | param1, param2, param3, param4 |  |
| `GetPagedPlaylistsBySearch` | param1, param2, param3, param4 |  |
| `GetPagedVideoListObjects` | param1, param2, param3 |  |
| `GetPagedVideoListObjectsByAddTime` | variante 1: actorId, 0, 50<br>variante 2: param1, param2, param3 | 2 variantes |
| `GetPlaylist` | param1, param2 |  |
| `GetPlaylistForPlayback` | param1, param2, param3 |  |
| `GetPlaylistsForDropdown` | param1 |  |
| `GetTopExternalVideosForPlayback` | param1 |  |
| `GetYouTubeVideo` | param1, param2 |  |
| `GetYouTubeVideoInfo` | param1 |  |
| `IncrementReportCount` | param1 |  |
| `IncrementViewsExternalVideo` | param1 |  |
| `LikePlaylist` | param1, param2, param3 |  |
| `LikeYouTube` | param1, param2 |  |
| `MoveVideoInPlaylist` | param1, param2, param3, param4, param5 |  |
| `RenamePlaylist` | param1, param2, param3 |  |
| `ReportErrorOnVideo` | param1 |  |
| `SaveToNewPlaylist` | param1, param2, param3, param4, param5 |  |
| `SaveToPlaylist` | param1, param2, param3, param4 |  |
| `YouTubeBlock` | param1, param2, param3, param4 |  |
| `YouTubePopulateViewsAndLikes` | param1, param2 |  |

### Social (amis, profil, messagerie)

#### `WebService.AMFMessageService`

Chemin AMF : `MovieStarPlanet.WebService.AMFMessageService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetMessagingActors` | variante 1: [id<br>variante 2: param1 | 2 variantes |
| `IsCommunicationAllowedWith` | param1, param2 |  |
| `SendChatMessageWithModerationCall` | param1, param2, param3, param4, param5, param6 |  |
| `SendOneToOneOrGroupChatMessage` | Number(param2), param8, param3, param6, _loc13_, param4 |  |
| `SetMessengerSession` | param1 |  |

#### `WebService.AMFMobileFriendshipService`

Chemin AMF : `MovieStarPlanet.WebService.AMFMobileFriendshipService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AcceptBoyfriend` | param1, param2, param3 |  |
| `AcceptMySpecialFriend` | param1 |  |
| `ApproveDefaultAnchorFriendship` | param1 |  |
| `ApproveFriendship` | param1, param2 |  |
| `ApproveFriendshipNeb` | param1, param2 |  |
| `AskToBeBoyFriend` | param1, param2, param3 |  |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 |  |
| `AskToBeMySpecialFriend` | param1 |  |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 |  |
| `BreakUp` | param1, param2, param3 |  |
| `DeleteFriendship` | param1, param2 |  |
| `DeleteFriendshipNeb` | param1, param2 |  |
| `GetActorSpecialSummary` | param1, param2 |  |
| `GetFriendListWithNameAndScore` | param1 |  |
| `GetMspRelationshipStatus` | param3, param1, param4 |  |
| `GetPagedFriendRequests` | actorId, pageIndex, pageSize |  |
| `GetRelationshipStatusNeb` | param2, param3, param4 |  |
| `RejectBoyfriend` | param1, param2, param3 |  |
| `RejectFriendShip` | param1, param2 |  |
| `RejectFriendShipNeb` | param1, param2 |  |
| `RejectMySpecialFriend` | param1 |  |
| `RequestFriendship` | param1, param2 |  |
| `RequestFriendshipFromSchoolmate` | param1, param2 |  |
| `RequestFriendshipNeb` | param1, param2 |  |

#### `WebService.AnchorCharacter.AMFAnchorCharacterService`

Chemin AMF : `MovieStarPlanet.WebService.AnchorCharacter.AMFAnchorCharacterService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AcceptFriendship` | anchorCharacterId |  |
| `AcceptGifts` | anchorCharacterId |  |
| `CancelFriendship` | anchorCharacterId |  |
| `GetAnchorCharacterList` | — |  |
| `RequestFriendship` | anchorCharacterId |  |
| `UpdateLastInviteSent` | param1, param2 |  |
| `UpdateLastStatusSeen` | param1 |  |

#### `WebService.Friendships.AMFFriendshipService`

Chemin AMF : `MovieStarPlanet.WebService.Friendships.AMFFriendshipService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AcceptBoyfriend` | param1, param2, param3 |  |
| `AcceptMySpecialFriend` | param1 |  |
| `ApproveDefaultAnchorFriendship` | param1 |  |
| `ApproveFriendship` | param1, param2 |  |
| `ApproveFriendshipNeb` | param1, param2 |  |
| `AskToBeBoyFriend` | param1, param2, param3 |  |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 |  |
| `AskToBeMySpecialFriend` | param1 |  |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 |  |
| `BreakUp` | userId, friendId, friendType |  |
| `DeleteFriendship` | param1, param2 |  |
| `DeleteFriendshipNeb` | param1, param2 |  |
| `FindUserForFriendBrowser` | params.actorId, params.includeDeleted, params.searchString, pageIndex, pageSize |  |
| `GetFriendList` | param1 |  |
| `GetFriendListWithNameAndScore` | actor.actorId, false |  |
| `GetFriendListWithNameAndScoreV2` | userId, isLoadingTopFriendsOnly |  |
| `GetFriendShipStatus` | param1, param2 |  |
| `GetMspActorSpecialSummary` | param1, param4, param3 |  |
| `GetNebNonFriendStatus` | param2, param4 |  |
| `GetPagedProfileTodos` | actorId, pageId, pageSize |  |
| `GetProfileTodos` | param1 |  |
| `GetProfileTodosCount` | param1 |  |
| `GetSpecialRelationship` | param1 |  |
| `RejectBoyfriend` | param1, param2, param3 |  |
| `RejectFriendShip` | param1, param2 |  |
| `RejectFriendShipNeb` | param1, param2 |  |
| `RejectMySpecialFriend` | param1 |  |
| `RequestFriendship` | param1, param2, param3 |  |
| `RequestFriendshipFromSchoolmate` | param1, param2, param3 |  |
| `RequestFriendshipNeb` | param1, param2 |  |
| `SendInvitation` | param1, param2, param3 |  |

#### `WebService.Messaging.AMFMessagingService`

Chemin AMF : `MovieStarPlanet.WebService.Messaging.AMFMessagingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `SetMessengerSession` | param1 |  |

#### `WebService.Profile.AMFProfileService`

Chemin AMF : `MovieStarPlanet.WebService.Profile.AMFProfileService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CollectRecycleGift` | param1 |  |
| `DeleteWallPost` | param1, param2, param3 |  |
| `GetWallPost` | param1 |  |
| `GetWallPosts` | param1, param2, param3 |  |
| `LoadProfileSummary` | param1, ActorSession.getActorId() |  |
| `LoadProfileSummaryNeb` | param2, ActorSession.getActorId() |  |
| `PostToWallWithModerationCall` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `RecycleItem` | param1, param2, param3 |  |
| `SetFavorite` | param1, param2, param3 |  |
| `loadActorRoom` | param1, param2 |  |

#### `WebService.School.AMFSchoolService`

Chemin AMF : `MovieStarPlanet.WebService.School.AMFSchoolService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DeleteSchool` | actorId |  |
| `FindFriendsOnSameSchool` | params.actorId, pageIndex, pageSize, params.includeNames |  |
| `RetrieveMySchoolInformation` | actorId |  |
| `UpdateMySchool` | actorId, schoolId, schoolYear, schoolClass, firstName |  |

### Cadeaux & wishlist

#### `MobileServices.AMFGiftsService+Version2`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFGiftsService+Version2`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyGift` | senderId, receiverId, giftId, SWF |  |
| `GetUnifiedActorClothItems` | param1, param2, param3 |  |
| `GetUnifiedActorClothesByType` | param1, param2, param3 |  |
| `GetUnifiedGiftsGiven` | param1, param2 |  |
| `GetUnifiedGiftsNew` | param1, param2 |  |
| `GetUnifiedGiftsReceived` | param1, param2 |  |
| `GetWishListPaged` | actorId, pageIndex, pageSize |  |
| `GiveGiftOfCategory` | senderActorId, receiverActorId, relId, giftId, giftCategory, swf, wrappingColor, msg |  |
| `OpenGift` | actorId, giftId |  |
| `removeFromWishlist` | actorId, giftId |  |

#### `WebService.Gifts.AMFGiftableMembershipService`

Chemin AMF : `MovieStarPlanet.WebService.Gifts.AMFGiftableMembershipService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetGiftableMemberships` | variante 1: VipCertificateStatus.GIVABLE<br>variante 2: VipCertificateStatus.OFFERED<br>variante 3: VipCertificateStatus.REDEEMED | 3 variantes |
| `GetMembershipsForUser` | variante 1: param1, -1, param2, param3<br>variante 2: param1, 1, param2, param3 | 2 variantes |
| `GetNumberOfUnredeemedMemberships` | — |  |
| `GetReceivedGiftableMemberships` | variante 1: VipCertificateStatus.OFFERED<br>variante 2: VipCertificateStatus.REDEEMED | 2 variantes |
| `GiveGiftableMembership` | param1, param2, "", "" |  |
| `HasMembershipActivity` | — |  |
| `RedeemGiftableMembership` | param1 |  |
| `RejectGiftedMembership` | param1 |  |

#### `WebService.Gifts.AMFGiftsService+Version2`

Chemin AMF : `MovieStarPlanet.WebService.Gifts.AMFGiftsService+Version2`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddItemToWishlist` | clothIds, clothColors |  |
| `AwardStartupReward` | actorId |  |
| `BuyGift` | senderId, receiverId, giftId, SWF |  |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize |  |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize |  |
| `GetGift` | giftId |  |
| `GetGiftLog` | variante 1: giftLogId<br>variante 2: param1 | 2 variantes |
| `GetMarketingStepGift` | actorId |  |
| `GiveGiftOfCategory` | senderActorId, receiverActorId, relId, giftId, contentCategory, swf |  |
| `HandleGift` | — |  |
| `IsInUseInRooms` | actorClothesRelId |  |
| `OpenGift` | receiverId, giftId |  |
| `ReturnMassGifts` | singleActorId, multipleActorIds, received |  |
| `RevertTrade` | giftLogId |  |
| `SetMarketingStep` | param1, param2, param3 |  |
| `UpdateGift` | actorId |  |
| `UpdateRetention` | actorId |  |
| `refundGift` | giftLogId, giftId |  |
| `removeFromWishlist` | actorId, giftId |  |
| `returnGift` | giftLogId, giftId |  |

### Scrapblog, photos, design

#### `MobileServices.AMFDesignService`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFDesignService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AutoRenameDesign` | param1 |  |
| `BuyDesignCopy` | actorId, designId |  |
| `CancelDesignSale` | actorId, desginId |  |
| `DeleteDesign` | actorId, designId |  |
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds |  |
| `GetDesignTemplatesPage` | skindId, categories, pageIndex, pageSize |  |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageid, pagesize |  |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageid, pagesize |  |
| `GetPagedListOfMyDesigns` | actorId, pageid, pagesize |  |
| `GetPagedListOfNewestDesigns` | skinId, pageid, pagesize |  |
| `GetPagedListOfTopDesigns` | skinId, pageIndex, pageSize |  |
| `ModeratorDeleteDesigns` | actorId, designId |  |
| `NumberOfDesignsForSale` | actorId |  |
| `ProduceDesign` | actorId, designId |  |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `SearchDesign` | searchString, pageid, pagesize |  |
| `SearchDesigner` | searchString, pageid, pagesize |  |
| `SellDesign` | actorId, designId, amount |  |

#### `WebService.DesignStudio.AMFDesignShopWebService`

Chemin AMF : `MovieStarPlanet.WebService.DesignStudio.AMFDesignShopWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyDesignCopy` | actorId, designId |  |
| `CancelDesignSale` | param1, param2 |  |
| `GetDesignsForSale` | param1, param2, param3 |  |
| `NumberOfDesignsForSale` | param1 |  |
| `SellDesign` | param1, param2, param3 |  |

#### `WebService.DesignStudio.AMFDesignStudioWebService`

Chemin AMF : `MovieStarPlanet.WebService.DesignStudio.AMFDesignStudioWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AutoRenameDesign` | param1 |  |
| `DeleteDesign` | actorId, designId |  |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageID, pageSize |  |
| `GetPagedListOfDesignsFromUser` | actorId, pageId, pageSize |  |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageID, pageSize |  |
| `GetPagedListOfMyDesigns` | actorId, pageID, pageSize |  |
| `GetPagedListOfNewestDesigns` | skinId, pageID, pageSize |  |
| `GetPagedListOfTopDesigns` | skinId, pageID, pageSize |  |
| `ModeratorDeleteDesigns` | actorId, designId |  |
| `ProduceDesign` | actorId, designId |  |
| `RenameDesign` | param1, param2, param3 |  |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `SearchDesign` | searchString, pageID, pageSize |  |
| `SearchDesigner` | searchString, pageID, pageSize |  |

#### `WebService.ImageUpload.AMFImageUpload`

Chemin AMF : `MovieStarPlanet.WebService.ImageUpload.AMFImageUpload`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddView` | param1, param2 |  |
| `DeleteImage` | param1, param2 |  |
| `EditHeadline` | param1, param2, param3, param4 |  |
| `EditHeadlineMod` | param1, param2 |  |
| `EditStatusMod` | variante 1: id, -2<br>variante 2: param1, param2 | 2 variantes |
| `GetFriendsUploads` | param1, param2, param3 |  |
| `GetModSearch` | param1, param2, param3 |  |
| `GetMyUploads` | param1, param2, param3 |  |
| `GetMyUploadsForArtbook` | param1 |  |
| `GetNewUploads` | param1, param2, param3 |  |
| `GetRemainingUploadCount` | param1, param2 |  |
| `GetSingleImage` | param1, param2 |  |
| `GetSingleImageModerator` | param1 |  |
| `GetSingleImageWithGuid` | param1, param2 |  |
| `GetSingleImageWithGuidModerator` | param1 |  |
| `GetTopUploads` | param1, param2, param3 |  |
| `GetUploadsFromUser` | param1, param2, param3 |  |
| `GetUserUploads` | param1, param2, param3 |  |
| `LikeImage` | actorId, imageUploadId |  |
| `PollImages` | param1 |  |
| `PurchaseUpload` | param1 |  |
| `SearchFriendsUploads` | param1, param2, param3, param4 |  |
| `SetPhotoUploadRulesAccepted` | param1 |  |
| `UploadImageWithSnapshot` | param1, param2, _loc5_, param3 |  |

#### `WebService.ScrapBlog.AMFClipArtService`

Chemin AMF : `MovieStarPlanet.WebService.ScrapBlog.AMFClipArtService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds |  |

#### `WebService.ScrapBlog.AMFScrapBlogService`

Chemin AMF : `MovieStarPlanet.WebService.ScrapBlog.AMFScrapBlogService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AdminDeleteScrapBlog` | param1, param2, param3 |  |
| `DeleteScrapBlog` | param1, param2 |  |
| `GetClipArtCategories` | — |  |
| `GetClipArtNew` | param1, param2 |  |
| `GetFriendsScrapBlogs` | param1, param2, param3 |  |
| `GetFriendsScrapBlogsBatched` | param1, param2 |  |
| `GetHighscoreScrapBlogs` | param1, param2, param3, param4, param5, param6 |  |
| `GetNewestScrapBlogs` | param1, param2 |  |
| `GetPrivateScrapBlogs` | param1, param2, param3 |  |
| `GetScrapBlogsBySearch` | _loc3_, _loc5_, _loc6_, _loc4_ |  |
| `GetScrapBlogsByType` | param1, param2, param3 |  |
| `GetScrapBlogsByUser` | param1, param2, param3 |  |
| `GetScrapBlogsFriendsLiked` | param1, param2, param3 |  |
| `GetSubmissibleScrapBlogs` | param1, param2, param3 |  |
| `LikeScrapBlog` | actorId, scrapBlogId, ownerId |  |
| `LoadScrapBlog` | param1, param2 |  |
| `LoadTemplateByType` | param1 |  |
| `ReplicateScrapblog` | param1, param2 |  |
| `SaveScrapBlogWithSnapshot` | actorId, scrapBlog, snapshotSmall, snapshotBig |  |
| `SetArtbookRulesAccepted` | param1 |  |

### Média (animations, fonds, musique)

#### `MobileServices.AMFAnimationsServiceForMobile`

Chemin AMF : `MovieStarPlanet.MobileServices.AMFAnimationsServiceForMobile`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActorAnimationsByCategory` | param1 |  |
| `GetAnimationsByFrameLabels` | param1 |  |

#### `WebService.Media.AMFMediaService`

Chemin AMF : `MovieStarPlanet.WebService.Media.AMFMediaService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetAnimations` | — |  |
| `GetBackgrounds` | false |  |
| `GetBackgroundsPaged` | false, pageIndex, pageSize |  |
| `GetMusic` | false |  |
| `GetMyAnimations` | param1 |  |
| `GetMyBackgrounds` | param1 |  |
| `GetMyMusic` | param1 |  |
| `getAnimationCount` | param1 |  |
| `getClothesCount` | param1 |  |
| `getPropsCount` | param1 |  |

### Quêtes, succès, récompenses

#### `WebService.AMFAwardService`

Chemin AMF : `MovieStarPlanet.WebService.AMFAwardService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `RequestAnchorCharacterIntroductionAward` | actorId |  |

#### `WebService.Achievement.AMFAchievementWebService`

Chemin AMF : `MovieStarPlanet.WebService.Achievement.AMFAchievementWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CheckLoginAchievements` | param1 |  |
| `ClaimReward` | param1, param2 |  |
| `GetAchievementData` | — |  |
| `GetActorAchievementProgressAll` | actorId |  |
| `GetArtbookStickers` | param1 |  |
| `GetClaimableCategories` | param1 |  |
| `GetPagedAchievements` | actorId, category, pageIndex, pageSize |  |
| `GetTotalProgress` | actorId, category |  |

#### `WebService.Awarding.AMFAwardingService`

Chemin AMF : `MovieStarPlanet.WebService.Awarding.AMFAwardingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BuyDiamondRespin` | — |  |
| `GetWheelData` | — |  |
| `RequestIntroductionAward` | actorId |  |
| `SpinWheel` | wheelId |  |
| `awardActor` | actorId, amount, type, winSpendType |  |
| `claimAdvertAwardByCampaign` | campaignId |  |
| `claimAdvertViewAward` | type, amount, actorId |  |
| `claimDailyAward` | awardStr, amnt, loggedInActorId |  |
| `countAwardsLeft` | awardStr, actorId |  |
| `hasAllDailyAwardLeft` | awardStr, actorId |  |
| `hasAnyDailyAwardLeft` | awardStr, actorId |  |
| `hasSomeDailyAwardLeft` | awardStr, actorId |  |

#### `WebService.Holiday.AMFHolidayService`

Chemin AMF : `MovieStarPlanet.WebService.Holiday.AMFHolidayService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetReceivedChristmasPresents` | param1, param2 |  |
| `RequestChristmasPresent` | param1, param2, param3 |  |

#### `WebService.PiggyBank.AMFPiggyBankService`

Chemin AMF : `MovieStarPlanet.WebService.PiggyBank.AMFPiggyBankService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CanDestroyPiggyBank` | — |  |
| `DestroyPiggyBank` | — |  |
| `GetPiggyBank` | — |  |

#### `WebService.Quest.AMFQuestService`

Chemin AMF : `MovieStarPlanet.WebService.Quest.AMFQuestService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BeginQuest` | param1, param2 |  |
| `BeginSpecialQuest` | param1, param2 |  |
| `ClaimReward` | param1, param2, param3 |  |
| `ClaimRewardForDownloadableClient` | param1, param2, param3 |  |
| `ClaimSpecialQuestBaseReward` | param1, param2 |  |
| `ClaimSpecialQuestSubOrFinalReward` | param1, param2 |  |
| `DiamondSkip` | param1, param2 |  |
| `ForceCompleteCurrentQuest` | param1, param2 |  |
| `ForceCompleteCurrentQuestForDownloadableClient` | param1, param2 |  |
| `GetAllQuestStatus` | param1 |  |
| `GetAllQuestStatusForDownloadableClient` | param1 |  |
| `GetGiftHuntQuestData` | param1, param2 |  |
| `ResetNotifications` | param1, param2 |  |
| `UpdateDoTaskObjectiveAndGetStatus` | param1, param2, param3, param4 |  |
| `UpdateGotoObjectiveAndGetStatus` | param1, param2, param3 |  |
| `UpdateSpecialQuestObjectiveOld` | param1, param2, param3 |  |
| `UpdateSpecialQuestObjectives` | param1, param2, param3 |  |

### Compétitions

#### `WebService.Competition.AMFCompetitionService`

Chemin AMF : `MovieStarPlanet.WebService.Competition.AMFCompetitionService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetMovieCompetition` | id |  |
| `GetMovieCompetitionList` | params[0 |  |
| `GetMovieCompetitionListById` | params[0 |  |
| `GetMovieCompetitionListByNewsId` | newsId |  |
| `GetNewsById` | param1, param2, param3 |  |
| `GetParticipatingLooks` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingMovies` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingRooms` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingScrapBlogs` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetSubmittedMovieCompetitionLook` | movieCompetitionId, actorId |  |
| `GetSubmittedMovieCompetitionMovie` | movieCompetitionId, actorId |  |
| `GetSubmittedMovieCompetitionRoom` | movieCompetitionId, actorId |  |
| `GetSubmittedScrapBlog` | competitionId, actorId |  |
| `HasActorVotedInCompetition` | movieCompetitionId, actorId |  |
| `LinkCompetitionToTheme` | newsId, themeId |  |
| `MovieCompetitionPublish` | param1, param2, param3 |  |
| `SaveMovieCompetition` | competition, awardPrizes |  |
| `SubmitEntityToCompetition` | movieCompetitionId, entityId, actorId |  |
| `VoteInMovieCompetition` | movieCompetitionId, movieId, actorId |  |

#### `WebService.DailyCompetition.AMFDailyCompetitionService`

Chemin AMF : `MovieStarPlanet.WebService.DailyCompetition.AMFDailyCompetitionService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `IncrementSubmissionResets` | — |  |
| `addToComp` | param2, param3, param4 |  |
| `canSubmit` | param2, param3 |  |
| `getRandomItem` | param2 |  |
| `getTodaysTheme` | — |  |
| `getVoteScore` | param2 |  |
| `voteFor` | param2, param3, param4, param5, param6 |  |

### Forum, sondages, news, activités

#### `Polls.AMFPollService`

Chemin AMF : `MovieStarPlanet.Polls.AMFPollService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetPoll` | pollId, actorId |  |
| `GetPollLatest` | actorId |  |
| `GetPolls` | pageindex, pagesize |  |
| `GetPollsUnused` | — |  |
| `LinkPolls` | pollId, nextPollId |  |
| `NewPoll` | question, answer1, answer2, answer3, answer4 |  |
| `NewPollPublish` | pollId, locale, siteDomain |  |
| `VotePoll` | pollId, actorId, answer |  |

#### `WebService.Campaign.AMFCampaignService`

Chemin AMF : `MovieStarPlanet.WebService.Campaign.AMFCampaignService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `UseCampaign` | param1, param2 |  |

#### `WebService.Forums.AMFForumService`

Chemin AMF : `MovieStarPlanet.WebService.Forums.AMFForumService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AdminCreateTopic` | actorName, actorPassword, forumId, subject, type, message, colorCode, subjectChatLogId, messageChatLogId |  |
| `AdminCreateTopicPoll` | actorId, forumId, filteredQuestion, filteredAnsers, topicType, adminUserName, adminPassword, -1 |  |
| `CheckAllowedCreateTopic` | actorId |  |
| `CreatePostWithModerationCall` | actorId, actorName, topicId, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `CreateTopicPollWithModerationCall` | actorId, actorName, forumId, pollQuestion, pollAnswers, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `CreateTopicWithModerationCall` | actorId, actorName, forumId, forumSubject, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `DeletePost` | postId, actorName, actorPassword |  |
| `DeleteTopic` | topicId, actorName, actorPassword |  |
| `GetFilteredTopics` | params.forumId, params.filterId, params.actorId, pageIndex, pageSize |  |
| `GetForums` | — |  |
| `GetPostAmount` | topicId |  |
| `GetPostData` | postId |  |
| `GetPosts` | topicID, pageIndex, pageSize |  |
| `GetTopic` | topicId, actorId |  |
| `ToggleSticky` | actorName, actorPassword, topicId, type |  |
| `UpdatePost` | actorId |  |
| `UpdateTopic` | topic.TopicId |  |
| `UserDeletePost` | actorId, postId |  |

#### `WebService.NewsService.AMFNewsService`

Chemin AMF : `MovieStarPlanet.WebService.NewsService.AMFNewsService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetActiveNewsScrapBlog` | param1 |  |
| `GetActiveNewsSlides` | param1 |  |
| `GetNewsById` | param1 |  |
| `NewsClicked` | param1, param2 |  |
| `SaveNews` | param1 |  |
| `SaveThemeSnapshot` | param1, param2, param3, param4, param5, param6 |  |
| `SetNewsUsage` | param1 |  |

#### `WebService.NotificationCenter.AMFNotificationCenterService`

Chemin AMF : `MovieStarPlanet.WebService.NotificationCenter.AMFNotificationCenterService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `ClaimBonus2` | actorId, contentTypes |  |
| `GetNotificationCount` | param1 |  |
| `GetNotificationsWithImageGuid` | param1 |  |
| `GetThirdPatyAppNotifications` | param1 |  |
| `GetTotalFameAward` | — |  |

### Highscores & thèmes

#### `WebService.Content.AmfContentService`

Chemin AMF : `MovieStarPlanet.WebService.Content.AmfContentService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetItemsInCurrentTheme` | ticket, themeId, hash |  |
| `GetLastEditedDate` | param1, param2, param3, param4 |  |

#### `WebService.ExternalApps.AMFExternalAppsService`

Chemin AMF : `MovieStarPlanet.WebService.ExternalApps.AMFExternalAppsService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetExternalAppsInCountry` | variante 1: _loc2_, "ALL"<br>variante 2: countryCode, "Android"<br>variante 3: countryCode, "IOS" | 3 variantes |

#### `WebService.Highscore.AMFHighscoreService`

Chemin AMF : `MovieStarPlanet.WebService.Highscore.AMFHighscoreService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetHighscoreActor` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreAnimations` | pageIndex, pageSize |  |
| `GetHighscoreBackgrounds` | pageIndex, pageSize |  |
| `GetHighscoreBonster` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreClothes` | pageIndex, pageSize |  |
| `GetHighscoreItems` | pageIndex, pageSize |  |
| `GetHighscoreLook` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreMovie` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscorePet` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreScrapBlog` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreYouTube` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |

#### `WebService.WorldTheme.AMFWorldThemeService`

Chemin AMF : `MovieStarPlanet.WebService.WorldTheme.AMFWorldThemeService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateNewWorldTheme` | themeName, folderName, themeId |  |
| `CreateNewWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |  |
| `DeleteWorldTheme` | worldThemeId |  |
| `EditWorldTheme` | worldThemeId, themeName, themeId |  |
| `EditWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |  |
| `GetAllWorldThemes` | — |  |
| `GetOldWorldThemes` | — |  |
| `GetPresentFutureWorldThemes` | — |  |
| `GetWorldThemeAreasByWorldThemeId` | worldThemeId |  |
| `GetWorldThemeChatRoom` | worldThemeId |  |
| `GetWorldThemeInfo` | — |  |
| `SaveWorldThemeChatRoomInfo` | worldThemeId, roomName, backgroundFileName, requiredItemType, requiredItemId |  |

### Admin, upload, modération, infra

#### `WebService.AMFCommonService`

Chemin AMF : `MovieStarPlanet.WebService.AMFCommonService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `ActorHasLiked` | param3, param1, param2 |  |
| `LikeAdd` | entityType, entityId, selfActorId, receiver |  |
| `LogChat` | param1, param2, param3, InputLocations.DESTINATION_TYPE_USER |  |
| `LogInput` | roomId, actorId, roomInstanceId, message, destinationType |  |
| `SendContentEmail` | param1, param2, param3, param4, param5 |  |
| `getNowAsString` | — |  |

#### `WebService.Admin.AMFAdminService`

Chemin AMF : `MovieStarPlanet.WebService.Admin.AMFAdminService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `BlockName` | param1, param2, param3 |  |
| `ClearCache` | param1, param2, true |  |
| `ClearNewMarkings` | param1, param2 |  |
| `DeleteTwitterText` | param1, param2, param3 |  |
| `GetActorLocale` | param1 |  |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize |  |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize |  |
| `GetBadWordActorList` | pageIndex, pageSize |  |
| `GetBlockedIP` | ipAsInt, moderatorName, moderatorPass |  |
| `GetBlockedInfo` | ipAsInt, moderatorName, moderatorPass |  |
| `GetBlockedNames` | searchphrase |  |
| `GetChatLogList` | actorId, pageIndex, pageSize |  |
| `GetChatLogListByReportTime` | paramObj.actorId, paramObj.reportId, pageIndex, pageSize |  |
| `GetChatLogListLocked` | actorId |  |
| `GetIPLoginType` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetIPUsers` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetIPWarnings` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetLocaleResources` | param1, param2, param3, param4, param5 |  |
| `GetLoginHistory` | param1, param2, param3 |  |
| `GetModeratorList` | pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |  |
| `GetModeratorWarningCount` | paramObj.moderatorId, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |  |
| `GetModeratorWarnings` | paramObj.moderatorId, paramObj.date, pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |  |
| `GetReportList` | onlyGetNotHandled, pageIndex, pageSize |  |
| `GetReportOverview` | — |  |
| `GetSecureModuleUrl` | — |  |
| `GetTotalModeratorActivitiesDone` | actorId, moderatorName, moderatorPass |  |
| `GetWarnedIPListNew` | paramObj.blocked, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass, paramObj.specificIp ? paramObj.specificIp : 0 |  |
| `GetWarningLog` | pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |  |
| `GiveAutoWarning` | param1, param2, param3, param4 |  |
| `IsAdminSite` | param1, param2 |  |
| `IsUploadSite` | — |  |
| `LockOutUser` | param1, param2, param3, param4, param5 |  |
| `RemoveRoboBlastContent` | actorId, contentType, contentId, reporterId, site |  |
| `ReportHandled` | reportId, handledByActorId |  |
| `SaveLocaleResources` | param1 |  |
| `UnblockName` | param1, param2, param3 |  |
| `blockIP` | ipAsIntToBlock, moderatorActorId, moderatorName, moderatorPass, blockingDaysCount, comment |  |
| `deleteMovieViaProfile` | movieId, moderatorName, moderatorPass |  |
| `getChatRoomOpenCloseTimes` | — |  |
| `isIPBlockedNew` | ipAsIntToFind, moderatorName, moderatorPass |  |
| `markIpAsPublic` | ipAsIntToMark, moderatorName, moderatorPass |  |
| `saveSpamReport` | spamtext, moderatorActorId, moderatorName, moderatorPass |  |
| `setChatRoomOpenCloseTimes` | open, close |  |
| `unblockIP` | ipAsIntToUnblock, moderatorID, moderatorName, moderatorPass, comment |  |
| `unmarkIpAsPublic` | ipAsIntToUnmark, moderatorName, moderatorPass |  |

#### `WebService.AnimationSnapshot.AMFAnimationSnapshotService`

Chemin AMF : `MovieStarPlanet.WebService.AnimationSnapshot.AMFAnimationSnapshotService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `getAnimationNames` | — |  |
| `saveImage` | data, name |  |

#### `WebService.Common.AMFCommonWebService`

Chemin AMF : `MovieStarPlanet.WebService.Common.AMFCommonWebService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `GetEntityName` | param1, param2 |  |
| `GetPlaylistExternalRef` | param1 |  |
| `LikeAdd` | entityType, entityId, actorId, receiverId |  |
| `SaveRoomWithSnapshot` | wallpaper, floor, arrayOfMyRoomInstances, roomSnapshotProfile, roomSnapshotMedium, roomSnapshotSmall |  |
| `SendContentEmail` | param1, param2, param3, param4, param5 |  |

#### `WebService.Logging.AMFLoggingService`

Chemin AMF : `MovieStarPlanet.WebService.Logging.AMFLoggingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `ClientLog` | param1, param2 |  |
| `CreateTestException` | — |  |
| `GetLatestServerException` | — |  |
| `LogClient` | param1, param2 |  |

#### `WebService.Moderation.AMFModeration`

Chemin AMF : `MovieStarPlanet.WebService.Moderation.AMFModeration`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CheckNewUsername` | userName, this._site |  |
| `FilterText` | variante 1: param1, param5, param4, param2, param3<br>variante 2: param1, param5, param4, param2, param3, param8, param9 | 2 variantes |
| `LoginEvent` | param1 |  |
| `ReportUser` | param2, param3, param4, param6, this._site, param7 |  |
| `ReportUserNeb` | param2, param5, param4, param6 |  |

#### `WebService.Os.AMFOs`

Chemin AMF : `MovieStarPlanet.WebService.Os.AMFOs`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateOsRef` | — |  |
| `RunOsCheck` | refId, hist.join(":") |  |

#### `WebService.PerformanceTracking.AMFPerformanceTrackingService`

Chemin AMF : `MovieStarPlanet.WebService.PerformanceTracking.AMFPerformanceTrackingService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `AddEntry` | param1, param2 |  |

#### `WebService.Snapshots.AMFGenericSnapshotService`

Chemin AMF : `MovieStarPlanet.WebService.Snapshots.AMFGenericSnapshotService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CreateSnapshot` | variante 1: param1, param2, param3, param4<br>variante 2: param1, param2, param3, param4, param5 | 2 variantes |
| `CreateSnapshotSmallAndBig` | param1, param2, param3, param4, param5, param6 |  |

#### `WebService.TagManager.AMFTagManager`

Chemin AMF : `MovieStarPlanet.WebService.TagManager.AMFTagManager`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DeleteTag` | param1 |  |
| `GetAllTags` | — |  |
| `GetBackgroundTags` | — |  |
| `GetTagsForSkinClothes` | param2 |  |
| `GetTagsInCategorySkin` | param2, param3 |  |
| `SaveTag` | param1 |  |

#### `WebService.ThemeManager.AMFThemeManagerService`

Chemin AMF : `MovieStarPlanet.WebService.ThemeManager.AMFThemeManagerService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `DeleteTheme` | param1 |  |
| `GetAllCampaigns` | — |  |
| `GetAllThemes` | — |  |
| `GetCurrectNewCategorySortIndex` | — |  |
| `InsertTheme` | param1, param2, param3, param4 |  |
| `LabelClothesWithTheme` | param1, param2 |  |
| `RetrieveThemeID` | param1, param2 |  |
| `SortShoppingItems` | param1, param2, param3 |  |
| `UpdateTheme` | param1 |  |

#### `WebService.Upload.AMFUploadService`

Chemin AMF : `MovieStarPlanet.WebService.Upload.AMFUploadService`

| Méthode | Paramètres (client) | Notes |
|--------|-------------------|------|
| `CheckAnimationExists` | animationName |  |
| `DeleteClipArt` | clipart, subpath |  |
| `DeleteFacepart` | facepartId, type |  |
| `DeleteWallpaper` | wallpaperId |  |
| `EditAnimation` | animationId, name, price, discount, checkVip, checkNew, checkDeleted, animCategoryId, themeID, priceDiamonds |  |
| `EditClipArt` | clipart, subpath, sort, checkvip, checknew, price, diamondsPrice |  |
| `EditFacepart` | facepartId, type, gender, name, fileName, price, checkvip, checknew, checkreg, discount, sortorder, themeID, priceDiamonds |  |
| `FileExistsCheck` | key |  |
| `GetAnimationCategories` | — |  |
| `GetClipArtPath` | clipart |  |
| `InsertAnimation` | name, price, diamondsprice, animCategory, vip, fileName, themeID |  |
| `InsertBackground` | name, price, backgroundCategory, vip, fileName, themeID |  |
| `InsertClipArt` | type, category, fileName, checkvip, checkNew, sortorder, price, diamondPrice, colorScheme |  |
| `InsertFacepart` | type, gender, name, fileName, price, diamondPrice, checkvip, dragonBone, defaultColors, checknew, checkreg, discount, sortorder, themeID, date, hidden |  |
| `InsertWallpaper` | type, roomtype, name, filepath |  |
| `getAllColorschemelessClothes` | pageIdx, pageSize |  |
| `getBonsterInfo` | templateName |  |
| `getClipArtCategoryNames` | paramid |  |
| `getClipArtTypes` | — |  |
| `giveBonster` | templateName |  |
| `saveClothUpdater` | cloth, themeID |  |
| `setClothColorSchemes` | variante 1: [colorSchemeObject<br>variante 2: clothColorSchemes | 2 variantes |
| `updateAnimation` | copy, themeID |  |
| `updateBackground` | copy, themeID |  |
| `updateBonsterColors` | bonsterId, colorMatrix |  |
| `updateBonsterScale` | bonsterId, mobScale, webScale |  |
| `updateCloth` | clothUpdater |  |
| `updateMusic` | copy |  |
| `uploadBonster` | templateName, templateId, armatureName, price, diamondsPrice, isVIP, deleted, specialEggCrate, scale, scaleWeb |  |

---

## Fichiers sources principaux

| Sujet | Fichier |
|-------|---------|
| Nourriture | `pets/module/petpopup/service/food/PetFood.as` |
| Favoris | `pets/module/petpopup/service/food/PersonalityFoods.as` |
| Prix bonbons | `bonster/service/BonsterCandyPrices.as` |
| Constantes Bonster | `bonster/BonsterConstants.as`, `bonster/BonsterUtils.as` |
| Caressage Bonster | `bonster/BonsterClickItem.as`, `bonster/service/BonsterAMFService.as` |
| Caressage ancien pet | `pet/service/PetAMFService.as`, `Components/MonsterPopup.as` |
| Rate limits | `utils/RateLimiterController.as`, `amf/AmfListener.as` |
| Sécurité AMF | `amf/AmfCall.as`, `amf/checksum/ChecksumCalculator.as`, `amf/AmfCallExternalCommands.as`, `amf/TicketGenerator.as` |
| OS Check | `moviestar/snapshot/SnapLoader.as` |
| Boosters | `services/spendingservice/valueObjects/SpecialsItem.as` |
| Fame booster | `utils/actorvalues/ActorValueManager.as` |
| Limite 10 pets/room | `chatrooms/view/overlayUserInterface/ChatRoomItemSelectorView.as` |
| Boutique pets | `shopping/module/petshop/model/PetShopModel.as` |
| Hôtel | `pets/hotel/PetHotel.as` |
| Anciens pets | `pet/utils/MonsterConstants.as` |
| Looks | `look/service/LookAMFService.as` |
| Vêtements / acteur | `actorservice/mobileservice/ActorAmfService.as`, `actorservice/service/ActorAmfServiceForWeb.as` |
| Boutique | `services/shopcontentservice/ShopContentAmfService.as` |
| Dépenses diamants | `services/spendingservice/SpendingAmfService.as` |

---

---

# MSP Infos — Pets & mechanics reference

Documentation extracted from the decompiled Flash client (`msp_client/scripts/`).  
Values marked **server** are not hardcoded in the client and may vary by region or update.  
**Empirical** values come from community observations or repo tools (`pets_msp/`, `test_script/pet_caress.py`) — verify in-game.

---

## Table of contents

1. [Pet types & IDs](#pet-types--ids)
2. [Bonster lifecycle (egg, crate, stages)](#bonster-lifecycle-egg-crate-stages)
3. [Food (Bonsters)](#food-bonsters)
4. [Personalities & favorites (full table)](#personalities--favorites-full-table)
5. [Candy — price per level](#candy--price-per-level)
6. [XP & levels](#xp--levels)
7. [Needs: hunger, wash, play](#needs-hunger-wash-play)
8. [Petting another player's pet](#petting-another-players-pet)
9. [Limits (rooms, shop)](#limits-rooms-shop)
10. [Pet hotel](#pet-hotel)
11. [Legacy pets (Monster / Boonie)](#legacy-pets-monster--boonie)
12. [Boosters & specials (diamond shop)](#boosters--specials-diamond-shop)
13. [Rate limits & anti-abuse](#rate-limits--anti-abuse)
14. [Network security & anti-tampering](#network-security--anti-tampering-charles--proxy)
15. [Response codes (all systems)](#response-codes-all-systems)
16. [Pet AMF endpoints](#pet-amf-endpoints)
17. [AMF reference — endpoints & parameters](#amf-reference--services-endpoints--parameters)

---

## Pet types & IDs

| Field | Description | Source |
|-------|-------------|--------|
| `BonsterId` | Shop catalog model ID | Server |
| `BonsterTemplateId` | Visual template ID (skeleton, palettes) | Server |
| `ActorBonsterRelId` | Unique ID of **your** owned pet instance | Server |
| `ActorClickItemRelId` | Unique ID of a legacy pet (Monster/Boonie) | Server |
| `Personality` | 1–5 (Shy, Sporty, Smiley, Sleepy, Smart) | Server |

There is **no** static list of all `BonsterId` values in the client — it is loaded dynamically from the shop and highscores.

**Bonster evolution stages** — visual stages at levels **12** and **24**.  
Reward animations at levels **6, 12, 18, 24, 28, 32**.  
Max UI level: **100** (candy disabled at level 100+).  
Animations unlock at level **6** (`MINIMUM_LEVEL_FOR_ANIMATIONS`).  
Pet name: max **20** characters, moderation required.

---

## Bonster lifecycle (egg, crate, stages)

Source: `ActorBonsterRelItem.as`, `BonsterConstants.as`

| State | Client condition | Visual |
|-------|------------------|--------|
| **Egg (Boonie)** | `EvolutionStage == 0` && `BonsterTemplateId == 0` | scale 0.5 |
| **Crate** | `EvolutionStage == 0` && `BonsterTemplateId != 0` | scale 0.6 |
| **Stage 1** | `EvolutionStage == 1` | scale 0.65 |
| **Stage 2** | `EvolutionStage == 2` | scale 0.85 |
| **Stage 3** | `EvolutionStage == 3` | scale 1.0 |

- **Boonie** = legacy egg pet (`BonsterTemplateId == 0`).
- **Hatch**: `HatchBonster` + animation; on hatch `WashPoints = 50`.
- **Auto evolution** at levels **12** and **24**.
- **Instant evolve**: `INSTANT_PET_GROW` booster → `InstantEvolveBonster`.

---

## Food (Bonsters)

Source: `PetFood.as`

| ID | Name | SC price | 💎 price | Type |
|----|------|----------|----------|------|
| 1 | Chicken | 3 | — | normal |
| 2 | Apple | 3 | — | normal |
| 3 | Burger | 3 | — | normal |
| 4 | Sushi | 3 | — | normal |
| 5 | Pizza | 3 | — | normal |
| 6 | Orange | 3 | — | normal |
| 7 | Sandwich | 3 | — | normal |
| 8 | Pineapple | 3 | — | normal |
| 9 | Toast | 3 | — | normal |
| 10 | Banana | 3 | — | normal |
| 11 | Medicine | 20 | — | medicine |
| 12 | Candy | — | 1 | normal |

Type constants: `FOODTYPE_NORMAL = 1`, `FOODTYPE_MEDICIN = 2`.

**Medicine** (ID 11) cures a **sick** pet. **Candy** (ID 12) uses **dynamic** diamond pricing — see next section.

---

## Personalities & favorites (full table)

Source: `PersonalityFoods.as`, `FoodListItemRenderer.as`

Each Bonster has a server-assigned `Personality` (1–5). Favorite foods show **sparkles** in the feed menu.

### Personality constants

| ID | Constant | EN | FR |
|----|----------|----|----|
| 1 | `BONSTER_PERSONALITY_SHY` | Shy | Timide |
| 2 | `BONSTER_PERSONALITY_SPORTY` | Sporty | Sportif |
| 3 | `BONSTER_PERSONALITY_SMILEY` | Smiley | Souriant |
| 4 | `BONSTER_PERSONALITY_SLEEPY` | Sleepy | Dormeur |
| 5 | `BONSTER_PERSONALITY_SMART` | Smart | Malin |

### Food × personality matrix

| ID | Food | Shy | Sporty | Smiley | Sleepy | Smart |
|----|------|:---:|:------:|:------:|:------:|:-----:|
| 1 | Chicken | ★ | | | | |
| 2 | Apple | ★ | | | | |
| 3 | Burger | | | ★ | | |
| 4 | Sushi | | ★ | | | |
| 5 | Pizza | | | | | ★ |
| 6 | Orange | | ★ | | | |
| 7 | Sandwich | | | | ★ | |
| 8 | Pineapple | | | | | ★ |
| 9 | Toast | | | | ★ | |
| 10 | Banana | | | ★ | | |

### Summary by personality

| Personality | Favorite IDs | Names |
|-------------|--------------|-------|
| Shy (1) | 1, 2 | Chicken, Apple |
| Sporty (2) | 4, 6 | Sushi, Orange |
| Smiley (3) | 3, 10 | Burger, Banana |
| Sleepy (4) | 7, 9 | Sandwich, Toast |
| Smart (5) | 5, 8 | Pizza, Pineapple |

---

## Candy — price per level

Sources: `BonsterCandyPrices.as`, `GetBonsterCandyPrices`, `FoodListItemRendererMediator.as`

At login, `GetBonsterCandyPrices` fills `candyPriceRaiseLevels` with `{ LevelFloor, LevelCeil, CandyPrice }`.

**`calculateCandyPrice(level)`**: find tier where `level >= LevelFloor && level < LevelCeil`; else use last tier.  
UI **overrides** default `priceDiamonds = 1` on `PetFood.CANDY`.  
**Level ≥ 100**: candy **unavailable**.

**`diamondsToEvolve(level)`**: sum of candy prices from `level` to next evolution threshold (12 or 24); returns 0 if level ≥ 24.

**Typical tiers (empirical — server)**: often **1💎** at low levels, **2💎** at higher tiers. Capture exact table via AMF `GetBonsterCandyPrices` at login.

---

## XP & levels

| Situation | XP | Source |
|-----------|-----|--------|
| Favorite food | **60** | Empirical (`pets_msp/`) |
| Regular food | **40** | Empirical (`pets_msp/`) |

`BonsterInteractionResponse` fields: `experience`, `experienceToNextLevel`, `experienceToCurrentLevel`, `level`, `evolutionStage`, `interactionPoints`, `lastInteractionDate`, `fameEarned`, `resultCode`. Exact XP math is **server-side**.

**Visual scales per stage** (`BonsterConstants.as`):

| Stage | Scale |
|-------|-------|
| Egg | 0.5 |
| Crate | 0.6 |
| Evolution 1 | 0.65 |
| Evolution 2 | 0.85 |
| Evolution 3 | 1.0 |

Wash points at hatch: **50** (`WASHPOINTS_AT_HATCH`).

---

## Needs: hunger, wash, play

Source: `BonsterUtils.as`, `BonsterConstants.as`, `Model.as`, `ViewConstants.as`

| Mechanic | Value |
|----------|-------|
| Decay (food / wash / play) | **−1 point / 15 min** |
| Sickness | after **3 days** without feeding |
| Max UI points (wash/play) | **100** |

**Power bar** (`ViewConstants`): ≥100→1, ≥75→2, ≥50→3, ≥25→4, ≥0→5.

**Dirt (WashPoints)**: ≤10 → 3 dirt, ≤25 → 2 dirt, ≤45 → 1 fly; hatch starts at **50**.

**AMF (own pet)**: `FeedBonster(foodId)`, `WashBonster(washPoints)`, `PlayWithBonster(playPoints)`.

---

## Petting another player's pet

### Client flow (Bonster)

1. Click another player's pet in chat room / MyRoom.
2. AMF `PetFriendBonster(actorId, actorBonsterRelId)`.
3. Server returns a plain **integer** (not `BonsterInteractionResponse`).
4. If **> 0**: SC animation with that amount.
5. If **== 0**: no reward (already petted or server deny).
6. If **== -429**: rate limited.

### SC calculation — what the client says

| Question | Answer |
|----------|--------|
| Formula in client? | **No** |
| Who calculates? | **Server only** |
| AMF return type | `int` |
| Display | Integer = SC credited to **petter** |
| Owner reward | **None** visible client-side |
| Empirical ( `pet_caress.py`) | often **5 SC** when response > 0 — **not** hardcoded in Flash |

### Limits

| Limit | Value |
|-------|-------|
| Per pet / client session | **1×** (`petsPettedAlready`) |
| Server rate limit | `-429` |
| Egg / crate | Not pettable |
| Own Bonster | Opens popup, no SC |
| Legacy pet cooldown UI | 3000 ms (`PET_INTERVAL`) |

---

## Limits (rooms, shop)

| Context | Limit | Source |
|---------|-------|--------|
| Pets in a chat room | **10 max** | `ChatRoomItemSelectorView` (`MAX_PETS_IN_ROOM`) |
| Shop — Top pets | 10 per page | `PetShopModel` |
| Shop — New pets | 9 per page | `PetShopModel` |
| Shop — Bonsters | 12 per page | `PetShopModel` |
| Shop — Boonies | 12 per page | `PetShopModel` |
| Shop — Friends' pets | 3 per page | `PetShopModel` |

---

## Pet hotel

Source: `PetHotel.as`

| Stay | Duration | SC price | VIP required |
|------|----------|----------|--------------|
| Period 0 | 7 days | 100 | No |
| Period 1 | 14 days | 200 | No |
| Period 2 | 28 days | 300 | **Yes** |

**50 % off** when `SHOPPING_SPREE` booster is active.

Endpoints: `CheckInBonsterAtPetHotel`, `CheckOutBonsterFromPetHotel` (Bonsters); `CheckInPetHotel`, `CheckOutPetHotel` (legacy pets).

---

## Legacy pets (Monster / Boonie)

Source: `MonsterConstants.as`

| Constant | Value |
|----------|-------|
| Food price | 10 SC |
| Medicine price | 20 SC (or 300 SC variant 2) |
| VIP food points | 2 |
| Petting interval | 3000 ms |
| Max dirt points | 3 |
| Time per dirt point | 3 s |
| Max feeding interval | 24 h |
| Min feeding interval | 8 h |
| Food points per stage | 9 |
| Sick level | −2 |

---

## Boosters & specials (diamond shop)

Source: `SpecialsItem.as`, `ActiveSpecialsType.as`

String identifiers (used for purchases and active effects):

| Identifier | Known effect (client) |
|------------|----------------------|
| `FAME_BOOSTER` | Fame × **2** (`ActorValueManager`); cannot buy while active |
| `SHOPPING_SPREE` | −50 % on eligible purchases (e.g. pet hotel) |
| `INSTANT_PET_GROW` | Instant evolution via `InstantEvolveBonster` |
| `CHANGE_PET` | Switch active pet |
| `FAME_WHEEL` | Fame wheel |
| `DIAMOND_TWIT` | Diamond tweet |
| `DIAMOND_CLOTHES` | Diamond clothes |
| `DIAMOND_CHARACTER_EFFECT` | Character effect |
| `CHARACTER_POPUP` | Character popup |
| `SPECIAL_GREETING` | Special greeting |
| `STARCOIN_SHOOTER` | Starcoin mini-game |

Numeric `SpecialsItemId` values are **server**-loaded via `SpendingAmfService`.

Additional fame bonus: **×1.1** if player is a celebrity (`isCeleb`), stacks with Fame Booster.

---

## Rate limits & anti-abuse

### Two distinct mechanisms

The client handles rate limiting at **two levels**:

| Level | Detection | Source | Popup |
|-------|-----------|--------|-------|
| **1 — AMF body** | Return value `== -429` | `RateLimiterController` | `INTERACTION_LIMIT_REACHED_BY_DESIGN_*` (per endpoint) or silent |
| **2 — HTTP transport** | Description contains `"429"` | `AmfListener` | `MSP1_POPUP_TOO_MANY_REQUESTS_*` + `Rate Limited` log |

Business logic code: **`CODE_IS_REQUEST_BLOCKED = -429`**.

> **Important**: the exact number of requests before a block (per minute, hour, day, per endpoint or per account) is **not in the client**. Quotas are computed **server-side only**. The client only detects `-429` or HTTP 429 and shows a popup.

### Complete rate-limited endpoint table (client)

Each row = call where `RateLimiterController.isLimitedAndPromptIfSo()` is invoked.

| Endpoint | AMF service | Field checked for `-429` | Popup when limited |
|----------|-------------|--------------------------|-------------------|
| `PetFriendBonster` | `AMFBonsterService` | return integer (SC) | **No** (`showPopup = false`) |
| `PetFriendPet` | `PetAMFService` | *(no explicit check)* | — |
| `MovieWatched` | `AMFMovieService` | `awardedFame` / `returnType` | Yes |
| `LikeAdd` | `AMFCommonService` | `fameEarned` | Yes |
| `LikeScrapBlog` | `ScrapBlogAMFService` | `fameEarned` | Yes |
| `LikeImage` | `AMFPictureUploadService` | `Code` | Yes |
| `SpinWheel` | `AMFAwardingService` | `Status` | Yes |
| `GiveAutographAndCalculateTimestamp` | `AMFUserSessionService` | `Fame` | Yes |
| `GiveAutographAndCalculateTimestampNeb` | `AMFActorService` | `Fame` | Yes |
| `SaveRoomWithSnapshot` | `AMFRoomService` | return integer | Yes |
| `OpenGift` | `AMFGiftService` | `GiftLogId` | Yes |
| `ClaimBonus2` | `NotificationCenterAmfService` | `ErrorCode` | Yes |
| `claimDailyAward` | `AMFAwardingService` | `amount` | Yes |
| `claimAdvertViewAward` | `AMFAwardingService` | `amount` | Yes |
| `claimAdvertAwardByCampaign` | `AMFAwardingService` | `amount` | Yes |
| `BuySpecialGreeting` | `SpendingAmfService` | `Code` | Yes |
| `PickupGuidePresent` | `AMFActorService` | `Code` | Yes |

Any other endpoint may also be rate-limited server-side via **HTTP 429** without a dedicated client handler.

### Client-side limits (local anti-spam, not server)

These limits are **hardcoded in the client** — distinct from server rate limits:

| Limit | Value | File |
|-------|-------|------|
| Pet pets / session | **1× per `ActorBonsterRelId` or `ActorClickItemRelId`** | `BonsterAMFService`, `PetAMFService` (`petsPettedAlready`) |
| Max concurrent AMF calls | **10** (configurable `MAX_CONCURRENT_AMF_CALLS`) | `AmfCaller` |
| AMF call timeout | **20 000 ms** | `AmfListener.TIMEOUT_MILLIS` |
| Daily gifts (UI) | **25** displayed (`DAILY_GIFT_LIMIT`) | `GiftService`, `SelectGift` |
| Server daily gift code | **`-20`** (`GIVE_GIFT_RETURN_CODE_DAILY_LIMIT_REACHED`) | `GiftService` |
| Max pets in room | **10** | `ChatRoomItemSelectorView` |
| Club creation VIP / regular | **1 / 0** | `ClubAMFService` |
| Photo upload | limited (`PICTURE_UPLOAD_LIMIT_REACHED`) | `PictureUploadUtils` |

### AMF HTTP errors (transport layer)

Source: `AmfListener.as`

| HTTP code | Constant | Behavior |
|-----------|----------|----------|
| `400` | `HTTP_ERROR_BAD_REQUEST` | No retry |
| `401` | `HTTP_ERROR_UNAUTHORIZED` | Nebula token refresh or fail |
| `427` | `HTTP_ERROR_EXPIRED_REFRESH_TOKEN` | Token renewal (`GetNebulaAccessTokenCommand`) |
| `429` | `HTTP_ERROR_TOO_MANY_REQUEST` | Too many requests popup |
| `500` | `HTTP_ERROR_INTERNAL_SERVER` | No retry |
| `501` | `HTTP_ERROR_NOT_IMPLEMENTED` | No retry |
| `505` | `HTTP_ERROR_VERSION_NOT_SUPPORTED` | No retry |

On retryable error: new `TicketHeader` generated (`generateAndAddNewTicketMarking`), queue cleared of `LOW_IMPORTANCE` calls.

---

## Network security & anti-tampering (Charles / proxy)

> The Flash client **does not mention Charles Proxy** explicitly. The mechanisms below protect AMF call integrity and detect modified environments. Intercepting traffic with a MITM proxy typically breaks the **response checksum** when app level ≥ 3.

### 1. Request checksum (client → server)

Source: `AmfCall.execute()`, `ChecksumCalculator.as`

- Every AMF call (except ignored functions) sends persistent header **`id`** = SHA1 of serialized args + obfuscated salt.
- Partial salt: `"Yd*xX#o@B15i@!th"` + dynamic character permutation.
- If `TicketHeader` in args: extracts `ticketPrefix + last 5 chars` for hash.
- Fallback without ticket: `"XSV7%!5!AX2L8@vn"`.

**Functions without request checksum** (`ignoredFunctions` list):

| Ignored full service path |
|---------------------------|
| `AMFLoggingService.LogClient` |
| `AMFAppSettingsService(Get/Mobile).GetAppSettings` |
| `AMFSessionServiceForMobile.CheckClientFreshness` |
| `AMFPaymentService.GetCurrentPaymentPossibilities` |
| `AMFLookService.GetRandomLookByLikes` |
| `AMFNebulaService.GetProfileIds` |
| `AMFOs.CreateOsRef` / `RunOsCheck` |
| `AMFUserSessionService.EmailValidated` |

### 2. Response checksum (server → client)

Source: `AmfCall.validateChecksum()`, `FluorineNetConnection.hashContent()`

- Server returns checksum via `serverChecksum` on connection.
- Client recalculates SHA1(`[TicketHeader, responseObject]`) and compares.
- App level (`AmfCallExternalCommands`, set by `AppSettings.AWS_HEX_VALUE`):

| Level | Behavior |
|-------|----------|
| **1** | Response checksum **disabled** |
| **2** | Validated but **non-blocking** on mismatch |
| **3+** | **Blocking** — call fails + log `[AMF ResponseChecksum Enforced]` |
| **4** | Blocking + silent fail log |

Debug flag: `AmfCall.isIgnoringChecksum = true` bypasses validation.

> **Charles Proxy impact**: modifying an AMF response body without recalculating server checksum → failure at level ≥ 3. Replaying requests requires valid `TicketHeader` with Nebula token + incremental marking ID.

### 3. Auth ticket (`TicketHeader`)

Source: `TicketGenerator.as`

Sensitive calls include a `TicketHeader`:

```
Ticket = [optional MD5 prefix_] + sessionTicket + markingId
anyAttribute.Token = Nebula access token
anyAttribute.DeviceId = persistent device ID
```

- `markingId`: global incrementing counter + double MD5/hex hash — **regenerated on every retry**.
- `sessionID`: random Base64 AMF header (46 hex chars) on all requests.
- Expired token → refresh via `SharedObjectUtil.refreshNebulaAccessToken` then single retry.

### 4. OS Check / environment alignment (`SnapLoader`)

Source: `SnapLoader.as`, `AMFOs` service

Environment anti-fraud (often timezone-related):

1. `CreateOsRef` → receives `TjData` + `RefId`
2. Deserializes actor snapshot, computes histogram (`SnapshotStats`)
3. `RunOsCheck(refId, histogram)` → must return a `String` (new refId)

- Enabled via `AppSettings.ACTIVATE_TIMEZONE_ALIGNMENT` (`WEB`, `MOB`, `WEB:E`, `MOB:E`)
- `:E` mode → blocking failure (`ignoreFail = false`)
- Forced retry every **120 s** if no success

### 5. Non-pausable calls

`CreateOsRef` and `RunOsCheck` are **not paused** when the AMF queue is paused (`AmfCaller.unPausable`).

### 6. Moderation & logging

| Mechanism | Endpoint / usage |
|-----------|------------------|
| Chat log | `LogChat`, `LogInput` (`AMFCommonService`) |
| Text moderation | `SetMoodWithModerationCall`, `TextModerationHandler` |
| User behavior | Separate service with dedicated host + active response checksum |

---

## Response codes (all systems)

### Bonsters / pets — `BonsterInteractionResponse`

| Code | Meaning |
|------|---------|
| `0` | Success |
| `−1` | Server exception |
| `−2` | Not VIP |
| `−3` | Not enough SC |
| `−4` | Not enough diamonds |
| `−5` | Pet sick |
| `−429` | Rate limited (via `RateLimiterController`) |

### Diamond shop — `SpendingProvider`

| Code | Meaning |
|------|---------|
| `0` | Success |
| `−1` | Exception |
| `−2` | Not enough diamonds |
| `−3` | Already bought today |

### Design Studio — `DesignerContentService`

| Code | Meaning |
|------|---------|
| `0` | Success |
| `−1` | Exception |
| `−2` | Not VIP |
| `−3` | Not enough SC |
| `−4` | Not enough diamonds |

### Gifts — `GiftService`

| Code | Meaning |
|------|---------|
| `0` | OK |
| `−1` | General error |
| `−10` | Non-VIP level 6 required |
| `−20` | Daily limit reached |
| `−30` | Already owns item |
| `−40` | Too early (cooldown) |

### Gift certificates — `ServiceResultDataOfListOfCertificateGift`

| Code | Meaning |
|------|---------|
| `5` | Success |
| `6` | Already used |
| `9` | Invalidated |
| `200` | Pending success |
| `−1` | Unknown |

### Forum — `NewTopic`

| Code | Meaning |
|------|---------|
| `0` | Success |
| `1` | Error |
| `2` | Topic chain (moderation) |

### Photo upload — `UploadAvailabilityVO`

| Code | Meaning |
|------|---------|
| `0` | Available |
| `1` | Unavailable (limit / VIP) |

### Clubs — ad hoc responses

| Code | Meaning |
|------|---------|
| `4` | Too many memberships (`RESPONSE_TOO_MANY_MEMBERSHIPS`) |
| `−1` | Too many clubs created (`RESPONSE_TOO_MANY_CREATED_CLUBS`) |

### Redeem codes — `RedeemModelEvent`

| Constant | Meaning |
|----------|---------|
| `ERROR_CODE_TOO_MANY_ATTEMPTS` | Too many attempts |

---

## Pet AMF endpoints

Bonster service: `MovieStarPlanet.WebService.Bonster.AMFBonsterService`

| Method | Parameters | Description |
|--------|------------|-------------|
| `FeedBonster` | relId, foodId, actorId | Feed |
| `WashBonster` | relId, washPoints, actorId | Wash |
| `PlayWithBonster` | relId, playPoints, actorId | Play |
| `PetFriendBonster` | actorId, relId | Pet (friend) |
| `HatchBonster` | relId, actorId | Hatch |
| `InstantEvolveBonster` | actorId, relId | Instant evolve (booster) |
| `RenameBonster` | relId, name, actorId | Rename |
| `DeleteBonsterName` | relId | Delete moderated name |
| `GetBonsterCandyPrices` | — | Candy prices per level |
| `GetBonsterListByActor` | actorId, flag | Pet list |
| `GetBonsterAnimations` | — | Animations |
| `CheckInBonsterAtPetHotel` | relId, stayPeriod, actorId | Hotel check-in |
| `CheckOutBonsterFromPetHotel` | relId, actorId | Hotel check-out |
| `BuyBonster` | actorId, bonsterId | Shop purchase |

Legacy pet service: `PetAMFService` — `PetFriendPet`, `WashPet`, `CheckInPetHotel`, `CheckOutPetHotel`, `HarvestPlant`, etc.

---

## AMF reference — services, endpoints & parameters

**74 services · 846 endpoints** — parameters as sent by the Flash client via `callFunction(...)`.

### Auth, session & compte

#### `WebService.AMFActorService`

AMF path : `MovieStarPlanet.WebService.AMFActorService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BlockActor` | param1, param2 |  |
| `BlockActorNeb` | param1, param2 |  |
| `BulkLoadActors` | param1 |  |
| `BuyClothesNew` | param1, param2 |  |
| `CreateNewUserWithSecureSnapshotV2` | newActorCreationData, checksum, store, deviceId, snapshotSmall, snapshotBig |  |
| `GetActorIdByName` | param1 |  |
| `GetActorZooItems` | param1 |  |
| `GetClothesFromNewestClothesSection` | param1, param2, param3 |  |
| `GetPagedClothByCategoryGroups` | param1, _loc5_ |  |
| `GetPagedClothByCategoryGroups_14` | param1, _loc5_ |  |
| `GetPostLoginBundle` | param1 |  |
| `IsActorNameUsed` | param1 |  |
| `IsNameBlocked` | param1 |  |
| `LoadActorDetails` | param1, param2 |  |
| `LoadActorDetailsExtended` | param1 |  |
| `LoadActorItems` | param1 |  |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 |  |
| `LoadActorWithCurrentClothesBasicDataOnlyRevised` | param1 |  |
| `LoadActorsVipDetails` | param1 |  |
| `LoadBlockedAndBlockingActors` | param1 |  |
| `LoadBlockedAndBlockingActorsNeb` | param1 |  |
| `LoadDataForRegisterNewUser` | — |  |
| `LoadModeratorInformation` | param1 |  |
| `LoadMood` | param1 |  |
| `LoadMovieStarListRevised` | param1 |  |
| `LockOutUser` | param1, param2, param3, param4, param5 |  |
| `LoginMobile` | userId, redirectToken, version, store, deviceId |  |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `PickupGuidePresent` | actorId, type, index |  |
| `ReportActor` | param1 |  |
| `ReportTabletAndroidConversion` | param1, param2 |  |
| `ReportTabletIOSConversion` | param1, param2 |  |
| `RequestMobileStartupReward` | param1 |  |
| `SaveAlertWordsCount` | param1, param2 |  |
| `SaveBirthInfoWithTicket` | param1, param2, param3 |  |
| `SearchActorByNameNeb` | param1, param2 |  |
| `SearchActorByNameWithRequestStatus` | param1, param2 |  |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 |  |
| `SubmitMobileStartupReward` | param1, param2, param3 |  |
| `ThirdPartyLoginDesktopV2` | param1, param2, param3, param4, param5 |  |
| `ThirdPartyLoginMobileV2` | nacd, snapshotBig, snapshotSmall, username, password, version, store, deviceId |  |
| `UnblockActor` | param1, param2 |  |
| `UnblockActorNeb` | param1, param2 |  |
| `UpdateClothes` | param1, param2 |  |
| `ValidateCaptcha` | param1, param2 |  |
| `fameOverhaul` | param1 |  |
| `loginMobileV2` | userName, password, version, store, deviceId, dfp |  |

#### `WebService.AMFUserService`

AMF path : `MovieStarPlanet.WebService.AMFUserService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `LogInput` | param1, param2, param3, param5, param4 |  |
| `LogInputGroupChat` | param1, param2, param3, param5, param4 |  |
| `LogInputWithConditionalModerationCall` | param1, param2, param3, param4, param5, param6 |  |

#### `WebService.ActorService.AMFActorServiceForWeb`

AMF path : `MovieStarPlanet.WebService.ActorService.AMFActorServiceForWeb`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BlockActor` | param1, param2 |  |
| `BlockActorNeb` | param1, param2 |  |
| `BlockedActors` | param1 |  |
| `ClaimAllLevelUpGifts` | param1, param2 |  |
| `ClaimSingleLevelUpGift` | param1, param2, param3 |  |
| `GetActorAddress` | actorId |  |
| `GetLevelUpGiftChoices` | actorId |  |
| `GetLevelUpGiftSelects` | actorId |  |
| `GetLevelUps` | — |  |
| `GetPostLoginBundle` | param1 |  |
| `GetPostLoginBundleStandalone` | param1 |  |
| `IsActorNameUsed` | param1 |  |
| `IsNameBlocked` | param1 |  |
| `LoadActorDetails` | param1, param2 |  |
| `LoadActorDetailsExtended` | param1 |  |
| `LoadBlockedAndBlockingActors` | param1 |  |
| `LoadBlockedAndBlockingActorsNeb` | param1 |  |
| `LoadModeratorInformation` | param1 |  |
| `LoadMood` | param1 |  |
| `ModerationSearchActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `ModerationSearchActorId` | actorId |  |
| `ModerationSearchMassDeleteActorByName` | params.searchString, pageIndex, pageSize + 1 |  |
| `PickupGuidePresent` | actorId, type, index |  |
| `PurchaseRecoloring` | param1, param2, param3, param4, param5 |  |
| `ReportActor` | param1 |  |
| `SaveActorAddress` | param1 |  |
| `SaveActorSoundMuted` | param1, param2 |  |
| `SaveBirthInfoWithTicket` | param1, param2, param3 |  |
| `SaveLevelUpGiftSelect` | param1, param2, param3 |  |
| `SearchActorByNameNeb` | param1, param2 |  |
| `SetColorOnActorItemNew` | param1, param2, param3, param4, param5 |  |
| `SetMoodWithModerationCall` | param1, param2, param3, param4 |  |
| `UnblockActor` | param1, param2 |  |
| `UnblockActorNeb` | param1, param2 |  |
| `ValidateCaptcha` | param1, param2 |  |
| `fameOverhaul` | param1 |  |
| `getWallActivitiesForActor` | pagingOptions.actorId, pagingOptions.activityType, pagingOptions.pageIndex, pagingOptions.pageSize |  |

#### `WebService.AppSettings.AMFAppSettingsService`

AMF path : `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetAppSetting` | param1 |  |
| `GetAppSettings` | param1 |  |

#### `WebService.AppSettings.AMFAppSettingsServiceMobile`

AMF path : `MovieStarPlanet.WebService.AppSettings.AMFAppSettingsServiceMobile`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetAppSetting` | param1 |  |
| `GetAppSettings` | param1 |  |

#### `WebService.Nebula.AMFNebulaService`

AMF path : `MovieStarPlanet.WebService.Nebula.AMFNebulaService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetProfileId` | param1 |  |
| `GetProfileIds` | missing |  |
| `GetProfiles` | param1 |  |

#### `WebService.ParentalConsent.AMFParentalConsentService`

AMF path : `MovieStarPlanet.WebService.ParentalConsent.AMFParentalConsentService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetActorParentalConsent` | param1 |  |
| `GetUserType` | param1 |  |
| `GrantParentalConsent` | param1, param2 |  |
| `HasVisibleParentalConsentCode` | param1 |  |
| `HideParentalConsentCode` | param1 |  |
| `MatchActorIdToParentalConsentConfirmCode` | param1, param2 |  |
| `ReSendParentalConsentCode` | param1 |  |
| `RememberParentalConsentCode` | param1 |  |
| `RequestParentalConsent` | param1 |  |
| `SaveParentEmailAddress` | param1, param2 |  |
| `SetActorsParentalConsent` | param1, param2 |  |

#### `WebService.Payment.AMFPaymentService`

AMF path : `MovieStarPlanet.WebService.Payment.AMFPaymentService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `DisableAutomaticRenewal` | param1 |  |
| `GetAvailablePurchaseTypes` | actorId |  |
| `GetBokuBuyUrlNew` | param1, param2, param3, param4, param5 |  |
| `GetBokuPricePoints` | — |  |
| `GetCurrentPaymentPossibilities` | types |  |
| `GetRecurringPaymentSubscription` | param1 |  |
| `GetTimeLimitedPurchaseType` | actorId |  |
| `GetTransactionPurchaseInfo` | param1, param2 |  |
| `GetTransactionPurchaseInfoWeb` | param1, param2 |  |
| `GetTransactionPurchaseList` | param1, param2, param3 |  |
| `GetTransactionPurchaseListIncludingManual` | param1, param2, param3 |  |
| `VerifyBokuTransaction` | param1 |  |

#### `WebService.User.AMFUserServiceWeb`

AMF path : `MovieStarPlanet.WebService.User.AMFUserServiceWeb`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CommentEntity` | entityComment |  |
| `CreateNewUserWithSecureSnapshotV2` | param1, param2, null, param3, param4 |  |
| `EntityCommentDelete` | param1, param2 |  |
| `GetActorPersonalInfo` | param1, "" |  |
| `GetEntityComments` | entityType, entityId, pageIndex, pageSize |  |
| `IsCommunicationAllowedWith` | communicationType, actorid |  |
| `IsCommunicationAllowedWithNeb` | communicationType, profileId |  |
| `LogInput` | locationId, actorId, roomInstanceId, message, destinationType |  |
| `LogInputGroupChat` | locationId, actorId, roomInstanceId, message, destinationType |  |
| `LogInputWithConditionalModerationCall` | locationId, actorId, roomInstanceId, message, destinationType, isUserRestricted |  |
| `Login` | userName, password, null, null, deviceId, dfp |  |
| `LoginModeratorV2` | username, password, userIps, otp, null, null |  |
| `LoginV2` | variante 1: param1, param2, null, null, null, null<br>variante 2: username, password, userIps, null, null, browserFingerprint<br>variante 3: username, password, userIps, null, null, null | 3 variants |
| `SaveChatAllowed` | param1, param2 |  |
| `UpdateActorPersonalInfo` | param1, param2 |  |

#### `WebService.UserSession.AMFUserSessionService`

AMF path : `MovieStarPlanet.WebService.UserSession.AMFUserSessionService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AwardStartupReward` | param1 |  |
| `BadWordCountAdd` | param1, param2 |  |
| `BadWordCountClear` | param1 |  |
| `ChangePasswordNew` | param1, param2, param3 |  |
| `DeleteUser` | param1, param2, param3 |  |
| `EmailChanged` | actorId, mail, username, password, emailSettings |  |
| `EmailValidated` | actorId |  |
| `EmailValidatedCancel` | param1 |  |
| `GetActorEmail` | actorId |  |
| `GetActorIdFromName` | name |  |
| `GetActorNameFromId` | actorId |  |
| `GetMarketingStepGift` | param1 |  |
| `GiveAutographAndCalculateTimestamp` | actorId, receiverId |  |
| `GiveAutographAndCalculateTimestampNeb` | actorId, receiverProfileId |  |
| `LoadActorDetails2` | actorId, updateProfileDisplayCount, callerId |  |
| `LoadActorDetailsExtended` | actorId |  |
| `LoadActorDetailsVersion` | actorId, updateProfileDisplayCount |  |
| `MassDeleteUsers` | usersIdsTobeDeleted, userName, password |  |
| `RecoverUserFromEmailHistory` | actorName, email |  |
| `RenameUser` | actorId, newActorName, moderatorName, moderatorPass |  |
| `ResyncLogin` | actorId |  |
| `SendEmailValidation` | param1, param2, param3, param4, param5 |  |
| `SendNewEmailValidation` | param1, param2, param3, param4, param5, param6 |  |
| `SendUserParentEmailValidation` | param1, param2, param3, param4, param5, param6 |  |
| `SetEmailSettings` | actorId, actorName, emailSettings |  |
| `SetFacebookId` | param1, param2 |  |
| `SetMarketingStep` | param1, param2, param3 |  |
| `UndeleteUser` | userIdTobeDeleted, userName, password |  |
| `UpdateBehaviourStatusNew` | actorId, behaviourStatus, lockedText, chatLogId, handledByActorId |  |
| `UpdateGift` | actorId |  |
| `UpdateMySchool` | actorId, passwordHash, schoolId, schoolYear |  |
| `UpdateRetention` | actorId |  |
| `deleteBioText` | actorId, moderatorName, moderatorPass |  |
| `eraseEmail` | email, moderatorName, moderatorPass |  |

#### `WebService.UserSession.AMFUserSessionServiceForMobile`

AMF path : `MovieStarPlanet.WebService.UserSession.AMFUserSessionServiceForMobile`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `UpdateGift` | actorId |  |

### Avatar & vêtements (MovieStar)

#### `WebService.BeautyClinic.AMFBeautyClinicService`

AMF path : `MovieStarPlanet.WebService.BeautyClinic.AMFBeautyClinicService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BuyBeautyClinicItems` | actorId, eyeId, eyeShadowId, noseId, mouthId, eyeColors, eyeShadowColors, mouthColors, skinColor, removeEyeShadow |  |
| `BuyManyBeautyClinicItems` | actorId, itemsArray |  |
| `GetMyBeautyClinicItems` | actorId |  |
| `GetMyBeautyClinicItemsWithHiddenOption` | actorId, includeHidden |  |
| `LoadDataForBeautyClinic` | — |  |
| `LoadModeratorDataForBeautyClinic` | — |  |
| `WearItems` | actorId, inventoryIdArray |  |

#### `WebService.MovieStar.AMFMovieStarService`

AMF path : `MovieStarPlanet.WebService.MovieStar.AMFMovieStarService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetActorClothesRel` | relId |  |
| `GetActorClothesRelList` | rels |  |
| `GetContextClothes` | actorId, contextId |  |
| `LoadActorBonstersPaged` | actorId, pageIndex, pageSize |  |
| `LoadActorWithCurrentClothesAndSpritesheet` | param1 |  |
| `LoadClothes` | skinId, shopId |  |
| `LoadClothesByIds` | clothesIds |  |
| `LoadClothesFromThemeId` | themeId |  |
| `LoadClothesWithThemeByIds` | clothesIds |  |
| `LoadDataForRegisterNewUser` | — |  |
| `LoadFaceParts` | — |  |
| `LoadMovieStarFlatMinimum` | actorId |  |
| `LoadMovieStarFlatRevised` | actorId |  |
| `LoadMovieStarListRevised` | actorIds |  |
| `LoadMovieStarRevised` | actorId |  |
| `LoadPagedActorClothes` | param1, param2, param3 |  |
| `LoadPagedActorGiftableClothes` | param1, param2, param3 |  |
| `LoadPagedActorGiftableItems` | param1, param2, param3 |  |
| `LoadPagedActorItems` | actorId, pageIndex, pageSize |  |
| `LoadRoomItems` | actorId |  |
| `UpdateClothes` | actorId, actorClothesRelIds |  |
| `getRandomClothesByType` | slotType, isFemale, amount |  |

### Looks (tenues)

#### `WebService.Looks.AMFLookService`

AMF path : `MovieStarPlanet.WebService.Looks.AMFLookService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CanWearOwnLook` | param1, param2 |  |
| `GetLookById` | variante 1: lookId<br>variante 2: lookId, this.actorModel.actorId | 2 variants |
| `GetLooksByOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksCreatedBy` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksForActor` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksForOthers` | actorId, this.actorModel.actorId, orderBy, pageIndex, pageSize |  |
| `GetLooksLatest` | pageIndex, pageSize |  |
| `GetLooksLatestByFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksLatestByMeAndFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksLikedByMe` | actorId, pageIndex, pageSize |  |
| `GetLooksTopAll` | pageIndex, pageSize |  |
| `GetLooksTopByFriends` | actorId, pageIndex, pageSize |  |
| `GetLooksTopByMeAndFriends` | actorId, pageIndex, pageSize |  |
| `GetRandomLookByLikes` | poolSize |  |
| `LookDelete` | lookId, this.actorModel.actorId |  |
| `SaveLookAndData` | look, clotheIds, lookSnapshot, fullSizeSnapshot |  |
| `SaveSmallLookSnapshot` | look, lookSnapshot |  |

### Boutique & dépenses

#### `WebService.Shopping.AMFShopContentService`

AMF path : `MovieStarPlanet.WebService.Shopping.AMFShopContentService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AddTag` | param1, param2 |  |
| `AddTheme` | param1, param2 |  |
| `BuyItems` | param1, ActorSession.loggedInActor.actorId |  |
| `GetPage` | pageIndex, pageSize, params.shopId, params.genderId, params.themeId, params.categoryId, params.tagToUse, params.vipToUse, params.currencyToUse, params.search |  |
| `RemoveTag` | param1, param2 |  |
| `RemoveTheme` | param1, param2 |  |
| `SetShopIds` | param1, param2 |  |

#### `WebService.Spending.AMFSpendingService`

AMF path : `MovieStarPlanet.WebService.Spending.AMFSpendingService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BuyAnimation` | param1, param2 |  |
| `BuyBackground` | param1, param2 |  |
| `BuyChangePet` | param1, param2, param3, param4 |  |
| `BuyCharacterPopUp` | param1 |  |
| `BuyClothes` | param1, param2, param3 |  |
| `BuyDiamondCharacterEffect` | param1 |  |
| `BuyDiamondTwit` | param1 |  |
| `BuyEmoticonPackage` | param1, param2 |  |
| `BuyFameBooster` | param1 |  |
| `BuyFameWheelSpin` | param1 |  |
| `BuyInstantPetGrow` | param1, param2 |  |
| `BuyMusic` | param1, param2 |  |
| `BuyShoppingSpree` | param1 |  |
| `BuySpecialGreeting` | actorId, friendId, greetingTypeId |  |
| `BuyStarcoinShooter` | param1 |  |
| `BuyStarcoinsWheelSpin` | param1 |  |
| `ClaimFreeDownloadableFameWheelSpin` | param1 |  |
| `GetActiveSpecialsItems` | param1 |  |
| `GetEmoticonPackages` | param1 |  |
| `GetGreetingIndices` | param1 |  |
| `GetPagedShopSpecials` | param1, param2, param3 |  |
| `GetSpecialsGreetingItem` | param1, param2 |  |
| `GetSpecialsItemPrice` | param1, param2 |  |
| `IsValidSpecialGreeting` | param1, param2 |  |

### Salles & chambres

#### `WebService.AMFRoomServiceForMobile`

AMF path : `MovieStarPlanet.WebService.AMFRoomServiceForMobile`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetActorBonsterList` | param1, param2 |  |
| `GetActorClickItemList` | param1, param2 |  |
| `GetActorClothesByShopId` | param1, param2, param3 |  |
| `GetWallpapers` | param1, param2 |  |
| `LoadHouse` | houseId, callingActorId |  |
| `LoadHouseAndSpecificRoom` | callingActorId, houseId, roomId |  |
| `LoveRoom` | param1, param2 |  |
| `SaveRoomWithSnapshot` | data, roomSnapshotProfile, roomSnapshotMedium, roomSnapshotSmall |  |

#### `WebService.Room.AMFRoomService`

AMF path : `MovieStarPlanet.WebService.Room.AMFRoomService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetActorBonsterList` | param1, param2 |  |
| `GetActorClickItemList` | param1, param2 |  |
| `GetActorClothesByShopId` | param1, param2, param3 |  |
| `GetWallpapers` | param1, param2 |  |

### Pets & Bonsters

#### `WebService.AMFMobilePetService`

AMF path : `MovieStarPlanet.WebService.AMFMobilePetService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CurePet` | param1 |  |
| `FeedPet` | param1, param2 |  |
| `GetActorClickItem` | param1 |  |
| `GetClickItems` | — |  |
| `GetClickItemsForActor` | param1 |  |
| `HatchPet` | param1, param2 |  |
| `PetFriendPet` | param1, param2 |  |
| `PurchaseClickItem` | param1, param2 |  |
| `SavePetName` | param1, param2 |  |
| `WashPet` | param1, param2 |  |

#### `WebService.Bonster.AMFBonsterService`

AMF path : `MovieStarPlanet.WebService.Bonster.AMFBonsterService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AnimationUsed` | actorBonsterRelId, animationId, actorId |  |
| `CheckInBonsterAtPetHotel` | actorBonsterRelId, bookTimeAmount, actorId |  |
| `CheckOutBonsterFromPetHotel` | actorBonsterRelId, actorId |  |
| `DeleteBonsterName` | actorBonsterRelId |  |
| `FeedBonster` | actorBonsterRelId, foodId, actorId |  |
| `GetBonsterAnimations` | param1, param2 |  |
| `GetBonsterById` | actorBonsterRelId |  |
| `GetBonsterCandyPrices` | — |  |
| `GetBonsterListByActor` | actorId, loadAnimations, excludeHotel |  |
| `GetBonsterTemplateList` | — |  |
| `HatchBonster` | actorBonsterRelId, actorId |  |
| `InstantEvolveBonster` | actorId, actorBonsterRelId |  |
| `PetFriendBonster` | actorId, actorBonsterRelId |  |
| `PlayWithBonster` | actorBonsterRelId, playPoints, actorId |  |
| `RenameBonster` | actorBonsterRelId, name, actorId |  |
| `SaveNewAndOldPetsPositionsInMyRoom` | actorId, bonsterPositionsList, clickItemsList |  |
| `WashBonster` | actorBonsterRelId, washPoints, actorId |  |

#### `WebService.Bonster.AMFBonsterShopService`

AMF path : `MovieStarPlanet.WebService.Bonster.AMFBonsterShopService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BuyBonster` | actorId, bonsterId |  |
| `GetCampaignBonster` | — |  |
| `GetListOfAllBonstersAndBoonies` | — |  |
| `GetListOfBonsters` | — |  |
| `GetListOfBoonies` | — |  |
| `GetPagedListOfBonsters` | pageId, pageSize |  |
| `GetPagedListOfBoonies` | pageId, pageSize |  |
| `GetPagedListOfFriendsPets` | pageId, pageSize |  |
| `GetPagedListOfNewPets` | pageId, pageSize |  |
| `GetPagedListOfTopPets` | pageId, pageSize |  |

#### `WebService.Pets.AMFPetService`

AMF path : `MovieStarPlanet.WebService.Pets.AMFPetService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BuyClickItem` | actorId, clickItemId |  |
| `CheckInPetHotel` | actorId, clickItemRelId, stayPeriod |  |
| `CheckOutPetHotel` | actorId, clickItemRelId |  |
| `CurePet` | actorClickItemRelId |  |
| `DeletePetName` | clickItemId, moderatorName, moderatorPass |  |
| `FeedPet` | actorClickItemRelId, foodPoints |  |
| `GetActorClickItem` | actorClickItemRelId |  |
| `GetClickItems` | — |  |
| `GetClickItemsForActor` | variante 1: actorid<br>variante 2: param1 | 2 variants |
| `GetClickItemsForActorThatCanStillGrow` | actorid |  |
| `GetClickItemsForActorWithPrice` | actorid |  |
| `GetClickItemsForPetHotel` | actorId |  |
| `HarvestPlant` | actorId, actorClickItemRelId |  |
| `HatchPet` | actorClickItemRelId, configuration |  |
| `PetFriendPet` | actorId, actorClickItemRelId |  |
| `PlayedPetGame` | actorClickItemRelId, playPoints |  |
| `SaveClickItemLocations` | locations |  |
| `SavePetName` | actorClickItemRelId, name |  |
| `WashPet` | actorId, actorClickItemRelId |  |

### Films & favoris mobile

#### `MobileServices.AMFFavs`

AMF path : `MovieStarPlanet.MobileServices.AMFFavs`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AddActorFav` | param1, param2 |  |
| `GetActorMovieFavs` | param1, param2 |  |
| `RemoveActorFav` | param1, param2 |  |

#### `MobileServices.AMFMovieService`

AMF path : `MovieStarPlanet.MobileServices.AMFMovieService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CreateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `DeleteMovie` | param1, param2 |  |
| `GetMovie` | movieId |  |
| `GetUnifiedMoviesByFriendsStarringMe` | param1, param2 |  |
| `GetUnifiedMoviesByMePrivate` | param1, param2 |  |
| `GetUnifiedMoviesLatestByAll` | param1, param2 |  |
| `GetUnifiedMoviesLatestByFriends` | param1, param2 |  |
| `GetUnifiedMoviesMinePublic` | param1, param2 |  |
| `GetUnifiedMoviesTopAll` | param1, param2 |  |
| `GetUnifiedMoviesTopByMeAndFriends` | param1, param2 |  |
| `MovieWatched` | movieId |  |
| `RateMovie` | param1, param2 |  |
| `UpdateMovieWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8, param9 |  |

#### `WebService.Favourites.AMFFavs`

AMF path : `MovieStarPlanet.WebService.Favourites.AMFFavs`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AddActorFav` | actorId, entityType, entityId |  |
| `GetActorMovieFavs` | actorId, byRating, pageIndex, pageSize |  |
| `RemoveActorFav` | actorId, entityType, entityId |  |

#### `WebService.MovieService.AMFMovieService`

AMF path : `MovieStarPlanet.WebService.MovieService.AMFMovieService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CommentMovie` | rateMovie |  |
| `DeleteMovie` | movieId, actorId |  |
| `DeleteMovieComment` | movieId, commentId |  |
| `GetActorMovieCount` | actorId |  |
| `GetAutoSavedMovieId` | actorId |  |
| `GetMovieByGuid` | movieGuid |  |
| `GetMovieById` | movieId |  |
| `GetMovieListForActor` | pagingOptions.params.actorId, pagingOptions.params.type, pagingOptions.pageIndex, pagingOptions.pageSize |  |
| `GetMovieRatings` | movie.MovieId, pageIndex, pageSize |  |
| `MovieWatched` | movieId, actorId |  |
| `PublishMovie` | movieId |  |
| `RateMovie` | rateMovie |  |
| `SaveMovieWithSnapshot` | movie, snapshotSmall, snapshotBig |  |
| `SearchMovie` | searchString, pageIndex, pageSize |  |
| `SendMovieAsMail` | movieId, toAddress |  |

### Vidéo / YouTube

#### `WebService.Video.AMFVideoService`

AMF path : `MovieStarPlanet.WebService.Video.AMFVideoService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AddVideoToMspTv` | param1, param2, param3, param4, param5 |  |
| `AutoSaveVideoFromFeed` | param1, param2, param3, param4, param5, _loc9_ |  |
| `CreateBlankPlaylist` | param1, param2 |  |
| `DeleteExternalVideoPlaylistRel` | param1, param2, param3 |  |
| `DeletePlaylist` | param1, param2, param3 |  |
| `GetCategoryExternalVideosForPlayback` | param1, param2 |  |
| `GetExternalVideoForChatRoom` | param1 |  |
| `GetMspTvExternalVideosForPlayback` | param1 |  |
| `GetMyPlaylistsForVideo` | param1 |  |
| `GetPagedBlockedExternalVideos` | param1, param2, param3, param4 |  |
| `GetPagedCategoryExternalVideos` | param1, param2, param3 |  |
| `GetPagedExternalVideos` | param1, param2, param3 |  |
| `GetPagedMspTvExternalVideos` | param1, param2 |  |
| `GetPagedNewestExternalVideos` | param1, param2 |  |
| `GetPagedPlaylists` | param1, param2, param3, param4 |  |
| `GetPagedPlaylistsBySearch` | param1, param2, param3, param4 |  |
| `GetPagedVideoListObjects` | param1, param2, param3 |  |
| `GetPagedVideoListObjectsByAddTime` | variante 1: actorId, 0, 50<br>variante 2: param1, param2, param3 | 2 variants |
| `GetPlaylist` | param1, param2 |  |
| `GetPlaylistForPlayback` | param1, param2, param3 |  |
| `GetPlaylistsForDropdown` | param1 |  |
| `GetTopExternalVideosForPlayback` | param1 |  |
| `GetYouTubeVideo` | param1, param2 |  |
| `GetYouTubeVideoInfo` | param1 |  |
| `IncrementReportCount` | param1 |  |
| `IncrementViewsExternalVideo` | param1 |  |
| `LikePlaylist` | param1, param2, param3 |  |
| `LikeYouTube` | param1, param2 |  |
| `MoveVideoInPlaylist` | param1, param2, param3, param4, param5 |  |
| `RenamePlaylist` | param1, param2, param3 |  |
| `ReportErrorOnVideo` | param1 |  |
| `SaveToNewPlaylist` | param1, param2, param3, param4, param5 |  |
| `SaveToPlaylist` | param1, param2, param3, param4 |  |
| `YouTubeBlock` | param1, param2, param3, param4 |  |
| `YouTubePopulateViewsAndLikes` | param1, param2 |  |

### Social (amis, profil, messagerie)

#### `WebService.AMFMessageService`

AMF path : `MovieStarPlanet.WebService.AMFMessageService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetMessagingActors` | variante 1: [id<br>variante 2: param1 | 2 variants |
| `IsCommunicationAllowedWith` | param1, param2 |  |
| `SendChatMessageWithModerationCall` | param1, param2, param3, param4, param5, param6 |  |
| `SendOneToOneOrGroupChatMessage` | Number(param2), param8, param3, param6, _loc13_, param4 |  |
| `SetMessengerSession` | param1 |  |

#### `WebService.AMFMobileFriendshipService`

AMF path : `MovieStarPlanet.WebService.AMFMobileFriendshipService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AcceptBoyfriend` | param1, param2, param3 |  |
| `AcceptMySpecialFriend` | param1 |  |
| `ApproveDefaultAnchorFriendship` | param1 |  |
| `ApproveFriendship` | param1, param2 |  |
| `ApproveFriendshipNeb` | param1, param2 |  |
| `AskToBeBoyFriend` | param1, param2, param3 |  |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 |  |
| `AskToBeMySpecialFriend` | param1 |  |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 |  |
| `BreakUp` | param1, param2, param3 |  |
| `DeleteFriendship` | param1, param2 |  |
| `DeleteFriendshipNeb` | param1, param2 |  |
| `GetActorSpecialSummary` | param1, param2 |  |
| `GetFriendListWithNameAndScore` | param1 |  |
| `GetMspRelationshipStatus` | param3, param1, param4 |  |
| `GetPagedFriendRequests` | actorId, pageIndex, pageSize |  |
| `GetRelationshipStatusNeb` | param2, param3, param4 |  |
| `RejectBoyfriend` | param1, param2, param3 |  |
| `RejectFriendShip` | param1, param2 |  |
| `RejectFriendShipNeb` | param1, param2 |  |
| `RejectMySpecialFriend` | param1 |  |
| `RequestFriendship` | param1, param2 |  |
| `RequestFriendshipFromSchoolmate` | param1, param2 |  |
| `RequestFriendshipNeb` | param1, param2 |  |

#### `WebService.AnchorCharacter.AMFAnchorCharacterService`

AMF path : `MovieStarPlanet.WebService.AnchorCharacter.AMFAnchorCharacterService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AcceptFriendship` | anchorCharacterId |  |
| `AcceptGifts` | anchorCharacterId |  |
| `CancelFriendship` | anchorCharacterId |  |
| `GetAnchorCharacterList` | — |  |
| `RequestFriendship` | anchorCharacterId |  |
| `UpdateLastInviteSent` | param1, param2 |  |
| `UpdateLastStatusSeen` | param1 |  |

#### `WebService.Friendships.AMFFriendshipService`

AMF path : `MovieStarPlanet.WebService.Friendships.AMFFriendshipService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AcceptBoyfriend` | param1, param2, param3 |  |
| `AcceptMySpecialFriend` | param1 |  |
| `ApproveDefaultAnchorFriendship` | param1 |  |
| `ApproveFriendship` | param1, param2 |  |
| `ApproveFriendshipNeb` | param1, param2 |  |
| `AskToBeBoyFriend` | param1, param2, param3 |  |
| `AskToBeBoyFriendFromSchoolmate` | param1, param2, param3 |  |
| `AskToBeMySpecialFriend` | param1 |  |
| `AskToBeMySpecialFriendFromSchoolmate` | param1 |  |
| `BreakUp` | userId, friendId, friendType |  |
| `DeleteFriendship` | param1, param2 |  |
| `DeleteFriendshipNeb` | param1, param2 |  |
| `FindUserForFriendBrowser` | params.actorId, params.includeDeleted, params.searchString, pageIndex, pageSize |  |
| `GetFriendList` | param1 |  |
| `GetFriendListWithNameAndScore` | actor.actorId, false |  |
| `GetFriendListWithNameAndScoreV2` | userId, isLoadingTopFriendsOnly |  |
| `GetFriendShipStatus` | param1, param2 |  |
| `GetMspActorSpecialSummary` | param1, param4, param3 |  |
| `GetNebNonFriendStatus` | param2, param4 |  |
| `GetPagedProfileTodos` | actorId, pageId, pageSize |  |
| `GetProfileTodos` | param1 |  |
| `GetProfileTodosCount` | param1 |  |
| `GetSpecialRelationship` | param1 |  |
| `RejectBoyfriend` | param1, param2, param3 |  |
| `RejectFriendShip` | param1, param2 |  |
| `RejectFriendShipNeb` | param1, param2 |  |
| `RejectMySpecialFriend` | param1 |  |
| `RequestFriendship` | param1, param2, param3 |  |
| `RequestFriendshipFromSchoolmate` | param1, param2, param3 |  |
| `RequestFriendshipNeb` | param1, param2 |  |
| `SendInvitation` | param1, param2, param3 |  |

#### `WebService.Messaging.AMFMessagingService`

AMF path : `MovieStarPlanet.WebService.Messaging.AMFMessagingService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `SetMessengerSession` | param1 |  |

#### `WebService.Profile.AMFProfileService`

AMF path : `MovieStarPlanet.WebService.Profile.AMFProfileService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CollectRecycleGift` | param1 |  |
| `DeleteWallPost` | param1, param2, param3 |  |
| `GetWallPost` | param1 |  |
| `GetWallPosts` | param1, param2, param3 |  |
| `LoadProfileSummary` | param1, ActorSession.getActorId() |  |
| `LoadProfileSummaryNeb` | param2, ActorSession.getActorId() |  |
| `PostToWallWithModerationCall` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `RecycleItem` | param1, param2, param3 |  |
| `SetFavorite` | param1, param2, param3 |  |
| `loadActorRoom` | param1, param2 |  |

#### `WebService.School.AMFSchoolService`

AMF path : `MovieStarPlanet.WebService.School.AMFSchoolService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `DeleteSchool` | actorId |  |
| `FindFriendsOnSameSchool` | params.actorId, pageIndex, pageSize, params.includeNames |  |
| `RetrieveMySchoolInformation` | actorId |  |
| `UpdateMySchool` | actorId, schoolId, schoolYear, schoolClass, firstName |  |

### Cadeaux & wishlist

#### `MobileServices.AMFGiftsService+Version2`

AMF path : `MovieStarPlanet.MobileServices.AMFGiftsService+Version2`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BuyGift` | senderId, receiverId, giftId, SWF |  |
| `GetUnifiedActorClothItems` | param1, param2, param3 |  |
| `GetUnifiedActorClothesByType` | param1, param2, param3 |  |
| `GetUnifiedGiftsGiven` | param1, param2 |  |
| `GetUnifiedGiftsNew` | param1, param2 |  |
| `GetUnifiedGiftsReceived` | param1, param2 |  |
| `GetWishListPaged` | actorId, pageIndex, pageSize |  |
| `GiveGiftOfCategory` | senderActorId, receiverActorId, relId, giftId, giftCategory, swf, wrappingColor, msg |  |
| `OpenGift` | actorId, giftId |  |
| `removeFromWishlist` | actorId, giftId |  |

#### `WebService.Gifts.AMFGiftableMembershipService`

AMF path : `MovieStarPlanet.WebService.Gifts.AMFGiftableMembershipService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetGiftableMemberships` | variante 1: VipCertificateStatus.GIVABLE<br>variante 2: VipCertificateStatus.OFFERED<br>variante 3: VipCertificateStatus.REDEEMED | 3 variants |
| `GetMembershipsForUser` | variante 1: param1, -1, param2, param3<br>variante 2: param1, 1, param2, param3 | 2 variants |
| `GetNumberOfUnredeemedMemberships` | — |  |
| `GetReceivedGiftableMemberships` | variante 1: VipCertificateStatus.OFFERED<br>variante 2: VipCertificateStatus.REDEEMED | 2 variants |
| `GiveGiftableMembership` | param1, param2, "", "" |  |
| `HasMembershipActivity` | — |  |
| `RedeemGiftableMembership` | param1 |  |
| `RejectGiftedMembership` | param1 |  |

#### `WebService.Gifts.AMFGiftsService+Version2`

AMF path : `MovieStarPlanet.WebService.Gifts.AMFGiftsService+Version2`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AddItemToWishlist` | clothIds, clothColors |  |
| `AwardStartupReward` | actorId |  |
| `BuyGift` | senderId, receiverId, giftId, SWF |  |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize |  |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize |  |
| `GetGift` | giftId |  |
| `GetGiftLog` | variante 1: giftLogId<br>variante 2: param1 | 2 variants |
| `GetMarketingStepGift` | actorId |  |
| `GiveGiftOfCategory` | senderActorId, receiverActorId, relId, giftId, contentCategory, swf |  |
| `HandleGift` | — |  |
| `IsInUseInRooms` | actorClothesRelId |  |
| `OpenGift` | receiverId, giftId |  |
| `ReturnMassGifts` | singleActorId, multipleActorIds, received |  |
| `RevertTrade` | giftLogId |  |
| `SetMarketingStep` | param1, param2, param3 |  |
| `UpdateGift` | actorId |  |
| `UpdateRetention` | actorId |  |
| `refundGift` | giftLogId, giftId |  |
| `removeFromWishlist` | actorId, giftId |  |
| `returnGift` | giftLogId, giftId |  |

### Scrapblog, photos, design

#### `MobileServices.AMFDesignService`

AMF path : `MovieStarPlanet.MobileServices.AMFDesignService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AutoRenameDesign` | param1 |  |
| `BuyDesignCopy` | actorId, designId |  |
| `CancelDesignSale` | actorId, desginId |  |
| `DeleteDesign` | actorId, designId |  |
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds |  |
| `GetDesignTemplatesPage` | skindId, categories, pageIndex, pageSize |  |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageid, pagesize |  |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageid, pagesize |  |
| `GetPagedListOfMyDesigns` | actorId, pageid, pagesize |  |
| `GetPagedListOfNewestDesigns` | skinId, pageid, pagesize |  |
| `GetPagedListOfTopDesigns` | skinId, pageIndex, pageSize |  |
| `ModeratorDeleteDesigns` | actorId, designId |  |
| `NumberOfDesignsForSale` | actorId |  |
| `ProduceDesign` | actorId, designId |  |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `SearchDesign` | searchString, pageid, pagesize |  |
| `SearchDesigner` | searchString, pageid, pagesize |  |
| `SellDesign` | actorId, designId, amount |  |

#### `WebService.DesignStudio.AMFDesignShopWebService`

AMF path : `MovieStarPlanet.WebService.DesignStudio.AMFDesignShopWebService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BuyDesignCopy` | actorId, designId |  |
| `CancelDesignSale` | param1, param2 |  |
| `GetDesignsForSale` | param1, param2, param3 |  |
| `NumberOfDesignsForSale` | param1 |  |
| `SellDesign` | param1, param2, param3 |  |

#### `WebService.DesignStudio.AMFDesignStudioWebService`

AMF path : `MovieStarPlanet.WebService.DesignStudio.AMFDesignStudioWebService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AutoRenameDesign` | param1 |  |
| `DeleteDesign` | actorId, designId |  |
| `GetPagedListOfCategoryDesigns` | skinId, categoryId, pageID, pageSize |  |
| `GetPagedListOfDesignsFromUser` | actorId, pageId, pageSize |  |
| `GetPagedListOfFriendsDesigns` | skinId, actorId, pageID, pageSize |  |
| `GetPagedListOfMyDesigns` | actorId, pageID, pageSize |  |
| `GetPagedListOfNewestDesigns` | skinId, pageID, pageSize |  |
| `GetPagedListOfTopDesigns` | skinId, pageID, pageSize |  |
| `ModeratorDeleteDesigns` | actorId, designId |  |
| `ProduceDesign` | actorId, designId |  |
| `RenameDesign` | param1, param2, param3 |  |
| `SaveDesignSecureWithSnapshot` | param1, param2, param3, param4, param5, param6, param7, param8 |  |
| `SearchDesign` | searchString, pageID, pageSize |  |
| `SearchDesigner` | searchString, pageID, pageSize |  |

#### `WebService.ImageUpload.AMFImageUpload`

AMF path : `MovieStarPlanet.WebService.ImageUpload.AMFImageUpload`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AddView` | param1, param2 |  |
| `DeleteImage` | param1, param2 |  |
| `EditHeadline` | param1, param2, param3, param4 |  |
| `EditHeadlineMod` | param1, param2 |  |
| `EditStatusMod` | variante 1: id, -2<br>variante 2: param1, param2 | 2 variants |
| `GetFriendsUploads` | param1, param2, param3 |  |
| `GetModSearch` | param1, param2, param3 |  |
| `GetMyUploads` | param1, param2, param3 |  |
| `GetMyUploadsForArtbook` | param1 |  |
| `GetNewUploads` | param1, param2, param3 |  |
| `GetRemainingUploadCount` | param1, param2 |  |
| `GetSingleImage` | param1, param2 |  |
| `GetSingleImageModerator` | param1 |  |
| `GetSingleImageWithGuid` | param1, param2 |  |
| `GetSingleImageWithGuidModerator` | param1 |  |
| `GetTopUploads` | param1, param2, param3 |  |
| `GetUploadsFromUser` | param1, param2, param3 |  |
| `GetUserUploads` | param1, param2, param3 |  |
| `LikeImage` | actorId, imageUploadId |  |
| `PollImages` | param1 |  |
| `PurchaseUpload` | param1 |  |
| `SearchFriendsUploads` | param1, param2, param3, param4 |  |
| `SetPhotoUploadRulesAccepted` | param1 |  |
| `UploadImageWithSnapshot` | param1, param2, _loc5_, param3 |  |

#### `WebService.ScrapBlog.AMFClipArtService`

AMF path : `MovieStarPlanet.WebService.ScrapBlog.AMFClipArtService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetClipArtNew` | clipArtCategoryId, filterDiamonds |  |

#### `WebService.ScrapBlog.AMFScrapBlogService`

AMF path : `MovieStarPlanet.WebService.ScrapBlog.AMFScrapBlogService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AdminDeleteScrapBlog` | param1, param2, param3 |  |
| `DeleteScrapBlog` | param1, param2 |  |
| `GetClipArtCategories` | — |  |
| `GetClipArtNew` | param1, param2 |  |
| `GetFriendsScrapBlogs` | param1, param2, param3 |  |
| `GetFriendsScrapBlogsBatched` | param1, param2 |  |
| `GetHighscoreScrapBlogs` | param1, param2, param3, param4, param5, param6 |  |
| `GetNewestScrapBlogs` | param1, param2 |  |
| `GetPrivateScrapBlogs` | param1, param2, param3 |  |
| `GetScrapBlogsBySearch` | _loc3_, _loc5_, _loc6_, _loc4_ |  |
| `GetScrapBlogsByType` | param1, param2, param3 |  |
| `GetScrapBlogsByUser` | param1, param2, param3 |  |
| `GetScrapBlogsFriendsLiked` | param1, param2, param3 |  |
| `GetSubmissibleScrapBlogs` | param1, param2, param3 |  |
| `LikeScrapBlog` | actorId, scrapBlogId, ownerId |  |
| `LoadScrapBlog` | param1, param2 |  |
| `LoadTemplateByType` | param1 |  |
| `ReplicateScrapblog` | param1, param2 |  |
| `SaveScrapBlogWithSnapshot` | actorId, scrapBlog, snapshotSmall, snapshotBig |  |
| `SetArtbookRulesAccepted` | param1 |  |

### Média (animations, fonds, musique)

#### `MobileServices.AMFAnimationsServiceForMobile`

AMF path : `MovieStarPlanet.MobileServices.AMFAnimationsServiceForMobile`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetActorAnimationsByCategory` | param1 |  |
| `GetAnimationsByFrameLabels` | param1 |  |

#### `WebService.Media.AMFMediaService`

AMF path : `MovieStarPlanet.WebService.Media.AMFMediaService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetAnimations` | — |  |
| `GetBackgrounds` | false |  |
| `GetBackgroundsPaged` | false, pageIndex, pageSize |  |
| `GetMusic` | false |  |
| `GetMyAnimations` | param1 |  |
| `GetMyBackgrounds` | param1 |  |
| `GetMyMusic` | param1 |  |
| `getAnimationCount` | param1 |  |
| `getClothesCount` | param1 |  |
| `getPropsCount` | param1 |  |

### Quêtes, succès, récompenses

#### `WebService.AMFAwardService`

AMF path : `MovieStarPlanet.WebService.AMFAwardService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `RequestAnchorCharacterIntroductionAward` | actorId |  |

#### `WebService.Achievement.AMFAchievementWebService`

AMF path : `MovieStarPlanet.WebService.Achievement.AMFAchievementWebService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CheckLoginAchievements` | param1 |  |
| `ClaimReward` | param1, param2 |  |
| `GetAchievementData` | — |  |
| `GetActorAchievementProgressAll` | actorId |  |
| `GetArtbookStickers` | param1 |  |
| `GetClaimableCategories` | param1 |  |
| `GetPagedAchievements` | actorId, category, pageIndex, pageSize |  |
| `GetTotalProgress` | actorId, category |  |

#### `WebService.Awarding.AMFAwardingService`

AMF path : `MovieStarPlanet.WebService.Awarding.AMFAwardingService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BuyDiamondRespin` | — |  |
| `GetWheelData` | — |  |
| `RequestIntroductionAward` | actorId |  |
| `SpinWheel` | wheelId |  |
| `awardActor` | actorId, amount, type, winSpendType |  |
| `claimAdvertAwardByCampaign` | campaignId |  |
| `claimAdvertViewAward` | type, amount, actorId |  |
| `claimDailyAward` | awardStr, amnt, loggedInActorId |  |
| `countAwardsLeft` | awardStr, actorId |  |
| `hasAllDailyAwardLeft` | awardStr, actorId |  |
| `hasAnyDailyAwardLeft` | awardStr, actorId |  |
| `hasSomeDailyAwardLeft` | awardStr, actorId |  |

#### `WebService.Holiday.AMFHolidayService`

AMF path : `MovieStarPlanet.WebService.Holiday.AMFHolidayService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetReceivedChristmasPresents` | param1, param2 |  |
| `RequestChristmasPresent` | param1, param2, param3 |  |

#### `WebService.PiggyBank.AMFPiggyBankService`

AMF path : `MovieStarPlanet.WebService.PiggyBank.AMFPiggyBankService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CanDestroyPiggyBank` | — |  |
| `DestroyPiggyBank` | — |  |
| `GetPiggyBank` | — |  |

#### `WebService.Quest.AMFQuestService`

AMF path : `MovieStarPlanet.WebService.Quest.AMFQuestService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BeginQuest` | param1, param2 |  |
| `BeginSpecialQuest` | param1, param2 |  |
| `ClaimReward` | param1, param2, param3 |  |
| `ClaimRewardForDownloadableClient` | param1, param2, param3 |  |
| `ClaimSpecialQuestBaseReward` | param1, param2 |  |
| `ClaimSpecialQuestSubOrFinalReward` | param1, param2 |  |
| `DiamondSkip` | param1, param2 |  |
| `ForceCompleteCurrentQuest` | param1, param2 |  |
| `ForceCompleteCurrentQuestForDownloadableClient` | param1, param2 |  |
| `GetAllQuestStatus` | param1 |  |
| `GetAllQuestStatusForDownloadableClient` | param1 |  |
| `GetGiftHuntQuestData` | param1, param2 |  |
| `ResetNotifications` | param1, param2 |  |
| `UpdateDoTaskObjectiveAndGetStatus` | param1, param2, param3, param4 |  |
| `UpdateGotoObjectiveAndGetStatus` | param1, param2, param3 |  |
| `UpdateSpecialQuestObjectiveOld` | param1, param2, param3 |  |
| `UpdateSpecialQuestObjectives` | param1, param2, param3 |  |

### Compétitions

#### `WebService.Competition.AMFCompetitionService`

AMF path : `MovieStarPlanet.WebService.Competition.AMFCompetitionService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetMovieCompetition` | id |  |
| `GetMovieCompetitionList` | params[0 |  |
| `GetMovieCompetitionListById` | params[0 |  |
| `GetMovieCompetitionListByNewsId` | newsId |  |
| `GetNewsById` | param1, param2, param3 |  |
| `GetParticipatingLooks` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingMovies` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingRooms` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetParticipatingScrapBlogs` | competitionId, params.moderatormode, pageIndex, pageSize |  |
| `GetSubmittedMovieCompetitionLook` | movieCompetitionId, actorId |  |
| `GetSubmittedMovieCompetitionMovie` | movieCompetitionId, actorId |  |
| `GetSubmittedMovieCompetitionRoom` | movieCompetitionId, actorId |  |
| `GetSubmittedScrapBlog` | competitionId, actorId |  |
| `HasActorVotedInCompetition` | movieCompetitionId, actorId |  |
| `LinkCompetitionToTheme` | newsId, themeId |  |
| `MovieCompetitionPublish` | param1, param2, param3 |  |
| `SaveMovieCompetition` | competition, awardPrizes |  |
| `SubmitEntityToCompetition` | movieCompetitionId, entityId, actorId |  |
| `VoteInMovieCompetition` | movieCompetitionId, movieId, actorId |  |

#### `WebService.DailyCompetition.AMFDailyCompetitionService`

AMF path : `MovieStarPlanet.WebService.DailyCompetition.AMFDailyCompetitionService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `IncrementSubmissionResets` | — |  |
| `addToComp` | param2, param3, param4 |  |
| `canSubmit` | param2, param3 |  |
| `getRandomItem` | param2 |  |
| `getTodaysTheme` | — |  |
| `getVoteScore` | param2 |  |
| `voteFor` | param2, param3, param4, param5, param6 |  |

### Forum, sondages, news, activités

#### `Polls.AMFPollService`

AMF path : `MovieStarPlanet.Polls.AMFPollService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetPoll` | pollId, actorId |  |
| `GetPollLatest` | actorId |  |
| `GetPolls` | pageindex, pagesize |  |
| `GetPollsUnused` | — |  |
| `LinkPolls` | pollId, nextPollId |  |
| `NewPoll` | question, answer1, answer2, answer3, answer4 |  |
| `NewPollPublish` | pollId, locale, siteDomain |  |
| `VotePoll` | pollId, actorId, answer |  |

#### `WebService.Campaign.AMFCampaignService`

AMF path : `MovieStarPlanet.WebService.Campaign.AMFCampaignService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `UseCampaign` | param1, param2 |  |

#### `WebService.Forums.AMFForumService`

AMF path : `MovieStarPlanet.WebService.Forums.AMFForumService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AdminCreateTopic` | actorName, actorPassword, forumId, subject, type, message, colorCode, subjectChatLogId, messageChatLogId |  |
| `AdminCreateTopicPoll` | actorId, forumId, filteredQuestion, filteredAnsers, topicType, adminUserName, adminPassword, -1 |  |
| `CheckAllowedCreateTopic` | actorId |  |
| `CreatePostWithModerationCall` | actorId, actorName, topicId, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `CreateTopicPollWithModerationCall` | actorId, actorName, forumId, pollQuestion, pollAnswers, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `CreateTopicWithModerationCall` | actorId, actorName, forumId, forumSubject, forumMessage, colorCode, TextModerationHandler.getInstance().isRestrictedUser() |  |
| `DeletePost` | postId, actorName, actorPassword |  |
| `DeleteTopic` | topicId, actorName, actorPassword |  |
| `GetFilteredTopics` | params.forumId, params.filterId, params.actorId, pageIndex, pageSize |  |
| `GetForums` | — |  |
| `GetPostAmount` | topicId |  |
| `GetPostData` | postId |  |
| `GetPosts` | topicID, pageIndex, pageSize |  |
| `GetTopic` | topicId, actorId |  |
| `ToggleSticky` | actorName, actorPassword, topicId, type |  |
| `UpdatePost` | actorId |  |
| `UpdateTopic` | topic.TopicId |  |
| `UserDeletePost` | actorId, postId |  |

#### `WebService.NewsService.AMFNewsService`

AMF path : `MovieStarPlanet.WebService.NewsService.AMFNewsService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetActiveNewsScrapBlog` | param1 |  |
| `GetActiveNewsSlides` | param1 |  |
| `GetNewsById` | param1 |  |
| `NewsClicked` | param1, param2 |  |
| `SaveNews` | param1 |  |
| `SaveThemeSnapshot` | param1, param2, param3, param4, param5, param6 |  |
| `SetNewsUsage` | param1 |  |

#### `WebService.NotificationCenter.AMFNotificationCenterService`

AMF path : `MovieStarPlanet.WebService.NotificationCenter.AMFNotificationCenterService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `ClaimBonus2` | actorId, contentTypes |  |
| `GetNotificationCount` | param1 |  |
| `GetNotificationsWithImageGuid` | param1 |  |
| `GetThirdPatyAppNotifications` | param1 |  |
| `GetTotalFameAward` | — |  |

### Highscores & thèmes

#### `WebService.Content.AmfContentService`

AMF path : `MovieStarPlanet.WebService.Content.AmfContentService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetItemsInCurrentTheme` | ticket, themeId, hash |  |
| `GetLastEditedDate` | param1, param2, param3, param4 |  |

#### `WebService.ExternalApps.AMFExternalAppsService`

AMF path : `MovieStarPlanet.WebService.ExternalApps.AMFExternalAppsService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetExternalAppsInCountry` | variante 1: _loc2_, "ALL"<br>variante 2: countryCode, "Android"<br>variante 3: countryCode, "IOS" | 3 variants |

#### `WebService.Highscore.AMFHighscoreService`

AMF path : `MovieStarPlanet.WebService.Highscore.AMFHighscoreService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetHighscoreActor` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreAnimations` | pageIndex, pageSize |  |
| `GetHighscoreBackgrounds` | pageIndex, pageSize |  |
| `GetHighscoreBonster` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreClothes` | pageIndex, pageSize |  |
| `GetHighscoreItems` | pageIndex, pageSize |  |
| `GetHighscoreLook` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreMovie` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscorePet` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreScrapBlog` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |
| `GetHighscoreYouTube` | parameters.actorId, parameters.forFriends, parameters.lastWeek, parameters.orderBy, pageIndex, pageSize |  |

#### `WebService.WorldTheme.AMFWorldThemeService`

AMF path : `MovieStarPlanet.WebService.WorldTheme.AMFWorldThemeService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CreateNewWorldTheme` | themeName, folderName, themeId |  |
| `CreateNewWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |  |
| `DeleteWorldTheme` | worldThemeId |  |
| `EditWorldTheme` | worldThemeId, themeName, themeId |  |
| `EditWorldThemeAreas` | worldThemeId, backgroundFileName, chatFileName, creativeFileName, gamesFileName, shoppingFileName, overviewFileName, petsFileName, logoFileName, overviewMobileFileName, spinTheWheelWebFileName, spinTheWheelMobileFileName |  |
| `GetAllWorldThemes` | — |  |
| `GetOldWorldThemes` | — |  |
| `GetPresentFutureWorldThemes` | — |  |
| `GetWorldThemeAreasByWorldThemeId` | worldThemeId |  |
| `GetWorldThemeChatRoom` | worldThemeId |  |
| `GetWorldThemeInfo` | — |  |
| `SaveWorldThemeChatRoomInfo` | worldThemeId, roomName, backgroundFileName, requiredItemType, requiredItemId |  |

### Admin, upload, modération, infra

#### `WebService.AMFCommonService`

AMF path : `MovieStarPlanet.WebService.AMFCommonService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `ActorHasLiked` | param3, param1, param2 |  |
| `LikeAdd` | entityType, entityId, selfActorId, receiver |  |
| `LogChat` | param1, param2, param3, InputLocations.DESTINATION_TYPE_USER |  |
| `LogInput` | roomId, actorId, roomInstanceId, message, destinationType |  |
| `SendContentEmail` | param1, param2, param3, param4, param5 |  |
| `getNowAsString` | — |  |

#### `WebService.Admin.AMFAdminService`

AMF path : `MovieStarPlanet.WebService.Admin.AMFAdminService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `BlockName` | param1, param2, param3 |  |
| `ClearCache` | param1, param2, true |  |
| `ClearNewMarkings` | param1, param2 |  |
| `DeleteTwitterText` | param1, param2, param3 |  |
| `GetActorLocale` | param1 |  |
| `GetAllGiftsGiven` | actorId, pageIndex, pageSize |  |
| `GetAllGiftsReceived` | actorId, pageIndex, pageSize |  |
| `GetBadWordActorList` | pageIndex, pageSize |  |
| `GetBlockedIP` | ipAsInt, moderatorName, moderatorPass |  |
| `GetBlockedInfo` | ipAsInt, moderatorName, moderatorPass |  |
| `GetBlockedNames` | searchphrase |  |
| `GetChatLogList` | actorId, pageIndex, pageSize |  |
| `GetChatLogListByReportTime` | paramObj.actorId, paramObj.reportId, pageIndex, pageSize |  |
| `GetChatLogListLocked` | actorId |  |
| `GetIPLoginType` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetIPUsers` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetIPWarnings` | ipAsIntToUse, moderatorName, moderatorPass |  |
| `GetLocaleResources` | param1, param2, param3, param4, param5 |  |
| `GetLoginHistory` | param1, param2, param3 |  |
| `GetModeratorList` | pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |  |
| `GetModeratorWarningCount` | paramObj.moderatorId, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass |  |
| `GetModeratorWarnings` | paramObj.moderatorId, paramObj.date, pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |  |
| `GetReportList` | onlyGetNotHandled, pageIndex, pageSize |  |
| `GetReportOverview` | — |  |
| `GetSecureModuleUrl` | — |  |
| `GetTotalModeratorActivitiesDone` | actorId, moderatorName, moderatorPass |  |
| `GetWarnedIPListNew` | paramObj.blocked, pageIndex, pageSize, paramObj.moderatorName, paramObj.moderatorPass, paramObj.specificIp ? paramObj.specificIp : 0 |  |
| `GetWarningLog` | pageIndex, pageSize, paramObj.actorName, paramObj.actorPassword |  |
| `GiveAutoWarning` | param1, param2, param3, param4 |  |
| `IsAdminSite` | param1, param2 |  |
| `IsUploadSite` | — |  |
| `LockOutUser` | param1, param2, param3, param4, param5 |  |
| `RemoveRoboBlastContent` | actorId, contentType, contentId, reporterId, site |  |
| `ReportHandled` | reportId, handledByActorId |  |
| `SaveLocaleResources` | param1 |  |
| `UnblockName` | param1, param2, param3 |  |
| `blockIP` | ipAsIntToBlock, moderatorActorId, moderatorName, moderatorPass, blockingDaysCount, comment |  |
| `deleteMovieViaProfile` | movieId, moderatorName, moderatorPass |  |
| `getChatRoomOpenCloseTimes` | — |  |
| `isIPBlockedNew` | ipAsIntToFind, moderatorName, moderatorPass |  |
| `markIpAsPublic` | ipAsIntToMark, moderatorName, moderatorPass |  |
| `saveSpamReport` | spamtext, moderatorActorId, moderatorName, moderatorPass |  |
| `setChatRoomOpenCloseTimes` | open, close |  |
| `unblockIP` | ipAsIntToUnblock, moderatorID, moderatorName, moderatorPass, comment |  |
| `unmarkIpAsPublic` | ipAsIntToUnmark, moderatorName, moderatorPass |  |

#### `WebService.AnimationSnapshot.AMFAnimationSnapshotService`

AMF path : `MovieStarPlanet.WebService.AnimationSnapshot.AMFAnimationSnapshotService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `getAnimationNames` | — |  |
| `saveImage` | data, name |  |

#### `WebService.Common.AMFCommonWebService`

AMF path : `MovieStarPlanet.WebService.Common.AMFCommonWebService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `GetEntityName` | param1, param2 |  |
| `GetPlaylistExternalRef` | param1 |  |
| `LikeAdd` | entityType, entityId, actorId, receiverId |  |
| `SaveRoomWithSnapshot` | wallpaper, floor, arrayOfMyRoomInstances, roomSnapshotProfile, roomSnapshotMedium, roomSnapshotSmall |  |
| `SendContentEmail` | param1, param2, param3, param4, param5 |  |

#### `WebService.Logging.AMFLoggingService`

AMF path : `MovieStarPlanet.WebService.Logging.AMFLoggingService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `ClientLog` | param1, param2 |  |
| `CreateTestException` | — |  |
| `GetLatestServerException` | — |  |
| `LogClient` | param1, param2 |  |

#### `WebService.Moderation.AMFModeration`

AMF path : `MovieStarPlanet.WebService.Moderation.AMFModeration`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CheckNewUsername` | userName, this._site |  |
| `FilterText` | variante 1: param1, param5, param4, param2, param3<br>variante 2: param1, param5, param4, param2, param3, param8, param9 | 2 variants |
| `LoginEvent` | param1 |  |
| `ReportUser` | param2, param3, param4, param6, this._site, param7 |  |
| `ReportUserNeb` | param2, param5, param4, param6 |  |

#### `WebService.Os.AMFOs`

AMF path : `MovieStarPlanet.WebService.Os.AMFOs`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CreateOsRef` | — |  |
| `RunOsCheck` | refId, hist.join(":") |  |

#### `WebService.PerformanceTracking.AMFPerformanceTrackingService`

AMF path : `MovieStarPlanet.WebService.PerformanceTracking.AMFPerformanceTrackingService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `AddEntry` | param1, param2 |  |

#### `WebService.Snapshots.AMFGenericSnapshotService`

AMF path : `MovieStarPlanet.WebService.Snapshots.AMFGenericSnapshotService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CreateSnapshot` | variante 1: param1, param2, param3, param4<br>variante 2: param1, param2, param3, param4, param5 | 2 variants |
| `CreateSnapshotSmallAndBig` | param1, param2, param3, param4, param5, param6 |  |

#### `WebService.TagManager.AMFTagManager`

AMF path : `MovieStarPlanet.WebService.TagManager.AMFTagManager`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `DeleteTag` | param1 |  |
| `GetAllTags` | — |  |
| `GetBackgroundTags` | — |  |
| `GetTagsForSkinClothes` | param2 |  |
| `GetTagsInCategorySkin` | param2, param3 |  |
| `SaveTag` | param1 |  |

#### `WebService.ThemeManager.AMFThemeManagerService`

AMF path : `MovieStarPlanet.WebService.ThemeManager.AMFThemeManagerService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `DeleteTheme` | param1 |  |
| `GetAllCampaigns` | — |  |
| `GetAllThemes` | — |  |
| `GetCurrectNewCategorySortIndex` | — |  |
| `InsertTheme` | param1, param2, param3, param4 |  |
| `LabelClothesWithTheme` | param1, param2 |  |
| `RetrieveThemeID` | param1, param2 |  |
| `SortShoppingItems` | param1, param2, param3 |  |
| `UpdateTheme` | param1 |  |

#### `WebService.Upload.AMFUploadService`

AMF path : `MovieStarPlanet.WebService.Upload.AMFUploadService`

| Method | Parameters (client) | Notes |
|--------|-------------------|------|
| `CheckAnimationExists` | animationName |  |
| `DeleteClipArt` | clipart, subpath |  |
| `DeleteFacepart` | facepartId, type |  |
| `DeleteWallpaper` | wallpaperId |  |
| `EditAnimation` | animationId, name, price, discount, checkVip, checkNew, checkDeleted, animCategoryId, themeID, priceDiamonds |  |
| `EditClipArt` | clipart, subpath, sort, checkvip, checknew, price, diamondsPrice |  |
| `EditFacepart` | facepartId, type, gender, name, fileName, price, checkvip, checknew, checkreg, discount, sortorder, themeID, priceDiamonds |  |
| `FileExistsCheck` | key |  |
| `GetAnimationCategories` | — |  |
| `GetClipArtPath` | clipart |  |
| `InsertAnimation` | name, price, diamondsprice, animCategory, vip, fileName, themeID |  |
| `InsertBackground` | name, price, backgroundCategory, vip, fileName, themeID |  |
| `InsertClipArt` | type, category, fileName, checkvip, checkNew, sortorder, price, diamondPrice, colorScheme |  |
| `InsertFacepart` | type, gender, name, fileName, price, diamondPrice, checkvip, dragonBone, defaultColors, checknew, checkreg, discount, sortorder, themeID, date, hidden |  |
| `InsertWallpaper` | type, roomtype, name, filepath |  |
| `getAllColorschemelessClothes` | pageIdx, pageSize |  |
| `getBonsterInfo` | templateName |  |
| `getClipArtCategoryNames` | paramid |  |
| `getClipArtTypes` | — |  |
| `giveBonster` | templateName |  |
| `saveClothUpdater` | cloth, themeID |  |
| `setClothColorSchemes` | variante 1: [colorSchemeObject<br>variante 2: clothColorSchemes | 2 variants |
| `updateAnimation` | copy, themeID |  |
| `updateBackground` | copy, themeID |  |
| `updateBonsterColors` | bonsterId, colorMatrix |  |
| `updateBonsterScale` | bonsterId, mobScale, webScale |  |
| `updateCloth` | clothUpdater |  |
| `updateMusic` | copy |  |
| `uploadBonster` | templateName, templateId, armatureName, price, diamondsPrice, isVIP, deleted, specialEggCrate, scale, scaleWeb |  |

---

## Main source files

| Topic | File |
|-------|------|
| Food | `pets/module/petpopup/service/food/PetFood.as` |
| Favorites | `pets/module/petpopup/service/food/PersonalityFoods.as` |
| Candy pricing | `bonster/service/BonsterCandyPrices.as` |
| Bonster constants | `bonster/BonsterConstants.as`, `bonster/BonsterUtils.as` |
| Bonster petting | `bonster/BonsterClickItem.as`, `bonster/service/BonsterAMFService.as` |
| Legacy petting | `pet/service/PetAMFService.as`, `Components/MonsterPopup.as` |
| Rate limits | `utils/RateLimiterController.as`, `amf/AmfListener.as` |
| AMF security | `amf/AmfCall.as`, `amf/checksum/ChecksumCalculator.as`, `amf/AmfCallExternalCommands.as`, `amf/TicketGenerator.as` |
| OS Check | `moviestar/snapshot/SnapLoader.as` |
| Boosters | `services/spendingservice/valueObjects/SpecialsItem.as` |
| Fame booster | `utils/actorvalues/ActorValueManager.as` |
| 10 pets/room limit | `chatrooms/view/overlayUserInterface/ChatRoomItemSelectorView.as` |
| Pet shop | `shopping/module/petshop/model/PetShopModel.as` |
| Hotel | `pets/hotel/PetHotel.as` |
| Legacy pets | `pet/utils/MonsterConstants.as` |
| Looks | `look/service/LookAMFService.as` |
| Clothes / actor | `actorservice/mobileservice/ActorAmfService.as`, `actorservice/service/ActorAmfServiceForWeb.as` |
| Shop | `services/shopcontentservice/ShopContentAmfService.as` |
| Diamond spending | `services/spendingservice/SpendingAmfService.as` |

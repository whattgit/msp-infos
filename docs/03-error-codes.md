# I.3 — Codes de réponse (tous systèmes)

## Bonsters — BonsterInteractionResponse

| Code | Signification |
|------|---------------|
| 0 | Succès |
| −1 | Exception |
| −2 | Pas VIP |
| −3 | Pas assez SC |
| −4 | Pas assez diamants |
| −5 | Pet malade |
| −429 | Rate limited |

## Spending — BuyClothes, boosters

| Code | Signification |
|------|---------------|
| 0 | Succès |
| −1 | Exception |
| −2 | Pas assez diamants |
| −3 | Déjà acheté aujourd'hui |
| −4 | Pas assez SC |
| −5 | Créateur ne peut pas acheter |

## Cadeaux — GiveGiftOfCategory

| Code | Signification |
|------|---------------|
| 0 | OK |
| −1 | Erreur |
| −10 | Non-VIP niv. 6 |
| −20 | Limite quotidienne |
| −30 | Déjà possédé |
| −40 | Cooldown |

## Upload photos — ImageUploadResponse

| Code | Signification |
|------|---------------|
| 0 | OK |
| −2 | Quota épuisé |
| −3 | Pas assez diamants |
| −6 | Like impossible |

## Forum — création topic

| Code | Signification |
|------|---------------|
| 0 | OK |
| 1 | Erreur |
| 2 | Chaîne interdite |

## Amis — GetFriendShipStatus

| Code | Signification |
|------|---------------|
| 0 | Même user |
| 1 | Pas amis |
| 2 | Amis |
| 3 | Demande envoyée |
| 4 | Demande reçue |

## Films — MovieWatched returnType

| Code | Signification |
|------|---------------|
| 0 | Déjà noté |
| 1 | Nouveau + notation |
| 2 | Visionnage sans re-note |

## Mur profil — PostToWall

| Code | Signification |
|------|---------------|
| 0 | Autorisé |
| 1 | Modérateur bloqué |
| 2 | Communication interdite |

## Clubs, certificats, redeem

| Système | Codes |
|---------|-------|
| Clubs | 4 = trop d'adhésions, −1 = trop créés |
| Certificats | 5 OK, 6 utilisé, 9 invalidé |
| Redeem | ERROR_CODE_TOO_MANY_ATTEMPTS |

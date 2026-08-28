# I.3 — Response codes (all systems)

> **EN** · [Français](../fr/03-error-codes.md)

## Bonsters — BonsterInteractionResponse

| Code | Meaning |
|------|---------|
| 0 | Success |
| −1 | Exception |
| −2 | Not VIP |
| −3 | Not enough SC |
| −4 | Not enough diamonds |
| −5 | Pet sick |
| −429 | Rate limited |

## Spending — BuyClothes, boosters

| Code | Meaning |
|------|---------|
| 0 | Success |
| −1 | Exception |
| −2 | Not enough diamonds |
| −3 | Already bought today |
| −4 | Not enough SC |
| −5 | Creator cannot buy |

## Gifts — GiveGiftOfCategory

| Code | Meaning |
|------|---------|
| 0 | OK |
| −1 | Error |
| −10 | Non-VIP lvl. 6 |
| −20 | Daily limit |
| −30 | Already owned |
| −40 | Cooldown |

## Photo upload — ImageUploadResponse

| Code | Meaning |
|------|---------|
| 0 | OK |
| −2 | Quota exhausted |
| −3 | Not enough diamonds |
| −6 | Like impossible |

## Forum — topic creation

| Code | Meaning |
|------|---------|
| 0 | OK |
| 1 | Error |
| 2 | Forbidden string |

## Friends — GetFriendShipStatus

| Code | Meaning |
|------|---------|
| 0 | Same user |
| 1 | Not friends |
| 2 | Friends |
| 3 | Request sent |
| 4 | Request received |

## Movies — MovieWatched returnType

| Code | Meaning |
|------|---------|
| 0 | Already rated |
| 1 | New + rating |
| 2 | Watch without re-rate |

## Profile wall — PostToWall

| Code | Meaning |
|------|---------|
| 0 | Allowed |
| 1 | Moderator blocked |
| 2 | Communication forbidden |

## Clubs, certificates, redeem

| System | Codes |
|---------|-------|
| Clubs | 4 = too many memberships, −1 = too many created |
| Certificates | 5 OK, 6 used, 9 invalidated |
| Redeem | ERROR_CODE_TOO_MANY_ATTEMPTS |

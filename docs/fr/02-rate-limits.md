# I.2 — Rate limits & quotas

> **FR** · [English](../en/02-rate-limits.md)


## Deux mécanismes

| Niveau | Signal | Handler |
|--------|--------|---------|
| Corps AMF | Valeur `== -429` | `RateLimiterController` |
| HTTP | Status 429 | `AmfListener` |

Code : **`CODE_IS_REQUEST_BLOCKED = -429`**. Quotas exacts = **serveur uniquement**.

## Endpoints avec handler client explicite

| Endpoint | Service | Champ vérifié | Popup |
|----------|---------|---------------|-------|
| `PetFriendBonster` | AMFBonsterService | entier SC | **Non** |
| `MovieWatched` | AMFMovieService | awardedFame | Oui |
| `LikeAdd` | AMFCommonService | fameEarned | Oui |
| `LikeScrapBlog` | AMFScrapBlogService | fameEarned | Oui |
| `LikeImage` | AMFImageUpload | Code | Oui |
| `SpinWheel` | AMFAwardingService | Status | Oui |
| `GiveAutographAndCalculateTimestamp` | AMFUserSessionService | Fame | Oui |
| `GiveAutographAndCalculateTimestampNeb` | AMFActorService | Fame | Oui |
| `SaveRoomWithSnapshot` | AMFRoomService | entier | Oui |
| `OpenGift` | AMFGiftsService | GiftLogId | Oui |
| `ClaimBonus2` | AMFNotificationCenterService | ErrorCode | Oui |
| `claimDailyAward` | AMFAwardingService | amount | Oui |
| `claimAdvertViewAward` | AMFAwardingService | amount | Oui |
| `claimAdvertAwardByCampaign` | AMFAwardingService | amount | Oui |
| `BuySpecialGreeting` | AMFSpendingService | Code | Oui |
| `PickupGuidePresent` | AMFActorService | Code | Oui |

## Limites client (anti-spam local)

| Limite | Valeur |
|--------|--------|
| Caresses / session / pet | 1× |
| AMF concurrents | 10 max |
| Timeout AMF | 20 000 ms |
| Cadeaux / jour (UI) | 25 |
| Pets / salle | 10 |
| Autographe non-VIP | 1 h cooldown |
| Autographe VIP | 4–30/h selon tier |

## Erreurs HTTP

| Code | Action |
|------|--------|
| 400 | Pas de retry |
| 401 | Refresh Nebula |
| 427 | Refresh token |
| 429 | Popup too many requests |
| 500/501/505 | Pas de retry |

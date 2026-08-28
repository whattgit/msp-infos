# I.2 — Rate limits & quotas

> **EN** · [Français](../fr/02-rate-limits.md)

## Two mechanisms

| Level | Signal | Handler |
|--------|--------|---------|
| AMF body | Value `== -429` | `RateLimiterController` |
| HTTP | Status 429 | `AmfListener` |

Code: **`CODE_IS_REQUEST_BLOCKED = -429`**. Exact quotas = **server only**.

## Endpoints with explicit client handler

| Endpoint | Service | Checked field | Popup |
|----------|---------|---------------|-------|
| `PetFriendBonster` | AMFBonsterService | SC integer | **No** |
| `MovieWatched` | AMFMovieService | awardedFame | Yes |
| `LikeAdd` | AMFCommonService | fameEarned | Yes |
| `LikeScrapBlog` | AMFScrapBlogService | fameEarned | Yes |
| `LikeImage` | AMFImageUpload | Code | Yes |
| `SpinWheel` | AMFAwardingService | Status | Yes |
| `GiveAutographAndCalculateTimestamp` | AMFUserSessionService | Fame | Yes |
| `GiveAutographAndCalculateTimestampNeb` | AMFActorService | Fame | Yes |
| `SaveRoomWithSnapshot` | AMFRoomService | integer | Yes |
| `OpenGift` | AMFGiftsService | GiftLogId | Yes |
| `ClaimBonus2` | AMFNotificationCenterService | ErrorCode | Yes |
| `claimDailyAward` | AMFAwardingService | amount | Yes |
| `claimAdvertViewAward` | AMFAwardingService | amount | Yes |
| `claimAdvertAwardByCampaign` | AMFAwardingService | amount | Yes |
| `BuySpecialGreeting` | AMFSpendingService | Code | Yes |
| `PickupGuidePresent` | AMFActorService | Code | Yes |

## Client limits (local anti-spam)

| Limit | Value |
|--------|--------|
| Pets / session / pet | 1× |
| Concurrent AMF | 10 max |
| AMF timeout | 20 000 ms |
| Gifts / day (UI) | 25 |
| Pets / room | 10 |
| Autograph non-VIP | 1 h cooldown |
| Autograph VIP | 4–30/h by tier |

## HTTP errors

| Code | Action |
|------|--------|
| 400 | No retry |
| 401 | Nebula refresh |
| 427 | Token refresh |
| 429 | Too many requests popup |
| 500/501/505 | No retry |

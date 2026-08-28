# II.3 — Gifts, Friends & Social

> **EN** · [Français](../fr/07-gifts-friendship-social.md)

## Gifts (AMFGiftsService+Version2)

### Send flow
1. `HasReachedDailyGiftsLimit` — max **25/day** UI
2. `GiveGiftOfCategory(sender, receiver, relId, category, giftId, swf)`
3. Codes: 0, −10 VIP, −20 daily, −30 duplicate, −40 cooldown

### Open flow
- `OpenGift(receiverId, giftId)` — **`GiftLogId==-429`** rate limit

### Trades
`GiveTradeGift` → `TradeItem` / `CancelTrade` / `RevertTrade`

## Friendship (AMFFriendshipService)

| Flow | Endpoints |
|------|-----------|
| Request | RequestFriendship, RequestFriendshipNeb |
| Acceptance | ApproveFriendship |
| BF | AskToBeBoyFriend → AcceptBoyfriend / BreakUp |
| Best friend | AskToBeMySpecialFriend → AcceptMySpecialFriend |

Statuses: 0–4 (+ 5/6 BF, 9 best friend). No rate limit.

## Profile (AMFProfileService)

- `LoadProfileSummary` / Nebula variant
- `PostToWallWithModerationCall` — MARS required, codes 0/1/2
- `SetFavorite`, `RecycleItem`, `loadActorRoom`

## Messaging

- `SendChatMessageWithModerationCall` — moderated chat
- `IsCommunicationAllowedWith` — wall/chat pre-check

## Detailed endpoints

→ [amf/11-gifts.md](amf/11-gifts.md) · [amf/10-social.md](amf/10-social.md)

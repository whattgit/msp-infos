# II.3 — Cadeaux, Amis & Social

> **FR** · [English](../en/07-gifts-friendship-social.md)


## Cadeaux (AMFGiftsService+Version2)

### Flux envoi
1. `HasReachedDailyGiftsLimit` — max **25/jour** UI
2. `GiveGiftOfCategory(sender, receiver, relId, category, giftId, swf)`
3. Codes : 0, −10 VIP, −20 daily, −30 duplicate, −40 cooldown

### Flux ouverture
- `OpenGift(receiverId, giftId)` — **`GiftLogId==-429`** rate limit

### Trades
`GiveTradeGift` → `TradeItem` / `CancelTrade` / `RevertTrade`

## Amitié (AMFFriendshipService)

| Flux | Endpoints |
|------|-----------|
| Demande | RequestFriendship, RequestFriendshipNeb |
| Acceptation | ApproveFriendship |
| BF | AskToBeBoyFriend → AcceptBoyfriend / BreakUp |
| Best friend | AskToBeMySpecialFriend → AcceptMySpecialFriend |

Statuts : 0–4 (+ 5/6 BF, 9 best friend). Pas de rate limit.

## Profil (AMFProfileService)

- `LoadProfileSummary` / Nebula variant
- `PostToWallWithModerationCall` — MARS requis, codes 0/1/2
- `SetFavorite`, `RecycleItem`, `loadActorRoom`

## Messagerie

- `SendChatMessageWithModerationCall` — chat modéré
- `IsCommunicationAllowedWith` — pré-check mur/chat

## Endpoints détaillés

→ [amf/11-gifts.md](amf/11-gifts.md) · [amf/10-social.md](amf/10-social.md)

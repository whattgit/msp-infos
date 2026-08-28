# II.1 — Pets & Bonsters (full mechanics)

> **EN** · [Français](../fr/05-pets-bonsters.md)

## Identifiers

| Field | Description |
|-------|-------------|
| `BonsterId` | Shop model (catalogue) |
| `BonsterTemplateId` | Visual template (skeleton, palettes) |
| `ActorBonsterRelId` | Owned instance (unique) |
| `ActorClickItemRelId` | Legacy Monster/Boonie pet (unique) |
| `Personality` | 1–5 (Shy, Sporty, Smiley, Sleepy, Clever) |

| Rule | Value |
|-------|--------|
| Visual evolution | Levels **12** and **24** |
| Reward animations | **6, 12, 18, 24, 28, 32** |
| Max UI level | **100** (candy off) |
| Max name | **20** characters, moderated |

## Life cycle

| State | Condition | Scale |
|------|-----------|-------|
| Boonie egg | stage 0, template 0 | 0.5 |
| Crate | stage 0, template ≠ 0 | 0.6 |
| Stage 1–3 | evolution 1–3 | 0.65–1.0 |

- **Hatch**: `HatchBonster` → `WashPoints = 50` on hatch.
- **Auto evolution**: levels 12 and 24.
- **Instant evolve**: booster `INSTANT_PET_GROW` → `InstantEvolveBonster`.

## Food

| ID | Name | SC | Notes |
|----|-----|-----|-------|
| 1–10 | Foods | 3 | Normal or favorite (60 vs 40 XP) |
| 11 | Medicine | 20 | Required if sick (`resultCode -5`) |
| 12 | Candy | 💎 dyn. | `GetBonsterCandyPrices` |

## Personalities & favourites

| Personality | Favourite food IDs |
|-------|---------------|
| Shy | 1, 2 |
| Sporty | 4, 6 |
| Smiley | 3, 10 |
| Sleepy | 7, 9 |
| Clever | 5, 8 |

## Candy

Tiers `{LevelFloor, LevelCeil, CandyPrice}` via `GetBonsterCandyPrices`. Algo `calculateCandyPrice(n)`. Off if n≥100.

## Needs & XP

| Mechanic | Value |
|-----------|--------|
| Bar decay | −1 pt / 15 min |
| Sickness | 3 days without feeding |
| Max bars | 100 |
| feed/wash/play response | `BonsterInteractionResponse` (XP, level, resultCode) |

## Petting

`PetFriendBonster(actorId, relId)` → **int SC**. 1×/session/pet client-side. `-429` silent.

| Return | Effect |
|--------|-------|
| `> 0` | SC credited |
| `0` | Already petted / refused |
| `-429` | Rate limit |

Legacy: `PetFriendPet` — UI cooldown 3000 ms.

## Hotel

7d/100 SC · 14d/200 · 28d/300 VIP. −50% `SHOPPING_SPREE`.

## AMF endpoints (full detail)

→ [amf/07-pets.md](amf/07-pets.md) — each endpoint with parameters, ticket, codes, rate limits and client files.

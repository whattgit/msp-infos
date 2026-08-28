# II.1 — Pets & Bonsters (mécanique complète)

> **FR** · [English](../en/05-pets-bonsters.md)


## Identifiants

| Champ | Description |
|-------|-------------|
| `BonsterId` | Modèle boutique (catalogue) |
| `BonsterTemplateId` | Template visuel (squelette, palettes) |
| `ActorBonsterRelId` | Instance possédée (unique) |
| `ActorClickItemRelId` | Ancien pet Monster/Boonie (unique) |
| `Personality` | 1–5 (Timide, Sportif, Souriant, Dormeur, Malin) |

| Règle | Valeur |
|-------|--------|
| Évolution visuelle | Niveaux **12** et **24** |
| Animations récompense | **6, 12, 18, 24, 28, 32** |
| Niveau max UI | **100** (bonbon off) |
| Nom max | **20** caractères, modéré |

## Cycle de vie

| État | Condition | Scale |
|------|-----------|-------|
| Œuf Boonie | stage 0, template 0 | 0.5 |
| Caisse | stage 0, template ≠ 0 | 0.6 |
| Stade 1–3 | evolution 1–3 | 0.65–1.0 |

- **Hatch** : `HatchBonster` → `WashPoints = 50` à l'éclosion.
- **Évolution auto** : niveaux 12 et 24.
- **Instant evolve** : booster `INSTANT_PET_GROW` → `InstantEvolveBonster`.

## Nourriture

| ID | Nom | SC | Notes |
|----|-----|-----|-------|
| 1–10 | Aliments | 3 | Normal ou favori (60 vs 40 XP) |
| 11 | Médicament | 20 | Requis si malade (`resultCode -5`) |
| 12 | Bonbon | 💎 dyn. | `GetBonsterCandyPrices` |

## Personnalités & favoris

| Perso | Favoris (IDs) |
|-------|---------------|
| Timide | 1, 2 |
| Sportif | 4, 6 |
| Souriant | 3, 10 |
| Dormeur | 7, 9 |
| Malin | 5, 8 |

## Bonbons

Paliers `{LevelFloor, LevelCeil, CandyPrice}` via `GetBonsterCandyPrices`. Algo `calculateCandyPrice(n)`. Off si n≥100.

## Besoins & XP

| Mécanique | Valeur |
|-----------|--------|
| Déclin barres | −1 pt / 15 min |
| Maladie | 3 jours sans nourrir |
| Barres max | 100 |
| Réponse feed/wash/play | `BonsterInteractionResponse` (XP, level, resultCode) |

## Caressage

`PetFriendBonster(actorId, relId)` → **int SC**. 1×/session/pet côté client. `-429` silencieux.

| Retour | Effet |
|--------|-------|
| `> 0` | SC crédités |
| `0` | Déjà caressé / refus |
| `-429` | Rate limit |

Legacy : `PetFriendPet` — cooldown UI 3000 ms.

## Hôtel

7j/100 SC · 14j/200 · 28j/300 VIP. −50% `SHOPPING_SPREE`.

## Endpoints AMF (détail complet)

→ [amf/07-pets.md](amf/07-pets.md) — chaque endpoint avec paramètres, ticket, codes, rate limits et fichiers client.

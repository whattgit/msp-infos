# I.1 — Sécurité & intégrité AMF

Le client MSP 1 protège les échanges AMF par plusieurs couches indépendantes.

## Vue d'ensemble

| Couche | Rôle | Fichiers client |
|--------|------|-----------------|
| Checksum requête | Intégrité des arguments envoyés | `AmfCall.as`, `ChecksumCalculator.as` |
| Checksum réponse | Détection réponse modifiée (proxy) | `AmfCall.validateChecksum()` |
| TicketHeader | Session + device + token Nebula | `TicketGenerator.as` |
| OS Check | Anti-fraude environnement | `SnapLoader.as`, `AMFOs` |
| Rate limit `-429` | Quotas actions à gain | `RateLimiterController.as` |

## I.1.1 Checksum requête

Chaque appel envoie un header **`id`** = SHA-1(args sérialisés + sel obfusqué).

| Élément | Détail |
|---------|--------|
| Sel | `"Yd*xX#o@B15i@!th"` + permutation dynamique |
| Avec ticket | Prefix ticket + 5 derniers chars |
| Sans ticket | `"XSV7%!5!AX2L8@vn"` |

**Exemptés :** `LogClient`, `GetAppSettings`, `CheckClientFreshness`, `GetCurrentPaymentPossibilities`, `GetRandomLookByLikes`, `GetProfileIds`, `CreateOsRef`, `RunOsCheck`, `EmailValidated`.

## I.1.2 Checksum réponse

Recalcul SHA-1(`[TicketHeader, responseObject]`) vs `serverChecksum`.

| Niveau `AWS_HEX_VALUE` | Comportement |
|------------------------|--------------|
| 1 | Désactivé |
| 2 | Validé, non bloquant |
| 3+ | **Bloquant** |
| 4 | Bloquant silencieux |

## I.1.3 TicketHeader & Nebula

```
Ticket = [MD5 prefix_] + sessionTicket + markingId
Token  = Nebula access token
DeviceId = ID persistant
```

- `markingId` renouvelé à chaque retry AMF.
- Token expiré → refresh Nebula → 1 retry.

## I.1.4 OS Check

1. `CreateOsRef` → `TjData` + `RefId`
2. Histogramme snapshot acteur
3. `RunOsCheck(refId, histogram)` → nouveau refId

Config `ACTIVATE_TIMEZONE_ALIGNMENT` : `WEB`, `MOB`, modes `:E` bloquants. Retry 120 s.

## I.1.5 Modération & logs

| Endpoint | Usage |
|----------|-------|
| `LogChat`, `LogInput` | Journalisation chat |
| `SetMoodWithModerationCall` | Mood modéré |
| `FilterText`, `ReportUser` | Modération texte |

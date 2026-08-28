# I.4 — Protocole AMF

> **FR** · [English](../en/04-protocol.md)


## Format

```
MovieStarPlanet.<Namespace>.<ServiceClass>.<Méthode>(arguments)
```

Le client utilise `AmfCaller.callFunction(nom, [args], needTicket, callback)`.

## File d'attente

| Paramètre | Valeur |
|-----------|--------|
| Concurrence max | 10 |
| Timeout | 20 s |
| Non pausables | CreateOsRef, RunOsCheck |
| Session header | sessionID aléatoire 46 hex chars |

## Flux type

1. Sérialisation args + checksum requête
2. Ajout TicketHeader si sensible
3. Envoi HTTP AMF
4. Validation checksum réponse (niv. ≥3)
5. Callback succès / gestion `-429` / codes métier

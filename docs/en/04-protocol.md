# I.4 — AMF protocol

> **EN** · [Français](../fr/04-protocol.md)

## Format

```
MovieStarPlanet.<Namespace>.<ServiceClass>.<Method>(arguments)
```

The client uses `AmfCaller.callFunction(name, [args], needTicket, callback)`.

## Queue

| Parameter | Value |
|-----------|--------|
| Max concurrency | 10 |
| Timeout | 20 s |
| Non-pausable | CreateOsRef, RunOsCheck |
| Session header | random sessionID 46 hex chars |

## Typical flow

1. Serialize args + request checksum
2. Add TicketHeader if sensitive
3. Send HTTP AMF
4. Validate response checksum (level ≥3)
5. Success callback / handle `-429` / business codes

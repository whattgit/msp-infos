# I.1 — Security & AMF integrity

> **EN** · [Français](../fr/01-security.md)

The MSP 1 client protects AMF exchanges with several independent layers.

## Overview

| Layer | Role | Client files |
|--------|------|-----------------|
| Request checksum | Integrity of sent arguments | `AmfCall.as`, `ChecksumCalculator.as` |
| Response checksum | Detection of modified response (proxy) | `AmfCall.validateChecksum()` |
| TicketHeader | Session + device + Nebula token | `TicketGenerator.as` |
| OS Check | Environment anti-fraud | `SnapLoader.as`, `AMFOs` |
| Rate limit `-429` | Quotas for reward actions | `RateLimiterController.as` |

## I.1.1 Request checksum

Each call sends an **`id`** header = SHA-1(serialized args + obfuscated salt).

| Element | Detail |
|---------|--------|
| Salt | `"Yd*xX#o@B15i@!th"` + dynamic permutation |
| With ticket | Ticket prefix + last 5 chars |
| Without ticket | `"XSV7%!5!AX2L8@vn"` |

**Exempt:** `LogClient`, `GetAppSettings`, `CheckClientFreshness`, `GetCurrentPaymentPossibilities`, `GetRandomLookByLikes`, `GetProfileIds`, `CreateOsRef`, `RunOsCheck`, `EmailValidated`.

## I.1.2 Response checksum

Recalculates SHA-1(`[TicketHeader, responseObject]`) vs `serverChecksum`.

| `AWS_HEX_VALUE` level | Behavior |
|------------------------|--------------|
| 1 | Disabled |
| 2 | Validated, non-blocking |
| 3+ | **Blocking** |
| 4 | Silent blocking |

## I.1.3 TicketHeader & Nebula

```
Ticket = [MD5 prefix_] + sessionTicket + markingId
Token  = Nebula access token
DeviceId = persistent device ID
```

- `markingId` renewed on every AMF retry.
- Expired token → Nebula refresh → 1 retry.

## I.1.4 OS Check

1. `CreateOsRef` → `TjData` + `RefId`
2. Actor snapshot histogram
3. `RunOsCheck(refId, histogram)` → new refId

Config `ACTIVATE_TIMEZONE_ALIGNMENT`: `WEB`, `MOB`, `:E` modes are blocking. Retry 120 s.

## I.1.5 Moderation & logs

| Endpoint | Usage |
|----------|-------|
| `LogChat`, `LogInput` | Chat logging |
| `SetMoodWithModerationCall` | Moderated mood |
| `FilterText`, `ReportUser` | Text moderation |

---
type: Metric
title: Aktive Nutzer (MAU)
description: Definition der monatlich aktiven Nutzer und wie sie berechnet werden.
icon: 📈
tags:
  - metrik
  - produkt
status: stable
generated:
  by: human:Max201203
  at: '2026-09-20T15:01:52Z'
stale_after: '2026-08-01T00:00:00Z'
---

# Definition

Ein Nutzer gilt in einem Kalendermonat als aktiv, wenn er mindestens eine **schreibende** Aktion ausgeführt hat. Reines Lesen zählt nicht.

# Berechnung

```sql
SELECT date_trunc('month', occurred_at) AS month,
       count(DISTINCT user_id)          AS mau
FROM events
WHERE kind IN ('create', 'update', 'delete')
GROUP BY 1
ORDER BY 1 DESC;
```

# Fallstricke

> [!WARNING]
> Service-Accounts sind in dieser Abfrage **nicht** ausgeschlossen. Bei Kunden mit Automatisierung ist die Zahl dadurch zu hoch.

- Testkonten der eigenen Firma sind enthalten
- Zeitzone ist UTC, nicht die des Kunden

> |  |  |  |
> | --- | --- | --- |
> |  |  |  |
> |  |  |  |

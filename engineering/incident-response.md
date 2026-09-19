---
type: Playbook
title: Incident Response
description: Was bei einem Produktionsausfall in welcher Reihenfolge passiert.
tags:
  - oncall
  - incident
  - engineering
status: draft
generated:
  by: human:Max201203
  at: '2026-09-19T11:30:56Z'
---

[TOC]

# Wann dieser Playbook greift

> [!WARNING]
> Nur bei **P1** und **P2**. Bei P3 reicht ein Ticket.

Status der Rufbereitschaft: <span data-status="green">Aktiv</span>

# Sofortmaßnahmen

- [ ] Incident-Kanal eröffnen

- [ ] Incident Lead benennen

- [ ] Statusseite aktualisieren

# Eskalationsstufen

| Stufe | Reaktionszeit | Wer |
| --- | --- | --- |
| P1 | 15 Minuten | Rufbereitschaft + Lead |
| P2 | 1 Stunde | Rufbereitschaft |
| P3 | 1 Werktag | Team-Backlog |

<details>
<summary>Beispiel: Datenbank antwortet nicht</summary>

Erst Verbindungen prüfen, dann Failover:

```bash
kubectl -n prod get pods -l app=postgres
kubectl -n prod exec deploy/pgbouncer -- pgbouncer -R
```

</details>

> [!TIP]
> Fehlerbudget: $B = 1 - \frac{U}{T}$

# Nach dem Incident

> [!NOTE]
> Postmortem innerhalb von 5 Werktagen, schuldfrei.X!

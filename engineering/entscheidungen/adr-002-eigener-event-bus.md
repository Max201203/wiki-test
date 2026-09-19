---
type: Decision Record
title: 'ADR-002: Eigener Event-Bus'
description: Zurückgenommen — wir nutzen seit 2026 einen verwalteten Dienst.
tags:
  - adr
  - engineering
status: draft
generated:
  by: human:Max201203
  at: '2026-09-19T11:38:19Z'
---

> [!CAUTION]
> Diese Entscheidung wurde im März 2026 zurückgenommen. Sie bleibt hier, weil ältere Seiten darauf verweisen.

# Kontext

2025 wollten wir Ereignisse zwischen Diensten übertragen und hielten Kafka für überdimensioniert.

# Entscheidung

Ein eigener Event-Bus auf Postgres-Basis mit `LISTEN`/`NOTIFY`.

# Warum zurückgenommen

- `NOTIFY` verliert Nachrichten, sobald ein Consumer offline ist
- Kein Replay, also kein Wiederaufsetzen nach einem Fehler
- Zwei Entwicklerinnen waren dauerhaft mit Betrieb beschäftigt

Ersetzt durch einen verwalteten Dienst. Die Migration ist in [Deployment](/engineering/deployment.md) beschrieben.

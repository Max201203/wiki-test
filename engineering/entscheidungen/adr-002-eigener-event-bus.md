---
type: Decision Record
title: 'ADR-002: Eigener Event-Bus'
description: Zurückgenommen — wir nutzen seit 2026 einen verwalteten Dienst.
icon: 🧱
tags:
  - adr
  - engineering
status: deprecated
generated:
  by: human:Max201203
  at: '2026-09-27T07:27:10Z'
order: 2
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

Ersetzt durch einen verwalteten Dienst. Die Migration ist in<span style="color: rgb(192, 57, 43);"> </span>[<span style="color: rgb(192, 57, 43);">Deploym</span>ent](/engineering/deployment.md) beschrieben.

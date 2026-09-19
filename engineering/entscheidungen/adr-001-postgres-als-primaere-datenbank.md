---
type: Decision Record
title: 'ADR-001: Postgres als primäre Datenbank'
description: Warum Postgres und nicht MongoDB oder DynamoDB.
icon: 🧱
tags:
  - adr
  - engineering
  - datenbank
status: stable
generated:
  by: human:Max201203
  at: '2026-09-19T11:38:06Z'
verified:
  - by: human:Max201203
    at: '2026-09-19T09:00:00Z'
sources:
  - id: lasttest
    resource: https://wiki.nordlicht/eng/lasttest-2025
    title: Lasttest 2025
order: 1
---

# Kontext

Wir brauchten 2025 eine primäre Datenbank für den Plattform-Monolithen. Erwartet wurden 50 Millionen Zeilen in der größten Tabelle und relationale Abfragen über mindestens vier Entitäten.

# Optionen

| Option | Pro | Contra |
| --- | --- | --- |
| PostgreSQL | Relational, JSONB, Team kennt es | Vertikale Skalierung endlich |
| MongoDB | Flexibles Schema | Joins fachlich nötig, aber teuer |
| DynamoDB | Betrieb entfällt | Zugriffsmuster müssen vorab feststehen |

# Entscheidung

**PostgreSQL 16.** Die Zugriffsmuster standen nicht vorab fest, und genau das schließt DynamoDB aus. Die Lasttests zeigten Reserve bis etwa das Zwanzigfache der heutigen Last.[^lasttest]

# Konsequenzen

- Schemamigrationen müssen abwärtskompatibel sein, siehe [Deployment](/engineering/deployment.md)
- JSONB nur für echte Freiformdaten, nicht als Ausrede für fehlende Modellierung
- Ein Read-Replica-Setup wird nötig, sobald Reports die Schreiblast stören

[^lasttest]: Lasttest 2025

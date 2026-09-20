---
type: Runbook
title: Rollback Runbook
description: Runbook für Rollbacks im Production-Umfeld
tags:
  - engineering
  - rollback
  - runbook
  - oncall
generated:
  by: keel-ai/openrouter/free
  at: '2026-09-20T13:39:22Z'
---

# Auslöser

Ein Rollback wird notwendig, wenn:
- Deployments nach Produktion fehlschlagen
- Smoke-Tests auf Staging oder Produktion fehlschlagen
- Ein kritischer Bug in der aktuellen Version entdeckt wird
- Ein Incident mit hoher Priorität deklariert wird

# Ablauf

## Vorbereitung

1. Incident im Chat kanalisieren und Rollback-Entscheidung dokumentieren
2. Letztes funktionierendes Image identifizieren (SHA-Tag aus CI)
3. Betroffene Services und Namespaces listen

## Ausführung

```bash
# Rollback aller Services im Production-Namespace
kubectl -n prod rollout undo deployment/api --to=<letztes-functionierendes-SHA>
kubectl -n prod rollout undo deployment/web --to=<letztes-functionierendes-SHA>
kubectl -n prod rollout undo deployment/worker --to=<letztes-functionierendes-SHA>

# Status prüfen
kubectl -n prod rollout status deployment/api
kubectl -n prod rollout status deployment/web
kubectl -n prod rollout status deployment/worker
```

## Validierung

- Smoke-Tests auf Produktion ausführen
- Metriken (Fehlerrate, Latenz, CPU) auf Normalniveau prüfen
- Incident im Kanal als gelöst markieren

# Wichtige Hinweise

> [!CAUTION]
> Ein Rollback der Anwendung macht **keine** Datenbankmigration rückgängig. Migrationen müssen immer abwärtskompatibel sein. Bei Datenbankproblemen separates Rollback-Verfahren für die DB anwenden.

# Vernetzung

- [Deployment](/engineering/deployment.md)
- [Incident Response](/engineering/incident-response.md)

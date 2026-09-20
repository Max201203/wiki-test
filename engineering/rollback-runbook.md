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
  at: '2026-09-20T13:40:22Z'
---

title: Rollback Runbook
type: Runbook
status: stable
trust: unverified
tags: engineering, rollback, runbook, oncall

# Auslöser

- Deployment nach Produktion fehlgeschlagen
- Smoke-Tests auf Staging oder Produktion fehlgeschlagen
- Kritischer Bug in der aktuellen Version entdeckt

# Ablauf

1. Letztes funktionierendes Image identifizieren (SHA-Tag aus CI)
2. Rollback aller betroffenen Services ausführen
3. Status prüfen und Smoke-Tests auf Produktion bestätigen

```bash
kubectl -n prod rollout undo deployment/api --to=<letztes-functionierendes-SHA>
kubectl -n prod rollout status deployment/api
```

# Wichtige Hinweise

> [!CAUTION]
> Ein Rollback der Anwendung macht **keine** Datenbankmigration rückgängig. Migrationen müssen immer abwärtskompatibel sein.

# Vernetzung

- [Deployment](/engineering/deployment.md)
- [Incident Response](/engineering/incident-response.md)

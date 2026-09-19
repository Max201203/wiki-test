---
type: Playbook
title: Deployment
description: Wie Code nach Produktion kommt und wie ein Rollback funktioniert.
icon: 🚀
tags:
  - engineering
  - deployment
  - oncall
status: stable
generated:
  by: human:Max201203
  at: '2026-09-19T11:36:50Z'
order: 3
---

# Auslöser

Jeder Merge nach `main`.

# Ablauf

1. CI baut das Image und taggt es mit dem Commit-SHA
2. Deployment nach Staging, automatisch
3. Smoke-Tests auf Staging
4. Freigabe nach Produktion per Knopfdruck

Aktueller Stand der Pipeline: <span data-status="green">Stabil</span>

# Rollback

```bash
kubectl -n prod rollout undo deployment/api
kubectl -n prod rollout status deployment/api
```

> [!CAUTION]
> Ein Rollback der Anwendung macht **keine** Datenbankmigration rückgängig. Migrationen müssen immer abwärtskompatibel sein.

# Verfügbarkeit

Unser Ziel ist eine monatliche Verfügbarkeit von 99,9 %. Das entspricht einem Fehlerbudget von $1 - 0{,}999 = 0{,}001$, also rund 43 Minuten pro Monat.

Bei einem Ausfall gilt das [Incident Response](/engineering/incident-response.md) Playbook.

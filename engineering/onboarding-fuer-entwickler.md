---
type: Guide
title: Onboarding für Entwickler
description: Vom leeren Laptop bis zum ersten Merge — in etwa einem Tag.
icon: 🧭
tags:
  - onboarding
  - engineering
status: stable
generated:
  by: human:Max201203
  at: '2026-09-23T16:11:57Z'
order: 1
---

[TOC]

# Voraussetzungen

- [ ] GitHub-Zugang zur Organisation
- [ ] Docker Desktop installiert
- [ ] Node 22 über `nvm`

# Repository aufsetzen

```bash
git clone git@github.com:nordlicht/platform.git
cd platform
nvm use
npm ci
docker compose up -d
npm run dev
```

> [!TIP]
> `docker compose up -d` startet Postgres und den Event-Bus. Warum wir Postgres nutzen, steht in [ADR-001](/engineering/entscheidungen/adr-001-postgres.md).

# Der erste Merge

1. Branch von `main` abzweigen
2. Änderung klein halten
3. Pull Request öffnen und Review anfragen — siehe [Code Review](/engineering/code-review.md)
4. Nach dem Merge deployt die Pipeline automatisch, siehe [Deployment](/engineering/deployment.md)

# Wenn etwas kaputtgeht

Keine Panik, und nichts heimlich reparieren. Der Ablauf steht im [Incident Response](/engineering/incident-response.md) Playbook.

> [!NOTE]
> In deiner ersten Woche wirst du mit ziemlicher Sicherheit etwas kaputtmachen. Das ist eingeplant.

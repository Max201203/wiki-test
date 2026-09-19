---
type: Policy
title: Passwort-Richtlinie
description: Mindestanforderungen an Passwörter und Zwei-Faktor-Authentifizierung.
icon: 🔒
tags:
  - sicherheit
  - policy
status: stable
generated:
  by: human:Max201203
  at: '2026-09-19T11:38:38Z'
verified:
  - by: human:Max201203
    at: '2026-09-19T09:05:00Z'
stale_after: '2027-03-01T00:00:00Z'
---

# Geltungsbereich

Alle Konten, die Zugriff auf Kundendaten haben.

# Anforderungen

| Anforderung | Wert |
| --- | --- |
| Mindestlänge | 12 Zeichen |
| Zwei-Faktor | verpflichtend |
| Passwortmanager | verpflichtend |
| Erzwungener Wechsel | nein |

> [!IMPORTANT]
> Wir erzwingen bewusst **keinen** regelmäßigen Passwortwechsel. Das führt nachweislich zu schwächeren Passwörtern. Gewechselt wird bei Verdacht auf Kompromittierung.

# Bei Verdacht auf Kompromittierung

- [ ] Passwort sofort ändern
- [ ] Sessions überall beenden
- [ ] Sicherheitsteam informieren
- [ ] Vorfall dokumentieren

Vorgehen im Ernstfall: [Incident Response](/engineering/incident-response.md).

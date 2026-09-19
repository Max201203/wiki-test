---
type: Playbook
title: Eskalation im Support
description: Wann ein Ticket an Engineering geht und mit welchen Informationen.
tags:
  - support
  - oncall
  - eskalation
status: draft
generated:
  by: human:Max201203
  at: '2026-09-19T11:38:41Z'
---

# Auslöser

Ein Ticket wird eskaliert, wenn eine der folgenden Bedingungen zutrifft.

| Bedingung | Stufe |
| --- | --- |
| Kunde kann nicht arbeiten, keine Umgehung | P1 |
| Funktion defekt, Umgehung vorhanden | P2 |
| Kosmetisch oder Einzelfall | P3 |

# Was die Eskalation enthalten muss

- [ ] Kundenname und Vertragsstufe
- [ ] Genaue Uhrzeit des ersten Auftretens
- [ ] Reproduktionsschritte
- [ ] Bereits versuchte Umgehungen

> [!WARNING]
> Eine Eskalation ohne Reproduktionsschritte wird zurückgegeben. Das ist keine Schikane — ohne sie beginnt Engineering bei null.

# Danach

P1 und P2 laufen über das [Incident Response](/engineering/incident-response.md) Playbook.

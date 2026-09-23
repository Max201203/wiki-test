---
type: Guide
title: Code Review
description: Was wir in einem Review erwarten und was ausdrücklich nicht.
icon: 👀
tags:
  - engineering
  - qualitaet
status: stable
generated:
  by: human:Max201203
  at: '2026-09-23T12:17:40Z'
order: 2
---

# Ziel

Ein Review soll Fehler finden und Wissen <span style="color: rgb(180, 83, 9);">verteile</span>n. Es ist kein Stilwettbewerb.

# Erwartungen

| Rolle | Erwartung |
| --- | --- |
| Autor | PR unter 400 Zeilen, Beschreibung erklärt das *Warum* |
| Reviewer | Erste Rückmeldung innerhalb eines Werktags |
| Beide | Diskussion im PR, nicht in privaten Nachrichten |

# Worauf wir achten

- Korrektheit vor Eleganz
- Tests für alles, was schiefgehen kann
- Keine offenen `TODO`s ohne Ticket

> [!WARNING]
> Ein Review ist keine Freigabe der Fachlichkeit. Wenn du unsicher bist, ob das Feature *fachlich* richtig ist, hol das Produktteam dazu.

# Was kein Blocker ist

<details>
<summary>Formatierung</summary>

Das macht der Formatter. Kommentare dazu sind Rauschen.

</details>

<details>
<summary>Persönliche Vorlieben</summary>

"Ich hätte das anders gemacht" ist kein Änderungswunsch. Wenn es wichtig ist, begründe es mit einer konkreten Konsequenz.

</details>

Neue Kolleginnen und Kollegen finden den Einstieg unter [Onboarding für Entwickler](/engineering/onboarding-fuer-entwickler.md).

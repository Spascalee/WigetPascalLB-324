---
name: Anforderung
about: Neue Funktionalität als Anforderung erfassen (Satzschablone)
title: "[Anforderung] "
labels: ''
assignees: ''
---

<!--
Bitte nach dem Erstellen MANUELL genau EINE Typ-Etikette setzen:
  - Funktionale Anforderung  (was das System tun soll)
  - Qualitätsanforderung     (wie gut: Performance, Sicherheit, Usability ...)
  - Randanforderung          (Rahmenbedingungen: Technik, Recht, Budget ...)
-->

## Anforderung (Satzschablone)

**Zielsystem:** <!-- betroffenes (Teil-)System, z. B. "Das Tagebbbuch" -->

**Priorität:** <!-- genau eines: muss (hoch) / soll (mittel) / wird (niedrig) -->

**Systemaktivität:** <!-- genau eines:
  - selbständig:          (keine Zusatzformulierung, z. B. "muss ... speichern")
  - Benutzerinteraktion:  "dem <Rolle> die Möglichkeit bieten"
  - Schnittstelle:        "fähig sein" -->

**Allfällige Ergänzungen:** <!-- Objekt / nähere Angaben, optional -->

**Funktionalität:** <!-- Prozesswort (Verb), z. B. "zu erfassen" -->

**Bedingungen:** <!-- optional; zeitlich mit "wenn", logisch mit "falls" -->

### Ausformulierter Satz

<Zielsystem> <muss|soll|wird> <Systemaktivität> <Ergänzungen> <Funktionalität>, <wenn|falls ...>.

<!-- Beispiel: Reflect Media Player muss dem Benutzer die Möglichkeit bieten,
J3D Szenengraphen aus einer wrml-Datei über das Netzwerk zu laden, falls der Benutzer eingeschrieben ist. -->

## Akzeptanzkriterien / Testfall

- [ ] <!-- woran erkennt man, dass die Anforderung erfüllt ist? Testfall hier verlinken oder einfügen -->

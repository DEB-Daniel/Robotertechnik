---
name: vl-kap07-kooperierende-anwendungen
description: Zusammenfassung VL Kapitel 7 – Anwendungen kooperierender Roboter, logische vs. geometrische Kooperation, Beispiele (Achsschweißen, Prüfen, MRK), Kollisionsschutz
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_07_KooperierendeRoboter.pdf` (22 Folien; blaue Markierungen nur bei Videolinks). Vertiefung in [[vl-kap10-kooperierende-roboter]].

**Kooperationsarten nach Anwendungsfeld (Automobil):**
- **Logische Kooperation:** Teileübergabe ohne Programmsynchronisation, überlagerter Prozess/Remote Commands, Transport mit Ablagen/Puffer; reduziert SPS-Signale, Datentransfer zwischen Steuerungen, flexible Master-/Slave-Zuordnung.
- **Geometrische Kooperation:** direkte geometrische Kopplung, zeitliche/räumliche Koordination (Arbeitsraumverwaltung, Lastteilung/Transport mit mehreren Robotern, koordinierte Bewegung an gemeinsamem bewegtem Bauteil).

**Einsatzgebiete/Beispiele:** Punktschweißen, Lackieren + Bauteilkontrolle, Robotermontage, **synchrones Bahnschweißen** (2 Roboter schweißen zeitgleich an einem durch einen 3. Roboter bewegten Bauteil → ideale Schweißposition, bessere Zugänglichkeit, weniger Vorrichtungen, Mehrfachnutzung der Anlage; Mercedes 2004), **automatische Schweißnahtprüfung** (Laser-Sensor, ersetzt visuelle Werkerprüfung, Nacharbeit durch Roboter, statistische Auswertung; Kooperation logisch + geometrisch), MRK (Bäckerei Yaskawa/UR, Prototypenschweißen UR, Fanuc-Cobots Verpackung), Bauteilvereinzelung „Griff in die Kiste“ (Fanuc iRVision 3D, UR + CNC-Beladung), Etikettieren, Mehrachsschweißmaschine (Yaskawa).

**Kollisionsschutz durch geometrische Kooperation:** Arbeitsräume gegen Betreten durch andere Roboter (mit sicherer Steuerung auch Menschen) verriegeln. Beispiel: Prozessroboter starten erst, wenn Handling-Roboter die Vorrichtung verlassen haben. Anforderungen bei beengtem Platz: (1) Roboter-Roboter-Überwachung im Prozess, (2) Unterbrechung darf bei Wiederanlauf nicht zu Asynchronität/Kollision führen, (3) manuelles Eingreifen + Wiederanlauf ohne Kollision, (4) übersichtliche Programmierung (spezielle Synchronisationsbefehle).

**Zusammenfassung Kap. 7 (Prüfungsantworten):** Typisch: mehrere Roboter arbeiten gleichzeitig nah beieinander oder direkt mit Menschen (Bahnschweißen, MRK-Handhabung, Lackieranlagen). Detailbeispiel: **PKW-Achsschweißen** – 2 Roboter schweißen zeitgleich → symmetrische Wärmeverteilung (weniger Verzug) und Kollisionsvermeidung. **Vorteile geometrischer/logischer Kooperation:** Taktzeit sinkt, Synchronisationsaufwand in der SPS entfällt, Roboter können sehr nah und schnell zueinander fahren, geringeres Kollisionsrisiko, einfachere Programmierung.

**Planspiel-Bezug:** Bei Mehrroboterzellen oder Mensch-Roboter-Zusammenarbeit logische vs. geometrische Kooperation und Arbeitsraumverriegelung als Konzeptoption (und verworfene Alternative) behandeln.

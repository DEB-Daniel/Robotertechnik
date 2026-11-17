---
name: vl-kap01-grundlagen
description: Zusammenfassung VL Kapitel 0/1 – Organisation, Roboterdefinition (DIN EN ISO 8373), Geschichte, Asimov, Cyborg/Android, Roboterarten; blau markierte Folien als prüfungsrelevant gekennzeichnet
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_00_Einleitung.pdf`, `..._01_Grundlagen...pdf`. ⭐ = in den Folien **blau markiert** (laut Dozent prüfungsrelevant; Erkennung teils automatisch, Folien bei Unsicherheit gegenprüfen).

**Kap. 0 Einleitung:** Dozent Dipl.-Ing. Mathias Richter (ex Mercedes, Roboter-Bahnschweißen, Kalibrierung). Lernfelder: Anwendungen, Aufbau, Ausblick, Steuerungskonzept, Wirtschaftlichkeit, Programmierung, Planung und Simulation, Einbindung in die Umwelt, Besondere Eigenschaften, Konzepte, Sensoren & Aktoren, Normativer Rahmen ⭐. Gliederung: 1 Begriffe/Historie, 2 Komponenten/Antriebe, 3 Kinematik, 4 Mathe-Grundlagen, 5 Klassifizierung/Hersteller, 6 Sensorik/Aktorik, 7 Anwendungen, 8 Genauigkeit/Kalibrierung, 9 Programmierkonzepte/mobile Robotik, 10 Kooperierende Roboter, 11 Cobots, 12 Sicherheit, 13 Planung/Simulation, 14 Wirtschaftlichkeit, 15 Trends. Exkursion Mercedes-Werk Mettingen geplant (Sicherheitsschuhe, Fotoverbot, Termin unbestätigt).

**Roboter ist ein Handhabungssystem** ⭐: Handhabungssysteme → manuell gesteuert (Manipulator, Teleoperator) / maschinell gesteuert → fest programmierbar (Einlegegeräte) / **frei programmierbar (Industrieroboter)** ⭐.

**Definition ⭐ (DIN EN ISO 8373 „Roboter und Robotikgeräte – Vokabular“):** Industrieroboter = *automatisch gesteuertes, wiederprogrammierbares, mehrzweckfähiges Handhabungsgerät mit drei oder mehr frei programmierbaren Bewegungsachsen, ortsfest oder mobil in industriellen Anwendungen*. Die 3 Eigenschaften ⭐: **wiederprogrammierbar** (ohne mechanischen Umbau), **mehrzweckfähig**, **mindestens 3 frei programmierbare, unabhängig steuerbare Achsen**. Begriff „Roboter“ von Karel Čapek (RUR, 1920; *robota* = Fronarbeit).

**Historie (⭐ = blau):** Automaten (Vaucanson 1738, Jaquet-Droz 1774, Jacquard-Webstuhl 1805 mit Lochkarten = erster spezialisierter „Roboter“). 1946 Devol Magnetsteuerung; **⭐1954 Devol programmierter Transport (Patent 1961)**; 1956 Unimation (Engelberger = „Vater der Robotik“); 1959 Planet Corp.; 1960 erster Industrieroboter Unimate (hydraulisch); **⭐1961 Unimate bei General Motors**; **⭐1967 Japan**, **⭐1970 Deutschland**; 1973 WAVE (erste Roboter-Programmiersprache); **⭐1973 KUKA „Famulus“, erster IR mit 6 elektromechanischen Achsen**; 1978 SCARA (Makino); 1979 PUMA (elektrisch); 1981 Direct-Drive; 1985 Delta-Roboter (Clavel); **⭐1993 Hochsprache IRL (Norm)**; 1998 PC-Steuerungen und Feldbusse; 2004 DLR-Leichtbauroboter mit Gelenkmomentsensorik; 2007 ROS; 2008 UR5 (erster erfolgreicher Cobot); 2012 Kiva/AMR/SLAM; 2016 ISO/TS 15066 (MRK, Kraft-/Leistungsbegrenzung statt Zaun); 2020–23 Physical AI; 2024–26 Humanoide Welle.
Entwicklungslinien: Kinematik seriell → parallel → nachgiebig/Cobot → biomorph; Aktorik Hydraulik → Elektromechanik+Getriebe → Direktantrieb → Smart Actuator; Sensorik Endschalter/Geber → Torque-Feedback → Vision/LiDAR → Sensorfusion; Software NC/APT → Herstellersprachen (WAVE, IRL, KRL) → ROS → neuronale Policies.

**Asimov-Gesetze ⭐** (hierarchisch): 0. Menschheit nicht schädigen; 1. keinen Menschen verletzen; 2. Befehlen gehorchen (außer Konflikt mit 1); 3. eigene Existenz schützen (außer Konflikt mit 1/2). Haben Einfluss auf heutige Roboterprogrammierung (z. B. Reinigungsroboter).

**Begriffe:** Cyborg = Mischwesen Organismus/Maschine (kein Roboter, kein Android). Exoskelett (ISO 13482) = am Körper getragene mechanische Struktur zur Unterstützung/Verstärkung. **Android ⭐** = Roboter mit menschenähnlichem Aussehen/Verhalten, Unterform des (persönlichen) Serviceroboters; Humanoidität ist Designmerkmal, technische Definition bleibt Wiederprogrammierbarkeit + Achsen.

**Einteilung der Roboter:** nach Konstruktionsweise (stationär, mobil, Laufroboter, rollend, fliegend, schwimmend/tauchend) und Verwendung (Industrie-, Service-, Haushalts-, Medizin-, Erkundungs-, Spielzeug-, Transport-, Militär-, Rettungsroboter), sonstige (BEAM, Schwarm, Nano, bionisch, kognitiv, humanoid, Androiden).

**Planspiel-Bezug:** Definition und 3 Eigenschaften nutzen, um zu begründen, dass die gewählte Zelle ein Roboter im Sinne der Norm ist.

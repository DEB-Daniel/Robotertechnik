---
name: vl-kap04b-programmierung
description: Zusammenfassung VL Kapitel 4b – Roboterprogramm, Programmierarten (online/offline/hybrid), Betriebsarten, Programmiergerät, Bewegungsformen PTP/LIN/CIRC/SPLINE, Überschleifen, RAPID, Programmpflege
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_04_b_Programmierung(...).pdf` (+ `(153)`). Wichtig für den vom Dozenten gewünschten Beispiel-Programmablauf im Planspiel ([[aufgabe-erklaerung-dozent]]).

**Roboterprogramm (ISO 8373):** geordnete Folge von Anweisungen und Daten zur Ausführung einer Aufgabe. Enthält Geometrie/Kinematik (Zielpunkte X,Y,Z,A,B,C, Bezugssysteme Tool/Base, Interpolationstyp), Ablauf/Prozesslogik (E/A, Kontrollstrukturen, Prozessbefehle), Parameter/Limits (Geschwindigkeit, Beschleunigung, Zonen, Lastdaten/Payload). Fehler in der Logik führen zu **physischer Kollision**, nicht nur Software-Crash.
- **Speicher:** persistent (PERS/RETENTIV: Zähler, Teach-Punkte, Kalibrierdaten), global flüchtig (Prozessstatus, Handshake-Flags), lokal (Stack). **E/A:** Eingänge zyklisch per Feldbus (PROFINET, EtherCAT); Ausgänge fallen bei Ausfall/Reboot auf 0 (stromlos) zurück, sofern Aktor nicht bistabil ist. Moderne Plattformen (ROS 2, UR, Unitree): Publisher/Subscriber, YAML-Konfiguration, Watchdogs/Heartbeats mit Fallback (Monitored Stop).
- **Neue Ansätze (Cobots/mobil):** No-Code/Blockprogrammierung (UR Polyscope), XR-Teachen, Demonstrationslernen/Imitation Learning, Natural Language to Code (LLM).

**Programmierarten:**
- **Online** (am Roboter): *Teach-In* (häufigste; Punkte mit Programmierhandgerät anfahren, Pose + Bewegungsform speichern; Vorteil einfach, Nachteil keine Vorab-Simulation, Stillstand); *Playback/Folgeprogrammierung* (Handführung, zyklisches Aufzeichnen, aus Lackierung; viele Punkte, schwer korrigierbar); *Interaktives Teachen/Freedrive* (Cobots, Gravitationskompensation, Direct Teaching + Logik textuell); *Master-Slave/Remote* (Modellroboter, Telerobotik, Lag).
- **Offline (OLP):** textuell, grafisch, Simulation. Herstellertools (ABB RobotStudio, KUKA.Sim, FANUC ROBOGUIDE; virtueller Controller, ≈100 % Taktzeitgenauigkeit) vs. herstellerübergreifend CAD/PLM (Siemens Tecnomatix/Process Simulate, Dassault DELMIA, Visual Components; ≈90 %, Postprozessor nötig).
- **Hybrid (Industriestandard):** Offline-Phase (Digitaler Zwilling, Erreichbarkeit, Takt, Kollision) → Transfer (Rapid, KRL, Karel) → Online-Touch-Up (kritische Punkte im Handbetrieb v ≤ 250 mm/s). Stillstandszeiten −80 %, höchste Genauigkeit; Nachteil: Qualifikation und Pflege des Zwillings.

**Betriebsarten:** Automatik (extern: durch Sicherheits-SPS), **T1** (Teach, sicher reduziert **≤ 250 mm/s**, Zustimmtaste nötig), **T2** (volle Geschwindigkeit, mit Zustimmtaste, möglichst vermeiden, spezielle Berechtigung). Automatik nur mit gesichertem Arbeitsbereich.
**Programmierhandgerät (PHG, KCP):** Betriebsartenwahlschalter, Not-Aus, Display, 6D-Maus (bis 4 Achsen gleichzeitig), Play-Tasten, **Zustimmtaster = Totmannschalter, redundant**, Freigabe der Fahrt in T1/T2. Verfahren: Einzelachsen, TCP-/WELT-/WERKZEUG-/Anwender-Ausrichtung. Alternativen: Laptop mit Herstellertool (RobotStudio, WorkVisual), CAD/OLP-Umgebungen.

**Programmstrukturen:** Bewegungsbefehle, E/A-Zugriff, Logik (FOR/IF/WHILE/REPEAT UNTIL), Interrupts, Unterprogramme, Break/Return/Exit, benutzerdefinierte Befehle (ARC ON).

**Bewegungsformen:** 
- **PTP** (Punkt zu Punkt; alle Achsen gleichzeitig, Geschwindigkeit in %, Pfad nicht definiert, nicht singularitätsanfällig; Grundstellungsfahren, schnelles Positionieren). Synchron (alle Achsen starten/stoppen gleichzeitig, typisch) vs. asynchron (schneller, weniger Rechenaufwand).
- **LIN** (gerade Linie, mm/s, präzise Bahn, singularitätsanfällig; Montage, Fügen), **CIRC** (Kreis über Hilfspunkt; Fräsen, Rohrschweißen), **SPLINE** (glatte Freiformkurven, rechenaufwendig; Lackieren).
- **Überschleifen:** nächste Bewegung beginnt vor exaktem Erreichen des Punktes → kontinuierlicher Übergang, keine Abbremsung; Überschleifdistanz < Punktabstand; Bahn läuft nicht exakt durch den Punkt (Planung beachten). RAPID: `fine` = punktgenau, `z50` = 50 mm Zone.
- **Orientierungsführung:** raumbezogen (ORI 1) vs. bahnbezogen (ORI 2, z. B. Lichtbogenschweißen).
- **RAPID-Befehle:** MoveJ (PTP), MoveL, MoveC, SetDO, WaitTime, WaitDI, TriggL (Trigger an der Bahn).

**Übungsaufgabe (Pick & Place):** Von Home zum zerbrechlichen Bauteil fahren, langsam (max. 20 mm/s) aus Vorrichtung heben; Greifer braucht ≥ 1 s zum Schließen; Signale `doGreifer_Auf`, `diBauteil_vorhanden`, `diGreifer_Auf`, `diGreifer_Zu`. → Muster für den Planspiel-Ablauf (Grundstellung → prüfen → warten → entscheiden).

**Optimale Programmierung:** harmonische Übergänge (Überschleifen), konstante Geschwindigkeit, Ruckvermeidung, passende Koordinatensysteme, Singularitäten vermeiden (Orientierung anpassen).

**Programmpflege in der Praxis:** Korrekturbedarf durch Kalibrierfehler, Bauteiländerungen, Roboteraustausch, Werkzeugverschleiß/Kollision, Vorrichtungsdefekte. Gegenmaßnahmen: zyklische Validierung der Roboterposition mit raumfesten Referenzpunkten, Kanonenstellung (Geber-Kontrolle), zyklische TCP- und Vorrichtungsvalidierung, **Masterbauteile** mit definierten Prozesspunkten. Punktschweißen: >50 % der Bewegungen sind kurz → Beschleunigung wichtiger als Maximalgeschwindigkeit.

**Zusammenfassung Kap. 4:** Achssteuerung über inverse Kinematik + DH + Regelung; Herausforderungen: Singularitäten, Mehrdeutigkeit, Toleranzen, Dynamik, Rechenfehler; KOS: TCP, World, Base; Vorwärts = Winkel → Pose, Rückwärts = Pose → Winkel; DH-Bestimmung durch Konstruktion und Lasertracker; Bewegungsformen PTP, LIN, CIRC, SPLINE.

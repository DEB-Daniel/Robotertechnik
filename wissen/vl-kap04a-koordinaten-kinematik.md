---
name: vl-kap04a-koordinaten-kinematik
description: Zusammenfassung VL Kapitel 4a – Robotersteuerung, Koordinatensysteme, Vorwärts-/Rückwärtskinematik, Mehrdeutigkeiten, Singularitäten, DH-Parameter inkl. Übungen
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_04_a_Koordinatensysteme(...).pdf` (22 Folien) und `(108-125)` (Übungsfolien DH). ⭐ = blau markiert (prüfungsrelevant).

**Achs-/Bahnsteuerung (vereinfacht):** Programm → Bahnvorgabe (kartesische Posen) → **inverse Kinematik mit DH-Parametern** → Achs-Sollwinkel (θ1…θ6) → Achsen-Lageregelung (PID, Regler mit Überwachung) → Antriebe; Ist-Werte der Resolver werden zurückgeführt und mit Soll verglichen. Robotersteuerung besteht aus Rechner, Speicher, Bewegungssteuerung, Achsen-Lageregelung, Kommunikation, Bedienpanel, Peripherie (Sensoren/Aktoren).

**Herausforderungen bei der Ansteuerung:** Singularitäten, mathematische Mehrdeutigkeit, Konstruktions-/Vermessungsungenauigkeiten, Rechenungenauigkeiten, dynamische Fehler.

**Koordinatensysteme ⭐:** Roboterprogramme enthalten entweder absolute Achswinkel oder relative Koordinaten (Translation + Rotation) des TCP in einem Bezugssystem.
- **WORLD** (Weltkoordinaten): fest definiert, meist CAD/Simulation, Bezug für globale Objektpositionen (z. B. Montagestationen).
- **ROOT** (Roboterfuß/Basis): alle Roboterbewegungen relativ zur Basis, Robotermodell (inverse Kinematik).
- **BASE/Bauteil (Anwenderkoordinaten):** auf Werkstück/Bauteil bezogen, relative Programmierung direkt am Bauteil (Schweißen, Bohren).
- **TCP** (Tool Center Point): Arbeitspunkt des Werkzeugs, Rotationspunkt bei Interpolation (Schweißpunkt, Greifpunkt).

**Vorwärtskinematik (direkt) ⭐:** Gelenkwinkel → Pose des Endeffektors; **immer eindeutig**. 2R-Beispiel: X = L1·cosθ1 + L2·cos(θ1+θ2), Y = L1·sinθ1 + L2·sin(θ1+θ2).
**Inverse Kinematik (Rückwärtstransformation) ⭐:** Zielpose → Gelenkwinkel; **mehrdeutig**, meist nur numerisch lösbar (höhere Achsen hängen von vorherigen ab). 6-Achs-Roboter hat oft **8 mathematisch gültige Lösungen (Konfigurationen):** Front/Rear, Ellbogen oben/unten (Up/Down), Flip/Non-Flip (Gelenk 5 wechselt Vorzeichen). Konfiguration muss zu Hindernissen (Zelle) passen; bei Linearbewegungen muss sie während der Fahrt gleich bleiben.

**Singularitäten ⭐:** Konfigurationen, in denen die Bewegung nicht mehr eindeutig bestimmbar ist oder unendlich große Gelenkgeschwindigkeiten nötig wären; Jacobi-Matrix nicht invertierbar. Arten: **Handgelenk (Wrist; A4/A6 kollinear, A5 = 0)** am häufigsten; **Ellbogen** (A2/A3 in einer Linie, Arm gestreckt/eingefaltet); **Schulter** (Handgelenkzentrum auf A1-Achse, Drehung um A1 ändert Hand nicht). Folgen: unkontrollierbare Geschwindigkeiten, unbestimmte Bewegung, Linear-/Kreisbahn durch die Pose unmöglich.

**DH-Parameter ⭐ (Denavit-Hartenberg):** standardisierte Beschreibung einer kinematischen Kette, 4 Parameter je Gelenk: a (Armlänge entlang x), α (Verwindungswinkel um x), d (Gelenkabstand entlang z; variabel bei translatorisch), θ (Gelenkwinkel um z; variabel bei rotatorisch). Transformation D = Tz(d)·Rz(θ)·Tx(a)·Rx(α). **Idealisierte DH** (Konstruktion) vs. **roboterspezifische DH** (durch Kalibrierung, z. B. Lasertracker, gemessen → korrigieren Toleranzen, ermöglichen Absolutgenauigkeit). Achsnummerierung 1 (Grundachse) bis 6 (Handflansch), manche Hersteller SLURBT o. ä. Übungsfolien: DH-Tabellen für 2-/3-/4-Achs-Kinematiken und KUKA-6-Achser (Beispielwerte d0 = 675, a1 = 300, a2 = 650, a3 = −155, d4 = −600, d6 = −140 mm).

**Planspiel-Bezug:** Konfiguration/Singularitäten bei der Platzierung von Bauteilen im Arbeitsraum berücksichtigen; roboterspezifische DH/Kalibrierung für Genauigkeits- und Austauschkonzept (siehe [[vl-kap08-genauigkeit]]).

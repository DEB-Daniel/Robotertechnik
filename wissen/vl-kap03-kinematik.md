---
name: vl-kap03-kinematik
description: Zusammenfassung VL Kapitel 3 – Kinematik, kinematische Kette, Freiheitsgrade/Pose, Bauformen (Knickarm, SCARA, Portal, Delta/Hexapod), Handbauformen, Prozessarmroboter
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_03_Kinematik...pdf`. Blaue Markierungen in diesem Kapitel sind überwiegend Bildbeschriftungen/Videolinks; inhaltlich zentral sind die Definitionen und Vergleichstabellen.

- **Kinematik:** geometrische Beschreibung der Bewegung ohne Kräfte (Gelenkkoordinaten ↔ Pose des Endeffektors, direkte/inverse Kinematik, Koordinatentransformationen).
- **Kinematische Kette:** Glieder + Gelenke, übertragen Bewegung von Basis zum Endeffektor. **Offen** (Industrieroboterarm, seriell) vs. **geschlossen** (Parallel-/Delta-Roboter).
- **Freiheitsgrade:** starrer Körper im Raum hat 6 (3 Translationen + 3 Rotationen). **Pose** = Position + Orientierung, p = (x, y, z, α, β, γ); Position in mm, Rotation (A, B, C) als Eulerwinkel in ° oder Quaternionen (ABB). Für beliebige Lage braucht man ≥ 6 Achsen.
- **Achsarten/Symbole nach VDI 2861:** rotatorisch (R) / translatorisch (T). Einflussfaktoren: Reihenfolge, Lage der Achsen, Anzahl.
- **Strukturen:** seriell, parallel, hybrid. Standard: Portal, Knickarm, SCARA (+ Delta); Sonder: Hexapod u. a.

| Bauform | Achsen | Vorteile | Nachteile / Einsatz |
|---|---|---|---|
| **6-Achs-Knickarm** (RRRRRR) | 6 | flexibel, großer Arbeitsraum, universell (Schweißen, Lackieren, Montage, Handling), kompakt, viele Traglasten | komplexe Steuerung, Wartung, relativ langsam, teuer |
| **SCARA** (RRRT) | 4 | sehr schnell (Pick&Place, Montage), günstig, einfach, gute Wiederholgenauigkeit; steif in Z, nachgiebig in XY (Selective Compliance) | nur 4 FG, begrenzter Arbeitsraum, nur leichte/mittlere Last |
| **Portal/Linear** (TTT) | 3 | hohe Präzision, großer Arbeitsraum, einfache kartesische Steuerung, robust | nur 3 FG, Platzbedarf, langsamer, hohe Installationskosten |
| **Parallel (Delta/Hexapod)** | 3–6 | hohe Präzision/Steifigkeit/Dynamik, geringe bewegte Masse, kompakt | komplexe Steuerung, teuer, kleiner Arbeitsraum, wartungsintensiv; Delta für Pick&Place |

- **Handbauformen:** Zentralhand (sphärisch, ein Achsschnittpunkt, einfache inverse Kinematik, aber Singularitäten), Winkel-/Offsethand (Achsversatz, 9 Lösungen, nicht geschlossen lösbar), Doppelwinkelhand (extreme Bewegungsfreiheit auf engem Raum, geringe Steifigkeit), **Hohlhand (Hollow wrist)** (hohle Achse 6 für Schlauchpaket).
- **7-Achs-Roboter** (z. B. KUKA LBR iiwa, Yaskawa VA1400/VS50): besserer Zugang, kompakte Bewegungen, Redundanz.
- **Prozessarmroboter:** für Prozess optimiert, z. B. Hohlhandroboter fürs Lichtbogenschweißen (ABB IRB 2600ID, KUKA KR … HW, Yaskawa). Medien (Draht, Schlauchpaket) intern durch das Handgelenk → **Lebensdauer des Schlauchpakets ca. 2–10× länger**; weniger Störkontur. Sonderbauformen: Gießerei (Sperrluft, V2A, IP67), Lackierroboter (ABB PixelPaint), Waschanlage.
- **Prozess beeinflusst Design:** Steifigkeit, Umgebungsbedingungen, Genauigkeit, Geschwindigkeit.

**Planspiel-Bezug:** Kinematikwahl begründen (Arbeitsraum, Geschwindigkeit, Genauigkeit, Kosten, Traglast) und mindestens eine verworfene Bauform nennen (z. B. SCARA vs. Knickarm vs. Delta).

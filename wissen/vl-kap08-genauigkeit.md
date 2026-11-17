---
name: vl-kap08-genauigkeit
description: Zusammenfassung VL Kapitel 8 – Genauigkeit (Pose/Absolut, Wiederhol-, Bahngenauigkeit), ISO 9283, Einflüsse, Kalibrierstrategie (TCP, Anwenderkoordinaten, H-Modell), Präzisionsrobotik
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_08_a/b/c_Genauigkeit...pdf`, `8_d_Präzisionsrobotik.pdf`. Zentral für Planspiel-Teile **Kalibrier-/Referenzkonzept** und **Genauigkeitsanforderungen**. Blaue Markierungen im Kapitel: u. a. Definitionen von Positionsgenauigkeit, Wiederholgenauigkeit, Bahnwiederholgenauigkeit, Bahngeschwindigkeit sowie der Hinweis zu DH/Kalibrierung ⭐.

**Normen/Definitionen ⭐ (DIN EN ISO 9283: Leistungskenngrößen von Industrierobotern):**
- **Positionsgenauigkeit (Accuracy, „Absolutgenauigkeit“):** Fähigkeit, einen programmierten Zielpunkt zu erreichen; mittlere Abweichung Soll ↔ Ist im globalen KOS nach Kalibrierung. Typisch ±0,5…2 mm (Industrieroboter oft schlecht); ortsabhängig, im vorderen Arbeitsbereich am besten. Schlechte DH-Parameter → schlechte Positionsgenauigkeit.
- **Wiederholgenauigkeit (Repeatability):** Streuung der erreichten Positionen um den Mittelwert beim wiederholten Anfahren desselben Punktes; typisch ±0,02 mm (sehr hoch); abhängig von Getriebegüte (Spiel, Elastizität) und Anfahrrichtung. Wichtig für Palettieren, Pick&Place, Punktschweißen.
- **Bahngenauigkeit / Bahnwiederholgenauigkeit (Path Accuracy):** Genauigkeit des Folgens einer programmierten Bahn (Hüllschlauch-Durchmesser dBahn); typisch ±1 mm, oft nicht angegeben; wichtig für Lackieren, Kleben, Fräsen, Schweißen; beeinflusst von Last, Geschwindigkeit, Getriebe.
- Weitere: Positionsabweichung, Positionsstabilität (Wandern über Zeit), Bahngeschwindigkeit.
- Kenngrößen aus der Anwendung: **dPunkt** (Punktwiederholgenauigkeit, Kugeldurchmesser), **dBahn** (Hüllschlauch), **dOrient** (TCP-Umorientierungsgenauigkeit: abhängig von Robotermodell/Absolutgenauigkeit; wichtig für Offline-Programme und Wiederanlauf nach Brenner-/Robotertausch), **Absolutgenauigkeit** (kompensiert Toleranzen über roboterspezifischen Parametersatz).
- Beispielanforderungen PKW-Achsen-Bahnschweißen: Umorientierung A4/A5 > 300°/s, A6 > 400°/s, dOrient < 0,6 mm, dPunkt < 0,1 mm, dBahn < 0,6 mm; Absolutgenauigkeit nötig, weil Anlagen digital simuliert werden und Roboter im Defektfall ohne Nachprogrammieren getauscht werden.
- **Dartscheiben-Bild:** hohe Wiederholgenauigkeit + schlechte Absolutgenauigkeit = enge Punktewolke daneben; gute Absolutgenauigkeit + schlechte Wiederholgenauigkeit = breite Wolke um das Ziel.
- Hersteller geben meist nur die Wiederholgenauigkeit eines Punktes an (z. B. KUKA KR4 Agilus 0,02 mm); sagt nichts über Punktgenauigkeit, Bahn oder Geschwindigkeitshaltung. Absolutgenauigkeit selten, Bahnwiederholgenauigkeit manchmal (z. B. ABB IRB 2600ID 0,15 mm). → Für anspruchsvolle Prozesse Voruntersuchung durch den technischen Planer.

**Absolutgenauigkeit ⭐ (DH):** Ein 6-Achs-Roboter braucht 6 × 4 DH-Parameter. Hersteller kalibrieren mit Lasertracker und definierten Lasten/Fahrprogrammen → individuelle optimierte DH-Parameter („Fingerabdruck“), oft als **käufliche Option**; ohne Kalibrierung nur generalisiertes DH-Set (deutlich schlechter); nach Hardwareänderung (Reparatur) ändern sich DH-Parameter ggf. KUKA/ABB: Datensatz je Roboter (ABB ca. 24 Parameter); **Yaskawa nur 6 Kompensationswerte** (25-Punkte-Methode, z. B. Wiest), verbessern Austauschbarkeit, aber begrenzte Absolutgenauigkeit. Ohne Hersteller: Zuliefertools (Wiest LoopIn), eigene Messzelle mit Lasertracker, lokale Kompensation.

**Prozessanforderungen → Genauigkeitsart:** Prozess als **Bahn** (Schweißen, Kleben, Fräsen) → Bahngenauigkeit + Geschwindigkeitsgenauigkeit; Prozess als **Punkt** (Montage, Bestücken) → Wiederholgenauigkeit; **Offline-Programmierung** → Absolutgenauigkeit; geschwindigkeitsempfindlich (Drucken, Lackieren) → konstante Bahngeschwindigkeit; kritische Schaltzeiten (Pick&Place) → schnelles, reproduzierbares Setzen von Ausgängen.
**Einflüsse (negativ):** externe Schlauchpakete (ziehen am Werkzeug), falsche Lastdaten (Werkzeug/Zusatzlasten → schlechte Regelung), hohe Geschwindigkeit/Abbremsen (Roboter nicht unendlich steif), große Trägheitsmomente von Greifern/Vorrichtungen, Arbeit am Rand des Arbeitsraums, große Entfernung Punkt ↔ KOS-Ursprung, hohe Auslastung. Positiv: harmonische Bewegungen, optimales Modell/Absolutgenauigkeit, korrekte Lastdaten, Prozessarmroboter.

**Kalibrierstrategie ⭐ („H-Modell“):** absolutgenauer Roboter → **Vermessungs-TCP** → (Roboter-Roboter-Kalibrierung) → **Arbeits-TCP und Werkobjekte/Anwenderkoordinaten** → Programm erstellen. Reihenfolge strikt einhalten, sonst nach Robotertausch Nachprogrammieren nötig. Erhalt der Genauigkeit: regelmäßige Wartung, regelmäßige Prüfung TCP und Vorrichtung.
- **TCP:** möglichst nah am Prozesspunkt (ggf. 2 TCPs); automatisiert (optisch: ABB BullsEye, Leoni TCP, Wiest ToolIn, KUKA TCP TRACC) oder manuell mit Messspitzen (typisch 4 Punkte XYZ, weitere für Orientierung); Prüfung durch Umorientierung RotX/Y/Z – guter TCP weicht < 0,3 mm ab.
- **Anwenderkoordinaten/Welt:** nah am Prozessort, mehrere Systeme sinnvoll, erst mit perfektem TCP vermessen; manuell 3 Punkte (ORG, X+, X−Y); vor Programmerstellung durch Anfahren von ORG und X/Y prüfen; dokumentierte Positionen/gleiche Strategie, Masterbauteile.
- **Kooperierende Systeme (Roboter-Roboter, Zusatzachsen/Drehtische):** zuerst TCP perfekt, ca. 3 Punkte, Prüfung im gekoppelten Modus; gekoppelte KOS erst nach der Roboterkalibrierung.

**Präzisionsrobotik (Medizintechnik, Luft-/Raumfahrt, Laserschweißen):** Medizin: Mehrkoordinatenmanipulator (MKM) für OP-Mikroskope (Fraunhofer IPA 1995, 6 FG, gewichtsausgeglichen), Mikrochirurgie mit Parallelkinematik (Stewart-Plattform) und optimiertem DH-Modell, da-Vinci. Beispiele für hochgenaue Roboter: Medizin (Positions-/Bahngenauigkeit), Laserschweißen (Bahnwiederholgenauigkeit), Luft-/Raumfahrt (Positionsgenauigkeit).

**Planspiel-Bezug:** Für die Zelle den Prozess als Punkt/Bahn/Offline einordnen, daraus die benötigte Genauigkeitsart und Zahlenwerte ableiten, Datenblatt richtig lesen (Wiederhol- ≠ Absolutgenauigkeit) und ein Kalibrier-/Referenzkonzept nach dem H-Modell inkl. Robotertausch beschreiben.

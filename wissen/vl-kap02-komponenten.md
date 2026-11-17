---
name: vl-kap02-komponenten
description: Zusammenfassung VL Kapitel 2 – Komponenten Roboter/Zelle, Normbegriffe, Antriebsstrang, Wegmesssysteme, Motoren, Getriebe (Harmonic Drive, Cyclo); blaue Folieninhalte markiert
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_02_Komponenten...pdf`. ⭐ = blau markiert (prüfungsrelevant).

**Roboterzelle ⭐ (5 Elemente):** 1 Industrieroboter, 2 Endeffektor, 3 Steuerungstechnik (Anschluss an SPS, Sicherheitssteuerung, überlagerte Leittechnik z. B. SAP), 4 Peripherie (Vorrichtungen, Zuführ-, Vereinzelungs-, Bereitstellungseinrichtungen), 5 Sicherheitstechnik (Zäune, Türen, Lichtschranken).

**Komponenten des klassischen Roboters ⭐ (Begriffe nach DIN EN ISO 8373:2022-04):** Manipulator (mechanische Struktur aus gegeneinander beweglichen Segmenten), Segment, Achse (Motor + Getriebe + Messtechnik), Hand, Handflansch, Endeffektor (Greifer/Werkzeug, am Handflansch), **TCP** (Tool Center Point: Arbeitspunkt am Endeffektor, Lage+Orientierung bezogen auf Handflansch-KOS), Steuerung (inkl. Regelung; Bahnplanung, Koordinatentransformation, Antriebsregelung), Programmiergerät (z. B. KCP), Anschlussleitungen (Energie + Signale), Bussystem (deterministisch, Echtzeit), Peripherie: Leittechnik, Aktorik, Sensorik, Sicherheit.

**Umgangssprachliche Segmente ⭐:** Fuß/Sockel (fest) → Karussell (A1) → Schwinge (A1–A2) → Oberarm (A2–A3, Schulter A2) → Unterarm (A3–A4, Ellbogen A3) → Handwurzelgehäuse (A4–A5, Antriebe der Orientierungsachsen) → Hand → Handflansch (A6, mechanische Schnittstelle zum Effektor). KUKA: Gewichtsausgleich (hydropneumatisch) minimiert Drehmomente.

**KUKA-Meilensteine:** 1973 Famulus; erster Roboter ohne Parallelogramm; offene PC-Steuerung; kooperierende Roboter; Safe-Robot; KUKA Titan 1300 kg; erster „fühlender“ Roboter (Kraft-Momenten-Sensoren); KR C4 mit integriertem Sicherheitskonzept.

**Antriebsstrang ⭐:** Steuerung/Bahnplanung → (Soll-Werte) Leistungselektronik → Motor → Getriebe → Manipulator; Messsystem liefert Ist-Werte zurück. Elektrische Antriebe > 85 % (D), Hydraulik < 15 % (Sonderlösungen). Der Antrieb bestimmt Leistungsdaten und Preis.

**Wegmesssysteme:** meist am Motor (Antriebsseite); müssen mehrere Umdrehungen erfassen. Typen: Hall-Sensoren, Resolver (induktiv), optische Geber (sehr genau). **Inkrementalgeber** liefern Impulse je Winkeländerung (zählen, Referenzfahrt nötig); **Absolutgeber** liefern eindeutigen Winkel pro Umdrehung (Bitmuster, Gray-Code: benachbarte Werte unterscheiden sich um 1 Bit → max. 1 Bit Lesefehler), nach Stromausfall sofort Position bekannt. Optisch = berührungslos, verschleißfrei.

**Motoren ⭐:** AC-Synchron (Servo) in Industrierobotern (extreme Bahngenauigkeit, hohe Haltekräfte). Vorteile: hohe Dynamik, Leistungsdichte, wartungsarm, kleines Läufer-Trägheitsmoment, hohes Spitzenmoment, guter Rundlauf, integrierter Geber, Haltebremse, IP54/IP65. AC-Asynchron: Förderbänder (robust, nicht millimetergenau); DC bürstenbehaftet: Hobby (billig); BLDC: Drohnen (Leistung/Gewicht).

**Getriebe ⭐:** kraftschlüssig (Schlupf) ungeeignet für Roboterachsen; **formschlüssig**: Kettengetriebe, Riemengetriebe (Zahnriemen), Rädergetriebe (Stirnrad, Planeten, Kegelrad, Schnecke), Sonderbauarten **Cyclo, Harmonic Drive**. Anforderungen ⭐: Torsionssteifigkeit, geringes Spiel (Backlash), schwingungsarm, belastbar, haltbar, temperaturunabhängig, hohe Kraftmomente, guter Wirkungsgrad.
- **Harmonic Drive:** Wave Generator (Eingang) – Flexspline (elliptisch verformt, n−2 Zähne) – Circular Spline (starrer Außenring). Spielfrei, steif, kompakt, 50:1–320:1 einstufig; in Handachsen und Leichtbauroboter/Cobots.
- **Cycloid (Cyclo):** Exzenterwelle – Zykloidscheiben (n−1 Zähne) – Bolzenring – Abtrieb. Schockbelastbar (bis 5× Nennmoment), extrem steif, spielarm, 50:1 bis >100:1; in hochbelasteten Grundachsen A1–A3.

**Planspiel-Bezug:** Zellenaufbau (5 Elemente) als Gliederung der Zelle; Antriebs-/Gebertyp und Kalibrier-/Referenzkonzept (Absolut- vs. Inkrementalgeber, Referenzfahrt nach Austausch).

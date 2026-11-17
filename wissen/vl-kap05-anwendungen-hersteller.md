---
name: vl-kap05-anwendungen-hersteller
description: Zusammenfassung VL Kapitel 5 – Kernaufgaben von Robotern, anwendungsspezifische Auslegung, Branchenbeispiele, Einteilung nach Fähigkeiten, Hersteller (ABB, KUKA, Fanuc, Yaskawa, UR, NEURA), Markt/Statistik
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_05_a_Aufgaben_und_Einteilung.pdf`, `05_b_Beispiele_Hersteller.pdf`, `05_c_AlleBeispiele.pdf` (05_c enthält überwiegend die Beispielfolien aus 05_a/05_b noch einmal). ⭐ = blau markiert.

**Leitfragen & Antworten (Kap. 5):**
1. **5 Kernaufgabengebiete ⭐:** Handhaben, Schweißen, Montieren, Auftragen, Bearbeiten.
2. Aufgaben beeinflussen Konstruktion: Sensorik, Geschwindigkeit, Dynamik, Genauigkeit, Traglast, Sicherheit werden aufgabenspezifisch ausgelegt.
3. Beispiele: Lego-Entertainment, Solarzellenfertigung (Löten, Mikroskopführung), Eierverpackung, Palettieren von Bananen, Entgraten.
4. **Einteilung nach Fähigkeiten ⭐:** bahngesteuerter → adaptiver → mobiler → autonomer Roboter (steigender Autonomiegrad; Industrieroboter: Vorbestimmtheit, Automatik, automatengerechte Umgebung; Serviceroboter: Weltmodell, Sensorfusion, Planung, Lernfähigkeit; Personal Robot: Kommunikation, Öffentlichkeit).
5. **Hersteller (Deutschland/International):** **ABB** (Lackieren, Schweißen, kooperierende Systeme, universell, stark in OLP/Mehrrobotersteuerung MultiMove), **KUKA** (Augsburg; universell, Schweißen, Handling, MRK, Automobil/Luftfahrt; offene PC-Steuerung, KRL), **Yaskawa/Motoman** (Bahnschweißen, Handling, MultiRobot-Technologie, Servoantriebe), **Fanuc** (Massenfertigung, sehr zuverlässig, proprietäre Steuerung, KAREL). Zusammen ca. 38 % Weltmarkt (2024). Neue: **Universal Robots** (2005, Odense, Teradyne; Cobots, einfach programmierbar, KMU), **NEURA Robotics** (2019, Metzingen; kognitive Robotik, KI, 3D-Sensorik).
6. **Marktentwicklung:** stetig steigende Installationen, neue Felder in allgemeiner Industrie wachsen stark, kollaborierende Roboter nehmen zu. Zahlen: Markt 2023 ca. 55,2 Mrd. USD, 2033 prognostiziert 163,9 Mrd. USD (CAGR 11,5 %); APAC ~66 %, Europa 17 %, Nordamerika 16 %. Bestand 2023: 4,28 Mio. IR weltweit (269.427 in Deutschland), 541.000 Neuinstallationen. Roboterdichte (Roboter pro 10.000 Beschäftigte): Südkorea 1.012 (Spitze), Deutschland weit oben.

**Auslegungsarten:** *Universalroboter* (Standardanwendungen, Varianten bei Nutzlast/Beweglichkeit/Arbeitsraum, große Stückzahlen, z. B. KR500-3) vs. *anwendungsspezifischer IR* (integrierte Prozessfunktion, vorkonfigurierte Zellen, mittlere Stückzahlen, z. B. Palettierer). Beispiele spezifischer Auslegung: Messen/Qualitätskontrolle (hohe Präzision, integrierte Sensoren, 5–6 FG), Laborautomation (preisgünstig, Tischgeräte, 3–5 FG, geringe Last), Pressenverkettung (bis 500 kg), Schweißen (Schnittstellen zu Werkzeugen, Nahtverfolgung, gewichtsbalanciert, OLP), Unterhaltung (hohe Beweglichkeit, leise, sichere MRI), Service/mobil (Sensorfusion, 24/7, Schwarm).

**Branchenbeispiele:** Automotive (Rohbau Punktschweißen/Kleben, Lackieren, Montage schwerer Teile z. B. Hybridbatterie MRK; Einstieg der IR in D über Punktschweißen im Fahrzeugbau wegen Großserie, automatisierungsgerechter Konstruktion), Elektro (Solarzellen löten), Metall (Schleifen, Entgraten, Fräsen), Kunststoff/Chemie/Medizintechnik (Reinraum, Rückverfolgbarkeit), Lebensmittel (Kommissionieren, Verpacken; hygienische/prozessuale/technische Herausforderungen; Entbeinen mit Vision + Kraft-Momenten-Sensorik), Getränke (Depalettieren Fässer, Laserscanner, ~100 % Verfügbarkeit), Versandhandel (Packen, Palettieren gemischter Packstücke), Service (Bodenreinigung: Mehrkosten max. ca. 10 T€ gegenüber manuell; H2-/Tankroboter: Problem ist Standardisierung der Schnittstelle Tankverschluss), Zusatzachsen (Überkopfmontage: Arbeitsraum +30 %, Linearachsen/Dreheinheit).

**Hersteller-Vergleich (Systeme):** KUKA offen/PC-basiert (KRC, Sunrise, KRL/Java, bis 16 IR × 18 Achsen), ABB (IRC5/OmniCore, RAPID, MultiMove, bis 4–6 Roboter nativ, bis 3 externe Achsen), Fanuc (R-30iB, KAREL, TP-Programmierung, 4–5 Roboter), Yaskawa (DX200/YRC, INFORM, bis 8 Roboter, MotoCOM SDK).

**Planspiel-Bezug:** Zelle einer der 5 Kernaufgaben zuordnen; Universal- vs. anwendungsspezifischer Roboter und Herstellerwahl begründen (Programmierbarkeit, Mehrroboter, Offenheit, Kosten).

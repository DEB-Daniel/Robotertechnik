---
name: vl-kap09-programmierkonzepte-assistenz
description: Zusammenfassung VL Kapitel 9 – Relativbewegungen (RelTool), Tool-/Welt-KOS, raumfester TCP, Zusatzachsen, hängende Roboter, Assistenzsysteme, mobile Systeme/FTS
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_09_a_Programmierkonzepte(...).pdf`. Ergänzt [[vl-kap04b-programmierung]].

- **Werkzeug-KOS/TCP:** liegt am Werkzeug (z. B. Spitze), Lage (Verschiebung + Drehung) relativ zum Flansch der Achse 6.
- **Relativbewegungen (z. B. ABB RelTool):** Zielpunkte nicht absolut, sondern als Verschiebung/Drehung vom aktuellen Punkt bzw. relativ zum Werkzeug (z. B. RelTool(−z) zum Abheben).
- **Raumfester TCP (externes Tool):** Bezugspunkt an fester Station/Werkzeug, Roboter bewegt das Bauteil relativ dazu (z. B. stationäre Schweißzange, wechselnde Werkzeuge).
- **Zusatzachsen:** Linearfahrbahn +1 FG, Drehachse +1 FG, Drehkipptisch +2 FG; erweitern die Pose und werden von der Bahnplanung berücksichtigt.
- **Hängende Roboter:** Welt-KOS wird entsprechend angepasst positioniert.
- **Assistenzsysteme (Mensch-Roboter-Arbeitsteilung bei überlappendem Arbeitsraum):** sichere, flexible, wirtschaftliche Zusammenarbeit; intuitive Kommunikation (Sprache, Haptik, Grafik), Szenenanalyse, Lernfähigkeit/Adaptivität, gemeinsame Bewegungsplanung. Beispiele: Produktionsassistent, handgeführte Cockpitmontage (KUKA LeanFit: 7. Achse, Joystick/Display, Not-Aus, SafeRobot-Technologie mit überwachter TCP-/Achsgeschwindigkeit, Beschleunigung, Achsbereich, Stillstand), Haushaltsassistenz, **mobile Transportagenten/FTS/AMR** (flexibler Materialfluss, Deadlock-Auflösung, kooperative Aufgabenvergabe).
- **Zusammenfassung Kap. 9:** Zusätzlich zu PTP/LIN/CIRC/Spline: Relativbewegung. Zusatzachsen = erweiterter Freiheitsgrad. Hängende Roboter: Welt angepasst. Assistenzsystem: Interaktion mit Umwelt, Detektion des Werkers, sichere Zusammenarbeit (Produktionsassistent, AMR, FTF).
- Wiederholung in der Folie: Kalibrierstrategie (Absolutgenauer Roboter → Vermessungs-TCP → Roboter-Roboter → Arbeits-TCP/Werkobjekte → Programm), siehe [[vl-kap08-genauigkeit]].

---
name: vl-kap-fallstudien
description: Zusammenfassung der Fallstudien 1–4 (ohne Lösungen) aus der Vorlesung – Achsträger-Zelle mit 60-s-Takt, Karosserie-Synchronisation, Roboterteam-Montage
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_F_Fallstudien1-4(ohne).pdf` (Lösungsfolien sind leer). Dient als Vorlage für die Methodik des Planspiels (Weg wichtiger als Lösung; keine eindeutige Lösung, Musterlösung gibt der Dozent). Siehe auch [[vl-kap13-planung]].

**Fallbeispiel 1 – Fertigungszelle für PKW-Achsen (Taktzeit- und platzoptimal):** Anbauteile werden an einen spiegelsymmetrischen Achsträger (ca. 1,2 m breit, 0,6 m tief; 2 Seitenteile, 2 Querbrücken, 2×3 Lagerböcke) geschweißt. Ziel-Takt **60 s**; bestehende Zelle mit 2 Robotern auf externer Achse in geometrischer Kooperation hat ca. 150–155 s; Kosten (CapEx/OpEx) minimieren; Prozessgeschwindigkeit 1,2 m/min (20 mm/s). Nahtnummerierung links ungerade, rechts gerade (z. B. N101 175 mm, N103 155 mm, N105 85 mm, N107 25 mm).
Fragen: Synchronität der Roboter sicherstellen? Was passiert bei minimaler Bahnabweichung? Methoden zur Kollisionsvermeidung? Rolle der Steuerungsarchitektur (ABB MultiMove)? Schrittfolge Greifen → Positionieren (5–7 Schritte), Störungen und Korrekturen.
Teilaufgaben: (1) Nahtplan (Tabelle der Bahnen), Vorgaben prüfen, Grundkonzept (Robotertyp, Anzahl, Layout: Bauteil fest/beweglich/vom Roboter gehalten); (2) Prozesslogik und Taktzeit je Schritt (Positionieren, TCP-Kalibrierung/-Prüfung, Reinigen, Seitenwechsel, Zünden + Endkraterfüllung ≈ 1,5 + 0,5 s, Teil/Lagerböcke einlegen (Werker nimmt 3 Lagerböcke auf einmal), Nahtzustellen, Tür auf/zu, Entnehmen; manuell vs. automatisches Be-/Entladen); (3) Sicherheit optimieren; (4) Steuerungstechnik optimieren; (5) Konzepte für 60 s erarbeiten und Output/CapEx/OpEx vergleichen; (6) Lösungsvorschlag ~60 s; (7) Konzeptvergleich nach Platz und Kosten.
Positionierer-Typen: Linearachsen/L-Positionierer, Drehachsen, H-Tische/„Heuwender“ (KUKA 2 Stationen), Y-Tische (Yaskawa), Sonderbauformen X-Tische (ABB, KUKA), Yaskawa RWV3 (3 Stationen reversierend); typische Spannrahmen 2000 × 1000 mm, ca. 1 t.
**Fallbeispiel 3 – Synchronisation im Karosseriebau:** Drei ABB-Roboter greifen gleichzeitig ein großes Karosserieteil und setzen es in eine Montagevorrichtung ein (Engineering-Plan, Diskussion des Lösungsansatzes).
**Fallbeispiel 4 – Robo-Team in der Fügetechnik:** Zwei Roboter montieren gemeinsam eine Achse: A hält das Werkstück, B schraubt und prüft. Fragen: Probleme (technisch/organisatorisch), Kommunikation/Koordination, nötige Sensoren und Steuerungsstrategien, Vorteile eines Roboteams; Ergebnis: Problem-/Lösungsliste und Koordinationsablauf in 3–5 Schritten.
(Fallbeispiel 2 entspricht inhaltlich dem Kühlschrank-/Achsbeispiel aus Kap. 13: MRK in der Kleinserienfertigung bzw. Zellenentwurf.)

**Planspiel-Bezug:** Gleiche Vorgehensweise übertragen: Prozess in Schritte mit Zeiten zerlegen, Konzeptvarianten (Anzahl Roboter, fester/beweglicher Tisch) vergleichen nach Takt, Platz, CapEx/OpEx, Sicherheit und Steuerungstechnik, Störungen und Korrekturen benennen.

---
name: sicherheit-scram-konzept
description: Sicherheitskonzept und SCRAM-Analyse der Retouren-Zelle (Entwurf) – gewählte Schutzvariante, verworfene Varianten, kritische Szenarien, Sicherheitsfunktionen
metadata:
  type: project
---

Ausarbeitung: `docs/sicherheit-scram.md` (Rolle Sicherheit & SCRAM, Stand 23.11.2026, **Entwurf [KI]**, E/S-Einstufungen sind Schätzungen). Grundlage: [[vl-kap12-sicherheit]], [[vl-kap10-kooperierende-roboter]], [[vl-kap13-planung]], [[vl-kap06-sensorik-aktorik-schnittstellen]]. Use-Case: [[use-case-retouren]].

**Vorschlag V4:** überwachte Zelle ohne Vollzaun. Der AMR fährt nur in einem festen Korridor; Speed & Separation über Scanner (Warnfeld → ≤ 250 mm/s, Schutzfeld → sicherer Stopp); Behälterwechsel über Durchreichen von außen; Öffnungsmesser gekapselt mit Zuhaltung und Lichtgitter; „Fahren XOR Greifen“; Personenschutz über zweikanalige Safe-SPS. Gegliedert nach dem 3-Stufen-Prinzip (inhärent → technisch → organisatorisch).
**Verworfen:** V1 Vollzaun (Mobilität sinnlos, Stillstand bei jedem Wechsel), V2 Mischverkehr in der ganzen Halle (E hoch), V3 nur Cobot-PFL (schützt nicht vor scharfen Artikeln und Messer).
**Kritische Situationen (SCRAM):** S1 Mensch im Fahrbereich (K → L), S2 beschädigter Li-Akku in der Retoure (K → M, Quarantänebehälter Q + Thermoüberwachung), S3 Paketstau am Öffnungsmodul (H → L). Weitere: KI-Fehlklassifikation (im Zweifel → „Prüfung Mensch“), Scanner verschmutzt, WLAN-Ausfall (Sicherheit lokal, nicht über WLAN), Cyber-Security.
**Matrix-Zuordnung** E (selten/gelegentlich/häufig) × S (leicht/mittel/schwer/katastrophal) → L/M/H/K ist eine eigene Annahme [KI], da die Folien keine feste Tabelle vorgeben.

**Offen:** Team-Bestätigung von V4; Behälter Q als 4. Ziel; Öffnungstechnik; max. Artikelgewicht; Gegenprüfung durch Optimist/Pessimist und durch die nächste Person in der Sicherheitsrolle.

**Why:** SCRAM und Sicherheitsbewertung sind Bewertungskriterium und laut Dozent klausurrelevant; die Sicherheitsrolle darf Entscheidungen blockieren.
**How to apply:** Bei Layout, E/A und Ablauf die Sicherheitsfunktionen SF1–SF9 und die Signalliste aus Abschnitt 8 der Ausarbeitung übernehmen. Nach Teamentscheidung den Status hier und im [[entscheidungslog]] aktualisieren.

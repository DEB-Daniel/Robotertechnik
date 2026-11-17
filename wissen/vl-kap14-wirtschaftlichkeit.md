---
name: vl-kap14-wirtschaftlichkeit
description: Zusammenfassung VL Kapitel 14 – Roboterökonomie, CapEx/OpEx/TCO, ROI, Payback, NPV, IRR mit Formeln und Rechenbeispielen, Kostenstruktur, Sensitivität, Bewertungsvorgehen
metadata:
  type: reference
---

Quelle: `Vorlesung/VL_HSE_WS2026_14_Wirtschaftlichkeit.pdf`. Grundlage für die **qualitative Kosten-Nutzen-Abwägung** (Invest, Betrieb, Schulung, Engineering) im Planspiel. Ergänzt [[vl-kap13-planung]].

**Leitfragen & Kernantworten:** (1) **CapEx** = einmalige Investition zu Projektbeginn (Roboter, Peripherie/Greifer/Schutz, Integration, Schulung; aktiviert und abgeschrieben); **OpEx** = laufende Betriebskosten (Wartungsverträge, Ersatzteile, Energie, Material, Bedienpersonal, Software-Lizenzen; sofort Aufwand in der GuV). (2) **Eisberg-Modell:** Anschaffungskosten (CapEx) sind nur die sichtbare Spitze, verdeckte Kosten (OpEx) über 7–10 Jahre Lebensdauer sind erheblich → **TCO** = CapEx + Σ OpEx_t (Erlöse/Einsparungen nicht enthalten). (3) Ziele von Unternehmen: Kostenreduktion (Lohn, Nacharbeit, Ausschuss), Produktivität (24/7, kürzere Zyklen), Qualität/Konsistenz/Nachverfolgbarkeit, Flexibilität/Wettbewerbsfähigkeit (Losgröße 1), Sicherheit/Ergonomie, neue Geschäftsmodelle. Unternehmen handeln ökonomisch, nicht technisch ideal.

**Kennzahlen ⭐ (Formeln):**
- **ROI** = (Einsparungen − Betriebskosten) / Investition (= jährlicher Netto-Nutzen / Investition); Beispiel 80.000 € Investition, 40.000 €/Jahr Nutzen → ROI 50 %; ROI ist nicht Payback und nicht Break-even.
- **Amortisationszeit (Payback)** = CapEx / jährlicher Netto-Cashflow (Beispiel 400.000 / 200.000 = 2 Jahre); ignoriert Zeitwert des Geldes.
- **NPV (Kapitalwert)** = −CapEx + Σ_t C_t / (1+r)^t; NPV > 0 ⇒ wirtschaftlich (absolute Wertschöpfung).
- **IRR** = Zinssatz mit NPV = 0; Vergleich mit Kapitalkosten (WACC).
- Jährliche Einsparung ΔC = C_manuell − C_Roboter; Payback = CapEx/ΔC.
- ROI und Payback allein reichen nicht; niedrige OpEx und günstiger Zins sind Voraussetzung für hohe Wirtschaftlichkeit (Sensitivitätsbeispiele: ROI 0,375/Payback 2,7 J/NPV +249 k€; ROI 0,13/PB 8 J/NPV −183 k€).

**Nutzenquellen:** Lohnkosteneinsparung (FTE inkl. Sozialabgaben/Overhead), Produktivität/Mehrausbringung, Qualität (weniger Ausschuss, bis −30 %), Verfügbarkeit/weniger Unfälle, neue Erlösquellen/Services. Weitere Aspekte: **Industrie 4.0** (Predictive Maintenance spart 10–40 % Kosten und 25–35 % Zeit [McKinsey], Losgröße-1/Mass Customization, digitale Zwillinge), Ethik/Recht (Haftung, Datenschutz bei Kameras, Nachhaltigkeit/Energie, Normen ISO 10218, TS 15066, CE). Energie: Standby-/Energiesparfunktionen (ProfiEnergy: Standby 2–30 %, Standby 3 bis 80 % Einsparung).

**Kostenstruktur (Anhaltswerte):** Roboterarm 25–150 k€ (20–30 % CapEx), Peripherie & Integration 50–250 k€ (40–50 %), Programmierung & Inbetriebnahme 50–150 k€, Schulung & Prozessanpassung 10–100 k€ (5–10 %). OpEx: Wartung 5–10 % der Anschaffungskosten p. a., Energie ca. 1–3 k€/Jahr (3–7 kWh/h), Ersatzteile/Updates, Stillstandskosten. TCO über 7–10 Jahre: CapEx 135–650 k€, OpEx 50–200 k€/Jahr. Cobots/kleine Systeme: CapEx ca. 20–50 k€, geringere Integration, oft Amortisation < 2–3 Jahre.
**Hebel zur Optimierung:** CapEx: weniger Hersteller-/Typenvielfalt, standardisierte/schlüsselfertige Anlagen; OpEx: eigene Instandhaltung, langlebige Hardware, energieeffizient (Pneumatik ist teuer), Tooling/Software-Kosten, vorbeugende Wartung. Größte Stellschrauben: Zahl ersetzter FTE, Auslastung/Zykluszeit, Integrationsaufwand (CapEx), Zins, OpEx.

**Bewertungsvorgehen (Dozenten-Checkliste) ⭐:** 1 Use-Case präzise definieren (Aufgabe, Laufzeit, Takt) → 2 alle CapEx-Positionen und realistische OpEx (nicht sparen) → 3 Netto-Jahresnutzen (Lohnersparnis ± Qualitäts-/Durchsatzeffekte − zusätzliche OpEx) → 4 Diskontsatz (WACC) wählen, NPV/IRR/Payback berechnen → 5 Sensitivitätsanalyse (z. B. ±20 % Lohnkosten, ±10 % Downtime, andere Zinssätze) → 6 Non-Financial-Faktoren (Flexibilität, Time-to-market, Sicherheit, soziale/organisatorische Kosten, Risiken wie Ausfälle, Integrationsprobleme, Lieferketten).

**Rechenbeispiele:** *A Pick & Place:* I0 = 80.000 €, OpEx 5.000 €, ersetzt 1 FTE (45.000 €) → Netto 40.000 €/Jahr, 8 Jahre → Payback 2 Jahre, NPV(5 %) 178.529 €, NPV(8 %) 149.866 €, NPV(12 %) 118.706 €, IRR ≈ 47,8 %. *Komplexe Schweißzelle:* CapEx ≈ 400.000 € (2 Roboter à 80 k€, Positionierer 40 k€, 2 Stromquellen 24 k€, Zäune/Vorrichtungen 40 k€, Integration/Programmierung/Schulung 80 k€, gerundet), OpEx ≈ 48.000 €/Jahr (Wartung 5 % = 20 k€, Energie 3 k€, Verbrauchsmaterial 10 k€, Ersatzteile 15 k€), manuell 4 Schweißer × 53 k€ + 25 k€ + 10 k€ = 247 k€; Roboter 1 Operator 53 k€ + 48 k€ = 101 k€ → Einsparung 146.000 €/Jahr → Payback ≈ 2,74 J, NPV(8 %, 8 J) ≈ 439.009 €, IRR ≈ 32,7 %. Sensitivität: Nutzen −20 % → Payback 3,4 J; CapEx +25 % (500 k€) → 3,42 J; OpEx +50 % → 3,28 J. Praxis: Amortisation < 1 bis ca. 3 Jahre bei Serienfertigung.

**Planspiel-Bezug:** Qualitative Abwägung Invest/Betrieb/Schulung/Engineering mit CapEx-/OpEx-Struktur, Eisberg-Argument und mindestens einer Sensitivitätsüberlegung; grobe Zahlen als `[KI]` kennzeichnen ([[ki-kennzeichnung]]).

# Planspiel – Ergebnisse (Sammeldokument fürs Team)

**Use-Case:** Mobiler Roboter zum Sortieren von Retouren **[KI]**. Ein mobiler Manipulator mit Hybridgreifer entnimmt Artikel aus automatisch geöffneten Rücksendungen, erkennt sie per Kamera, Barcode/RFID und KI und sortiert sie in „wieder verkaufen“, „Prüfung durch Mensch“ oder „Entsorgung“.

## So tragt ihr ein

1. Unter **eurem Arbeitspaket** eine Zeile in der Tabelle anlegen, mit Name, Datum, Status und Kurzfassung.
2. Längere Ausarbeitungen kommen als **eigene Datei in `docs/`** und werden hier nur verlinkt (z. B. `docs/sicherheit-scram.md`).
3. Status: `Entwurf` → `im Team besprochen` → `final`.
4. KI-Inhalte mit **[KI]** kennzeichnen (siehe `wissen/ki-kennzeichnung.md`).
5. Entscheidungen und **verworfene Alternativen** zusätzlich in `wissen/entscheidungslog.md` eintragen (Pflicht: mindestens eine pro Meilenstein).
6. Danach committen und pushen, damit alle den Stand haben.

## Rollen (Stand 23.11.2026)

| Rolle | Person | Seit |
|---|---|---|
| Prozess & Planung | _offen_ | |
| Technik & Robotik | _offen_ | |
| Sicherheit & SCRAM | Rathika | 23.11.2026 |
| Betrieb & Wirtschaft | _offen_ | |
| Moderator (Entscheidungen protokollieren, Optimist/Pessimist zuweisen) | _offen_ | |

Rollen werden im Projektverlauf gewechselt. Jede Person soll mindestens einmal Sicherheit, Technik und Wirtschaft übernehmen.

---

## 1. Ablauf-/Funktionskonzept
8–12 Funktionsschritte, aufgeteilt in Mensch / Automatisierung / Roboter; 1–2 exemplarische Abläufe in Klartext/Pseudocode.

| Wer | Datum | Status | Ergebnis / Link |
|---|---|---|---|
| | | | |

## 2. Technische Auslegung
Robotertyp, Greifer, Sensorik/Aktorik, Kalibrier-/Referenzkonzept, Genauigkeit.

| Wer | Datum | Status | Ergebnis / Link |
|---|---|---|---|
| | | | |

## 3. E/A-Schnittstelle
Ein-/Ausgangssignale, logische Kommunikation (Roboter ↔ SPS ↔ WMS).

| Wer | Datum | Status | Ergebnis / Link |
|---|---|---|---|
| | | | Sicherheitsrelevante Signale sind schon gesammelt: [sicherheit-scram.md, Abschnitt 8](sicherheit-scram.md#8-input-für-die-anderen-rollen) |

## 4. Groblayout & SCRAM
Layoutskizze, 2–3 kritische Situationen bewerten, planerische Maßnahmen.

| Wer | Datum | Status | Ergebnis / Link |
|---|---|---|---|
| Rathika | 23.11.2026 | Entwurf | [sicherheit-scram.md](sicherheit-scram.md) **[KI]** |

**Kurzfassung Sicherheit:**
- **Vorschlag V4:** überwachte Zelle ohne Vollzaun. Der AMR fährt nur in einem festen Korridor; Scanner mit Warnfeld (langsamer) und Schutzfeld (Stopp); Behälterwechsel über Durchreichen von außen; Messer gekapselt mit Zuhaltung; Fahren und Greifen nie gleichzeitig.
- **Verworfen:** V1 Vollzaun (Mobilität sinnlos, Stillstand bei jedem Wechsel), V2 freier Mischverkehr in der Halle (zu viele Personen), V3 nur Cobot-Kraftbegrenzung (schützt nicht vor scharfen Artikeln und Messer).
- **Kritische Situationen:** S1 Mensch im Fahrbereich, S2 beschädigter Li-Akku in der Retoure (→ Quarantänebehälter Q), S3 Paketstau am Öffnungsmodul.
- **Offen für das Team:** V4 bestätigen; Behälter Q als 4. Ziel aufnehmen; Öffnungstechnik und Artikelgewicht festlegen.

## 5. Wirtschaft
Qualitative Kosten-Nutzen-Abwägung: Invest, Betrieb, Schulung, Engineering.

| Wer | Datum | Status | Ergebnis / Link |
|---|---|---|---|
| | | | |

---

## Pitch (Folgeveranstaltung)
Use-Case, Funktionsweise der Zelle, Entscheidungen mit Begründung.

| Teil | Wer | Status |
|---|---|---|
| Use-Case & Ablauf | | |
| Technik | | |
| Sicherheit & SCRAM | Rathika | Inhalt im Entwurf |
| Wirtschaft | | |

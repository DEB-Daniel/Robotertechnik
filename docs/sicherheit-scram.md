# Sicherheit & SCRAM – Retouren-Sortierzelle mit mobilem Manipulator

**Rolle:** Sicherheit & SCRAM – Rathika · **Stand:** 23.11.2026 · **Status:** Entwurf, muss im Team besprochen werden
**Kennzeichnung:** Struktur, Szenarien, Bewertungen und Maßnahmen sind von Claude vorgeschlagen **[KI]**, aufgebaut nach VL Kap. 12 (SCRAM, ISO 12100, Zonen), Kap. 10/11 (MRK, ISO 10218/TS 15066, AMR) und Kap. 13 (Fehlerszenarien). Die Einstufungen E/S sind **Schätzungen** und müssen fachlich geprüft werden.
**Nicht Teil der Aufgabe:** normative PL/SIL-Auslegung. Sicherheitsfunktionen werden nur benannt, nicht berechnet.

---

## 1. Use-Case (kurz)

Ein mobiler Manipulator (AMR + Roboterarm) mit Hybridgreifer (Vakuum + Finger) entnimmt Artikel aus automatisch geöffneten Rücksendungen. Er erkennt sie per Kamera, Barcode/RFID und KI und sortiert sie in **A „wieder verkaufen“**, **B „Prüfung durch Mensch“** oder **C „Entsorgung“**.
Ergänzung aus Sicherheitssicht: ein vierter Behälter **Q „Quarantäne“** für Gefahrgut, z. B. beschädigte Akkus (siehe Szenario S2).

## 2. Systemmodell (SCRAM Schritt 1 / ISO 12100 Schritt 1: Grenzen)

| Bereich | Inhalt |
|---|---|
| **Komponenten** | Zuführband für Pakete; Öffnungsmodul (Messer oder Cutter); AMR mit Sicherheitslaserscanner; Roboterarm auf dem AMR (Cobot, Klasse II); Hybridgreifer; 2D/3D-Kamera, Barcode-/RFID-Leser; KI-Klassifizierung; Zielbehälter A/B/C/Q; Prüfplatz für den Menschen; Ladestation; Safe-SPS; WLAN-Anbindung an das Lagerverwaltungssystem (WMS) |
| **Beteiligte Menschen** | Bediener am Prüfplatz, Logistiker beim Behälterwechsel, Instandhalter, Einrichter/Programmierer; Fremdpersonal im Hallengang (nicht unterwiesen) |
| **Räumlich** | Zelle in einer Logistikhalle; Fahrkorridor des AMR; Bedienstellen; Materialein- und -ausgang |
| **Lebenszyklus** | Inbetriebnahme/Teachen, Automatikbetrieb, Behälterwechsel, Störungsbeseitigung (Paketstau, verlorener Artikel), Reinigung, Wartung, Laden des AMR |
| **Umgebung** | Staub und Kartonreste (Scanner/Kamera verschmutzen), wechselndes Hallenlicht, WLAN mit Störungen; **unbekannte Artikel**: scharf, schwer, zerbrechlich, flüssig, Akkus |
| **Vorhersehbarer Fehlgebrauch** | in den Paketstau greifen, Behälter „schnell mal“ im Betrieb tauschen, Scanner überbrücken, über den Fahrweg abkürzen |

**Besonderheit des Use-Cases:** Bei Retouren weiß man vorher **nicht, was im Paket ist**. Die Gefährdung kommt daher nicht nur vom Roboter, sondern auch vom **Werkstück**. Genau dafür ist SCRAM gedacht (offene Umgebung, KI als unsichere Datenquelle, Interaktion mit Menschen; VL 12_b).

## 3. Variantenbildung: Wie wird der Mensch geschützt?

Ideenrunde für das Teilsystem Sicherheit (Divergieren → Konvergieren), eingeordnet auf der Skala der Mensch-Roboter-Interaktion (VL Kap. 13):

| # | Variante | Optimist | Pessimist | Bewertung |
|---|---|---|---|---|
| V1 | **Vollzaun** um die ganze Zelle, Tür mit Zuhaltung (Isolation) | einfach, bewährt, hohe Geschwindigkeit möglich | Mobilität bringt nichts mehr; jeder Behälterwechsel und jeder B-Artikel stoppt die Zelle; viel Fläche | **verworfen** |
| V2 | AMR fährt **frei in der Halle** im Mischverkehr, nur Scanner auf dem AMR | maximal flexibel | viele, auch nicht unterwiesene Personen → Eintrittswahrscheinlichkeit hoch; Arm bewegt sich im offenen Raum | **verworfen** |
| V3 | **Nur Cobot-Kraftbegrenzung (PFL)**, kein Scanner („ist ja ein Cobot“) | billig, kein Zaun | PFL schützt nicht vor **scharfen Artikeln im Greifer** oder vor dem Messer; „nur langsamer fahren macht nicht sicher“ (VL 13); TS 15066 verlangt trotzdem eine Risikobeurteilung | **verworfen** |
| V4 | **Überwachte Zelle ohne Vollzaun**: AMR fährt nur in einem festen Korridor; Speed & Separation über Scanner (Warnfeld/Schutzfeld); Behälter über **Durchreichen** nach außen; Öffnungsmodul gekapselt; **Fahren XOR Greifen** | Mensch muss im Normalbetrieb nicht in die Zelle; Mobilität bleibt (mehrere Stationen, umsetzbar); Werkstückgefahren werden separat abgesichert | mehr Sensorik und Safe-SPS-Aufwand; Scanner können verschmutzen | **Vorschlag** |

**Vorschlag: V4.** Begründung nach dem **3-Stufen-Prinzip** (VL 12, ISO 12100):
1. **Inhärent sicher:** Der Mensch braucht im Normalbetrieb keinen Zutritt (Durchreichen). Der Arm bewegt sich nicht, während der AMR fährt. Das Messer ist gekapselt.
2. **Technisch:** Scanner mit Warn- und Schutzfeld, Lichtgitter, Zuhaltung, sichere Zonen und Geschwindigkeit am Arm, Not-Halt, Safe-SPS.
3. **Organisatorisch:** Bodenmarkierung, Ampel, Unterweisung, Betriebsanweisung, Schnittschutzhandschuhe am Prüfplatz.

> Verworfene Alternative für den Meilenstein „Sicherheitskonzept“: **V1, V2, V3** (Gründe siehe Tabelle). Eintrag im [Entscheidungslog](../wissen/entscheidungslog.md).

## 4. Groblayout mit Zonen

```
                 Hallengang (Personenverkehr, nicht unterwiesen)
 ════════════════════════════════════════════════════════════════════════
  ░░░░░░░░░░░░░░░░░ Beobachtungszone: gelbe Bodenmarkierung, Ampel ░░░░░░
  ░  ┌───────────┐   ┌──────────────────────┐                           ░
  ░  │ Zuführband│──▶│ Öffnungsmodul        │  Haube mit Zuhaltung,     ░
  ░  │  (Pakete) │   │ [Messer gekapselt]   │  Lichtgitter am Einlauf    ░
  ░  └───────────┘   └─────────┬────────────┘                           ░
  ░                    Entnahmeplatz                                    ░
  ░  ┃━━━━━━━━━━━━━━━━ Fahrkorridor AMR (Gefahrenzone) ━━━━━━━━━━━━━━┃  ░
  ░  ┃   [AMR + Arm]  ⇄        Scanner: Warnfeld ▒ / Schutzfeld ▓      ┃  ░
  ░  ┃━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┃  ░
  ░  │ A Wiederverk. │ B Prüfung │ C Entsorgung │ Q Quarantäne │ Laden │ ░
  ░  └──────┬────────┴─────┬─────┴──────┬───────┴──────┬───────┴───────┘ ░
  ░   Durchreiche     Rollenbahn    Durchreiche   feuerfester           ░
  ░   (Wechsel        zum Prüf-     (Wechsel      Behälter,             ░
  ░   von außen)      platz         von außen)    Rauch-/Temp.-Sensor   ░
  ░               ┌─────────────┐                                       ░
  ░               │ Prüfplatz   │ Not-Halt, Taster „Behälter wechseln“  ░
  ░               │ (Mensch)    │                                       ░
  ░               └─────────────┘   Wartungstür mit Zuhaltung ⊟         ░
  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
```

| Zone (Sicht Werker, VL 12) | Wo | Sicht Roboter | Reaktion |
|---|---|---|---|
| **Gefahrenzone** | Fahrkorridor, Arbeitsraum des Arms, Inneres des Öffnungsmoduls | Gefahrbereich | Mensch erkannt → sicherer Stopp |
| **Schutzzone** | Schutzfeld des Scanners, Lichtgitter am Öffnungsmodul, Zuhaltung der Wartungstür | überwachter Bereich | Gefahr wird verhindert, bevor ein Kontakt möglich ist |
| **Beobachtungszone** | Warnfeld, Bodenmarkierung, Ampel | überwachter Bereich | Frühwarnung, sicher reduzierte Geschwindigkeit |
| außerhalb | Prüfplatz, Durchreichen, Hallengang | unbeschränkt | normaler Betrieb |

## 5. SCRAM-Risikomatrix

Einstufung nach VL 12_b: Eintrittswahrscheinlichkeit **E** × Schadensausmaß **S** → **L** (akzeptabel), **M** (Maßnahmen empfohlen), **H** (Maßnahmen zwingend), **K** (nicht akzeptabel, stoppen/neu designen).
Die genaue Zuordnung der Felder ist eine Annahme **[KI]**, weil die Folien keine feste Tabelle vorgeben.

| S \ E | **selten** | **gelegentlich** | **häufig** |
|---|---|---|---|
| **leicht** (reversibel, Erste Hilfe) | L | L | M |
| **mittel** (ärztliche Behandlung) | L | M | H |
| **schwer** (irreversibel) | M | H | K |
| **katastrophal** (Tod, mehrere Personen, Brand) | H | K | K |

## 6. Hazard Scenarios (SCRAM Schritt 2–4)

### 6.1 Die drei kritischen Situationen (für den Pitch)

**S1 – Mensch im Fahr- oder Arbeitsbereich während des Betriebs**
*Situation:* Ein Logistiker will Behälter C „schnell“ von innen tauschen, oder ein Kollege kürzt über den Fahrkorridor ab. Der AMR fährt gerade an oder der Arm schwenkt mit einem Artikel.
*Gefährdung:* Stoß oder Quetschen durch AMR/Arm, Schnitt durch einen scharfen Artikel im Greifer.
*Bewertung ohne Maßnahmen:* E häufig × S schwer = **K**
*Maßnahmen:*
1. Inhärent: Behälterwechsel über Durchreichen von außen. Taster „Behälter wechseln“: Der Roboter beendet den Zyklus und meldet „Behälter frei“, erst dann darf gewechselt werden. Fahren und Greifen nie gleichzeitig; beim Fahren steht der Arm in einer überwachten Transportpose.
2. Technisch: Scanner auf dem AMR und ein stationärer Flächenscanner für den Korridor. Das **Warnfeld** schaltet auf sicher reduzierte Geschwindigkeit (Arm ≤ 250 mm/s nach VL 10), das **Schutzfeld** löst einen sicheren Stopp aus. Sichere Zonen- und Achsbegrenzung des Arms, damit er nicht aus dem Korridor heraus schwenkt. PFL als zusätzliche Ebene.
3. Organisatorisch: Bodenmarkierung, Ampel, Unterweisung, Zutritt nur über die Wartungstür mit Zuhaltung.
*Restrisiko:* E selten × S mittel = **L**

**S2 – Beschädigter Lithium-Akku in der Retoure**
*Situation:* Eine zurückgeschickte Powerbank oder ein Handy ist gequetscht. Das Öffnungsmodul oder der Greifer beschädigt den Akku zusätzlich.
*Gefährdung:* Thermisches Durchgehen, Brand, giftiger Rauch in der Halle. Das Risiko kommt vom Werkstück, nicht vom Roboter.
*Bewertung ohne Maßnahmen:* E gelegentlich **[KI-Schätzung]** × S katastrophal = **K**
*Maßnahmen:*
1. Inhärent: Das Öffnungsmodul schneidet nur mit begrenzter Schnitttiefe (nur der Karton wird geöffnet). Die Klasse „Akku/Elektronik“ wird per Barcode/RFID/KI erkannt, bevor der Arm greift. Solche Artikel werden mit reduzierter Greifkraft und ohne Vakuum auf der Akkufläche gegriffen.
2. Technisch: Thermokamera bzw. Temperatursensor am Entnahmeplatz. Bei Auffälligkeit wird der Artikel sofort in den feuerfesten **Quarantänebehälter Q** gelegt, mit Rauch- und Temperaturüberwachung und Alarm an die Halle.
3. Organisatorisch: Unterweisung zum Umgang mit Akkus, Löschmittel für Lithium-Brände an der Zelle, Brandschutzkonzept mit dem Betreiber abstimmen.
*Restrisiko:* E selten × S schwer = **M** → dokumentieren und vom Team bewusst akzeptieren oder weiter senken.

**S3 – Paketstau am Öffnungsmodul, Mensch greift hinein**
*Situation:* Ein Paket verkantet sich im Öffnungsmodul. Der Bediener greift hinein, um es zu lösen (**vorhersehbarer Fehlgebrauch**).
*Gefährdung:* Schnittverletzung durch das Messer, Einzug durch das Förderband.
*Bewertung ohne Maßnahmen:* E gelegentlich × S schwer = **H**
*Maßnahmen:*
1. Inhärent: Messer vollständig gekapselt, Rückzugsposition des Messers in Ruhe.
2. Technisch: Haube mit **Zuhaltung**. Sie öffnet erst, wenn Messer und Band sicher stehen. Lichtgitter am Einlauf. Störungsbehebung nur bei offener Haube in einer sicheren Betriebsart (Tippbetrieb mit Zustimmtaster).
3. Organisatorisch: Betriebsanweisung „Stau beheben“, Schnittschutzhandschuhe.
*Restrisiko:* E selten × S mittel = **L**

### 6.2 Weitere Szenarien (Gesamtübersicht)

| # | Hazard Scenario | E | S | Risiko | Maßnahmen (Stufe 1 / 2 / 3) | Rest |
|---|---|---|---|---|---|---|
| S4 | **KI-Fehlklassifikation:** gefährlicher oder defekter Artikel landet in A „wieder verkaufen“ → Gefahr für Endkunden (Produktsicherheit) | gelegentlich | schwer | H | Im Zweifel immer B (Prüfung Mensch). Schwellwert für die Konfidenz; A nur bei übereinstimmendem Barcode/RFID und Bild; Stichproben; Rückverfolgbarkeit pro Artikel | M |
| S5 | **Scharfer Artikel** (Messer, Glasbruch) geht an den Prüfplatz → Schnitt beim Bediener | gelegentlich | mittel | M | Kategorie „scharf“ erkennen → in einer Schale ablegen statt lose; Schnittschutzhandschuhe | L |
| S6 | **Artikel fällt aus dem Greifer** (Vakuumverlust, schwerer Artikel) | gelegentlich | mittel | M | Vakuum- und Greifkraftüberwachung; Bewegung nur über dem Boden des Korridors; maximales Artikelgewicht festlegen; bei Druckluftausfall Zustand halten | L |
| S7 | **Kommunikationsausfall** (WLAN zum WMS oder Safety-Kommunikation) | selten | schwer | M | Sicherheitsfunktionen laufen lokal auf dem AMR (Safe-SPS), nicht über WLAN. Watchdog/Lebensbit → sicherer Stopp. WMS-Ausfall → Artikel nach B | L |
| S8 | **Scanner verschmutzt oder geblendet** (Staub, Kartonreste, Hallenlicht) | gelegentlich | schwer | H | Sichere Scanner mit Selbstdiagnose (Verschmutzung → sicherer Zustand); Reinigungsintervall; Kamera ist **kein** Personenschutz, nur Prozesssensorik | L |
| S9 | **Unbefugter Zugriff** (Remote-Wartung, WLAN, Teachen durch Unbefugte) | selten | schwer | M | „No safety without security“ (VL 10, ISO 10218-1:2025 Kl. 5.1.16): Zugriffsrechte, Schlüsselschalter für die Betriebsart, abgesichertes Netz | L |
| S10 | **Einrichten/Teachen in der Zelle** | gelegentlich | mittel | M | Betriebsart T1 (≤ 250 mm/s) mit Zustimmtaster, Scanner bleibt aktiv, Zutritt nur für Einrichter | L |
| S11 | **Laden des AMR** (Kurzschluss, Ladekontakte) | selten | mittel | L | Ladestation im Korridor, Kontakte nur bei angedocktem AMR unter Spannung | L |

## 7. Sicherheitsfunktionen (Kette: Sensor → Safe-SPS → Aktor)

Grundsatz aus VL 6/12: **Personenschutz läuft über eine zweikanalige Safe-SPS, nicht über die Robotersteuerung.** Die Robotersteuerung ist nur ein sicherer Teilnehmer.

| SF | Sicherheitsfunktion | Sensor | Reaktion (Aktor) | Szenario |
|---|---|---|---|---|
| SF1 | Not-Halt | Not-Halt-Taster am Prüfplatz, an den Durchreichen, am AMR und an der Wartungstür | alle Antriebe stopp (Arm, AMR, Messer, Band) | alle |
| SF2 | Schutzfeld verletzt → sicherer Stopp | Scanner AMR + Flächenscanner | Stopp von Arm und AMR | S1 |
| SF3 | Warnfeld verletzt → sicher reduzierte Geschwindigkeit | Scanner AMR + Flächenscanner | Arm ≤ 250 mm/s, AMR langsam | S1 |
| SF4 | Fahren XOR Greifen (Transportpose überwacht) | sichere Achs-/Posenüberwachung des Arms | AMR darf nur bei Arm in Transportpose fahren | S1, S6 |
| SF5 | Sichere Arbeitsraumbegrenzung des Arms | sichere Zonenüberwachung in der Robotersteuerung | Stopp bei Verlassen der Zone | S1 |
| SF6 | Haube Öffnungsmodul: Zuhaltung + Lichtgitter | Zuhaltungsschalter, Lichtgitter | Messer und Band stopp; Haube öffnet erst bei Stillstand | S3 |
| SF7 | Wartungstür mit Zuhaltung | Türschalter | Zelle stopp, Wiederanlauf nur nach Quittieren von außen | S1, S10 |
| SF8 | Betriebsartenwahl + Zustimmtaster | Schlüsselschalter, Zustimmtaster | T1 nur mit gedrücktem Zustimmtaster | S9, S10 |
| SF9 | Brand-/Temperaturüberwachung Q | Thermokamera, Rauch-/Temperatursensor | Alarm, Zelle stopp, Behälter Q geschlossen | S2 |

Typische Anforderung für Klasse-II-Roboter: PL d, Kat. 3 (VL 10). Nur als Hinweis, die Auslegung ist laut Aufgabenstellung **nicht gefordert**.

## 8. Input für die anderen Rollen

**Für E/A (sicherheitsrelevante Signale):**
- *Sichere Eingänge:* Not-Halt-Kreise (zweikanalig), Scanner-OSSD Schutzfeld, Scanner Warnfeld, Lichtgitter, Zuhaltung Haube, Zuhaltung Wartungstür, Zustimmtaster, Betriebsartenschalter, Arm in Transportpose
- *Sichere Ausgänge:* Freigabe Arm, Freigabe AMR-Antrieb, Freigabe Messer/Band, Zuhaltung entriegeln
- *Standard-E/A:* Ampel (rot/gelb/grün), Taster „Behälter wechseln“, „Behälter frei“, Quittieren, Vakuum OK, Temperaturalarm Q, Lebensbit/Watchdog zum WMS

**Für Technik:** Scanner-Felder und Abstände (EN ISO 13855) bei der Layoutplanung berücksichtigen; maximales Artikelgewicht und Greifkraft festlegen; nach einem Crash Referenzfahrt.

**Für Wirtschaft:** Zusatzkosten der Sicherheit (Scanner, Safe-SPS, Zuhaltungen, Quarantänebehälter, Thermokamera) gegenüber V1 (Zaun, billiger, aber Stillstand bei jedem Behälterwechsel).

**Für Prozess:** Der Ablauf muss die Schritte „Behälter wechseln anfordern“ und „Akku-Verdacht → Q“ enthalten.

## 9. Exemplarischer Ablauf: Behälterwechsel (sicherheitsrelevant)

Ein solcher Ablauf wird vom Dozenten gefordert. Logische Kooperation, Klartext/Pseudocode:

```
WENN Taster "Behälter X wechseln" gedrückt:
    Ampel Durchreiche X = gelb
    Roboter beendet den laufenden Greifvorgang (Artikel ablegen, nicht abbrechen)
    Roboter sperrt Ziel X → Artikel für X werden zwischengepuffert oder nach B gelegt
    Arm fährt in Transportpose, AMR verlässt den Bereich vor X
    WARTEN bis Safe-SPS meldet "Bereich X frei" (Timeout 60 s → Störmeldung)
    Durchreiche X entriegeln, Ampel = grün
    Mensch tauscht Behälter von außen
    WARTEN auf "Behälter X eingesetzt" (Sensor) UND Quittieren
    Durchreiche verriegeln, Ampel = aus, Ziel X wieder freigeben
```
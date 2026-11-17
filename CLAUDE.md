# Projekt: Planspiel – Grundlagen der Robotertechnik

Gemeinsames Gruppenprojekt (Vorlesung "Grundlagen der Robotertechnik", Dozent nennt es "Planspiel").
Team: Daniel, Jan, Ratika, Luca.

## Repo-Struktur
- `Vorlesung/` – Vorlesungsunterlagen (Folien, Skripte)
- `Aufgabe/` – Aufgabenstellung des Dozenten
- `wissen/` – **geteiltes Claude-Gedächtnis** (siehe unten)
- `docs/` – Anleitungen fürs Team

## Gedächtnis-Regeln (für Claude)
Das geteilte Gedächtnis liegt im Repo unter `wissen/`. Der Index wird automatisch geladen:

@wissen/INDEX.md

1. Lies bei Bedarf die im Index verlinkten Dateien, bevor du Annahmen zum Projekt triffst.
2. Neue Erkenntnisse, die **für alle** relevant sind (Entscheidungen, Annahmen, Formeln, Parameter, Aufgabenstand, Absprachen, Arbeitsweise), speicherst du als **eigene Datei in `wissen/`** (eine Tatsache pro Datei, Format siehe `wissen/README.md`) und ergänzt eine Zeile in `wissen/INDEX.md`. Vorher prüfen, ob es die Info schon gibt – dann die Datei aktualisieren statt duplizieren.
3. Persönliches (E-Mail, Namen privater Chats, individuelle Vorlieben) gehört **nicht** ins Repo, sondern ins private Gedächtnis oder `CLAUDE.local.md` (ist gitignored).
4. Schreibe `wissen/`-Einträge auf Deutsch, kurz und sachlich. Bei Entscheidungen immer das *Warum* und das Datum nennen.
5. Nach Änderungen an `wissen/` kurz darauf hinweisen, dass der Nutzer committen und pushen soll, damit die anderen es bekommen.
6. Quellen angeben (Folie/Seite/Datei), wenn Wissen aus Vorlesungsunterlagen stammt.

## Was NICHT ins geteilte Gedächtnis (`wissen/`) darf – verbindlich
- **Nur Projektbezug:** Gespeichert wird ausschließlich, was mit dem Planspiel bzw. der Vorlesung zu tun hat. Alles andere (andere Fächer, Hobbys, Smalltalk, Nebenthemen) bleibt draußen.
- **Keine Privatnachrichten:** Keine Chatverläufe, E-Mails, WhatsApp-/Discord-Nachrichten, Zitate aus privaten Gesprächen. Nur das *Ergebnis* einer Absprache, z. B. „Wir nutzen Variante B", ohne wer-wann-wo-was-geschrieben-hat.
- **Keine privaten Daten:** Keine E-Mail-Adressen, Telefonnummern, Adressen, Zugangsdaten, Passwörter, API-Schlüssel/Tokens, Matrikelnummern, Noten oder Gesundheits-/Privatsituationen einzelner Personen.
- **Keine Bewertung von Personen:** Keine Einschätzungen zu Leistung, Verhalten oder Fähigkeiten einzelner Teammitglieder. Rollen und Aufgaben im Projekt sind erlaubt.
- **Keine Dritten:** Keine personenbezogenen Daten Dritter (Dozent, Kommilitonen) außer dem, was für das Projekt nötig ist (z. B. Name des Dozenten, Abgabetermin).
- **Keine rohen Aufnahmen/Transkripte** (z. B. Plaud) ungefragt: nur eine sachliche Zusammenfassung, vollständige Transkripte nur nach ausdrücklicher Zustimmung des Teams.
- **Keine fremden Urheberrechtsinhalte in Masse:** Nur eigene Kurzfassungen mit Quellenangabe, keine kompletten Kopien von Folien oder Büchern.
- **Nichts Unbelegtes als Fakt:** Vermutungen, Schätzungen und KI-Zahlen sind als solche zu kennzeichnen (`[KI]`, siehe `wissen/ki-kennzeichnung.md`). Unklares als „offen" markieren, nicht raten.
- **Im Zweifel nicht speichern** – erst den Nutzer fragen. Findest du beim Arbeiten schon Gespeichertes, das gegen diese Regeln verstößt, weise darauf hin und schlage das Löschen vor.
- **Nur auf Zuruf speichern:** Lege neue Dateien in `wissen/` an, wenn der Nutzer es verlangt oder eine Erkenntnis eindeutig für alle relevant ist; nenne dann kurz, was du gespeichert hast.
- **Keine Geheimnisse committen:** Weise darauf hin, wenn ein Commit Zugangsdaten oder private Dateien enthalten würde.

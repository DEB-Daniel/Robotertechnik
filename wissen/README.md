# Format der Wissensdateien

Jede Datei enthält **genau eine Tatsache** und beginnt mit Frontmatter:

```markdown
---
name: kurzer-kebab-case-name
description: Einzeiler, an dem Claude erkennt, ob die Datei relevant ist
metadata:
  type: user | feedback | project | reference
---

Inhalt. Bei feedback/project danach:

**Why:** Begründung / Datum
**How to apply:** Wann und wie das angewendet wird
```

Typen:
- `project` – Entscheidungen, Aufgabenstand, Parameter, Termine
- `feedback` – Absprachen zur Arbeitsweise mit Claude ("immer so, niemals so")
- `reference` – Verweise auf Folien, Seiten, Links, externe Quellen
- `user` – nur teamweite Rollen (z. B. wer macht was), nichts Privates

Nach dem Anlegen eine Zeile in `INDEX.md` ergänzen. Dateien aktuell halten, falsche löschen.

**Tabu in `wissen/`** (Details in `CLAUDE.md`): alles ohne Projektbezug, Privatnachrichten und Chatverläufe, private Daten (E-Mail, Telefon, Passwörter, Tokens, Noten), Bewertungen einzelner Personen, rohe Transkripte ohne Teamzustimmung, Masse-Kopien von Folien. Unsicheres mit `[KI]` bzw. „offen" kennzeichnen. Im Zweifel nicht speichern, sondern fragen.

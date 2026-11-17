# Geteiltes Claude-Gedächtnis – Anleitung fürs Team

Ziel: Daniel, Jan, Ratika und Luca arbeiten mit Claude auf demselben Wissensstand, egal von welchem Rechner.

## 1. Wie es funktioniert

Claude hat zwei Arten von Gedächtnis:

| Art | Wo | Geteilt? |
|---|---|---|
| **Privates Auto-Gedächtnis** | `~/.claude/projects/<Pfad-des-Repos>/memory/` auf deinem Rechner | Nein – pro Person und pro Ordnerpfad |
| **Projektdatei `CLAUDE.md`** | im Repo (Root) | **Ja, via Git** |

Das private Gedächtnis hängt am lokalen Ordnerpfad und lässt sich nicht sinnvoll über Git teilen. Deshalb nutzen wir:

- **`CLAUDE.md`** – wird bei jeder Session automatisch geladen. Enthält Projektkontext und die Regeln, wie Claude mit dem Wissen umgeht.
- **`wissen/`** – unser geteiltes Gedächtnis: `INDEX.md` (wird per `@wissen/INDEX.md` automatisch geladen) plus eine Datei pro Wissenseintrag.

Claude liest den Index zu Sessionbeginn und öffnet einzelne Dateien bei Bedarf. Neue gemeinsame Erkenntnisse legt Claude (laut `CLAUDE.md`) als Datei in `wissen/` ab.

## 2. Einrichtung (einmalig pro Person)

1. Repo klonen und in VS Code öffnen:
   ```
   git clone <REPO-URL>
   code Robotertechnik
   ```
2. Claude-Code-Erweiterung in VS Code installieren und anmelden (oder Claude Desktop → Tab **Code** → Ordner des Repos wählen).
3. Fertig – `CLAUDE.md` wird automatisch geladen. Test: Claude fragen *„Was weißt du über unser Projekt?“* – er sollte das Planspiel und das Team nennen.

Hinweis: In Claude Desktop funktioniert das geteilte Gedächtnis **nur im Code-Tab** (gleiche Engine wie VS Code). Im normalen Chat-Tab liest Claude das Repo nicht; dort müssten Dateien manuell hochgeladen werden.

## 3. Täglicher Ablauf

**Vor dem Arbeiten:** `git pull` – so bekommst du das neue Wissen der anderen.

**Wissen speichern:** Einfach sagen, z. B.
- *„Merk dir im Repo: Wir haben uns auf einen 6-Achs-Knickarm geeinigt, weil …“*
- *„Speichere die Zusammenfassung der Aufgabenstellung in wissen/.“*

Claude legt dann `wissen/<name>.md` an und ergänzt `wissen/INDEX.md`. Formatregeln stehen in [wissen/README.md](../wissen/README.md).

**Danach:**
```
git add wissen CLAUDE.md
git commit -m "Wissen: <Thema>"
git push
```

Du kannst auch selbst Dateien in `wissen/` schreiben – gleiches Format, plus Zeile im Index.

## 4. Was gehört wohin?

- **Ins Repo (`wissen/`)**: Entscheidungen, Annahmen, Parameter, Formeln, Aufgabenstand, Termine, Absprachen zur Arbeitsweise, Verweise auf Folien.
- **Nicht ins Repo**: E-Mail-Adressen, private Vorlieben, Chatverläufe. Dafür das private Gedächtnis oder `CLAUDE.local.md` (steht in `.gitignore`).

**Verbindliche Regeln für das geteilte Gedächtnis** (stehen auch in `CLAUDE.md`, damit Claude sie befolgt):
- Nur Inhalte mit Projektbezug (Planspiel, Vorlesung). Nichts zu anderen Themen.
- Keine Privatnachrichten oder Chatverläufe. Festgehalten wird nur das Ergebnis einer Absprache, nicht wer was geschrieben hat.
- Keine privaten Daten: E-Mail, Telefon, Adresse, Passwörter, Tokens, Matrikelnummern, Noten.
- Keine Bewertungen einzelner Personen. Rollen und Aufgaben im Projekt sind in Ordnung.
- Rohe Aufnahmen und Transkripte (z. B. Plaud) nur nach Zustimmung des Teams, sonst nur eine sachliche Zusammenfassung.
- Keine Massenkopien von Folien oder Büchern, nur eigene Kurzfassungen mit Quelle.
- Unsicheres mit `[KI]` kennzeichnen, Unklares als „offen" markieren.
- Im Zweifel nicht speichern, sondern im Team nachfragen.
- Vor jedem Push kurz prüfen (`git diff --staged`), ob etwas Privates mitgeht.

## 5. Regeln gegen Chaos

- **Eine Tatsache pro Datei**, sprechender Dateiname, Index aktuell halten.
- **Kleine, häufige Commits** für `wissen/` – reduziert Merge-Konflikte.
- **Konflikt im `INDEX.md`?** Beide Zeilen behalten, Duplikate entfernen, committen.
- **Veraltetes löschen** statt anhäufen. Claude kann das auf Zuruf: *„Prüfe wissen/ auf Widersprüche und Veraltetes.“*
- **Claude kann irren:** Eingetragenes Wissen kurz gegenlesen, bevor ihr es pusht (besonders Zahlen und Formeln).
- Änderungen an `CLAUDE.md` bitte kurz im Team abstimmen, da sie das Verhalten aller Sessions beeinflussen.

## 6. Fehlersuche

- *Claude kennt das Projekt nicht:* Sitzung im richtigen Ordner (Repo-Root) gestartet? Mit `/memory` in Claude Code sieht man, welche Dateien geladen sind.
- *Neues Wissen der anderen fehlt:* `git pull` vergessen, danach neue Session starten.
- *Eintrag wird ignoriert:* Steht er im `INDEX.md`? Ist die `description` aussagekräftig?

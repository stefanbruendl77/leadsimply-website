# Auftrag: Danke-Seite und Leistungsblock

Zwei getrennte Aufgaben. Bitte Teil A vollständig abschließen, mir das Ergebnis zeigen, dann Teil B.

---

# TEIL A — Danke-Seite für den Leitfaden

## Ausgangslage

Auf `/leitfaden/` steht ein Formular, das den Leitfaden anfordert. Die PDF `leitfaden-fruehwarnsignale.pdf` liegt im Hauptverzeichnis. Bisher sollte der Leitfaden laut Formulartext per E-Mail zugesendet werden — das wird durch einen direkten Download ersetzt.

Formspree-ID: `xwlegdgr`

## A1 — Formular anpassen

In `leitfaden/index.html`:

**a)** In Zeile 637 den Platzhalter `DEINE_FORM_ID` durch `xwlegdgr` ersetzen.

**b)** Innerhalb des `<form>`-Tags ein verstecktes Feld ergänzen:

```html
<input type="hidden" name="_next" value="https://leadsimply.de/leitfaden/danke/">
```

**c)** Den Rechtstext in Zeile 655 anpassen. Dort steht, der Leitfaden werde per E-Mail zugesendet — das stimmt nach der Umstellung nicht mehr. Neu sinngemäß: Der Leitfaden steht direkt im Anschluss zum Download bereit, die Daten werden nicht weitergegeben, Verweis auf die Datenschutzerklärung bleibt.

**d)** Den Kommentarblock in den Zeilen 631–636 (Anleitung zum Einrichten von Formspree) entfernen — erledigt.

## A2 — PDF an den richtigen Ort

`leitfaden-fruehwarnsignale.pdf` liegt im Hauptverzeichnis. Verschiebe sie nach `dateien/leitfaden-fruehwarnsignale.pdf`. Falls im Projekt bereits eine Konvention für solche Dateien existiert, nutze diese und sag mir, welche.

## A3 — Danke-Seite bauen

Neue Datei: `leitfaden/danke/index.html`

**Wichtig:** Übernimm Aufbau, Kopfzeile, Fußzeile, CSS-Einbindung und Schriften exakt von einer bestehenden Seite. Keine neuen Farben, keine neuen Schriften, keine eigene Gestaltungssprache.

Inhalt:

- **Überschrift**, die sagt, dass der Leitfaden bereitsteht — kein bloßes „Danke"
- **Download-Button**, prominent, Beschriftung benennt die Handlung: „Leitfaden herunterladen (PDF, 6 Seiten)"
- **Kurzer Absatz**, was den Leser erwartet: die zwölf Signale in vier Bereichen und die vier Gesprächsfragen. Zwei bis drei Sätze, sachlich
- **Abschnitt zum nächsten Schritt**, deutlich abgesetzt, Verweis auf `/analyse-call/`: 45 Minuten, kostenlos, kein Verkaufsgespräch. Ergebnis sind eine Einordnung der eigenen Fluktuation, der größte Hebel und ein konkreter nächster Schritt
- **Unauffälliger Link** zurück zur Startseite

Technisch:

- `<meta name="robots" content="noindex, nofollow">` im Head
- Block A aus `leadsimply-schema-anleitung.md` einfügen
- Responsiv bis Mobil, sichtbarer Tastaturfokus

---

# TEIL B — Leistungsblock auf der Startseite

## Was fehlt

Auf `index.html` gibt es keinen Hinweis auf die Leistungen — sie stehen nur in der Navigation und im Fußbereich. Das soll ein eigener Abschnitt werden.

## Wo

In `index.html`, **vor** dem abschließenden Call-to-Action-Abschnitt („45 Minuten, die Ihnen Klarheit verschaffen"), **nach** dem Abschnitt „Ihr Weg zu mir".

## Gestaltung

Übernimm die Gestaltungssprache der bestehenden Abschnitte auf der Startseite. Keine neuen Farben oder Schriften.

**Wichtig zur Darstellung:** Die drei Leistungen sind keine gleichrangigen Alternativen, sondern bauen aufeinander auf — die Diagnose ist im 90-Tage-Programm enthalten, der Retainer schließt an. Die Darstellung soll diese Abfolge erkennbar machen, nicht drei beliebig wählbare Kästchen suggerieren.

**Keine Preise.** Jede Leistung verlinkt auf ihre Detailseite.

## Inhalt

**Eyebrow:** Leistungen

**Überschrift:** Drei Schritte, die aufeinander aufbauen.

---

**1 — Fluktuation-Diagnose** → `/fluktuation-diagnose/`

Eine Inventur Ihrer Belegschaft: Wer ist da, welche Rollen sind Schlüsselfunktionen, wo sitzen die Flaschenhälse, wer hat Perspektive — und bei wem würde ein Abgang wirklich wehtun. Die Leitfrage dabei: Würden Sie diese Person heute nochmal einstellen? Am Ende steht eine Auswertung mit konkreten Handlungsempfehlungen.

---

**2 — 90-Tage-Programm** → `/90-tage-programm/`

Die Diagnose ist enthalten. Danach geht es um die Umsetzung: Was zuerst, wie konkret, in welcher Reihenfolge. Ich begleite die 90 Tage und frage nach — damit die Empfehlungen nicht im Ordner liegen bleiben.

---

**3 — Sparring-Retainer** → `/retainer/`

Ein fester Ansprechpartner für Fluktuation und Mitarbeiterbindung. Wir schauen laufend auf Entwicklungen und besprechen Personalentscheidungen, bevor sie getroffen sind.

---

**Abschließende Zeile, kleiner gesetzt:**

Wo Sie einsteigen, klären wir im Erstgespräch.

---

# Zum Schluss

- Zeig mir mit `git diff`, was sich in `leitfaden/index.html` und `index.html` geändert hat
- Bestätige, dass der PDF-Pfad in der Danke-Seite stimmt
- Nenne mir den Pfad der neuen Seite

Nichts committen — das mache ich selbst.

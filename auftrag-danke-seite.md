# Auftrag: Danke-Seite für den Leitfaden

## Ausgangslage

Auf `/leitfaden/` steht ein Formular, das den Leitfaden anfordert. Die PDF `leitfaden-fruehwarnsignale.pdf` liegt im Hauptverzeichnis. Bisher wurde der Leitfaden laut Formulartext per E-Mail zugesendet — das soll durch einen direkten Download nach dem Absenden ersetzt werden.

Formspree-ID: `xwlegdgr`

---

## Aufgabe 1 — Formular auf /leitfaden/ anpassen

In `leitfaden/index.html`:

**a)** In Zeile 637 den Platzhalter `DEINE_FORM_ID` durch `xwlegdgr` ersetzen.

**b)** Innerhalb des `<form>`-Tags ein verstecktes Feld ergänzen, das Formspree nach dem Absenden weiterleitet:

```html
<input type="hidden" name="_next" value="https://leadsimply.de/leitfaden/danke/">
```

**c)** Den Rechtstext in Zeile 655 anpassen. Aktuell steht dort, der Leitfaden werde per E-Mail zugesendet. Das stimmt nach der Umstellung nicht mehr. Neuer Text sinngemäß: Der Leitfaden steht direkt im Anschluss zum Download bereit, die Daten werden nicht weitergegeben, Verweis auf die Datenschutzerklärung bleibt bestehen.

**d)** Den Kommentarblock in den Zeilen 631–636 (die Anleitung zum Einrichten von Formspree) entfernen — er ist erledigt.

---

## Aufgabe 2 — PDF an den richtigen Ort

`leitfaden-fruehwarnsignale.pdf` liegt derzeit im Hauptverzeichnis. Verschiebe sie nach `dateien/leitfaden-fruehwarnsignale.pdf` und lege den Ordner an, falls er fehlt. Falls im Projekt bereits eine andere Konvention für solche Dateien existiert (etwa ein vorhandener Ordner für Downloads), nutze diese stattdessen und sag mir, welche du gewählt hast.

---

## Aufgabe 3 — Danke-Seite bauen

Neue Datei: `leitfaden/danke/index.html`

**Wichtig:** Übernimm Aufbau, Kopfzeile, Fußzeile, CSS-Einbindung und Schriftarten exakt von einer bestehenden Seite (z. B. `leitfaden/index.html`), damit die Seite sich nahtlos einfügt. Keine neuen Farben, keine neuen Schriften, keine eigene Gestaltungssprache.

### Inhalt der Seite

**Überschrift:** Bestätigung, dass es geklappt hat. Kein bloßes „Danke" — sondern eine Zeile, die sagt, dass der Leitfaden bereitsteht.

**Download-Button:** Prominent, führt auf die PDF. Beschriftung benennt die Handlung, z. B. „Leitfaden herunterladen (PDF, 6 Seiten)".

**Kurzer Absatz:** Was den Leser im Leitfaden erwartet — die zwölf Signale in vier Bereichen und die vier Gesprächsfragen. Zwei bis drei Sätze, kein Marketing-Ton.

**Abschnitt mit dem nächsten Schritt:** Deutlich abgesetzt, mit Verweis auf das kostenlose Erstgespräch (`/analyse-call/`). Formulierung sachlich: 45 Minuten, kostenlos, kein Verkaufsgespräch. Ergebnis sind eine Einordnung der eigenen Fluktuation, der größte Hebel und ein konkreter nächster Schritt. Dieser Abschnitt ist der eigentliche Zweck der Seite — er soll sichtbar sein, ohne aufdringlich zu wirken.

**Rückweg:** Ein unauffälliger Link zurück zur Startseite.

### Technische Anforderungen

- `<meta name="robots" content="noindex, nofollow">` im Head — die Seite soll nicht in Suchergebnissen auftauchen
- Kein Schema-Block nötig, aber Block A aus der Schema-Anleitung einfügen, damit die Seite konsistent bleibt
- Responsiv bis Mobil
- Sichtbarer Tastaturfokus auf Button und Links

---

## Aufgabe 4 — Prüfen und berichten

Nach den Änderungen:

- Zeig mir mit `git diff`, was sich in `leitfaden/index.html` geändert hat
- Bestätige, dass der Pfad zur PDF in der Danke-Seite stimmt
- Nenne mir den fertigen Pfad der neuen Seite

Nichts committen — das mache ich selbst.

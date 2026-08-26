# Anmeldungen automatisch in ein Google Sheet schreiben

Am Ende landet jede Leitfaden-Anforderung als neue Zeile in einer Tabelle: Datum, Vorname, E-Mail, Unternehmen. Zusätzlich zur bisherigen E-Mail von Formspree, nicht statt ihr.

Dauer: etwa 20 Minuten. Die Schritte 1 bis 6 machen Sie selbst im Browser. Schritt 7 macht Claude Code.

---

## Schritt 1 — Tabelle anlegen

1. `sheets.google.com` aufrufen, mit Ihrem Google-Konto anmelden
2. Auf **Leer** klicken
3. Oben links den Namen ändern in: `LeadSimply Anmeldungen`
4. In die erste Zeile diese vier Spaltenüberschriften eintragen, jeweils eine Zelle:

   A1: `Zeitpunkt`
   B1: `Vorname`
   C1: `E-Mail`
   D1: `Unternehmen`

Die Überschriften müssen genau so heißen — das Skript verlässt sich darauf.

---

## Schritt 2 — Skript-Editor öffnen

Im Menü: **Erweiterungen** → **Apps Script**

Es öffnet sich ein neuer Tab mit einem Code-Fenster. Darin steht bereits etwas wie:

```
function myFunction() {
}
```

**Löschen Sie den gesamten vorhandenen Inhalt.**

---

## Schritt 3 — Code einfügen

Fügen Sie stattdessen genau das hier ein:

```javascript
function doPost(e) {
  try {
    var blatt = SpreadsheetApp.getActiveSpreadsheet().getSheets()[0];
    var daten = e.parameter;

    blatt.appendRow([
      new Date(),
      daten.vorname || '',
      daten.email || '',
      daten.unternehmen || ''
    ]);

    return ContentService
      .createTextOutput(JSON.stringify({ status: 'ok' }))
      .setMimeType(ContentService.MimeType.JSON);

  } catch (fehler) {
    return ContentService
      .createTextOutput(JSON.stringify({ status: 'fehler' }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

Dann oben auf das **Speichern-Symbol** (Diskette) klicken.

Falls nach einem Projektnamen gefragt wird: `LeadSimply Formular`

---

## Schritt 4 — Als Web-App veröffentlichen

1. Oben rechts auf **Bereitstellen** → **Neue Bereitstellung**
2. Links neben "Typ auswählen" auf das **Zahnrad** klicken → **Web-App** wählen
3. Jetzt die Einstellungen:

   **Beschreibung:** `Formular Anmeldungen`
   **Ausführen als:** `Ich` (Ihre E-Mail-Adresse)
   **Zugriffsberechtigung:** `Jeder`

Der letzte Punkt ist wichtig. „Jeder" klingt bedenklich, bedeutet hier aber nur: Ihre Website darf Daten hinschicken, ohne dass sich der Besucher bei Google anmelden muss. Niemand kann die Tabelle dadurch lesen — das Skript schreibt nur.

4. Auf **Bereitstellen** klicken

---

## Schritt 5 — Berechtigung erteilen

Google fragt jetzt nach Ihrer Erlaubnis. Der Dialog wirkt abschreckend, ist aber normal:

1. **Zugriff autorisieren** klicken
2. Ihr Google-Konto auswählen
3. Es erscheint eine Warnung: *"Google hat diese App nicht überprüft"* — das ist Ihre eigene App, deshalb die Warnung
4. Auf **Erweitert** klicken (klein, links unten)
5. Auf **Zu LeadSimply Formular (unsicher)** klicken
6. **Zulassen**

---

## Schritt 6 — Adresse kopieren

Nach dem Bereitstellen zeigt Google eine **Web-App-URL**. Sie sieht ungefähr so aus:

```
https://script.google.com/macros/s/AKfycbx.../exec
```

**Diese Adresse kopieren.** Sie brauchen sie im nächsten Schritt.

Falls Sie den Dialog geschlossen haben: **Bereitstellen** → **Bereitstellungen verwalten** zeigt sie wieder an.

---

## Schritt 7 — Auftrag für Claude Code

Terminal öffnen, `claude` starten, dann diesen Text hineinkopieren — **ersetzen Sie vorher HIER_DIE_ADRESSE durch Ihre Web-App-URL**:

> In leitfaden/index.html gibt es ein Skript, das das Formular per fetch an Formspree sendet und danach auf /leitfaden/danke/ weiterleitet. Bitte ergänze einen zweiten, parallelen fetch an diese Adresse: HIER_DIE_ADRESSE
>
> Anforderungen: Der zweite fetch läuft mit mode: 'no-cors' und derselben FormData. Er darf die Weiterleitung nicht verzögern und nicht blockieren — wenn er fehlschlägt, passiert nichts Sichtbares, der Besucher kommt trotzdem zur Danke-Seite. Der Formspree-Aufruf bleibt unverändert und bestimmt weiterhin allein, ob es geklappt hat. Zeig mir danach den git diff.

Anschließend wie gewohnt hochladen:

```
git add .
git commit -m "Anmeldungen zusaetzlich in Google Sheet schreiben"
git push
```

---

## Schritt 8 — Testen

Zwei Minuten warten, dann `leadsimply.de/leitfaden/` mit **Cmd+Shift+R** neu laden und das Formular absenden.

Danach in der Tabelle nachsehen. Dort sollte eine neue Zeile stehen.

**Falls nicht:** Prüfen Sie zuerst, ob die Feldnamen stimmen. Das Skript erwartet `vorname`, `email` und `unternehmen` — genau so heißen die Felder in Ihrem Formular. Falls Sie später Felder umbenennen, muss das Skript mitgeändert werden.

---

## Nicht vergessen: Datenschutzerklärung

Sobald Kontaktdaten in einem Google Sheet liegen, gehört das in Ihre Datenschutzerklärung. Aktuell ist dort vermutlich nur Formspree genannt.

Zu ergänzen ist sinngemäß: dass die im Formular angegebenen Daten zusätzlich in einer Tabelle bei Google gespeichert werden, zu welchem Zweck, und wie lange. Google verarbeitet dabei auch außerhalb der EU — das ist der Punkt, auf den es rechtlich ankommt.

Diesen Absatz sollten Sie nicht aus einer Vorlage übernehmen. Wenn Sie unsicher sind, lassen Sie ihn von jemandem prüfen, der das rechtlich beurteilen kann.

# Domain, Sicherheit und Auswertung

---

# TEIL 1 · Beide Adressen sicher erreichbar

Ziel: `leadsimply.de` **und** `www.leadsimply.de` funktionieren, beide mit
Schloss-Symbol, keine Warnung.

## Was bei Strato eingestellt sein muss

**A-Records** — Hauptdomain auf GitHub. Strato erlaubt nur einen Eintrag,
das genügt:

| Typ | Host | Wert |
|-----|------|------|
| A | @ | 185.199.108.153 |

*(GitHub betreibt vier Adressen: .108.153, .109.153, .110.153, .111.153.
Falls Strato mehrere zulässt, alle vier eintragen — mehr Ausfallsicherheit.)*

**CNAME** — www auf GitHub:

| Typ | Präfix | Wert |
|-----|--------|------|
| CNAME | www | stefanbruendl77.github.io |

**Wichtig:** Der alte Eintrag `sites.ludicrous.cloud` (Funnelspot) muss weg.
Solange der steht, zeigt www weiter auf die alte Seite — daher deine
Zertifikatswarnung.

## Was bei GitHub eingestellt sein muss

Settings → Pages → **Custom domain**: `leadsimply.de` eintragen, speichern.

Danach steht dort „DNS Check in Progress". Das dauert bis zu einer Stunde.
Sobald der Haken erscheint: **Enforce HTTPS** aktivieren.

Das Häkchen lässt sich erst setzen, wenn das Zertifikat ausgestellt ist —
in der Regel innerhalb von 15 Minuten bis 24 Stunden nach korrektem DNS.

## Reihenfolge

1. Strato: alten CNAME-Wert löschen, `stefanbruendl77.github.io` eintragen
2. Strato: A-Record auf 185.199.108.153 prüfen
3. GitHub: Custom domain auf `leadsimply.de`
4. Warten, bis der grüne Haken erscheint
5. **Enforce HTTPS** anhaken

Danach leitet GitHub automatisch um: www → ohne www, http → https.
Beide Adressen zeigen dann dieselbe Seite mit Schloss.

## Wenn die Warnung bleibt

Fast immer liegt es an einem der beiden:

- Der alte Funnelspot-CNAME steht noch → löschen
- Der Browser hat die alte Seite zwischengespeichert → im privaten Fenster testen

DNS-Änderungen brauchen bis zu 24 Stunden, bis sie weltweit greifen.

---

# TEIL 2 · Besucher messen

GitHub Pages liefert keine Statistik. Du brauchst ein zusätzliches Werkzeug.

## Was ich empfehle: Plausible

**Warum nicht Google Analytics:** Es setzt Cookies, verarbeitet Daten in den
USA und erfordert damit ein Einwilligungsbanner. Das kostet dich Besucher —
ein Teil klickt weg, bevor er die Seite sieht — und du müsstest die
Datenschutzerklärung erweitern.

**Plausible** setzt keine Cookies, speichert in der EU, braucht kein Banner.
Rund 9 € im Monat, 30 Tage kostenlos testen.

### Einrichten — 10 Minuten

1. `plausible.io` — Konto anlegen, Domain `leadsimply.de` eintragen
2. Plausible zeigt dir eine Skript-Zeile
3. Diese Zeile in **jede** HTML-Datei direkt vor `</head>` einfügen

*Alternative, falls dir 9 € zu viel sind:* **Cloudflare Web Analytics** ist
kostenlos, ebenfalls cookiefrei, aber weniger komfortabel in der Auswertung.

### Was du danach siehst

| Ansicht | Was sie dir sagt |
|---------|------------------|
| Besucher gesamt | Wächst überhaupt etwas? |
| **Top Pages** | Auf welchen Seiten Menschen landen und bleiben |
| **Sources** | Woher sie kommen — LinkedIn, Google, direkt |
| Bounce Rate | Ob die Startseite hält, was sie verspricht |
| Visit Duration | Ob wirklich gelesen wird |
| **Goal: Klick auf Analyse-Call** | Die einzige Zahl, die zählt |

Das Ziel richtest du unter Goals ein: Ziel-Typ „Pageview", Pfad `/analyse-call/`.
Dann siehst du täglich, wie viele Besucher bis zur Buchungsseite kommen.

## Google Search Console — zusätzlich, kostenlos

Zeigt, was Plausible nicht kann: mit welchen **Suchbegriffen** Menschen dich
finden und auf welcher Position du stehst.

1. `search.google.com/search-console`
2. Property hinzufügen → URL-Präfix → `https://leadsimply.de`
3. Bestätigung per HTML-Datei: herunterladen, ins Repository legen, bestätigen
4. Unter Sitemaps eintragen: `sitemap.xml`

Nach zwei bis vier Wochen erscheinen dort die ersten Suchbegriffe. Das ist die
Grundlage für alle künftigen Blogthemen: Du schreibst über das, wonach
tatsächlich gesucht wird.

## UTM-Parameter — woher genau

Damit du unterscheiden kannst, ob jemand über dein Profil oder über einen
Beitrag kam:

```
Profil:        https://leadsimply.de/?utm_source=linkedin&utm_medium=profil
Beitrag:       https://leadsimply.de/?utm_source=linkedin&utm_medium=post
Signatur:      https://leadsimply.de/?utm_source=email&utm_medium=signatur
Empfehlung:    https://leadsimply.de/?utm_source=empfehlung
Podcast:       https://leadsimply.de/?utm_source=podcast&utm_medium=[name]
```

Diese Links erscheinen in Plausible unter Sources getrennt. So weißt du nach
vier Wochen, welcher Kanal tatsächlich Menschen bringt — und welcher nur
Aufwand ist.

---

# TEIL 3 · Wochenrhythmus

Fünf Minuten, jeden Montag:

| Zahl | Wo | Bedeutung |
|------|-----|-----------|
| Besucher letzte Woche | Plausible | Wächst es? |
| Meistbesuchte Seite | Plausible → Top Pages | Was zieht? |
| Stärkste Quelle | Plausible → Sources | Wo lohnt der Aufwand? |
| Klicks auf /analyse-call/ | Plausible → Goals | Der eigentliche Wert |
| Gebuchte Gespräche | TidyCal | Das Ergebnis |

**Die entscheidende Verhältniszahl:** Besucher → Klicks auf Analyse-Call.
Unter 3 % heißt: Die Seite überzeugt noch nicht. Über 5 % heißt: Sie
funktioniert, du brauchst nur mehr Besucher.

Diese eine Zahl sagt dir, ob du an der Seite arbeiten musst oder an der
Reichweite. Das ist der wichtigste Unterschied im ganzen Marketing.

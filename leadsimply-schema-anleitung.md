# Schema.org für leadsimply.de — Anleitung zum Einfügen

## Was das ist (in einem Satz)

Ein unsichtbarer Code-Block, der Google und KI-Suchmaschinen direkt sagt:
"Das ist Stefan Bründl, Berater für Fluktuation, Weil der Stadt."
Besucher sehen davon nichts — er steht nur im Quelltext.

## Wo das hinkommt

In jede HTML-Datei, ganz am Ende des `<head>`-Bereichs — also direkt **vor** der Zeile `</head>`.

```html
    ...
    <script type="application/ld+json">   <-- hier rein
    ...
    </script>
  </head>
```

## Wichtige Regel

Schema darf nur behaupten, was auf der Seite auch **sichtbar** steht.

Deshalb enthalten die Leistungsblöcke **keine Preise** — die stehen bei Ihnen nicht auf der Seite. Falls Sie später Preise sichtbar auf eine Leistungsseite schreiben, können Sie dort diesen Zusatz ergänzen (Beispiel Fluktuation-Diagnose, Komma davor nicht vergessen):

```
  "offers": {
    "@type": "Offer",
    "price": "2400",
    "priceCurrency": "EUR",
    "url": "https://leadsimply.de/fluktuation-diagnose/",
    "availability": "https://schema.org/InStock"
  }
```

---

# BLOCK A — auf ALLE Seiten

Dieser Block ist auf jeder der 23 Seiten identisch. Einmal kopieren, überall einfügen.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "ProfessionalService",
      "@id": "https://leadsimply.de/#organisation",
      "name": "LeadSimply",
      "legalName": "Vario Brüdoservice GmbH",
      "url": "https://leadsimply.de/",
      "logo": {
        "@type": "ImageObject",
        "url": "https://leadsimply.de/bilder/logo.png"
      },
      "image": "https://leadsimply.de/og-bild.jpg",
      "description": "Beratung für Geschäftsführer mittelständischer Unternehmen mit 10 bis 300 Mitarbeitenden zur messbaren Senkung der Fluktuation und zur Bindung von Leistungsträgern.",
      "email": "info@leadsimply.de",
      "founder": { "@id": "https://leadsimply.de/#stefan" },
      "employee": { "@id": "https://leadsimply.de/#stefan" },
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "Neckarstrasse 2",
        "postalCode": "71263",
        "addressLocality": "Weil der Stadt",
        "addressRegion": "Baden-Württemberg",
        "addressCountry": "DE"
      },
      "geo": {
        "@type": "GeoCoordinates",
        "latitude": 48.7503,
        "longitude": 8.8706
      },
      "areaServed": {
        "@type": "Country",
        "name": "Deutschland"
      },
      "priceRange": "€€€",
      "knowsLanguage": "de-DE",
      "sameAs": [
        "https://www.linkedin.com/in/stefan-bruendl/"
      ]
    },
    {
      "@type": "Person",
      "@id": "https://leadsimply.de/#stefan",
      "name": "Stefan Bründl",
      "givenName": "Stefan",
      "familyName": "Bründl",
      "url": "https://leadsimply.de/ueber-stefan/",
      "image": "https://leadsimply.de/bilder/stefan-about.jpg",
      "jobTitle": "Berater für Mitarbeiterbindung und Fluktuation",
      "description": "Berater mit über 20 Jahren eigener Führungsverantwortung, 1.300+ geführten Mitarbeitenden und 135 Mio. € Umsatzverantwortung. Kennt den Arbeitsmarkt aus drei Rollen: als Führungskraft, als Personaldienstleister und als Einstellender.",
      "worksFor": { "@id": "https://leadsimply.de/#organisation" },
      "knowsAbout": [
        "Fluktuation",
        "Mitarbeiterbindung",
        "Führung im Mittelstand",
        "Leistungsträger halten",
        "Abwerbung",
        "Onboarding"
      ],
      "alumniOf": [
        { "@type": "CollegeOrUniversity", "name": "Universität Stuttgart" },
        { "@type": "CollegeOrUniversity", "name": "Universität Hohenheim" },
        { "@type": "CollegeOrUniversity", "name": "London Business School" },
        { "@type": "CollegeOrUniversity", "name": "TIAS School for Business and Society, Tilburg" },
        { "@type": "CollegeOrUniversity", "name": "INSEAD Paris" }
      ],
      "sameAs": [
        "https://www.linkedin.com/in/stefan-bruendl/"
      ]
    },
    {
      "@type": "WebSite",
      "@id": "https://leadsimply.de/#website",
      "url": "https://leadsimply.de/",
      "name": "LeadSimply",
      "inLanguage": "de-DE",
      "publisher": { "@id": "https://leadsimply.de/#organisation" }
    }
  ]
}
</script>
```

---

# BLOCK B — nur Startseite

Zusätzlich zu Block A einfügen.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "@id": "https://leadsimply.de/#webpage",
  "url": "https://leadsimply.de/",
  "name": "Fluktuation senken im Mittelstand",
  "description": "Niemand wird abgeworben, der zufrieden ist. Stefan Bründl zeigt Geschäftsführern, woran sie eine Kündigung Monate vorher erkennen.",
  "inLanguage": "de-DE",
  "isPartOf": { "@id": "https://leadsimply.de/#website" },
  "about": { "@id": "https://leadsimply.de/#stefan" },
  "primaryImageOfPage": "https://leadsimply.de/og-bild.jpg"
}
</script>
```

---

# BLOCK C — die drei Leistungsseiten

Jeweils zusätzlich zu Block A.

## C1 — /fluktuation-diagnose/

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Service",
  "@id": "https://leadsimply.de/fluktuation-diagnose/#service",
  "name": "Fluktuation-Diagnose",
  "serviceType": "Fluktuationsanalyse",
  "url": "https://leadsimply.de/fluktuation-diagnose/",
  "description": "Strukturierte Analyse der Fluktuation im Unternehmen: Wer geht, wann im Lebenszyklus und aus welchem Grund. Ergebnis ist eine Einordnung der eigenen Quote und der wichtigste Hebel.",
  "provider": { "@id": "https://leadsimply.de/#organisation" },
  "areaServed": { "@type": "Country", "name": "Deutschland" },
  "audience": {
    "@type": "BusinessAudience",
    "name": "Geschäftsführer mittelständischer Unternehmen mit 10 bis 300 Mitarbeitenden"
  }
}
</script>
```

## C2 — /90-tage-programm/

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Service",
  "@id": "https://leadsimply.de/90-tage-programm/#service",
  "name": "90-Tage-Programm",
  "serviceType": "Führungs- und Bindungsprogramm",
  "url": "https://leadsimply.de/90-tage-programm/",
  "description": "Begleitung über 90 Tage: Aufbau von Führungsroutinen, Frühwarnsystem und konkreten Maßnahmen zur Bindung von Leistungsträgern.",
  "provider": { "@id": "https://leadsimply.de/#organisation" },
  "areaServed": { "@type": "Country", "name": "Deutschland" },
  "audience": {
    "@type": "BusinessAudience",
    "name": "Geschäftsführer mittelständischer Unternehmen mit 10 bis 300 Mitarbeitenden"
  }
}
</script>
```

## C3 — /retainer/

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Service",
  "@id": "https://leadsimply.de/retainer/#service",
  "name": "Sparring-Retainer",
  "serviceType": "Laufende Führungsberatung",
  "url": "https://leadsimply.de/retainer/",
  "description": "Laufendes Sparring für Geschäftsführer zu Führung, Mitarbeiterbindung und konkreten Personalentscheidungen.",
  "provider": { "@id": "https://leadsimply.de/#organisation" },
  "areaServed": { "@type": "Country", "name": "Deutschland" }
}
</script>
```

---

# BLOCK D — /ueber-stefan/

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "ProfilePage",
  "@id": "https://leadsimply.de/ueber-stefan/#webpage",
  "url": "https://leadsimply.de/ueber-stefan/",
  "name": "Über Stefan Bründl",
  "inLanguage": "de-DE",
  "isPartOf": { "@id": "https://leadsimply.de/#website" },
  "mainEntity": { "@id": "https://leadsimply.de/#stefan" }
}
</script>
```

---

# BLOCK E — /rechner/ (Kostenrechner)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "@id": "https://leadsimply.de/rechner/#app",
  "name": "Fluktuationskosten-Rechner",
  "url": "https://leadsimply.de/rechner/",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "inLanguage": "de-DE",
  "description": "Kostenloser Rechner: Was kostet Fluktuation Ihr Unternehmen pro Jahr? Berücksichtigt direkte, indirekte und versteckte Kosten.",
  "publisher": { "@id": "https://leadsimply.de/#organisation" },
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "EUR"
  }
}
</script>
```

---

# BLOCK F — /leitfaden/ (12 Frühwarnsignale)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "@id": "https://leadsimply.de/leitfaden/#webpage",
  "url": "https://leadsimply.de/leitfaden/",
  "name": "12 Frühwarnsignale, bevor jemand kündigt",
  "inLanguage": "de-DE",
  "isPartOf": { "@id": "https://leadsimply.de/#website" },
  "description": "Kostenloser Leitfaden auf sechs Seiten: zwölf Signale in vier Bereichen und vier Fragen für das Gespräch.",
  "mainEntity": {
    "@type": "DigitalDocument",
    "name": "Leitfaden: 12 Frühwarnsignale",
    "author": { "@id": "https://leadsimply.de/#stefan" },
    "inLanguage": "de-DE"
  }
}
</script>
```

---

# BLOCK G — /blog/ Übersichtsseite

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Blog",
  "@id": "https://leadsimply.de/blog/#blog",
  "url": "https://leadsimply.de/blog/",
  "name": "LeadSimply Blog",
  "inLanguage": "de-DE",
  "description": "Beiträge zu Fluktuation, Mitarbeiterbindung und Führung im Mittelstand.",
  "publisher": { "@id": "https://leadsimply.de/#organisation" },
  "author": { "@id": "https://leadsimply.de/#stefan" }
}
</script>
```

## Vorlage für einzelne Blogartikel

Für jeden Artikel einzeln, mit ausgetauschten Werten:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "HIER DIE ÜBERSCHRIFT DES ARTIKELS",
  "url": "https://leadsimply.de/blog/ARTIKEL-ADRESSE/",
  "datePublished": "2026-08-26",
  "dateModified": "2026-08-26",
  "inLanguage": "de-DE",
  "author": { "@id": "https://leadsimply.de/#stefan" },
  "publisher": { "@id": "https://leadsimply.de/#organisation" },
  "isPartOf": { "@id": "https://leadsimply.de/blog/#blog" },
  "description": "HIER EIN SATZ, WORUM ES GEHT"
}
</script>
```

Datum immer im Format `JAHR-MONAT-TAG` schreiben, also `2026-08-26`.

---

# BLOCK H — /presse/

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "@id": "https://leadsimply.de/presse/#webpage",
  "url": "https://leadsimply.de/presse/",
  "name": "Presse und Medien",
  "inLanguage": "de-DE",
  "isPartOf": { "@id": "https://leadsimply.de/#website" },
  "about": { "@id": "https://leadsimply.de/#stefan" },
  "description": "Wo über die Arbeit von Stefan Bründl gesprochen wird: Porträt in der WirtschaftsWoche 07/2026 und Podcast-Gespräche."
}
</script>
```

---

# BLOCK I — /analyse-call/

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "@id": "https://leadsimply.de/analyse-call/#webpage",
  "url": "https://leadsimply.de/analyse-call/",
  "name": "Kostenloses Erstgespräch buchen",
  "inLanguage": "de-DE",
  "isPartOf": { "@id": "https://leadsimply.de/#website" },
  "description": "45 Minuten, kostenlos, kein Verkaufsgespräch. Ergebnis: Einschätzung der eigenen Fluktuation, der größte Hebel und ein konkreter nächster Schritt.",
  "mainEntity": {
    "@type": "Service",
    "name": "Erstgespräch",
    "provider": { "@id": "https://leadsimply.de/#organisation" },
    "offers": {
      "@type": "Offer",
      "price": "0",
      "priceCurrency": "EUR"
    }
  }
}
</script>
```

---

# Danach: prüfen

1. Änderungen zu GitHub hochladen, ein bis zwei Minuten warten.
2. Auf **validator.schema.org** die Adresse einer Seite eingeben und auf Fehler prüfen.
3. Zusätzlich den **Google Rich Results Test** laufen lassen (search.google.com/test/rich-results).

Grüne Häkchen oder gar keine Meldung heißt: passt.
Rote Fehler heißt meistens: irgendwo fehlt ein Komma oder eine geschweifte Klammer.

## Häufigster Anfängerfehler

Nach dem letzten Eintrag vor einer schließenden Klammer `}` darf **kein Komma** stehen.
Falsch: `"name": "Test",` gefolgt von `}`
Richtig: `"name": "Test"` gefolgt von `}`

---

# Restseiten (Impressum, Datenschutz, Leistungen, Abwerber-Perspektive)

Dort reicht Block A allein. Diese Seiten sollen bewusst nicht prominent in Suchergebnissen erscheinen.

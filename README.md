# GST Lernpfade

Interaktive HTML-Lerninhalte für den Unterricht, veröffentlicht über Cloudflare Pages.

## Struktur

```
index.html                  Startseite mit allen Lernpfaden
fonts/                      Schriften lokal (Lexend, Atkinson Hyperlegible, SIL OFL) – keine Google-Server
Physik8/
  reflexion-spiegel.html    Reflexion am ebenen Spiegel
  spiegelbild-uebungen.html Spiegelbild konstruieren · Üben (Lichtwege, Winkelspiegel)
  lichtbrechung-experiment.html  Lichtbrechung 1: Schülerexperiment
  lichtbrechung-theorie.html     Lichtbrechung 2: Theorie
  lichtbrechung-uebungen.html    Lichtbrechung 3: Üben
Physik9/
  energie-einfuehrung.html  Was ist Energie? (Energieformen, Stationen, Energiewandler)
  lageenergie.html          Lageenergie (Fall-Labor, E = m · g · h, Nullniveau)
  energieerhaltung.html     Energieerhaltung und Energieentwertung
```

Jede Klasse bzw. jedes Fach bekommt einen eigenen Ordner. Die Adresse einer Seite ist der Pfad ohne `.html`,
z. B. `/Physik8/reflexion-spiegel`. Groß- und Kleinschreibung der Ordner gehört zur Adresse.

## Neuen Lernpfad hinzufügen

1. HTML-Datei in den passenden Ordner legen (Ordner bei Bedarf neu anlegen).
2. In `index.html` in der Liste `KURSE` einen Eintrag ergänzen. Für ein Vorschaubild im Objekt `BILDER` ein kleines SVG (320 × 140) anlegen und im Eintrag mit `bild:'name'` verknüpfen.
3. Committen und pushen – Cloudflare veröffentlicht automatisch.

## Cloudflare-Pages-Einstellungen

- Framework preset: None
- Build command: (leer)
- Build output directory: `/`

## Schriften

Neue Seiten binden die Schriften mit `<link rel="stylesheet" href="/fonts/fonts.css">` ein – nicht über Google Fonts.

## Schul-Branding

Farben, Logo und Mosaik stammen aus der PowerPoint-Vorlage der Schule und liegen in `brand/`:

- `brand/brand.css` – gemeinsames Branding für alle Lernpfade (Kopf in Schiefergrau mit Pixel-Mosaik, Farbleiste, Logo in Navigation und Fuß, Überschriften in Source Sans 3)
- `brand/logo.svg`, `brand/mosaik-links.svg`, `brand/mosaik-rechts.svg`
- Farben: Schiefer #3E4B4C, #5F6F74, Graugrün #76989D, #ACBDC3, #C9D2D3, Hellgrau #E4E7E9, Akzentgelb #FCBE00

Neue Lernpfade binden nach ihrem `<style>`-Block ein: `<link rel="stylesheet" href="/brand/brand.css">`.
Die fachlichen Farben der Lernpfade (z. B. Laserrot, Energie-Farben) bleiben bewusst erhalten.
Schrift: Source Sans 3 (SIL OFL) als freie Alternative zur Hausschrift Myriad Pro.

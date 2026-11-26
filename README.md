# GST Lernpfade

Interaktive HTML-Lerninhalte für den Unterricht, veröffentlicht über Cloudflare Pages.

## Struktur

```
index.html                  Startseite mit allen Lernpfaden
impressum.html              Impressum, Datenschutz, Urheberrecht/KI, Haftung (Link im Fuß jeder Seite)
feedback/                   Feedback: Worker (worker.js), Datenbank-Aufbau (schema.sql), Anleitung AUSWERTEN.md
wrangler.jsonc              Cloudflare-Worker „lernapps“ (statische Dateien + /api/feedback, D1 gst-feedback)
.assetsignore               Dateien, die nicht öffentlich ausgeliefert werden
fonts/                      Schriften lokal (Lexend, Atkinson Hyperlegible, SIL OFL) – keine Google-Server
Physik8/
  reflexion-spiegel.html    Reflexion am ebenen Spiegel
  spiegelbild-uebungen.html Spiegelbild konstruieren · Üben (Lichtwege, Winkelspiegel)
  lichtbrechung-experiment.html  Lichtbrechung 1: Schülerexperiment
  lichtbrechung-theorie.html     Lichtbrechung 2: Theorie
  lichtbrechung-uebungen.html    Lichtbrechung 3: Üben
  kraefte-wirkungen.html    Kräfte 1 · Was ist eine Kraft? (Kraftwirkungen, Kraftpfeil, Newton)
  gewichtskraft-masse.html  Kräfte 2 · Gewichtskraft und Masse (Gravitation, Ortsfaktor, F_G = m · g)
  hookesches-gesetz.html    Kräfte 3 · Kräfte messen: hookesches Gesetz (Feder-Labor, Federkonstante)
  kraefte-newton.html       Kräfte 4 · Mehrere Kräfte und Newtons Gesetze (Kräftegleichgewicht, Trägheit, Kraft = Gegenkraft)
  schall-entstehung.html    Akustik 1 · Wie entsteht Schall? (Schallquelle, -leiter, -empfänger, Vakuum, Schwingungen, Lineal-Labor)
Physik9/
  energie-einfuehrung.html  Was ist Energie? (Energieformen, Stationen, Energiewandler)
  lageenergie.html          Lageenergie (Fall-Labor, E = m · g · h, Nullniveau)
  energieerhaltung.html     Energieerhaltung und Energieentwertung
  wirkungsgrad.html         Der Wirkungsgrad (Aufwand und Nutzen, η = E_Nutzen : E_Aufwand, Energieketten)
  <lernpfad>-heftaufschrieb.pdf / <lernpfad>-uebungsblatt.pdf  Druckversionen zu allen vier Energie-Lernpfaden
Physik11/
  kraft-grundlagen.html     1 · Kraft – Grundlagen (Wirkungen, Kraftpfeil, Gewichtskraft, Trägheit)
  kraefteaddition.html      2 · Kräfteaddition und Gleichgewicht (Parallelogramm, Kräfteplan)
  kraeftezerlegung.html     3 · Kräftezerlegung (grafisch und rechnerisch)
  schiefe-ebene.html        4 · Schiefe Ebene (Hangabtriebs- und Normalkraft)
  schiefe-ebene-heftaufschrieb.pdf  Heftaufschrieb zum Ausfüllen (Lückentext, eigene Zeichnung)
  schiefe-ebene-uebungsblatt.pdf    Übungsblatt mit Platz für den Rechenweg (beide: Download im Lernpfad, Symbol auf der Kachel)
  newton-reibung.html       5 · Newtonsche Gesetze und Reibung
  impuls-grundlagen.html    Impuls 1 · Der Impuls – eine neue Größe (p = m · v, Einheit, Vektor, Alltag)
  stoesse-impulserhaltung.html  Impuls 2 · Stöße und Impulserhaltung (Stoß-Labor, Sonderfälle, Wagen-Versuche)
  rueckstoss.html           Impuls 3 · Das Rückstoßprinzip
  kraftstoss.html           Impuls 4 · Kraftstoß und Newtons Axiome (Δp = F · Δt)
  elastischer-stoss.html    Impuls 5 · Stöße quantitativ (IES + EES, Energiebilanz)
```

Jede Klasse bzw. jedes Fach bekommt einen eigenen Ordner. Die Adresse einer Seite ist der Pfad ohne `.html`,
z. B. `/Physik8/reflexion-spiegel`. Groß- und Kleinschreibung der Ordner gehört zur Adresse.

## Neuen Lernpfad hinzufügen

1. HTML-Datei in den passenden Ordner legen (Ordner bei Bedarf neu anlegen).
2. In `index.html` in der Liste `KURSE` den Lernpfad eintragen. Die Liste ist gegliedert nach Stufe (`Mittelstufe`/`Oberstufe`) → Klasse → Thema (`themen`) → Lernpfade (`seiten`). Neues Thema: weiteren Eintrag in `themen`; neue Klasse: weiteren Block mit `stufe`, `klasse`, `fach`, `ordner`. Die Startseite baut daraus Stufen-Auswahl, Sprungmarken zu den Klassen, aufklappbare Themen (starten eingeklappt) und die Suche automatisch auf. Für ein Vorschaubild im Objekt `BILDER` ein kleines SVG (320 × 140) anlegen und im Eintrag mit `bild:'name'` verknüpfen.
3. Committen und pushen – Cloudflare veröffentlicht automatisch.

## Druckversionen

Zu einem Lernpfad kann es zwei PDFs geben: einen Heftaufschrieb zum Ausfüllen (Lückentext, Zeichnungen selbst anfertigen) und ein Übungsblatt (Aufgaben mit Platz für den Rechenweg, Kontrolle online).
Vorlage und Anleitung: `tools/druck/` (LIESMICH.md). In `KURSE` mit `druck:'Heftaufschrieb und Übungsblatt zum Drucken'` markieren (Symbol auf der Kachel); der Download-Link `a.arbeitsblatt` steht im Lernpfad selbst (Kopf, „Festhalten“ und „Üben“). Verbindliche Regeln: `CLAUDE.md`, Abschnitt „Druckversionen“.

## Cloudflare-Pages-Einstellungen

- Framework preset: None
- Build command: (leer)
- Build output directory: `/`

## Schriften

Neue Seiten binden die Schriften mit `<link rel="stylesheet" href="/fonts/fonts.css">` ein – nicht über Google Fonts.

## Schul-Branding

Farben, Logo und Mosaik stammen aus der PowerPoint-Vorlage der Schule und liegen in `brand/`:

- `brand/brand.css` – gemeinsames Branding für alle Lernpfade (Kopf in Schiefergrau mit Pixel-Mosaik, Farbleiste, Logo in Navigation und Fuß, Überschriften in Source Sans 3)
- `brand/mischen.js` – mischt bei jedem Laden die Reihenfolge der Antworten (Dropdowns, Multiple Choice, Mehrfachauswahl, `[data-mischen]`), damit sie die Lösung nicht verrät; Ausnahme mit `data-fest`
- `brand/theme.js` – Hell/Dunkel-Umschaltung (Wahl auf der Startseite oder per Knopf in der Navigation, gilt für alle Seiten, gespeichert nur im Browser)
- `brand/logo.svg`, `brand/mosaik-links.svg`, `brand/mosaik-rechts.svg`
- `brand/piktos.svg` – Piktogramme für Aufgaben und Quiz (Muster `.mitbild`, `.mitpk`, MC-Knöpfe mit Bild in `brand.css`; Katalog: `tools/piktos-katalog.html`; Regeln: CLAUDE.md)
- Farben: Schiefer #3E4B4C, #5F6F74, Graugrün #76989D, #ACBDC3, #C9D2D3, Hellgrau #E4E7E9, Akzentgelb #FCBE00

Neue Lernpfade binden im `<head>` nach `/fonts/fonts.css` `<script src="/brand/theme.js"></script>` ein und nach ihrem `<style>`-Block `<link rel="stylesheet" href="/brand/brand.css">`.
`brand.css` legt das gemeinsame Farbsystem für hell und dunkel fest (Schiefer-Grautöne, dunkles Graugrün für Bedienelemente, Merke und Heftaufschrieb, Akzentgelb nur als Markierung).
Die fachlichen Farben der Lernpfade (z. B. Laserrot, Energie-Farben) bleiben bewusst erhalten.
Schrift: Source Sans 3 (SIL OFL) als freie Alternative zur Hausschrift Myriad Pro.

## Formeln

Formeln werden mit KaTeX gesetzt (lokal in `katex/`, keine externen Server). Im Quelltext stehen sie lesbar in `<f-m>…</f-m>`,
z. B. `<f-m>h = E<sub>L</sub> : (m · g)</f-m>`. `katex/formel.js` setzt sie beim Anzeigen: Variablen kursiv, Einheiten aufrecht,
`:` und `/` als Bruchstrich, Dezimalkomma und Tausender-Abstand korrekt. Das gilt auch für Rückmeldungen, die erst per Skript erscheinen.

Neue Lernpfade binden nach `brand.css` ein:

```html
<link rel="stylesheet" href="/katex/katex.min.css">
<script defer src="/katex/katex.min.js"></script>
<script defer src="/katex/formel.js"></script>
```

Formeln müssen nicht von Hand markiert werden: `python3 tools/formeln_markieren.py Physik9/neu.html` erkennt Formeln
(auch in Rückmeldungen im Skript) und markiert sie. Der Doppelpunkt zählt nur mit Leerzeichen (` : `) als Geteilt-Zeichen.

Die Impuls-Lernpfade heben die Heftaufschriebe als eigene Kästen „✎ HEFTAUFSCHRIEB“ hervor (Navigation: „Heft“).
Formeln: `kg·m/s` und `N·s` gelten als Einheiten, `Δp`, `Δt` usw. als ein Formelzeichen, Minus am Anfang einer Klammer ist erlaubt, z. B. `2,0 kg · (−6,0 m/s)`.

## Feedback

Jeder Lernpfad bindet `<script defer src="/brand/feedback.js"></script>` ein (nach `formel.js`). Das Skript setzt einen
Knopf „Feedback“ in die Navigation und in den Fuß und lädt `brand/feedback.css`. Auf der Startseite steht der Knopf im
Platzhalter `<p data-feedback></p>` (allgemeines Feedback). Im Formular wählt man die Rolle Schüler/in oder Lehrer/in. Rückmeldungen gehen anonym an `/api/feedback` (Worker in
`feedback/worker.js`) und werden in Cloudflare D1 (`gst-feedback`) gespeichert, vorgefiltert und vorbewertet.
Auswerten: siehe `feedback/AUSWERTEN.md` – oder Claude bitten: „Werte das neue Feedback aus.“

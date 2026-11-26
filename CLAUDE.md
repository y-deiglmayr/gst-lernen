# Projekt „Physik Unterricht“ – GST-Lernpfade

Interaktive Lernpfade (je eine HTML-Datei, alles inline) für das Technische Gymnasium BW. Sprache: Deutsch, du-Ansprache.
Cloudflare veröffentlicht automatisch von `main`: https://physik.party/ (eigene Domain; alt: lernapps.gst-lernen.workers.dev). Adresse ohne `.html`. QR-Codes und Links immer mit physik.party.
Details zu Aufbau, Branding und Formeln: `README.md`.

**Diese Regeln gelten zusätzlich zum Skill „gst-lernpfad“ und haben Vorrang, wo der Skill etwas anderes sagt**
(z. B. beschreibt der Skill noch einen „dunklen Labor-Kopf“ – gilt nicht mehr).

## Gestaltung (Schul-Branding)
- Nach dem `<style>`-Block jeder Lernpfad-Seite einbinden:
  ```html
  <link rel="stylesheet" href="/brand/brand.css">
  <link rel="stylesheet" href="/katex/katex.min.css">
  <script defer src="/katex/katex.min.js"></script>
  <script defer src="/katex/formel.js"></script>
  <script defer src="/brand/feedback.js"></script>
  <script defer src="/brand/mischen.js"></script>
  ```
- Schulfarben: Schiefer #3E4B4C, #5F6F74, Graugrün #76989D, #ACBDC3, #C9D2D3, Hellgrau #E4E7E9, Akzentgelb #FCBE00.
  Keine eigenen Dunkelblau-Töne für Kopf oder Vorschaubilder (Vorschaubild-Grund: #3E4B4C bzw. #2f393a).
- Fachliche Farben bleiben (Optik: Laserrot; Energie: E_L blau, E_B grün, E_therm rot …).
- Farbsystem und Darkmode stehen zentral in `brand/brand.css` (Grundflächen, Text, Linien hell/dunkel in Schiefer-Tönen; Bedienelemente, Merke, Heft-Überschriften in dunklem Graugrün `--gst-acc`; Akzentgelb `--gst-mark` nur als Markierung: Fortschritt, Fokus, kleine Quadrate). Keine eigenen Akzentfarben (Orange, Laserrot) für Navigation, Knöpfe, Merke oder Heft.
- Heftaufschriebe sind überall deutlich grün (`--gst-heft`, zentral in brand.css): `.heft`, Kästen `.heftbox` mit Kopf `.hb-head`, aufklappbare Musterlösung `details.reveal` mit `.heft` darin, `.insheft`, `a.heftlink`. Keine eigenen Farben dafür in den Seiten.
- Darkmode: `<script src="/brand/theme.js"></script>` direkt nach `/fonts/fonts.css` im `<head>` (ohne defer). Es setzt `data-theme` auf `<html>` (localStorage `gst-theme`) und fügt in Lernpfaden einen Hell/Dunkel-Knopf in `nav .wrap` ein; auf der Startseite steht die Auswahl Automatisch/Hell/Dunkel im Platzhalter `data-theme-switch`. Farben in Lernpfaden immer mit `light-dark(hell,dunkel)`, dunkle Werte in Schiefer-Tönen (z. B. #1b2122, #232b2d), kein Dunkelblau.
- Schriften nur lokal über `/fonts/fonts.css` (Überschriften Source Sans 3 kommt über brand.css), keine Google Fonts, keine externen Dienste.
- Im Fuß jedes Lernpfads (am Ende von `footer .wrap`): `<p class="rechtl"><a href="/impressum">Impressum · Datenschutz</a></p>`. Impressum, Datenschutz, KI-Hinweis und Haftung stehen zentral in `impressum.html`; neue externe Dienste nur nach Ergänzung dort.
- QR-Code der eigenen Live-Adresse im Kopf (Python `segno`), Startseite-Eintrag in `KURSE` + Vorschaubild in `BILDER`, README-Liste ergänzen.

## Formeln
- Formeln normal schreiben, z. B. `h = E<sub>L</sub> : (m · g)`; Geteilt-Zeichen „ : “ mit Leerzeichen.
- Vor dem Veröffentlichen: `python3 tools/formeln_markieren.py <datei>` – markiert Formeln mit `<f-m>…</f-m>`, `katex/formel.js` setzt sie.
- Mit Playwright prüfen: keine Konsolen-Warnung „Formel nicht gesetzt“, kein sichtbares `<f-m>` im Text.

## Didaktik
- Phasen: Einstieg/Wiederholen → Entdecken → Festhalten → Üben (★/★★/★★★, Tipps, Lösungen).
- Antwortreihenfolge nie fest: `brand/mischen.js` mischt bei jedem Laden Dropdowns (`select` mit `data-a`/`data-ans` oder in `.selbox`/`[data-task]`, Platzhalter „…“ bleibt oben), Multiple-Choice-Knöpfe (`.mc button[data-k]`/`[data-j]`), Mehrfachauswahl (`.multi label`) und Kinder von `[data-mischen]` (z. B. Wortbausteine), auch per JS erzeugte. Prüfen-Logik daher immer über Werte/Kennungen, nie über Positionen. Reine Zahlenlisten bleiben geordnet; Ausnahme per `data-fest`.
- Multiple Choice: nach Fehlversuch Hinweis und kurze Denkpause (kein Durchraten).
- Pro Lernpfad 2–3 „Begründe“-Aufträge mit Musterbegründung (erst nach eigenem Satz sichtbar).
- Konstruktionen: „Erst im Heft konstruieren, dann hier prüfen.“
- Simulationen dürfen nichts „entdecken“ lassen, was physikalisch nicht stimmt; Modellannahmen (z. B. ohne Reibung) nennen.
- Fortschritt nur im Browser (localStorage), keine Datenerhebung.

## Feedback
- Schüler-Feedback liegt anonym in Cloudflare D1 `gst-feedback` (ID 17e96367-7f67-4c99-b1f8-ff75f1f89423). Abrufen und Auswerten nach `feedback/AUSWERTEN.md`: nur Einträge mit Stellenbezug, die sich nachprüfen lassen und fachlich stimmen; dem Nutzer erst eine Liste vorlegen, dann ändern, danach `status` setzen.
- `wrangler.jsonc` + `feedback/worker.js` bilden den Worker „lernapps“; `.assetsignore` hält interne Dateien (CLAUDE.md, tools/, feedback/) aus der Auslieferung.

## Prüfen und Veröffentlichen
- Lokal mit `python3 -m http.server` + Playwright: keine JS-Fehler, Desktop 1280 px und Handy 390 px ohne seitliches Scrollen, Aufgaben durchklicken, Screenshots ansehen.
- Vor dem Push `git fetch` und auf neue Commits achten – auf dem PC des Nutzers (yannik-pc) kann es ungepushte Änderungen geben.
- Fertige Lernpfade direkt auf `main` pushen, danach Live-Adresse prüfen.
- Sicherung nach `D:\OneDrive\Unterricht WBS\Lernapps`: alle HTML-Dateien **und** die Ordner `brand/`, `fonts/`, `katex/`.
  Aus einer Cloud-Session ohne verbundenen PC stattdessen ein ZIP schicken und sagen, dass die Sicherung nachgeholt werden muss.

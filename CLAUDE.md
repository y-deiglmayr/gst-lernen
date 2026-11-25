# Projekt „Physik Unterricht“ – GST-Lernpfade

Interaktive Lernpfade (je eine HTML-Datei, alles inline) für das Technische Gymnasium BW. Sprache: Deutsch, du-Ansprache.
Cloudflare veröffentlicht automatisch von `main`: https://lernapps.gst-lernen.workers.dev/ (Adresse ohne `.html`).
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
  ```
- Schulfarben: Schiefer #3E4B4C, #5F6F74, Graugrün #76989D, #ACBDC3, #C9D2D3, Hellgrau #E4E7E9, Akzentgelb #FCBE00.
  Keine eigenen Dunkelblau-Töne für Kopf oder Vorschaubilder (Vorschaubild-Grund: #3E4B4C bzw. #2f393a).
- Fachliche Farben bleiben (Optik: Laserrot; Energie: E_L blau, E_B grün, E_therm rot …).
- Schriften nur lokal über `/fonts/fonts.css` (Überschriften Source Sans 3 kommt über brand.css), keine Google Fonts, keine externen Dienste.
- QR-Code der eigenen Live-Adresse im Kopf (Python `segno`), Startseite-Eintrag in `KURSE` + Vorschaubild in `BILDER`, README-Liste ergänzen.

## Formeln
- Formeln normal schreiben, z. B. `h = E<sub>L</sub> : (m · g)`; Geteilt-Zeichen „ : “ mit Leerzeichen.
- Vor dem Veröffentlichen: `python3 tools/formeln_markieren.py <datei>` – markiert Formeln mit `<f-m>…</f-m>`, `katex/formel.js` setzt sie.
- Mit Playwright prüfen: keine Konsolen-Warnung „Formel nicht gesetzt“, kein sichtbares `<f-m>` im Text.

## Didaktik
- Phasen: Einstieg/Wiederholen → Entdecken → Festhalten → Üben (★/★★/★★★, Tipps, Lösungen).
- Multiple Choice: nach Fehlversuch Hinweis und kurze Denkpause (kein Durchraten).
- Pro Lernpfad 2–3 „Begründe“-Aufträge mit Musterbegründung (erst nach eigenem Satz sichtbar).
- Konstruktionen: „Erst im Heft konstruieren, dann hier prüfen.“
- Simulationen dürfen nichts „entdecken“ lassen, was physikalisch nicht stimmt; Modellannahmen (z. B. ohne Reibung) nennen.
- Fortschritt nur im Browser (localStorage), keine Datenerhebung.

## Prüfen und Veröffentlichen
- Lokal mit `python3 -m http.server` + Playwright: keine JS-Fehler, Desktop 1280 px und Handy 390 px ohne seitliches Scrollen, Aufgaben durchklicken, Screenshots ansehen.
- Vor dem Push `git fetch` und auf neue Commits achten – auf dem PC des Nutzers (yannik-pc) kann es ungepushte Änderungen geben.
- Fertige Lernpfade direkt auf `main` pushen, danach Live-Adresse prüfen.
- Sicherung nach `D:\OneDrive\Unterricht WBS\Lernapps`: alle HTML-Dateien **und** die Ordner `brand/`, `fonts/`, `katex/`.
  Aus einer Cloud-Session ohne verbundenen PC stattdessen ein ZIP schicken und sagen, dass die Sicherung nachgeholt werden muss.

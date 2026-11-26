# Druckversionen (Arbeitsblätter zu Lernpfaden)

Jede Druckvorlage ist eine HTML-Seite in diesem Ordner (A4, Schul-CI, Formeln wie in den Lernpfaden mit `<f-m>`).
Das fertige PDF liegt neben dem Lernpfad, z. B. `Physik11/schiefe-ebene-uebungsblatt.pdf`, und wird in `index.html`
beim Lernpfad mit `druck:'Heftaufschrieb und Übungsblatt zum Drucken'` (Text für das Symbol) mit einem kleinen Symbol auf der Kachel markiert. Der Download selbst steht im Lernpfad: `<a class="arbeitsblatt" href="…pdf" download>` (Stil in brand.css) im Kopf unter den Phasen und am Anfang von „Festhalten“ (Heftaufschrieb) bzw. „Üben“ (Übungsblatt).

Zu jedem Lernpfad zwei Dokumente:

- **Heftaufschrieb** (`…-heftaufschrieb`, 1–2 Seiten): Lückentext des Heftaufschriebs aus „Festhalten“ mit leerem Karo-Feld und Schritt-für-Schritt-Anleitung für die eigene Zeichnung. Lösung ist der aufklappbare Heftaufschrieb im Lernpfad – beide müssen Wort für Wort zusammenpassen.
- **Übungsblatt** (`…-uebungsblatt`, 2–4 Seiten):  die Aufgabenstellungen der Übungen (gleiche Nummern wie im Lernpfad) mit Karo-Feldern
für den Rechenweg und Ergebnis-Zeilen. Kontrolliert wird online im Lernpfad („online geprüft“ abhaken). Richtwert 2–4 Seiten.
Konstruktionen mit Maßstab werden in echten Millimetern gezeichnet (SVG in mm) – Hinweis „in 100 % drucken“.

Vorhanden: Physik11/schiefe-ebene, Physik9/energie-einfuehrung, Physik9/lageenergie, Physik9/energieerhaltung, Physik9/wirkungsgrad.
Neue Vorlagen am besten von einer vorhandenen kopieren (Kopf, Schritt-Leiste, Abschnitte). Bausteine in `druck.css`:
Heftaufschrieb `body.heftseite`, `.heftblatt` > `.hs` (Abschnitt), Lücken `.l .s/.m/.g/.xg`, `.zeichnen` (Karo-Feld + Schrittliste),
`.kt` (Tabelle), `.box`, `.sf` (zwei Fälle nebeneinander), `.hmerke`, `.teil.gg` (Geg./Ges./Rechn./Antw.-Zeilen);
Übungsblatt `.aufg` (Kopf `.ah` mit Nummer, ★, AFB), `.teil`, `.karo`, `.zeilen`, `.erg` mit `.feld` und `.ok`, `.rf` (richtig/falsch), `.beg` (Begründe).
Seitenumbruch vor einer Aufgabe mit `class="aufg seite"`; Abschnitte und Aufgaben werden nicht zerteilt.
QR-Code: Platzhalter `<!--QR:https://physik.party/…-->` im Kopf, dann `python3 tools/druck/qr_einsetzen.py <datei>.html`.

PDF erzeugen (im Repo-Hauptordner):

```
python3 -m http.server 8123 &
node tools/druck/pdf.js schiefe-ebene-heftaufschrieb Physik11/schiefe-ebene-heftaufschrieb.pdf "Physik 11 · Schiefe Ebene · Heftaufschrieb"
node tools/druck/pdf.js schiefe-ebene-uebungsblatt Physik11/schiefe-ebene-uebungsblatt.pdf "Physik 11 · Schiefe Ebene · Übungsblatt"
```

Das Skript meldet ungesetzte Formeln und Konsolen-Fehler. Danach Seitenzahl und Bilder prüfen (z. B. `pdftoppm -png`).
QR-Code im Kopf: mit Python `segno` aus der Adresse https://physik.party/<Ordner>/<lernpfad> erzeugt (Fußzeile ebenfalls physik.party).

Kein Feld für Name/Klasse/Datum und kein Formel-Kasten auf den Blättern (Wunsch der Lehrkraft).

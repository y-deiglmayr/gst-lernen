# Druckversionen (Arbeitsblätter zu Lernpfaden)

Jede Druckvorlage ist eine HTML-Seite in diesem Ordner (A4, Schul-CI, Formeln wie in den Lernpfaden mit `<f-m>`).
Das fertige PDF liegt neben dem Lernpfad, z. B. `Physik11/schiefe-ebene-arbeitsblatt.pdf`, und wird in `index.html`
beim Lernpfad mit `druck:{datei:'…pdf',text:'Arbeitsblatt zum Drucken',info:'PDF · 3 Seiten'}` als Download in die Kachel gesetzt.

Idee: Das Blatt enthält vor allem die Aufgabenstellungen der Übungen (gleiche Nummern wie im Lernpfad) mit Karo-Feldern
für den Rechenweg und Ergebnis-Zeilen. Kontrolliert wird online im Lernpfad („online geprüft“ abhaken). Richtwert 2–4 Seiten.
Konstruktionen mit Maßstab werden in echten Millimetern gezeichnet (SVG in mm) – Hinweis „in 100 % drucken“.

PDF erzeugen (im Repo-Hauptordner):

```
python3 -m http.server 8123 &
node tools/druck/pdf.js schiefe-ebene-arbeitsblatt Physik11/schiefe-ebene-arbeitsblatt.pdf "Physik 11 · Schiefe Ebene · Arbeitsblatt"
```

Das Skript meldet ungesetzte Formeln und Konsolen-Fehler. Danach Seitenzahl und Bilder prüfen (z. B. `pdftoppm -png`).
QR-Code im Kopf: mit Python `segno` aus der Live-Adresse des Lernpfads erzeugt.

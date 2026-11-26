# Feedback auswerten

Schüler schicken Rückmeldungen über den Knopf „Feedback“ (Navigation und Fuß jedes Lernpfads).
Sie landen anonym in der Cloudflare-D1-Datenbank **gst-feedback**
(ID `17e96367-7f67-4c99-b1f8-ff75f1f89423`, Tabelle `feedback`, Aufbau in `schema.sql`).

## So läuft es technisch

- `brand/feedback.js` baut Knopf und Formular, `feedback/worker.js` nimmt unter `POST /api/feedback` an.
- **Harte Filter (wird gar nicht gespeichert):** unter 40 Zeichen oder unter 7 Wörtern, Zeichenketten wie „aaaaaa“,
  Links, E-Mail-Adressen, Telefonnummern, Schimpfwörter, fast nur Sonderzeichen, Bots (verstecktes Feld,
  Formular kürzer als 10 s offen), fremde Herkunft, mehr als 300 Einträge am Tag, doppelte Texte.
  Im Browser zusätzlich höchstens 5 Rückmeldungen pro Tag.
- **Vorbewertung `qualitaet` (0–100)** mit Begründung in `gruende`: Punkte für Länge, genannte Stelle, Vorschlag,
  Fachwörter/konkrete Bezüge, Zahlen, Begründung („weil“, „sollte“ …); Abzug für GROSSBUCHSTABEN, „!!!“,
  abwertend ohne Begründung („langweilig“, „doof“ …), viele Wiederholungen, kurzes Lob.
  Faustregel: ab 50 lohnt sich ein Blick, ab 70 meist konkret und brauchbar.
- `status`: `neu` → `uebernommen` (eingebaut) / `erledigt` (geprüft, keine Änderung nötig) / `verworfen`.
- Täglich um 3:17 Uhr (UTC) löscht der Worker Einträge älter als 12 Monate und verworfene älter als 30 Tage.

## Abrufen mit Claude

Einfach sagen: **„Werte das neue Feedback aus.“** Claude geht dann so vor:

1. Neue Einträge holen (Cloudflare-Werkzeug `d1_database_query`):
   ```sql
   SELECT id, erstellt, seite, stelle, art, text, vorschlag, qualitaet, gruende
   FROM feedback WHERE status = 'neu' AND qualitaet >= 50
   ORDER BY seite, qualitaet DESC;
   ```
   Überblick über alles: `SELECT seite, status, COUNT(*), AVG(qualitaet) FROM feedback GROUP BY seite, status;`
2. **Jeden Eintrag selbst prüfen** – die Zahl ist nur eine Vorsortierung. Ausgewertet wird nur, was
   - sich auf eine bestimmte Stelle bezieht und nachvollziehbar ist (Seite öffnen, Aufgabe nachrechnen, Simulation testen),
   - fachlich stimmt (ein gemeldeter „Fehler“ kann auch ein Denkfehler des Schülers sein – dann ist das ein Hinweis,
     dass Tipp oder Erklärung an der Stelle besser werden sollte, nicht dass die Lösung falsch ist),
   - zur Didaktik der Lernpfade passt (siehe CLAUDE.md) und nicht nur Geschmack ist („zu viel Text“ ohne Stelle).
   Mehrere ähnliche Rückmeldungen zur selben Stelle sind ein starkes Zeichen, auch wenn einzelne schwach formuliert sind.
3. Dem Lehrer eine kurze Liste vorlegen: übernehmen / Erklärung verbessern / verwerfen, je mit Grund.
   Erst nach seinem OK ändern, prüfen und veröffentlichen wie üblich.
4. Status setzen:
   ```sql
   UPDATE feedback SET status = 'uebernommen', notiz = 'Toleranz in 4a erhöht' WHERE id = 12;
   UPDATE feedback SET status = 'verworfen' WHERE status = 'neu' AND qualitaet < 30;
   ```

Schwache Einträge (`qualitaet < 50`) bei Bedarf trotzdem überfliegen:
`SELECT id, seite, stelle, art, text FROM feedback WHERE status = 'neu' AND qualitaet < 50;`

## Ohne Claude

Cloudflare-Dashboard → Storage & Databases → D1 → gst-feedback → Console, dort dieselben SQL-Befehle.

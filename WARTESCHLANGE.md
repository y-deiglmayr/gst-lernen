# Warteschlange Lernpfade und Druckversionen

Eine geplante Aufgabe arbeitet diese Liste ab: **pro Lauf genau eine Einheit**, immer die erste mit Status `offen`.
Regeln: `CLAUDE.md` (Vorrang) und Skill „gst-lernpfad“; Druckversionen nach CLAUDE.md „Druckversionen“ und `tools/druck/LIESMICH.md`.
Neues Material wird unten als neue Einheiten angehängt (Lernpfad, danach eigene Einheit „Druck“).
Status: `offen` → `fertig (Datum, Commit)`; bei Problemen `blockiert: Grund` und mit der nächsten Einheit weitermachen.
OneDrive-Sicherung: Spalte „Sicherung“ – `offen`, bis die Dateien in `D:\OneDrive\Unterricht WBS\Lernapps` liegen.

Quelle: Unterrichtsmaterial von Herrn Deiglmayr (OneNote-Export „3. Akustik“, „4. Mechanik“, TG8, Schuljahr 2025/26).
Das Material liegt nicht im Repo (öffentlich, Schülernamen), Inhalte unten sind die verbindliche Zusammenfassung.
In Lernpfaden **keine Schülernamen** aus dem Material verwenden; Beispielpersonen frei erfinden.
Überschneidung mit „Dynamik · Kräfte“ (Kräfte 1–4, schon online) vermeiden: Kräfte kommen in der Mechanik-Reihe nicht vor.
## Ablauf eines Laufs (verbindlich für die geplante Aufgabe)

**Sparregeln (Cache-Lesen gering halten):**
- Ein Lauf = eine Einheit, kurze frische Sitzung, keine Subagenten, nur ein Lauf gleichzeitig.
- Keine ganzen Dateien lesen: CLAUDE.md und diese Datei nur abschnittsweise (`grep -n`, `sed -n`); aus der Inhaltsliste nur den Abschnitt der eigenen Einheit.
- Vorlage kopieren statt lesen: neuen Lernpfad mit `cp` aus einem fertigen Physik8-Lernpfad anlegen und gezielt per Skript/`sed`/Edit umbauen; aus Mustern nur einzelne Stellen per `grep` ansehen, keine zweite oder dritte Musterdatei öffnen.
- Werkzeugausgaben klein halten: keine Datei-Dumps, Server/Playwright/PDF-Befehle leise (`>/dev/null`, `| tail -5`), Prüfskript gibt nur Fehler und Kennzahlen aus; höchstens 2–3 Screenshots ansehen.
- Nicht dieselbe Prüfung wiederholt laufen lassen, nur nach echten Änderungen.

**Schritte:**
1. `git fetch origin main`, auf origin/main. Erste Einheit mit `offen` nehmen (`in Arbeit` jünger als 3 h überspringen). Sofort `in Arbeit (Datum Uhrzeit)` setzen, committen, auf main pushen.
2. Lernpfad bzw. Druck nach CLAUDE.md bauen (Lernpfad ohne PDFs; Druck nach `tools/druck/LIESMICH.md`), Startseite/README ergänzen.
3. Prüfen nach CLAUDE.md „Prüfen“ (leise), Fehler beheben.
4. Status `fertig (Datum, Commit)`, `git fetch` + zusammenführen, auf main pushen.
5. Sicherung: `list_devices`; ist D:\OneDrive\Unterricht WBS\Lernapps erreichbar, Ordner mit `device_request_folder_access` anfordern (vorab freigegeben, keine Rückfrage), alle auf main seit dem Commit in `/mnt/project-files/sicherung/letzte-sicherung-commit.txt` geänderten Auslieferungsdateien (ohne tools/, feedback/) nach /mnt/project-files/sicherung/aktuell/ kopieren und mit `device_commit_files` schreiben; danach Commit-ID in die Datei schreiben und Sicherung-Spalte auf `ja (Datum)`. Sonst `offen` lassen.
6. Kurz melden (unter 60 Wörtern, Live-Link, Sicherung ja/nein), Thread erledigt.


## Reihenfolge

| Nr | Einheit | Datei | Status | Sicherung |
|----|---------|-------|--------|-----------|
| 1 | Lernpfad Akustik 1 · Wie entsteht Schall? | Physik8/schall-entstehung | fertig (26.11.2026, 31faa82) | ja (26.11.2026) |
| 2 | Druck Akustik 1 | Physik8/schall-entstehung-*.pdf | fertig (26.11.2026, 31a9c78) | ja (26.11.2026) |
| 3 | Druck Reflexion am ebenen Spiegel | Physik8/reflexion-spiegel-*.pdf | fertig (26.11.2026, 49a03b4) | ja (26.11.2026) |
| 4 | Lernpfad Akustik 2 · Schwingungen beschreiben | Physik8/schwingungen | fertig (27.11.2026, 6b26061) | offen |
| 5 | Druck Akustik 2 | Physik8/schwingungen-*.pdf | fertig (27.11.2026, fc5dcb3) | offen |
| 6 | Druck Kräfte 1 · Was ist eine Kraft? | Physik8/kraefte-wirkungen-*.pdf | fertig (27.11.2026, 4150084) | offen |
| 7 | Lernpfad Akustik 3 · Tonhöhe, Lautstärke, Schallarten | Physik8/schallarten | fertig (27.11.2026, 31e5db1) | offen |
| 8 | Druck Akustik 3 | Physik8/schallarten-*.pdf | fertig (28.11.2026, bb26e7d) | offen |
| 9 | Druck Kräfte 2 · Gewichtskraft und Masse | Physik8/gewichtskraft-masse-*.pdf | in Arbeit (28.11.2026 10:07) | offen |
| 10 | Lernpfad Akustik 4 · Schallausbreitung | Physik8/schallausbreitung | offen | offen |
| 11 | Druck Akustik 4 | Physik8/schallausbreitung-*.pdf | offen | offen |
| 12 | Druck Kräfte 3 · hookesches Gesetz | Physik8/hookesches-gesetz-*.pdf | offen | offen |
| 13 | Lernpfad Akustik 5 · Schallgeschwindigkeit | Physik8/schallgeschwindigkeit | offen | offen |
| 14 | Druck Akustik 5 | Physik8/schallgeschwindigkeit-*.pdf | offen | offen |
| 15 | Druck Kräfte 4 · Mehrere Kräfte und Newtons Gesetze | Physik8/kraefte-newton-*.pdf | offen | offen |
| 16 | Lernpfad Akustik 6 · Hören, Lärm und Lärmschutz | Physik8/hoeren-laerm | offen | offen |
| 17 | Druck Akustik 6 | Physik8/hoeren-laerm-*.pdf | offen | offen |
| 18 | Druck Spiegelbild konstruieren · Üben | Physik8/spiegelbild-uebungen-*.pdf | offen | offen |
| 19 | Lernpfad Bewegung 1 · Größen und Einheiten | Physik8/groessen-einheiten | offen | offen |
| 20 | Druck Bewegung 1 | Physik8/groessen-einheiten-*.pdf | offen | offen |
| 21 | Druck Lichtbrechung 1 · Schülerexperiment | Physik8/lichtbrechung-experiment-*.pdf | offen | offen |
| 22 | Lernpfad Bewegung 2 · Bewegungen beschreiben | Physik8/bewegungen-beschreiben | offen | offen |
| 23 | Druck Bewegung 2 | Physik8/bewegungen-beschreiben-*.pdf | offen | offen |
| 24 | Druck Lichtbrechung 2 · Theorie | Physik8/lichtbrechung-theorie-*.pdf | offen | offen |
| 25 | Lernpfad Bewegung 3 · Das s-t-Diagramm | Physik8/st-diagramm | offen | offen |
| 26 | Druck Bewegung 3 | Physik8/st-diagramm-*.pdf | offen | offen |
| 27 | Druck Lichtbrechung 3 · Üben | Physik8/lichtbrechung-uebungen-*.pdf | offen | offen |
| 28 | Lernpfad Bewegung 4 · Geschwindigkeit berechnen | Physik8/geschwindigkeit | offen | offen |
| 29 | Druck Bewegung 4 | Physik8/geschwindigkeit-*.pdf | offen | offen |
| 30 | Druck Physik11 · 1 Kraft – Grundlagen | Physik11/kraft-grundlagen-*.pdf | offen | offen |
| 31 | Lernpfad Bewegung 5 · v-t-Diagramm und zusammengesetzte Bewegungen | Physik8/vt-diagramm | offen | offen |
| 32 | Druck Bewegung 5 | Physik8/vt-diagramm-*.pdf | offen | offen |
| 33 | Druck Physik11 · 2 Kräfteaddition | Physik11/kraefteaddition-*.pdf | offen | offen |
| 34 | Druck Physik11 · 3 Kräftezerlegung | Physik11/kraeftezerlegung-*.pdf | offen | offen |
| 35 | Druck Physik11 · 5 Newtonsche Gesetze und Reibung | Physik11/newton-reibung-*.pdf | offen | offen |
| 36 | Druck Physik11 · Impuls 1 | Physik11/impuls-grundlagen-*.pdf | fertig (27.11.2026, Thread „Druckversionen Impuls“) | offen |
| 37 | Druck Physik11 · Impuls 2 (mit Versuchsprotokoll, Lernpfad mit Stoßexperiment) | Physik11/stoesse-impulserhaltung.html + -*.pdf, index.html | fertig (26.11.2026, Thread „Stoßversuch“) | ja (26.11.2026) |
| 38 | Druck Physik11 · Impuls 3 Rückstoß | Physik11/rueckstoss-*.pdf | fertig (27.11.2026, Thread „Druckversionen Impuls“) | offen |
| 39 | Druck Physik11 · Impuls 4 Kraftstoß | Physik11/kraftstoss-*.pdf | fertig (27.11.2026, Thread „Druckversionen Impuls“) | offen |
| 40 | Druck Physik11 · Impuls 5 Stöße quantitativ | Physik11/elastischer-stoss-*.pdf | fertig (27.11.2026, Thread „Druckversionen Impuls“) | offen |

Schon fertig (Druck): schiefe-ebene (Physik11), energie-einfuehrung, lageenergie, energieerhaltung (Physik9).
Startseite: neues Thema „Akustik“ und „Mechanik · Bewegungen“ in Klasse 8 (`KURSE`), jeweils mit Vorschaubild in `BILDER`.

---

## Inhalte Akustik (Klasse 8)

### Akustik 1 · Wie entsteht Schall? (`schall-entstehung`)
- Einstieg: Geräusche-Rätsel (verschiedene Schallquellen: reiner Ton, Klang, Knall, Rascheln); Frage: Was braucht man, um etwas zu hören? Ist Luft nötig?
- Akustik = Lehre vom Schall. Zum Hören braucht man **Schallquelle** (z. B. Stimmgabel) → **Schallleiter/Schallmedium** (z. B. Luft) → **Schallempfänger** (Ohr).
- Versuch Klingel/Wecker unter evakuierter Glasglocke: Ton wird leiser bis unhörbar → im Vakuum kein Schall (Weltraumschlachten im Film sind physikalisch falsch). Hinweis: Glocke muss frei aufgehängt sein, sonst leiten Kabel/Unterlage.
- Andere Schallleiter: Wasser (Tauchen, Walgesang), feste Stoffe (Ohr am Boden, Stimmgabel an Stativstange, Schnurtelefon).
- Schallquellen untersuchen: Kehlkopf anfassen, Stimmgabel ins Wasser, Kügelchen auf Lautsprecher, Lautsprecher „atmen“ lassen, Federstahl/Lineal an der Tischkante.
- Beobachtungen (Heft): Schallquellen vibrieren, d. h. sie führen rasche Hin- und Herbewegungen aus = **Schwingungen**. Nur Schwingungen, die so schnell sind, dass das Auge nicht folgen kann, erzeugen einen hörbaren Ton. Je größer die **Amplitude** (Weite des Ausschlags), desto **lauter** der Ton.
- Aufgaben: Was schwingt bei Instrumenten (Gitarre: Saite, Trommel: Fell, Flöte: Luftsäule, Stimme: Stimmbänder)? Welche Insekten hört man (Mücke/Biene ja, Schmetterling nein → Flügelschläge zu langsam)? Trommel groß/klein vergleichen.
- Simulation: Lineal an Tischkante (Länge, Ausschlag) – qualitativ: kürzer → schneller → höher; weiter ausgelenkt → lauter. Glasglocke mit Pumpe (Luftmenge ↓ → leiser).
- Begründe: Warum hört man im Weltall keine Explosion? Warum summt eine Mücke, ein Schmetterling nicht?

### Akustik 2 · Schwingungen beschreiben (`schwingungen`)
- Definition Schwingung: Bewegung, deren Richtung sich immer wieder umkehrt und die sich mit der Zeit wiederholt (Hin-und-her-Bewegung). Vibriert etwas, schwingt es sehr schnell. Beispiele: Fadenpendel, Federpendel, Schaukel, Stimmgabel.
- Schwingungen aufzeichnen: Stift an Stimmgabel / Kreide an der Tafel entlanglaufen → **Schwingungsdiagramm**: zeitlich nacheinander kommende Positionen werden räumlich nebeneinander dargestellt (x-Achse Zeit t, y-Achse Auslenkung s → t-s-Diagramm). Ruhende Stimmgabel → gerade Linie.
- Begriffe: **Ruhelage**, **Umkehrpunkt**, **Amplitude** (maximale Auslenkung von der Ruhelage zum Umkehrpunkt), **Periode** (eine vollständige Hin- und Herbewegung), **Periodendauer T** (Zeit für eine Periode).
- **Frequenz f** = Anzahl der Schwingungen (Perioden) pro Sekunde; Einheit Hertz: 1 Hz = 1 : s. f = 1 : T bzw. T = 1 : f. Messen: Perioden in z. B. 10 s zählen (Federpendel/Fadenpendel).
- Stroboskop: stehendes Bild, wenn Blitzfrequenz = Schwingfrequenz (Blitze pro Sekunde); drehendes Rad scheint rückwärts zu laufen.
- Je größer f, desto höher der Ton. Amplitude (Lautstärke) und Frequenz (Tonhöhe) sind unabhängig voneinander.
- Exkurs physikalische Größen: Größe = Zahlenwert · Einheit, Formelzeichen (s, t, m, f) – kurz, wird in Bewegung 1 vertieft.
- Übungen (aus ÜB 2.1 / 2.1.1): Aus Diagrammen A, T, f und Anzahl Perioden ablesen; Diagramm zeichnen (A = 3 cm, T = 0,5 s, zwei Perioden); f = 4 Hz → T = 0,25 s, Diagramm für 1 s; Ton A (2 cm, 2 Hz) vs. Ton B (4 cm, 2 Hz) vergleichen (gleich hoch, B lauter).
- Simulation: Federpendel mit Ablesen von T und A am Diagramm (mit Hinweis: ohne Reibung / gedämpft optional).

### Akustik 3 · Tonhöhe, Lautstärke und Schallarten (`schallarten`)
- Oszilloskop: Mikrofon wandelt Luftdruckschwankungen (vom schwingenden Lautsprecher) in elektrische Signale; Oszilloskop zeichnet Schwingungsbild viel schneller, als wir zeichnen können.
- Beobachtungen: je größer Amplitude → lauter; je größer Frequenz (enger Verlauf) → höher. Unabhängig voneinander.
- Schallarten mit Schallbildern: **Ton** (gleichbleibende Frequenz, sinusförmig, z. B. Stimmgabel), **Klang** (regelmäßig wiederkehrendes Muster, aus mehreren Tönen, z. B. Blockflöte, Stimme), **Geräusch** (unregelmäßig, ohne Struktur, z. B. zerknülltes Papier, Rassel), **Knall** (kurz, anfangs sehr große Amplitude, schnell abnehmend, z. B. Klatschen).
- Hörbereich des Menschen: ca. 20 Hz bis 20 000 Hz; darunter **Infraschall** (Elefanten, Erdbeben), darüber **Ultraschall** (Fledermaus, Hund hört höher). Mit dem Alter sinkt die obere Grenze (Hörtest mit Tongenerator: z. B. 75 Hz bis 16 000 Hz).
- Übung „Oszi-Schwingungen“: Bilder zuordnen: große Frequenz + kleine Amplitude; gleiche Tonhöhe; tief und leise; hoch und laut (mit Begründung).
- Labor: Tongenerator-ähnlicher Regler f/A mit gezeichnetem Schwingungsbild (Ton nur auf Knopfdruck, leise voreingestellt, Lautstärkewarnung) – kein Zwang zum Ton.
- Begründe: Warum klingen Flöte und Geige beim gleichen Ton verschieden? (Klang: gleiche Grundfrequenz, unterschiedliches Muster).

### Akustik 4 · Schallausbreitung (`schallausbreitung`)
- Versuch: 50 ml Wasser + 50 ml Spiritus ergeben nur ca. 97 ml → Stoffe bestehen aus kleinen Teilchen mit Zwischenräumen (Teilchenmodell).
- Teilchenmodell Schall: Schallquelle stößt durch ihre Schwingung die benachbarten Teilchen an, diese stoßen die nächsten an usw.; die Teilchen bleiben (im Mittel) an ihrem Platz. **Schall** = sich ausbreitende **Verdichtung und Verdünnung** der Teilchen (Längswelle).
- Schraubenfedermodell: Feder in Längsrichtung anstoßen → Verdichtung läuft entlang der Feder; Feder = Luft.
- Stimmgabel in Längsrichtung der Zinken lauter (Hand-Experiment).
- Schallleiter: feste Stoffe, Flüssigkeiten, Gase; Vakuum leitet nicht (keine Teilchen). Stethoskop erklären (Schlauch leitet Verdichtungen gebündelt zum Ohr).
- 3.2.1 Eigenschaften: **Reflexion** an festen Wänden (Echo in den Bergen); Teilchenmodell: Verdichtung prallt an dichter Oberfläche ab und kehrt um. Anwendungen: Echolot, Sonar, Echoortung (Fledermäuse, Delfine, Blinde).
  **Absorption**: poröse Stoffe „schlucken“ Schall; Verdichtungen geraten in Hohlräume, werden dort hin- und herreflektiert, bis sie abgeschwächt sind. Anwendungen: Schaumstoff, Dämmmatten, Ohrstöpsel, Lärmschutzwände, Vorhänge.
- Simulation: Teilchenkette/Schraubenfeder mit Verdichtung, Wand reflektierend vs. porös absorbierend (Modell, qualitativ).
- Begründe: Wie funktioniert ein Stethoskop? Warum hallt es in einer leeren Wohnung stärker als in einer eingerichteten?

### Akustik 5 · Schallgeschwindigkeit (`schallgeschwindigkeit`)
- Schall braucht Zeit (Beobachtung: Blitz vor Donner, Startschuss aus der Ferne). Geschwindigkeit messen: Strecke und dafür benötigte Zeit, v = Δs : Δt (Δ = Differenz).
- Messung mit zwei Smartphones (App phyphox, „Akustische Stoppuhr“): Abstand messen, an Handy 1 klatschen (Start), an Handy 2 klatschen (Stopp), Zeitdifferenz, 5 Messungen, Mittelwert.
- Schallgeschwindigkeit hängt vom Medium ab: Luft ca. 340 m/s (bei 20 °C ca. 343 m/s), Wasser ca. 1480 m/s, Stahl ca. 5000 m/s.
- Gewitterregel: Sekunden zwischen Blitz und Donner : 3 = Entfernung in km (Licht fast sofort da).
- Echo-Rechnung (Hin- und Rückweg: s = v · t : 2), Echolot.
- Richtungshören: Zeitunterschied zwischen linkem und rechtem Ohr; Versuch mit Klick-Geräusch, Wegunterschied Δs messen, Δt = Δs : 340 m/s (sehr kleine Zeiten, z. B. 0,03 m → ca. 0,0001 s). Unsere Ohren sind zeitlich sehr empfindlich.
- Überschall (Flugzeug schneller als 340 m/s ≈ 1224 km/h → Überschallknall) nur als Ausblick.
- Übungen ★–★★★: Gewitterentfernung, Echo am Berg, Echolot, Laufzeit in Stahlschiene vs. Luft, Messwerte auswerten.

### Akustik 6 · Hören, Lärm und Lärmschutz (`hoeren-laerm`)
- 3.3 Schallempfänger Ohr: Ohrmuschel → Gehörgang → **Trommelfell** schwingt → Mittelohr: **Hammer, Amboss, Steigbügel** → Innenohr: **Hörschnecke** mit Basilarmembran und ca. 16 000 Hörsinneszellen (Härchen) → Nervenimpulse → Gehirn. Hohe Töne am Anfang (Basis) der Schnecke, tiefe Töne an der Spitze.
  (Achtung Material: „tiefe Töne oben, hohe weiter unten“ – fachlich korrekt formulieren: hohe Töne nahe dem ovalen Fenster, tiefe an der Schneckenspitze.)
- Zwei Ohren → Richtungshören (Verweis Akustik 5).
- Lärm: Härchenzellen werden bei zu hoher Belastung geschädigt; Dauerlärm stört die Durchblutung, Zellen sterben ab – für immer. Lautstärke in Dezibel (dB) als Skala (Flüstern ca. 30 dB, Gespräch 60 dB, Straßenverkehr 80 dB, Disco 100 dB, Schmerzgrenze ca. 120–130 dB); ab ca. 85 dB über längere Zeit gehörschädigend.
- Lärmschutz: an der Quelle (leisere Motoren, Tempolimit), auf dem Weg (Lärmschutzwand, Dämmung, Absorption), am Empfänger (Gehörschutz, Ohrstöpsel, Kopfhörer leiser, Pausen).
- Begründe: Hörvorgang mit Fachbegriffen beschreiben; Warum ist Lärmschutz wichtig?
- Abschluss: kleine Wiederholung Akustik (Größen f, T, A mit Formelzeichen und Einheit).

## Inhalte Mechanik · Bewegungen (Klasse 8, Kinematik)
Mechanik = Kinematik (Beschreibung von Bewegungen) + Dynamik (Ursachen: Kräfte). Dynamik ist schon als „Kräfte 1–4“ online → hier nur Kinematik.

### Bewegung 1 · Größen und Einheiten (`groessen-einheiten`)
- Warum Einheiten? Früher Elle/Fuß je nach König verschieden → Probleme beim Handel. Meter: 1/10 000 000 der Strecke Pol–Äquator, Urmeter (bis 1960), heute: Strecke, die Licht im Vakuum in 1/299 792 458 s zurücklegt (Vorteil: Naturkonstante, überall gleich). Sekunde: Atomuhr.
- SI-Einheitensystem: weltweit gültig. Physikalische Größe = Größenname, Formelzeichen, Einheit; Größe = Zahlenwert · Einheit (z. B. s = 5 km).
- Basisgrößen: Länge s (m), Masse m (kg), Zeit t (s), Temperatur T (K), Stromstärke I (A), Lichtstärke (cd) (Stoffmenge nur erwähnen).
- Zuordnungsübung: „wie schwer“ → Masse, kg; „wie warm“ → Temperatur, K (°C); „wie viel Platz“ → Volumen, m³; „wie schnell“ → Geschwindigkeit, m/s; „wie lang“ → Länge, m; „wie lange“ → Zeit, s. Messgeräte: Waage, Stoppuhr, Radar, Thermometer, Maßband.
- Vorsätze: Kilo k = 1000, Milli m = 1/1000, Mikro µ = 1/1 000 000, Nano n = 1/1 000 000 000 (Tabelle, nicht auswendig); Umrechnen von Einheiten (Länge, Zeit: h/min/s, Masse).
- Geltende Ziffern (Ziffernregel): Jede Stelle eines korrekt angegebenen Messwertes ist eine geltende Ziffer; je mehr geltende Ziffern, desto genauer; Nachkommastellen und führende Nullen hängen nur von der Einheit ab; Ergebnis nicht genauer angeben als die Messwerte.
- Begründe: Warum ist die heutige Meter-Definition besser als der Urmeter?

### Bewegung 2 · Bewegungen beschreiben (`bewegungen-beschreiben`)
- Einstieg: Was bedeutet „schneller als“? Was ist Geschwindigkeit? Hohe Geschwindigkeiten (Schall 340 m/s, Licht 300 000 km/s …).
- Bewegungsarten: **gleichförmige Bewegung** (konstante Geschwindigkeit, keine Richtungsänderung, in gleichen Zeiten gleiche Strecken); **beschleunigte Bewegung** (schneller = positive Beschleunigung, langsamer = Verzögerung/negative Beschleunigung); Sonderfälle **Kreisbewegung** (Richtung ändert sich ständig) und **Schwingung** (Geschwindigkeit und Richtung ändern sich; Verweis Akustik).
- Formulierungshilfen (Beobachtung, Geschwindigkeit, Weg/Zeit, Richtung) zum Beschreiben in ganzen Sätzen.
- Bezugssystem: Bewegung hängt vom Beobachter ab (Athlet auf fahrendem Zug: für Person im Zug langsam, für Person neben Gleis schnell). Relative Geschwindigkeiten: gleiche Richtung addieren (100 km/h + 20 km/h = 120 km/h vom Bahnsteig), Gegenrichtung subtrahieren.
- Einstiegsaufgabe „geheimnisvoller Urlaub“: 9 h Flug, 800 km/h → 7200 km; Start/Landung beschleunigt, Reiseflug gleichförmig.
- Übungen: Bewegungen zuordnen (Fahrstuhl, Karussell, Pendel, ICE auf gerader Strecke, Bremsen vor Ampel), Bezugssystem-Aufgaben.
- Begründe: Ist ein Flug von Stuttgart nach New York eine gleichförmige Bewegung?

### Bewegung 3 · Das s-t-Diagramm (`st-diagramm`)
- s-t-Diagramm (Weg-Zeit-Diagramm): Zu welchem Zeitpunkt hat der Körper welchen Abstand vom Start; jeder Punkt = Wertepaar (t | s); Messwerte in Tabelle, x-Achse Zeit, y-Achse Weg.
- Versuch Läufer: Schüler mit Stoppuhren alle 2 m (bzw. 4 m), drei Läufer, gemeinsames Diagramm in drei Farben; Auswertung: Schnellster = steilste Linie; Steigung = Geschwindigkeit; Anfang beschleunigt, später gleichförmig.
- Formen: **Ursprungsgerade** = gleichförmig; steiler = schneller; **waagerecht** = Stillstand; **nach oben gekrümmt** = schneller werden; **flacher werdend** = langsamer werden; **fallende Gerade** = Bewegung zurück zum Start.
- Übungsblatt 4.2: Messreihen (Wegmarken gleich weit, Zeiten 1: 0,4/0,8/…/2,8 s; 2: 0,6/1/1,35/1,7/2,1/2,6/3,2 s; 3: 2/4/…/14 s; 4: 1,5/2,6/3,5/4,2/4,8/5,2/5,5 s) zeichnen, Bewegungsart bestimmen, Situationen zuordnen (gleichmäßig gehen = 3, Fahrrad gleichmäßig = 1, Fahrrad abbremsen = 2 (Zeitabstände pro Wegstück werden größer → langsamer), Fahrrad aus der Ruhe anfahren = 4 (Zeitabstände werden kleiner → schneller)).
  **Achtung**: Die Begründungssätze in der Musterlösung des Materials sind zwischen 2 und 4 vertauscht – fachlich korrekt: kleiner werdende Zeitabstände pro gleichem Wegstück = schneller werden.
- Motion-Mapper-Idee: eigene Simulation „Figur so bewegen, dass der Graph passt“ (Schieberegler/Ziehen, Graph live).
- Begründe: Woran erkennst du im s-t-Diagramm, wer schneller ist?

### Bewegung 4 · Geschwindigkeit berechnen (`geschwindigkeit`)
- Gleichförmig: in gleichen Zeiten gleiche Strecken, v konstant. Geschwindigkeit = Strecke pro Zeit: v = s : t (genauer v = Δs : Δt, Durchschnittsgeschwindigkeit). v von lat. velocitas, t von tempus. Einheit m/s; km/h : 3,6 = m/s, m/s · 3,6 = km/h (Herleitung 1 km/h = 1000 m : 3600 s).
- Umstellen: s = v · t, t = s : v. Vorgehen: Gegeben (Größe zuordnen) → Gesucht → Formel → umstellen → einsetzen mit Einheiten → Ergebnis mit Antwortsatz.
- Steigung im s-t-Diagramm = Geschwindigkeit (Steigungsdreieck mit Größen: Δs : Δt).
- Aufgaben aus dem Material: Radfahrer 20 m in 10 s → 2 m/s; 18 km/h → 5 m/s, in 5 s 25 m; Sprint 100 m: 12,5 s vs. 10 s – Vorsicht, wer jünger ist, läuft evtl. kürzere Strecke (z. B. 75 m) → erst v vergleichen; Schrecksekunde 30 km/h → 8,3 m, bei 50 km/h 13,9 m (5,6 m länger); 54 km/h = 15 m/s; 20 m/s = 72 km/h; 120 m/min = 2 m/s; RC-Auto 4 m/s: 15 s → 60 m, 100 m → 25 s; Schulweg 3 km mit 18 km/h → 600 s = 10 min; Begegnung 1,5 m/s und 1 m/s, 150 m → 60 s; Lokführer/Rennrad/Wanderer Tabellen (20 m/s, 15 m/s, 2 m/s) mit s-t-Diagramm.
- Gewitter-Faustregel (Verweis Akustik 5) als ★★★.
- Begründe: Warum ist in der Tempo-30-Zone der Weg in der Schrecksekunde wichtig?

### Bewegung 5 · v-t-Diagramm und zusammengesetzte Bewegungen (`vt-diagramm`)
- v-t-Diagramm: gleichförmige Bewegung = waagerechte Linie; Stillstand = Linie auf v = 0; Rückwärts = negative v.
- Zurückgelegter Weg = Fläche zwischen Graph und t-Achse (Rechteck v · t). Beispiel Auto 30 m/s (108 km/h) für 10 s → 300 m.
- Zusammengesetzte Bewegungen (abschnittsweise gleichförmig): Fahrt zum Autorennen in drei Abschnitten (Landstraße, Baustelle, Stadt; je fehlende Größe berechnen, Gesamtzeit, Gesamtstrecke, s-t-Diagramm).
- Durchschnittsgeschwindigkeit = Gesamtstrecke : Gesamtzeit (nicht Mittelwert der Geschwindigkeiten!): Fahrrad 12 km mit 20 km/h + 4 km mit 10 km/h → 16 km in 1 h = 16 km/h.
- Geschichte zum s-t-Diagramm: Lehrer geht zur Haltestelle, wartet, eilt nach Hause (Monatskarte), sofort zurück, Bus fährt los → s-t- und v-t-Skizze mit gleicher Zeitachse.
- Zwei Autos A/B im s-t-Diagramm: gleiche Geschwindigkeit = parallele Abschnitte, Treffen = Schnittpunkt.
- 800-m-Lauf mit zwei Läufern (idealisierte Diagramme): richtig/falsch-Aussagen.
- Begründe: Warum ist die Durchschnittsgeschwindigkeit der Radtour nicht 15 km/h?

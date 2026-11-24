# GST Lernpfade

Interaktive HTML-Lerninhalte für den Unterricht, veröffentlicht über Cloudflare Pages.

## Struktur

```
index.html                  Startseite mit allen Lernpfaden
fonts/                      Schriften lokal (Lexend, Atkinson Hyperlegible, SIL OFL) – keine Google-Server
Physik8/
  reflexion-spiegel.html    Reflexion am ebenen Spiegel
```

Jede Klasse bzw. jedes Fach bekommt einen eigenen Ordner. Die Adresse einer Seite ist der Pfad ohne `.html`,
z. B. `/Physik8/reflexion-spiegel`. Groß- und Kleinschreibung der Ordner gehört zur Adresse.

## Neuen Lernpfad hinzufügen

1. HTML-Datei in den passenden Ordner legen (Ordner bei Bedarf neu anlegen).
2. In `index.html` in der Liste `KURSE` einen Eintrag ergänzen.
3. Committen und pushen – Cloudflare veröffentlicht automatisch.

## Cloudflare-Pages-Einstellungen

- Framework preset: None
- Build command: (leer)
- Build output directory: `/`

## Schriften

Neue Seiten binden die Schriften mit `<link rel="stylesheet" href="/fonts/fonts.css">` ein – nicht über Google Fonts.

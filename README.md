# Mediathek-Extractor – Downloads

Suche und Download aus den Mediatheken der öffentlich-rechtlichen Sender (ARD, ZDF, ARTE, 3sat …)
für macOS, Windows und Linux.

**Installer:** unter [Releases](../../releases/latest).

| System | Datei |
|---|---|
| Mac (Apple Silicon und Intel) | `Mediathek-Extractor-…-macOS.dmg` |
| Windows (übliche PCs) | `Mediathek-Extractor-…-Windows-Installer.exe` |
| Windows auf ARM (z. B. Surface Pro X, Windows in UTM/Parallels auf dem Mac) | `Mediathek-Extractor-…-Windows-ARM-Installer.exe` |
| Linux (alle Distributionen) | `Mediathek-Extractor-…-Linux.AppImage` |
| Linux Debian/Ubuntu | `…-Linux-Debian-Ubuntu.deb` |
| Windows ohne Installation (z. B. USB-Stick) | `…-Windows-portabel.zip` bzw. `…-Windows-ARM-portabel.zip` |

**Mac mit Homebrew** – installiert yt-dlp und ffmpeg gleich mit:

```bash
brew tap 7hdmm9pp2w-code/tap
brew trust 7hdmm9pp2w-code/tap
brew install --cask mediathek-extractor
```

„Source code (zip / tar.gz)“ fügt GitHub automatisch zu jedem Release hinzu – es enthält nur
diese Anleitung, nicht die App.

## Was die App kann

- **Mediatheken durchsuchen** (ARD, ZDF, ARTE, 3sat, Dritte …) – mit Senderauswahl und Filter „nur ab 60 Min.“
- **Kostenlose Filme finden** über kinogrid.com, mit „verfügbar bis“
- **Videos aus Seiten auslesen:** einfach die URL einer Video- oder Übersichtsseite einfügen
- **Herunterladen** mit Warteschlange, **Anhalten und Fortsetzen**, automatischem Fortsetzen nach Verbindungsabbrüchen, MP3/M4A und Untertiteln (SRT)
- **Deutsch + Original in einer Datei:** zwei Tonspuren statt zwei Filme
- **Serien:** nach Staffeln sortiert, „Staffel laden“, „✓ geladen“
- **Vorschau** direkt in der App
- **Automatische Updates** – Fehlerbehebungen kommen still im Hintergrund
- **Merkliste:** Filme mit Ablauf-Erinnerung, Serien mit neuen Folgen, **gemerkte Suchen** mit neuen Treffern
- **Bewertungen** (TMDB), **Film des Tages**, „⏳ läuft bald ab“
- **Empfehlungen** von filmdienst.de
- **Einfach- und Profi-Modus** (Profi mit Protokoll aller Aktionen)
- **Mehrfachauswahl und Sortieren** der Trefferliste
- **Beschreibung nachladen** vom Sender oder aus der Wikipedia
- **Windows portabel** ohne Installation
- **Einrichtung beim ersten Start**, „Später starten“ (z. B. nachts), Größe und Speicherplatz vorab
- **Untertitel als Spur** statt eingebrannt – bei ARTE auch in der Originalsprache
- **Filminfos** (Jahr, Genre, Regie, Besetzung – über TMDB für fast jeden Film) mit Filtern, **Suche nach Regie und Darstellern**, **Dateinamen nach Wunsch** (z. B. „Jahr – Titel“)
- **Bedienung mit der Tastatur** (⌘/Strg+F, Pfeiltasten, Kontextmenü per Taste) und für VoiceOver/Sprachausgabe
- **Teilen** – auch mehrere Filme auf einmal – über das System (Mac, Windows), als Text oder per E-Mail – geteilte Links öffnen den Film direkt in der App; **App weiterempfehlen**

## Erster Start

Die Installer sind nicht signiert:

- **macOS:** App in „Programme“ ziehen und einmal öffnen – macOS meldet „nicht geöffnet“ → **Fertig**. Dann **Systemeinstellungen → Datenschutz & Sicherheit**, ganz unten bei „Mediathek-Extractor wurde blockiert“ auf **Dennoch öffnen** klicken und mit Passwort bzw. Touch ID bestätigen. Nur einmal nötig; Updates kommen danach automatisch.
  Alternativ im Terminal: `xattr -dr com.apple.quarantine /Applications/Mediathek-Extractor.app`
- **Windows:** „Der Computer wurde durch Windows geschützt“ → „Weitere Informationen“ → „Trotzdem ausführen“.

## Versionen

Neue Funktionen kommen etwa alle zwei Monate, Fehlerbehebungen bei Bedarf – die spielt die App
von selbst ein. Hier die letzten drei Versionen; ältere stehen bei den [Releases](../../releases).

### 1.5.0

- **Downloads anhalten und fortsetzen:** „⏸ Anhalten“ an jedem Download und „Alle anhalten“ über der Warteschlange. „▶ Fortsetzen“ lädt an der erreichten Stelle weiter – auch bei Streams und nach einem Neustart der App.
- **Genaue Suche:** Begriffe in Anführungszeichen finden nur das ganze Wort – „"Eis"“ findet das Eis, aber nicht mehr „Reise“, „Kreis“ oder „Preis“.
- **Mehr Originalfassungen bei der ARD:** Manche Originalversionen führt nur die ARD-Mediathek selbst (z. B. „Amerikanische Fiktion“). Die App findet sie jetzt auch – mit „+ OV“ und Deutsch + Original.
- **Mehrere Filme teilen:** in der Merkliste Häkchen setzen, in anderen Listen mit ⌘/Strg-Klick auswählen, in der Warteschlange über „Teilen…“ – eine Nachricht mit allen Filmtipps und Links.
- **Updates nebenbei:** Die App sieht auch während des Betriebs nach neuen Versionen und lädt sie im Hintergrund. Fehlerbehebungen kommen ohne Hinweisleiste beim nächsten Start.
- **Tastatur:** ⌘/Strg+F springt ins Suchfeld, Menütaste oder Umschalt+F10 öffnen das Kontextmenü, Enter lädt herunter, Esc schließt Dialoge, ein Rahmen zeigt den Fokus. Für VoiceOver und die Windows-Sprachausgabe beschriftet.
- **Homebrew:** auf dem Mac jetzt auch per `brew install --cask` (siehe oben).

Linux bleibt vorerst auf 1.2.2 – die Linux-Fassung folgt Anfang November.

### 1.4.0

- **🔔 Suche merken (Suchabo):** Neben „Alle“ lässt sich eine Suche merken, z. B. „Regie: …“ oder ein Stichwort. Neue Treffer erscheinen in der Merkliste mit „✓ Gesehen“ und „⬇ Neue laden“, auf Wunsch lädt die App sie automatisch. Dazu gibt es eine Mitteilung.
- **★ Bewertung:** Filme zeigen ihre Bewertung von TMDB in der Liste und in der Detailansicht. Neue Sortierung „Bewertung (TMDB)“ und Knopf „★ ab 7“ in der Genre-Leiste.
- **🎬 Film des Tages:** Auf der Startseite steht jeden Tag ein gut bewerteter Spielfilm aus den Mediatheken. Mit ✕ verschwindet er bis morgen.
- **⏳ Läuft bald ab:** Filme, die in wenigen Tagen aus der Mediathek verschwinden, zeigen „noch 2 Tage“. Neue Sortierung „läuft bald ab“.
- **Filmplakate:** in der Detailansicht und als „Film-poster.jpg“ neben dem Film, wenn „.nfo-Datei“ eingeschaltet ist (für Kodi, Jellyfin, Plex).
- **Nur Ton als M4A:** Im Profi-Modus lässt sich wählen, ob „Nur Ton“ als MP3 oder M4A gespeichert wird.
- **Zahl am Dock-Symbol:** Der Mac zeigt am App-Symbol, wie viele Downloads gerade laufen.
- **Behoben:** Die Personensuche fand bei häufigen Filmtiteln (z. B. „Undine“) nicht alle Filme. ARTE-Filme, die es nur mit eingebrannten Untertiteln gibt, waren versteckt.

Beim ersten Start holt die App die Filminfos einmal neu (wegen Bewertung und Plakat). Die Filminfos erscheinen deshalb anfangs etwas langsamer.

Linux bleibt vorerst auf 1.2.2 – die Linux-Fassung folgt Anfang November.

### 1.3.0

- **Kein doppeltes Laden aus Versehen:** Steht ein Film schon in der Warteschlange oder wurde er schon geladen, fragt die App nach. Bei mehreren Filmen auf einmal lassen sich die schon vorhandenen überspringen. Nach dem Klick zeigt der Knopf kurz „✓ In der Warteschlange“.
- **Warteschlange bleibt nach dem Neustart:** Die letzten 50 Downloads (fertig, fehlgeschlagen, abgebrochen) erscheinen wieder. Was beim Beenden noch lief, steht als „Unterbrochen“ da und startet mit „Wiederholen“ neu.
- **Nicht mehr verfügbare Filme:** Hat der Sender ein Video entfernt (depubliziert), sagt das die Detailansicht schon vorher, und der Download-Knopf ist gesperrt. Scheitert ein Download daran, steht dort „Nicht mehr verfügbar“ statt eines Fehlercodes.
- **Kein Hängenbleiben:** Bleiben Daten aus, versucht die App es erneut (direkte Dateien, fortgesetzt an der erreichten Stelle). Streams über yt-dlp brechen nach 5 Minuten ohne Daten mit einer klaren Meldung ab.
- **yt-dlp:** Die App-eigene Kopie aktualisiert sich jetzt täglich. Ist ein selbst installiertes yt-dlp (Homebrew, winget …) veraltet, weist die App darauf hin und zeigt den passenden Befehl zum Aktualisieren. Der Fortschritt kommt in einem eigenen, festen Format von yt-dlp und hängt nicht mehr an dessen Textausgabe; er zeigt jetzt auch die Größe wie bei direkten Downloads.
- **🎲 Überrasch mich:** Der Würfel neben der Sortierung springt zu einem zufälligen Video der Liste.
- **Statistik:** Das Über-Fenster zählt die geladenen Filme und Folgen, ihre Laufzeit, die Größe und das Lieblingsgenre. Zum Angeben lässt sich das teilen. Bei runden Zahlen gibt es in der Fertig-Mitteilung einen kleinen Jubel.
- **Teilen mit Genre-Emoji:** Geteilte Filmtipps beginnen mit 📺 und einem Emoji zum Genre, z. B. 📺🤠 für einen Western oder 📺🔪 für einen Krimi.
- Beim Suchen ein Spruch aus der Fernsehwelt, und nachts ein Gruß zum Sendeschluss.
- Im Über-Fenster versteckt sich ein Easter Egg. 🤫

## Danksagung und verwendete Projekte

Der Mediathek-Extractor ist eine Oberfläche, die auf hervorragender freier Software und offenen Daten aufbaut:

- **[yt-dlp](https://github.com/yt-dlp/yt-dlp)** – lädt Streams, Video-Seiten und MP3. Ohne yt-dlp ginge vieles nicht. Die App liefert yt-dlp nicht mit, sondern nutzt eine vorhandene Installation oder lädt auf Wunsch die offizielle Version.
- **[FFmpeg](https://ffmpeg.org)** – fügt Bild und Tonspuren zusammen, wandelt in MP3 um. Ebenfalls nicht mitgeliefert; unter Windows auf Wunsch aus den [yt-dlp-FFmpeg-Builds](https://github.com/yt-dlp/FFmpeg-Builds).
- **[MediathekViewWeb](https://mediathekviewweb.de)** und das Projekt **[MediathekView](https://mediathekview.de)** – die Datenbasis der Mediathek-Suche. Wer die App nützlich findet, kann MediathekView [unterstützen](https://mediathekview.de/spenden/).
- **[kinogrid.com](https://kinogrid.com)** – Verzeichnis kostenloser Filme.
- **[TMDB](https://www.themoviedb.org)** – Filminfos (Jahr, Genre, Regie, Besetzung) und Personensuche. *This product uses the TMDB API but is not endorsed or certified by TMDB.*
- **[Wikidata](https://www.wikidata.org)** (CC0) und **[Wikipedia](https://de.wikipedia.org)** (CC BY-SA) – Filminfos, wo TMDB nichts kennt, und Beschreibungen, wenn der Sender keine liefert.
- **[Tauri](https://tauri.app)** (MIT/Apache-2.0), **[hls.js](https://github.com/video-dev/hls.js)** (Apache-2.0) und **[Noto Emoji](https://github.com/googlefonts/noto-emoji)** (Apache-2.0, App-Icon).

Alle genannten Projekte sind unabhängig und nicht für diese App verantwortlich.

## Hinweise

- Bitte nur für Inhalte nutzen, die du privat speichern darfst. Kopiergeschützte Inhalte lädt die App nicht.

Dieses Repository enthält nur die Installer; der Quellcode ist nicht öffentlich.

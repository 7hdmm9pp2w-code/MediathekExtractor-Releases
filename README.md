# Mediathek-Extractor – Downloads

Suche und Download aus den Mediatheken der öffentlich-rechtlichen Sender (ARD, ZDF, ARTE, 3sat …)
für macOS, Windows und Linux.

**Entdecken. Laden. Teilen.**

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

## Worauf wir stolz sind

1. **Deutsch und Original in einer Datei.** Die App findet zum Film die Originalfassung – auch die, die nur die ARD-Mediathek selbst führt – und packt beide Tonspuren samt Untertiteln in eine einzige MP4.
2. **Die Merkliste nimmt auf.** Filme, Serien und ganze Suchen („Regie: Wim Wenders“, oder ein Film, der noch nirgends läuft) verfolgen: Taucht etwas auf, meldet sich die App und lädt es auf Wunsch von selbst. „⏳ noch 2 Tage“ zeigt, was bald verschwindet.
3. **Ein Filmkatalog statt nackter Titel.** Bewertung (TMDB), Jahr, Genre, Regie, Besetzung und Plakat; filtern nach „★ ab 7“, Genre oder Jahrzehnt; alle Filme einer Schauspielerin in den Mediatheken; jeden Tag ein Film des Tages.
4. **Downloads, die einfach funktionieren.** Eine Suche über alle öffentlich-rechtlichen Sender; Anhalten und Fortsetzen auch nach einem Neustart; „Staffel laden“; „Später starten“ für die Nacht. yt-dlp, FFmpeg und die App selbst halten sich von allein aktuell.
5. **Fertig für Plex, Jellyfin und Kodi.** Dateinamen nach eigener Vorlage mit Jahr und Staffel/Folge, dazu .nfo-Datei und Plakat – der Film landet gleich richtig einsortiert in der Mediathek zu Hause.
6. **Bonus: Filmtipps teilen.** Einen oder mehrere Filme als Nachricht, per E-Mail oder über das System teilen – der Link öffnet den Film beim Empfänger direkt in der App.

## Was die App sonst noch kann

- **Gezielt suchen:** Senderauswahl, „nur ab 60 Min.“, die besten Treffer zuerst, Begriffe in Anführungszeichen als ganzes Wort
- **(Auch mehrere) Videos aus Seiten auslesen:** einfach die URL einer Video- oder Übersichtsseite einfügen
- **Kostenlose Filme finden** über kinogrid.com, mit „verfügbar bis“, und **Empfehlungen** von filmdienst.de
- **Vorschau** direkt in der App
- **Untertitel als Spur** statt eingebrannt – bei ARTE auch in der Originalsprache; auf Wunsch als SRT-Datei
- **Nur Ton** als MP3 oder M4A
- **Robuste Downloads:** automatisches Fortsetzen nach Verbindungsabbrüchen, Größe und freier Speicherplatz vorab, „✓ geladen“ an allem, was schon da ist
- **Einfach- und Profi-Modus** (Profi mit Protokoll aller Aktionen)
- **Mehrfachauswahl und Sortieren** der Trefferliste
- **Beschreibung nachladen** vom Sender oder aus der Wikipedia
- **Bedienung mit der Tastatur** (⌘/Strg+F, Pfeiltasten, Kontextmenü per Taste) und für VoiceOver/Sprachausgabe
- **Einrichtung beim ersten Start** – yt-dlp lädt die App auf Wunsch selbst (unter Windows auch FFmpeg), auf dem Mac zeigt sie den passenden Homebrew-Befehl
- **Windows portabel** ohne Installation, z. B. vom USB-Stick
- **App weiterempfehlen** aus dem Über-Fenster

## Erster Start

Die Installer sind nicht signiert:

- **macOS:** App in „Programme“ ziehen und einmal öffnen – macOS meldet „nicht geöffnet“ → **Fertig**. Dann **Systemeinstellungen → Datenschutz & Sicherheit**, ganz unten bei „Mediathek-Extractor wurde blockiert“ auf **Dennoch öffnen** klicken und mit Passwort bzw. Touch ID bestätigen. Nur einmal nötig; Updates kommen danach automatisch.
  Alternativ im Terminal: `xattr -dr com.apple.quarantine /Applications/Mediathek-Extractor.app`
- **Windows:** „Der Computer wurde durch Windows geschützt“ → „Weitere Informationen“ → „Trotzdem ausführen“.

## Versionen

Neue Funktionen kommen etwa alle zwei Monate, Fehlerbehebungen bei Bedarf – die spielt die App
von selbst ein. Hier die letzten drei Versionen; ältere stehen bei den [Releases](../../releases).

### 1.5.2

- **Filminfos schneller und nach und nach:** Bewertung, Jahr und Genre erscheinen zuerst für die Filme, die gerade zu sehen sind, und dann laufend für den Rest – statt alle auf einmal nach bis zu einer Minute.
- **Suche ohne Hänger:** Große Suchen laden ihre Seiten gleichzeitig; antwortet eine Seite nicht, fragt die App nach 12 Sekunden noch einmal. Originalfassungen aus der ARD-Mediathek kommen im Hintergrund dazu.
- **„🔔 Benachrichtigen, wenn es kommt“:** Findet die Suche nichts, lässt sie sich gleich merken. Taucht der Film später auf, meldet sich die App.
- **Zur Bewertung durchklicken:** In der Detailansicht führt „bei TMDB“ zur Filmseite.
- **Update bereit:** Liegt eine neue Version bereit, zeigt die App das jetzt auch bei Fehlerbehebungen – mit „Jetzt neu starten“.

### 1.5.1

- **Bessere Treffer-Reihenfolge:** Oben steht, was am besten passt – Titel genau wie gesucht vor Treffern im Thema oder als Wortteil, Spielfilme vor Clips, Hauptfassungen vor Audiodeskription. Beispiel „transit“: Der Kinofilm steht jetzt auf Platz 1 statt auf Platz 39.
- **Ladebalken für Filminfos:** „Filminfos 37 / 120“ beim Nachschlagen von Bewertungen, Jahr und Genre; im Profi-Modus mit Quelle und Restzeit.
- **Nach dem Teilen** endet die Auswahl, kurz erscheint „✓ 3 Filmtipps kopiert“.
- **Download-Verlauf:** Die App merkt sich fertige Downloads ausführlicher – als Grundlage für spätere Empfehlungen. Nur auf deinem Rechner (siehe [Datenschutz](#datenschutz)).

### 1.5.0

- **Downloads anhalten und fortsetzen:** „⏸ Anhalten“ an jedem Download und „Alle anhalten“ über der Warteschlange. „▶ Fortsetzen“ lädt an der erreichten Stelle weiter – auch bei Streams und nach einem Neustart der App.
- **Genaue Suche:** Begriffe in Anführungszeichen finden nur das ganze Wort – „"Eis"“ findet das Eis, aber nicht mehr „Reise“, „Kreis“ oder „Preis“.
- **Mehr Originalfassungen bei der ARD:** Manche Originalversionen führt nur die ARD-Mediathek selbst (z. B. „Amerikanische Fiktion“). Die App findet sie jetzt auch – mit „+ OV“ und Deutsch + Original.
- **Mehrere Filme teilen:** in der Merkliste Häkchen setzen, in anderen Listen mit ⌘/Strg-Klick auswählen, in der Warteschlange über „Teilen…“ – eine Nachricht mit allen Filmtipps und Links.
- **Updates nebenbei:** Die App sieht auch während des Betriebs nach neuen Versionen und lädt sie im Hintergrund. Fehlerbehebungen kommen ohne Hinweisleiste beim nächsten Start.
- **Tastatur:** ⌘/Strg+F springt ins Suchfeld, Menütaste oder Umschalt+F10 öffnen das Kontextmenü, Enter lädt herunter, Esc schließt Dialoge, ein Rahmen zeigt den Fokus. Für VoiceOver und die Windows-Sprachausgabe beschriftet.
- **Homebrew:** auf dem Mac jetzt auch per `brew install --cask` (siehe oben).

Linux bleibt vorerst auf 1.2.2 – die Linux-Fassung folgt Anfang November.

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

Und danke an Haiko, Marko, Johannes und Jan fürs Testen und für viele Anregungen.

## Datenschutz

Die App hat keinen eigenen Server, kein Konto und keine Analyse. Merkliste, Download-Verlauf, Statistik und
Einstellungen liegen nur auf deinem Rechner. Für Suche, Filminfos und Downloads fragt die App direkt bei den
genannten Diensten an (MediathekViewWeb, TMDB, Wikidata/Wikipedia, ARD-API, kinogrid, filmdienst, Server der
Sender); diese sehen dabei deine IP-Adresse und den Suchbegriff bzw. Filmtitel. Nach Updates fragt die App bei GitHub.

## Hinweise

- Bitte nur für Inhalte nutzen, die du privat speichern darfst. Kopiergeschützte Inhalte lädt die App nicht.

Dieses Repository enthält nur die Installer; der Quellcode ist nicht öffentlich.

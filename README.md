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

| Linux Debian/Ubuntu bzw. Fedora | `…-Linux-Debian-Ubuntu.deb` bzw. `…-Linux-Fedora.rpm` |
| Windows ohne Installation (z. B. USB-Stick) | `…-Windows-portabel.zip` bzw. `…-Windows-ARM-portabel.zip` |

**Linux:** Version 0.6.0 gibt es nicht für Linux – bitte [0.5.0](../../releases/tag/v0.5.0) verwenden. Die nächste Version kommt wieder für alle Systeme.

„Source code (zip / tar.gz)“ fügt GitHub automatisch zu jedem Release hinzu – es enthält nur
diese Anleitung, nicht die App.

## Was die App kann

- **Mediatheken durchsuchen** (ARD, ZDF, ARTE, 3sat, Dritte …) – mit Senderauswahl und Filter „nur ab 60 Min.“
- **Kostenlose Filme finden** über kinogrid.com, mit „verfügbar bis“
- **Videos aus Seiten auslesen:** einfach die URL einer Video- oder Übersichtsseite einfügen
- **Herunterladen** mit Warteschlange, automatischem Fortsetzen nach Verbindungsabbrüchen, MP3 und Untertiteln (SRT)
- **Deutsch + Original in einer Datei:** zwei Tonspuren statt zwei Filme
- **Serien:** nach Staffeln sortiert, „Staffel laden“, „✓ geladen“
- **Vorschau** direkt in der App
- **Automatische Updates** ab Version 0.4.0
- **Merkliste:** Filme mit Ablauf-Erinnerung, Serien mit neuen Folgen
- **Empfehlungen** von filmdienst.de
- **Einfach- und Profi-Modus** (Profi mit Protokoll aller Aktionen)
- **Mehrfachauswahl und Sortieren** der Trefferliste
- **Beschreibung nachladen** vom Sender oder aus der Wikipedia
- **Windows portabel** ohne Installation

## Erster Start

Die Installer sind nicht signiert:

- **macOS:** App in „Programme“ ziehen und einmal öffnen – macOS meldet „nicht geöffnet“ → **Fertig**. Dann **Systemeinstellungen → Datenschutz & Sicherheit**, ganz unten bei „Mediathek-Extractor wurde blockiert“ auf **Dennoch öffnen** klicken und mit Passwort bzw. Touch ID bestätigen. Nur einmal nötig; Updates kommen danach automatisch.
  Alternativ im Terminal: `xattr -dr com.apple.quarantine /Applications/Mediathek-Extractor.app`
- **Windows:** „Der Computer wurde durch Windows geschützt“ → „Weitere Informationen“ → „Trotzdem ausführen“.

## Versionen

### 0.6.0

- **Deutsch + Original** auch, wenn man nach „Originalversion“ sucht – die deutsche Fassung wird automatisch dazugesucht.
- **„✓ geladen“** gilt nur für die tatsächlich geladene Fassung.
- **„Alle“** sagt, was es lädt („Deutsch + Original“ oder „nur Deutsch“).
- **Abbrechen** hinterlässt keine Teil-Dateien mehr (auch unter Windows); Reste werden beim Start aufgeräumt.
- **Empfehlungen/Merkliste:** keine Verwechslung mit der vorherigen Suche mehr.
- **Mehrfachauswahl:** ⌘/Strg-Klick, Shift-Klick für Bereiche, ⌘/Strg+A für alle – dann „Herunterladen“ oder „Merken“.
- **Windows portabel:** ZIP ohne Installation, alle Daten bleiben im Ordner neben dem Programm (z. B. auf einem USB-Stick). Updates dort per neuer ZIP.
- **Sortieren:** nach Datum, Titel, Dauer, Sender, „läuft bald ab“ oder Bewertung – je Quelle gemerkt.
- **Beschreibung nachladen:** Fehlt eine Beschreibung (kinogrid, Empfehlungen, eingefügte Seiten), holt die App sie vom Sender – oder aus der Wikipedia (nur wenn es eindeutig dieser Film ist, mit Quellenangabe).
- Suchverlauf entfernt.

### 0.5.0

- **Empfehlungen:** „Sehenswert in Mediatheken“ von filmdienst.de als eigene Quelle – mit Sternen, Ablaufdatum und Link zur Kritik.
- **Qualität wählen:** Beste (HD), Standard (bis 720p) oder Klein – spart Platz.
- **Übersichtlicher:** Senderleiste bricht um statt zu scrollen; Staffel-Ansicht nur bei echten Serien.
- **kinogrid:** „Alle Angebote laden“ statt nur YouTube.
- **Audiodeskription und Gebärdensprache** sind standardmäßig ausgeblendet („alle Fassungen“ zeigt sie).
- **Einfach und Profi:** „Einfach“ zeigt nur das Nötigste (Suchen, Herunterladen, Vorschau – die Originalfassung kommt automatisch als zweite Tonspur mit). „Profi“ zeigt alle Optionen und ein **Protokoll** aller yt-dlp- und ffmpeg-Aufrufe.
- **Untertitel in die MP4** als zuschaltbare Spur statt separater Datei.
- **Infos in der Datei:** Titel, Sender, Datum, Beschreibung und bei Serien Serie/Staffel/Folge – Player und Plex/Jellyfin/Kodi zeigen sie an; auf Wunsch zusätzlich eine .nfo-Datei.
- **Merkliste (★):** Filme merken – die App erinnert beim Start, wenn sie in 3 Tagen ablaufen. Serien verfolgen – neue Folgen erscheinen in der Merkliste und lassen sich mit einem Klick (oder automatisch) laden.
- **Senderlogo entfernen (experimentell):** Die App findet das Logo (z. B. ZDF, ARTE) und kodiert das Video ohne Logo neu. Bei ruhigem Hintergrund unsichtbar, bei unruhigem bleibt ein weicher Fleck.

### 0.4.0

- **Serien nach Staffeln:** Folgen landen in „Serie/Staffel 02/Serie – S02E04 – Titel.mp4“ – so erkennen Plex, Jellyfin und Kodi sie sofort (abschaltbar in den Einstellungen).
- **Serien-Ansicht:** Treffer nach Serie und Staffel gruppiert, mit „Staffel laden“ für alle noch fehlenden Folgen.
- **Übersichtlichere Liste:** Hörfilm-, Gebärdensprach-, Untertitel- und OV-Fassungen sowie Wiederholungen werden zusammengefasst („alle Fassungen“ zeigt sie wieder).
- **„✓ geladen“:** Die App merkt sich, was schon heruntergeladen wurde.
- **Automatische Updates:** Neue Versionen meldet die App selbst und installiert sie auf Wunsch.

### 0.3.1

- **Bessere Titel beim Einfügen von Seiten-URLs:** Ein einzelnes Video heißt jetzt wie die Seite (z. B. „Ein unmöglicher Zufall“) statt wie die Datei.
- **Hinweis, wenn yt-dlp fehlt:** Bei ARTE, ZDF, ARD & Co. bietet die App yt-dlp zum Laden an – für Titel, Beschreibung, beste Qualität und alle Sprachen.
- **Über-Fenster mit Danksagung** an yt-dlp, FFmpeg, MediathekView und die anderen verwendeten Projekte (ⓘ oben rechts).
- **Hinweis:** Die App hat eine neue interne Kennung. Zielordner und Suchverlauf müssen einmalig neu eingestellt werden.

### 0.3.0

- **Senderauswahl:** Knopf „Sender“ unter der Suche, mehrere Sender gleichzeitig (Haupt-, Dritte, Sparten- und Auslandssender). Mit gewählten Sendern geht die Suche auch ohne Suchbegriff – z. B. „alles Neue von ARTE“.
- **Sender in der Ergebnisliste:** Leiste mit Trefferzahl je Sender, ein Klick filtert.
- **Filter „nur ab 60 Min.“:** blendet Trailer, Clips und kurze Beiträge aus.
- **Deutsch + Original in einer Datei:** Gibt es zu einem Film die Originalfassung („+ OV“ in der Liste), lädt die App das Bild einmal und legt deutschen Ton und Originalton als zwei Tonspuren in eine Datei – statt zwei Dateien mit je mehreren Gigabyte.
- **Alle Sprachen in einer Datei** bei ARTE-Seiten (z. B. Deutsch und Französisch).
- **kinogrid:** Option, weitere Anbieter als ladbar zu behandeln (Einstellungen in der Warteschlange).

### 0.2.0

Erste veröffentlichte Version.

- **Mediathek-Suche** über mediathekviewweb (ARD, ZDF, ARTE, 3sat, Dritte …) mit Titel, Sender, Dauer, Datum und Beschreibung.
- **kinogrid.com** als zweite Quelle für kostenlose Filme, mit „verfügbar bis“.
- **Videos aus Seiten auslesen:** Seiten-URL einfügen – die App findet die Videos, auch auf Übersichtsseiten mit mehreren Filmen.
- **Downloads:** Warteschlange mit zwei parallelen Downloads, Fortschritt, Abbrechen und Wiederholen; abgebrochene Verbindungen werden automatisch fortgesetzt.
- **MP3** und **Untertitel** (als SRT) auf Wunsch.
- **Vorschau** direkt in der App.
- **Suchverlauf** mit den letzten fünf Suchen.
- Installer für macOS (Apple Silicon und Intel), Windows (auch ARM) und Linux.

## Danksagung und verwendete Projekte

Der Mediathek-Extractor ist eine Oberfläche, die auf hervorragender freier Software und offenen Daten aufbaut:

- **[yt-dlp](https://github.com/yt-dlp/yt-dlp)** – lädt Streams, Video-Seiten und MP3. Ohne yt-dlp ginge vieles nicht. Die App liefert yt-dlp nicht mit, sondern nutzt eine vorhandene Installation oder lädt auf Wunsch die offizielle Version.
- **[FFmpeg](https://ffmpeg.org)** – fügt Bild und Tonspuren zusammen, wandelt in MP3 um. Ebenfalls nicht mitgeliefert; unter Windows auf Wunsch aus den [yt-dlp-FFmpeg-Builds](https://github.com/yt-dlp/FFmpeg-Builds).
- **[MediathekViewWeb](https://mediathekviewweb.de)** und das Projekt **[MediathekView](https://mediathekview.de)** – die Datenbasis der Mediathek-Suche. Wer die App nützlich findet, kann MediathekView [unterstützen](https://mediathekview.de/spenden/).
- **[kinogrid.com](https://kinogrid.com)** – Verzeichnis kostenloser Filme.
- **[Tauri](https://tauri.app)** (MIT/Apache-2.0), **[hls.js](https://github.com/video-dev/hls.js)** (Apache-2.0) und **[Noto Emoji](https://github.com/googlefonts/noto-emoji)** (Apache-2.0, App-Icon).

Alle genannten Projekte sind unabhängig und nicht für diese App verantwortlich.

## Hinweise

- Bitte nur für Inhalte nutzen, die du privat speichern darfst. Kopiergeschützte Inhalte lädt die App nicht.

Dieses Repository enthält nur die Installer; der Quellcode ist nicht öffentlich.

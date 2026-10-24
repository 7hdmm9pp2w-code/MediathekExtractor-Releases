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

„Source code (zip / tar.gz)“ fügt GitHub automatisch zu jedem Release hinzu – es enthält nur
diese Anleitung, nicht die App.

## Was die App kann

- **Mediatheken durchsuchen** (ARD, ZDF, ARTE, 3sat, Dritte …) – mit Senderauswahl und Filter „nur ab 60 Min.“
- **Kostenlose Filme finden** über kinogrid.com, mit „verfügbar bis“
- **Videos aus Seiten auslesen:** einfach die URL einer Video- oder Übersichtsseite einfügen
- **Herunterladen** mit Warteschlange, automatischem Fortsetzen nach Verbindungsabbrüchen, MP3 und Untertiteln (SRT)
- **Deutsch + Original in einer Datei:** zwei Tonspuren statt zwei Filme
- **Vorschau** direkt in der App

## Erster Start

Die Installer sind nicht signiert:

- **macOS:** Rechtsklick auf die App → „Öffnen“ → „Öffnen“ bestätigen.
- **Windows:** „Der Computer wurde durch Windows geschützt“ → „Weitere Informationen“ → „Trotzdem ausführen“.

## Versionen

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

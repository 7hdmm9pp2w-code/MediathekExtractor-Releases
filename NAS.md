# Mediathek Plus auf dem NAS (Docker)

Die NAS-Fassung lädt rund um die Uhr – auch wenn dein Rechner aus ist. Bedient wird sie im Browser, mit derselben Oberfläche wie die App. Für Intel und ARM, FFmpeg ist dabei, yt-dlp holt sie sich selbst.

## Einrichten auf der Synology (Container Manager)

**Am einfachsten mit dem [yml-Baukasten](https://7hdmm9pp2w-code.github.io/Mediathek-Plus/nas/):** Freigaben für Filme, Serien und Dokus eintragen, `docker-compose.yml` herunterladen und in Schritt 3 als Quelle „docker-compose.yml hochladen“ wählen – dann entfällt Schritt 4.

1. **Paket-Zentrum:** „Container Manager“ installieren (DSM 7.2 oder neuer).
2. **File Station:** den Ordner `docker/mediathek-plus` anlegen.
3. **Container Manager → Projekt → Erstellen:** Name `mediathek-plus`, Pfad `docker/mediathek-plus`, Quelle „docker-compose.yml erstellen“ – den Text unten einfügen.
4. **Drei Stellen anpassen:**
   - `MX_PASSWORD` – dein Passwort
   - `volumes` und `MX_DOWNLOADS` – die Freigabe für die Filme, **genau so geschrieben wie in der File Station** (`Video` ≠ `video`)
   - Serien oder Dokus in eigenen Freigaben? Je Freigabe einen weiteren Block unter `volumes` und `MX_SERIES` bzw. `MX_DOKUS` (siehe [Filme, Serien, Dokus getrennt](#filme-serien-dokus-getrennt))
   - `PUID` / `PGID` – nur falls dein Benutzer nicht 1026 / 100 ist (per SSH: `id`)
5. **Weiter → Fertig.** Dann im Browser `http://<NAS-Adresse>:8080` öffnen und anmelden.

Andere NAS oder Server: siehe [Per Kommandozeile](#per-kommandozeile).

```yaml
services:
  mediathek-plus:
    image: ghcr.io/7hdmm9pp2w-code/mediathek-plus:latest
    container_name: mediathek-plus
    restart: unless-stopped
    ports:
      - "8080:8080"                       # links ggf. anderen Port wählen
    environment:
      MX_PASSWORD: "bitte-ändern"         # Pflicht
      TZ: Europe/Berlin
      PUID: 1026                          # dein Benutzer (Synology meist 1026 / 100)
      PGID: 100
      PGIDS: 101                          # Gruppe administrators – hat auf Synology-Freigaben meist die Schreibrechte
      MX_DOWNLOADS: /volume1/video/Mediathek
    volumes:
      - type: bind                        # Einstellungen, Merkliste, Protokoll
        source: /volume1/docker/mediathek-plus
        target: /data
        bind: { create_host_path: false }
      - type: bind                        # Freigabe für die Filme – links und rechts derselbe Pfad
        source: /volume1/video
        target: /volume1/video
        bind: { create_host_path: false }
```

## Filme, Serien, Dokus getrennt

Liegen Serien und Dokus auf dem NAS in eigenen Freigaben (z. B. `Video`, `Serien`, `Doku` – wie die Bibliotheken in Plex oder Jellyfin), legt die App jede Art dort ab: Serienfolgen in „Serie/Staffel 01“, Dokus erkennt sie an Genre und Sendereihe (Terra X, 37 Grad …). In der Detailansicht lässt sich die Art vor dem Laden ändern. In der yml dazu:

```yaml
    environment:
      MX_DOWNLOADS: /volume1/Video
      MX_SERIES: /volume1/Serien
      MX_DOKUS: /volume1/Doku
    volumes:
      # … wie oben, dazu je Freigabe ein Block:
      - type: bind
        source: /volume1/Serien
        target: /volume1/Serien
        bind: { create_host_path: false }
      - type: bind
        source: /volume1/Doku
        target: /volume1/Doku
        bind: { create_host_path: false }
```

Ohne `MX_SERIES`/`MX_DOKUS` landet alles im Filmordner wie bisher; ändern lässt es sich jederzeit im Browser unter Einstellungen → Download.

## Senderlogo schneller mit der Grafikeinheit

Das Senderlogo zu entfernen heißt, den Film neu zu kodieren. Auf einem NAS mit Intel-Prozessor übernimmt das die eingebaute Grafikeinheit: ein Spielfilm auf der DS724+ dauert so rund 25 Minuten statt 2–3 Stunden. Dazu die Grafikeinheit in den Container durchreichen – im [Baukasten](https://7hdmm9pp2w-code.github.io/Mediathek-Plus/nas/) das Häkchen „Grafikeinheit für Logo-Entfernung nutzen“ setzen oder in der yml direkt unter `restart:` ergänzen:

```yaml
    devices:
      - /dev/dri:/dev/dri                 # Grafikeinheit für die Logo-Entfernung
```

- **Nur bei Intel-Modellen mit Grafikeinheit** (z. B. DS224+, DS423+, DS724+, DS920+). Bei AMD-Ryzen-Modellen (DS923+, DS1522+) und ARM-Modellen (DS223, DS124) weglassen: Fehlt `/dev/dri`, startet der Container nicht.
- Die nötigen Rechte holt sich der Container selbst, an `PUID`/`PGID` ändert sich nichts.
- Ob es klappt, steht im Protokoll des ersten Logo-Auftrags: „Encoder gewählt: … (Grafikeinheit)“. Sonst rechnet die App wie bisher auf dem Prozessor – das Ergebnis ist dasselbe, nur langsamer.
- Auf Wunsch rechnet das NAS nur nachts (1–6 Uhr): Einstellungen → Download (Profi-Modus) → „Erst nachts entfernen“.

## Per Kommandozeile

Für jedes NAS oder jeden Linux-Server mit Docker. Auf der Synology vorher SSH einschalten (Systemsteuerung → Terminal & SNMP) und sich mit `ssh <benutzer>@<NAS-Adresse>` anmelden.

Am einfachsten: Der [Baukasten](https://7hdmm9pp2w-code.github.io/Mediathek-Plus/nas/) zeigt unter „Oder per SSH“ die fertigen Befehle samt yml zum Einfügen. Von Hand geht es so:

```bash
# 1. Eigene Kennung ansehen – uid und gid gehören in PUID/PGID
id

# 2. Ordner anlegen (als dein Benutzer, nicht mit sudo)
mkdir -p /volume1/docker/mediathek-plus /volume1/video/Mediathek
cd /volume1/docker/mediathek-plus

# 3. Die yml von oben als docker-compose.yml speichern und anpassen
nano docker-compose.yml

# 4. Starten
sudo docker compose up -d

# Läuft es? Die letzten Zeilen zeigen Adresse und ggf. Hinweise zu Schreibrechten
sudo docker compose logs --tail 20
```

Außerhalb der Synology heißen die Pfade anders – `/volume1/…` in Schritt 2 und in der yml durch die eigenen ersetzen.

| Was | Befehl (im Ordner der yml) |
|---|---|
| Update | `sudo docker compose pull && sudo docker compose up -d` |
| Anhalten / Starten | `sudo docker compose stop` / `sudo docker compose start` |
| Nach Änderung der yml | `sudo docker compose up -d` |
| Protokoll live | `sudo docker compose logs -f` |
| Entfernen (Daten bleiben im Ordner) | `sudo docker compose down` |

## Mit der Desktop-App verbinden

In der App unter **Einstellungen → Heimnetz** (Profi-Modus) Adresse (z. B. `diskstation.local:8080`) und Passwort eingeben. Dann gibt es **„⬇ Auf dem NAS laden“**, und die Warteschlange zeigt die Downloads des NAS. Auf Wunsch liegen Merkliste und gemerkte Suchen auf dem NAS – dann lädt es neue Folgen selbst, rund um die Uhr. Verbundene Geräte lassen sich im Browser unter Einstellungen → Geräte trennen.

## Gut zu wissen

- **Nur im Heimnetz.** Den Port nicht im Router freigeben – von unterwegs über VPN oder Tailscale.
- **Weitere Freigaben:** einen zweiten Block unter `volumes` ergänzen (wieder links und rechts derselbe Pfad) oder die yml im [Baukasten](https://7hdmm9pp2w-code.github.io/Mediathek-Plus/nas/) neu erzeugen, Projekt neu erstellen. In der App dann unter Einstellungen → Ändern… wählen. Fehlt eine Freigabe, zeigt die App oben den passenden Block zum Kopieren.
- **Hinweis oben in der App „Kein Schreibzugriff“?** Er nennt Benutzer, Gruppen und meist auch gleich die Lösung (z. B. „PGIDS: 101 eintragen“). Sonst in DSM unter Systemsteuerung → Freigegebener Ordner → Berechtigungen deinem Benutzer Schreibrechte geben.
- **Startet nicht, „bind source path does not exist“:** Ein Pfad in `volumes` stimmt nicht – meist die Groß-/Kleinschreibung.
- **Update:** Container Manager → Projekt → Aktion → Erstellen. Merkliste und Einstellungen bleiben.

## Lizenzen

Das Image enthält Pakete aus Debian, darunter [FFmpeg](https://ffmpeg.org) (LGPL/GPL). Den Quellcode aller enthaltenen Pakete in genau diesen Fassungen gibt es bei jedem [Release](../../releases/latest) als `Mediathek-Plus-…-NAS-Quellcode.tar`; die Lizenztexte liegen im Image unter `/usr/share/doc/`. yt-dlp ist nicht enthalten – der Server lädt es beim ersten Start von der offiziellen Seite.

# Mediathek Plus auf dem NAS (Docker)

Die NAS-Fassung lädt rund um die Uhr – auch wenn dein Rechner aus ist. Bedient wird sie im Browser, mit derselben Oberfläche wie die App. Für Intel und ARM, FFmpeg ist dabei, yt-dlp holt sie sich selbst.

## Einrichten auf der Synology (Container Manager)

1. **Paket-Zentrum:** „Container Manager“ installieren (DSM 7.2 oder neuer).
2. **File Station:** den Ordner `docker/mediathek-plus` anlegen.
3. **Container Manager → Projekt → Erstellen:** Name `mediathek-plus`, Pfad `docker/mediathek-plus`, Quelle „docker-compose.yml erstellen“ – den Text unten einfügen.
4. **Drei Stellen anpassen:**
   - `MX_PASSWORD` – dein Passwort
   - `volumes` und `MX_DOWNLOADS` – die Freigabe für die Filme, **genau so geschrieben wie in der File Station** (`Video` ≠ `video`)
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

## Per Kommandozeile

Für jedes NAS oder jeden Linux-Server mit Docker. Auf der Synology vorher SSH einschalten (Systemsteuerung → Terminal & SNMP) und sich mit `ssh <benutzer>@<NAS-Adresse>` anmelden.

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

In der App unter **Einstellungen → NAS** Adresse (z. B. `diskstation.local:8080`) und Passwort eingeben. Dann gibt es **„⬇ Auf dem NAS laden“**, und die Warteschlange zeigt die Downloads des NAS. Auf Wunsch liegen Merkliste und gemerkte Suchen auf dem NAS – dann lädt es neue Folgen selbst, rund um die Uhr. Verbundene Geräte lassen sich im Browser unter Einstellungen → Geräte trennen.

## Gut zu wissen

- **Nur im Heimnetz.** Den Port nicht im Router freigeben – von unterwegs über VPN oder Tailscale.
- **Weitere Freigaben:** einen zweiten Block unter `volumes` ergänzen (wieder links und rechts derselbe Pfad), Projekt neu erstellen. In der App dann unter Einstellungen → Ändern… wählen.
- **Hinweis oben in der App „Kein Schreibzugriff“?** Er nennt Benutzer, Gruppen und meist auch gleich die Lösung (z. B. „PGIDS: 101 eintragen“). Sonst in DSM unter Systemsteuerung → Freigegebener Ordner → Berechtigungen deinem Benutzer Schreibrechte geben.
- **Startet nicht, „bind source path does not exist“:** Ein Pfad in `volumes` stimmt nicht – meist die Groß-/Kleinschreibung.
- **Update:** Container Manager → Projekt → Aktion → Erstellen. Merkliste und Einstellungen bleiben.

## Lizenzen

Das Image enthält Pakete aus Debian, darunter [FFmpeg](https://ffmpeg.org) (LGPL/GPL). Den Quellcode aller enthaltenen Pakete in genau diesen Fassungen gibt es bei jedem [Release](../../releases/latest) als `Mediathek-Plus-…-NAS-Quellcode.tar`; die Lizenztexte liegen im Image unter `/usr/share/doc/`. yt-dlp ist nicht enthalten – der Server lädt es beim ersten Start von der offiziellen Seite.

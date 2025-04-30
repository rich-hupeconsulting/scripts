# Plex Media Docker Stack

This Docker Compose stack manages automation and maintenance for a Plex-based media server.

## Included Services:

- **Tautulli**: Tracks Plex usage stats and sends alerts.
- **Sonarr**: Automatically downloads TV shows using torrent/NZB indexers.
- **Radarr**: Automatically downloads movies.
- **Plex Meta Manager (PMM)**: Manages and updates Plex collections automatically.
- **Duplicacy Web**: Web interface for deduplication and backup of media directories.

## Configuration Notes:

- Media folders are mounted from:
  - TV: /media/newd/TV, /home/rich/TV, /media/newd2/newd2/TV2
  - Movies: /media/newd/Film, /home/rich/Films, /media/newd2/newd2/Film2

- PMM reads the native Plex config from:
  `/var/lib/plexmediaserver/Library/Application Support/Plex Media Server`

- Replace any `1000` UID/GID with your actual user/group if needed.

## To Start:

```bash
docker compose up -d

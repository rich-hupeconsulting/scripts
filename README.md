
# Plex Media Docker Stack

This Docker Compose stack automates media management around a Plex Media Server.

---

## ✅ Services Included

### 🖥️ Tautulli – Plex Stats Dashboard
- **URL**: http://localhost:8181
- **Purpose**: Tracks who watches what on Plex. Sends notifications and creates usage reports.
- **Login**: Set up an admin user on first launch.

### 📺 Sonarr – TV Show Downloader
- **URL**: http://localhost:8989
- **Purpose**: Automatically downloads and renames TV episodes using torrent or NZB indexers.
- **Setup**:
  - Connect to indexers (e.g. Jackett)
  - Connect to your download client (e.g. qBittorrent)
  - Set up your shows and monitor folders

### 🎬 Radarr – Movie Downloader
- **URL**: http://localhost:7878
- **Purpose**: Just like Sonarr, but for movies.
- **Setup**:
  - Add your movie library folders
  - Define quality profiles (e.g. 1080p, HDR)
  - Monitor upcoming or missing movies

### 🧠 Plex Meta Manager – Collection & Metadata Automation
- **Run in background**, no web interface by default.
- **Config path**: `/srv/media/config/pmm/`
- **Purpose**: Automatically create and update smart collections in Plex (e.g. Top IMDb, Recently Aired).
- **How to configure**:
  - Edit `config.yml`, `Movies.yml`, and `TV.yml` in the PMM folder
  - Run container to apply updates, or schedule via cron
- Uses your Plex token to push updates to native Plex

### 🧹 Duplicacy Web – Backup & Duplicate File Manager
- **URL**: http://localhost:3875
- **Purpose**: Provides a browser-based GUI to scan for duplicate files, deduplicate storage, and schedule backups.
- **Login**: No auth by default (can be enabled in UI).

---

## 📂 Mounted Media Paths

- **TV Shows**:
  - `/media/newd/TV`
  - `/home/rich/TV`
  - `/media/newd2/newd2/TV2`

- **Movies**:
  - `/media/newd/Film`
  - `/home/rich/Films`
  - `/media/newd2/newd2/Film2`

- **Downloads**: `/srv/media/Downloads`

---

## 🚀 Getting Started

1. Place your media in the proper folders.
2. Configure Sonarr/Radarr via their web UI.
3. Edit `config.yml` under `/srv/media/config/pmm/` for PMM automation.
4. Run the stack:

```bash
docker compose up -d
```

---

## 🔧 Maintenance

To clean up unused Docker data:

```bash
docker image prune -a
```

To restart PMM manually:

```bash
docker restart plex-meta-manager
```

---

## 📝 Notes

- Plex is expected to run **natively on the host**, not in Docker.
- PMM is configured to read from the native Plex config path:
  `/var/lib/plexmediaserver/Library/Application Support/Plex Media Server`

---

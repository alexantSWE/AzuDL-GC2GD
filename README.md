# AzuDl - GC2GD

**Azizi Universal Downloader - Google Colab to Google Drive**

AzuDl - GC2GD is a Google Colab based universal downloader that downloads supported files directly to Google Drive. It supports direct links, YouTube videos and playlists, torrent magnet links, `.torrent` files, private torrent mode, batch downloads, download history, file management tools, ZIP creation, SHA256 hashing, aria2 status monitoring, duplicate torrent detection, live seeding status, and resumable downloads using aria2 session persistence.

> فارسی: [README.fa.md](README.fa.md)

---

## Version

```text
Version: 1.2.8
```

---

## Features

- Direct link download to Google Drive
- YouTube video download
- YouTube playlist download
- YouTube quality selection
- YouTube audio-only MP3 extraction
- Custom YouTube format ID support
- Auto-fix for video-only YouTube formats by adding best available audio
- Magnet torrent download
- `.torrent` file download from URL or local path
- Private torrent mode
- Optional torrent seeding after download
- Live torrent download progress
- Live torrent seeding status
- Upload speed display during seeding
- Uploaded size display during seeding
- Torrent ratio display
- Seeder and connection display
- Duplicate torrent InfoHash detection
- Resume existing aria2 torrent tasks instead of adding duplicates
- Remove errored duplicate torrents automatically
- aria2 session persistence
- Resume-friendly download behavior
- Auto link type detection
- Batch download
- Download history
- List downloaded files
- Latest file viewer
- Google Drive storage report
- SHA256 hash for latest or selected files
- ZIP selected folder
- ZIP latest downloaded folder
- Dedicated Torrent Tools menu
- Developer information section
- Built-in help menu

---

## What Is New in v1.2.8

Version `1.2.8` focuses on torrent reliability and better torrent management.

AzuDl now reads the torrent `InfoHash` before adding a `.torrent` file to aria2. If the same torrent already exists in aria2, AzuDl does not add a duplicate torrent. It detects the existing GID, resumes or monitors the existing task, and if the existing torrent is in an error state, it removes it and adds the torrent again.

This prevents common aria2 errors like:

```text
InfoHash is already registered
```

---

## Main Menu

```text
1. Auto detect link
2. Torrent tools
3. YouTube video or playlist
4. Direct link
5. Batch download
6. Download history
7. List downloaded files
8. Storage report
9. SHA256 latest file
10. SHA256 selected file
11. ZIP folder
12. ZIP latest folder
13. Latest file
14. Developer
15. Help
16. Exit
```

---

## Torrent Tools Menu

```text
1. Torrent magnet
2. Torrent file
3. Private torrent
4. aria2 status
5. Remove aria2 GID
6. Clear stopped aria2 results
7. Save aria2 session
8. Back
```

---

## Storage Structure

AzuDl creates the following folder structure in Google Drive:

```text
/content/drive/MyDrive/AzuDl-GC2GD
```

```text
AzuDl-GC2GD/
├── TorrentDownloads/
├── YouTubeDownloads/
├── DirectDownloads/
├── BatchDownloads/
├── Archives/
└── Logs/
```

| Folder | Purpose |
|---|---|
| `TorrentDownloads` | Torrent magnet and `.torrent` downloads |
| `YouTubeDownloads` | YouTube video, playlist, and audio downloads |
| `DirectDownloads` | Direct URL downloads |
| `BatchDownloads` | Batch download outputs |
| `Archives` | ZIP files created by AzuDl |
| `Logs` | History, aria2 session file, and debug files |

---

## aria2 Session File

AzuDl stores aria2 session data here:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Logs/aria2.session
```

This file helps aria2 reload unfinished tasks after restarting the notebook.

AzuDl uses:

```text
--continue=true
--always-resume=true
--save-session
--input-file
--force-save=true
```

This makes downloads more resume-friendly.

---

## Important Note About Google Colab Timeout

AzuDl does not bypass Google Colab timeout. Google Colab may disconnect idle or long-running sessions depending on its runtime policies.

AzuDl improves reliability by saving aria2 session data, saving files directly to Google Drive, enabling resume options in aria2, detecting existing torrent tasks, and continuing existing aria2 jobs where possible.

For long-term torrent seeding or unattended downloading, use a VPS or seedbox.

---

## Supported Link Types

AzuDl can automatically detect:

```text
magnet:?...
https://example.com/file.zip
https://example.com/file.torrent
https://youtube.com/...
https://youtu.be/...
```

| Type | Supported |
|---|---|
| Direct HTTP/HTTPS links | Yes |
| FTP links | Yes |
| YouTube videos | Yes |
| YouTube playlists | Yes |
| Magnet links | Yes |
| `.torrent` URLs | Yes |
| Local `.torrent` files | Yes |
| Batch links | Yes |

---

## Direct Downloads

AzuDl can download direct links using aria2.

Examples:

```text
https://example.com/file.zip
https://example.com/video.mp4
https://example.com/archive.rar
https://example.com/document.pdf
```

Optional fields:

- Folder name
- Output file name
- Speed limit
- Custom headers as JSON

Example custom headers:

```json
{"User-Agent":"Mozilla/5.0","Referer":"https://example.com"}
```

---

## YouTube Downloads

AzuDl uses `yt-dlp` to download YouTube videos and playlists.

Supported options:

- Best quality
- Quality limit
- Audio-only MP3
- Playlist download
- Custom format ID
- Metadata saving
- Thumbnail saving

Available quality values:

```text
best
4320
2160
1440
1080
720
480
360
```

---

## YouTube Audio Fix

Some YouTube formats are video-only, especially high quality formats.

For example:

```text
137
```

is often a video-only format.

AzuDl automatically tries to add the best available audio:

```text
137 -> 137+ba/best
```

Recommended custom format examples:

```text
137+140
248+251
22
18
best
```

---

## MP3 Audio Extraction

Choose:

```text
Audio only? y
```

AzuDl extracts audio as:

```text
MP3 320kbps
```

---

## Torrent Downloads

AzuDl supports magnet links, `.torrent` file URLs, local `.torrent` files, private torrent mode, optional seeding, live download progress, live seeding status, duplicate InfoHash handling, and aria2 resume/session persistence.

### Magnet example

```text
magnet:?xt=urn:btih:EXAMPLE_HASH
```

Use:

```text
Torrent Tools > Torrent magnet
```

### Torrent file example

```text
https://example.com/file.torrent
```

Use:

```text
Torrent Tools > Torrent file
```

For public torrents, use `Torrent file`, not `Private torrent`.

---

## Private Torrent Mode

Private torrent mode is designed for private trackers.

Use:

```text
Torrent Tools > Private torrent
```

Recommended input:

```text
.torrent file from your private tracker
```

Private mode disables:

```text
DHT
DHT6
PEX
LPD
```

This is important for private trackers because many private trackers do not allow public peer discovery.

---

## Seeding

When AzuDl asks:

```text
Keep seeding after download? y/n
```

Choose:

```text
y
```

to keep seeding after the download completes.

AzuDl displays live seeding information:

```text
Upload speed
Uploaded size
Ratio
Connections
Seeders
Elapsed seeding time
```

Example:

```text
Seeding Upload: up=1.20 MB/s, uploaded=350.40 MB, ratio=0.42, connections=8, seeders=12, time=08:31
```

Seeding only works while the Colab runtime is alive. For long-term seeding, use a VPS, seedbox, or dedicated server.

---

## Why AzuDl Uses 525600 Minutes for Seeding

Some aria2 builds do not accept:

```text
seed-time=-1
```

So AzuDl uses:

```text
525600
```

This means 525600 minutes, which is around one year. Since Colab will disconnect much earlier than that, this effectively means: seed as long as the Colab runtime is alive.

---

## Duplicate Torrent Handling

AzuDl reads the torrent InfoHash before adding `.torrent` files. If the torrent is already registered in aria2, AzuDl will detect the existing torrent, show the existing GID, resume or monitor the existing task, and remove and re-add it if the existing task is errored.

---

## aria2 Status

Use:

```text
Torrent Tools > aria2 status
```

This shows:

```text
GID
Status
Name
InfoHash
Progress
Completed size
Download speed
Upload speed
Uploaded size
Ratio
Connections
Seeders
Errors
```

---

## Removing a Torrent Task

Use:

```text
Torrent Tools > Remove aria2 GID
```

Then paste the GID shown in aria2 status.

This can be useful when a torrent is stuck, duplicated, errored, or when you want to stop a seeding task.

---

## Batch Download

Batch download allows multiple links to be downloaded one by one.

Supported in batch mode:

- Direct links
- YouTube links
- Magnet links
- `.torrent` links

Unknown links are skipped.

---

## Download History

AzuDl stores download history in:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Logs/download_history.json
```

History includes type, source, output, status, time, format, seed mode, and error message.

---

## File Management Tools

AzuDl includes:

```text
List downloaded files
Show latest file
Storage report
SHA256 latest file
SHA256 selected file
ZIP folder
ZIP latest folder
```

ZIP files are saved in:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Archives
```

---

## Speed Limit Examples

```text
500K
2M
10M
```

Leave empty for no speed limit.

---

## Requirements

AzuDl installs required packages inside Colab:

```bash
apt install -y aria2 ffmpeg p7zip-full
pip install tqdm requests yt-dlp
```

| Tool | Purpose |
|---|---|
| aria2 | Direct, torrent, magnet downloads |
| ffmpeg | YouTube merging and audio extraction |
| yt-dlp | YouTube download engine |
| tqdm | Progress bars |
| requests | HTTP requests |
| p7zip-full | Archive support |

---

## How to Use

1. Open Google Colab: `https://colab.research.google.com`
2. Create a new notebook.
3. Paste the full AzuDl code into a cell.
4. Run the cell.
5. Authorize Google Drive mount.
6. Choose an option from the menu.

---

## Recommended Usage

For public torrent files:

```text
Torrent Tools > Torrent file
```

For private tracker torrents:

```text
Torrent Tools > Private torrent
```

For YouTube:

```text
YouTube video or playlist
```

For direct files:

```text
Direct link
```

For mixed links:

```text
Auto detect link
```

---

## Legal Notice

Use AzuDl only for content that you have the right to download, store, or distribute. The developer is not responsible for misuse of this project. AzuDl is a downloader tool. Responsibility for the downloaded content belongs to the user.

---

## Limitations

- Google Colab can disconnect at any time.
- Colab is not suitable for permanent torrent seeding.
- Some direct links require authentication.
- Some websites block Colab IP addresses.
- Some YouTube videos may require cookies or may not be available in Colab.
- Private tracker seeding should be done on a VPS or seedbox for reliable long-term ratio.
- Google Drive write speed may vary.

---

## Developer

```text
Developer: The Azizi
Project: AzuDl - GC2GD
Full Name: Azizi Universal Downloader - Google Colab to Google Drive
```

Links:

- X: https://x.com/the_azzi
- GitHub: https://github.com/TheGreatAzizi
- Telegram: https://t.me/luluch_code
- Git: https://git.theazizi.ir/TheAzizi
- Website: https://theazizi.ir

---

## Repository Description

```text
AzuDl - GC2GD is a Google Colab based universal downloader for downloading direct links, YouTube videos, playlists, magnet links, torrent files, and private torrents directly to Google Drive with aria2 resume support, live progress, seeding status, batch downloads, history, ZIP tools, and SHA256 utilities.
```

---

## Suggested Commit Message

```text
fix(torrent): detect duplicate infohash and resume existing aria2 task
```

Alternative:

```text
release: AzuDl GC2GD v1.2.8
```

---

## Changelog

### v1.2.8

- Added torrent InfoHash detection before adding `.torrent` files
- Added duplicate torrent detection
- Added resume/monitor behavior for existing aria2 torrent tasks
- Added automatic removal of existing errored torrent tasks
- Improved aria2 status output with InfoHash
- Kept dedicated Torrent Tools menu
- Kept private torrent mode
- Kept live seeding status
- Kept aria2 session persistence
- Kept YouTube audio format fix
- Kept ZIP, SHA256, history, and file tools

### v1.2.7

- Fixed tqdm bool error during seeding status display

### v1.2.6

- Moved torrent features into a dedicated Torrent Tools menu

### v1.2.5

- Added live torrent seeding status
- Added aria2 session persistence
- Added resume-friendly aria2 settings

### v1.2.4

- Fixed invalid infinite seed-time issue
- Replaced invalid `-1` seed time with long valid seed time

### v1.2.3

- Improved `.torrent` download validation
- Improved aria2 RPC error messages

---

## License

Choose the license that matches your repository policy.

Recommended open-source options:

```text
MIT
Apache-2.0
GPL-3.0
```

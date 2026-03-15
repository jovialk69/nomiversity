# Nomi Archive — Image & Prompt Toolkit

A lightweight, offline toolkit for Nomi.ai users to log, organise, and browse their generated images alongside the prompts that created them. No installation, no accounts, no cloud — everything runs locally in your browser.

---

## What's Included

| File | Purpose |
|---|---|
| `logger.html` | Log new images and prompts as you create them |
| `gallery.html` | Browse your full archive with search and filters |
| `prompts.csv` | Your master list of images and prompts (sample included) |
| `images/` | Folder where your downloaded images live |

---

## Folder Structure

Set up your folder like this before you begin:

```
Nomi Archive/
├── images/          ← put all your downloaded Nomi images here
├── logger.html      ← open this to log new entries
├── gallery.html     ← open this to browse your archive
└── prompts.csv      ← your master prompt list (auto-exported from logger)
```

---

## Quick Start

### Step 1 — Set up your Nomis in the Logger

1. Open `logger.html` in Safari or Chrome
2. In the left sidebar under **Add Nomi**, type each of your Nomi names and press `+` or hit `Return`
3. Your Nomis will appear in the sidebar — they're saved automatically between sessions

### Step 2 — Log an image

Each time you generate and download an image from Nomi.ai:

1. Select the **Nomi name** from the dropdown
2. Click the image picker area and select the downloaded image from your `images/` folder
3. If the filename is messy (e.g. `Aurora Selfie (3).png`), a blue **rename hint** will appear showing you exactly what to rename it to (e.g. `aurora_006.png`) — hit **Copy name**, then rename it in Finder:
   - Select the file → press `Return` → paste the name → press `Return` again
4. Paste the **image prompt** from Nomi.ai into the prompt field
5. Click **Log entry →**

The entry is saved instantly. Filenames are auto-numbered per Nomi (e.g. `aurora_001.png`, `aurora_002.png`).

### Step 3 — Export your prompts.csv

When you're ready to update your gallery:

1. In `logger.html`, click **↓ Export prompts.csv** in the sidebar
2. Save the file into your `Nomi Archive/` folder, replacing the old one

### Step 4 — Browse your gallery

1. Open `gallery.html` in Safari or Chrome
2. Under **Load your archive**, click the image picker → navigate to your `images/` folder → select all images (Cmd+A)
3. Click the CSV picker → select your `prompts.csv`
4. Click **Load gallery**

Your full archive appears — browse by Nomi, search prompts by keyword, and copy any prompt to clipboard with one click.

---

## The prompts.csv Format

If you want to edit or build your CSV manually, the format is:

```
filename, nomi_name, prompt
aurora_001.png, Aurora, "silver hair, violet eyes, cinematic portrait, soft morning light"
aurora_002.png, Aurora, "dark forest, bioluminescent glow, fantasy art style"
lyra_001.png, Lyra, "short auburn hair, golden hour rooftop, lifestyle photography"
```

- **filename** — must match exactly what the image file is named in your `images/` folder
- **nomi_name** — the name of your Nomi (drives the filter tabs in the gallery)
- **prompt** — the full image prompt; wrap in quotes if it contains commas
- First row must be the header: `filename,nomi_name,prompt`

You can edit this in any spreadsheet app (Numbers, Excel) or a plain text editor. If using Numbers or Excel, always export/save as `.csv` not `.numbers` or `.xlsx`.

---

## Importing an Existing CSV

If you already have a `prompts.csv` from a previous session or from another device:

1. Open `logger.html`
2. Click **↑ Import existing CSV** in the sidebar
3. Select your file — any new entries will be added without duplicating existing ones

---

## Tips

- **Logger saves automatically** — your Nomis and entries persist in your browser's local storage between sessions. You don't need to re-enter anything each time you open it.
- **Gallery requires reloading each session** — because browsers can't access your local files directly without you selecting them, you'll need to re-select your images and CSV each time you open `gallery.html`. This is a browser security feature, not a bug.
- **Naming convention** — the logger auto-generates filenames like `nominame_001.png`. Keeping this consistent makes your archive much easier to manage long-term.
- **Image number** — the logger auto-increments the number per Nomi. You can override it manually if needed (e.g. if you're backfilling old images).
- **Dark mode** — both files automatically switch to dark mode based on your system settings.

---

## Nomi.ai API Note

As of early 2026, the Nomi.ai API does not expose an endpoint for retrieving generated images or their prompts. This toolkit is designed to work around that limitation by giving you a fast, low-friction way to log prompts manually at the time of creation. If Nomi.ai adds image history to their API in the future, this workflow could be further automated.

For API feedback, reach the Nomi.ai team at support@nomi.ai or via their Discord: https://discord.com/invite/nomiai

---

## Hosting on GitHub Pages (Recommended)

Hosting on GitHub Pages unlocks the full version of `gallery.html` — it auto-loads `prompts.csv` and all images automatically, with no file picking required.

### One-time setup

1. Go to [github.com](https://github.com) and sign in
2. Click **+** → **New repository** → name it `nomi-archive` → set to **Public** → click **Create repository**
3. On your Mac, open Terminal and run:
   ```
   cd ~/Desktop
   git clone https://github.com/YOUR_USERNAME/nomi-archive.git
   ```
4. Copy the contents of this zip into that cloned folder
5. Push to GitHub:
   ```
   cd nomi-archive
   git add .
   git commit -m "Initial archive"
   git push
   ```
6. On GitHub, go to your repo → **Settings** → **Pages** → under Source select **main branch** → click **Save**
7. Your gallery will be live at `https://YOUR_USERNAME.github.io/nomi-archive/`

### Updating with new images

Each time you add new images and export a fresh `prompts.csv` from the logger:

1. Copy the new images into the `images/` folder in your cloned repo
2. Replace `prompts.csv` with your latest export
3. Run in Terminal:
   ```
   cd ~/Desktop/nomi-archive
   git add .
   git commit -m "Add new images"
   git push
   ```
4. GitHub Pages updates automatically within ~30 seconds

---

## Compatibility

**gallery.html has two modes:**
- **GitHub Pages (web server)** — auto-loads everything, no file picking, all features enabled
- **Local file** — requires manual file selection each session (browser security restriction)

`logger.html` always works locally — it uses browser storage and does not need a server.

- Works in Safari and Chrome on Mac
- Works in Chrome on Windows
- No internet connection required after first open (fonts load from Google Fonts on first use)
- No installation, no Node.js, no dependencies

---

*Built with Claude on claude.ai*

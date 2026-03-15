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

Hosting on GitHub Pages unlocks the full version of `gallery.html` — it auto-loads `prompts.csv` and all images automatically, with no file picking required. Your gallery becomes a live website accessible from any browser or device.

---

### Part 1 — Create your GitHub repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** icon in the top-right corner → **New repository**
3. Name it `nomi-archive`
4. Set visibility to **Public**
5. Leave everything else as default and click **Create repository**

---

### Part 2 — Generate a Personal Access Token

GitHub does not accept your account password for Git operations. You need a Personal Access Token (PAT) instead. You only need to do this once.

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Generate new token** → **Generate new token (classic)**
3. In the **Note** field, type something like `nomi-archive-mac`
4. Set **Expiration** to **No expiration** (or choose a date if you prefer)
5. Under **Select scopes**, tick the **repo** checkbox (this is all that's needed)
6. Scroll down and click **Generate token**
7. **Copy the token immediately** — it looks like `ghp_xxxxxxxxxxxxxxxxxxxx`
   > GitHub only shows this token once. If you lose it, you'll need to generate a new one.

---

### Part 3 — Push your files to GitHub

Open Terminal on your Mac and run these commands one at a time, replacing `YOUR_USERNAME` with your GitHub username:

```bash
# Step 1 — Store your credentials in macOS Keychain (one-time only)
git config --global credential.helper osxkeychain

# Step 2 — Go to your Desktop (or wherever you want to keep the folder)
cd ~/Desktop

# Step 3 — Clone the empty repository
git clone https://github.com/YOUR_USERNAME/nomi-archive.git
```

When prompted:
- **Username**: your GitHub username
- **Password**: paste your Personal Access Token (not your GitHub password)

macOS Keychain saves this — you won't be asked again.

```bash
# Step 4 — Move into the cloned folder
cd nomi-archive
```

Now copy all the files from this toolkit (gallery.html, logger.html, prompts.csv, and the images/ folder) into the `nomi-archive` folder on your Desktop.

```bash
# Step 5 — Add, commit, and push all files
git add .
git commit -m "Initial archive"
git push
```

---

### Part 4 — Enable GitHub Pages

1. Go to `https://github.com/YOUR_USERNAME/nomi-archive`
2. Click **Settings** (the tab at the top of the repo)
3. In the left sidebar, scroll down and click **Pages**
4. Under **Source**, select **Deploy from a branch**
5. Under **Branch**, select **main** and keep the folder as **/ (root)**
6. Click **Save**
7. Wait 30–60 seconds, then refresh the page
8. A green banner will appear saying **"Your site is published at…"**

Your gallery is now live at:
```
https://YOUR_USERNAME.github.io/nomi-archive/
```

Bookmark this URL — it's your gallery from any browser, on any device.

---

### Part 5 — Updating with new images

Follow these steps every time you want to add new images to your live gallery.

**Step 1 — Export a fresh prompts.csv from the logger**

1. Open `logger.html` in your browser
2. Make sure all your new entries are logged
3. Click **↓ Export prompts.csv** in the left sidebar
4. When the download dialog appears, navigate to your `nomi-archive` folder on your Desktop and save it there — **replacing the existing `prompts.csv`**

> This is the most important step. The gallery reads directly from `prompts.csv` in the repo — if you skip this, your new images won't appear.

**Step 2 — Copy your new images into the repo folder**

1. Open Finder and navigate to your `nomi-archive` folder on your Desktop
2. Open the `images/` subfolder inside it
3. Copy (or move) your newly downloaded and renamed images into this `images/` folder

**Step 3 — Push everything to GitHub**

Open Terminal and run these commands:

```bash
cd ~/Desktop/nomi-archive
git add .
git commit -m "Add new images"
git push
```

**Step 4 — Check your live gallery**

Wait 30–60 seconds, then open your gallery URL:
```
https://YOUR_USERNAME.github.io/nomi-archive/
```
Your new images should appear automatically. If they don't, do a hard refresh in your browser: **Cmd + Shift + R**.

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

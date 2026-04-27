# PressTrack

T-shirt inventory and press order manager — built for multi-shop screen printing businesses.

## Features

- Track inventory by type, brand, style/SKU, color, and size
- Brand-scoped style/SKU dropdowns (Bella+Canvas styles stay separate from Gildan styles, etc.)
- Cost-per-blank tracking with total stock value
- AI-powered receipt import (paste supplier receipts, Claude parses them)
- Press order logging with shop name, order #, and notes
- Multi-shop support with order log filtered by shop
- Export/import backup as JSON
- Works offline after first load
- Dark mode support

---

## Setup: GitHub Pages (first time)

### Step 1 — Create a new GitHub repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** in the top right → **New repository**
3. Name it `presstrack` (or anything you like)
4. Set it to **Public**
5. Leave everything else as default — **do not** check "Add a README"
6. Click **Create repository**

### Step 2 — Upload the files

1. On your new empty repo page, click **uploading an existing file**
2. Drag all four files into the upload area:
   - `index.html`
   - `manifest.json`
   - `icon-192.png`
   - `icon-512.png`
3. Scroll down, add a commit message like `Initial upload`, and click **Commit changes**

### Step 3 — Enable GitHub Pages

1. In your repo, click **Settings** (top tab bar)
2. In the left sidebar, click **Pages**
3. Under "Branch", select **main** and keep the folder as `/ (root)`
4. Click **Save**
5. Wait about 60 seconds, then refresh — you'll see a green banner with your URL:
   `https://YOUR-USERNAME.github.io/presstrack/`

That's it! Bookmark that URL and it works on any device.

---

## Adding your Anthropic API key

The AI receipt parsing feature needs an Anthropic API key:

1. Go to [console.anthropic.com](https://console.anthropic.com) and sign up
2. Navigate to **API Keys** → **Create Key**
3. Copy the key
4. In PressTrack, click the **⚙ Settings** icon (top right)
5. Paste your key and click **Save key**

The key is stored only in your browser's local storage — it never leaves your device except when calling Anthropic's API directly.

---

## Updating the app (iterating)

When you want to make changes after real-world testing:

1. Go back to Claude and describe what you want changed
2. Claude generates an updated `index.html`
3. Download it
4. Go to your GitHub repo
5. Click on `index.html` → click the **pencil (edit) icon** → click the **three dots** → **Upload file**, or simply:
   - Click `index.html` in the file list
   - Click the **pencil icon** to edit
   - Replace all content and commit, **OR**
   - Go to **Add file** → **Upload files** → drag the new `index.html` → commit

GitHub Pages updates within 1–2 minutes.

---

## Backup your data

Go to **⚙ Settings → Export backup (JSON)** to download all your inventory and orders as a file. Keep this somewhere safe — it's your data safety net.

---

## Local storage note

All data is saved in your browser's local storage. This means:
- Data is per-device and per-browser (Chrome on your Mac ≠ Safari on your iPhone)
- Use **Export/Import** to move data between devices
- Clearing browser data will erase inventory — export a backup first

# PressTrack

Inventory and order manager built for decorated apparel businesses — screen printing, embroidery, DTG, heat transfer, vinyl, and beyond. Track your blank stock, log production orders, manage reservations, and run monthly reports — all in a single HTML file that runs in any browser.

---

## Features

### Inventory
- Grouped browse view: **Type → Brand → Style → Color/Size**
- Filter by type, brand, style, color, size, and status (In stock / Low / Out)
- Quick-reset filter button when filters are active
- **Lot-based cost tracking** — each purchase is stored as its own lot with its own cost; buying the same shirt at a different price never overwrites old cost data
- Cost/unit shows a range (e.g. `$3.25–$5.10`) when multiple lots exist at different prices
- Stock value calculated across all lots
- **By color** and **By size** pivot grid views — choose any type (T-shirt, Tote bag, etc.) and see a cross-tab of your stock at a glance
- Watch/reorder alerts per SKU — a collapsible warning panel lists low or out-of-stock watched items, sortable by qty, brand, or color
- Status filter: In stock, Low stock, Low + In stock, Out of stock
- Low stock threshold configurable in Settings

### Press Orders
- Slide-out panel from the inventory page — click **+ New press order** on the Order Log tab
- **Fill from reservation** — pull items directly from a saved or working reservation into the order cart
- FIFO cost calculation — blank cost per order line is calculated from oldest lots first
- Order # required on submit to keep the log clean
- Per-shop color coding on order pills (set in Settings → Shops)
- Deducts inventory on submit; closing without submitting returns everything

### Reservations
- **Working reservation** — click **Reserve** on any inventory row to add 1 unit to a running cart; a sticky amber bar shows what's building
- **Reservations slide-out** — review, name, and save working reservations; or build one from scratch line by line
- Reserved qty shows in the inventory status column: `7 avail · 1 res.`
- Press order availability respects reservations — reserved stock won't appear as available
- Release a reservation at any time to return stock to available

### Order Log
- Grouped by order # — each order is a collapsible card showing shop, date, total units, blank cost, and note
- Filter by shop, type, date period (All time / This month / Last month / Custom range)
- Advanced filters: brand, style, color, size, minimum units in order
- Sort newest or oldest first
- Edit any log entry (date, shop, order #, blank cost, note)
- Delete a log entry — stock is automatically restored to inventory
- Clear entire log moved to Settings → Danger zone

### Reports
Two sub-tabs:

**Monthly Report**
- KPI cards: units purchased, blank cost purchased, units pressed, blank cost pressed
- Inventory purchased detail table (collapsible)
- Orders pressed detail table (collapsible)
- Supplier breakdown — units, total cost, avg cost/unit, order numbers per supplier for the month
- Download CSV or Print/Save PDF

**Popularity**
- All-time bar charts: top brands, colors, sizes, types, shops, and styles by units pressed
- Screen only — not included in print output

### Add Stock
- Slide-out from the Inventory tab — click **+ Add stock**
- Three modes: **Single entry**, **Size run (bulk)**, **CSV import**
- Each addition creates a new cost lot — previous lot costs are never modified
- Supplier and supplier order # fields on all modes
- CSV template downloadable with all supported columns

### Settings
- **Catalog manager** — rename or delete brands, styles, colors, types, shops, and suppliers; changes cascade through inventory and order log
- **Shop colors** — assign a color pill to each shop for easy scanning in the order log
- **Low stock threshold** — configure what qty triggers the Low badge
- **Backfill supplier info** — assign supplier and order # to existing stock log entries that predate the supplier field
- **Export backup (JSON)** — saves all inventory, orders, reservations, and catalog data
- **Import backup** — restore from any previous export
- **Clear order log** — in the Danger zone, requires deliberate navigation to Settings

---

## Setup: GitHub Pages

### Step 1 — Create a repository

1. Go to [github.com](https://github.com) and sign in
2. Click **+** → **New repository**
3. Name it `presstrack` (or anything you like), set to **Public**
4. Do **not** check "Add a README"
5. Click **Create repository**

### Step 2 — Upload the files

1. On the empty repo page, click **uploading an existing file**
2. Drag in all four files: `index.html`, `manifest.json`, `icon-192.png`, `icon-512.png`
3. Add a commit message and click **Commit changes**

### Step 3 — Enable GitHub Pages

1. Go to **Settings → Pages**
2. Under Branch, select **main** and folder **/ (root)**
3. Click **Save**
4. After ~60 seconds your app is live at `https://YOUR-USERNAME.github.io/presstrack/`

Bookmark that URL — it works on any device, including mobile.

---

## Updating the app

1. Describe your changes to Claude
2. Download the updated `index.html`
3. In your GitHub repo, go to **Add file → Upload files**, drag in the new `index.html`, and commit

GitHub Pages updates within 1–2 minutes.

---

## Data and backup

All data lives in your browser's **local storage**. This means:

- Data is per-device and per-browser (Chrome on Mac ≠ Safari on iPhone)
- Use **Settings → Export backup (JSON)** to download everything
- Use **Import backup** to restore or move data to another device or browser
- Clearing browser data will erase your inventory — export a backup first

Regular exports are your safety net. Keep them somewhere you won't lose them.

---

## Inventory data model

Each SKU (type + brand + style + color + size combination) stores an array of **purchase lots**:

```
{ qty, cost, isoDate }
```

Every time you add stock, a new lot is created. Press orders deduct from the oldest lots first (FIFO). This preserves accurate cost history and means a sale-price purchase never corrupts the cost of stock you bought earlier at a different price.

---

## Local development

No build step required. Open `index.html` directly in any browser. Everything is self-contained in a single file.

# Changelog

All notable changes to the **Asset Template Explorer**.

---

## [1.0.2] — 2026-09-22

### 🔑 Highlights
- A version number is now visible directly in the app, so you can always tell which build you're running
- Fixed a bug where a tree branch could stop responding to clicks and need a page refresh to recover

### ✨ Added
- **Version badge** — small, fixed label in the bottom-left corner showing the current version (e.g. `v1.0.2`), visible from every view

### 🐛 Fixed
- **A tree branch could stop expanding/collapsing**, especially after uploading your own files (rather than the sample), requiring a refresh and re-upload to recover. Caused by a timing issue where uploading files could attach a duplicate click handler to the tree, so every click fired twice and canceled itself out. Fixed by ensuring the tree's click handling is only ever set up once, no matter how the files are loaded.

---

## [1.0.1] — 2026-09-22

### 🔑 Highlights
- Hide or delete a model/task — with a warning if it's shared elsewhere in the tree
- New **Export click model** button — same report as before, now live from your current edits
- Cleaner Import screen with an animated progress bar
- Exports now work when hosted outside claude.ai (Netlify, local file, etc.)
- Three real bugs fixed, including one that made navigation feel broken

### ✨ Added
- **Hide/Unhide** for models and tasks (separate from Delete) — keeps the data, just removes it from Click Preview
- **Shared-model warning** — if you hide, delete, or edit something used in more than one place, you'll see every affected location before confirming
- **Legend** on the Explorer sidebar explaining what "Deleted" and "Hidden" mean
- **Upload progress bar** on the Import screen — fills as each file loads, with a friendly status message
- **Click Model export** — a flattened spreadsheet of every click path (Click 1–4/task) with a `isVisible` column showing what's actually reachable in Click Preview
- **"Export click model" button** in the Explorer — generates that same report live, reflecting any edits you've made
- **README.md** — setup and usage docs

### 🔄 Changed
- The root of the tree ("All Baselines") now **starts expanded** — no more extra click to see your top-level branches
- Root no longer shows a "hidden" icon (it was never a real option there anyway)
- Export file renamed to `asset-template-export.zip`
- Positioned as an **internal tool for business analysts**, not a client demo — removed leftover "Corrigo" branding from app text
- **Task Template baseline updated** to your cleaned file (7,077 → 1,562 rows). Only one asset lost its tasks, and it's a branch Click Preview already skips — no real impact

### 🐛 Fixed
- **Navigation felt like scrolling instead of moving to a new page** — the Import screen was quietly staying visible behind the Explorer the whole time. Now switching views is clean and instant.
- **Clicking "Click Preview" sometimes looked like it returned to the starting page** — same root cause as above, now fixed.
- **The shared-model warning popup could get stuck on screen**, unresponsive to clicks — it was appearing before you'd even done anything. Fixed, and it now also closes with a click outside or the Escape key as backups.
- **Export and Export click model showed "Downloads aren't available in this view" and stayed disabled** whenever the app was opened outside claude.ai (Netlify, a local file, etc.). Both buttons now fall back to a standard browser download in that case, so exporting works the same everywhere.

---

## [1.0.0] — 2026-09-18

**Initial release**, marked as *Asset Template Explorer V1*.

### ✨ Added
- **Import** — drag-and-drop the three baseline files, or load a built-in sample instantly
- **Explorer** — browse the asset tree, edit names/tasks inline, delete/restore items, light & dark mode, and export your edits back into the original 3-file format
- **Click Preview** — a clickable simulation of the real end-user request flow, with a clear breadcrumb trail, two-column layout for long lists, and smooth navigation animations
- Renamed from *Facility Asset Explorer* to **Asset Template Explorer**

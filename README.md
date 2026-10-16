# Asset Template Explorer — v1.4.0

An internal tool for business analysts to import, browse, edit, and export asset templates. It has two modes:

- **Builder** — build and review a template from the three baseline import files (Asset, Model, Task) before a deployment.
- **Editor** — adjust the asset template of a deployed space using its Workzone asset data (Spaces) file, without touching Models or Tasks.

No backend. No install. Just open `index.html` in any modern browser.

---

## Features

### Upload screen
- Switch between **Builder** and **Editor** with the tabs at the top
- **Builder:** upload the Asset, Model and Task Template files, then click **Proceed** — or load the embedded sample baseline
- **Editor:** upload the Spaces file (required) and, optionally, the instance's Model Template, then click **Proceed**
- Files are checked on upload; a wrong file type is rejected with a message

### Builder
- Collapsible asset hierarchy tree with a count on each folder
- Asset page shows the **model** and its **tasks** (with priority and NTE)
- **Rename** assets in place — the Path of every row underneath updates automatically
- **Edit task text** in place; **Edit NTE** (whole numbers) and **Edit Priority** (priorities used in the Task file) from the task ⋮ menu
- **Sidebar ⋮ — Delete / Restore** changes the Asset Template only; **deleting a parent deletes everything under it** (with a confirm listing what will be deleted) and its children are locked until the parent is restored
- **Model ⋮ on the asset page** — **Hide / Unhide model** (Public in the Model file), **Delete / Restore model** (Action in the Model file only; asks first if the model is used in more than one place) and **Delete / Restore on Asset Template**
- Hidden or deleted models, and everything under them, don't show in Click Preview
- **Hide / delete / restore tasks** from the task ⋮ menu
- Restoring a row that was Delete in the original file sets its Action to **Add**
- **Export** — a zip of the three files with the standard formatting (blue header, grey required/optional row, frozen top rows, column widths); extra sheets kept
- **Export click model** (in the Export menu — download icon, top right) — flattened click paths for exactly what Click Preview shows

### Editor
- Tree of property › spaces › assets, with tags for **NEW**, **MOVED**, **RENAMED** and **Locked** items
- **Rename**, **Add asset** (model required; searchable list when a Model Template is loaded), **Move to…** (within the same space), **Delete / Restore** — spaces themselves can't be renamed or deleted
- **Multi-select** to delete or move several models at once (Shift+click for a range, "Select all" on an open branch)
- **Lock / Unlock** — Recurring and Engineering models, and Equipment next to Recurring, are locked automatically when the file loads
- **Export** — the full Spaces file in its original format: original rows (renames as Update) → Delete rows → Add rows; moved items are deleted and re-added with every original value

### Both modes
- **Click Preview** — a clickable simulation of the end-user request flow (Equipment and Recurring excluded), with breadcrumb and slide animations
- **Export preview** — the file exactly as it will be exported, opening on the changed rows (old value crossed out above the new one) with summary counts and an Export button; Builder has **Asset Template / Model / Task** tabs; columns have vertical lines and can be resized
- **Undo** (button or **Ctrl+Z / Cmd+Z**) and **Escape** to cancel an edit
- **Session history** — the clock button (top right) opens a panel listing every action with its status (Not exported / Exported / Undone / No file change) and a status line at the top; click an entry to jump to the item (it flashes briefly; on Click Preview, renamed items open there); pin it to the right side and resize it; **Export history** downloads a CSV (Exported, Description, Time) — also in the Export menu (download icon, top right)
- **Show deleted items** switch — off by default, hides deleted items (and everything under a deleted parent) from the tree
- **Safety prompts** — red confirm for deletes, confirm before Start over with unexported changes, and a warning when closing the tab
- **Naming rules** — new names use letters, numbers and spaces only; duplicate names on the same path are allowed after a confirmation
- **Keyboard support** for uploads, tabs, the tree, menus and pop-ups; screen-reader labels
- Light / dark theme (meets WCAG AA contrast in both)

---

## File Structure

```
Asset template viewer/
│
├── index.html          # The entire app — open this in any browser
├── CHANGELOG.md        # Version history
├── README.md           # This file
└── Baseline Data/      # Baseline import files used for testing
```

---

## How to Use

### Option A — Open locally
1. Open `index.html` in a modern browser (Chrome, Edge, Firefox)
2. An internet connection is needed when the page first loads (the spreadsheet libraries and fonts load from a CDN); all file processing runs in the browser

### Option B — Host on Netlify
1. Go to [netlify.com](https://netlify.com)
2. Drag `index.html` into the deploy drop zone
3. Share the generated URL with your team

---

## How to Update

1. Open the **Asset Template Maker** Claude Project
2. Request changes (new features, fixes, data updates)
3. Replace `index.html` in this folder with the updated file and add an entry to `CHANGELOG.md`
4. Commit and push — Netlify auto-deploys

---

## Source Data

The embedded sample baseline (Builder) is built from three baseline import files:

| File | Contents |
|---|---|
| `AssetTemplateData_BASELINE.xlsx` | 273 asset rows across the full hierarchy |
| `ModelTemplate_Baseline.xlsx` | 314 model definitions |
| `TaskTemplate_Baseline.xlsx` | 7,079 task rows |

In-scope after filtering: **262 models**, **1,483 tasks**

Editor works on a Workzone asset data export (Spaces file, `AssetData*.xlsx`), for example `Baseline Data/CorrigoAssetData_Spaces.xlsx`.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, grid, flexbox) |
| Logic | Vanilla JavaScript (ES5-compatible) |
| Excel reading | [SheetJS](https://sheetjs.com/) `xlsx@0.18.5` |
| Excel export (keeps formatting) | [ExcelJS](https://github.com/exceljs/exceljs) `4.4.0` |
| ZIP export | [JSZip](https://stuk.github.io/jszip/) `3.10.1` |
| Fonts | IBM Plex Sans, IBM Plex Mono (Google Fonts) |

---

## Versioning

| Version | Date | Notes |
|---|---|---|
| 1.4.0 | 2026-10-16 | Export preview tabs for all three files, Model ⋮ menu on the asset page, Edit NTE / Priority, standard export formatting, History highlight, new sample baseline |
| 1.3.2 | 2026-10-15 | Export moved to an icon next to History, export messages as pop-ups, fixed multi-select bar layout, drawn ⋯/⋮ icons |
| 1.3.1 | 2026-10-14 | Removed the file-count labels from the mode switch |
| 1.3.0 | 2026-10-13 | Session history panel with CSV export, Show deleted items switch, delete/hide warnings for parents, spaces can't be deleted |
| 1.2.0 | 2026-10-13 | Export preview, Undo/Ctrl+Z, formatting-safe Builder exports, path-safe renames and deletes, auto-lock, new sidebar header, keyboard and contrast fixes |
| 1.1.0 | 2026-10-10 | Editor mode for deployed spaces (Spaces file) |
| 1.0.2 | 2026-09-22 | Version badge; tree click fix |
| 1.0.1 | 2026-09-22 | Hide/unhide, shared-model warning, Export click model |
| 1.0.0 | 2026-09-18 | Initial release — Import, Explorer, Click Preview |

See `CHANGELOG.md` for full details.

---

## Author

Vernon — Technical Virtual Assistant  
Built with Claude (Anthropic) · Asset Template Maker Project

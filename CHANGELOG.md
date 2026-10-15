# Changelog

All notable changes to the **Asset Template Explorer**.

---

## [1.3.2] — 2026-10-15

### 🔄 Changed
- **Export moved to the top right** — an Export icon now sits next to History and light/dark (order: Export, History, light/dark) on the Builder and Editor tree pages. It opens a small menu with that mode's export options (Builder: Export, Export click model, Export history; Editor: Export, Export history). The Export button and ▾ menu are removed from the sidebar
- Export messages ("Preparing files…", "Exported — …", errors) and undo notes now show as a brief pop-up under the top-right icons; Builder now also confirms a successful export
- Editor multi-select bar has a fixed layout: count and Clear on top, **Move selected** / **Delete selected** as two equal buttons below; labels no longer change with the count

### 🐛 Fixed
- Editor multi-select bar buttons shifted and wrapped unevenly when items were selected
- The ⋯ and ⋮ menu buttons could look like dashes on some computers — they are now drawn icons; the ⋯ button matches the height of the Undo button

---

## [1.3.1] — 2026-10-14

### 🔄 Changed
- Upload page: removed the "3 files" / "1 file" labels from the Builder / Editor mode switch

---

## [1.3.0] — 2026-10-13

### 🔑 Highlights
- New **Session history** in both modes — every action you take is listed with whether it has been exported; click an entry to jump to the item, and download the list as a CSV
- New **Show deleted items** switch — deleted items (and everything under a deleted parent) are hidden from the tree by default
- **Clearer warnings** before deleting a parent or hiding a model that has items under it
- Editor: **spaces can no longer be deleted**

### ✨ Added

**Both modes**
- **History button** (clock icon) next to the light/dark button — shown in Builder and Editor, not on the upload page
- **History panel**
  - Status line at the top, always shown: "N changes · not exported yet", "All changes exported · last export at HH:MM", or "No changes yet"
  - Two columns, newest first: **Action** (what was done, with the item's path and time) and **Status** — *Not exported*, *Exported*, *Undone*, or *No file change* (Editor lock / unlock)
  - Entries stay after an export; only their status changes to *Exported*
  - Undoing an edit that hasn't been exported marks it *Undone*; undoing an edit that was already exported adds a new "Undid: …" entry (*Not exported*)
  - **Click an entry to jump** to that item in the tree (turns on *Show deleted items* if the item is deleted)
  - Opens only when clicked; floats below the top-right buttons; closes with ✕, Escape or a click outside
  - **Pin** docks it on the right side; the pinned panel can be **resized** by dragging its left edge (or with ← / → on the edge), and is limited so the asset page always keeps at least 400px, rechecked when the window is resized
  - A long history scrolls inside the panel
  - One session only — Start over or loading new files starts a fresh history
- **Export history** — downloads the session history as a CSV with three columns: *Exported*, *Description* (action and item path), *Time*; available in the History panel and in the sidebar Export ▾ menu
- **Show deleted items** switch (off by default) in the sidebar
  - Off: deleted items and everything under a deleted parent are hidden from the tree; folder counts only count what's shown; in Builder, deleted tasks are also hidden on the asset page with a note saying how many
  - On: everything shows, with strikethrough, as before
  - The asset page of a hidden deleted item explains how to bring it back

**Builder**
- **Delete confirm for parents** — deleting an item that has items under it asks first and lists what will be deleted ("Delete N items"); items with nothing under them are deleted straight away
- **Hide confirm** — hiding a model that has items under it warns that those items will also disappear from Click Preview (count and list); if the model is used in several places, the places are listed in the same pop-up

### 🔄 Changed
- **Sidebar change counter removed** — the status now lives in the History panel
- Editor's Export button gets a **▾ menu** (holding *Export history*), matching Builder
- Builder's Export ▾ menu is always available (it now also holds *Export history*)
- The *Show deleted items* label sits on the left with the switch at the right end of the row
- Deleted item labels and Editor's RENAMED tag use the standard muted colour (with strikethrough for deleted) so they meet contrast requirements when shown
- The asset-page breadcrumb keeps clear of the History and light/dark buttons

### 🐛 Fixed
- Editor: **spaces could be deleted** — Delete is no longer offered for spaces (⋮ menu or asset page), with or without locked items

---

## [1.2.0] — 2026-10-13

### 🔑 Highlights
- New **Export preview** in both modes — see the file exactly as it will be exported (same columns, same row order) before downloading, with an Export button on the page
- **Safer exports** — Builder now keeps the original file formatting, renames update every row underneath, deleting a parent deletes everything under it, and Editor writes rows in an order the import can apply
- **Undo everywhere** — Builder gets Undo, and both modes support **Ctrl+Z** (Cmd+Z on Mac)
- **Cleaner sidebar** — a reorganised header with one main Export button, a collapsible legend and more room for the tree
- **Full keyboard support and readable contrast** in light and dark mode

### ✨ Added

**Both modes**
- **Export preview** page — opens on the changed rows with a switch to see all rows; changed cells show the old value crossed out above the new one; summary counts at the top (rows in file, changed, added, set to Delete, renamed, path updated); only the file's own columns are shown
- **Ctrl+Z / Cmd+Z** triggers Undo (ignored while typing in a field or while a pop-up is open)
- **Unsaved-changes warning** when closing or refreshing the tab with changes that haven't been exported
- **Duplicate-name confirm** — giving an item the same name as another item on the same path is allowed (the system allows it) but asks first: *"A model called "ATM" already exists on this path: … Rename / Add / Move anyway?"*
- **Keyboard support**
  - Tab reaches the upload boxes; Enter or Space opens the file picker
  - ← / → switch between the Builder and Editor tabs
  - Tree: ↑ / ↓ move, → opens a branch, ← closes it or goes to the parent, Home / End, Enter selects, Shift+F10 opens the row's ⋮ menu
  - Menus: ↑ / ↓ move between items, Escape closes and returns to the row or button
  - Pop-ups: focus moves in, Tab stays inside, focus returns to where it was on close
- Screen-reader labels: ⋮ buttons are named after their row ("Options for ATM"), the Builder/Editor switch is announced as tabs, Editor's select boxes are named

**Builder**
- **Proceed** button on the upload screen — the explorer no longer opens by itself once the 3 files are loaded ("Load the sample baseline" still opens straight away)
- **Undo** button — steps back through renames, task edits, deletes/restores and hides/unhides
- **Escape** leaves a name or task edit without saving
- **Model shown on the asset page** ("Model: …" under the title)
- **Name rule** — new names can only use letters, numbers and spaces (existing names are left as they are)
- **Locked children** — items under a deleted parent can't be edited; the asset page explains why and how to unlock (restore the parent)
- **Start over** asks for confirmation when there are unexported changes

**Editor**
- **Auto-lock on load** — items directly under a space whose Model contains *Recurring*, *Engineering Equipment*, *Engineering* or *z Engineering Equipment* are locked, and so is *Equipment* when it sits next to a Recurring branch; the opening page lists what was locked
- **Searchable model list** when a Model Template is uploaded (picks must come from the file); without one, the model is typed in
- **Name rule** — new names (rename / add) can only use letters, numbers and spaces; moving an item keeps its existing name

### 🔄 Changed

**Both modes**
- **Sidebar header reorganised** — title row with Undo and a ⋯ menu (holding *Start over*), a row with Click Preview and Export preview, a full-width Export button, the change counter, and a **collapsible legend**
- **Change counter** reads "N changes · not exported yet", switches to **"Exported"** after an export and counts edits made since then (undo keeps the count right)
- **Upload screens** — both use a green **Proceed** button; new descriptions; heading is "Asset Template Explorer"
- **Delete and Start over confirms** use a red button
- **Version badge** only shows on the upload page
- Name standardised to **Asset Template Explorer** everywhere; "Corrigo" removed from the interface text and file names (export zip now contains `AssetTemplateData.xlsx`; upload hints read `AssetTemplateData*.xlsx` / `AssetData*.xlsx`)
- **Colours** — deeper amber in light mode, dark text on amber/green buttons in dark mode, priority labels with light/dark shades — all pass WCAG AA contrast

**Builder**
- **Exports keep the original formatting** — header colours, frozen rows, column widths and the explanation / "Regular Asset only" sheets; only data cells change (the sample baseline exports as before)
- **Renaming an asset updates the Path of every row under it**; renaming the top level also updates TemplateName
- **Deleting a parent deletes everything under it**; restoring the parent (or Undo) brings them back — Model and Task files are not affected
- Breadcrumb uses **">"** between levels (was "/")
- Click Preview's first step comes from the **TemplateName** column
- Sidebar totals removed — the per-folder counts in the tree stay
- "Export click model" moved into the Export **▾** menu
- Start over asks only when there are unexported changes

**Editor**
- **Move** now writes the original row as *Delete* and a new *Add* row (blank ID) that **copies every value** from the original row
- **Export row order** — original rows (Update) → Delete rows (deepest first) → Add rows (parents first), so a new or moved item can reuse a name that's being deleted
- "EDITOR MODE · property" line, header totals and the "Changes" box on the opening page removed
- Model shown once, in the Details card
- "Select multiple" moved to its own row under Click Preview / Export preview
- The "Space name is final" note on space pages removed (spaces still can't be renamed)

### 🐛 Fixed
- Builder: renaming a parent left its children pointing to the old name (broken rows on import)
- Builder: deleting a parent left its children as Add rows under a parent that wouldn't exist
- Builder: names with ">" were accepted and added a false level to the path
- Builder: after Start over and reloading, the asset page could show an item from the previous session
- Builder: the change counter still said "not exported yet" after a successful export
- Editor: a moved item lost its original values (e.g. IsModelInheritance / IncludeNonControllable reset to defaults)
- Editor: deleting an item and adding a new one with the same name wrote the Add row before the Delete row
- Both: white text on amber buttons was unreadable in dark mode (1.97:1)
- Upload error grammar ("an Asset Template file")

---

## [1.1.0] — 2026-10-10

### 🔑 Highlights
- New **Editor** mode: adjust the asset template of a property that's already deployed, using its Spaces asset data export — no need to re-edit Models and Tasks
- The import screen now has two modes: **Builder** (the existing three-file flow) and **Editor** (one file)
- Editor exports keep the original file's formatting — header colours, column widths, frozen rows and the Field Explanations sheet

### ✨ Added
- **Builder / Editor switch** on the import screen, each with its own description
- **Editor upload** — the Spaces file (required) plus an optional Model Template. With a Model file, adding an asset offers a dropdown of its Regular Asset models; without one, the model name is typed in
- **Editor tree** — property > spaces > assets, with tags for New, Moved, Renamed and Locked items
- **Rename** assets (space names are final and can't be renamed)
- **Add asset** under any item, with the Model required and default values for new rows: Status Online, CriticalFacilities Inherit, Restricted No, IsModelInheritance N/A, IncludeNonControllable No
- **Delete** with a reminder listing everything under a parent that will also be deleted; **Restore** to bring it back
- **Move to…** within the same space only — the record is deleted at the old location and re-added at the new one with a new ID
- **Lock / Unlock** from the ⋮ menu — locked models (and everything under them) can't be changed, selected, moved or deleted, plus a reminder to lock Recurring and Engineering Equipment
- **Multi-select** — tick models to delete or move them together, with Shift+click to tick a range and **Select all** on any open branch; exits automatically after a delete or move
- **Undo** — steps back through renames, adds, deletes, restores, moves and locks one at a time
- **Click Preview for Editor** — starts at the spaces (or straight inside the space when there's only one) and shows that tasks aren't visible in this mode
- **Export** writes the full Spaces file back: original rows in place (renames as Update), then Add rows (parents first), then Delete rows (deepest first)

### 🔄 Changed
- Version bumped to **1.1.0**

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

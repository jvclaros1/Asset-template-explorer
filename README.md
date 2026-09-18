# Asset Template Explorer — V1

An internal tool for business analysts to import, browse, edit, and export templates (Asset, Model, and Task). Built to streamline template review and preparation before deployments.

No backend. No install. Just open the HTML file in any browser.

---

## Features

### Import
- Upload the 3 files (Asset Template, Model Template, Task Template) to review how it would look like before uploading to the system
- Or load the embedded sample baseline, and edit from there

### Explorer
- Collapsible asset hierarchy tree
- Inline editing of asset names and task text
- Delete / restore assets via the ⋮ row menu
- Change counter tracks all edits in the session
- Export edits back as three `.xlsx` files (zipped, standard import format)
- Light / dark theme toggle

### Click Preview
- Interactive drill-down menu for reviewing the asset and task hierarchy
- Covers: Building Exterior, Building Interior, Project Activity
- Excludes Equipment and Recurring models
- 2-column layout for menus with more than 8 items
- Slide animation on forward drill and back navigation
- Fully clickable breadcrumb path (All Baselines > Category > … > Task)
- Task text only at the leaf level — clean and distraction-free

---

## File Structure

```
asset-template-explorer/
│
├── facility-asset-explorer.html   # The entire app — open this in any browser
└── README.md                      # This file
```

---

## How to Use

### Option A — Open locally
1. Download `facility-asset-explorer.html`
2. Open it in any modern browser (Chrome, Edge, Firefox)
3. No internet connection required after the file loads (all processing runs in the browser)

### Option B — Host on Netlify
1. Go to [netlify.com](https://netlify.com) and sign up free
2. Drag `facility-asset-explorer.html` into the deploy drop zone
3. Share the generated URL with your team

---

## How to Update

1. Open the **Asset Template Maker** Claude Project
2. Request changes (new features, fixes, data updates)
3. Download the updated `facility-asset-explorer.html`
4. Replace the file in this folder
5. Commit and push — Netlify auto-deploys

---

## Source Data

The embedded sample baseline is built from three baseline import files:

| File | Contents |
|---|---|
| `AssetTemplateData_BASELINE.xlsx` | 273 asset rows across the full hierarchy |
| `ModelTemplate_Baseline.xlsx` | 314 model definitions |
| `TaskTemplate_Baseline.xlsx` | 7,079 task rows |

In-scope after filtering: **262 models**, **1,483 tasks**

---

## Tech Stack

| Layer | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, grid, flexbox) |
| Logic | Vanilla JavaScript (ES5-compatible) |
| Excel parsing | [SheetJS](https://sheetjs.com/) `xlsx@0.18.5` |
| ZIP export | [JSZip](https://stuk.github.io/jszip/) `3.10.1` |
| Fonts | IBM Plex Sans, IBM Plex Mono (Google Fonts) |

---

## Versioning

| Version | Date | Notes |
|---|---|---|
| V1 | 2026-09-18 | Initial release — Import, Explorer, Click Preview |

---

## Author

Vernon — Technical Virtual Assistant  
Built with Claude (Anthropic) · Asset Template Maker Project

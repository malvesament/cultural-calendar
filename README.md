# Cultural Calendar 2026

A live, searchable calendar of major cultural events across Music, Cinema & TV, Art, Design, and Fashion.

---

## File structure

```
/
├── index.html          ← the web app (never needs editing)
├── README.md           ← this file
└── data/
    ├── music.json      ← all music events
    ├── cinema.json     ← cinema & TV events
    ├── art.json        ← art events (in progress)
    ├── design.json     ← design events (in progress)
    └── fashion.json    ← fashion events (in progress)
```

---

## How to set up GitHub Pages (one-time, ~10 minutes)

### Step 1 — Create a GitHub account
Go to [github.com](https://github.com) and sign up if you don't have an account.

### Step 2 — Create a new repository
1. Click the **+** icon (top right) → **New repository**
2. Name it: `cultural-calendar` (or anything you like)
3. Set it to **Private** if you want it password-protected, **Public** if open access is fine
4. Click **Create repository**

### Step 3 — Upload the files
1. On your new repository page, click **uploading an existing file**
2. Drag and drop all the files:
   - `index.html`
   - `README.md`
   - The entire `data/` folder (upload music.json, cinema.json, art.json, design.json, fashion.json)
3. Scroll down, write a commit message like `initial upload`, click **Commit changes**

> **Important:** GitHub needs to see the folder structure. Upload the data files inside a `data/` subfolder. To create the folder when uploading: type `data/music.json` in the filename field and GitHub creates the folder automatically.

### Step 4 — Enable GitHub Pages
1. Go to your repository → **Settings** (top tabs)
2. Scroll down to **Pages** in the left sidebar
3. Under **Source**, select **Deploy from a branch**
4. Choose branch: **main**, folder: **/ (root)**
5. Click **Save**

### Step 5 — Get your URL
After 1–2 minutes, refresh the Settings → Pages page.
Your live URL will appear: `https://yourusername.github.io/cultural-calendar`

Done. Share that URL with your team.

---

## How to update events (your workflow with Claude)

### Adding events to an existing category
1. Open the relevant JSON file on GitHub (e.g., `data/music.json`)
2. Click the **pencil icon** (Edit this file)
3. Copy all the text
4. Paste it into a Claude conversation and say: *"Add these events to the music JSON: [event details]"*
5. Claude returns updated JSON
6. Paste it back into GitHub, click **Commit changes**
7. The live site updates in ~30 seconds

### Adding a new category (e.g., Art)
The `art.json`, `design.json`, and `fashion.json` files are already in place with the right structure but empty `events` arrays. To populate them:
1. Open a Claude conversation
2. Say: *"Research and populate this JSON with art events for 2026"* and paste the empty JSON
3. Claude researches and returns populated JSON
4. Upload to GitHub

### The event schema
Every event in a JSON file follows this structure:
```json
{
  "id": "unique-slug",
  "cat": "sub-category-id",
  "name": "Event Name",
  "date": "Human-readable date (e.g. May 12–23)",
  "date_sort": "YYYY-MM-DD (for sorting and calendar)",
  "location": "City, Country",
  "note": "Optional description or details."
}
```
- `id` must be unique within the file (use lowercase-with-dashes)
- `cat` must match one of the `id` values in the `categories` array at the top of the file
- `date_sort` drives the calendar view — use the start date

---

## Adding a new top-level section (e.g., Sport, Literature)
1. Create a new JSON file (e.g., `data/sport.json`) following the same structure as `music.json`
2. Open `index.html`, find the `CATEGORY_DEFS` array (~line 10 of the script), and add one line:
   ```js
   { id: 'sport', label: 'Sport', color: '#your-color', file: 'data/sport.json' },
   ```
3. Upload both files to GitHub. The new tab appears automatically.

---

## Password protection (optional)
GitHub Pages public repositories are open to anyone with the URL. If you want password protection:
1. Sign up at [netlify.com](https://netlify.com)
2. Connect your GitHub repository
3. Go to Site Settings → Access control → Password protection
4. Set a password

Netlify deploys the same files but adds a password gate. Your team enters the password once per browser session.

# Nutrilens calorie tracker project setup
_Exported on 30/05/2026 at 15:19:25 GMT+5:30 from Cursor (3.4.20)_

---

**User**

Create a new project called "nutrilens-calorie-tracker". 
Set up a single-file HTML app (index.html) with the following structure:
- No frameworks, no npm, no build step — pure HTML/CSS/JS
- Google Fonts: Syne (display) + DM Sans (body)
- Chart.js from CDN: https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js
- Mobile-first design, max-width optimized for 390px screens
- Dark theme: background #0a0a0a, surface #111111, accent green #4ade80
- CSS variables for all colors at :root level
- All state stored in localStorage under key "nutriLensG"

Create the file and commit it with message: "feat: project scaffold"

---

**Cursor**

Creating the nutrilens-calorie-tracker project scaffold and committing it. Checking the workspace layout first.


Creating the project scaffold with a complete single-file HTML app structure.


**nutrilens-calorie-tracker** is set up and committed.

### Project layout
- `nutrilens-calorie-tracker/index.html` — single-file app (no npm, no build)

### What’s included
- **Fonts:** Syne (display/logo) + DM Sans (body) via Google Fonts
- **Chart.js 4.4.1** from the CDN you specified
- **Mobile-first:** `max-width: 390px`, safe-area padding, sticky header
- **Dark theme** with `:root` CSS variables (`--color-bg`, `--color-surface`, `--color-accent`, etc.)
- **localStorage** under key `nutriLensG` with `loadState()` / `saveState()` and a default shape: `{ goal, meals, history }`
- **UI scaffold:** calorie ring (doughnut), weekly bar chart, today’s meal list, “+ Log meal” FAB (demo entry for now)

### Commit
```
f65a11f feat: project scaffold
```

Open the app by opening `nutrilens-calorie-tracker/index.html` in a browser (or serve that folder with any static server). The FAB adds a sample meal so you can confirm charts and persistence right away.

---

**User**

Add a 4-tab navigation system to index.html with pages: Home, Scan, Weekly, Goals.

Requirements:
- Sticky nav bar at top with backdrop blur
- App logo "NutriLens" with green accent on "Lens"
- Tab switching via JS: switchPage(name) function
  - Hides all .page divs, shows only #page-{name}
  - Marks active tab with .active class
- Streak badge (🔥 count) in top-right of nav
- Page transition: fadeUp animation (opacity 0→1, translateY 10px→0, 0.3s ease)
- Each page is a div with class "page" and id "page-home", "page-scan", etc.

Commit: "feat: navigation and page routing"


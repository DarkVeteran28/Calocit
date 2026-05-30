# Nutrilens calorie tracker project setup
_Exported on 30/05/2026 at 15:21:34 GMT+5:30 from Cursor (3.4.20)_

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

---

**Cursor**

Reading `index.html` to integrate the 4-tab navigation and page routing.


Restructuring the app with a sticky blurred nav, four routed pages, and `switchPage` routing.


Using class-based visibility only — the `hidden` attribute conflicts with the fadeUp animation.


Added a 4-tab navigation system and committed as `2177f6f feat: navigation and page routing`.

### Navigation
- **Sticky nav** with `backdrop-filter: blur(12px)` and semi-transparent background
- **Logo:** Nutri**Lens** (green accent on “Lens”)
- **Streak badge** top-right: `🔥 {count}` from `state.streak` in `nutriLensG`
- **Tabs:** Home · Scan · Weekly · Goals with `.active` styling

### Page routing
`switchPage(name)`:
- Removes `.active` from all `.page` elements
- Shows only `#page-{name}` and retriggers **fadeUp** (opacity 0→1, `translateY(10px→0`, 0.3s ease)
- Toggles `.active` on matching `.nav-tab` buttons
- Hides the FAB when not on Home

### Content split
| Page | Content |
|------|---------|
| **Home** | Daily ring, macros, today’s meals, date, FAB |
| **Scan** | Placeholder for camera scan |
| **Weekly** | Bar chart (moved from Home) |
| **Goals** | Placeholder for goal settings |

---

**User**

Build the Home page dashboard inside #page-home with these components:

1. HERO SECTION (bg #111111):
   - Date label: current weekday + date, uppercase, muted
   - Greeting: "Good Morning/Afternoon/Evening 👋" based on hour
   - Animated SVG calorie ring (170x170px):
     * Two circles at cx=85 cy=85 r=68, stroke-width=11
     * Background circle: rgba(255,255,255,0.05)
     * Progress circle: green→cyan gradient, stroke-dasharray=427.3
     * Starts at stroke-dashoffset=427.3 (empty), fills clockwise
     * Center shows: current calories consumed, "of {goal} kcal"
     * id="calRing" for JS manipulation
   - 3-column macro grid (Protein/Carbs/Fat):
     * Each card: label (colored), value in grams, thin progress bar
     * Protein = blue (#60a5fa), Carbs = amber (#fbbf24), Fat = coral (#fb7185)

2. SCAN CTA BUTTON:
   - Full width, green background, "Scan Your Meal with AI"
   - onClick: switchPage('scan')

3. FOOD LOG LIST:
   - Section header: "Today's Log" + meal count
   - Empty state with 🍽️ emoji when no meals
   - Each food item: emoji icon + name + macro summary + calorie count + time
   - Items rendered in reverse order (newest first)

State shape in localStorage:
{
  goals: { calories: 2000, protein: 150, carbs: 250, fat: 65 },
  diary: { "Mon Jun 1 2026": { items: [], totals: { calories:0, protein:0, carbs:0, fat:0 } } },
  streak: 0, bestStreak: 0, lastLogDate: null,
  weekHistory: { "Mon Jun 1 2026": 1450 }
}

JS functions needed: updateUI(), renderFoodList(), todayDiary()

Commit: "feat: home dashboard with calorie ring and macro cards"

---

**Cursor**

Building the Home dashboard and migrating state to the new shape. Reading the current file.



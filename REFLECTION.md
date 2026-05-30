# NutriLens — Project Reflection

An honest look at building a Cal AI–style tracker with vanilla web tech and Gemini Vision.

## What Was Easy

**UI layout** — A single `index.html` with CSS variables and a 390px max-width made the mobile-first design straightforward. Sticky nav, card-based sections, and tab routing with `switchPage()` stayed simple without a framework.

**Chart.js integration** — Bar and doughnut charts on the Weekly page plugged in quickly. Destroy-and-recreate on each `renderWeekly()` avoided the classic “canvas already in use” error once that pattern was in place.

**localStorage persistence** — For an MVP, serializing `goals`, `diary`, `weekHistory`, and streak fields to `nutriLensG` was enough. No backend, auth, or sync logic — users get instant load/save with minimal code.

## What Was Hard

**Gemini JSON response parsing** — The model is supposed to return raw JSON, but it often wraps output in markdown fences or adds a short preamble. Stripping fences and regex-matching `\{[\s\S]*\}` before `JSON.parse` was necessary. Empty or malformed `foods` arrays still needed explicit validation before rendering.

**Calorie ring SVG math** — The progress ring uses `stroke-dasharray` and `stroke-dashoffset` on a circle with circumference ≈ 427.3 (`2π × 68`). Getting “empty at start, fill clockwise from top” required `transform="rotate(-90 85 85)"` plus `offset = circumference × (1 - progress)`. Small mistakes made the ring jump backward or look capped wrong.

**Streak logic edge cases** — Streak updates run on each `addNutrition()` call, but only the first log of a day should count. Comparing `lastLogDate` to `today` and `yesterday` via `toDateString()` works for most cases, but logging at **11:59 PM** vs **12:01 AM** is literally adjacent days — that’s correct for a “daily” streak, yet feels harsh without timezone clarity. Users traveling across timezones could also see odd streak behavior; production apps would normalize to a fixed timezone or “logging day” boundary.

## What I’d Improve

1. **Barcode scanner** — Packaged foods with UPC codes could pull nutrition from Open Food Facts or similar, reducing reliance on vision for labeled items.
2. **Meal templates** — Save “usual breakfast” or frequent meals for one-tap logging without re-scanning.
3. **Water intake tracking** — Separate goal and progress bar for hydration alongside calories.
4. **Push notifications** — Remind users to log lunch/dinner (would need a PWA + service worker or native wrapper).

## What I Learned

**Gemini Vision is surprisingly accurate for food recognition** — With a strict JSON prompt and low temperature, it often names specific dishes and plausible portions. It’s not perfect on hidden oils or restaurant portions, but it’s good enough for a demo and daily awareness.

**localStorage is sufficient for MVP-level persistence** — For a competition prototype, browser storage avoids hosting costs and complexity. The tradeoff is no cross-device sync and a ~5MB cap — fine for text JSON, not for image history.

**SVG stroke animations are more precise than canvas for ring charts** — The home calorie ring is pure SVG with CSS `transition` on `stroke-dashoffset`. Chart.js doughnuts are great for macro breakdowns, but a single-value ring is cleaner and sharper in SVG without fighting chart config.

---

*NutriLens — built with vanilla HTML/CSS/JS and Google Gemini Vision.*

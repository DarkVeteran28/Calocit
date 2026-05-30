# NutriLens — AI Calorie Tracker

A mobile-first calorie tracking app inspired by Cal AI, powered by **Google Gemini Vision** (free tier) for food photo analysis. No frameworks, no build step — open `index.html` and start logging meals.

## Description

NutriLens lets you photograph meals and get AI-estimated calories and macros, then track daily intake against personalized goals. Data persists locally in your browser so you can use it offline after the first analysis.

## Features

- **Food photo scanning** — Upload a meal image; Gemini 2.5 Flash Vision identifies foods and estimates nutrition
- **Macro tracking** — Protein, carbs, and fat with color-coded progress on Home and Goals
- **Daily diary** — Today's log with emoji icons, macros, calories, and timestamps (newest first)
- **Weekly history charts** — 7-day calorie bar chart with goal line; macro donut for today
- **Streak tracking** — Consecutive-day logging streak with personal best
- **Goal setting** — Custom daily targets for calories and macros

## How to Run

1. Clone or download this repository.
2. Open `nutrilens-calorie-tracker/index.html` in a modern browser (Chrome, Safari, or Firefox).
3. Go to the **Scan** tab and enter a free Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey) → **Get API key**.
4. Upload a food photo and tap **Analyze with Gemini Vision (Free)**.
5. Add results to your diary and explore **Home**, **Weekly**, and **Goals**.

No install, npm, or server required.

## Tech Stack

| Layer | Choice |
|-------|--------|
| UI | Vanilla HTML, CSS, JavaScript |
| AI | Google Gemini 2.5 Flash Vision API |
| Charts | [Chart.js](https://www.chartjs.org/) 4.4.1 (CDN) |
| Storage | `localStorage` (`nutriLensG` key) |
| Fonts | Google Fonts — Syne, DM Sans |

## API Used

**Google AI Studio (Gemini API)** — Free tier for developers

- **Model:** `gemini-2.5-flash` (vision + text)
- **Limit:** ~1,500 requests/day (subject to Google’s current quotas)
- **Billing:** No credit card required for the free API key
- **Docs:** [https://ai.google.dev/](https://ai.google.dev/)

## Project Structure

```
.
├── README.md
├── REFLECTION.md
├── ai-logs/              # AI conversation logs (see below)
└── nutrilens-calorie-tracker/
    └── index.html        # Single-file app
```

## AI Logs

All Cursor / AI assistant conversation logs for this project should be saved in the **`ai-logs/`** folder at the repository root. This keeps prompts, iterations, and debugging history together for submission and review.

## Gemini Debug Logging

To log full Gemini request/response/parsing details in the browser console:

```js
localStorage.setItem('nutriLensGeminiDebug', 'true');
```

Reload the page, run a scan, then open DevTools → Console. Set to `'false'` to disable.

## License

Built for educational / competition submission. Gemini API usage is subject to [Google’s terms](https://ai.google.dev/terms).

# Sahiti — Handoff Report for Manus

You are taking over / continuing a **6-language Smart India Hackathon prototype** at:

`C:\Users\dheeraj\OneDrive\Desktop\sahiti\gov-site\`

It is a **static, vanilla HTML + CSS + JS** app (NO build step, NO framework, NO package.json).
It opens directly by double-clicking `index.html`. No server needed (except one offline
note below).

---

## 1. HARD BRANDING RULES (do not violate)

- Branded ONLY as **"Sahiti" / "By Team Sahiti"**.
- **NEVER** use "Government of India", any ministry name, or the official **Star of India
  State Emblem** anywhere. The national emblem image was already removed because using it is
  illegal without authorization (State Emblem of India Act, 2005). Keep it out.
- Use the **tricolour palette** (navy `#1e3a8a` / saffron `#ff9933` / white) as a *retail*
  theme only, plus an accent blue `#2563eb`. No ministry affiliation implied.

---

## 2. FILE MAP (master files)

| File | Role |
|------|------|
| `index.html` | Login page + cinematic intro |
| `otp.html` | OTP page (any 6 digits accepted) |
| `onboarding.html` | 2-step business setup |
| `dashboard.html` | Main app with sidebar + 7 tabs |
| `css/styles.css` | All styling |
| `js/app.js` | All logic |
| `js/i18n.js` | 6 language dictionaries + runtime (`t`, `applyLanguage`, etc.) |
| `DEBUG_REPORT.md` | Older review request to Claude (ignore / optional) |

---

## 3. USER FLOW (do not break)

1. `index.html` — enter a valid 10-digit mobile → `sessionStorage['userPhone']` → `otp.html`
2. `otp.html` — enter ANY 6 digits → `onboarding.html`
3. `onboarding.html` — pick location (Pune/Lohegaon) → business → loan intent → `dashboard.html`
4. `dashboard.html` — guarded dashboard with:
   - **Loan Calculator** (EMI)
   - **Document Guide** (3 category chips → doc list)
   - **ROI Tracker** (3-year projection + canvas line chart)
   - **Market Check** (competitors/demand form → profit calc)
   - **Report** (preview + hand-rolled PDF export, no library)
   - **AI Assistant** (rule-based chat, 5 suggestion chips + free-text intent)
   - **Get Loan** (Phase 3 placeholder card)

**Guards** in `js/app.js` redirect users when required `sessionStorage` state is missing.

---

## 4. CURRENT STATE (what it looks like right now)

### Cinematic intro (NEW, recently implemented)
`#intro.intro-overlay` on `index.html` has 3 `data-step` blocks:
1. `[data-step="title"]` — "Welcome to Sahiti" blurs in **letter-by-letter** (vanilla port
   of the React `motion`/`BlurText` component) centered full-screen with breathing room.
   Driven by `blurTitle()` in `initIntro()` (`js/app.js`).
2. It **holds**, then **fades out** (`title.classList.add('fade')`).
3. `[data-step="stage"]` — after the title fades, a hidden `.intro-stage` (grid + caption)
   fades in; the 3×3 grid cells **pop in one-by-one** (staggered), each a photo of an Indian
   place overlaid with the **native-script regional greeting** (Hindi नमस्ते, Marathi
   कसा काय, Gujarati કેમ છો, Punjabi ਸਤ ਸ੍ਰੀ ਅਕਾਲ, Tamil வணக்கம், Kannada ನಮಸ್ಕಾರ,
   Bengali নমস্কার, Ladakhi ཇུ་ལེ, and center "Jai Hind" over a Taj Mahal photo).
4. Caption fades in → overlay fades out → `body.intro-done` reveals the login page.

- **Images**: cell backgrounds come from remote Unsplash URLs keyed by `data-loc` in the
  `IMAGES` map in `initIntro()`. **Concern: if offline or URLs die, cells render blank.**
- **Note `DEBUG_REPORT.md` (older, points at `.intro-cell-logo` / `🕉️` center cell) is now
  OUTDATED** — the om/emblem center cell was replaced with a real photo. Do not trust it.

### Recent changes (all DONE and verified)
- Removed the Indian national emblem `<img>` from the top banner of ALL 4 pages.
- Removed the obsolete `.emblem` and `.intro-cell-logo` / `.cell-emblem` CSS.
- Banner branding centered (`justify-content: center` on `.banner-inner`).
- Replaced the center om (🕉️) grid cell with a Taj Mahal / "Jai Hind" photo cell.
- Greetings in the grid use native scripts (no romanization except Julley sub-label).

---

## 5. WHAT TO REVIEW / PRIORITISE NEXT (what I want you to do)

Ranked for a Manus agent. Verify each, then suggest / implement improvements and report back.

1. **Image reliability (most important)** — the intro grid + top banner use remote hotlinked
   images (Unsplash + a Wikimedia URL that is now removed). If the user demoes offline, the
   grid shows empty boxes. Recommend and implement a robust solution:
   - bundle local placeholder images under an `assets/` or `img/` folder, OR
   - add a graceful CSS-gradient fallback + `onerror` + preload before the grid pops, OR
   - both.
2. **Intro pacing / total length** — the full intro (blur title → hold → fade → 9 cell
   stagger → caption → reveal) currently runs ~7–8s before login appears. Confirm it feels
   right, and if too long, tighten timing constants in `initIntro()` (`HOLD`, `SHOW`, `GAP`,
   `gridStart`, the `+ 700 + 800` reveal offset).
3. **Reduced-motion** — verify `prefers-reduced-motion` fully skips the intro (JS removes
   `#intro`). Check no cell/caption stays stuck invisible in that path.
4. **A11y** — `#intro` has `aria-hidden="true"` while animating; cells get `role="img"` +
   `aria-label` at runtime. Confirm acceptable, or improve (focus management, `aria-live`).
5. **i18n integrity** — `js/i18n.js` was previously corrupted by an encoding bug
   (PowerShell `Get-Content -Raw` + `WriteAllText` lossy-decode turned Devanagari/virama
   into `�`, U+FFFD). It was fully rewritten clean. **Do NOT re-save via that PowerShell
   method.** If you edit i18n strings, use UTF-8-safe tooling and re-verify no `�` appears.
   Spot-check Hindi/Marathi/Gujarati/Telugu/Tamil render in a browser.
6. **Any other correctness/clarity** across login → OTP → onboarding → dashboard → AI.

---

## 6. HOW TO TEST (no framework)

- `node --check js/app.js` and `node --check js/i18n.js` (syntax).
- Open `index.html` in a browser (or headless Chrome via CDP). Existing headless scripts
  live in `C:\Users\dheeraj\AppData\Local\Temp\opencode\*_test.js`
  (e.g. `intro_test.js`, `chat_test.js`, `docs_test.js`, `otp_test.js`).
  - `ai_test.js` is OBSOLETE (seeds `userAadhar`, which no longer exists — ignore).
- Full manual flow: phone (10 digits) → OTP (6 digits) → onboarding → dashboard.

---

## 7. KNOWN SMALL ISSUES WORTH FIXING

- The AI assistant's `DOC_MAP`/doc-key lookup uses `businessId` values (`agriculture`,
  `microfinance`, `business`) but onboarding stores different `businessId`s
  (hardware, jewellery, pg, grocery, dairy, food, beauty, coaching) — so the AI "docs"
  reply may fall back to the default. Worth aligning, though not blocking.
- The intro reveal is slow (see #2).

---

## 8. DELIVERABLE

After your review, give me:
- a short bullet list of concrete changes you made (with file:line),
- anything you recommend but did NOT do (and why),
- confirmation that `index.html` → `otp.html` → `onboarding.html` → `dashboard.html` still
  works and renders all 6 languages correctly.

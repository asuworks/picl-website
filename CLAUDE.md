# PICL Website

Static presentation website for PICL — an AI-powered Android app that turns photos and voice memos into marketplace listings using Gemini AI.

**Developer:** Anton Suharev (suharev.works@gmail.com)
**Repo:** git@github.com:asuworks/picl-website.git (branch: master)
**Hosted:** https://asuworks.github.io/picl-website/
**Related project:** `../picl` (Android app), `../picl-privacy` (standalone privacy/terms pages)

## Files

| File | Purpose |
|---|---|
| `index.html` | Main landing page — all sections |
| `privacy.html` | Privacy policy (same nav/footer as index) |
| `terms.html` | Terms of service (same nav/footer as index) |
| `style.css` | Shared styles for all pages |
| `CLAUDE.md` | This file |

## Page Structure (index.html)

Sections appear in this order:
1. **Nav** — fixed top, frosted glass, hamburger on mobile
2. **Hero** — mascot image, acronym, h1, subtitle, Powered by Gemini, Play Store button
3. **Features** (`#features`) — 6 highlight cards in 3-col grid
4. **Setup** (`#setup`) — Gemini API key instructions
5. **How It Works** (`#how`) — 3-step pipeline + screenshot grid
6. **Export** (`#export`) — Google Drive export details, minimal permissions
7. **Support** (`#support`) — Ko-fi and PayPal links
8. **Footer** — brand, links, copyright

Nav link order matches section order: Features, Setup, How It Works, Export, Privacy, Terms, Support

## Design Principles

- **Minimalism, brevity, clarity** — Chekhov's rule: "brevity is the sister of talent"
- **Professional but friendly** tone — no slogans, no metaphors, functional naming
- **Sage color palette** — not vibrant green
- No frameworks — plain HTML/CSS/JS
- Font: Outfit (Google Fonts)

## Theming

- Dark/light mode via `data-theme` attribute on `<html>`
- Auto-detects OS preference via `prefers-color-scheme` media query
- Manual toggle persists to `localStorage('theme')`
- Inline script in `<head>` sets theme before paint (prevents flash)
- CSS variables handle all color switching — see `:root` and `[data-theme="dark"]` in style.css

### Key Colors

| Token | Light | Dark |
|---|---|---|
| `--bg` | `#FFFFFF` | `#1A1E1A` |
| `--text` | sage-900 | sage-200 |
| `--accent` | `#4B8E58` | `#71AF76` |
| `--card` | `#FFFFFF` | `#252A25` |
| `--border` | sage-200 | `#333A33` |

Dark mode has intentionally reduced contrast (not pure black/white).

Step number colors: `#5BAE6A` (green), `#E0A33E` (golden), `#5BB8CF` (sky blue).

## Screenshots

- Light theme: `assets/screenshots/light/1.jpg` through `8.jpg`
- Dark theme: `assets/screenshots/dark/1.jpg` through `8.jpg` (plus `4a.jpg`)
- Swapped via CSS only (no JS): `.screenshots-light` hidden in dark mode, `.screenshots-dark` hidden in light mode
- Images use `aspect-ratio: 9 / 19.5` to prevent layout shift from lazy loading
- Old unused screenshots exist in `assets/screenshots/` root (screenshot_0–9.jpg)

## Assets

- `assets/branding/pickle_camera.png` — mascot with camera (hero, OG image)
- `assets/branding/pickle_logo_small.png` — favicon and nav brand
- `assets/branding/pickle_logo.png` — full logo
- `assets/branding/pickle_logo_splash.png` — splash screen logo (used in picl-privacy)
- `assets/branding/pickle_wink.png` — winking mascot (unused on website)
- `assets/branding/ic_launcher_foreground.png` — launcher icon (unused on website)

## CSS Architecture

Style sections in order:
1. Reset + scroll-margin (`[id] { scroll-margin-top: 80px }` for fixed nav offset)
2. Tokens (sage palette, light/dark variables)
3. Base (body, links, images)
4. Nav (fixed, frosted glass, hamburger)
5. Hero
6. Pipeline (steps grid, step numbers)
7. Powered By
8. Play Store Button
9. Screenshots (flex-wrap centered, theme switching)
10. Highlights (feature cards grid)
11. Info Sections (setup, export — `.info-section`, `.info-section.alt`)
12. Support Links
13. Footer
14. Privacy page styles
15. Responsive (768px: hamburger + 2-col, 480px: 1-col)

## Nav Consistency

All three pages (index, privacy, terms) must have identical nav links and footer links. Privacy and terms prefix anchors with `index.html#` (e.g., `index.html#features`).

## SEO

- Each page has: title, description, keywords, author, robots, canonical URL
- index.html additionally has: Open Graph, Twitter Card, JSON-LD (`MobileApplication` schema)
- Canonical base URL: `https://asuworks.github.io/picl-website/`

## External Links

| Link | Used In |
|---|---|
| https://ko-fi.com/piclapp | Support section |
| https://paypal.me/piclapp | Support section |
| https://aistudio.google.com/apikey | Setup section |
| https://myaccount.google.com/permissions | Export section, privacy page |
| Google Play Store | Hero button (placeholder `href="#"` — needs real URL) |

## Things to Remember

- PICL stands for "Photos Into Selling Listings" (NOT Craigslist — changed deliberately)
- The mascot is called "Pickle" — a green felt-textured muppet with a camera
- The Play Store button href is still a placeholder (`#`) — update when published
- The app uses `drive.file` scope (most restrictive) — this is a key selling point
- No backend servers, no analytics, no tracking — emphasize this
- Feature names must be functional, not slogans (e.g., "Photo and voice capture" not "Point, don't type")
- Dark mode contrast is intentionally muted — don't make it too stark

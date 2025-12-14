# Copilot Instructions for Dr. Sayed Magdy Portfolio

## Architecture
Single-file SPA (1883 lines): All HTML, CSS, and JavaScript embedded in [index.html] with no external dependencies except Google Fonts. Zero build process—production-ready as-is.

## Project Structure
```
/
├── index.html              # Complete SPA with inline CSS & JS
├── assets/                 # Images
│   ├── dr_sayed_1.jpeg     # Professional photo (web-ready)
│   ├── dr_sayed_2.JPG      # Professional photo (note uppercase ext)
│   └── dr_sayed_3.HEIC     # Needs conversion to JPEG/WebP
└── dr_sayed_magdy_cv.pdf   # Downloadable CV
```

## Core Patterns

### CSS Architecture (lines 14-1156)
- **CSS Variables**: All theming through `--primary-color: #00a8cc`, `--text-dark`, etc. in `:root`
- **Dark Theme**: Override variables with `[data-theme="dark"]` selector—persisted via `localStorage.setItem('theme')`
- **RTL Support**: `[dir="rtl"]` selector flips layout for Arabic with `font-family: 'Cairo'`
- **Animation System**: `.fade-in` class + IntersectionObserver (lines 1776-1784) triggers visibility on scroll

### Bilingual System (data-* attributes)
Every text element has `data-en` and `data-ar` for English/Arabic. Toggle switches language (lines 1721-1747):
```javascript
html.setAttribute('lang', newLang);
html.setAttribute('dir', newLang === 'ar' ? 'rtl' : 'ltr');
updateLanguage(newLang); // Updates all [data-en][data-ar] elements
```
Persists via `localStorage.setItem('language', newLang)`. Initial state restored on page load (lines 1696-1707).

### Layout Components
- **Timeline Pattern**: Vertical centerline with alternating `.timeline-item` using `:nth-child(even)` for right-side positioning
- **Skill Bars**: Animated width on scroll using IntersectionObserver (lines 1786-1800) + `data-progress` attributes
- **Responsive Grids**: `grid-template-columns: repeat(auto-fit, minmax(300px, 1fr))` for cards/courses/projects

## Critical Features

### State Management (localStorage)
Three keys persist across sessions:
- `theme`: 'light' | 'dark'
- `language`: 'en' | 'ar'
- Restored on load before any user interaction (lines 1696-1707)

### Navigation Behavior
- **Smooth Scroll**: 80px offset for fixed navbar (lines 1822-1835)
- **Active Link**: Highlights based on `scrollY` vs section `.offsetTop` (lines 1838-1853)
- **Mobile Menu**: `.nav-links.active` toggle with hamburger (lines 1750-1759)

### Scroll Effects
- Navbar gains `.scrolled` class at `window.scrollY > 100` for backdrop filter
- Parallax hero: `translateY(${scrolled * 0.5}px)` (lines 1870-1878)
- Scroll-to-top button visible after 500px (lines 1802-1815)

## File References
- CV: `./dr_sayed_magdy_cv.pdf` (download attribute in line 1202)
- Images: `./assets/dr_sayed_1.jpeg`, `./assets/dr_sayed_2.JPG` (note uppercase), `dr_sayed_3.HEIC` ⚠️ needs JPEG conversion
- External: Google Fonts Poppins (English) + Cairo (Arabic) from CDN

## Local Development
```bash
python3 -m http.server 8000  # No build step—serves at http://localhost:8000
```
Direct file editing immediately reflected on refresh. No compilation, bundling, or transpilation.

## Modification Patterns
- **New Section**: Add `<section id="name">` + nav link with `href="#name"` for auto-scroll
- **Add Translation**: Both `data-en="Text"` and `data-ar="النص"` required on element for language toggle
- **Change Colors**: Modify CSS variables in `:root` (lines 15-27)—cascades to entire site
- **RTL Layout Fix**: Add specific rules under `[dir="rtl"]` selector (lines 75-93) for Arabic directional adjustments

## Design System
- **Colors**: Primary `#00a8cc` (teal-blue), Secondary `#0077b6`, Accent `#48cae4`—medical professional aesthetic
- **Typography**: Poppins (Latin), Cairo (Arabic)—loaded from Google Fonts
- **Animations**: `cubic-bezier(0.4, 0, 0.2, 1)` via `--transition` variable
- **Cards**: 15px `border-radius`, `--shadow` on hover with `transform: translateY(-10px)`
- **Spacing**: Container max-width `1200px` with `5rem` padding for sections

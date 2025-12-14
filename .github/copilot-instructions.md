# Copilot Instructions for Dr. Sayed Magdy Portfolio

## Project Overview
Personal portfolio website for Dr. Sayed Magdy, a medical professional. This is a static HTML/CSS/JS website showcasing professional credentials, experience, and contact information.

## Project Structure
```
/
├── index.html              # Main landing page (currently empty)
├── assets/                 # Images and media
│   ├── dr_sayed_1.jpeg     # Professional photo option 1
│   ├── dr_sayed_2.JPG      # Professional photo option 2
│   └── dr_sayed_3.HEIC     # Professional photo option 3 (needs conversion)
└── dr_sayed_magdy_cv.pdf   # CV document for download
```

## Development Guidelines

### HTML Structure
- Use semantic HTML5 elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`)
- Keep the single-page layout structure with anchor navigation for sections
- Ensure mobile-responsive meta tags are included
- Reference assets using relative paths: `./assets/` and `./dr_sayed_magdy_cv.pdf`

### Styling Approach
- Prefer modern CSS (Flexbox/Grid) for layouts
- Use CSS custom properties for theming (colors, fonts, spacing)
- Mobile-first responsive design with media queries
- Consider a professional medical/academic aesthetic (clean, trustworthy, professional)

### Asset Handling
- HEIC images need conversion to web-compatible formats (JPEG/WebP)
- Optimize images for web (compress, appropriate dimensions)
- Provide download link for CV PDF
- Use appropriate image formats: JPEG for photos, SVG for icons

### Typical Sections for Medical Portfolio
- Hero/Header: Name, title, professional photo
- About: Brief professional bio and specialization
- Education & Credentials
- Professional Experience
- Skills/Expertise
- Publications/Research (if applicable)
- Contact Information
- CV Download link

### No Build Process
This is a static website with no build tooling. All files should be production-ready and can be directly served by any web server or hosting platform (GitHub Pages, Netlify, etc.).

### Accessibility
- Include alt text for all images
- Use proper heading hierarchy (h1 → h2 → h3)
- Ensure sufficient color contrast
- Make interactive elements keyboard-accessible

## Quick Start Commands
```bash
# Serve locally for development (Python 3)
python3 -m http.server 8000

# Or with Node.js
npx serve .
```

## Key Decisions
- **Static HTML**: No frameworks needed for this simple portfolio - keeps it lightweight and universally compatible
- **Single Page**: All content on index.html with smooth scrolling navigation
- **Professional Tone**: Medical professional portfolio requires clean, trustworthy design

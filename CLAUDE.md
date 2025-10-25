# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an **Academic Project Page Template** - a static website for showcasing research papers. The current instance is configured for a paper under double-blind review (anonymized).

**Tech Stack**: HTML5, CSS3 (Bulma framework), JavaScript (jQuery + vanilla), GitHub Pages compatible

## Development Commands

Since this is a static HTML website, there are no build commands. Development workflow:

- **Local testing**: Open `index.html` directly in a browser, or use a local server:
  ```bash
  python -m http.server 8000
  ```
  Then visit http://localhost:8000

- **Check git status**: `git status`
- **Deploy**: Push to GitHub Pages (configured via `.nojekyll` file)

## Project Architecture

### File Structure

```
index.html              # Main entry point - all content and structure
static/
├── css/
│   ├── bulma.min.css   # Bulma CSS framework v0.9.1
│   └── index.css       # Custom styling (753 lines, CSS variables)
├── js/
│   ├── index.js        # Custom functionality (dropdown, copy, scroll, video)
│   ├── bulma-carousel.js
│   └── bulma-slider.js
├── images/             # Static images (favicon, teaser, carousel items)
└── videos/             # Video files (banner, carousel videos)
```

### Key Files

**[index.html](index.html)** - Single-page website with:
- Lines 4-72: SEO meta tags, Open Graph tags, Google Fonts
- Lines 82-101: Hero section (title, authors, publication venue)
- Lines 117-144: Abstract section
- Lines 148-167: Commented template sections (image/video carousels, PDF viewer, BibTeX)
- Lines 170-196: Footer with attribution

**[static/css/index.css](static/css/index.css)** - Custom styling:
- Lines 1-50: CSS Variables (colors, shadows, spacing, transitions)
- Lines 52-400: Component styles (buttons, hero, publications, carousels)
- Lines 401-600: Interactive elements (dropdown, scroll-to-top)
- Lines 601-753: Responsive breakpoints (480px, 768px, 1024px)

**[static/js/index.js](static/js/index.js)** - Interactive features:
- Lines 4-37: `toggleMoreWorks()` - dropdown menu management
- Lines 39-73: `copyBibTeX()` - clipboard functionality with fallback
- Lines 75-91: `scrollToTop()` - scroll utilities
- Lines 93-120: `setupVideoCarouselAutoplay()` - IntersectionObserver for video autoplay
- Lines 122-142: jQuery initialization for carousels and sliders

### Design System

The project uses **CSS Variables** for theming (defined at top of [static/css/index.css](static/css/index.css)):
- Primary color: `#2563eb` (blue)
- Secondary color: `#64748b` (gray)
- Shadow system: `--shadow-sm`, `--shadow-md`, `--shadow-lg`, `--shadow-xl`
- Border radius: `--radius-md` (12px), `--radius-lg` (16px)
- Transitions: Cubic-bezier easing for smooth animations

## Content Customization

The template uses HTML comments to mark customization points:

1. **Meta tags** (lines 10-56): Update title, description, keywords, social preview image
2. **Hero section** (lines 82-101): Paper title, authors, institution, conference
3. **Abstract** (lines 117-144): Paper description
4. **Media sections** (lines 148-167): Uncomment and configure:
   - Image carousels (class `results-carousel`)
   - Video embeds (YouTube iframes)
   - Video carousels (class `hero-body`)
   - PDF poster viewer
   - BibTeX citations (class `card`)

## Important Notes

- **Anonymization**: Current instance removes author information for double-blind review
- **Favicon**: Replace `static/images/favicon.ico` with your own
- **Social preview**: Create 1200x630px image at `static/images/social_preview.png`
- **Large videos**: Use YouTube embedding (>10MB) instead of local files
- **Image optimization**: Compress images with TinyPNG before adding

## Component Interactions

**Bulma Carousel** initialization in [static/js/index.js](static/js/index.js#L122-L142):
```javascript
bulmaCarousel.attach('.results-carousel', {
  slidesToScroll: 1,
  slidesToShow: 1,
  loop: true,
  autoplay: true,
  autoplaySpeed: 5000
});
```

**Video Autoplay** uses IntersectionObserver (lines 93-120) to play videos when 50% visible, pause when out of view.

**More Works Dropdown** (lines 4-37) closes on outside click or Escape key for accessibility.

## Responsive Design

Mobile breakpoints in [static/css/index.css](static/css/index.css):
- `480px`: Small phones (adjust button sizes, hide elements)
- `768px`: Tablets (adjust layouts, dropdown positioning)
- `1024px`: Desktop (full feature set)

## License

Website licensed under Creative Commons Attribution-ShareAlike 4.0 International License.

# CLAUDE.md - AI Assistant Guide for salinsde.github.io

**Last Updated:** 2025-12-28
**Repository:** Personal Portfolio Website (GitHub Pages)
**Owner:** Denis Salins
**Domain:** salinsde.github.io

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Development Workflow](#development-workflow)
4. [File Organization](#file-organization)
5. [HTML Architecture](#html-architecture)
6. [CSS Architecture & Theming](#css-architecture--theming)
7. [JavaScript Architecture](#javascript-architecture)
8. [Common Tasks](#common-tasks)
9. [Key Conventions](#key-conventions)
10. [Git Workflow](#git-workflow)
11. [Deployment](#deployment)

---

## Project Overview

### What This Is

A **static personal portfolio website** built on the "Waxon" template by Marketify. Features:

- Single-page layout with smooth anchor navigation
- 8 hero animation variants (slider, glitch, ken burns, particle effects, etc.)
- Dark mode and RTL (right-to-left) language support
- Portfolio filtering with Isotope
- AJAX contact form with PHP backend
- Custom cursor and parallax effects
- Fully responsive design

### Technology Stack

- **Frontend:** HTML5, CSS3, JavaScript (jQuery-based)
- **Backend:** PHP (contact form only)
- **Libraries:** jQuery, Swiper, Isotope, Owl Carousel, WOW.js, Magnific Popup, Vegas, SimpleParallax, Jarallax
- **Deployment:** GitHub Pages
- **No Build Process:** Manually managed assets (no npm, webpack, gulp)

### Key Statistics

- **Total Size:** ~5.2 MB
- **HTML Files:** 19 page variants
- **JavaScript:** 561 KB (5 files)
- **CSS:** 479 KB (6 files)
- **Images:** 4.2 MB (56 files + 50+ SVG icons)

---

## Repository Structure

```
salinsde.github.io/
├── css/
│   ├── plugins.css         # Third-party plugin styles (5,369 lines)
│   ├── mycss.css           # Main custom styles (2,516 lines)
│   ├── mycolors.css        # Color theming system (13 schemes)
│   ├── darkMode.css        # Dark mode overrides
│   ├── rtl.css             # Right-to-left support
│   └── font/               # xcon custom icon font (5 formats)
│
├── js/
│   ├── plugins.js          # Compiled third-party libraries (439 KB)
│   ├── customcode.js       # Application logic (561 lines)
│   ├── jquery.js           # jQuery library
│   ├── modernizr.custom.js # Feature detection
│   └── ie8.js              # IE8 compatibility stub
│
├── img/
│   ├── about/              # Profile/about section images
│   ├── logo/               # Branding (light/dark variants)
│   ├── portfolio/          # Project showcase images
│   ├── news/               # Blog post images
│   ├── partners/           # Client logos (with light/ subdirectory)
│   ├── slider/             # Hero carousel images
│   ├── resume/             # CV PDF documents
│   └── svg/                # Icon library (50+ icons)
│       └── social/         # Social media icons (6 files)
│
├── modal/
│   └── contact.php         # Contact form backend
│
├── index.html              # Default homepage
├── index-dark.html         # Dark theme variant
├── index-glitch.html       # Glitch effect hero
├── index-kenburn.html      # Ken Burns animation
├── index-particle.html     # Particle effect hero
├── index-slider.html       # Hero carousel
├── index-rtl.html          # RTL layout
├── index-no-animation.html # Minimal animation
├── portfolio*.html         # Portfolio pages (3 variants)
├── portfolio-single*.html  # Project detail pages (3 variants)
└── news-single*.html       # Blog post pages (3 variants)
```

---

## Development Workflow

### No Build System

This project uses **no build tools** (npm, webpack, gulp). All files are:

- Manually edited
- Pre-compiled/minified (plugins.js, plugins.css)
- Directly committed to Git
- Deployed via Git push to GitHub Pages

### Making Changes

1. **Edit HTML directly** in root directory files
2. **Modify CSS** in `/css/mycss.css` for custom styles
3. **Update JavaScript** in `/js/customcode.js` for behavior changes
4. **Replace images** in appropriate `/img/` subdirectories
5. **Test locally** by opening HTML files in browser
6. **Commit and push** changes to deploy

### Local Development

```bash
# No installation required - just open files
open index.html  # macOS
xdg-open index.html  # Linux
start index.html  # Windows

# For PHP contact form testing, run local server:
php -S localhost:8000
```

---

## File Organization

### Naming Conventions

#### HTML Files
- `index.html` - Default/base version
- `index-{variant}.html` - Theme/animation variants
- `{page}.html` - Light theme page
- `{page}-dark.html` - Dark theme variant
- `{page}-rtl.html` - RTL variant

#### CSS Classes
```css
.waxon_tm_{component}              /* Main container */
.waxon_tm_{component} .{subpart}   /* Nested element */
.waxon_tm_{component}.{state}      /* State modifier */
.fn_cs_{functional_name}           /* Functional components */
```

#### JavaScript Functions
```javascript
waxon_tm_{feature}()               // Core initialization
{brand}_tm_{feature}()             // Helper functions
```

#### Images
- Numbered: `1.jpg`, `2.jpg`, `3.jpg`
- Sized: `100x100.jpg`, `500x500.jpg`, `1200x1200.jpg`
- Themed: `logo.png` (light), `dark.png` (dark)
- Descriptive: `hero-rtl.jpg`, `dot.png`, `dot-dark.png`

---

## HTML Architecture

### Page Template Structure

All pages follow this consistent structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Meta tags -->
  <!-- Google Fonts: Mulish, Poppins, Montserrat -->
  <!-- CSS: plugins.css, mycolors.css, darkMode.css, rtl.css, mycss.css -->
</head>
<body> <!-- Add class="dark" for dark mode, class="rtl" for RTL -->

  <!-- PRELOADER -->
  <div class="waxon_tm_preloader">...</div>

  <!-- WRAPPER -->
  <div class="waxon_tm_all_wrap" data-magic-cursor="" data-color="">

    <!-- TOPBAR -->
    <div class="waxon_tm_topbar">
      <div class="logo">...</div>
      <div class="menu">
        <ul class="anchor_nav">
          <li><a href="#home">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#portfolio">Projects</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </div>
    </div>

    <!-- MOBILE MENU -->
    <div class="waxon_tm_mobile_menu">...</div>

    <!-- HERO SECTION -->
    <div class="waxon_tm_hero" id="home">...</div>

    <!-- ABOUT SECTION -->
    <div class="waxon_tm_about" id="about">...</div>

    <!-- SERVICES SECTION -->
    <div class="waxon_tm_services">...</div>

    <!-- PORTFOLIO SECTION -->
    <div class="waxon_tm_portfolio" id="portfolio">...</div>

    <!-- CONTACT SECTION -->
    <div class="waxon_tm_contact" id="contact">...</div>

    <!-- COPYRIGHT -->
    <div class="waxon_tm_copyright">...</div>

    <!-- CURSOR -->
    <div class="mouse-cursor cursor-outer">...</div>
    <div class="mouse-cursor cursor-inner">...</div>

  </div>

  <!-- SCRIPTS -->
  <script src="js/jquery.js"></script>
  <script src="js/plugins.js"></script>
  <script src="js/customcode.js"></script>
</body>
</html>
```

### Key Data Attributes

```html
<!-- Wrapper configuration -->
<div class="waxon_tm_all_wrap"
     data-magic-cursor=""          <!-- "" = show, "hide" = hide -->
     data-color="blue">             <!-- Color theme selector -->

<!-- WOW.js animations -->
<div data-wow-duration="0.8s"
     data-wow-delay="0.2s">

<!-- Background image loader -->
<div data-img-url="img/about/1.jpg">

<!-- Portfolio filtering -->
<li data-filter=".branding">

<!-- Parallax effects -->
<img data-speed="0.5" class="jarallax-img">
```

### HTML Variants Differences

| File | Body Class | Hero Type | Key Features |
|------|------------|-----------|--------------|
| `index.html` | (none) | Static image | Default light theme |
| `index-dark.html` | `dark` | Static image | Dark color scheme |
| `index-glitch.html` | (none) | Glitch effect | CSS glitch animation |
| `index-kenburn.html` | (none) | Ken Burns | Vegas zoom animation |
| `index-particle.html` | (none) | Particles | Particle.js effect |
| `index-slider.html` | (none) | Swiper carousel | Multiple images |
| `index-rtl.html` | `rtl` | Static image | Right-to-left layout |
| `index-no-animation.html` | (none) | Static image | Minimal animations |

---

## CSS Architecture & Theming

### CSS Loading Order (Critical!)

```html
<!-- ALWAYS load in this order: -->
<link rel="stylesheet" href="css/plugins.css" />    <!-- 1. Framework/plugins -->
<link rel="stylesheet" href="css/mycolors.css" />   <!-- 2. Color themes -->
<link rel="stylesheet" href="css/darkMode.css" />   <!-- 3. Dark mode -->
<link rel="stylesheet" href="css/rtl.css" />        <!-- 4. RTL support -->
<link rel="stylesheet" href="css/mycss.css" />      <!-- 5. Custom styles -->
```

### CSS File Structure

#### mycss.css - Numbered Sections
```
01) WAXON BASE           - Resets, body, typography
02) WAXON TOPBAR         - Navigation bar
03) WAXON MOBILE MENU    - Hamburger menu
04) WAXON HERO           - Hero/banner section
05) WAXON ABOUT          - About section
06) WAXON SERVICES       - Services carousel
07) WAXON PORTFOLIO      - Portfolio grid/filtering
08) WAXON PARTNERS       - Partner logos
09) WAXON TESTIMONIALS   - Client testimonials
10) WAXON NEWS           - Blog/news section
11) WAXON CONTACT        - Contact form
12) WAXON COPYRIGHT      - Footer
13) WAXON CURSOR         - Custom cursor
14) WAXON MEDIA QUERIES  - Responsive breakpoints
```

### Color Theming System

13 color schemes available via `data-color` attribute:

```html
<div class="waxon_tm_all_wrap" data-color="blue|green|brown|pink|orange|black|white|purple|sky|cadetBlue|crimson|olive|red">
```

**Implementation in mycolors.css:**
```css
.waxon_tm_all_wrap[data-color="blue"] .element {
  color: #4169e1; /* Affects headings, buttons, hover, cursor, SVG, links */
}
```

### Dark Mode

Applied via body class:

```html
<body class="dark">
```

**Features:**
- Background color inversions
- Text color adjustments
- Image display toggles (`.light` vs `.dark` images)
- Form placeholder color updates
- Logo swapping

### RTL Support

Applied via body class:

```html
<body class="rtl">
```

**Features:**
- `direction: rtl` CSS property
- Flipped margins and padding
- Mirrored float directions
- Text alignment reversals

### Responsive Breakpoints

Common breakpoints in media queries:
- Mobile: 480px
- Tablet: 768px
- Desktop: 1040px, 1200px, 1600px
- Large: 1920px

---

## JavaScript Architecture

### Loading Order (Critical!)

```html
<!-- ALWAYS load in this order: -->
<script src="js/jquery.js"></script>        <!-- 1. jQuery core -->
<script src="js/plugins.js"></script>       <!-- 2. Third-party plugins -->
<script src="js/customcode.js"></script>    <!-- 3. Application logic -->
```

### plugins.js - Third-Party Libraries

Contains pre-compiled versions of:

- **jQuery** - DOM manipulation
- **WOW.js** - Scroll animations
- **Swiper** - Touch sliders
- **Vegas** - Ken Burns backgrounds
- **Owl Carousel** - Service carousels
- **Isotope** - Portfolio filtering/masonry
- **Magnific Popup** - Lightboxes
- **SimpleParallax** - Image parallax
- **Jarallax** - Background parallax
- **One Page Nav** - Anchor navigation
- **Hamburger** - Mobile menu icon
- **mgGlitch** - Glitch effects
- **Google Maps API** - Contact maps

### customcode.js - Application Logic

All initialization happens in `jQuery(document).ready()`:

#### Core Functions (in order):

```javascript
// 1. Image Animations
waxon_tm_about_animations()      // 4 parallax image types

// 2. Hero Sliders
waxon_tm_hero_slider()           // Swiper carousel
waxon_tm_kenburn_slider()        // Vegas zoom animation

// 3. Navigation
jQuery('.anchor_nav').onePageNav() // Smooth scrolling
waxon_tm_filter_opener()         // Portfolio filter toggle
waxon_tm_nav_bg()                // Navbar scroll effects

// 4. Interactions
waxon_tm_testimonials_effect()   // Hover testimonial swap
waxon_tm_jarallax()              // Parallax setup
edrea_tm_hamburger()             // Mobile menu toggle
waxon_tm_cursor()                // Custom cursor tracking

// 5. Carousels
waxon_tm_partners()              // Owl carousel services

// 6. Utilities
waxon_tm_imgtosvg()              // IMG to inline SVG conversion
waxon_tm_data_images()           // Background image loader

// 7. Popups & Forms
waxon_tm_popup()                 // Magnific popup setup
waxon_tm_contact_form()          // AJAX form submission

// 8. Portfolio
waxon_tm_portfolio()             // Isotope filtering

// 9. Effects
$(".glitch").mgGlitch()          // Glitch effect config

// 10. Loading
waxon_tm_myload()                // Staggered load animations
waxon_tm_isotope()               // Masonry layout recalc
```

### Contact Form Implementation

**Frontend (customcode.js):**
```javascript
function waxon_tm_contact_form() {
  $(".contact_form #send_message").on('click', function() {
    var name    = $('.contact_form #name').val();
    var email   = $('.contact_form #email').val();
    var message = $('.contact_form #message').val();

    $.ajax({
      type: "POST",
      url: "modal/contact.php",
      data: {
        ajax_name: name,
        ajax_email: email,
        ajax_message: message
      },
      success: function(response) {
        // Handle success/error messages
        // Reset form on success
      }
    });
  });
}
```

**Backend (modal/contact.php):**
- **Recipient:** `salins.denis@gmail.com` (line 4)
- **Validation:** `filter_var($php_email, FILTER_VALIDATE_EMAIL)`
- **Sanitization:** `FILTER_SANITIZE_EMAIL`
- **Email Format:** HTML with MIME headers
- **CC:** Sends copy to sender

---

## Common Tasks

### Adding a New Portfolio Item

1. **Add image** to `/img/portfolio/`
2. **Edit HTML** in portfolio section:
   ```html
   <li class="category-name">
     <div class="inner">
       <div class="entry waxon_tm_portfolio_animation_wrap" data-title="Project Name" data-category="Category">
         <a href="portfolio-single.html">
           <img src="img/portfolio/your-image.jpg" alt="" />
         </a>
       </div>
     </div>
   </li>
   ```
3. **Create detail page** (copy `portfolio-single.html`)
4. **Repeat for dark/RTL variants** if needed

### Changing Color Theme

**Option 1: JavaScript (Dynamic)**
```javascript
jQuery('.waxon_tm_all_wrap').attr('data-color', 'purple');
```

**Option 2: HTML (Static)**
```html
<div class="waxon_tm_all_wrap" data-color="purple">
```

Available colors: `blue`, `green`, `brown`, `pink`, `orange`, `black`, `white`, `purple`, `sky`, `cadetBlue`, `crimson`, `olive`, `red`

### Updating Contact Email

Edit `/modal/contact.php` line 4:
```php
$php_main_email = "your-email@example.com";
```

### Adding New Pages

1. **Copy existing page** (e.g., `index.html`)
2. **Update title** in `<head>`
3. **Modify content** in sections
4. **Update navigation** links if needed
5. **Create dark/RTL variants** if supporting those themes

### Customizing Animations

**WOW.js scroll animations:**
```html
<div class="wow fadeInUp" data-wow-duration="0.8s" data-wow-delay="0.2s">
  Content here
</div>
```

**Parallax images:**
```html
<img src="img/about/1.jpg" alt="" class="thumbnail" data-speed="0.5" />
```

Thumbnail classes: `thumbnail`, `thumbnail-2`, `thumbnail-3`, `thumbnail-4`

### Modifying Hero Section

**For static hero:**
```html
<div class="waxon_tm_hero" id="home" data-img-url="img/slider/1.jpg">
```

**For slider hero:**
```html
<div class="fn_cs_swiper">
  <div class="swiper-wrapper">
    <div class="swiper-slide" data-img-url="img/slider/1.jpg"></div>
    <div class="swiper-slide" data-img-url="img/slider/2.jpg"></div>
  </div>
</div>
```

---

## Key Conventions

### For AI Assistants

#### Critical Rules

1. **Never modify plugins.js or plugins.css** - These are pre-compiled libraries
2. **Maintain CSS loading order** - plugins → mycolors → darkMode → rtl → mycss
3. **Maintain JS loading order** - jquery → plugins → customcode
4. **Keep naming conventions** - Use `waxon_tm_` prefix for all custom functions/classes
5. **Update all variants** - When changing index.html, consider updating dark/RTL/other variants
6. **Test responsive design** - Changes should work across all breakpoints
7. **Preserve data attributes** - WOW.js, parallax, and filtering rely on these

#### When Editing HTML

- Always maintain the section structure (topbar → mobile menu → hero → about → services → portfolio → contact → copyright)
- Preserve class names exactly (template relies on specific selectors)
- Keep anchor navigation IDs: `#home`, `#about`, `#portfolio`, `#contact`
- Don't remove `data-img-url` attributes (used for background loading)
- Maintain WOW.js attributes for animations

#### When Editing CSS

- Add custom styles to **mycss.css** only
- Follow numbered section comments
- Use `.waxon_tm_` prefix for new components
- Don't override plugin styles directly
- Consider dark mode and RTL implications

#### When Editing JavaScript

- Add custom code to **customcode.js** only
- Initialize in `jQuery(document).ready()`
- Use `waxon_tm_` function prefix
- Don't modify plugin initialization in plugins.js
- Test AJAX form functionality after changes

#### Image Guidelines

- **Portfolio images:** 1200x1200px recommended
- **Hero images:** 1920x1080px recommended
- **Logo:** Provide both light and dark versions
- **Format:** JPG for photos, PNG for logos, SVG for icons
- **Optimization:** Compress images before adding (target <200KB per image)

#### Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- IE9+ (with conditional comments in place)
- Mobile Safari and Chrome
- Test custom cursor on mobile (should hide automatically)

---

## Git Workflow

### Branch Strategy

- **Main branch:** Direct commits for simple changes
- **Feature branches:** Use `claude/{description}-{sessionId}` format for AI-assisted work
- **No pull requests:** Direct push to GitHub Pages deployment

### Commit Messages

Recent patterns observed:
```
"Updating Index to hide TBD items"
"Update time content"
"Content Update"
"Updating index content and links"
"Updating Logo"
"Update Map Coordinates"
"Update images and resume"
```

**Convention:**
- Use present tense: "Update" not "Updated"
- Be descriptive but concise
- Capitalize first word
- No period at end

### Common Git Commands

```bash
# Check status
git status

# Add and commit changes
git add .
git commit -m "Update portfolio section"

# Push to GitHub Pages
git push origin main

# View recent commits
git log --oneline -10

# Create feature branch
git checkout -b claude/feature-name-abc123
```

---

## Deployment

### GitHub Pages

- **Auto-deployment:** Every push to main branch
- **URL:** https://salinsde.github.io
- **DNS:** Served directly from GitHub
- **Build:** None required (static files)

### Deployment Checklist

Before pushing changes:

- [ ] Test HTML files locally in browser
- [ ] Verify contact form (if PHP backend available)
- [ ] Check responsive design (mobile, tablet, desktop)
- [ ] Test dark mode variant (if modified)
- [ ] Test RTL variant (if modified)
- [ ] Validate all links work
- [ ] Check console for JavaScript errors
- [ ] Verify image paths are correct
- [ ] Test portfolio filtering
- [ ] Test smooth scroll navigation
- [ ] Confirm custom cursor works
- [ ] Check all animations fire correctly

### Performance Considerations

**Current load times:**
- Total page size: ~5.2 MB
- Largest asset: `plugins.js` (439 KB)
- Images: 4.2 MB (largest opportunity for optimization)

**Optimization opportunities:**
1. Compress images (use tools like TinyPNG, ImageOptim)
2. Lazy load below-fold images
3. Consider WebP format for modern browsers
4. Minify customcode.js (currently unminified)
5. Enable GZIP compression via GitHub Pages

---

## File Editing Quick Reference

### Most Commonly Edited Files

| File | Purpose | When to Edit |
|------|---------|--------------|
| `index.html` | Main homepage | Content updates, layout changes |
| `css/mycss.css` | Custom styles | Styling adjustments |
| `js/customcode.js` | Behavior | Adding/modifying interactions |
| `img/resume/*.pdf` | Resume/CV | Update professional documents |
| `modal/contact.php` | Email backend | Change recipient email |

### Files to NEVER Edit

| File | Reason |
|------|--------|
| `js/plugins.js` | Pre-compiled libraries - updates break functionality |
| `css/plugins.css` | Framework styles - custom edits will be lost |
| `js/jquery.js` | Core library - use official versions only |

### Safe to Delete

| Item | Impact |
|------|--------|
| `index-{variant}.html` | Only affects that specific variant |
| Unused images in `/img/` | No impact if not referenced in HTML |
| `.DS_Store` | macOS metadata, not needed |

---

## Troubleshooting

### Common Issues

**Portfolio filtering not working:**
- Check Isotope initialization in customcode.js
- Verify `data-filter` attributes match CSS classes
- Ensure plugins.js loaded before customcode.js

**Contact form not submitting:**
- Check PHP server is running (GitHub Pages doesn't support PHP)
- Verify email address in `modal/contact.php` line 4
- Check browser console for AJAX errors
- Ensure form fields have correct IDs: `#name`, `#email`, `#message`

**Animations not firing:**
- Verify WOW.js loaded in plugins.js
- Check `data-wow-duration` and `data-wow-delay` attributes present
- Ensure elements have `wow` class: `class="wow fadeInUp"`

**Images not displaying:**
- Check file paths are correct (case-sensitive on servers)
- Verify `data-img-url` attribute format
- Ensure images exist in `/img/` directory

**Custom cursor not showing:**
- Check `data-magic-cursor=""` on wrapper (not `"hide"`)
- Verify cursor elements exist at end of HTML
- Check browser console for JavaScript errors

**Dark mode not working:**
- Ensure `<body class="dark">` is set
- Verify darkMode.css loaded after mycolors.css
- Check if dark logo image exists (`img/logo/dark.png`)

---

## Additional Resources

### Template Documentation
- Original template: Waxon by Marketify
- Template uses standard web technologies (no proprietary frameworks)

### Libraries Documentation
- [jQuery](https://api.jquery.com/)
- [Swiper](https://swiperjs.com/get-started)
- [Isotope](https://isotope.metafizzy.co/)
- [WOW.js](https://wowjs.uk/docs.html)
- [Owl Carousel](https://owlcarousel2.github.io/OwlCarousel2/)
- [Magnific Popup](https://dimsemenov.com/plugins/magnific-popup/)

### Testing Tools
- **Validators:** W3C HTML Validator, CSS Validator
- **Performance:** Google PageSpeed Insights, GTmetrix
- **Responsive:** Chrome DevTools, BrowserStack
- **Accessibility:** WAVE, axe DevTools

---

## Contact Information

**Site Owner:** Denis Salins
**Email:** salins.denis@gmail.com
**Repository:** https://github.com/salinsde/salinsde.github.io
**Live Site:** https://salinsde.github.io

---

## Version History

| Date | Version | Changes |
|------|---------|---------|
| 2025-12-28 | 1.0 | Initial CLAUDE.md documentation created |

---

**Note for AI Assistants:** This documentation is maintained to help you understand the codebase structure and conventions. When making changes, always consider:
- Impact on all HTML variants (light/dark/RTL)
- Responsive design implications
- Browser compatibility
- Existing naming conventions
- Git commit message patterns

Always test changes locally when possible before committing to the repository.

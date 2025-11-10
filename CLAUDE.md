# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a modern, responsive personal portfolio website for Wayne Correa, a Cloud Infrastructure Product Leader. The site is built with vanilla HTML, CSS, and JavaScript—no frameworks or build tools required.

**Key stats:**
- 28+ years in product management
- $134M in combined revenue delivered
- Expertise: Cloud infrastructure, product strategy, enterprise leadership

## Technology Stack

- **HTML**: Semantic markup with Meta tags for SEO
- **CSS**: Custom CSS with CSS variables for theming, flexbox/grid layouts
- **JavaScript**: Vanilla JS (no frameworks) for interactivity
- **External**: Google Fonts (Inter, Outfit), Formspree for contact form backend
- **Hosting**: Static site suitable for any web host or CDN

## Architecture & Key Components

### Page Structure
The site uses a single-page application (SPA) design with smooth scrolling:
1. **Navigation (sticky navbar)** - Links to all sections with active state highlighting
2. **Hero Section** - Eye-catching intro with stats cards and CTAs
3. **About** - Personal introduction with sticky highlight box
4. **Achievements** - 6 achievement cards in responsive grid
5. **Expertise** - 4 categories of skills with checkmark styling
6. **Experience** - Timeline layout (alternating left/right on desktop)
7. **Contact** - Gradient background with contact info + contact form
8. **Footer** - Simple footer with copyright

### Key JavaScript Behaviors
- **Smooth scrolling** - Anchor links scroll smoothly to sections
- **Scroll animations** - Elements fade in as they enter viewport (IntersectionObserver)
- **Active nav highlighting** - Highlights current section in navigation based on scroll position
- **Stats counter animation** - Numbers animate upward when hero section is visible
- **Parallax effect** - Subtle parallax on gradient circle in hero
- **Navbar scroll effect** - Shadow changes on scroll
- **Contact form** - Uses Formspree API (myzopbzd) to send emails to waynejcorrea@gmail.com

### CSS Design System
- **Color scheme**: Primary blue (#0066ff), secondary orange (#ff6b35), light gray backgrounds
- **Gradients**: Two main gradients (blue and orange) used throughout
- **Typography**: Inter (body), Outfit (headings) from Google Fonts
- **Shadows**: Three levels (sm, md, lg) for depth
- **Spacing**: Consistent 80px section padding, responsive gaps
- **Responsive breakpoints**: 768px (tablet), 480px (mobile)

## Customization for Job Opportunities

This portfolio is designed to be rapidly customized for different job opportunities using your resume files in the Job-Search directory. Here's the workflow:

### Typical Customization Flow
1. **Select relevant resume** from `/home/wayne/AI-Projects/Job-Search/`
2. **Extract key achievements** from the target role's resume version
3. **Update the portfolio** with role-specific content (see quick edits below)
4. **Test responsively** and verify all links work
5. **Deploy** to relevant portfolio URL/domain

### Quick Edits for Different Roles

**For Product Manager roles:**
- Update hero subtitle (index.html:33) to emphasize product strategy focus
- Reorder achievement cards (index.html:83-118) to highlight product launches first
- Adjust expertise section (index.html:128-167) to emphasize "Product & Strategy"

**For Leadership/Sales roles:**
- Emphasize revenue delivery in hero stats (index.html:35-46)
- Move "Enterprise Sales Excellence" achievement card to top
- Highlight "Leadership & Sales" expertise category

**For Cloud/Infrastructure roles:**
- Focus hero on technical infrastructure achievements
- Lead with "Cloud & Infrastructure" expertise category (index.html:128-137)
- Highlight Equinix and IBM Direct Link experiences in timeline

### Content Mapping from Resumes
- **Hero stats** (index.html:35-46): Pull 3 strongest metrics from resume
- **Achievement cards** (index.html:83-118): 6 best examples from your experience, ordered by relevance to role
- **Expertise sections** (index.html:128-167): Match 4 categories to job description keywords
- **Timeline** (index.html:177-237): Keep all entries, let achievement cards emphasize relevance

## Common Development Tasks

### Adding New Content
1. **Update hero subtitle**: Edit text in `index.html:33` - this is the first impression
2. **Update hero stats**: Edit the `.stat-card` elements in `index.html:35-46` - pull from resume metrics
3. **Reorder achievement cards**: Move `.achievement-card` divs in `index.html:83-118` - put most relevant first
4. **Update expertise category order**: Reorder `.expertise-category` divs in `index.html:128-167` - emphasize job-relevant skills
5. **Add timeline item**: Insert new `.timeline-item` in `index.html:177-237`

### Styling Changes
- Update CSS variables in `:root` (styles.css:5-18) to change colors globally
- Mobile-first responsive design: start with mobile styles, use media queries for larger screens
- Key breakpoints are 768px and 480px (see styles.css:724-819)

### Contact Form
- Currently sends to Formspree endpoint `https://formspree.io/f/myzopbzd` (script.js:68)
- To change recipient email: create new Formspree form at formspree.io, update endpoint in script.js
- Form validation is handled by HTML5 `required` attributes

### Testing & Validation
- Open `index.html` directly in browser to test (no build step needed)
- Check responsive design using browser DevTools (F12, toggle device toolbar)
- Verify form submission works with Formspree
- Test smooth scrolling and animations in all modern browsers

## Quick Reference: Edit Locations

Quick lookup for the most common edits when customizing for different roles:

| Content | File | Lines | Notes |
|---------|------|-------|-------|
| Hero subtitle (first impression) | index.html | 33 | Update to match role focus |
| Hero stats (3 key metrics) | index.html | 35-46 | Pull from resume |
| Achievement cards | index.html | 83-118 | 6 cards total; reorder by relevance |
| Cloud & Infrastructure skills | index.html | 128-137 | First expertise category |
| Product & Strategy skills | index.html | 139-147 | Second expertise category |
| Leadership & Sales skills | index.html | 149-157 | Third expertise category |
| Certifications & Learning | index.html | 159-167 | Fourth expertise category |
| Timeline items (experience) | index.html | 177-237 | 5 entries total; order is chronological |
| Color scheme (CSS variables) | styles.css | 5-18 | Primary (#0066ff), secondary (#ff6b35) |
| Responsive breakpoints | styles.css | 724-819 | 768px (tablet), 480px (mobile) |
| Contact form API endpoint | script.js | 68 | Formspree form ID |
| Stats counter animation | script.js | 101-135 | Detects $M, %, or + formatting |
| Active nav highlighting | script.js | 190-208 | Updates on scroll (200px offset) |

## File Structure

```
waynecorrea/
├── index.html          # Main HTML file with all content
├── styles.css          # All styling (800+ lines, well-commented)
├── script.js           # Client-side interactivity (245 lines)
└── CLAUDE.md           # This file

Related directory:
../Job-Search/         # Resume files for different opportunities
├── Wayne Correa - MGMTinMotion.pdf
├── Wayne Correa Resume - Flexential.docx
├── Wayne Correa Resume GCP PM.pdf
└── [other role-specific resumes]
```

## Performance Notes

- No build process or dependencies to install
- CSS custom properties enable efficient theme changes
- IntersectionObserver used efficiently for scroll animations (auto-unobserves when done)
- Parallax effect uses `transform` property (GPU-accelerated)
- Contact form offloads backend to Formspree (zero-cost for non-commercial use)

## Important Implementation Details

### Syncing with Job-Search Resumes
The portfolio content should align with your resume files in `/home/wayne/AI-Projects/Job-Search/`. Key alignment points:
- **Hero stats**: Extract 3 strongest quantifiable results from the target resume
- **Achievement cards**: Pull 6 best examples that match the job description
- **Expertise sections**: Reorder or emphasize categories matching job requirements
- When tailoring for a specific opportunity, review the corresponding resume first to ensure consistency

### Stats Counter (script.js:101-135)
The counter animation parses text content to detect format (currency with $M, percentage %, or count with +). Ensure stat values maintain this format when updating.

### Timeline Alternation (styles.css:476-482)
The experience timeline alternates left/right using CSS `direction: rtl` on even items. This creates the classic alternating timeline look. Maintain this pattern when adding new experiences.

### Form Submission (script.js:53-94)
The form uses async fetch to Formspree. Error handling provides fallback email address (waynejcorrea@gmail.com). Status messages display for 5 seconds on success.

### Active Nav Link (script.js:190-208)
Detects current section based on scroll position with 200px offset. Links update dynamically. The active state adds `active` class which triggers the underline (defined in CSS but not currently visible—could be styled further).

## Deployment

- Deploy entire directory as-is to any static hosting (GitHub Pages, Netlify, Vercel, etc.)
- No environment variables or secrets needed (Formspree form ID is public)
- Works offline except for Google Fonts and Formspree
- All modern browsers supported (uses ES6+ JavaScript features)

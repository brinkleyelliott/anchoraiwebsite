# CLAUDE.md - AI Assistant Guide for Anchor AI Website

## Project Overview

This is a **static HTML website** for Anchor AI Management (anchoraimanagement.net) - a business automation platform targeting service-based businesses. The site consists of self-contained HTML files deployed via GitHub Pages with no build process required.

**Key Characteristics:**
- Pure vanilla HTML5, CSS3, and JavaScript (ES6+)
- No frameworks, bundlers, or package managers
- All styles and scripts embedded within each HTML file
- Direct GitHub Pages deployment

## Project Structure

```
/anchoraiwebsite/
├── index.html                    # Main landing page (hero, navigation, modals)
├── dashboard.html                # Business dashboard demo (multi-section SPA)
├── client-portal.html            # Client-facing portal demo
├── booking.html                  # Step-by-step booking wizard
├── roi-calculator.html           # Interactive ROI calculator
├── before-after.html             # Before/after comparison toggle
├── workflow-builder.html         # Automation workflow builder
├── staff-scheduling.html         # Staff scheduling calendar
├── customer-chat.html            # AI chat interface demo
├── sms-marketing.html            # SMS campaign composer
├── review-management.html        # Review management interface
├── social-graphics.html          # Social media graphics creator
├── email-templates.html          # Email template gallery
├── loyalty-program.html          # Loyalty program management
├── Anchor_AI_*.html              # Alternative demo variants
├── dashboard (6).html            # Dashboard variant
├── CNAME                         # GitHub Pages domain (anchoraimanagement.net)
├── logo.png                      # Company logo (WebP format)
└── README.md                     # Minimal project readme
```

**Note:** All files are at root level - flat structure with no subdirectories.

## Technology Stack

| Technology | Usage |
|------------|-------|
| HTML5 | Document structure, semantic markup |
| CSS3 | Styling, Grid, Flexbox, animations, custom properties |
| JavaScript (ES6+) | Interactivity, DOM manipulation |
| Google Fonts | Inter font family (300-800 weights) |
| GitHub Pages | Hosting and deployment |

**No external libraries or frameworks** - everything is vanilla web technologies.

## Design System

### Color Variables (CSS Custom Properties)

```css
:root {
  /* Primary colors */
  --navy: #003366;
  --navy-light: #004d80;
  --navy-faded: rgba(0,51,102,0.08);
  --navy-soft: #e8f0f8;

  /* Accent colors */
  --red: #CC0000;
  --hover-red: #A30000;
  --red-faded: rgba(204,0,0,0.08);
  --red-soft: #fef2f2;

  /* Dark theme (dashboard pages) */
  --dark: #0f172a;
  --dark-card: #1e293b;
  --dark-border: #334155;

  /* Text colors */
  --text: #e2e8f0;
  --text-muted: #94a3b8;

  /* Utility colors */
  --green: #22c55e;
  --white: #ffffff;
  --light-gray: #F5F5F5;
}
```

### Typography
- **Font Family:** Inter (with system fallbacks)
- **Weights:** 300, 400, 500, 600, 700, 800
- **Source:** Google Fonts API

### Design Patterns
- Hero sections with gradient backgrounds
- Card-based layouts with shadows
- Sidebar navigation on dashboard pages
- Modal dialogs for additional content
- CSS Grid for responsive layouts

## Common Code Patterns

### Page Switching (SPA-like Navigation)

```javascript
function showPage(pageId) {
    document.querySelectorAll('.page-section').forEach(page => {
        page.style.display = 'none';
    });
    document.getElementById('page-' + pageId).style.display = 'block';
    // Update active navigation
    document.querySelectorAll('.nav-item').forEach(item => {
        item.classList.remove('active');
    });
    document.querySelector(`.nav-item[data-page="${pageId}"]`).classList.add('active');
}
```

### Modal Management

```javascript
function openModal(modalId) {
    document.getElementById(modalId).classList.add('active');
}

function closeModal() {
    document.querySelector('.modal.active').classList.remove('active');
}
```

### Input/Slider Synchronization

```javascript
function syncSlider(inputId, value) {
    document.getElementById(inputId).value = value;
    document.getElementById(inputId + '-slider').value = value;
    calculate(); // Trigger recalculation
}
```

### Event Handling Convention
- Inline handlers for simple actions: `onclick="showPage('dashboard')"`
- Data attributes for element identification: `data-page="dashboard"`
- Direct style manipulation: `element.style.display = 'block'`

## CSS Patterns

### Responsive Grid Layouts
```css
.grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1.5rem;
}
```

### Animations
```css
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

.animated-element {
    animation: fadeIn 0.5s ease-out;
}
```

### Media Queries
- Primary breakpoint: `@media (max-width: 800px)`
- Mobile adjustments: `@media (max-width: 600px)`

## Development Workflow

### Making Changes

1. **Edit HTML directly** - Open the relevant `.html` file
2. **Modify CSS** - Edit within the `<style>` block in `<head>`
3. **Update JavaScript** - Edit within the `<script>` block at end of `<body>`
4. **Test locally** - Open file in browser (no build needed)
5. **Commit and push** - Changes deploy automatically to GitHub Pages

### Creating New Pages

1. Create new `.html` file with HTML5 boilerplate
2. Copy CSS variables and global styles from `index.html`
3. Add page-specific content and functionality
4. Add navigation link from `index.html` if needed
5. Commit and push to deploy

### File Structure Within HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Page description">
    <title>Page Title - Anchor AI</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        /* All CSS here */
    </style>
</head>
<body>
    <!-- HTML content -->

    <script>
        /* All JavaScript here */
    </script>
</body>
</html>
```

## External Links & Services

- **Calendly:** `https://calendly.com/brinkley-anchoraimanagement/30min`
- **Email:** `brinkley@anchoraimanagement.net`
- **Domain:** `anchoraimanagement.net` (via CNAME)

## Important Conventions

### Do's
- Use CSS custom properties for colors
- Follow existing naming patterns for classes
- Keep all code (CSS/JS) within the HTML file
- Use semantic HTML elements
- Maintain responsive design with Grid/Flexbox
- Test across browsers before pushing

### Don'ts
- Don't add npm/build tooling without explicit request
- Don't create separate CSS/JS files (maintain current pattern)
- Don't add external libraries without approval
- Don't modify CNAME unless changing domain
- Don't commit sensitive data or API keys

## Common Functions Reference

| Function | Purpose | Used In |
|----------|---------|---------|
| `showPage(pageId)` | Switch page sections | dashboard, client-portal, customer-chat |
| `closeModal()` | Close modal dialogs | Multiple pages |
| `sendMessage()` | Handle message sending | customer-chat, sms-marketing |
| `toggleView()` | Toggle between views | before-after |
| `syncSlider(id, val)` | Sync input/slider | booking, roi-calculator |
| `calculate()` | Perform calculations | roi-calculator |
| `nextStep() / prevStep()` | Wizard navigation | booking, sms-marketing |
| `selectService()` | Service selection | booking |

## Deployment

**GitHub Pages** - Automatic deployment on push to main branch

- Domain configured via `CNAME` file
- No build step required
- Changes go live within minutes of push

## Git Workflow

```bash
# Standard workflow
git add <files>
git commit -m "Description of changes"
git push origin <branch-name>
```

**Branch naming:** Feature branches use `claude/` prefix when created by AI assistants.

## Accessibility Notes

Current implementation could benefit from:
- ARIA labels on interactive elements
- Alt text on all images
- Keyboard navigation support
- Focus management in modals
- Color contrast verification

## Performance Considerations

- No minification (files served as-is)
- Google Fonts loaded from CDN
- Images should be optimized before adding
- Each page is self-contained (no shared resources)

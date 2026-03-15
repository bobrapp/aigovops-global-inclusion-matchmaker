# Claude Code Rules
# AiGovOps Global Inclusion Matchmaker

## Project Context
This is an open-source, single-page HTML application that connects Indigenous communities, rural populations, and disadvantaged groups across G20 nations with organizations, funders, and project opportunities for AI governance and policy-as-code.

## Architecture Rules

### Single File Architecture
- The entire application MUST be a single `index.html` file
- All CSS MUST be inline in a `<style>` tag
- All JavaScript MUST be inline in a `<script>` tag
- All data MUST be embedded as JavaScript constants
- NO external dependencies (no CDN links, no npm packages, no frameworks)
- NO build step required
- File MUST work when opened directly from filesystem (file:// protocol)

### Technology Stack
- HTML5 semantic elements
- CSS3 with CSS Custom Properties (variables)
- Vanilla JavaScript ES6+ (no jQuery, no React, no Vue)
- No external fonts (use system font stack)
- No external images (use SVG inline or CSS-generated graphics)

### Performance
- Total file size MUST be under 500KB
- No lazy loading needed (single file)
- Minimize DOM manipulation (use documentFragment for batch updates)
- Use event delegation on parent containers

## Data Rules

### Organization Entries
Every organization MUST have:
- `id`: unique kebab-case identifier (e.g., "us-aigovops")
- `name`: official organization name
- `country`: full country name
- `countryCode`: ISO 3166-1 alpha-2 code
- `region`: state/province/region within country
- `type`: one of ["indigenous", "rural", "academic", "government", "nonprofit", "tech"]
- `url`: valid HTTPS URL
- `email`: contact email (can be empty string)
- `phone`: contact phone (can be empty string)
- `mission`: max 200 characters describing mission
- `topics`: array of lowercase topic tags
- `founded`: year as number
- `size`: one of ["small", "medium", "large"]

### Funder Entries
Every funder MUST have:
- `id`: unique kebab-case identifier
- `name`: organization name
- `program`: specific grant program name
- `url`: valid HTTPS URL to program page
- `fundingMin`: minimum grant amount in base currency (number)
- `fundingMax`: maximum grant amount in base currency (number)
- `currency`: ISO 4217 currency code
- `topics`: array of lowercase topic tags
- `geographicFocus`: array of country names or "Global"
- `deadline`: date string or "Rolling"
- `description`: max 200 characters
- `type`: one of ["tech_company", "government", "foundation", "multilateral"]

### Topic Tags
Use consistent topic tags from this controlled vocabulary:
- governance, policy-as-code, indigenous, rural, training
- certification, standards, broadband, language, sovereignty
- data-sovereignty, digital-equity, ai-literacy, community
- open-source, mentorship, workforce, agriculture, health
- education, youth, women, disability, climate

## UI/UX Rules

### Accessibility (WCAG 2.1 AA)
- All images MUST have alt text
- All form inputs MUST have associated labels
- Color contrast ratio MUST be at least 4.5:1 for text
- All functionality MUST be keyboard accessible
- Tab order MUST be logical
- Dynamic content changes MUST use aria-live regions
- Focus MUST be managed when switching tabs

### Design System
- Primary color: #1a5632 (forest green -- earth/sovereignty)
- Secondary color: #c4820e (amber -- warmth/inclusion)
- Accent color: #2563eb (blue -- trust/technology)
- Use system font stack: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif
- Border radius: 8px for cards, 4px for inputs
- Card shadow: 0 1px 3px rgba(0,0,0,0.1)

### Responsive Design
- Mobile-first approach
- Breakpoints: 640px (tablet), 1024px (desktop)
- Cards stack on mobile, 2-column on tablet, 3-column on desktop
- Navigation tabs scroll horizontally on mobile

## Code Style Rules

### JavaScript
- Use `const` by default, `let` only when reassignment needed
- Never use `var`
- Use arrow functions for callbacks
- Use template literals for string interpolation
- Use destructuring where it improves readability
- All functions MUST have JSDoc comments
- Use meaningful variable names (no single letters except loop counters)

### CSS
- Use CSS Custom Properties for all colors, spacing, and typography
- Use `rem` for font sizes, `px` for borders/shadows
- Use Flexbox for 1D layouts, Grid for 2D layouts
- Mobile styles first, then `@media (min-width: ...)` for larger screens
- No `!important` unless overriding third-party styles (which shouldn't exist)

### HTML
- Use semantic elements: `<main>`, `<nav>`, `<article>`, `<section>`, `<aside>`
- Use `<button>` for actions, `<a>` for navigation
- Use `<fieldset>` and `<legend>` for filter groups
- All `<input>` elements MUST have `<label>` elements

## Security Rules

- NEVER use `innerHTML` with user input -- use `textContent` or `createElement`
- NEVER make external HTTP requests
- NEVER set or read cookies
- NEVER use `eval()` or `Function()` constructor
- NEVER use `document.write()`
- All URLs in data MUST be HTTPS

## Testing Rules

- Test all 5 tabs render correctly
- Test filter combinations return expected subsets
- Test matchmaker with known inputs returns expected scores
- Test proposal generator fills all template sections
- Test keyboard navigation through all interactive elements
- Test with screen reader (VoiceOver on macOS)
- Test offline functionality

## Git Rules

- Commit messages: imperative mood ("Add feature" not "Added feature")
- One logical change per commit
- Data additions: "Add [org-name] to [country] organizations"
- Feature changes: "Add [feature] to [tab] tab"
- Bug fixes: "Fix [issue] in [component]"
- Docs: "Update [document] with [change]"

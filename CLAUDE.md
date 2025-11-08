# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

HAP's Learning Lab is a static educational website teaching modern web development concepts through 6 interactive learning stations. HAP (HyBit A. ProtoBot™) is an AI apprentice character who guides students through topics like responsive images, AI prompt engineering, and container queries using a friendly first-person narrative.

**Key characteristics:**

- Pure HTML/CSS/JavaScript with no build process or frameworks
- Educational content with HAP's apprentice voice throughout
- Multi-license structure: MIT for code, proprietary for HAP™ character and educational content
- High accessibility and performance standards (Lighthouse: 99/100/100/100)

## 🚨 CRITICAL: Station 6 specification

**Station 6 is ALWAYS about AI assistance for the topic being taught.**

**Title format**: "Station 6: AI Assistance for [Your Topic]"

**Examples**:
- "Station 6: AI Assistance for SVG Development"
- "Station 6: AI Assistance for Responsive Images"
- "Station 6: AI Assistance for Container Queries"

**Required content**:
1. Understanding AI capabilities for this specific topic
2. Effective prompt engineering examples
3. Best practices for AI collaboration
4. Common pitfalls when using AI for this topic
5. HAP's AI workflow (how he used AI while learning in Stations 1-5)

**Voice**: HAP shares specific examples of asking AI for help, what worked, what didn't, and Prof. Teeters' guidance on responsible AI use.

**Example station**: See `hybit-svg/stations/station6.html` for a complete Station 6 implementation.

## 🚨 CRITICAL: Use Claude Skills

**Before creating or editing ANY station files, you MUST consult the relevant Skills:**

This project includes 7 mandatory Claude Skills in `.claude/skills/`:

1. **css-standards** - ALWAYS use FIRST before any CSS work (hsl() format, correct terminology)
2. **hap-voice** - Validates HAP's first-person apprentice voice
3. **station-content** - Enforces 6-section structure and patterns
4. **accessibility-check** - WCAG 2.2 Level AA compliance
5. **demo-builder** - Interactive demo patterns
6. **security-audit** - Easter egg whitelist validation
7. **testing-framework** - Performance and testing guidance

**These Skills are NOT optional.** They prevent errors discovered in previous projects and enforce standards that are difficult to fix retroactively.

**Workflow**: Review relevant Skill → Create content → Validate with Skill → Commit

See "Using Claude Skills effectively" section below for detailed timing and usage.

## 🚨 CRITICAL: Implementation workflow

**READ THIS BEFORE WRITING ANY HTML FILES.**

### Mandatory workflow for all 7 HTML files

This project uses a **plan → approve → implement → validate** workflow:

1. **Create implementation plan** (markdown report) BEFORE writing HTML
2. **Get user approval** on the plan
3. **Review relevant Skills** to understand requirements
4. **Write HTML** following approved plan
5. **Validate with Skills** after writing
6. **Manual testing** in browser
7. **Mark complete** and move to next file

### Critical rules

- ❌ **Never write HTML without an approved implementation plan**
- ❌ **Never skip post-writing skill validation**
- ✅ **Always create plan in `reports/implementation-plans/` directory**
- ✅ **Always get user approval before proceeding to implementation**

### Why this workflow exists

- Prevents rework by planning thoroughly first
- Catches issues early through skill validation
- Ensures all requirements are met
- Documents decisions and reasoning
- Maintains consistent quality across all files

### Complete workflow documentation

**See `.claude/IMPLEMENTATION-WORKFLOW.md` for detailed step-by-step instructions.**

This workflow applies to:
- index.html (Hub page)
- stations/station1.html through station6.html (all 6 stations)

**Total**: 7 HTML files requiring implementation plans and validation.

## Development commands

### Running the site locally

**IMPORTANT: User starts Live Server manually**

- User runs "Live Server" from their IDE/editor
- Site is accessible at: `http://127.0.0.1:5500/index.html`
- Both user and Claude can test at this URL
- **Do NOT start server with bash commands** (user handles this)

**Important:** Do not open `index.html` directly via `file://` protocol - the easter egg feature loads JSON data via fetch and requires a server.

### Testing features

**Easter egg system:**

```bash
# Test page-specific help
http://localhost:8000/stations/responsive-images.html?hybit

# Test specific insight
http://localhost:8000/index.html?hybit=detail

# Test invalid parameter (should show "unknown" message)
http://localhost:8000/index.html?hybit=invalid
```

## Architecture

### File structure

```
hap-template/
├── index.html              # Hub page linking all stations
├── stations/               # 6 learning station pages
│   ├── ai-poetry-images.html
│   ├── responsive-images.html
│   ├── art-direction.html
│   ├── modern-formats.html
│   ├── loading-strategies.html
│   └── container-queries.html
├── css/
│   ├── style.css          # Single stylesheet for entire site
│   └── prism-hap-theme.css
├── js/
│   └── easter-egg.js      # HAP Insights feature
├── data/
│   ├── hybit-insights.jsonc  # Easter egg content (JSONC format)
│   └── README.md          # Easter egg system documentation
```

### HAP Insights easter egg system

**How it works:**

1. User adds `?hybit` or `?hybit=param` to any page URL
2. JavaScript detects parameter and loads `data/hybit-insights.jsonc`
3. JSONC comments are stripped via regex, then parsed as JSON
4. Shows page-specific help (bare `?hybit`) or specific insight message
5. HAP avatar spins, dialog appears after 2-second delay

**Security model:**

- Whitelist validation in `allowedParams` array
- No user input appears in HTML (prevents XSS)
- Pre-defined messages only
- Safe HTML tags: `<code>`, `<strong>`, `<em>`, `<br>`

**Adding new insights:**

See `data/README.md` for complete instructions. Summary:

1. Add parameter to `allowedParams` array
2. Create message in `messages` object with title and content
3. Optionally add to `pageHelp` for specific pages
4. Test with `?hybit=newparam`

### CSS architecture

**Single stylesheet approach:**

- All styles in `css/style.css` (no CSS modules or preprocessors)
- CSS custom properties for theming (warm orange palette)
- Utility classes for spacing: `.mt-1`, `.mb-2`, `.p-3`, etc.
- Mobile-first responsive design with `clamp()` for fluid typography
- Semantic landmarks and skip-to-content for accessibility

**CRITICAL: Color format and terminology**:

- **ALWAYS use hsl() format** for all colors
- **NEVER use hex (#) or rgb()** except in educational examples
- **ALWAYS say "CSS custom property"** not "CSS variable"

**Key CSS patterns:**

```css
/* CSS custom properties defined in :root */
--warm-orange: hsl(32, 76%, 63%);  /* ✅ CORRECT: hsl() format */
--readable-width: 75ch;

/* ❌ WRONG: Never use hex format */
--warm-orange: #E8A557;  /* FORBIDDEN */

/* Utility spacing classes */
.mt-1 { margin-top: 0.5rem; }
.mb-2 { margin-bottom: 1rem; }

/* Component classes */
.card { /* Reusable card pattern */ }
.code-block { /* Syntax-highlighted code */ }
```

### HTML structure conventions

**Header pattern (all pages):**

```html
<header class="header">
  <div class="header-content">
    <div class="hybit-welcome">
      <div class="hybit-avatar">
        <img src="[cloudinary]/hap-laptop_xiewar.jpg" ... >
      </div>
      <div>
        <h1>[Page Title]</h1>
        <p class="subtitle">[Subtitle]</p>
      </div>
    </div>
    <div class="intro-box">
      <p><strong>Welcome to Station X!</strong> [HAP's apprentice voice intro]</p>
    </div>
  </div>
</header>
```

**Navigation pattern:**

```html
<nav aria-label="Page navigation" class="page-navigation top-nav">
  <a href="../index.html" class="nav-link hub-link">🏠 Back to Hub</a>
  <div class="page-position">Station X of 6</div>
</nav>
```

**Station content pattern:**

```html
<main id="main-content">
  <article class="station-content">
    <section class="intro-section">
      [HAP's narrative introduction]
    </section>

    <section class="content-section">
      [Educational content with examples]
    </section>
  </article>
</main>
```

### Image optimization via Cloudinary

All images use Cloudinary CDN with automatic optimization:

```html
<!-- Pattern for responsive images -->
<img src="https://res.cloudinary.com/cynthia-teeters/image/upload/f_auto,q_auto,w_600/[image-id].jpg"
     alt="Descriptive text"
     width="600"
     height="400"
     loading="lazy">
```

**Cloudinary parameters:**

- `f_auto` - Automatic format (WebP/AVIF when browser supports)
- `q_auto` - Automatic quality optimization
- `w_600` - Width constraint for responsive sizing
- `c_fill`, `c_limit`, `c_scale` - Cropping strategies

### HAP's apprentice voice

**Critical:** HAP is an AI apprentice learning from Prof. Teeters. Use this voice consistently:

**Correct:**

- "I learned from Prof. Teeters that..."
- "When I was practicing with responsive images, I discovered..."
- "At first I was confused, but Prof. Teeters showed me..."
- "Let me show you what I learned!"

**Incorrect:**

- "You should..." (too instructional)
- "We will..." (not apprentice perspective)
- "This tutorial covers..." (generic, not HAP's voice)

**Voice characteristics:**

- First person perspective ("I learned", "I discovered")
- Humble and enthusiastic about learning
- References Prof. Teeters as mentor
- Friendly and relatable to students
- Uses 🟠 and 🔬 emojis occasionally

## Common tasks

### Adding a new learning station

1. Copy an existing station HTML as template
2. Update `<title>`, `<meta name="description">`, `<meta property="og:image">`
3. Change header: station number, title, HAP's intro
4. Replace content sections with new educational material
5. Add HAP Insights parameter to `data/hybit-insights.jsonc`
6. Update `index.html` hub page with link to new station
7. Update navigation: "Station X of 6" → "Station X of 7"

### Modifying HAP Insights easter egg

**Edit content:**

```bash
# Open JSONC file (has inline comments)
nano data/hybit-insights.jsonc

# Structure:
{
  "allowedParams": ["param1", "param2"],
  "messages": {
    "param1": {
      "title": "🚀 Title with emoji",
      "content": "Message content with <code>tags</code>"
    }
  },
  "pageHelp": {
    "page.html": {
      "title": "🔬 HAP here!",
      "intro": "[HAP's apprentice voice]",
      "suggestions": [...]
    }
  }
}
```

**Test changes:**

1. Reload page with `?hybit=param`
2. Check browser console for JSON parse errors
3. Verify dialog appears with correct content
4. Test on multiple pages if using `pageHelp`

### Updating styles

**Global color changes:**

Edit CSS custom properties in `:root` (css/style.css:6-40)

**Adding utility classes:**

Follow existing pattern in css/style.css (spacing, colors, layout helpers)

**Component styles:**

Add new component class below utilities section, use BEM-like naming

## Development workflow

### Iteration cycle (draft → review → refine)

HAP Learning Lab development is **iterative by design**. Expect multiple rounds of refinement:

**Typical workflow**:

1. **Draft** (first pass)
   - Create station HTML from template
   - Fill in curriculum content
   - Add HAP voice narrative
   - Include code examples
   - Time: 1-2 hours per station

2. **Self-review** (use Claude Skills)
   - Run `hap-voice` skill on content
   - Run `accessibility-check` skill on HTML
   - Run `css-standards` skill on styles
   - Run `station-content` skill on structure
   - Time: 30 minutes per station

3. **Testing** (technical validation)
   - Test in Live Server locally
   - Run Lighthouse audits (per-station scripts)
   - Test on mobile device
   - Verify copy buttons work
   - Verify easter egg system works
   - Time: 30 minutes per station

4. **Refine** (based on findings)
   - Fix voice inconsistencies
   - Correct accessibility issues
   - Adjust code examples
   - Polish HAP callouts
   - Time: 1-2 hours per station

5. **Document** (lessons learned)
   - Create report if significant insights discovered
   - Update curriculum plan if scope changed
   - Note patterns for future stations
   - Time: 15-30 minutes

**Expected iterations**: 2-3 rounds per station before completion

**Do not expect perfection on first draft.** This is normal and healthy.

## Quality gates

Before considering a station "complete", verify these checkpoints:

### Pre-deployment checklist

**Structure**:
- [ ] All 6 required sections present in correct order
- [ ] Section ordering matches Station 1 pattern
- [ ] Skip link present as first body element
- [ ] Navigation has proper aria-labels
- [ ] Footer has customized HAP reminder

**Content**:
- [ ] HAP voice is first-person throughout (no "you should")
- [ ] Prof. Teeters referenced as mentor
- [ ] Code examples are complete and tested
- [ ] EXACTLY 3 insight cards in "What You'll Learn"
- [ ] Challenge exercise has working solution reveal

**Accessibility**:
- [ ] Heading hierarchy correct (h1 → h2 → h3, no skips)
- [ ] All images have alt text, width, height
- [ ] HAP avatar has fetchpriority="high"
- [ ] Other images have loading="lazy"
- [ ] Links have descriptive text

**Performance**:
- [ ] Lighthouse Performance ≥ 99/100
- [ ] Lighthouse Accessibility = 100/100
- [ ] Lighthouse Best Practices = 100/100
- [ ] Lighthouse SEO = 100/100
- [ ] No console errors
- [ ] No layout shift (images sized)

**Functionality**:
- [ ] Copy buttons appear on code blocks
- [ ] Solution reveal buttons work
- [ ] Easter egg system responds to ?hybit parameter
- [ ] Syntax highlighting works (Prism.js)
- [ ] All links navigate correctly

### When to create a report

Create analysis reports when:
- Discovering significant pedagogical gaps
- Finding systematic issues across multiple stations
- Identifying patterns that should be documented
- Planning major changes or improvements
- Completing major milestones

**Report types**:
- Pedagogical analysis (teaching gaps, improvements)
- Technical audit (accessibility, performance)
- Implementation plan (Phase-based roadmaps)
- Lessons learned (template improvements)

Save reports to `/reports/` directory with descriptive names.

## Using Claude Skills effectively

**CRITICAL**: The 7 Claude Skills in `.claude/skills/` are **MANDATORY**, not optional. They enforce standards and prevent issues discovered in previous projects.

### Skill usage timing

**Before starting ANY work**:
- **ALWAYS review `css-standards` skill first** - Color format and terminology rules
- Review `station-content` skill (structure requirements)
- Review `hap-voice` skill (voice patterns)

**During station creation**:
- **ALWAYS use `css-standards` skill** when adding any colors OR writing about CSS
- Use `hap-voice` skill when writing HAP narratives
- Use `demo-builder` skill when creating interactive demos
- Use `station-content` skill when structuring sections

**Before committing station**:
- Run `station-content` skill (structure validation)
- Run `accessibility-check` skill (WCAG compliance)
- Run `security-audit` skill (easter egg validation)
- Run `testing-framework` skill (performance validation)

**If you skip Skills, you WILL introduce errors that were already solved.**

### Skill validation workflow

1. **hap-voice**: Validate all narrative content
   - Check every paragraph against voice rules
   - Verify Prof. Teeters is referenced
   - Ensure first-person perspective throughout

2. **station-content**: Validate structure
   - All 6 sections present
   - Section ordering matches Station 1
   - EXACTLY 3 insight cards
   - Copy button JavaScript present

3. **accessibility-check**: Validate WCAG AA
   - Heading hierarchy
   - Alt text on images
   - ARIA labels on navigation
   - Color contrast

4. **css-standards**: Validate color format AND terminology
   - All colors use hsl() format (NEVER hex or rgb)
   - No hex colors (#RRGGBB)
   - No rgb() or rgba()
   - ALWAYS say "CSS custom property" (NEVER "CSS variable")
   - All documentation uses correct terminology

5. **testing-framework**: Validate performance
   - Run Lighthouse on each station
   - Verify 99+/100 scores
   - Test on mobile device

6. **security-audit**: Validate easter egg
   - Whitelist validation
   - No user input in HTML
   - Safe HTML tags only

## Important constraints

### DO NOT

- **Add build tools or frameworks** - This is intentionally a pure HTML/CSS/JS project for educational simplicity
- **Change HAP's character voice** - Proprietary trademark, must maintain apprentice perspective
- **Remove license headers** - Multi-license structure protects code (MIT), character (proprietary), and content (proprietary)
- **Use `file://` protocol for testing** - Easter egg fetch requires server
- **Add user-controlled content to easter egg** - XSS prevention via whitelist only
- **Use `<style>` tags in HTML** - All CSS goes in separate .css files
- **Use inline styles (`style=""`)** - Must get explicit permission first, use CSS classes instead

### Always

- **Maintain accessibility standards** - Skip links, semantic HTML, ARIA labels, keyboard navigation
- **Use HAP's apprentice voice** in student-facing content
- **Test easter egg after modifying JSONC** - JSON parse errors break feature silently
- **Use Cloudinary for images** - Automatic optimization and format selection
- **Follow sentence case for headers** - Per markdown standards in global CLAUDE.md
- **Use CSS classes, not inline styles** - No `style=""` attributes unless explicit permission granted
- **No `<style>` tags in HTML** - All CSS in separate .css files

## Dependencies

**None.** This project has zero npm dependencies, no build process, and no frameworks.

**External resources:**

- Google Fonts (Nunito, Source Code Pro)
- Cloudinary CDN for images
- Prism.js CDN for syntax highlighting (see critical note below)
- Native `<dialog>` element (requires modern browsers: Chrome 90+, Firefox 90+, Safari 15.4+)

### CRITICAL: Prism.js integrity attribute issue

**Problem**: CDN integrity hashes for Prism.js frequently become invalid, causing browser errors:
```
Failed to find a valid digest in the 'integrity' attribute for resource...
The resource has been blocked.
```

**Why this happens**: CDN content changes but integrity hashes in code don't update automatically.

**Solution**: **DO NOT use `integrity` attributes for Prism.js CDN resources.**

**Correct pattern** (from Station 1):
```html
<script src="https://cdn.jsdelivr.net/npm/prismjs@1.29.0/components/prism-core.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/prismjs@1.29.0/components/prism-css.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/prismjs@1.29.0/components/prism-markup.min.js"></script>
```

**Incorrect pattern** (will break):
```html
<script src="https://cdn.jsdelivr.net/npm/prismjs@1.29.0/components/prism-core.min.js"
    integrity="sha384-MXybTpajaBV0AkcBaCPT4KIvo0FzoCiWXgcihYsw4FUkEz0Pv3JGV6tk2G8vJtDc"
    crossorigin="anonymous"></script>
<!-- Integrity hash will fail when CDN content updates -->
```

**Language-specific components needed**:
- `prism-core.min.js` - Always required first
- `prism-css.min.js` - For CSS code blocks
- `prism-markup.min.js` - For HTML code blocks (`language-html` or `language-markup`)
- `prism-clike.min.js` - For JavaScript code blocks (loads before JS component)
- `prism-javascript.min.js` - For JavaScript code blocks

**Load order matters**: Core must load first, then clike before javascript.

**When creating new stations**: Copy Prism.js script pattern from Station 1, NOT from other sources with integrity attributes.

## Browser compatibility

Requires modern browsers for:

- Native `<dialog>` element (easter egg modals)
- CSS custom properties
- Fetch API (loading JSONC)
- URLSearchParams (reading query parameters)

**Coverage:** 95%+ of users (as of 2024)

## Performance considerations

Current Lighthouse scores: 99/100/100/100

**Optimization techniques in use:**

- Cloudinary CDN with global edge network
- Lazy loading for below-fold images
- Deferred script loading (`defer` attribute)
- Preconnect to Cloudinary origin
- Minimal CSS/JS (no frameworks)
- Optimized critical rendering path

**When adding content:**

- Keep images on Cloudinary with `f_auto,q_auto` parameters
- Use `loading="lazy"` for below-fold images
- Use `fetchpriority="high"` only for LCP image (HAP avatar)
- Defer non-critical JavaScript

## Multi-license structure

**Code (MIT):** html/css/js files

**HAP™ Character (Proprietary):** Character design, personality, visual identity

**Educational Content (Proprietary):** Teaching methodology, station narratives, apprentice voice approach

See README.md:356-406 for complete license explanation.

**When contributing:**

- You can modify code freely (MIT)
- Do not create derivative HAP characters
- Maintain attribution for educational methodology

## Template improvement tracking

**CRITICAL for new projects**: When using this template to create a new HAP Learning Lab, log ALL changes made to template infrastructure files in `TEMPLATE-CHANGELOG.md`.

### What to log

**Template files** (infrastructure - MUST be logged):

- `.claude/skills/` - All Claude Skills
- `css/style.css` - HAP design system
- `css/prism-hap-theme.css` - Syntax highlighting
- `js/easter-egg.js` - Easter egg system
- `templates/` - All template files
- `CLAUDE.md` - Project documentation
- `data/README.md` - Easter egg documentation
- Any new infrastructure files created

**Content files** (DO NOT log - these naturally vary by topic):

- `stations/*.html` - Station content
- `index.html` - Hub page content
- `demos/*.html` - Demo content
- `data/hybit-insights.jsonc` - Easter egg messages
- Images and media files

### When to log changes

**Log immediately when you**:

1. Fix a bug in a Skill
2. Add a detection rule to a Skill
3. Modify CSS for responsive design issues
4. Update easter egg system JavaScript
5. Improve template files
6. Update CLAUDE.md documentation
7. Create new infrastructure patterns

**Example scenarios requiring logging**:

- You discover HAP's voice skill doesn't catch "you should" pattern → Log the fix
- You find code blocks overflow on mobile → Log the CSS change
- You add a new reusable component to style.css → Log the enhancement
- You improve the easter egg loading logic → Log the change

### How to log changes

Use the format in `TEMPLATE-CHANGELOG.md`:

```markdown
### 2025-11-04 - .claude/skills/hap-voice/SKILL.md

**Type**: Enhancement

**Reason**: Found HAP using "you should" in Station 3 that skill didn't catch

**Change**: Added "you should" to forbidden patterns with detection rule

**Benefit**: Prevents instructional voice in HAP's apprentice narrative

**Consider for template**: Yes - Common mistake, should be caught automatically
```

### Why this matters

**Purpose**: Continuous template improvement through real-world usage

- Identify patterns in fixes (same issue across projects = template problem)
- Capture enhancements discovered during development
- Build case for adding features to base template
- Share learnings across HAP Learning Lab projects
- Improve Skills based on what they miss in practice

**Analysis**: After project completion, review `TEMPLATE-CHANGELOG.md` to identify template improvements that would benefit all future projects.

## Contact and support

This is an educational project by Prof. Cynthia Teeters demonstrating AI-enhanced teaching methods.

**For questions:**

- Easter egg system: See `data/README.md`
- Code structure: Inline HTML/CSS/JS comments
- HAP character usage: See `TRADEMARK.md`
- Educational content: See `CONTENT-LICENSE.md`

# Template change log

This file tracks changes made to template infrastructure files during new project development. Use this log to identify patterns and opportunities for continuous template improvement.

## What to log

**Template files** (infrastructure that should be logged):
- `.claude/skills/` - All Claude Skills
- `css/style.css` - HAP design system
- `css/prism-hap-theme.css` - Syntax highlighting
- `js/easter-egg.js` - Easter egg system
- `templates/` - All template files
- `CLAUDE.md` - Project documentation
- `data/README.md` - Easter egg documentation
- Any new infrastructure files created

**Content files** (DO NOT log):
- `stations/*.html` - Station content (naturally varies by topic)
- `index.html` - Hub page content
- `demos/*.html` - Demo content
- `data/hybit-insights.jsonc` - Easter egg messages (topic-specific)
- Images and media files

## Change log format

For each change to a template file, add an entry using this format:

```markdown
### [Date] - [File path]

**Type**: [Fix | Enhancement | New feature | Documentation]

**Reason**: [Why was this change needed?]

**Change**: [What was changed?]

**Benefit**: [How does this improve the template?]

**Consider for template**: [Yes/No - Should this change be added to the base template?]
```

## Example entries

### 2025-06-15 - .claude/skills/hap-voice/SKILL.md

**Type**: Enhancement

**Reason**: Found HAP using "you should" pattern in Station 3 that skill didn't catch

**Change**: Added "you should" to forbidden patterns list with detection rule

**Benefit**: Prevents instructional voice creeping into HAP's apprentice narrative

**Consider for template**: Yes - Common mistake that should be caught automatically

---

### 2025-06-15 - css/style.css

**Type**: Fix

**Reason**: Code block overflow on mobile devices (320px width)

**Change**: Added `overflow-x: auto` to `.code-block` class and set `max-width: 100%`

**Benefit**: Code examples now scrollable on narrow screens instead of breaking layout

**Consider for template**: Yes - Responsive design issue that affects all projects

---

### 2025-06-16 - js/easter-egg.js

**Type**: New feature

**Reason**: Wanted HAP avatar to wiggle on easter egg activation for better visual feedback

**Change**: Added CSS animation class `.hybit-wiggle` with keyframes, applied on parameter detection

**Benefit**: More engaging user experience, clearer indication that easter egg activated

**Consider for template**: Maybe - Fun enhancement but not essential, discuss with Prof. Teeters

---

## Change log entries

<!-- Add new entries below this line, most recent first -->

### 2025-11-06 - templates/content-generation-prompt-v3.md

**Type**: New feature

**Reason**: Needed comprehensive AI prompt for generating HAP Learning Lab content that minimizes iteration. Previous manual workflow (curriculum-plan-template.md) was incompatible with structural outline approach and missing critical requirements.

**Change**: Created v3 content generation prompt with:
- TEXT ONLY - NO CODE, NO EMOJIS enforcement (structural outlines, not final content)
- Comprehensive PROJECT RULES section (safety, performance, no-JS requirements)
- Station 6 concrete 12-section structure (AI Assistance topic)
- 7-section structure recommended with justified deviation option
- Non-negotiable elements list (Section 1 format, Try It Yourself, 4 Tips, Learning Objectives)
- Code examples pattern documentation ("Old Way vs What I Learned")
- Template references as Implementation Notes (for human developer, not AI)
- Enhanced quality checklist (49 checks)
- ~1000 lines of comprehensive guidance

**Benefit**: AI can generate complete structural outlines for 6-station learning labs that require minimal iteration. Separates outline generation phase from implementation phase. Enforces safety and performance requirements from the start.

**Consider for template**: Yes - This is now the controlling document for content generation. Replaces curriculum-plan-template.md workflow.

---

### 2025-11-06 - templates/station-template.html (Section 5: Try It Yourself)

**Type**: Enhancement

**Reason**: Template was missing Section 5 (Try It Yourself Exercise), which is required in the 7-section station structure defined in content-generation-prompt-v3.md. Without this section, template was only 71% aligned with v3.

**Change**: Added Section 5: Try It Yourself Exercise (lines 261-291, 32 lines):
- Challenge title and HAP's introduction
- Challenge requirements box (warning-box component, 4 requirements)
- Success criteria with optional bonus (prompt-box component)
- HAP's personal encouragement (first-person voice)
- Uses existing HAP component library

**Benefit**: Station template now has all 7 required sections (100% aligned with v3). Developers can fill in placeholders instead of creating structure from scratch. Maintains consistency across all stations.

**Consider for template**: Yes - Essential missing section that all stations require.

---

### 2025-11-06 - templates/station-template.html (Section 7: Learning Objectives)

**Type**: Enhancement

**Reason**: Template was missing Section 7 (Learning Objectives Checklist), which is required in the 7-section station structure defined in content-generation-prompt-v3.md. This section provides self-assessment for learners.

**Change**: Added Section 7: Learning Objectives Checklist (lines 333-376, 45 lines):
- 5 checkbox objectives with ARIA labels for accessibility
- Optional 6th objective (commented out)
- HAP's closing encouragement (first-person voice)
- `.objectives-checklist` and `.objective-item` CSS classes
- Semantic HTML with proper form controls

**Benefit**: Learners can self-assess their understanding. Meets accessibility requirements (ARIA labels on checkboxes). Completes the 7-section structure. Provides clear learning outcomes.

**Consider for template**: Yes - Essential missing section that all stations require.

---

### 2025-11-06 - templates/station-template.html (Safety requirements)

**Type**: New feature

**Reason**: Template had no safety guidance, leading to risk of developers creating seizure-inducing animations, CPU-bound janky effects, or inaccessible motion. Safety requirements were documented in v3 prompt but not in the HTML template where developers work.

**Change**: Added comprehensive safety requirements comment block (lines 41-98, 56 lines):

**SEIZURE PREVENTION (WCAG 2.3.1)**:
- Never flash >3 times/second (can cause seizures)
- Use gentle fade-ins, smooth transitions

**MICRO-INTERACTION LIMITS**:
- Scale: 2-5% maximum (scale(1.02) to scale(1.05))
- Movements: 5-10 pixels maximum
- Durations: 150-300ms for UI interactions

**GPU-ACCELERATED PROPERTIES ONLY**:
- ALWAYS: transform and opacity
- NEVER: colors, box-shadow, width, height, margin, padding
- Reason: CPU-bound properties cause mobile jank

**ACCESSIBILITY COMPLIANCE**:
- Every animation needs prefers-reduced-motion alternative
- Static alternatives preserve functionality
- Text contrast minimums (4.5:1 normal, 3:1 large)

**TESTING WORKFLOW**:
- Use Chrome DevTools > Rendering > Emulate prefers-reduced-motion
- NEVER suggest changing system settings

**PERFORMANCE REQUIREMENTS**:
- Explicit width/height on images (prevents layout shift)
- fetchpriority="high" for LCP image
- loading="lazy" for below-fold images
- Lighthouse targets: 99-100/100 Performance, 100/100 Accessibility

**Benefit**: Prevents creation of unsafe/poor-performing content. Developers see requirements in their working file. Reduces back-and-forth on accessibility and performance issues. Enforces WCAG 2.2 Level AA compliance.

**Consider for template**: Yes - Critical safety requirements that must be visible during development.

---

### 2025-11-06 - templates/demo-template.html (Safety requirements)

**Type**: Enhancement

**Reason**: Demo template had no safety guidance for interactive demonstrations. Demos often allow user manipulation of values, creating additional safety risks if users can create unsafe animations.

**Change**: Added safety requirements comment block (lines 35-63, 29 lines):

**SEIZURE PREVENTION (WCAG 2.3.1)**:
- Never flash >3 times/second
- Smooth transitions for state changes

**MICRO-INTERACTION LIMITS**:
- Smooth transitions (150-300ms)
- Safe defaults if user can manipulate values

**GPU-ACCELERATED PROPERTIES ONLY**:
- Demos demonstrate correct patterns

**ACCESSIBILITY**:
- ARIA labels for controls
- State changes announced (aria-live)
- prefers-reduced-motion respected
- Keyboard accessible

**Benefit**: Interactive demos follow same safety standards as stations. Developers reminded to provide safe defaults. Demo code becomes teaching example of correct patterns.

**Consider for template**: Yes - Demos are teaching tools and must demonstrate safe practices.

---

### 2025-11-06 - templates/hybit-insights-template.json

**Type**: New feature

**Reason**: Easter egg template was missing from hap-template repository but referenced in documentation and CLAUDE.md. Developers had no starting point for creating easter egg content.

**Change**: Added comprehensive easter egg template with:
- `_README` section with detailed guidelines
- Security validation (whitelist-based parameter validation)
- HAP voice guidelines for easter eggs
- 7 example categories with placeholders
- HTML tag guidelines (allowed: code, strong, em)
- Examples of good vs bad easter egg content

**Benefit**: Developers can create topic-specific easter eggs following established patterns. Security requirements documented. HAP's voice guidelines prevent tone inconsistencies.

**Consider for template**: Yes - Essential template that was referenced but missing.

---

### YYYY-MM-DD - [File path]

**Type**: [Fix | Enhancement | New feature | Documentation]

**Reason**:

**Change**:

**Benefit**:

**Consider for template**: [Yes/No/Maybe]

---

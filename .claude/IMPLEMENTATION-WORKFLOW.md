# Implementation workflow for HAP Learning Lab

**CRITICAL**: Read this before implementing any HTML files

---

## Project structure understanding

### Reports folder = Content source (the "manuscript")
- `reports/focused-outline-hub.md` → Content for `index.html`
- `reports/focused-outline-station1.md` → Content for `stations/station1.html`
- `reports/focused-outline-station2.md` → Content for `stations/station2.html`
- `reports/focused-outline-station3.md` → Content for `stations/station3.html`
- `reports/focused-outline-station4.md` → Content for `stations/station4.html`
- `reports/focused-outline-station5.md` → Content for `stations/station5.html`
- `reports/focused-outline-station6.md` → Content for `stations/station6.html`
- `reports/focused-outline-hierarchy.md` → Overall structure reference
- `reports/project-startup-gap-analysis.md` → Gap analysis and requirements

### Template files = Structure framework (the "printing press")
- `index.html` - Hub page template with placeholders
- `stations/station1.html` through `station6.html` - Station templates with placeholders
- These contain `[PLACEHOLDERS]` to be replaced with actual content

### Skills folder = Quality assurance
- `.claude/skills/css-standards/` - Verify hsl() format, "CSS custom property" terminology
- `.claude/skills/hap-voice/` - Validate HAP's first-person apprentice voice
- `.claude/skills/station-content/` - Ensure 6-section structure in correct order
- `.claude/skills/accessibility-check/` - Verify WCAG 2.2 Level AA compliance
- `.claude/skills/demo-builder/` - Interactive demo patterns
- `.claude/skills/security-audit/` - Easter egg whitelist validation
- `.claude/skills/testing-framework/` - Performance and testing guidance

---

## MANDATORY workflow for each HTML file

### ⚠️ STOP - Do NOT write HTML directly

For each of the **7 HTML files**, you MUST follow this sequence:

### Step 1: Create implementation plan report (markdown)

**Before touching any HTML file**, create a detailed implementation plan as a markdown file.

**Location**: Save in `reports/implementation-plans/`

**Naming convention**:
- `implementation-plan-hub.md` for index.html
- `implementation-plan-station1.md` for station1.html
- `implementation-plan-station2.md` for station2.html
- etc.

**Required contents of implementation plan**:
1. **Content source**: Which outline file(s) will be used
2. **Sections to implement**: List all major sections from outline
3. **HAP narratives needed**: Specific stories/confessions to write
4. **Code examples required**: List all code blocks needed
5. **Interactive demonstrations**: What demos need to be built
6. **Accessibility requirements**: Specific `prefers-reduced-motion` implementations
7. **Skills to validate with**: Which skills will be used for QA
8. **Success criteria**: How to know this file is complete
9. **Estimated complexity**: Time estimate and difficulty assessment
10. **Dependencies**: What needs to exist first (CSS classes, JS functions, images)

**Why this step exists**:
- Forces thorough planning before coding
- Identifies missing content or unclear requirements
- Surfaces questions that need answers
- Creates a checklist for implementation
- Prevents scope creep and forgotten sections

### Step 2: Get approval on implementation plan

**Do NOT proceed to HTML until user approves the plan.**

User will review and may:
- Approve as-is → proceed to Step 3
- Request changes → revise plan and resubmit
- Ask clarifying questions → answer and update plan

### Step 3: Use skills BEFORE writing (proactive QA)

**Before writing HTML**, review relevant skills to understand requirements:

**Always review**:
- `css-standards` - Color format rules, terminology
- `hap-voice` - Voice patterns and examples
- `station-content` - Required section structure

**Review as needed**:
- `accessibility-check` - For sections with animations
- `demo-builder` - For interactive demonstrations
- `security-audit` - For easter egg implementations

**Purpose**: Prevent errors by understanding requirements first, not discovering violations after writing.

### Step 4: Implement HTML file

Now write the HTML file:
- Follow the approved implementation plan
- Use template structure as framework
- Replace placeholders with content from outlines
- Write in HAP's first-person apprentice voice
- Include all required sections
- Add all code examples
- Implement accessibility patterns

### Step 5: Use skills AFTER writing (validation QA)

**After writing HTML**, validate with skills:

**Must validate**:
- ✅ `hap-voice` - Check every HAP narrative
- ✅ `station-content` - Verify structure and sections
- ✅ `css-standards` - Check colors and terminology
- ✅ `accessibility-check` - Verify WCAG compliance

**Validate if applicable**:
- ✅ `demo-builder` - If interactive demos added
- ✅ `security-audit` - If easter egg parameters added

### Step 6: Address skill feedback

If skills identify issues:
- Fix all violations
- Re-run skills to verify fixes
- Document any exceptions with justification

### Step 7: Manual testing

After skill validation passes:
- Test in browser locally
- Test `prefers-reduced-motion` with DevTools
- Test all interactive elements
- Verify copy buttons work
- Check keyboard navigation

### Step 8: Mark complete and move to next file

Only after all validation passes:
- Mark file as complete in progress tracking
- Move to next HTML file
- Start from Step 1 (implementation plan)

---

## The 7 HTML files to implement

Work in this order:

1. **index.html** (Hub page)
   - Outline: `reports/focused-outline-hub.md`
   - Plan: `reports/implementation-plans/implementation-plan-hub.md`
   - Complexity: Medium (includes immediate visual demo)

2. **stations/station1.html** (CSS Transforms)
   - Outline: `reports/focused-outline-station1.md`
   - Plan: `reports/implementation-plans/implementation-plan-station1.md`
   - Complexity: High (establishes demo patterns for all stations)

3. **stations/station2.html** (CSS Transitions)
   - Outline: `reports/focused-outline-station2.md`
   - Plan: `reports/implementation-plans/implementation-plan-station2.md`
   - Complexity: Medium (introduces `prefers-reduced-motion`)

4. **stations/station3.html** (Timing Functions and Performance)
   - Outline: `reports/focused-outline-station3.md`
   - Plan: `reports/implementation-plans/implementation-plan-station3.md`
   - Complexity: High (complex performance examples)

5. **stations/station4.html** (Micro-interactions)
   - Outline: `reports/focused-outline-station4.md`
   - Plan: `reports/implementation-plans/implementation-plan-station4.md`
   - Complexity: High (many patterns to demonstrate)

6. **stations/station5.html** (Keyframes Animations)
   - Outline: `reports/focused-outline-station5.md`
   - Plan: `reports/implementation-plans/implementation-plan-station5.md`
   - Complexity: Medium (keyframes syntax and patterns)

7. **stations/station6.html** (AI Assistance for Animation)
   - Outline: `reports/focused-outline-station6.md`
   - Plan: `reports/implementation-plans/implementation-plan-station6.md`
   - Complexity: Medium (prompt examples and workflows)

---

## Skills as quality assurance checkpoints

### Think of skills as automated reviewers

**During planning** (Step 1):
- Read skills to understand what they check
- Plan content that will pass skill validation
- Identify potential issues early

**During writing** (Step 4):
- Keep skill rules in mind
- Write to pass validation first time
- Don't rely on skills to catch everything

**After writing** (Step 5):
- Run all relevant skills
- Fix any issues immediately
- Re-run until all pass

### Skills prevent these common mistakes

**css-standards prevents**:
- Using hex colors instead of hsl()
- Saying "CSS variable" instead of "CSS custom property"
- Missing `prefers-reduced-motion` queries
- Incorrect color format documentation

**hap-voice prevents**:
- Using "you should" (instructional voice)
- Using "we will" (not apprentice perspective)
- Generic tutorial voice
- Missing Prof. Teeters references

**station-content prevents**:
- Missing required sections
- Wrong section order
- Wrong number of insight cards (must be exactly 3)
- Missing copy button JavaScript

**accessibility-check prevents**:
- Heading hierarchy violations
- Missing alt text
- Missing ARIA labels
- Missing keyboard navigation support

---

## Critical rules enforced by this workflow

### Content rules
- ✅ All content comes from outline files in reports/
- ✅ HAP's voice is first-person apprentice throughout
- ✅ Prof. Teeters is referenced as mentor
- ✅ Every station has exactly 6 main sections
- ✅ Every station has exactly 3 insight cards

### Accessibility rules
- ✅ Every animation has `prefers-reduced-motion` support
- ✅ Heading hierarchy is correct (no skipping levels)
- ✅ All images have alt text, width, height
- ✅ All interactive elements are keyboard accessible
- ✅ Multiple cues for important information (not animation alone)

### Performance rules
- ✅ Only animate `transform` and `opacity`
- ❌ Never animate width, height, margin, padding, position
- ❌ Never use `transition: all`
- ✅ All colors in hsl() format
- ✅ Images have loading="lazy" except LCP image

### Animation-specific rules
- ✅ Micro means micro: 2-5% scale, 5-10px movement
- ✅ Duration: 150-300ms for UI interactions
- ✅ Timing: ease-out for 95% of interactions
- ✅ No flashing more than 3 times per second
- ✅ Infinite loops need pause controls OR reduced motion alternative

### CSS and JavaScript rules
- ❌ **NO `<style>` tags in HTML files**
- ❌ **NO inline styles (style="...") in HTML unless explicit permission granted**
- ✅ All CSS goes in `css/style.css` OR separate CSS file in `css/` folder
- ✅ If demo-specific CSS needed, create `css/demos.css` or similar
- ✅ Use CSS classes instead of inline styles
- ✅ JavaScript for demos CAN be inline in `<script>` tags
- ✅ Link additional CSS files in `<head>` after `style.css`

**Why no inline styles?**
- Maintainability: Changes require editing HTML instead of CSS
- Consistency: Harder to maintain design system
- Performance: Can't be cached separately
- Specificity: Inline styles override everything
- **Only exception**: User grants explicit permission for specific use case

---

## Why this workflow matters

### Prevents rework
- Planning before coding reduces mistakes
- Skill validation catches issues early
- Approval process ensures alignment

### Ensures quality
- Implementation plans force thorough thinking
- Skills enforce standards automatically
- Manual testing catches edge cases

### Maintains consistency
- Same workflow for all 7 files
- Same quality gates for each
- Predictable, repeatable process

### Documents decisions
- Implementation plans explain reasoning
- Skill validation provides audit trail
- Clear record of what was done and why

---

## Checklist for each HTML file

Before considering a file "complete":

- [ ] Implementation plan created and approved
- [ ] Relevant skills reviewed before writing
- [ ] HTML file written following plan
- [ ] `hap-voice` skill validation passed
- [ ] `station-content` skill validation passed
- [ ] `css-standards` skill validation passed
- [ ] `accessibility-check` skill validation passed
- [ ] Other relevant skills validated
- [ ] All skill feedback addressed
- [ ] Manual browser testing completed
- [ ] `prefers-reduced-motion` tested with DevTools
- [ ] Interactive elements tested
- [ ] Keyboard navigation tested
- [ ] File marked complete in tracking

---

## Emergency exceptions

**When can you skip steps?**

**Never skip**:
- Implementation plan (Step 1)
- User approval (Step 2)
- Post-writing skill validation (Step 5)

**Can compress if user explicitly authorizes**:
- Pre-writing skill review (Step 3) - if very familiar with requirements
- Some manual testing (Step 7) - if extremely simple page

**Ask user permission before skipping any step.**

---

## Summary: The golden rule

**PLAN → APPROVE → REVIEW SKILLS → WRITE → VALIDATE → TEST → COMPLETE**

Never write HTML without an approved implementation plan.
Never consider HTML complete without skill validation.

This workflow exists because:
- It saves time (less rework)
- It ensures quality (fewer mistakes)
- It maintains standards (consistent output)
- It documents decisions (clear reasoning)

**Follow this workflow for every HTML file.**

---

*This workflow document must be read before starting any HTML file implementation.*

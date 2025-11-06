# HAP Learning Lab content generation prompt v3

Use this prompt with any generative AI to create structural outlines for a new HAP Learning Lab. The AI will generate detailed blueprints that describe what content will teach, which Claude Code will then use to build the hub page and all 6 stations.

---

## CRITICAL: You are generating STRUCTURAL OUTLINES

**This prompt generates detailed structural outlines that describe WHAT will be taught, NOT the actual teaching content.**

Think of this as creating a blueprint. You are describing:
- What HAP's stories will be about (not writing the stories)
- What Prof. Teeters will teach (not writing the lessons)
- What code examples will show (not writing the code)
- What sections will contain (not writing the content)

**Correct outline style:**
> "HAP's struggle with cascade specificity
> - Trying to override inherited styles
> - Using !important incorrectly
> - Prof. Teeters explaining specificity hierarchy
> - HAP's aha moment when he understood the cascade"

**Incorrect outline style (too much content):**
> "I was so confused when my styles wouldn't apply! I kept adding !important everywhere, which Prof. Teeters said was like using a sledgehammer. She taught me about the specificity hierarchy..."

**Remember: Describe the blueprint, don't write the content.**

---

## The prompt

I need you to create detailed STRUCTURAL OUTLINES for a HAP Learning Lab on **[YOUR TOPIC HERE]**. These outlines will be used to build an educational website where HyBit A. ProtoBot™ (HAP™), Prof. Teeters' robot apprentice, teaches students through his first-person learning journey.

### About HAP's voice

HAP is Prof. Teeters' apprentice who is learning **[YOUR TOPIC]** alongside students. He always speaks in first-person, references Prof. Teeters as his mentor, shares his mistakes and struggles, and makes complex topics relatable through his authentic learning journey.

**Critical voice requirements:**
- HAP uses "I", "me", "my" (not "you" or "we")
- HAP references Prof. Teeters frequently ("Prof. Teeters showed me...", "When Prof. Teeters corrected me...")
- HAP shares specific struggles and mistakes he made
- HAP is humble, enthusiastic, and relatable
- HAP never uses instructional language ("you should", "let's do this")

---

## CRITICAL PROJECT RULES

These rules are NON-NEGOTIABLE and apply to every outline you generate. Violating these rules will result in rejection.

### Technical Requirements

**CSS Color Format:**
- ✅ ALWAYS use HSL format: `hsl(220, 80%, 50%)`
- ❌ NEVER use hex: `#3b82f6`
- ❌ NEVER use RGB: `rgb(59, 130, 246)`
- When describing colors, specify "hsl() format" not "hex" or "rgb"

**CSS Terminology:**
- ✅ CORRECT: "CSS custom property"
- ❌ FORBIDDEN: "CSS variable" - this is incorrect terminology

**No JavaScript:**
- This is for no-JavaScript courses
- ❌ Do not include JavaScript teaching
- ❌ Do not suggest JavaScript solutions
- ✅ Pure CSS solutions only
- Note: Station 6 may mention AI can generate JS, but focus remains on CSS

**Performance Requirements:**
- ✅ Animations must use transform and opacity (GPU-accelerated)
- ❌ Do not animate: colors, box-shadow, width, height, margin, padding, position
- Reason: CPU-bound properties cause mobile performance issues
- Always describe using "GPU-accelerated properties" or "transform and opacity only"

### Safety Requirements (WCAG Compliance)

**Seizure Prevention (WCAG 2.3.1):**
- ❌ NEVER describe flashing/flickering more than 3 times per second
- Applies to: color changes, opacity changes, visibility toggles
- This can cause seizures in people with photosensitive epilepsy
- Always describe safe alternatives: fade-ins, gentle pulses, smooth transitions

**Accessibility Compliance:**
- ✅ Every animation example MUST include prefers-reduced-motion alternative
- ✅ Describe static alternatives that preserve functionality
- ✅ No auto-playing looping animations without pause controls
- ✅ WCAG 2.2 Level AA: 4.5:1 contrast minimum for text
- Describe how users maintain control over motion

**Micro-Interaction Limits:**
- ✅ 2-5% scale changes maximum
- ✅ 5-10 pixel movements maximum
- ✅ 150-300 millisecond durations for UI animations
- ❌ No large sweeping movements (vestibular disorder concerns)
- Describe "subtle" and "micro" movements, not dramatic ones

### Testing and Tools Requirements

**Accessibility Testing:**
- ✅ ALWAYS describe using Chrome DevTools to emulate prefers-reduced-motion
- ❌ NEVER suggest changing system settings
- ❌ NEVER suggest changing OS settings
- Reason: DevTools is faster and smoother workflow
- Correct phrasing: "Use Chrome DevTools rendering panel to emulate prefers-reduced-motion"

**Browser and OS References:**
- ❌ Do NOT discuss operating systems unless explicitly asked
- ❌ Do NOT discuss specific browsers unless explicitly asked
- ✅ Use generic "browser" when needed
- Exception: Chrome DevTools for accessibility testing is allowed

**Device Testing:**
- ✅ Describe testing on mobile devices
- ✅ Mention budget phones for performance testing
- ❌ Do not specify OS (iOS vs Android) unless asked

### Content and Voice Requirements

**HAP's Voice:**
- ✅ ALWAYS first-person: "I", "me", "my"
- ❌ NEVER instructional: "you should", "let's", "we can"
- ✅ Prof. Teeters referenced frequently (10+ times per station)
- ✅ Specific mistakes and struggles detailed
- ✅ Humble, enthusiastic, relatable

**Scope Limits:**
- ✅ 3-4 core patterns per station MAXIMUM
- ❌ No comprehensive coverage that overwhelms
- ✅ Focus on reusable library, not every variation
- ✅ Appropriate depth: confident use, not expert-level

**Modern Patterns Only:**
- ❌ No Material Design (2014)
- ❌ No Bootstrap default patterns
- ❌ No outdated design systems
- ✅ Current 2024-2025 best practices
- ❌ No Bento grids (reserved for separate Layout Learning Lab)

### Outline Format Requirements

**Text-Only Descriptions:**
- ❌ NO code examples (describe what code will show)
- ❌ NO emojis (describe where they'll appear)
- ❌ NO code blocks with backticks
- ❌ NO inline code snippets
- ✅ Describe in plain text only

**Structure Consistency:**
- Stations 1-5: Exactly 7 sections each
- Station 6: Exactly 12 sections
- Section order must be consistent
- Section titles must match specified format

---

### CRITICAL: TEXT ONLY - NO CODE, NO EMOJIS

**You are generating TEXT-ONLY DESCRIPTIONS, not actual content.**

**Absolutely forbidden in your response:**
- ❌ NO code examples (CSS, HTML, JavaScript, or any code)
- ❌ NO emojis of any kind
- ❌ NO code blocks with backticks
- ❌ NO inline code snippets
- ❌ NO syntax examples
- ❌ NO actual CSS properties or values

**Instead, DESCRIBE what code will show:**

**WRONG (contains code):**
```css
.box {
  transform: translateX(100px);
}
```

**CORRECT (describes code):**
"Code example showing transform property using translateX to move element 100 pixels right"

**WRONG (contains emoji):**
"🟠 HAP's tip: Always test in multiple browsers"

**CORRECT (describes emoji placement):**
"HAP Note Callout (with HAP orange circle emoji) containing browser testing tip"

**WRONG (contains inline code):**
"HAP learned to use `transition: all 0.3s ease`"

**CORRECT (describes what will be shown):**
"HAP learned to use the transition property with 0.3s duration and ease timing function"

**If you include ANY code or emojis, your response will be rejected.**

---

### CRITICAL SCOPE RULES

**These rules prevent overwhelming content and maintain focus:**

- Focus on **3-4 core patterns**, not comprehensive coverage
- Build a **small reusable library**, not every possible variation
- **Appropriate depth**: explain enough to use confidently, not expert-level detail
- **Station length should be consistent** (check against other stations)
- **When in doubt, cut content** rather than overwhelm students

**Examples:**

**Station 4 (combining techniques):**
- ❌ WRONG: Teach 10 different button animation patterns
- ✅ CORRECT: Teach 2-3 essential button patterns well

**Station 5 (advanced/production):**
- ❌ WRONG: Cover every possible keyframes variation
- ✅ CORRECT: Focus on entrance, exit, and attention animations

**Station 2 (core concept):**
- ❌ WRONG: Explain every CSS property related to topic
- ✅ CORRECT: Focus on properties that matter most for common use cases

**Remember: Students learn better with focused examples than comprehensive encyclopedias.**

---

## What I need from you

Generate structural outlines in this exact structure:

---

## 1. Hub page outline

### Main heading

[Create engaging title for the Learning Lab]

### Introduction paragraph

[Describe HAP's introduction - why he got excited about learning this topic, 3-4 sentences in first-person voice]

### Why this topic matters

[Describe HAP explaining why Prof. Teeters said this topic is important, 2-3 sentences]

### Station descriptions

For each of stations 1-5, provide:
- **Station title**: [Clear, specific title]
- **One-sentence description**: [What HAP learned in this station]
- **Key concept**: [Main takeaway]

---

## 2. Stations 1-5: Standard Structure (7 sections recommended)

**Default structure**: Use this 7-section structure unless your topic genuinely requires different organization.

All Stations 1-5 follow this structure with integrated storytelling.

### Section 1: What You'll Learn

**HAP's Discovery Story:**
[Describe HAP's initial encounter with the topic - 3-4 sentences about specific problem/confusion that led him to learn this]

**Three Insight Cards:**
- Card 1: [Describe first key insight]
- Card 2: [Describe second key insight]
- Card 3: [Describe third key insight]

**HAP Note Callout:**
[Describe HAP's confession about early mistakes with this topic - relatable struggle]

### Sections 2-4: Main Content (3-4 concept sections)

For each major concept (3-4 concepts per station maximum per scope rules):

**Section Title:** [Name of concept being taught]

**Content structure for each main content section:**

Describe how the section will be structured:
- Core concept explanation
- HAP's initial attempts and mistakes (woven into teaching, not separate)
- Prof. Teeters' corrections and guidance (woven into teaching, not separate)
- Code examples that will be shown (describe what they demonstrate)
- Interactive demonstrations (describe what students can manipulate)
- HAP's insights and aha moments (woven throughout)
- Wrong way vs right way comparisons
- Common pitfalls HAP encountered

**CRITICAL NOTE:** Do NOT create separate "HAP struggled" and "Prof. Teeters taught" sections. Weave the narrative throughout the concept teaching. HAP's story and Prof. Teeters' guidance are integrated into each concept section.

**Example of integrated storytelling:**
> "Section 2: Translate and Scale
> - Describe explaining translate function for moving elements
> - Describe HAP's story about trying to move button with margin changes (woven in)
> - Describe Prof. Teeters showing why transform is better for performance (woven in)
> - Describe code examples showing translateX, translateY, translate shorthand
> - Describe HAP's aha moment when he saw 60fps animation vs janky margin animation
> - Describe scale function for size changes
> - Describe HAP's mistake using percentage scale (too dramatic)
> - Describe Prof. Teeters' guidance on micro-interactions (2-5% scale changes)
> - Describe code examples with subtle scale hover effects"

### Section 5: Try It Yourself Exercise

[Describe 1-2 hands-on challenges with clear requirements and success criteria]

### Section 6: Quick Reference Tips (exactly 4 numbered tips)

- Tip 1: [Describe first essential tip]
- Tip 2: [Describe second essential tip]
- Tip 3: [Describe third essential tip]
- Tip 4: [Describe fourth essential tip]

**CRITICAL:** Must be exactly 4 tips, not more, not less.

### Section 7: Learning Objectives Checklist

[Describe checklist items - what students should confidently be able to do after completing this station]

---

### When to deviate from 7-section structure

**The 7-section structure is recommended for most topics.** Use it unless your content genuinely requires different organization.

**You may modify the structure if**:
- Topic genuinely requires more/fewer main content sections (Sections 2-4)
- Pedagogical approach demands different organization
- Content doesn't fit standard pattern due to topic complexity

**If deviating, you MUST**:
1. **Explain why** 7 sections don't work for this specific topic
2. **Propose alternative** structure with clear rationale
3. **Maintain required elements** (see below)

**Example justified deviation**:

> "Station 4 requires 5 main content sections instead of 3-4 because this topic
> has 5 distinct transform functions (translate, rotate, scale, skew, matrix)
> that each need dedicated explanation with examples. Combining them would create confusion.
>
> Modified structure (9 sections total):
> - Section 1: What You'll Learn (Discovery + 3 Insights + HAP Note)
> - Sections 2-6: Five transform functions (5 main content sections)
> - Section 7: Try It Yourself Exercise
> - Section 8: Quick Reference (exactly 4 tips)
> - Section 9: Learning Objectives Checklist"

### Non-negotiable elements

**Regardless of section count, these are REQUIRED in all Stations 1-5:**

✅ **Section 1 format** (always first):
- HAP's Discovery Story
- Three Insight Cards
- HAP Note Callout

✅ **Try It Yourself section** (placement flexible if deviating):
- Hands-on challenges
- Success criteria
- HAP's encouragement

✅ **Quick Reference Tips** (placement flexible if deviating):
- Exactly 4 numbered tips (not more, not less)

✅ **Learning Objectives Checklist** (always last):
- Self-assessment checklist items

✅ **Integrated storytelling**:
- HAP's struggles woven throughout content sections
- Not separate "HAP struggled" / "Prof. Teeters taught" sections

✅ **HAP's first-person voice**:
- Throughout all sections

---

### Code examples pattern

**All code examples must follow the "Old Way vs What I Learned" pattern:**

Describe code examples showing:
1. **HAP's old incorrect approach** with description of mistake
2. **Correct approach** with explanation of why it's better
3. **Key difference** highlighted (performance, accessibility, etc.)
4. **HAP's learning moment** when it clicked

**Example outline description**:
> "Code example: HAP's old way using margin-left for movement (causes layout reflow, janky on mobile),
> then correct approach using transform: translateX() (GPU-accelerated, smooth 60fps).
> Key difference: Prof. Teeters showed HAP the performance timeline in DevTools -
> margin animation caused 200ms of layout work, transform was 2ms. That's when HAP
> understood why transform matters for mobile users."

**Implementation note** (for developer building from these outlines):
> The HTML structure for "Old Way vs What I Learned" code comparisons is provided in
> `templates/station-template.html` lines 154-167.

---

### 📋 Implementation Note

**For developer building stations from these outlines:**

When implementing the content described in these structural outlines, use:
- **`templates/station-template.html`** for HTML structure and components
- **`templates/demo-template.html`** for interactive demonstrations
- **`templates/hybit-insights-template.json`** for easter egg system

These templates provide the HTML/CSS/JSON structure to implement the text
descriptions from your outlines. The templates include:
- Required safety comments (seizure prevention, GPU properties)
- Performance optimization patterns
- Accessibility features (ARIA, skip links, screen reader support)
- HAP voice patterns and components

**This note is for the human implementer, not part of the outline generation.**

---

## 3. Station 1: [Title]

[Follow 7-section structure above]

**Section 1:** What You'll Learn (Discovery Story + 3 Insight Cards + HAP Note Callout)
**Sections 2-4:** Main Content (3-4 concept sections with integrated storytelling)
**Section 5:** Try It Yourself Exercise
**Section 6:** Quick Reference Tips (exactly 4)
**Section 7:** Learning Objectives Checklist

---

## 4. Station 2: [Title]

[Follow same 7-section structure as Station 1]

---

## 5. Station 3: [Title]

[Follow same 7-section structure as Station 1]

---

## 6. Station 4: [Title]

[Follow same 7-section structure as Station 1]

---

## 7. Station 5: [Title]

[Follow same 7-section structure as Station 1]

---

## 8. Station 6: AI Assistance for [Topic]

**CRITICAL**: Station 6 is ALWAYS about AI assistance for the specific topic being taught.

Station 6 follows a different structure with **12 required sections**:

### Section 1: What You'll Learn (HAP Note Callout)

[Describe HAP Note Callout explaining what students will learn about using AI for this topic]

### Section 2: What AI Can and Can't Do

**Outline comparison grid showing:**
- What AI is excellent at for this topic
- What AI struggles with for this topic
- What AI cannot do for this topic

### Section 3: [Creating Basic Animations] with AI

**Task pattern: Most common use case**

Choose the most frequent task students will do for this topic.

**Examples by topic:**
- CSS Animations: "Creating Button Hover Animations with AI"
- CSS Forms: "Generating Form Validation Markup with AI"
- CSS Layouts: "Building Grid Layouts with AI"

**Outline this section:**
- HAP's initial prompts for this common task
- What went wrong with early attempts
- Prof. Teeters' improvements to prompting approach
- Describe working example progression

### Section 4: [Complex Sequences] with AI

**Task pattern: More sophisticated technique**

Choose a multi-step or complex task that builds on Section 3.

**Examples by topic:**
- CSS Animations: "Generating Keyframes Animations with AI"
- CSS Forms: "Creating Multi-Step Form Flows with AI"
- CSS Layouts: "Designing Responsive Navigation Patterns with AI"

**Outline this section:**
- HAP's struggles with this specific task type
- Describe effective prompt patterns discovered
- Describe what to watch out for with AI for this task
- How complexity requires more specific prompting

### Section 5: [Critical Requirement] with AI

**Task pattern: Accessibility, semantics, or best practices**

ALWAYS focus on what AI often gets wrong - typically accessibility or semantic concerns.

**Examples by topic:**
- CSS Animations: "AI for Animation Accessibility"
- CSS Forms: "AI for Accessible Form Labels"
- CSS Layouts: "AI for Semantic Landmark Structure"

**Outline this section:**
- Why this task is critical (user harm if done wrong)
- How AI helps (and where it fails)
- Describe HAP's verification process
- Prof. Teeters' guidance on never trusting AI blindly for accessibility

### Section 6: [Performance/Production] with AI

**Task pattern: Optimization or real-world deployment**

Choose task related to performance, browser compatibility, or production readiness.

**Examples by topic:**
- CSS Animations: "Optimizing Animation Performance with AI"
- CSS Forms: "Form Validation Patterns with AI"
- CSS Layouts: "Mobile-First Responsive Patterns with AI"

**Outline this section:**
- Performance considerations for this topic
- Describe how to prompt for performance
- Describe testing AI suggestions (DevTools, mobile devices)
- Common performance mistakes AI makes

### Section 7: Try It Yourself

[Describe 2-3 AI prompt experiments students can try with clear success criteria]

### Section 8: HAP's Rules for AI Assistance

**Outline exactly 6 numbered rules in card format:**

Each rule should be:
- Specific to this topic
- Based on HAP's mistakes and learnings
- Actionable guidance

Describe what each rule covers (don't write the actual rule text):
- Rule 1: [Describe what this rule covers]
- Rule 2: [Describe what this rule covers]
- Rule 3: [Describe what this rule covers]
- Rule 4: [Describe what this rule covers]
- Rule 5: [Describe what this rule covers]
- Rule 6: [Describe what this rule covers]

**CRITICAL:** Must be exactly 6 rules, not more, not less.

### Section 9: Advanced Prompt Strategies

**Outline three subsections:**

**Iteration techniques:**
[Describe refining prompts approach - how HAP learned to improve prompts systematically]

**Troubleshooting when AI gives wrong answers:**
[Describe HAP's troubleshooting process - how to identify and fix AI mistakes]

**Safety checks before using AI code:**
[Describe verification steps - accessibility, performance, semantics]

### Section 10: When NOT to Use AI

**Outline this section:**
- Describe specific scenarios where AI isn't appropriate for this topic
- Describe HAP's stories about over-relying on AI and getting stuck
- Describe Prof. Teeters' guidance on developing own skills first
- When manual coding is faster/better than prompting

### Section 11: Quick Reference Grid

[Describe task-by-task AI suitability ratings - outline quick decision matrix showing which tasks are good/bad for AI assistance]

### Section 12: Learning Objectives Checklist

[Describe checklist items - what students should be able to do with AI for this topic]

---

## 9. Effective prompting examples for Station 6

**Provide exactly 6 prompt examples showing clear progression from poor to excellent.**

**Each example must show clear progression:**
- Example 1 → Example 2: Add specificity about task
- Example 2 → Example 3: Add technical constraints (performance, GPU properties)
- Example 3 → Example 4: Add accessibility requirements (prefers-reduced-motion, semantics)
- Example 4 → Example 5: Add performance/quality requirements (specific values, best practices)
- Example 5 → Example 6: Add context and advanced constraints (edge cases, browser support)

**Each lesson must build on previous:**
- Example 2's lesson should reference Example 1's lesson
- Example 3's lesson should reference Examples 1-2's lessons
- And so on...

For each example, outline:

### Example 1: Too Vague (shows baseline problem)

- **HAP's prompt**: [Describe vague, generic prompt]
- **What went wrong**: [Describe why this didn't help]
- **Prof. Teeters' feedback**: [Describe specific issue to address]
- **Key lesson**: [Describe one thing to improve - specificity]

### Example 2: Better But Still Issues (shows common improvement mistake)

- **HAP's prompt**: [Describe improved but still flawed prompt - added task specificity]
- **What went wrong**: [Describe remaining issues - missing technical constraints]
- **Prof. Teeters' feedback**: [Describe next improvement needed - add technical details]
- **Key lesson**: [Describe building on Example 1 lesson - specificity + technical constraints]

### Example 3: Getting Closer (shows right direction)

- **HAP's prompt**: [Describe more specific prompt with technical constraints - now adding accessibility]
- **What went wrong**: [Describe minor issues remaining - missing accessibility requirements]
- **Prof. Teeters' feedback**: [Describe fine-tuning needed - prefers-reduced-motion, semantics]
- **Key lesson**: [Describe building on Examples 1-2 - specificity + technical + accessibility]

### Example 4: Much Better (shows near-success)

- **HAP's prompt**: [Describe well-structured prompt with accessibility - now adding performance/quality]
- **Why this mostly worked**: [Describe what improved - covers task, technical, accessibility]
- **Prof. Teeters' feedback**: [Describe small refinements - add specific values, best practices]
- **Key lesson**: [Describe building on Examples 1-3 - adding quality/performance requirements]

### Example 5: Excellent (shows target quality)

- **HAP's prompt**: [Describe high-quality prompt with context and constraints]
- **Why this worked**: [Describe what made it effective - comprehensive, specific, safe]
- **Result**: [Describe what HAP learned/received - usable code that needed minimal edits]
- **Key lesson**: [Describe what makes this prompt excellent - complete requirements upfront]

### Example 6: Advanced Context (shows mastery level)

- **HAP's prompt**: [Describe sophisticated prompt with edge cases, browser support, advanced constraints]
- **Why this is advanced**: [Describe additional sophistication - anticipates problems, provides context]
- **Result**: [Describe high-quality, nuanced assistance - production-ready code]
- **Key lesson**: [Describe mastery-level prompting technique - proactive problem-solving]

**CRITICAL**: Each example must build on lessons from previous examples, showing clear progression in HAP's understanding.

---

## 10. Learning structure

Choose the approach that best fits your topic:

### Progressive structure (for dependent concepts)

Use this if your topic has natural dependencies where concepts must build on each other (e.g., HTML fundamentals, JavaScript basics, database design).

Show how concepts build across stations:
- **Station 1** teaches: [Describe foundation concept]
- **Station 2** builds on Station 1 by: [Describe next concept]
- **Station 3** builds on Stations 1-2 by: [Describe advanced concept]
- **Station 4** builds on Stations 1-3 by: [Describe complex application]
- **Station 5** builds on Stations 1-4 by: [Describe integration/mastery]
- **Station 6** teaches: AI assistance for all concepts from Stations 1-5

**HAP's journey**: Describe how each station shows HAP struggling with the new concept until he applies what he learned previously.

### Modular structure (for independent concepts)

Use this if your topic contains independent concepts that can be learned in any order (e.g., CSS transforms vs transitions vs animations, different testing frameworks, various design patterns).

Show HAP's learning sequence with rationale:
- **Station 1** teaches: [Describe Concept A - standalone skill]
- **Station 2** teaches: [Describe Concept B - standalone skill]
- **Station 3** teaches: [Describe Concept C - standalone skill]
- **Station 4** teaches: [Describe integration/combination of concepts A+B+C]
- **Station 5** teaches: [Describe advanced applications, performance, or production best practices]
- **Station 6** teaches: AI assistance for all concepts from Stations 1-5

**HAP's journey**: Describe why Prof. Teeters chose this particular order for HAP's learning, even though the concepts are independent. (Example: "Prof. Teeters had me start with transforms because our first project needed positioned elements, but she said I could have learned transitions first if I wanted.")

### Station 6 (always the same)

Regardless of progressive or modular structure, **Station 6 is always about AI assistance** for the specific topic, covering all concepts from Stations 1-5.

---

## 11. Easter egg parameters

Define 8-12 easter egg parameters that reveal additional insights when students add `?hybit=[parameter]` to URLs.

For each parameter, provide:
- **Parameter name**: [One word, lowercase]
- **Which station**: [Where this appears]
- **Insight type**: [Behind-the-scenes struggle / Prof. Teeters' wisdom / Advanced tip]
- **Message outline**: [Describe 2-3 sentences in HAP's voice revealing something extra - don't write actual message]

Example format:

Parameter: detail
Station: Station 1
Type: Behind-the-scenes struggle
Message outline: "Describe HAP mentioning when he first tried specific thing, completely missed specific detail, Prof. Teeters had to show him three times before he noticed, lesson about small details making big difference"

---

## 12. Interactive demo ideas

For each station 1-5, suggest 1-2 interactive demos where students can:
- Manipulate values and see results
- Test different approaches
- Experiment safely

For each demo, provide:
- **Demo name**
- **Purpose**: [Describe what concept it teaches]
- **Interaction**: [Describe what students manipulate - sliders, inputs, toggles]
- **Feedback**: [Describe what students see/learn from results - live preview, metrics]
- **HAP's commentary**: [Describe what HAP learned from trying different values]

---

## 13. Common student mistakes (based on HAP's experience)

For each station, list 3-4 mistakes HAP made that students will likely make too:
- **Mistake**: [Describe what HAP did wrong]
- **Why it's tempting**: [Describe why this seems right]
- **What went wrong**: [Describe specific result/error]
- **Prof. Teeters' explanation**: [Describe why this doesn't work]
- **Correct approach**: [Describe what to do instead]

---

## 14. Key terminology

List 10-15 key terms for this topic:
- **Term**: [Exact term to use]
- **Definition**: [Clear, simple definition]
- **Why this term**: [If there are similar terms, why this one is correct]
- **HAP's memory trick**: [Describe how HAP remembers this term]

Example:

Term: CSS custom property
Definition: A CSS entity defined with -- prefix that holds values you can reuse
Why this term: NOT "CSS variable" - that's incorrect terminology. The spec calls them "custom properties"
HAP's memory trick: "Describe HAP remembering it's CUSTOM property because he CUSTOMIZES it for his project, like Prof. Teeters customized his learning plan."

---

## Format requirements

**Please format your response with:**
- Clear markdown headings (## for major sections, ### for subsections)
- Bullet lists using - (not * or +)
- TEXT ONLY descriptions (NO code, NO emojis)
- Consistent first-person voice throughout all HAP content descriptions
- Specific, concrete examples (not generic placeholders)
- Prof. Teeters' name mentioned frequently in HAP's narrative

**CRITICAL REMINDERS:**
- Describe what code will show, don't write code
- Describe where emojis will appear, don't use emojis
- Use correct terminology (CSS custom property, hsl() format, HTML element)
- Follow scope rules: 3-4 patterns maximum per station
- Keep station length consistent
- Stations 1-5: Exactly 7 sections with integrated storytelling
- Station 6: Exactly 12 sections with task patterns
- Quick Reference Tips: Exactly 4 tips
- HAP's Rules: Exactly 6 rules

---

## Quality checklist

Before submitting your outlines, verify:

### TEXT ONLY requirements (CRITICAL)

- [ ] ZERO code examples anywhere in response (no CSS, HTML, JavaScript, etc.)
- [ ] ZERO emojis anywhere in response
- [ ] ZERO code blocks with backticks
- [ ] ZERO inline code snippets with backticks
- [ ] All code is DESCRIBED in plain text only
- [ ] All emoji placements are DESCRIBED in plain text only

### Project rules compliance (CRITICAL)

- [ ] All colors use hsl() format described (NEVER hex or rgb)
- [ ] "CSS custom property" used (NEVER "CSS variable")
- [ ] No JavaScript teaching (pure CSS solutions only)
- [ ] Transform and opacity only for animations (GPU-accelerated, performance rule)
- [ ] Seizure safety followed (no >3 flashes/second)
- [ ] Micro-interaction limits followed (2-5% scale, 5-10px movement, 150-300ms duration)
- [ ] Chrome DevTools described for accessibility testing (NEVER system settings)
- [ ] No OS or browser discussion unless asked
- [ ] Modern patterns only (no Material Design 2014, no Bootstrap defaults, no Bento grids)

### Scope requirements

- [ ] Each station focuses on 3-4 core patterns (not comprehensive coverage)
- [ ] Appropriate depth (confident use, not expert-level)
- [ ] No overwhelming content or excessive variations
- [ ] Station length is consistent across all stations

### Structure requirements (CRITICAL)

- [ ] Stations 1-5 use 7-section structure (OR justified deviation with explanation and rationale)
- [ ] If deviating from 7 sections: all required elements maintained (Section 1 format, Try It Yourself, 4 Tips, Learning Objectives)
- [ ] Station 6 uses required 12-section structure
- [ ] Section order is consistent across stations (unless deviation justified)
- [ ] Sections 2-4 in Stations 1-5 have integrated storytelling (not separate struggle/teaching sections)
- [ ] Quick Reference has exactly 4 numbered tips (not more, not less)
- [ ] Section 8 in Station 6 has exactly 6 numbered rules (not more, not less)
- [ ] Station 6 sections 3-6 follow task patterns (common → complex → critical → performance)
- [ ] Code examples follow "Old Way vs What I Learned" pattern
- [ ] Progressive OR modular structure clearly defined with rationale

### HAP voice requirements

- [ ] Every section description uses HAP's first-person voice consistently
- [ ] Prof. Teeters is referenced frequently (10+ times per station)
- [ ] Specific struggles and mistakes are detailed (not generic)
- [ ] "Aha!" moments are concrete and relatable
- [ ] No instructional language ("you should", "let's", "we can")

### Accessibility requirements (CRITICAL)

- [ ] Every animation example includes prefers-reduced-motion alternative
- [ ] Static alternatives preserve functionality
- [ ] Text contrast meets WCAG 2.2 Level AA (4.5:1 minimum)
- [ ] No auto-playing looping animations without pause controls
- [ ] Users maintain control over motion

### Content requirements

- [ ] Learning structure is clear (progressive with dependencies OR modular with rationale)
- [ ] Station 6 focuses entirely on AI assistance for this specific topic
- [ ] Station 6 includes exactly 6 prompt examples showing progression
- [ ] Each prompt example builds on lessons from previous examples
- [ ] Prompt progression follows pattern: task specificity → technical → accessibility → performance → context
- [ ] Easter egg parameters align with station content
- [ ] Interactive demo ideas are specific and teaching-focused
- [ ] Common mistakes are detailed and authentic

### Outline format requirements

- [ ] Outlines DESCRIBE content, don't write it
- [ ] Each section outlines structure clearly
- [ ] No prose content (only structural descriptions)
- [ ] Clear what will be covered in each section

**If ANY code or emojis appear in your response, it will be REJECTED.**

**If ANY safety rules are violated (flashing >3/second, no prefers-reduced-motion, large movements), it will be REJECTED.**

---

## Example of excellent outline description

**Good outline description (describes content with integrated storytelling):**
> "Section 2: Translate and Scale
>
> Describe this section structure:
> - Explain translate function for moving elements on screen
> - Weave in HAP's story about trying to move button with margin changes causing layout reflow
> - Weave in Prof. Teeters showing why transform is better (GPU-accelerated, no reflow)
> - Describe code examples showing translateX, translateY, translate shorthand with pixel values
> - Describe HAP's aha moment when he saw 60fps transform animation vs janky margin animation
> - Explain scale function for size changes
> - Weave in HAP's mistake using scale(1.5) causing button to double in size (too dramatic)
> - Weave in Prof. Teeters' guidance on micro-interactions (1.02 to 1.05 scale, not 1.5)
> - Describe code examples with subtle scale hover effects
> - Describe interactive demo where students adjust scale values and see results"

**Poor outline description (writes actual content):**
> "I was so frustrated when my button animation was janky! I had tried using margin to move it around, and Prof. Teeters came over and asked, 'Have you tried transform?' I didn't know what she meant..."

**Good outline description (describes Station 6 task):**
> "Section 3: Creating Button Hover Animations with AI
>
> Describe this section:
> - HAP's initial vague prompt: 'make a button hover effect'
> - Result: AI gave generic code without performance considerations
> - Prof. Teeters' improvement: 'Create a button hover effect using transform and opacity only, with 150ms duration and ease timing, that scales to 1.03 on hover'
> - Result: AI gave GPU-accelerated code with specific values
> - HAP's learning: Be specific about properties, values, and constraints"

**Poor outline description (tries to write prompts):**
> "HAP should ask AI: 'Create a button hover animation using transform scale 1.03 with 150ms ease timing that's GPU-accelerated'"

---

**Now, please generate complete STRUCTURAL OUTLINES for a HAP Learning Lab on [YOUR TOPIC], following all the requirements above.**

**Remember: You are creating a BLUEPRINT that describes what will be taught. Do not write the actual teaching content.**

**Double-check PROJECT RULES before submitting - safety requirements are non-negotiable.**

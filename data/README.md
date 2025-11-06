# HAP Insights easter egg system

## What is this?

HAP Insights is an educational "easter egg" feature that lets you add hidden tips and messages to your learning lab. When students add special codes to the URL (like `?hybit=detail`), HAP appears with helpful insights.

**Example**:
- Normal URL: `http://localhost:5500/index.html`
- With easter egg: `http://localhost:5500/index.html?hybit=detail`
- Result: HAP's dialog appears with extra information!

## Quick start

### Step 1: Choose your format

**Option A: JSON (simpler, no comments)**
- Use `hybit-insights-template.json` as starting point
- Copy to `hybit-insights.json` in your project
- Edit with any text editor
- Can't include comments (JSON limitation)

**Option B: JSONC (with comments)**
- Use `hybit-insights-template.jsonc` as starting point
- Copy to `hybit-insights.jsonc` in your project
- Can include `//` comments for documentation
- Requires comment-stripping JavaScript (already included)

**Recommendation**: Start with JSON (simpler). Switch to JSONC later if you want inline documentation.

### Step 2: Add your first parameter

Open your `hybit-insights.json` file and add a parameter:

```json
{
  "allowedParams": [
    "detail",
    "mytip"        ← Add your parameter name here
  ],
  "messages": {
    "detail": { ... },
    "mytip": {     ← Define what it shows
      "title": "🟠 HAP's Pro Tip",
      "content": "Here's something I learned from Prof. Teeters: <strong>Always test on mobile first!</strong>"
    }
  }
}
```

### Step 3: Test it

1. Start your local server (Live Server in VS Code)
2. Open your page: `http://localhost:5500/index.html`
3. Add your parameter: `http://localhost:5500/index.html?hybit=mytip`
4. HAP's dialog should appear with your message!

## Parameter types

### Type 1: Simple message (shows same content everywhere)

```json
{
  "allowedParams": ["shortcuts"],
  "messages": {
    "shortcuts": {
      "title": "⌨️ Keyboard Shortcuts",
      "content": "Press <code>Ctrl+C</code> to copy code examples!"
    }
  }
}
```

**Usage**: `?hybit=shortcuts` on any page

### Type 2: Page-specific help (different content per page)

```json
{
  "pageHelp": {
    "index.html": {
      "title": "🏠 Hub Page Help",
      "intro": "Welcome! Here's how to navigate.",
      "suggestions": [
        "Start with Station 1",
        "Complete stations in order",
        "Use ?hybit on any page for tips"
      ]
    },
    "stations/station1.html": {
      "title": "🔬 Station 1 Help",
      "intro": "Tips for this station:",
      "suggestions": [
        "Read the intro carefully",
        "Try the examples yourself",
        "Check the Quick Reference section"
      ]
    }
  }
}
```

**Usage**: `?hybit` (no parameter) shows page-specific help

### Type 3: Station-specific parameter

```json
{
  "allowedParams": ["gradients"],
  "messages": {
    "gradients": {
      "title": "🎨 Understanding Gradients",
      "content": "Prof. Teeters taught me gradients are like <em>smooth transitions between colors</em>. Think of a sunset! 🌅"
    }
  }
}
```

**Usage**: `?hybit=gradients` on station about gradients

## HTML tags allowed

**Safe tags** (you can use these):
- `<code>` - Inline code
- `<strong>` - Bold text
- `<em>` - Italic text
- `<br>` - Line break

**Example**:
```json
{
  "content": "Use <code>viewBox</code> to set the <strong>coordinate system</strong>.<br>Prof. Teeters says: <em>\"ViewBox is the secret sauce!\"</em>"
}
```

**Not allowed**:
- `<script>` - Security risk
- `<img>` - Use HAP's avatar in dialog instead
- `<a>` - Links not supported in dialogs

## Step-by-step tutorial: Adding a new tip

Let's add a tip about responsive design!

### 1. Pick a parameter name

Choose something short and descriptive:
- ✅ Good: `responsive`, `mobile`, `breakpoints`
- ❌ Bad: `tip1`, `thing`, `stuff`

Let's use `responsive`.

### 2. Add to allowedParams

```json
{
  "allowedParams": [
    "detail",
    "responsive"  ← Add this
  ]
}
```

### 3. Create the message

```json
{
  "messages": {
    "responsive": {
      "title": "📱 HAP's Responsive Design Tip",
      "content": "I used to design for desktop first - BIG mistake! Prof. Teeters taught me <strong>mobile-first</strong> design. Start with the smallest screen, then <em>add</em> complexity for larger screens. Mind = blown! 🟠"
    }
  }
}
```

### 4. Test it

```
http://localhost:5500/stations/station6.html?hybit=responsive
```

### 5. Tell students about it

Add a hint in your station content:

```html
<p>Want a tip about responsive design? Add <code>?hybit=responsive</code> to this page's URL! 🟠</p>
```

## Common questions

### Can I use images in messages?

No, but HAP's avatar already appears in the dialog! Focus your content on text with code examples and formatting.

### How many parameters should I create?

**Recommendation**: 5-10 total parameters across all stations

- Too few (1-2): Underutilizes the feature
- Too many (20+): Overwhelming for students
- Just right (5-10): Discoverable and valuable

### Should every page have page-specific help?

**Hub page**: Yes, definitely
**Stations**: Optional - only if you have unique navigation tips
**Demos**: Usually not needed

### Can parameters work on multiple pages?

Yes! If you add `"mytip"` to `allowedParams` and create a message, it works on ALL pages:

```
index.html?hybit=mytip        ← Works
station1.html?hybit=mytip     ← Works
station2.html?hybit=mytip     ← Works
```

### What if I make a syntax error?

Check the browser console (F12 → Console tab):
- "JSON parse error" = Missing comma, bracket, or quote
- "Parameter not allowed" = Not in `allowedParams` array
- Nothing happens = JavaScript might be disabled

## Examples from real learning labs

### hybit-svg project (SVG teaching lab)

```json
{
  "allowedParams": ["detail", "formats", "viewbox", "xmlns"],
  "messages": {
    "viewbox": {
      "title": "🔬 HAP's ViewBox Explanation",
      "content": "I thought <code>viewBox</code> was just another way to set width/height - WRONG! Prof. Teeters explained: <strong>ViewBox creates the coordinate system</strong>. It's like setting up a graph before plotting points. Once I understood this, SVG positioning made SO much sense! 🟠"
    },
    "xmlns": {
      "title": "🌐 The xmlns Attribute",
      "content": "When I first saw <code>xmlns=\"http://www.w3.org/2000/svg\"</code>, I ignored it. Then my standalone .svg files didn't work! Prof. Teeters taught me: <em>xmlns tells tools 'this is SVG, not HTML'</em>. Always include it in standalone files! 🟠"
    }
  },
  "pageHelp": {
    "index.html": {
      "title": "🏠 Welcome to HAP's SVG Learning Lab!",
      "intro": "Hi! I'm HAP, and I learned everything here from Prof. Teeters.",
      "suggestions": [
        "Start with Station 1 to understand the basics",
        "Try <code>?hybit=viewbox</code> for my ViewBox breakthrough moment",
        "Each code example has a Copy button - test them yourself!"
      ]
    }
  }
}
```

## Voice tips

**HAP's personality in easter eggs**:
- ✅ First person: "I learned...", "When I tried..."
- ✅ Humble: "I thought... but I was WRONG!"
- ✅ Enthusiastic: "Mind = blown!", "SO much sense!"
- ✅ Credits Prof. Teeters: "Prof. Teeters explained..."
- ✅ Uses 🟠 emoji: HAP's signature

**Examples**:

```json
{
  "content": "I used to make this mistake ALL THE TIME. Prof. Teeters showed me the right way: <code>example</code>. Now I never forget! 🟠"
}
```

```json
{
  "content": "This confused me for DAYS until Prof. Teeters explained: <em>\"Think of it like...\"</em> and suddenly it clicked! 🟠"
}
```

## Security notes

The easter egg system is designed to be safe:

- **Whitelist validation**: Only parameters in `allowedParams` work
- **No user input in HTML**: Pre-defined messages only
- **Safe HTML tags**: Only `<code>`, `<strong>`, `<em>`, `<br>` allowed
- **No JavaScript execution**: Content is displayed as text, not executed

**Do NOT**:
- Allow user-submitted parameters
- Accept URL parameters without whitelist validation
- Include `<script>` tags in messages

## Troubleshooting

### Dialog doesn't appear

1. Check browser console for errors
2. Verify parameter is in `allowedParams` array
3. Verify JSON syntax is valid (use JSONLint.com)
4. Test with `?hybit` (no parameter) for page-specific help

### Message shows "unknown"

The parameter isn't in your `allowedParams` array. Add it:

```json
{
  "allowedParams": ["detail", "yourparameter"]
}
```

### JSON parse error

Common syntax errors:
- Missing comma between items
- Missing closing bracket `}` or `]`
- Unescaped quotes in content (use `\"` inside strings)
- Trailing comma after last item (not allowed in JSON)

**Fix**: Use a JSON validator like JSONLint.com

### JSONC comments cause errors

If using JSONC format and seeing parse errors:

1. Verify `easter-egg.js` has comment-stripping code
2. Check console for specific error message
3. Try converting to plain JSON temporarily to isolate issue
4. Ensure comments use `//` or `/* */` syntax

## File structure reference

### Complete JSON structure

```json
{
  "allowedParams": [
    "param1",
    "param2"
  ],
  "messages": {
    "param1": {
      "title": "Title with emoji",
      "content": "Message content with <code>tags</code>"
    }
  },
  "pageHelp": {
    "page.html": {
      "title": "Help title",
      "intro": "HAP's introduction",
      "suggestions": [
        "Suggestion 1",
        "Suggestion 2"
      ]
    }
  }
}
```

### Field descriptions

**allowedParams** (required):
- Array of strings
- Whitelist of valid parameter names
- Must match message keys

**messages** (required):
- Object with parameter names as keys
- Each message has `title` and `content`
- Both fields are required strings

**pageHelp** (optional):
- Object with filenames as keys
- Each page help has `title`, `intro`, and `suggestions`
- `suggestions` is an array of strings

## Content guidelines

### Writing effective titles

**Good titles**:
- ✅ "🚀 Lighthouse Score: 99%!" (specific metric)
- ✅ "📱 Perfect image for every screen" (clear benefit)
- ✅ "🎯 Deferred scripts = faster page loads!" (shows cause/effect)

**Avoid**:
- ❌ "Performance" (too vague)
- ❌ "This is about images and stuff" (unprofessional)
- ❌ "AMAZING OPTIMIZATION TECHNIQUES!!!" (too hype)

### Writing effective content

**Best practices**:
- Keep it concise (1-3 sentences)
- Focus on benefits, not just features
- Include specific numbers when possible ("80% reduction")
- Use `<code>` tags for technical terms
- Explain WHY, not just WHAT

**Example - Good**:
```
"Container queries let components respond to their container size,
not just viewport size. No more duplicate CSS versions!"
```

**Example - Too technical**:
```
"Use @container queries with container-type: inline-size to enable
CQ containment on parent elements."
```

**Example - Too vague**:
```
"Container queries are a new CSS feature that helps with responsive design."
```

### Emoji usage

**Use emojis in titles to create visual interest**:
- 🚀 - Performance, speed
- 🔬 - Learning, research, HAP's insights
- 📱 - Mobile, responsive
- 📸 - Images, photos
- ☁️ - Cloud, CDN
- 🎯 - Precision, targeting
- 📊 - Data, analytics
- 🎨 - Design, creativity
- 🔒 - Security
- 🟠 - Tips, important notes (HAP's signature emoji)

**Keep it professional**:
- One emoji per title maximum
- Place at the beginning or end
- Ensure emoji is relevant to content

## Advanced usage

### Conditional messages

You can create messages that work differently depending on context by using page-specific help:

```json
{
  "allowedParams": ["tip"],
  "messages": {
    "tip": {
      "title": "General Tip",
      "content": "This shows on all pages"
    }
  },
  "pageHelp": {
    "stations/station1.html": {
      "suggestions": [
        "Try <code>?hybit=tip</code> for a helpful tip!"
      ]
    }
  }
}
```

### Multiple suggestions per page

```json
{
  "pageHelp": {
    "index.html": {
      "title": "🏠 Hub Page Tips",
      "intro": "I have lots of tips for navigating this lab!",
      "suggestions": [
        "Add <code>?hybit=detail</code> to see project statistics",
        "Each station has unique tips - try <code>?hybit</code> on any station page",
        "Look for 🟠 orange circles throughout the site for more hints",
        "All code examples have Copy buttons - test them yourself!",
        "Prof. Teeters says: <em>\"The best way to learn is by doing!\"</em>"
      ]
    }
  }
}
```

### Linking parameters

Mention other parameters in your content:

```json
{
  "messages": {
    "responsive": {
      "title": "📱 Responsive Design",
      "content": "Start mobile-first! Also check out <code>?hybit=breakpoints</code> to learn about media queries."
    },
    "breakpoints": {
      "title": "🎯 Media Query Breakpoints",
      "content": "Common breakpoints: 768px (tablet), 1024px (desktop). See <code>?hybit=responsive</code> for the big picture!"
    }
  }
}
```

## Testing checklist

Before deploying your easter eggs:

- [ ] All parameters in `allowedParams` have corresponding messages
- [ ] JSON syntax is valid (use validator)
- [ ] Tested each parameter on at least one page
- [ ] Tested bare `?hybit` on pages with `pageHelp`
- [ ] Tested invalid parameter (should show "unknown" message)
- [ ] All HTML tags are safe (`<code>`, `<strong>`, `<em>` only)
- [ ] HAP voice is consistent (first person, humble, enthusiastic)
- [ ] No typos in parameter names
- [ ] Suggestions array has at least one item per page
- [ ] Tested on multiple browsers

## Maintenance

### Updating existing messages

1. Find the parameter in `messages` object
2. Edit `title` or `content`
3. Save and test
4. No need to update `allowedParams` (parameter already whitelisted)

### Removing parameters

1. Remove from `allowedParams` array
2. Remove from `messages` object
3. Remove from any `pageHelp` suggestions
4. Test to ensure no broken links

### Renaming parameters

Don't rename - it breaks existing usage. Instead:

1. Add new parameter to `allowedParams`
2. Copy message content to new parameter
3. Keep old parameter for backward compatibility
4. Gradually update references in content

## Version history

- **v4.0** (November 2025) - Beginner tutorial rewrite with step-by-step examples
- **v3.0** (October 2025) - Updated all page help to HAP's apprentice voice
- **v2.0** (October 2025) - Converted to JSONC with comments
- **v1.0** (October 2025) - Initial JSON-based system

## Next steps

1. ✅ Create your `hybit-insights.json` from template
2. ✅ Add 2-3 parameters relevant to your topic
3. ✅ Add page-specific help for hub page
4. ✅ Test all parameters in browser
5. ✅ Add hints in station content about available parameters

**Have fun adding HAP's insights!** 🟠

## Additional resources

- **JSON validator**: https://jsonlint.com/
- **HAP voice guidelines**: See `stations/_template-station.html` comments
- **Example learning labs**: See `hybit-svg` project for real-world usage
- **Security best practices**: Never allow user-controlled content in messages

## Questions?

For questions about this easter egg system:
- Check browser console for error messages
- Validate JSON syntax at jsonlint.com
- Review examples in this document
- Test with simple parameter first, then add complexity
- Remember: HAP's voice should be friendly, humble, and enthusiastic! 🟠

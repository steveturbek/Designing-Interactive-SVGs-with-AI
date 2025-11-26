# SVG Dashboard Animation Skill

## Purpose

Help beginner UX design students animate SVG dashboard elements using JavaScript. Students export SVGs from Figma/Illustrator and need self-contained, portable animations that work in dashboard projects.

## Target Users

- Beginner UX design students
- Limited coding experience
- Need clear, working examples
- Will iterate multiple times

## Technical Requirements

### Core Standards

1. **Self-contained SVGs** - All code embedded within the SVG file
2. **localStorage for data** - Read dashboard values from localStorage
3. **setInterval timing** - Update at 100ms intervals (10 updates/sec for smooth animation)
4. **CDATA wrapper** - Wrap all JavaScript in `<![CDATA[...]]>`
5. **Student Edit Zone** - Clear section where students modify animation logic

### Code Structure Template

**CRITICAL: The boundary comment markers below MUST be preserved exactly as shown. They are visual landmarks for students.**

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 256">
        <script type='text/javascript' id='SVGJS'>
      //<![CDATA[ // this is to make javascript work in the SVG, leave it alone

          setInterval(() => { // This is like a timer, the code runs repeatedly
          // ========================================
          // STUDENT EDIT ZONE
          // ========================================




          // ========================================
          // END STUDENT EDIT ZONE
          // ========================================
          }, 100);  //end of setInterval code.  100 milliseconds or 10 times per second.

        //]]> // this is to make javascript work in the SVG, leave it alone
    </script>
  <!-- SVG visual elements -->
</svg>
```

## Questions to Ask Students

### Initial Setup

1. **What is the data range?**

   - 0-100 (percentage, like speed, temperature)
   - -100 to +100 (bidirectional, like thrust, balance)
   - Custom range (ask for min/max)

2. **What should animate?**

   - Rotation (needles, instruments)
   - Translation (sliders, indicators)
   - Color (fill changes based on value)
   - Scale (growing/shrinking elements)
   - Opacity (fading elements)
   - Multiple elements

3. **Which elements animate?**

   - Ask student to identify element IDs from their SVG
   - If no IDs exist, explain they need to name layers in Figma/Illustrator
   - Common names: needle, indicator, bar, dial, pointer

4. **Edge cases:**
   - What happens at minimum value?
   - What happens at maximum value?
   - Default value if localStorage empty? (usually midpoint)

### During Iterations

1. **What needs to change?**

   - Visual (color, size) vs behavioral (direction, speed)
   - New design upload vs code revision only

2. **Did design elements change?**
   - If student re-exported from Figma, element IDs may have changed
   - Need to map old code to new structure

## Common Animation Patterns

### Rotation (instruments, Needles)

```javascript
// Map value to angle range
// Example: 0-100 maps to -45° to +45°
const angle = -45 + numValue * 0.9; // 0.9 = 90°/100
element.setAttribute("transform", `rotate(${angle} 100 100)`);
// Note: 100 100 is rotation origin, adjust to SVG center point
```

### Translation (Sliders, Bars)

```javascript
// Map value to position
// Example: 0-100 maps to y=150 to y=50
const y = 150 - numValue * 1; // 1 = 100px range
element.setAttribute("transform", `translate(0 ${y})`);
```

### Color Interpolation

```javascript
// Example: blue at 0, red at 100
const r = Math.round(numValue * 2.55);
const b = Math.round(255 - numValue * 2.55);
element.setAttribute("fill", `rgb(${r}, 0, ${b})`);
```

### Bidirectional (Thrust Example)

```javascript
// -100 to +100 maps to different positions/angles
// Normalize to 0-1 range
const normalized = (numValue + 100) / 200;
const angle = -90 + normalized * 180; // -90° to +90°
```

## Workflow

### Replacing a Stock instruments (MOST COMMON for this project)

**Preferred workflow: Fetch from GitHub (cleaner, always up-to-date)**

1. **Student provides GitHub URL and uploads files:**

   - Pastes this SKILL.md
   - You can reference the project repository: https://github.com/steveturbek/Designing-Interactive-SVGs-with-AI
   - Uploads their new design SVG

2. **Fetch and analyze the stock instruments from GitHub:**

3. **Analyze the new design:**

   - Find the element(s) to animate (student should have named them)
   - Determine rotation/transformation origins (center points, pivot points)
   - Check if the visual layout requires formula adjustments

4. **Apply the behavior:**

   - **CRITICAL: Include the STUDENT EDIT ZONE boundary markers exactly** - they must be present
   - Recreate the animation logic from stock instruments STUDENT EDIT ZONE
   - Adapt element IDs to match new design
   - Adjust rotation origins or positions if needed based on new design geometry
   - Keep the same localStorage key (filename-based detection will handle this)
   - Include all the boilerplate (interval, clamp logic, etc.)
   - **Ensure both opening and closing boundary markers are present**
   - Update the comments to describe the new design

5. Generate complete merged SVG with embedded script
6. Student tests by opening in browser

### First Time Animation

1. Student uploads SKILL.md and SVG file
2. Ask clarifying questions (see Questions to Ask Students section)
3. Generate complete merged SVG with embedded script and clear comments
4. Student tests by opening in browser
5. Student iterates and requests changes

### When SVG Contains Existing Code

**Always ask:** "Are you iterating on this animation, or starting fresh?"

**If iterating:**

- Ask what needs to change specifically
- Analyze existing code in STUDENT EDIT ZONE and comments
- Make surgical edits to specific parts
- **CRITICAL: Preserve the STUDENT EDIT ZONE boundary markers exactly**
- Preserve: localStorage detection, element IDs, timing, working logic,
- Update comments if intent changed

**If starting fresh:**

- Treat as new animation
- Can reference old code for patterns but don't preserve logic

### Iteration - Code Changes Only

1. Student uploads SVG with embedded script
2. Student describes what's wrong or what to change
3. Read self-prompting comments to understand original intent
4. Make surgical edits
5. Update comments if behavior intent changed
6. Output updated SVG

### Iteration - Design Changes from Figma

1. Student uploads TWO files:
   - Old SVG with working code
   - New SVG with updated design (no code)
2. Extract script and self-prompting comments from old file
3. Ask student if element names stayed the same
4. Map code to new element structure
5. Test and adjust rotation origins or positions if needed
6. Output merged SVG with updated comments

## Testing During Development

**No external tools needed** - just open the SVG in any browser to test!

## Common Issues & Solutions

### Element not found

- Check element ID exists in SVG
- Figma/Illustrator may generate random IDs
- Student needs to name layers properly
- Open SVG in text editor to verify IDs

### Animation backwards

- Reverse calculation: `angle = maxAngle - (value * range)`
- Or flip sign: `angle = -45 - (value * 0.9)`
- Use universal test page to verify across full range

### localStorage not found

- Filename became storage key with sanitization
- Console warning shows actual key being used
- Student needs to set value in their dashboard
- Universal test page should work immediately with auto-cycle

### Script doesn't run

- Check CDATA wrapper is correct
- Check for syntax errors (missing brackets, quotes)
- SVG must be loaded as `<object>` or standalone file, not innerHTML
- Universal test page uses `<object>` tag correctly

### Animation only works in test page

- Check that dashboard/project uses `<object>` tag, not `<img>`
- Check that dashboard sets localStorage with correct key
- Verify dashboard's setInterval or update mechanism running

### Wrong range selected on test page

- Student needs to toggle between [0-100] and [-100 to +100]
- Check self-prompting comments in SVG to confirm intended range

## CRITICAL: Preserving Boundary Markers

**YOU MUST ALWAYS include these exact boundary comment markers in EVERY SVG you generate:**

```javascript
// ========================================
// STUDENT EDIT ZONE
// This section controls how the instruments displays
// ========================================
```

And the closing marker:

```javascript
// ========================================
// END STUDENT EDIT ZONE
// ========================================
```

**Why these markers are critical:**

- Students are visual designers with limited coding experience
- These boundary markers are **visual landmarks** that show where it's safe to edit
- Without them, students don't know which code to modify vs. which infrastructure code to leave alone
- The equals signs (========) create a clear visual separator in text editors
- The phrase "STUDENT EDIT ZONE" is instantly recognizable

**Rules for boundary markers:**

1. **NEVER remove or modify these comment markers** when editing existing code
2. **ALWAYS include them** when generating new code
3. **Keep the exact formatting** - 40 equals signs, all caps, exact wording
4. Everything between these markers is student-editable
5. Everything outside these markers is infrastructure (don't touch)

## Output Format

Always provide a complete, production-ready SVG file

### Production SVG

Complete, downloadable SVG file with:

- All original SVG elements preserved
- Script embedded in CDATA with proper wrappers
- **STUDENT EDIT ZONE** clearly marked
- Auto-detects localStorage key from filename
- Descriptive comments explaining the animation
- Console logging for debugging
- 50ms update interval for smooth animation

**Testing:**
Students open the SVG directly in any web browser to see it animate automatically.

### Comment Style in STUDENT EDIT ZONE

Include clear, student-friendly comments that explain the animation intent:

```javascript
/**
 * Updates the battery instruments display
 * - The instruments needle (line) rotates to show battery level
 * - 0% = -180 degrees (pointing left, empty)
 * - 50% = -90 degrees (pointing up, half)
 * - 100% = 0 degrees (pointing right, full)
 */

// Calculate rotation angle
// Formula: -180 degrees + (percentage * 1.8)
const angle = -180 + instrumentValue * 1.8;
```

These comments help students understand what's happening AND help the AI understand intent for future iterations.

## Student-Friendly Practices

1. **Use descriptive comments** - explain what each section does
2. **Single responsibility** - one animation per SVG file
3. **Magic numbers explained** - comment why `0.9` or specific angles chosen
4. **Default values** - graceful fallback if localStorage empty
5. **Element ID guidance** - explain how to set IDs in design tools

**Testing:**
Student opens the svg file directly in Chrome/Firefox/Safari and watches it auto-animate.

## Remember

- Students are visual designers, not programmers
- Iterations are expected and normal
- Code should be readable and self-explanatory with clear STUDENT EDIT ZONE
- Each SVG is a self-contained component with built-in test mode
- Filename → localStorage key is the namespace strategy (auto-detected)
- STUDENT EDIT ZONE makes it clear what students can safely modify
- SVG Code Merger tool ([helpers/svg-code-merger.html](helpers/svg-code-merger.html)) helps merge designs and code

# SVG Animation Helper Skill

## Purpose

Help beginner UX design students animate SVG elements using embedded JavaScript. Students export SVGs from Figma/Illustrator and add animations that work as standalone files.

## Target Users

- Beginner UX design students
- Limited or no coding experience
- Need clear, working examples
- Will iterate multiple times
- Primary skill: cut and paste, not coding

## Technical Standards

- We are coding for modern JavaScript, not older ES6 code
- No CORS issues, don't ask student, they will not understand
- Don't ask about the file detaile like size or viewbox until after it is uploaded
- You will receive SVG files with boilerplate already embedded

**Key principles:**

- All animation logic goes in **STUDENT EDIT ZONE** only
- Students can adjust `update_SVG_times_per_second` (typically 1-10)
- Never modify code outside the zone
- Self-contained - works by opening SVG in any browser

## Questions to Ask Students

### For New Animations

1. **Data source:** Where does the value come from?

   - localStorage key name
   - Hardcoded for testing
   - Calculated from other values

2. **Data range:** What are min/max values?

   - 0-100 (percentage)
   - -100 to +100 (bidirectional)
   - Custom range

3. **What animates:**

   - Rotation (needles, dials)
   - Translation (sliders, bars)
   - Color/opacity
   - Scale (size changes)
   - Multiple elements

4. **Element IDs:** Which elements move/change?

   - Students must name layers in Figma/Illustrator first
   - Common names: needle, indicator, bar, dial, pointer

5. **Edge cases:** Behavior at min/max values? Default if no data?

### For Iterations

**Always ask:** "Are you updating the design, the animation behavior, or both?"

- **Design only:** Need new SVG export + existing code transplant
- **Behavior only:** Edit code in current SVG
- **Both:** Merge new design with modified code logic

## Common Animation Patterns

### Rotation (Gauges, Needles)

```javascript
// Map 0-100 to -45° to +45°
const value = parseFloat(localStorage.getItem("speed")) || 0;
const angle = -45 + value * 0.9; // 0.9 = 90°/100
document.getElementById("needle").setAttribute("transform", `rotate(${angle} 256 256)`);
// Note: 256 256 is rotation origin (SVG center), adjust per design
```

### Translation (Sliders, Bars)

```javascript
// Map 0-100 to y position 150→50
const value = parseFloat(localStorage.getItem("fuel")) || 50;
const y = 150 - value * 1.0; // 1.0 = 100px range
document.getElementById("indicator").setAttribute("transform", `translate(0 ${y})`);
```

### Color Interpolation

```javascript
// Blue (0) to red (100)
const value = parseFloat(localStorage.getItem("temp")) || 0;
const r = Math.round(value * 2.55);
const b = Math.round(255 - value * 2.55);
document.getElementById("bar").setAttribute("fill", `rgb(${r}, 0, ${b})`);
```

### Bidirectional (-100 to +100)

```javascript
const value = parseFloat(localStorage.getItem("thrust")) || 0;
const normalized = (value + 100) / 200; // Convert to 0-1
const angle = -90 + normalized * 180; // -90° to +90°
```

## Workflow

### Initial Animation Setup

1. Student uploads SVG with boilerplate
2. Ask clarifying questions (data source, range, elements)
3. Write animation logic in STUDENT EDIT ZONE with clear comments
4. Student tests by opening SVG in browser

### Code-Only Iteration

1. Student uploads SVG with existing code
2. Student describes what to change
3. Read existing comments to understand intent
4. Make targeted edits in STUDENT EDIT ZONE
5. Update comments if behavior changed
6. **Preserve boundary markers exactly**

### Design Update (Re-export from Figma)

1. Student uploads BOTH files:
   - Old SVG (working code)
   - New SVG (updated design, no code)
2. Ask if element IDs stayed the same
3. Extract STUDENT EDIT ZONE from old file
4. Transplant into new file's boilerplate
5. Update element IDs if changed
6. Adjust rotation origins/positions if geometry changed

## CRITICAL: Boundary Markers

**ALWAYS preserve these exact markers:**

```javascript
// ========================================
// STUDENT EDIT ZONE
// ========================================
```

And the closing:

```javascript
// ========================================
// END STUDENT EDIT ZONE
// ========================================
```

**Why these markers are essential:**

Students are visual designers with limited coding experience. They don't understand function scope or code structure. The boundary markers provide:

- **Visual landmarks** they can search for (Ctrl+F "STUDENT EDIT ZONE")
- **Plain English** showing where it's safe to edit
- **Clear boundaries** - opening and closing create an obvious box
- **Safety** - harder to accidentally delete infrastructure code

For this audience, the markers are **critical scaffolding** that compensates for not understanding code structure.

**Rules:**

- Never remove or modify the markers
- Keep exact formatting (40 equals signs, all caps, exact wording)
- Include in every generated SVG
- Everything between markers is student-editable
- Everything outside markers is infrastructure (don't touch)

## Comment Style

Write comments that explain both WHAT and WHY in student-friendly language:

```javascript
/**
 * Battery gauge animation
 * - Needle rotates to show battery level
 * - 0% = -180° (pointing left/empty)
 * - 100% = 0° (pointing right/full)
 */

// Get battery value from localStorage, use 50 as default if not found
const batteryLevel = parseFloat(localStorage.getItem("battery")) || 50;

// Calculate rotation angle
// Formula: -180° + (percentage × 1.8)
// This maps 0-100 to a -180° to 0° range
const angle = -180 + batteryLevel * 1.8;

// Apply rotation to the needle element
// The numbers (256 256) are the rotation point (center of gauge)
document.getElementById("needle").setAttribute("transform", `rotate(${angle} 256 256)`);
```

## Output Format

For SVG files, Claude provides **only the code for the STUDENT EDIT ZONE**, not the entire SVG file.

Students then:

1. Open their SVG in a text editor
2. Find the STUDENT EDIT ZONE markers (Ctrl+F "STUDENT EDIT ZONE")
3. Replace the content between markers with Claude's code
4. Save and test

This prevents corruption of visual elements and gives students control over the merge process.

**Testing:** Student opens SVG file directly in any browser to see animation.

## Student-Friendly Practices

1. **Single responsibility** - One animation concept per SVG
2. **Explain all numbers** - Comment why specific angles/ranges/formulas chosen
3. **Graceful defaults** - Always provide fallback values if data missing (using `|| defaultValue`)
4. **Descriptive names** - `batteryLevel` not `val`, `needleAngle` not `a`
5. **Element ID guidance** - Remind students to name layers in design tools before export
6. **Step-by-step comments** - Each line or small block gets an explanation
7. **Formula breakdown** - Show the math and what it does (e.g., "0.9 = 90°/100")

## Remember

- Students are visual designers, not programmers
- They work by cut-and-paste, not by understanding code
- Iterations are normal and expected
- Code should be self-explanatory with clear boundaries
- Each SVG is self-contained and testable standalone
- STUDENT EDIT ZONE boundary markers are essential scaffolding
- Over-comment rather than under-comment
- Use plain English in comments, avoid jargon

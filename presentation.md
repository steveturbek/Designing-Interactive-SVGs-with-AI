# Make It Go! Designing Interactive SVGs with AI Code Help

Steve Turbek 2026

---

# Who Am I?

- Teaches "Tangible Interfaces" Senior Design Studio at Pratt Institute
- Industrial Design program
- No prior student coding experience required

---

# Creative Mornings FieldTrip

**January 2026**

"Designers can create interactive, data-driven experiences—they just need a little help."

---

# The Question

## Should designers learn to code?

Discussed for decades since web design split into "people who draw the UI and people who code it"

---

# The Flash Era

**2000s:** Designers created complex interactive experiences
- Macromedia Director and Flash
- Blended sketching and making
- English majors who learned design + scrappy HTML skills

**2010:** Steve Jobs killed Flash for being a "closed system" 🤔

---

# What We Lost

"Flash had many issues as a technology, but we should mourn the loss of a tool that let designers create directly, rather than write specs for others."

This workshop is about **reclaiming a piece of that power.**

---

# TLDR

**Design is all about precise communication, yet designers have struggled to communicate with computers.**

What if there was another way?

---

# The SVG Advantage

- SVG file format = powerful like HTML
- Vector format, written in language
- LLMs are great at manipulating language
- Designer uploads image + collaborates interaction into life
- Style sheets and JavaScript INSIDE the file, sandboxed

---

# Round Trip Workflow

Design Program ↔ AI ↔ Design Program

With proper setup, iterate between your tools and AI collaboration

---

# Background: The Submarine Project

Students designed personal submarine with:
- Working steering controls
- UX instruments dashboard
- No coding experience

"Pretty magical" results led to this workshop

---

# What is SVG?

**Markup Languages:** "Mark up" data in `<tags>` so both computers and people could understand it

**SGML** (1970s) → **HTML** → **XML** → **SVG**

SVGs are a graphic file format, but store information as **math, not pixels**

---

# SVG = Scalable Vector Graphics

- **Vector** shapes: lines, rectangles, circles, curves
- **Scalable** up to billboard size without blur
- Tiny file size
- Made in Figma or Illustrator

---

# SVG's Secret Powers

From its origin story in ancient markup times:

- Style with CSS
- Animate with CSS
- JavaScript for interactivity
- JavaScript to load data
- **Code lives INSIDE the SVG file**

---

# Why This Matters for Designers

1. Design in your tools (Figma, Illustrator, Inkscape)
2. Save as SVG
3. AIs are excellent at interpreting language
4. Collaborate with AI to add functionality

---

# Designer Superpowers Unlocked

- Call out to web APIs for live data
- Carry styling and code inside file ("Sandboxed")
- Can't break the website it's on
- Upload to locked-down corporate CMS
- Work during build phase when devs are busy

---

# What SVG Code Looks Like

```
<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="40" fill="#4A90E2"/>
</svg>
```

*[Show visual example]*

---

# Animation: The Drawing Effect

SVG animation with just a couple lines of code

**Concept:** Huge dashed line style that slides along the path, looking like drawing

*[Show Z animation example]*

---

# Example 1: Color Wheel

**Basic Interactivity**

"I made this handy color wheel for a design system page when we had no developers available."

- Hover to view color info
- Click to lock and copy values
- Uploaded as SVG to CMS

---

# Example 2: Currency Trading Game

**Data API & Game Logic**

- Interactive button clicks
- Real-time financial market prices
- Running score
- **Filesize under 4k!**

---

# Example 3: Submarine Dashboard

**Webpage ↔ SVG Communication**

Strategy: localStorage for data sharing
- Game saves values like "oxygen", "battery"
- SVG timer looks for updates regularly
- Code encapsulated, can't break website

[Example chat session with AI](https://chatgpt.com/share/690a222c-f46c-800d-9600-128b0e82be92)

---

# The SVG AI Helper Tool

**What we will do:**
1. Design an image of a data visualization
2. Save as SVG
3. Add some code using helpers
4. Work with AI to get it right

**15-60 minutes** (more if you use social media)

---

# You Will Need

- Design software (Adobe Illustrator best for this demo)
- Chrome browser + internet
- AI access (ChatGPT allows SVG upload without paying)
- Patience and iteration mindset

---

# Best Practices: Composability

"By designing elements to work independently, but as part of a larger system, you can better manage complexity."

**You are the teacher of the AI.**

"Rotate item carLogo 30 degrees" is very legible to an AI.

---

# The Helper Tool Workflow

1. Enter your SVG file + text description
2. Paste into AI chat window
3. AI may ask follow-up questions
4. Copy returned JavaScript code
5. Paste back into SVG AI Helper
6. You may get a working interactive SVG!
7. **Iterate!**

All code works in browser only, no data retained.

---

# Workshop: Track the ISS

**International Space Station Location on Map**

Starting point: Equirectangular World Map
- Stretched globe proportionally into rectangle
- Much simpler math than Mercator projection

---

# The Prompt

```
There's an API for the International Space Station at
http://api.open-notify.org/iss-now.json

In my SVG there is an element with ID `ISS`
I want to position it on my equirectangular map based on
lat/long from the API.

It doesn't need to be pixel-perfect.
I want it to update once a second
```

---

# It May Not Work First Try

**That's OK! Iterate.**

- Claude got it right first try
- ChatGPT took a second try
- Explained what wasn't working
- AI diagnosed the problem
- Fixed version worked

---

# Wrap Up: A New Way Forward

**Not about replacing programmers**
- Programming is deeply skilled
- Programmers uncover hidden cases
- "Where do we mail the check if the person has no address?"

**About empowering designers**
- Make the thing, not just design the thing
- Use old tools in new ways
- Create richer experiences without waiting for developers

---

# The AI Irony

"AI created by programmers, who focus on programming problems, whose strongest skill is programming."

**BUT:** AI is transformative for designers when harnessed properly

**Warning:** AI generating design from scratch = generic design
(AI is fundamentally averaging ideas from the past)

---

# Design is Communication

"If we designers become better communicators, using our visual design tools with our new skills of working with AI coding assistants, both we and society will benefit."

---

# Key Tips

- Have as much patience as an AI
- Be a good communicator: prompts should be a paragraph long
- Be a scientist: document each step, save versions
- Name your layers!!
- Don't be afraid to start over
- Try different AIs

---

# Technical Tips

**Layer naming is critical:**
- Name it `yourElementName` in Figma/Illustrator
- Check SVG text for `id="yourElementName"`
- Element IDs must match layer names

**Tools available:**
- SVG AI Helper
- SVG Code Transplant tool

---

# Common Issues

**"Cannot read property 'setAttribute' of null"**
→ Element ID not found, check spelling

**Code disappeared after re-export**
→ Use Code Transplant tool

**SVG works alone but not on page**
→ Use `<object>` tag, not `<img>` tag

---

# What You Can Animate

```javascript
// Rotation
element.setAttribute("transform", `rotate(${angle} centerX centerY)`);

// Move position
element.setAttribute("transform", `translate(${x} ${y})`);

// Change color
element.setAttribute("fill", "red");
```

---

# Try These APIs

- [ISS Location](http://api.open-notify.org/iss-now.json)
- [Weather on Mt Everest](https://api.open-meteo.com/v1/forecast?latitude=27.9882&longitude=86.9254&current_weather=true)
- [Currency Exchange Rates](https://api.coinbase.com/v2/prices/EUR-USD/spot)

---

# Resources

**Learn More:**
- SVG AI Helper tool (included)
- SVG Code Transplant tool
- GitHub repo (all open source)
- CSS animation tutorials
- Reference documentation

**All browser-based, no data collected**

---

# Thank You!

**Questions?**

turbek.com/Designing-Interactive-SVGs-with-AI

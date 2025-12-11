# Make It Go!

<image href="oxygen.svg" x="50%" y="10%" width="400" height="400"/>
Designing Interactive SVGs with AI Code Help

Steve Turbek _turbek.com_

January 2026

---

## Who Is Steve Turbek?

- UX Designer, in recovery
- "Tangible Interfaces" studio @Pratt Industrial Design
- Noted lollygagger, dillydallyer, & goldbricker

---

## What We Shall Speak of Today

- A new (?) way to make interactive graphics
- A short technical history detour
- A new framework for designers to use AI
- A few personal observations

---

## TLDR

- SVG image files: powerful like HTML
- Supported widely in browsers
- Designer tools make SVGs
- SVGs are written in a language
- LLMs are great at manipulating language
- Designers can _collaborate_ interaction into life

---

# Should designers learn to code?

---

## Quick History of Design & Tech

_1990s:_ English majors learned design & HTML

_2000s:_ Designers created complex interactive experiences

_2000s:_ Many restaurant Flash websites were made...

_2010s:_ Steve Jobs killed Flash for being "closed" 🤔

_2020s:_ "People Who Draw the UI and People Who Code It"

---

# What We Lost

---

# What if there was another way?

---

# An _orphan with magic powers_ ?

---

## What is SVG? Can It Be Cured?

_Markup Languages:_ "Mark up" data in `<tags>` so both computers and people could understand it

` `

_SGML_ (1970s) → _HTML_ → _XML_ → _SVG_

---

## SVG = Scalable Vector Graphics

- _Graphic_ files, but _math, not pixels_
- _Vector_ shapes lines, rectangles, circles, curves
- _Scalable_ up to billboard size without blur
- Tiny file size
- Make in Figma, Illustrator, ... or _TextEdit?_

---

## SVG's Secret Powers

- Style with CSS
- Animate with CSS
- JavaScript for interactivity
- JavaScript to load data
- _Code lives INSIDE the SVG file_

---

## Why This Matters for Designers

1. Design in your tools (Figma, Illustrator, Inkscape)
2. Save as SVG
3. AIs are excellent at interpreting language
4. Collaborate with AI to add functionality
5. Design Program ↔ AI ↔ Design Program

---

## Designer Superpowers Unlocked

- Call out to web APIs for live data
- Carry styling and code inside file ("Sandboxed")
- Can't break the website it's on
- Upload to locked-down corporate CMS
- Work during build phase when devs are busy

---

## What SVG Code Looks Like

```
<svg width="100" height="100"
  xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="40" fill="green"/>
</svg>
```

<image href="green-circle.svg" x="50" y="700" width="100" height="100"/>

---

## Animation: The Drawing Effect

SVG animation with just a couple lines of code

_Concept:_ Huge dashed line style that slides along the path, looking like drawing

_[Show Z animation example]_

---

## Background: The Submarine Project

Students designed personal submarines with:

- Working steering hardware
- UX instruments dashboard
- No coding experience

---

## Color Wheel

<image href="GSDS-color-wheel-v2.svg" x="30%" y="0%" height="50%"/>

---

## Currency Trading _Game_

<image href="currency-game.svg" x="30%" y="50%" height="50%"/>

---

## Example 3: Submarine Dashboard

_Webpage ↔ SVG Communication_

Strategy: localStorage for data sharing

- Game saves values like "oxygen", "battery"
- SVG timer looks for updates regularly
- Code encapsulated, can't break website

---

## The SVG AI Helper Tool

_What we will do:_

1. Design an image of a data visualization
2. Save as SVG
3. Add some code using helpers
4. Work with AI to get it right

_15-60 minutes_ (more if you use social media)

---

## You Will Need

- Design software (Adobe Illustrator best for this demo)
- Chrome browser + internet
- AI access (ChatGPT allows SVG upload without paying)
- Patience and iteration mindset

---

# Communicating Design

and Designing with Communication

---

## Best Practices: Composability

"By designing elements to work independently, but as part of a larger system, you can better manage complexity."

_You are the teacher of the AI._

"Rotate item carLogo 30 degrees" is very legible to an AI.

---

## The Helper Tool Workflow

1. Enter your SVG file + text description
2. Paste into AI chat window
3. AI may ask follow-up questions
4. Copy returned JavaScript code
5. Paste back into SVG AI Helper
6. You may get a working interactive SVG!
7. _Iterate!_

All code works in browser only, no data retained.

---

## Workshop: Track the ISS

_International Space Station Location on Map_

Starting point: Equirectangular World Map

- Stretched globe proportionally into rectangle
- Much simpler math than Mercator projection

---

## The Prompt

```
There's an API for the International Space Station at
http://api.open-notify.org/iss-now.json

In my SVG there is an element with ID `ISS`
I want to position it on my equirectangular map based on
lat/long from the API.

It doesn't need to be pixel-perfect.
I want it to update once a second.
```

---

## It May Not Work First Try

_That's OK! Iterate._

- Claude got it right first try
- ChatGPT took a second try
- Explained what wasn't working
- AI diagnosed the problem
- Fixed version worked

---

## The AI Irony

"AI created by programmers, who focus on programming problems= AIs strongest skill is programming."

_BUT:_ AI is transformative for designers when harnessed properly

_Warning:_ AI generating design from scratch = generic design
(AI is fundamentally averaging ideas from the past)

---

## Wrap Up: A New Way Forward

_Not about replacing programmers_

- Programming is deeply skilled
- Programmers uncover hidden cases

_About empowering designers_

- Make the thing, not just design the thing
- Use old tools in new ways
- Create richer experiences without waiting for developers

---

# Design is Communication

---

## Key Tips

- Have as much patience as an AI
- Be a good communicator: prompts should be a paragraph long
- Be a scientist: document each step, save versions
- Name your layers!!
- Don't be afraid to start over
- Try different AIs

---

## Technical Tips

_Layer naming is critical:_

- Name it `yourElementName` in Figma/Illustrator
- Check SVG text for `id="yourElementName"`

---

## What You Can Animate

```javascript
// Rotation
element.setAttribute("transform", `rotate(${angle} centerX centerY)`);

// Move position
element.setAttribute("transform", `translate(${x} ${y})`);

// Change color
element.setAttribute("fill", "red");
```

---

# _This presentation is a SVG_

---

## Thank You!

turbek.com/Designing-Interactive-SVGs-with-AI

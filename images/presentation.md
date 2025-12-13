# Make It Go!

<image href="oxygen.svg" x="60%" y="10%" width="400" height="400"/>
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

- A new hack to make interactive graphics
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

_2010s:_ Steve Jobs killed Flash for being “closed” 🤔

_2020s:_ “People Who Draw the UI and People Who Code It”

---

# What if there was another way?

---

# An _orphan with magic powers_ ?

---

## What is SVG? Can It Be Cured?

- SVG = Scalable Vector Graphics
- _Graphic_ files, but _shapes,_ not pixels
- _Vector_ shapes lines, rectangles, circles, curves
- _Scalable_ up to billboard size without blur
- Tiny file size
- Make in Figma, Illustrator, ... or _TextEdit?_

---

## Markup Languages

“Mark up” data in `<tags>` so both computers and people could understand it

` `

_SGML_ (1970s) → _HTML_ → _XML_ → _SVG_

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

## CSS Animation

<image href="z-animation.svg" x="25%" y="10%" height="50%"/>

```

```

```

	stroke:#000;
	stroke-dasharray:1800;
	stroke-dashoffset:1800;
	animation:animateZ 5s linear alternate infinite;
```

---

## SVG's Secret Powers

- Style with CSS
- Animate with CSS
- JavaScript for interactivity
- JavaScript to load data
- _Code lives INSIDE the SVG file_

---

## Why This Matters for Designers

1. Design tools (Figma, Illustrator, Inkscape) save SVG
2. Collaborate with AI to add functionality
3. Design Program ↔ AI ↔ Design Program

```


```

**But how?**

---

# 🕹️ 🕹️ 🕹️ 🕹️ 🕹️ Demo Time! 🕹️ 🕹️ 🕹️ 🕹️

---

## Color Wheel

<image href="GSDS-color-wheel-v2.svg" x="10" y="15%" height="80%"/>

---

## Currency Trading Game _(?)_

<image href="currency-game.svg" x="600" y="30%"  width="400" height="400"/>

---

## Submarine Dashboard

<image href="pitch.svg" x="100" y="30%" width="400" height="400" />

<image href="depth.svg" x="0" y="20%" height="600" />

<image href="battery.svg" x="1100" y="30%" width="400" height="400" />

---

## Data Visualization, Not Animation

<image href="oxygenManual.svg" x="600" y="30%" width="400" height="400" />

<image href="oxygenManual-minus.svg" x="600" y="80%" width="300" height="300" />
<image href="oxygenManual-plus.svg" x="820" y="80%" width="300" height="300" />

---

# 🛠️ 🛠️ 🛠️ 🛠️ Workshop Time! 🛠️ 🛠️ 🛠️ 🛠️

---

## Let's Track A Space Station!

1. World Map SVG
2. Get location of ISS from internet
3. Animate!

<image href="International_Space_Station_top_view.svg" x="900" y="20%" width="600" height="600" />

```



```

_NASA, Public domain, via Wikimedia Commons_

---

## You Will Need

- Design software (Adobe Illustrator best for this demo)
- Chrome browser + internet
- Steve's SVG AI Helper Tool
- AI access (ChatGPT allows SVG upload without paying)
- Patience and iteration mindset

---

## Process

1. Design an image of a data visualization
2. Save as SVG
3. What exactly do you want to happen?
4. Work with AI to code it up
5. Iterate!

---

<image href="ISS-Map-0-original.svg" x="200" y="10%" width="50%" />

## 1 The Artwork

```






```

Thanks _Sven nestle2_ at Wikipedia

---

<image href="ISS-Map-1-simplified-styles.svg" x="0" y="0"  width="100%" />

## 2 Edited Vector File

---

<image href="ISS-Map-3-simplified-styles.svg" x="0" y="0"  width="100%"  />

## 3 Added Marker

```
  <g id="ISS">
    <circle id="circle" class="st6" cx="0" cy="0" r="5"/>
  </g>
```

---

<image href="svg-ai-helper-wireframe.svg" x="440" y="20"  height="80%"  />

## SVG AI Helper Tool Workflow

1. Select your SVG file
2. Describe what you want to happen
3. Copy SVG AI Helper output; Paste into AI chat window
4. AI may ask follow-up questions
5. AI returns JavaScript code; Paste into SVG AI Helper
6. You may get a working interactive SVG!

_All SVG AI Helper code works in browser locally. No data transmitted or retained._

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

<image href="ISS-Map-5-simplified-styles-interactive-chatGPT-fixed.svg" x="0" y="0"  width="100%"  />

## 4 Working ISS Tracker!

---

## Key Tips

- Have as much patience as an AI
- Name your layers!!
- Be a good communicator: prompts should be a paragraph long
- Be a scientist: document each step, save versions
- Don't be afraid to start over
- Try different AIs

---

## It May Not Work on First Try

_That's OK! Iterate._

- Claude got it right first try
- ChatGPT took a second try
- I explained what wasn't working
- AI diagnosed its mistake
- Next version worked

---

## Wrap Up: A New Toy, A New Tool

- Not about replacing programmers
- Designers can make the thing, not just design the thing
- Use old tools in new ways
- Let's make some cool stuff!

---

# Design is the _Communication of Intent_

---

# BTW: _This presentation is a SVG_

---

# Thank You!

Steve Turbek, turbek.com/Designing-Interactive-SVGs-with-AI

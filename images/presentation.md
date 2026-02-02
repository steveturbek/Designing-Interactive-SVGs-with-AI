# Make It Go!

<!-- slide-bg=#d4d6cb -->
<image href="oxygen.svg" x="60%" y="10%" width="400" height="400"/>
Designing Interactive Graphics with AI Code Help
turbek.com/Designing-Interactive-SVGs-with-AI

Steve Turbek January 2026

---

# Who Is Steve Turbek?

- UX Designer, in recovery
- Hobbyist programmer
- ...

---

<image href="https://bubblecalendar.com/img/bubble_calendar_timeless_finger_L.jpg" x="0" y="0"  width="100%" />

# Bubble Calendar

---

<video src="https://www.mechanical-library.org/img/site/mechanical-library-cabinet-video.mp4" x="0" y="0" width="100%" height="110%" autoplay loop muted />

# Mechanical-Library.org

---

## Tangible Interfaces Design Studio at Pratt

<image href="https://turbek.com/Tangible-Interfaces-Submarine-Design-Project/artwork/steve-test-drive-wonderfour.jpg" x="40" y="15%" height="80%" />
<image href="https://turbek.com/Tangible-Interfaces-Submarine-Design-Project/artwork/2025_fall_sub_marine.jpg" x="840" y="15%"  height="80%" />

---

## What We Shall Speak of Today

- A new hack to make interactive graphics
- A short tech history detour
- A new tool for UX designers to use AI
- A few personal observations on design, tech, culture

---

## TLDR

1. SVG image files: powerful like HTML, widely supported
2. SVGs images are actually written in a language
3. LLMs are great at manipulating language
4. Designers can _collaborate_ interaction into life

---

# Why does AI design disappoint?

---

<image href="images/midjourney-humidifier.jpg" x="0" y="0" width="100%" />

---

# Design is the _Communication of Intent_

- 🖌️ Depict
- ✍️ Describe
- 📐 Design

---

# Should designers learn to code?

---

# Coding vs Thinking

---

<image href="images/krea-industrial-design.jpg" x="0" y="0" width="100%" />

---

# A mockup is worth a thousand prompts

---

# We lack a UI for coding interactions

---

# What if there was another way?

---

# An _orphan with magic powers_ ?

---

## Quick History of Design & Tech

_1990s:_ English majors learned design & HTML

_2000s:_ Designers created complex interactive experiences

........ Many restaurant Flash websites were made

_2010s:_ Steve Jobs killed Flash for being “closed” 🤔

_2020s:_ “Designers draw the UI, Programmers code the UI”

---

## Markup Languages

“Mark up” data with `<tags>` so computers and people understand

```
<person>
    <name>Alice</name>
        <age>30</age>
</person>
```

---

## Markup Languages History

_1970s_ SGML: Standard Generalized Markup Language
_1993_ HTML: HyperText Markup Language
_1998_ XML: eXtensible Markup Language
_2001_ SVG: Scalable Vector Graphics
...
_1995_ VRML: Virtual Reality Markup Language

---

## What is SVG? Can It Be Cured?

- SVG = Scalable Vector Graphics
- _Graphic_ files, but _shapes,_ not pixels
- _Vector_ shapes lines, rectangles, circles, curves
- _Scalable_ up to billboard size without blur
- Tiny file size
- Make in Figma, Illustrator, ... or _TextEdit?_

---

## SVG is Text

```
<svg width="100" height="100"
  xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="40" fill="green"/>
</svg>
```

<image href="green-circle.svg" x="50" y="700" width="100" height="100"/>

---

# SVG is an open standard

---

<image href="https://i0.wp.com/www.paloaltoonline.com/wp-content/uploads/2021/07/93278_original.jpg?resize=1568%2C1045&ssl=1" x="0" y="0"  width="100%" />

# Adobe & SVG : Jon Ferraiolo

---

## Illustrator layers define the SVG code

```
<svg id="Layer_1" viewBox="0 0 100 100">
  <g id="shapes">
    <rect id="BrownBox" x="4" y="8" width="43" height="43"/>
    <circle id="BlueCircle"cx="71" cy="70" r="24"/>
  </g>
<text class="st0" transform="translate(60.2 40.2)">
<tspan x="0" y="0">T</tspan></text>
</svg>
```

<image href="images/illustrator_layers_example.jpg" x="60%" y="25%" width="35%" />

---

## SVG's Secret Powers

- Style with CSS
- Animate with CSS
- JavaScript for interactivity
- JavaScript to load data
- _Code lives INSIDE the SVG file_

---

## CSS Animation

<image href="hello.svg" x="0" y="0" width="100%"/>

```

fill: none;
stroke: #2e368f;
stroke-width: 7px;
stroke-dasharray:3000;
stroke-dashoffset:3000;
animation:animateZ 5s linear alternate infinite;
```

---

## Color Wheel

<image href="GSDS-color-wheel-v2.svg" x="10" y="15%" height="80%"/>

---

# But how?

---

# 🕹️ 🕹️ 🕹️ 🕹️ Demo Time! 🕹️ 🕹️ 🕹️ 🕹️

---

## Submarine Project

<image href="https://turbek.com/Tangible-Interfaces-Submarine-Design-Project/artwork/steve-test-drive-wonderfour.jpg" x="40" y="15%" height="80%" />
<image href="https://turbek.com/Tangible-Interfaces-Submarine-Design-Project/artwork/2025_fall_sub_marine.jpg" x="840" y="15%"  height="80%" />

---

<video src="images/game-video-clip.mp4" x="0" y="0" width="100%" height="100%" autoplay loop muted />

## Submarine Game

---

<video src="images/dashboard.mp4" x="0" y="10%" width="100%" height="100%" autoplay loop muted />

## Submarine Dashboard

---

## Submarine Dashboard Instruments

<image href="pitch.svg" x="100" y="30%" width="400" height="400" />

<image href="depth.svg" x="0" y="20%" height="600" />

<image href="battery.svg" x="1100" y="30%" width="400" height="400" />

---

## How does this work? Javascript in the SVG

```
<script xmlns="http://www.w3.org/2000/svg" type="text/javascript">
<![CDATA[
async function updateSVG() {
 // do stuff
 }
setInterval(updateSVG, 5000); // Update every 5 seconds
]]></script>
```

---

## Data Visualization, Not Animation

```
// Get the angle
angle = localStorage.getItem("oxygen");

// Select the needle line SVG element
line = document.getElementById('line');

// Rotate the needle around its end point
line.setAttribute('transform', `rotate(${angle}, y1, y1)`);

```

<image href="oxygenManual.svg" x="900" y="20%" width="400" height="400" />

<image href="oxygenManual-minus.svg" x="900" y="70%" width="300" height="300" />
<image href="oxygenManual-plus.svg" x="1120" y="70%" width="300" height="300" />

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

## https://api.wheretheiss.at/v1/satellites/25544

```
{
  "name": "iss",
  "id": 25544,
  "latitude": -51.704193597782,
  "longitude": 102.13435954688,
  "altitude": 444.24120384636,
  "velocity": 27513.867576207,
  "visibility": "daylight",
  "footprint": 4628.7910951374,
  "timestamp": 1769633602,
  "daynum": 2461069.3703935,
  "solar_lat": -18.020194285052,
  "solar_lon": 229.90476289451,
  "units": "kilometers"
}
```

---

<image href="svg-ai-helper-wireframe.svg" x="450" y="130"  height="80%"  />

## SVG AI Helper Tool Workflow

1. Select your SVG file
2. Describe what you want to happen
3. Copy SVG AI Helper output; Paste into AI chat window
4. AI may ask follow-up questions
5. AI returns JavaScript code; Paste into SVG AI Helper
6. You may get a working interactive SVG!

_No data transmitted, Tool works locally in browser._

---

## The Prompt

```
There's an API for the International Space Station at
https://api.wheretheiss.at/v1/satellites/25544
It returns: `{"name":"iss","id":25544,"latitude":-23.316958619104,"longitude":31.677031345303,"altitude":435.78710948733,"velocity":27526.435812994,"visibility":"eclipsed","footprint":4586.9246082066,"timestamp":1769632629,"daynum":2461069.3591319,"solar_lat":-18.023202266704,"solar_lon":233.95842078519,"units":"kilometers"}`
In my SVG there is an element with ID `ISS`
I want to position it on my equirectangular map based on latitude/longitude from the API response.
It doesn't need to be pixel-perfect.
I want it to update once a second
```

---

# 🛠️ 🛠️ 🛠️ 🛠️ LIVE DEMO 🛠️ 🛠️ 🛠️ 🛠️

---

## How did I know how to code this?

- _I_ didn't.
- I knew what I wanted.
- My buddy Claude helped me figure it out.

---

## It May Not Work on First Try

_That's OK! Iterate._

- Claude got it right first try
- ChatGPT took a second try
- I explained what wasn't working
- AI diagnosed its mistake
- Next version worked

---

## Process

1. Design an image of a data visualization
2. Save as SVG
3. What exactly do you want to happen?
4. Work with AI to define the problem
5. Work with AI to write prompt
6. Use SVG AI helper
7. Iterate!

---

## Tips

- Name your layers!!
- Have as much patience as an AI
- Be a good communicator: prompts should be a paragraph long
- Be a scientist: document each step, save versions
- Don't be afraid to start over
- Try different AIs

---

## What else could you do?

1. Data Dashboards
2. Illustrations and animations
3. Infographics
4. A weather app
5. Games
6. Restaurant websites!!

---

## Summary

- SVG image files: powerful like HTML
- Supported widely in browsers
- Designer tools make SVGs
- SVGs are written in a language
- LLMs are great at manipulating language
- Designers can _collaborate_ interaction into life

---

# Design is the _Communication of Intent_

---

# Open Standards Rock!

---

# Wrap Up: A New Toy, A New Tool

---

# Designers can make the thing, not just design the thing

---

# Let's make some cool stuff!

---

# BTW: _This presentation is a SVG_

---

# Thank You!

Steve Turbek
turbek.com/Designing-Interactive-SVGs-with-AI

---
theme: default
title: Automotive Head-Up Display — HUD Prototype
titleTemplate: '%s'
favicon: '/fav-icon.svg'
info: |
  ## Automotive Head-Up Display (HUD) Prototype
  Research and prototype development of an embedded HUD system.
  Presentation for Research Methodology — Alireza Hassani Eghtedar
class: text-[#F2EDE3]
colorSchema: dark
background: 'radial-gradient(ellipse at 50% -10%, #1A100A 0%, #0B0705 55%, #050403 100%)'
transition: fade
mdc: true
fonts:
  sans: 'Inter'
  serif: 'Big Shoulders Display:500,600,700,800'
  mono: 'JetBrains Mono'
---

<!-- ============ SIGNATURE: reusable "speed-tape" side rail ============
Real automotive/avionics HUDs render a vertical tick-mark tape (speed, RPM,
altitude) in the driver's peripheral view. We reuse that exact motif as the
deck's one recurring signature element, instead of a generic corner-bracket
frame. It appears quietly down the left margin of content slides. -->

<div class="absolute inset-0 flex items-center justify-center pointer-events-none">
  <div class="relative w-[780px] h-[420px]">
    <div class="absolute -top-3 left-1/2 -translate-x-1/2 font-mono text-[10px] tracking-[0.5em] text-[#FF7A33]/40">HUD · 01</div>
  </div>
</div>

<div class="relative flex flex-col items-center justify-center h-full text-center px-20">
  <div class="font-mono text-xs tracking-[0.45em] text-[#FF7A33] mb-6">RESEARCH METHODOLOGY</div>
  <h1 class="font-serif font-800 uppercase text-6xl leading-[0.95] text-[#F7F1E6]" style="letter-spacing: 0.01em;">
    Automotive<br>Head&#8209;Up Display
  </h1>
  <div class="font-mono text-sm tracking-[0.25em] text-[#B9A88F] mt-6 uppercase">
    Prototype of an embedded HUD system
  </div>
  <div class="flex items-center gap-3 my-8">
    <div class="w-16 h-px bg-[#FF7A33]/50"></div>
    <div class="w-1.5 h-1.5 rotate-45 bg-[#FF7A33]"></div>
    <div class="w-16 h-px bg-[#FF7A33]/50"></div>
  </div>
  <div class="font-mono text-xs text-[#8C7E6C] leading-relaxed">
    Alireza Hassani Eghtedar &nbsp;·&nbsp; Student ID 992023008<br>
    Instructor: Dr. Kalarestaghi &nbsp;·&nbsp; Kharazmi University — Computer Engineering
  </div>
</div>

<div @click="$slidev.nav.next" class="absolute bottom-8 right-14 font-mono text-xs text-[#FF7A33] flex items-center gap-2 cursor-pointer opacity-70 hover:opacity-100">
  PRESS SPACE <carbon:arrow-right />
</div>

<!--
Title slide: introduce yourself, the course, and the instructor. One line on the core problem: drivers looking away from the road to read dashboard data.
-->

---
transition: fade
---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div>&nbsp</div>
<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 01 — INTRODUCTION</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Problem Statement</h1>

<div class="grid grid-cols-[1fr_auto] gap-10 items-start">
<div class="space-y-5 font-sans text-lg text-[#D9CFC0]">

<v-clicks>

- Safe driving requires **continuous visual attention on the road**
- Critical data — speed, RPM, navigation — lives only on the **dashboard or center screen**
- Reading it means **looking away from the road**, even briefly
- At speed, that brief glance equals **meters of road travelled with zero visual attention**
- A known contributing factor in accidents caused by **driver distraction**

</v-clicks>

</div>

<div class="w-56 pt-2">
<v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1, transition: { delay: 800 } }">
<div class="border border-[#2A2018] bg-[#120D09] p-4 font-mono text-xs text-[#B9A88F] leading-relaxed">
  <div class="text-[#FF7A33] mb-1">// AT 100 KM/H</div>
  1.5s glance ≈ 42m<br>travelled blind
</div>
</v-motion>
</div>

</div>

<v-click>
<div class="mt-2 border-l-2 border-[#FF7A33] pl-5 py-2 bg-[#FF7A33]/5 max-w-2xl">
  <span class="font-mono text-xs text-[#FF7A33]">RESEARCH QUESTION</span>
  <div class="text-[#F2EDE3] mt-1">How can essential driving data reach the driver without changing the direction or focus of their gaze?</div>
</div>
</v-click>

</div>

---
transition: fade
---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 01 — INTRODUCTION</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Why It Matters</h1>

<div class="grid grid-cols-2 gap-10">

<div>
<div class="font-mono text-xs text-[#8C7E6C] uppercase mb-3">Driver distraction</div>
<v-clicks>

- One of the most common, well-documented causes of accidents worldwide
- The EU's General Safety Regulation II (GSR II) mandates support for driver-assist display technologies like HUD

</v-clicks>
</div>

<div>
<div class="font-mono text-xs text-[#8C7E6C] uppercase mb-3">Global HUD market growth</div>
<div class="space-y-4">
<v-click>
<div class="flex items-baseline gap-3">
  <span class="font-serif font-800 text-4xl text-[#FF7A33]">$1.23B</span>
  <span class="text-sm text-[#B9A88F]">waveguide combiner market, 2025</span>
</div>
</v-click>
<v-click>
<div class="flex items-baseline gap-3">
  <span class="font-serif font-800 text-4xl text-[#FF7A33]">18.6%</span>
  <span class="text-sm text-[#B9A88F]">CAGR</span>
</div>
</v-click>
<v-click>
<div class="flex items-baseline gap-3">
  <span class="font-serif font-800 text-4xl text-[#FF7A33]">$2.85B</span>
  <span class="text-sm text-[#B9A88F]">projected by 2030</span>
</div>
</v-click>
</div>
</div>

</div>

<v-click>
<div class="mt-10 border border-[#FFC24B]/30 bg-[#FFC24B]/5 p-4 font-mono text-xs text-[#FFC24B] max-w-2xl">
  🇮🇷 IRAN — the domestic market relies mainly on imported, low-cost units; local research and manufacturing infrastructure remains limited.
</div>
</v-click>

</div>

---
transition: slide-up
---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 01 — INTRODUCTION</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Research Objectives</h1>

<div class="grid grid-cols-2 gap-5 max-w-4xl">

<v-click><div class="border border-[#2A2018] bg-[#120D09] p-5"><span class="font-mono text-[#FF7A33] text-sm">01</span><div class="mt-2 text-[#D9CFC0]">Examine the theory, history, and categories of automotive HUD technology</div></div></v-click>

<v-click><div class="border border-[#2A2018] bg-[#120D09] p-5"><span class="font-mono text-[#FF7A33] text-sm">02</span><div class="mt-2 text-[#D9CFC0]">Compare existing products in international and domestic (Iranian) markets</div></div></v-click>

<v-click><div class="border border-[#2A2018] bg-[#120D09] p-5"><span class="font-mono text-[#FF7A33] text-sm">03</span><div class="mt-2 text-[#D9CFC0]">Identify the hardware and software building blocks for a low-cost prototype</div></div></v-click>

<v-click><div class="border border-[#2A2018] bg-[#120D09] p-5"><span class="font-mono text-[#FF7A33] text-sm">04</span><div class="mt-2 text-[#D9CFC0]">Design the architecture and build process of a working embedded HUD prototype</div></div></v-click>

</div>

</div>

---
transition: fade
---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 02 — THEORETICAL FOUNDATIONS</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">What Is a HUD?</h1>

<div class="grid grid-cols-2 gap-14 items-center">

<div>
<div class="text-lg text-[#D9CFC0] leading-relaxed mb-8">
A system that projects information transparently, directly in the user's line of sight — so data can be read without looking away from the environment ahead.
</div>

<div class="space-y-5">
<v-click>
<div class="flex gap-4">
  <div class="font-mono text-[#FF7A33] text-sm shrink-0">WWI–WWII</div>
  <div class="text-[#B9A88F] text-sm">Origin in fighter aircraft — simple optical markers helped pilots aim without looking down at instruments</div>
</div>
</v-click>
<v-click>
<div class="flex gap-4">
  <div class="font-mono text-[#FF7A33] text-sm shrink-0">1988</div>
  <div class="text-[#B9A88F] text-sm">First automotive HUD introduced by <b class="text-[#F2EDE3]">General Motors</b>, using amber vacuum-fluorescent display technology inherited from cockpit instruments</div>
</div>
</v-click>
<v-click>
<div class="flex gap-4">
  <div class="font-mono text-[#FF7A33] text-sm shrink-0">since</div>
  <div class="text-[#B9A88F] text-sm">Gradual adoption across premium, then mid-range vehicle segments</div>
</div>
</v-click>
</div>
</div>

<v-motion :initial="{ opacity: 0, scale: 0.96 }" :enter="{ opacity: 1, scale: 1, transition: { delay: 300 } }">
<div class="relative border border-[#2A2018] bg-[#0A0705] p-2">
  <img src="/hud.png" alt="Automotive HUD projecting speed onto the windshield" class="w-full h-auto object-cover" style="aspect-ratio: 4/3;" />
  <div class="absolute top-0 left-0 w-8 h-8 border-t-2 border-l-2 border-[#FF7A33]/70"></div>
  <div class="absolute top-0 right-0 w-8 h-8 border-t-2 border-r-2 border-[#FF7A33]/70"></div>
  <div class="absolute bottom-0 left-0 w-8 h-8 border-b-2 border-l-2 border-[#FF7A33]/70"></div>
  <div class="absolute bottom-0 right-0 w-8 h-8 border-b-2 border-r-2 border-[#FF7A33]/70"></div>
  <div class="mt-2 font-mono text-[10px] text-[#8C7E6C] px-1">FIG. 01 — HUD PROJECTION ON WINDSHIELD</div>
</div>
</v-motion>

</div>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 02 — THEORETICAL FOUNDATIONS</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Core Components</h1>

<div grid="~ cols-3 gap-5">

<div v-click="1" class="border p-5 transition-all duration-300" :class="$clicks >= 1 ? 'border-[#FF7A33]/60 bg-[#FF7A33]/5' : 'border-[#2A2018]'">
  <div class="font-mono text-xs text-[#FF7A33]">UNIT 01</div>
  <div class="font-serif font-600 text-xl mt-2 text-[#F7F1E6]">Picture Generation Unit</div>
  <div class="text-sm text-[#B9A88F] mt-2">Processes raw sensor and vehicle-bus data into a graphical frame</div>
</div>

<div v-click="2" class="border p-5 transition-all duration-300" :class="$clicks >= 2 ? 'border-[#FF7A33]/60 bg-[#FF7A33]/5' : 'border-[#2A2018]'">
  <div class="font-mono text-xs text-[#FF7A33]">UNIT 02</div>
  <div class="font-serif font-600 text-xl mt-2 text-[#F7F1E6]">Optical Unit / Projector</div>
  <div class="text-sm text-[#B9A88F] mt-2">Generates and directs the light that carries the image</div>
</div>

<div v-click="3" class="border p-5 transition-all duration-300" :class="$clicks >= 3 ? 'border-[#FF7A33]/60 bg-[#FF7A33]/5' : 'border-[#2A2018]'">
  <div class="font-mono text-xs text-[#FF7A33]">UNIT 03</div>
  <div class="font-serif font-600 text-xl mt-2 text-[#F7F1E6]">Combiner</div>
  <div class="text-sm text-[#B9A88F] mt-2">The surface — windshield or a dedicated pane — where the final image becomes visible to the driver</div>
</div>

</div>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 02 — THEORETICAL FOUNDATIONS</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-2">HUD Technology Types</h1>
<div class="text-sm text-[#8C7E6C] mb-8">by position of the display surface</div>

<div class="flex flex-col gap-3 max-w-3xl">
  <div v-for="(item, i) in [
      { tag: 'HUD-C', title: 'Combiner-based', desc: 'A small transparent panel between dashboard and windshield — simplest, cheapest, narrower field of view.' },
      { tag: 'HUD-W', title: 'Windshield-based', desc: 'Image projected directly onto the windshield — better field of view; ~73% of the 2025 global market.' },
      { tag: 'HUD-AR', title: 'Augmented Reality', desc: 'Fuses map + ADAS data, aligning graphics precisely with real-world road objects — the most advanced generation.' },
    ]"
    :key="i"
    class="flex gap-5 items-start border-l-2 pl-5 py-3 transition-all duration-300"
    :class="$clicks > i ? 'border-[#FF7A33] bg-[#FF7A33]/5' : 'border-[#2A2018] opacity-40'">
    <div class="font-mono text-sm w-16 shrink-0" :class="$clicks > i ? 'text-[#FF7A33]' : 'text-[#8C7E6C]'">{{ item.tag }}</div>
    <div>
      <div class="font-serif font-600 text-lg text-[#F7F1E6]">{{ item.title }}</div>
      <div class="text-sm text-[#B9A88F] mt-1">{{ item.desc }}</div>
    </div>
  </div>
</div>

<div v-click="3" class="mt-6 font-mono text-xs text-[#FF7A33]">
  ↗ HUD-AR segment CAGR ≈ 16–17% globally — the industry is shifting toward augmented reality
</div>

</div>

---
transition: fade
---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 03 — RELATED WORK</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">International Landscape</h1>

<div class="space-y-5 max-w-3xl">

<v-click>
<div class="border-b border-[#2A2018] pb-4">
  <div class="font-serif font-600 text-lg text-[#F7F1E6]">Continental <span class="font-mono text-xs text-[#FF7A33] ml-2">~61% share, 2025</span></div>
  <div class="text-sm text-[#B9A88F] mt-1">Leading Tier-1 supplier of conventional HUDs — favored for reliability and lower cost versus AR systems</div>
</div>
</v-click>

<v-click>
<div class="border-b border-[#2A2018] pb-4">
  <div class="font-serif font-600 text-lg text-[#F7F1E6]">Envisics <span class="font-mono text-xs text-[#FF7A33] ml-2">holographic waveguide</span></div>
  <div class="text-sm text-[#B9A88F] mt-1">Supplies the HUD-AR system for the 2026 Cadillac Vistiq</div>
</div>
</v-click>

<v-click>
<div class="pb-2">
  <div class="font-serif font-600 text-lg text-[#F7F1E6]">UniMax <span class="font-mono text-xs text-[#FF7A33] ml-2">Taiwan, 2024</span></div>
  <div class="text-sm text-[#B9A88F] mt-1">Mirror-Array Vision Extender — cuts optical unit volume by 30%+ and removes ghosting</div>
</div>
</v-click>

</div>

<v-click>
<div class="mt-8 font-mono text-xs text-[#FF7A33] max-w-2xl">
  → The industry is moving quickly from simple optics toward compact, smarter solutions
</div>
</v-click>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 03 — RELATED WORK</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">The Iranian Market</h1>

<div class="space-y-4 max-w-2xl text-lg text-[#D9CFC0]">
<v-clicks>

- Products are sold almost entirely as **aftermarket, portable units**
- Typically a small LED/LCD panel plus a semi-transparent reflective piece
- Data comes from the **OBD-II port** or an internal **GPS receiver**
- Technologically equivalent to simple **HUD-C** — no AR, no factory integration
- No domestic industrial base for advanced components like waveguide combiners
- Activity is mostly limited to university projects and open-source prototyping (Arduino / Raspberry Pi)

</v-clicks>
</div>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 03 — RELATED WORK</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Open-Source DIY Prototypes</h1>

<div class="grid grid-cols-2 gap-6 max-w-4xl">

<v-click>
<div class="border border-[#2A2018] bg-[#120D09] p-5">
  <div class="font-mono text-xs text-[#FF7A33] mb-2">UNIVERSITY / HOBBYIST BUILDS</div>
  <div class="text-[#D9CFC0]">Raspberry Pi + PiTFT touchscreen + OBD-II adapter, optionally an IMU</div>
  <div class="font-mono text-2xl text-[#F7F1E6] mt-4">$100–150</div>
  <div class="text-xs text-[#8C7E6C]">total parts cost</div>
</div>
</v-click>

<v-click>
<div class="border border-[#2A2018] bg-[#120D09] p-5">
  <div class="font-mono text-xs text-[#FF7A33] mb-2">PIHUDDISPLAY PROJECT</div>
  <div class="text-[#D9CFC0]">Raspberry Pi 4B + ELM327 USB adapter + stretched display + custom beamsplitter + 3D-printed housing</div>
</div>
</v-click>

</div>

<v-click>
<div class="mt-8 font-mono text-xs text-[#FF7A33]">
  ✓ A working HUD prototype is achievable with accessible parts and a student-level budget
</div>
</v-click>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 04 — IMPLEMENTATION</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Proposed Components</h1>

<div class="max-w-3xl border border-[#2A2018]">
<div v-for="(row, i) in [
    ['Processing', 'Raspberry Pi 4, or ESP32 microcontroller'],
    ['Display', 'TFT / OLED, high brightness — image rendered mirror-flipped'],
    ['Optics', 'Beamsplitter panel at ~45°'],
    ['Vehicle data', 'OBD-II adapter, e.g. ELM327'],
    ['Positioning', 'GPS module + IMU (accelerometer / gyroscope)'],
    ['Software', 'Python — Pygame / PyQt, OpenCV for computer vision'],
  ]" :key="i"
  v-motion :initial="{ opacity: 0, x: -20 }" :enter="{ opacity: 1, x: 0, transition: { delay: i * 150 } }"
  class="grid grid-cols-[160px_1fr] gap-4 px-5 py-3" :class="i % 2 === 0 ? 'bg-[#120D09]' : ''">
  <div class="font-mono text-xs text-[#FF7A33] uppercase self-center">{{ row[0] }}</div>
  <div class="text-sm text-[#D9CFC0] self-center">{{ row[1] }}</div>
</div>
</div>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 05 — SYSTEM ARCHITECTURE</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-8">Proposed Architecture</h1>

<div class="flex flex-col gap-2.5 max-w-3xl">
<div
  v-for="(layer, i) in [
    ['Data sources', 'OBD-II adapter and optional IMU / GPS module'],
    ['Processing', 'Raspberry Pi reads, validates, and converts raw data into a graphics format'],
    ['Render & UI', 'Draws graphical elements on a scheduled cycle, roughly every 200–500ms'],
    ['Physical display', 'OLED/TFT panel shows the mirror-flipped image'],
    ['Optics', 'Beamsplitter combiner reflects a floating image into the driver’s line of sight'],
  ]"
  :key="i"
  v-motion
  :initial="{ x: -80, opacity: 0 }"
  :enter="{ x: 0, opacity: 1, transition: { delay: i * 280 } }"
  class="flex items-center gap-4 border-l-2 border-[#FF7A33] bg-[#120D09] pl-4 pr-5 py-3">
  <div class="font-mono text-xs text-[#FF7A33] w-6 shrink-0">L{{ i + 1 }}</div>
  <div class="font-serif font-600 text-[#F7F1E6] w-40 shrink-0">{{ layer[0] }}</div>
  <div class="text-sm text-[#B9A88F]">{{ layer[1] }}</div>
</div>
</div>

<v-click at="6">
<div class="mt-6 font-mono text-xs text-[#8C7E6C] max-w-2xl">
  Key constraints: minimize latency · maintain readability under direct sunlight · keep on-screen elements limited for safe HMI
</div>
</v-click>

</div>

---
transition: slide-up
---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 06 — METHODOLOGY</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-2">Research Methodology</h1>
<div class="text-sm text-[#8C7E6C] mb-10">Applied-developmental research</div>

<div class="grid grid-cols-2 gap-6 max-w-4xl">

<v-click>
<div class="border border-[#2A2018] bg-[#120D09] p-6">
  <div class="font-mono text-xs text-[#FF7A33] mb-2">DATA COLLECTION — PART 1</div>
  <div class="font-serif font-600 text-lg text-[#F7F1E6] mb-2">Literature Review</div>
  <div class="text-sm text-[#B9A88F]">Market analysis reports, technical documentation of active companies, and open-source project documentation</div>
</div>
</v-click>

<v-click>
<div class="border border-[#2A2018] bg-[#120D09] p-6">
  <div class="font-mono text-xs text-[#FF7A33] mb-2">DATA COLLECTION — PART 2</div>
  <div class="font-serif font-600 text-lg text-[#F7F1E6] mb-2">Iterative Prototyping</div>
  <div class="text-sm text-[#B9A88F]">Design → build → test → refine, in short repeated cycles until the final version matures</div>
</div>
</v-click>

</div>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 06 — METHODOLOGY</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Execution Roadmap</h1>

<div class="max-w-2xl">
<v-clicks>

<div class="flex gap-4 py-2.5 border-b border-[#2A2018]"><span class="font-mono text-[#FF7A33] w-6">01</span><span class="text-[#D9CFC0]">Study prior work; identify driver needs and technical/budget constraints</span></div>
<div class="flex gap-4 py-2.5 border-b border-[#2A2018]"><span class="font-mono text-[#FF7A33] w-6">02</span><span class="text-[#D9CFC0]">Design overall architecture; select hardware and software components</span></div>
<div class="flex gap-4 py-2.5 border-b border-[#2A2018]"><span class="font-mono text-[#FF7A33] w-6">03</span><span class="text-[#D9CFC0]">Source parts and wire up the initial hardware setup</span></div>
<div class="flex gap-4 py-2.5 border-b border-[#2A2018]"><span class="font-mono text-[#FF7A33] w-6">04</span><span class="text-[#D9CFC0]">Develop the data-acquisition, processing, and graphical UI software</span></div>
<div class="flex gap-4 py-2.5 border-b border-[#2A2018]"><span class="font-mono text-[#FF7A33] w-6">05</span><span class="text-[#D9CFC0]">Integrate components; run initial bench tests / simulated data</span></div>
<div class="flex gap-4 py-2.5"><span class="font-mono text-[#FF7A33] w-6">06</span><span class="text-[#D9CFC0]">Evaluate data accuracy, display latency, and readability</span></div>

</v-clicks>
</div>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FFC24B] mb-3">§ 07 — LIMITATIONS</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Challenges &amp; Constraints</h1>

<div class="grid grid-cols-2 gap-3 max-w-4xl">

<v-click><div class="border-l-2 border-[#FFC24B] bg-[#FFC24B]/5 p-4"><div class="font-serif font-600 text-[#F7F1E6]">Cognitive load &amp; safety</div><div class="text-sm text-[#B9A88F] mt-1">Poor design risks visual clutter and information overload</div></div></v-click>

<v-click><div class="border-l-2 border-[#FFC24B] bg-[#FFC24B]/5 p-4"><div class="font-serif font-600 text-[#F7F1E6]">Optical readability</div><div class="text-sm text-[#B9A88F] mt-1">Needs high-brightness (nit) displays for direct sunlight</div></div></v-click>

<v-click><div class="border-l-2 border-[#FFC24B] bg-[#FFC24B]/5 p-4"><div class="font-serif font-600 text-[#F7F1E6]">Ergonomic variation</div><div class="text-sm text-[#B9A88F] mt-1">Requires an adjustable optical unit for different driver heights and eye levels</div></div></v-click>

<v-click><div class="border-l-2 border-[#FFC24B] bg-[#FFC24B]/5 p-4"><div class="font-serif font-600 text-[#F7F1E6]">OBD-II inconsistency</div><div class="text-sm text-[#B9A88F] mt-1">Manufacturer-specific PIDs vary across vehicles</div></div></v-click>

<v-click><div class="border-l-2 border-[#FFC24B] bg-[#FFC24B]/5 p-4"><div class="font-serif font-600 text-[#F7F1E6]">Advanced optics cost</div><div class="text-sm text-[#B9A88F] mt-1">Waveguide combiners are out of reach for a student budget</div></div></v-click>

<v-click><div class="border-l-2 border-[#FFC24B] bg-[#FFC24B]/5 p-4"><div class="font-serif font-600 text-[#F7F1E6]">Regulatory concerns</div><div class="text-sm text-[#B9A88F] mt-1">In-vehicle field testing requires safety and legal review</div></div></v-click>

</div>

</div>

---
layout: center
class: text-center
---

<div class="max-w-3xl mx-auto">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-4">§ 08 — CONCLUSION</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Conclusion</h1>

<div class="space-y-4 text-lg text-[#D9CFC0] text-left">
<v-clicks>

- HUD reduces distraction and improves safety by displaying data directly in the driver's line of sight
- The industry is shifting from simple combiner-based solutions toward advanced AR systems
- Iran's domestic market still relies heavily on simple aftermarket products
- A functional, educational prototype is **fully achievable** with open-source components

</v-clicks>
</div>

</div>

---

<div class="hud-rail"></div>

<div class="h-full flex flex-col justify-center pl-28 pr-20">

<div class="font-mono text-xs tracking-[0.35em] text-[#FF7A33] mb-3">§ 08 — CONCLUSION</div>
<h1 class="font-serif font-700 uppercase text-4xl text-[#F7F1E6] mb-10">Future Work</h1>

<div class="space-y-4 max-w-2xl text-lg text-[#D9CFC0]">
<v-clicks>

- Add basic AR features — route arrows aligned with GPS heading
- Improve the optical unit by testing cheaper semi-waveguide combiners in place of a simple beamsplitter
- Run in-vehicle field tests (with proper safety review)
- Conduct a UX evaluation with a group of real drivers

</v-clicks>
</div>

</div>

---
layout: center
class: text-center
---

<div class="absolute inset-0 flex items-center justify-center pointer-events-none">
  <div class="relative w-[820px] h-[380px]">
    <div class="absolute top-0 left-0 w-14 h-14 border-t-2 border-l-2 border-[#FF7A33]/60"></div>
    <div class="absolute top-0 right-0 w-14 h-14 border-t-2 border-r-2 border-[#FF7A33]/60"></div>
    <div class="absolute bottom-0 left-0 w-14 h-14 border-b-2 border-l-2 border-[#FF7A33]/60"></div>
    <div class="absolute bottom-0 right-0 w-14 h-14 border-b-2 border-r-2 border-[#FF7A33]/60"></div>
  </div>
</div>

<div class="relative">
  <div class="font-mono text-xs tracking-[0.4em] text-[#FF7A33] mb-6">END OF TRANSMISSION</div>
  <h1 class="font-serif font-800 uppercase text-5xl text-[#F7F1E6]">Thank You</h1>
  <div class="font-mono text-sm text-[#B9A88F] mt-6">Questions and feedback are welcome</div>
  <div class="flex items-center justify-center gap-3 my-8">
    <div class="w-16 h-px bg-[#FF7A33]/50"></div>
    <div class="w-1.5 h-1.5 rotate-45 bg-[#FF7A33]"></div>
    <div class="w-16 h-px bg-[#FF7A33]/50"></div>
  </div>
  <div class="font-mono text-xs text-[#8C7E6C]">
    Alireza Hassani Eghtedar &nbsp;·&nbsp; Research Methodology &nbsp;·&nbsp; Kharazmi University
  </div>
</div>

<style>
/*
  Signature element used across content slides: a vertical HUD "speed tape"
  rail — the tick-mark strip a real automotive/avionics HUD renders in the
  driver's peripheral vision. Kept quiet and consistent instead of a
  repeated corner-bracket frame, and grounded in how the actual instrument
  works rather than a decorative flourish.
*/
.hud-rail {
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 56px;
  pointer-events: none;
  background-image: repeating-linear-gradient(
    to bottom,
    rgba(255, 122, 51, 0.35) 0px,
    rgba(255, 122, 51, 0.35) 1px,
    transparent 1px,
    transparent 28px
  );
  background-position: 40px 0;
  opacity: 0.5;
}
.hud-rail::before {
  content: '';
  position: absolute;
  left: 40px;
  top: 0;
  bottom: 0;
  width: 1px;
  background: linear-gradient(to bottom, transparent, rgba(255,122,51,0.25) 15%, rgba(255,122,51,0.25) 85%, transparent);
}
.slidev-layout {
  background-image: repeating-linear-gradient(to bottom, rgba(255,255,255,0.012) 0px, rgba(255,255,255,0.012) 1px, transparent 1px, transparent 3px);
}
</style>

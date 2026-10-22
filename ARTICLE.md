# PEM Water Electrolyzer Stack, Animated: A Code-Driven Anatomy of How Hydrogen Is Made

### A 34-second, frame-accurate explainer that treats electrolysis with the honesty it deserves — electrons that don't cross the membrane, energy that's always consumed, and no fake purity guarantees.

**Try it live:** [pem-electrolyzer-explainer](https://mizcausevic-dev.github.io/pem-electrolyzer-explainer/) · **Source:** [GitHub repo](https://github.com/mizcausevic-dev/pem-electrolyzer-explainer)

---

Most "how electrolysis works" animations lie to you. Not maliciously — just conveniently. They show electrons hopping across a membrane that, in reality, stops them cold. They imply 100% pure hydrogen streams straight out of the cell. They frame electricity as if it were free, renewable, and infinite. And they almost never tell you the one fact that matters most: **electrolysis consumes energy. It always has. It always will.**

That's thermodynamics, not an opinion.

So I built something different: a **PEM water electrolyzer stack anatomy explainer** — a 34-second, code-driven, frame-accurate motion piece that shows the mechanism the way an engineer would draw it on a whiteboard, with every claim tagged by what kind of evidence it is. No fake dimensions. No invented efficiencies. No impossible service procedures. Just the anatomy, the pathways, and the truth about energy.

This article is the story of what it shows, why it's built that way, and how you can use it.

---

## What is a PEM water electrolyzer stack?

A **Proton Exchange Membrane (PEM) water electrolyzer** splits water into hydrogen and oxygen using electricity. "PEM" refers to the polymer membrane at the heart of each cell — a thin sheet that lets protons through but blocks electrons and gases. A **stack** is many of these cells bolted together in series between two end plates, so the voltage adds up and the gas output scales.

PEM electrolyzers matter because they're one of the leading pathways to **clean hydrogen** — the molecule that hard-to-decarbonize industries (steel, ammonia, long-haul transport, seasonal energy storage) need but can't get from fossil fuels without CO₂. The U.S. Department of Energy lays out the fundamentals [here](https://www.energy.gov/cmei/fuels/hydrogen-production-electrolysis).

But "clean hydrogen" is a claim about *where the electricity comes from*, not about the electrolyzer. The electrolyzer itself is a machine that **trades electrical energy for chemical energy**. That trade is the whole point, and the explainer keeps it in view the entire time.

---

## The anatomy, one layer at a time

A single PEM cell is a sandwich. From the anode side to the cathode side, the layers are:

1. **Bipolar plate** (anode) — structural, conducts current, carries flow channels for water and gas.
2. **Porous transport layer (PTL)** — a sintered metal or carbon cloth that spreads water and lets gas escape.
3. **Anode catalyst layer** — typically iridium-based; where water is oxidized.
4. **PEM membrane** — the proton-conducting, electron-blocking core.
5. **Cathode catalyst layer** — typically platinum-based; where protons become hydrogen.
6. **Porous transport layer (cathode)** — lets hydrogen gas out.
7. **Bipolar plate (cathode)** — mirrors the anode plate.

Stack five of those between two end plates, connect a DC supply to the end plates, feed water, and you get oxygen out the anode side and hydrogen out the cathode side. That's the whole machine.

The explainer renders exactly this sandwich, with the repeating cells visible and the end plates labeled with their polarity (`+` anode, `−` cathode).

---

## The two half-reactions (and the energy truth)

Electrolysis isn't one reaction — it's two, one at each electrode:

- **Anode (oxidation):** `2 H₂O → O₂ + 4 H⁺ + 4 e⁻`
- **Cathode (reduction):** `4 H⁺ + 4 e⁻ → 2 H₂`
- **Overall:** `2 H₂O → 2 H₂ + O₂`

Three things have to line up for this to work, and the explainer shows all three simultaneously:

- **Protons (H⁺)** cross the membrane from anode to cathode. This is the internal charge pathway.
- **Electrons (e⁻)** cannot cross the membrane. They're forced to go the long way — out through the external circuit, through the power supply, and back into the cathode. That's the external charge pathway.
- **Energy** flows *into* the system from the power supply. The Gibbs free energy change is **positive** (`ΔG > 0`), meaning the reaction is endothermic and will not happen on its own. You pay for every molecule of hydrogen you make.

This is the part most animations blur. The explainer colors the pathways so you can't miss them: **cyan** for the proton transport across the membrane, **gold** for the electrons routing through the external circuit, **violet** for the polarity and energy-direction state overlays.

---

## Where most explainer animations go wrong

I've watched a lot of electrolysis animations. The same four errors show up again and again:

1. **Electrons cross the membrane.** They don't. In an ideal PEM, the membrane is an electronic insulator. If electrons crossed, you'd have a short circuit and no useful product. The explainer labels the membrane explicitly: *"electrons do NOT cross."*

2. **Zero crossover / purity guarantees.** Real stacks have gas crossover — a little hydrogen leaks to the anode side, a little oxygen to the cathode. Output is never 100% pure straight out of the cell; it gets purified downstream. The explainer states on-screen: *"Crossover is non-zero in real stacks."*

3. **Electricity assumed renewable.** An electrolyzer doesn't know or care whether its electrons came from solar, wind, or a coal plant. "Green hydrogen" is a *system* claim, not a *device* claim. The explainer makes **no renewable-source assumption**.

4. **Invented performance numbers.** Exact voltages, efficiencies, and dimensions are equipment-specific and proprietary. The explainer invents none of them. It shows the thermodynamic minimum (~1.23 V) only as a labeled textbook value and marks practical cell voltage as qualitative.

Every on-screen label is tagged by evidence type — `PHYSICAL`, `MEASURED`, `INFERRED`, `CONCEPTUAL`, `MATH`, or `SIGNAL` — so you always know whether you're looking at a real component, a measured quantity, an inference, or a schematic abstraction.

---

## The design system: color, camera, and a deterministic timeline

**Color is explanatory, not literal.** The palette is restrained and assigned by function:

- `#0B1019` — dark technical stage
- `#344257` — muted structural materials (plates, PTLs)
- `#00E5FF` cyan — the primary transport pathway (protons)
- `#FFD166` gold — energy and actuation (electrons, power supply)
- `#9D4EDD` violet — control and state overlays (polarity, ΔG)

Physical products (water, oxygen, hydrogen) are rendered in muted, plausible colors so they never compete with the saturated "signal" overlays. Nothing is glowing because it's glowing — it's glowing because it's the thing you're supposed to follow.

**The camera is continuous macro-to-micro-to-macro.** Six keyframes with cubic easing carry your eye from the whole stack, into the anode catalyst interface, across the membrane and external circuit, into the cathode, and back out to the full system boundary. There are no cuts — the motion itself is the connective tissue between stages.

**The timeline is deterministic and frame-driven.** The piece is 34 seconds at 30 fps = **1,020 frames, indexed 0–1019**. Every pixel is a pure function of the frame index. There's no randomness in playback, no drift. Scrub to frame 600 and you get exactly frame 600, every time. That makes it screenshot-safe, testable, and reproducible — which matters if you're embedding frames in a slide deck or a paper.

---

## A walkthrough of the five segments

| Frames | Time | What you see |
|---|---|---|
| 0–149 | 0–5 s | **Reveal.** The full stack: repeating cells, water feed, DC electrical input, separated O₂ and H₂ outlets, end plates with polarity. |
| 150–299 | 5–10 s | **Anode interface.** Camera pushes into the anode catalyst layer supplied with water. |
| 300–509 | 10–17 s | **The split.** Oxygen evolves at the anode, protons cross the membrane, electrons travel the powered external circuit. Anode half-reaction inset appears. |
| 510–749 | 17–25 s | **Hydrogen forms.** Cathodic H₂ evolution and distinct gas collection. Cathode half-reaction inset appears. |
| 750–1019 | 25–34 s | **System boundary.** Pull back to all inputs (electricity, water) and outputs (hydrogen, oxygen, waste heat) with the overall reaction and energy balance. Ends on a stable, complete-system view. |

Two accuracy tags appear during the molecular segments and then leave: a **time-compression** tag (~10⁶×, because molecular events are shown in slow motion) and a **scale-exaggeration** note. The footer always reads: *"CUTAWAY / CONCEPTUAL SCHEMATIC — INTERNAL VIEWS ARE NOT A SERVICEABLE ASSEMBLY."* That last line is important — it stops anyone from mistaking an exploded cross-section for a procedure you can perform.

---

## How to use it

The live preview has full transport controls:

- **Play / Pause** and **Restart**
- A **scrubber** to seek any of the 1,020 frames
- A **speed** selector (0.25× to 2×)
- A **deep-link** hash: append `#f=400` to the URL to jump straight to frame 400 and pause there — handy for linking a specific moment in a tweet, a doc, or a slide.

Because it's a single self-contained `index.html` (Canvas 2D, vanilla JS, no dependencies, no network calls), you can also save the page and run it offline, embed it in an iframe, or host it anywhere static.

---

## Open source

The whole thing is one file and it's public:

- **Live preview:** [pem-electrolyzer-explainer on GitHub Pages](https://mizcausevic-dev.github.io/pem-electrolyzer-explainer/)
- **Source:** [github.com/mizcausevic-dev/pem-electrolyzer-explainer](https://github.com/mizcausevic-dev/pem-electrolyzer-explainer)

It deploys from a `gh-pages` branch. Fork it, change the colors, swap in your own labels, or use it as a template for a different energy-systems anatomy piece.

---

## Who this is for

- **Educators** who want a hydrogen-production visual that won't embarrass them in front of thermodynamics-literate students.
- **Engineers and founders** who need to explain PEM electrolysis to investors without overclaiming.
- **Policy and climate folks** who keep hearing "green hydrogen" and want to understand the device underneath the slogan.
- **Developers and designers** who care about building technical animations that are deterministic, accessible, and honest about their own limits.

---

## What this is *not*

This is a **conceptual working brief, not a certified engineering design.** It will not tell you a cell's active area, its current density, its stack voltage at a given load, or its efficiency. It won't give you operating pressures, temperatures, or a startup procedure. It contains **no operating instructions for hazardous equipment**. If you're designing or buying a real electrolyzer, the mechanism here is a starting point — the geometry and the numbers come from the equipment vendor's documentation and your own engineering judgment.

The reference (DOE, linked above) supports the *mechanism*, not every artistic choice. Verify implementation-specific claims against primary sources.

---

## The bottom line

Hydrogen is going to be a big part of how we store and move clean energy — but only if we're honest about what it costs to make. An animation that hides the energy input, fakes the purity, and lets electrons cheat across the membrane isn't teaching electrolysis. It's selling a vibe.

This explainer does the opposite. It shows you the sandwich, the two half-reactions, the three pathways (mass, charge, energy), and the unflattering thermodynamic truth — `ΔG > 0`, always — in 34 seconds of deterministic, frame-accurate motion.

**[Open it. Scrub it. Steal it.](https://mizcausevic-dev.github.io/pem-electrolyzer-explainer/)** Just don't pretend the electricity is free.

---

*Topics: Hydrogen · Clean Energy · PEM Electrolysis · Data Visualization · Technical Animation · Energy Systems · Green Hydrogen · Decarbonization · Developer · Open Source*

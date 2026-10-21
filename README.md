# PEM Water Electrolyzer Stack — Anatomy Motion Explainer

A code-driven, anatomy-style motion explainer for a **Proton Exchange Membrane (PEM) water electrolyzer stack**. Single-file, dependency-free, deterministic frame-driven timeline.

- **Duration:** 34 s @ 30 fps = 1,020 frames (indexed 0–1019)
- **Category:** Energy Systems
- **Format:** One self-contained `index.html` (Canvas 2D + vanilla JS). No build step, no external libraries, no network calls.

## What it shows

A continuous macro-to-micro camera move through the stack, then a pull-back to the full system boundary:

| Frames | Time | Segment |
|---|---|---|
| 0–149 | 0–5 s | S1 — Reveal repeating cells, water feed, DC input, separated gas outlets |
| 150–299 | 5–10 s | S2 — Anode catalyst interface supplied with water |
| 300–509 | 10–17 s | S3 — O2 evolution, H+ crossing the membrane, e− via the external circuit |
| 510–749 | 17–25 s | S4 — Cathodic H2 formation and distinct gas collection |
| 750–1019 | 25–34 s | S5 — Pull back to inputs (electricity, water) and outputs (H2, O2, waste heat) |

## Accuracy posture

This is a **conceptual working brief, not a certified engineering design**. The animation enforces the following explicitly on-screen:

- Electrolysis **consumes** energy (ΔG > 0, endothermic).
- Electrons do **not** cross an ideal PEM membrane; they are routed through the powered external circuit.
- Protons (H+) carry charge across the membrane (anode → cathode).
- No zero-crossover, purity guarantee, or renewable-source assumption is made.
- No exact dimensions, settings, proprietary internals, efficiencies, or guaranteed performance are implied.
- Internal views are a labeled **cutaway / conceptual schematic**, not a serviceable assembly.
- Molecular events are shown in **slow motion** with an on-screen time-compression tag (~10^6×) and a scale-exaggeration note.
- Every label is tagged by evidence type: `PHYSICAL`, `MEASURED`, `INFERRED`, `CONCEPTUAL`, `MATH`, `SIGNAL`.

Half-reactions shown as math insets:
- Anode (oxidation): `2 H2O → O2 + 4 H+ + 4 e−`
- Cathode (reduction): `4 H+ + 4 e− → 2 H2`
- Overall: `2 H2O → 2 H2 + O2`

## Controls

- **Play / Pause** and **Restart** buttons.
- **Scrubber** to seek any frame 0–1019.
- **Speed** selector (0.25× – 2×).
- URL hash `#f=NNN` jumps to and pauses on a specific frame (used for deterministic screenshots).

## Reference

Mechanism reference (supports the mechanism, not every artistic choice):
- U.S. DOE, *Hydrogen Production: Electrolysis* — https://www.energy.gov/cmei/fuels/hydrogen-production-electrolysis

Verify implementation-specific geometry and any publication claims against selected equipment documentation.

## Run locally

Open `index.html` directly in a browser. No server required.

## Deploy (GitHub Pages)

This repo includes a workflow at `.github/workflows/pages.yml` that publishes the site to GitHub Pages on every push to `main`. After pushing:

1. Repo → **Settings → Pages → Build and deployment → Source: GitHub Actions**.
2. The workflow runs on the next push and deploys to `https://<user>.github.io/<repo>/`.

## License

MIT. The conceptual schematic is explanatory; it is not a certified engineering design.

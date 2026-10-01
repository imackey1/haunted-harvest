# The Haunted Harvest: Monsters' City Street

A Halloween experience built with **only HTML5 and CSS3**. There is no JavaScript anywhere in the project: no `<script>` tags, no inline event handlers, no `javascript:` links.

**Scene option:** Option 4, Monsters' City Street
**Author:** Ibrahim Mackey (solo project)

![Main Street](assets/preview-street.png)

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Semantic page: header, nav, effect switches, three scenes, footer, hidden SVG artwork library |
| `haunted-harvest.css` | The single stylesheet (palette variables, layout, scenes, animation, responsive, reduced motion) |
| `assets/favicon.svg` | Pumpkin favicon |
| `assets/preview-*.png` | Screenshots of each scene |

## The three scenes

Scenes are switched with the CSS `:target` selector, so the URL hash decides what shows (`#street`, `#boutique`, `#rooftops`). The nav links, and the doors, ladders and hatch inside the scenes, are all ordinary anchor links.

| Scene | People | Animals | Weather | Vehicle / object in motion | Halloween theme |
| --- | --- | --- | --- | --- | --- |
| **Main Street** `#street` | Witch, vampire and sheet-ghost trick-or-treaters; a zombie | Black cat on the fence, dog in a pumpkin vest, bats | Rolling fog, windblown leaves | Hearse with spinning wheels and headlights; swinging paper lantern | Full moon, jack-o'-lanterns, flickering windows |
| **Costume Boutique** `#boutique` | Waving shopkeeper, two customers | Cat flicking its tail, hanging bats, a spider on a thread | Rain and lightning on the window | Taxi passing the window; spinning ceiling fan; swaying costume rack | Costumes, candy jars, twinkling string lights |
| **Rooftops** `#rooftops` | Skeleton and pumpkin-head dancers, a stargazer, a balloon rider | Blinking owl, prowling cat, bats | Storm clouds, lightning, wind-blown bunting and leaves | Witch on a broom, drifting pumpkin balloon, swinging weather vane | Harvest moon, bunting, chimney smoke |

Each scene also has a "What is happening here?" `<details>` panel that lists these elements in text, so the content is available without seeing the animation.

## Required CSS-only features

* **`:target` scene switching**: starter rules kept, with `:has()` so Main Street shows by default.
* **`:hover` / `:focus` micro-interactions**: nav pills lift and glow; doors, ladders and hatch light up and brighten their signs; jack-o'-lanterns scale up; cats' eyes change colour; effect switches glow.
* **Checkbox-hack toggles** (real `<input type="checkbox">` plus `<label>`, so mouse, touch and keyboard all work):
  * *Thicker mist*, *Candy confetti* and *Candle glow* switches at the top, using `:has(:checked)`.
  * Clickable jack-o'-lanterns in every scene that light up.
* **`@keyframes` ambient animation**: 46 keyframe sets: walking with leg swing, flapping bats, wheel spin, rain, fog loops, lightning, flicker, dancing, swaying, and more.

## Design system

* **Palette** lives in `:root` as `--pumpkin`, `--candy-purple`, `--spider-black`, `--slime-green`, `--ghost-white`, `--candle-glow`. A few supporting shades (`--purple-light`, `--blood`, skin tones and so on) sit next to them. SVG artwork is coloured through utility classes that read those variables.
* **Typography**: Creepster for display headings and Poppins for body text (loaded with one `@import` at the top of the stylesheet), with `Segoe UI` and system fonts as fallbacks.
* **Scaling**: each stage defines `--u` as `1cqw` (1% of the stage width, with a `1vw` fallback), so everything inside a scene scales together. Per-sprite position and speed are set with small custom properties (`--x`, `--y`, `--w`, `--dur`, `--delay`).
* **Loops**: walkers animate `left` across the stage. Their negative `--delay` values start them at the positions in `--x`, so the scene is composed from the first frame.

## Accessibility

* Semantic landmarks (`header`, `nav`, `main`, `footer`), one `h1`, an `h2` per scene, a skip link, and `lang="en"`.
* Every decorative SVG is `aria-hidden`; each stage is a labelled `role="group"` with a text description.
* Visible focus ring (3px candle-glow outline) on every link, switch, pumpkin, and `<summary>`.
* Touch targets of at least 44px for nav, switches and pumpkins.
* Contrast (WCAG 2.x): body text 16.2:1, nav text 9.3:1, active nav 6.7:1, headings 6.7 to 12.7:1, sign text 12.7:1. All pass AA.
* No flashing above 3 per second; lightning is a gentle, low-opacity double flash every 9 to 11 seconds.
* **`prefers-reduced-motion: reduce`**: every animation and transition is switched off (`animation: none`). Each moving item has a sensible resting position in its base rule, so scenes still read as complete still images. This replaces the starter rule, which shortened animations instead of stopping them.

## Responsive

Mobile-first. The stage is 4:5 on phones, 4:3 from 640px, and 16:10 from 960px. Checked for horizontal overflow at 320, 360, 390, 480, 640, 768, 1024, 1280 and 1440px: none at any width.

## Browser support

Requires `:has()` and container query units: current Chrome, Edge, Safari 16+, and Firefox 121+.

## Run it locally

Open `index.html` in a browser. No build step, no dependencies.

## GitHub and deployment checklist

1. Create a public repo (for example `haunted-harvest`) and push this folder with a few real commits (for example: starter + palette, Main Street, Boutique, Rooftops, accessibility pass, README).
2. Deploy `index.html`, `haunted-harvest.css` and `assets/` to Codd so the URL serves `index.html`.
3. Fill in `submission_Template_halloween.html` with the GitHub URL and the deployed URL.

## Credits

All artwork is hand-built inline SVG and CSS. Fonts: Creepster and Poppins from Google Fonts.

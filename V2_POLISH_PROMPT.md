# v2 polish — six fixes to make the current site land

paste this into the same claude.ai/design conversation that produced
`hours i live v2.html`. it knows the file. each fix is self-contained
and can be done in one pass. keep all chrome visible — clock,
now-strip, floorplan, ticker, marginalia all stay. we are not trimming.

**ground rule (this matters):** v2 works because it's built from
typography, hand-coded SVG components, and *her real artwork* from the
art folder. it does NOT work because of generated images. so for every
fix below, prefer real photos placed by hand over AI-generated images.
where AI gen is the fallback, generate at small scales (single product,
single object) and never try one big composition. the previous attempt
(v3) failed because it gambled on a big AI panorama.

work in this order. don't skip.

---

## fix 01 — the desk has placeholder gradient cards. replace with real packaging.

right now (lines ~336–377 of v2) every desk item is a colored gradient
`.obj-art` with a `.shape` div that just says "cazy / catze" or
"memory / milk" in italic type. these are wireframes. they need to be
**her actual packaging photos** — the ones she posted on instagram.

**preferred path (do this if at all possible).** the user has these
images already. they will save 7 files into `art/desk/`:

```
art/desk/cazy.jpg   — Cazy Catze Club coffee labelling
art/desk/kiwi.jpg   — KiwiKoi Jam jars
art/desk/khwa.jpg   — khwa-sau confectionery
art/desk/hot.jpg    — Hot Pot food packaging
art/desk/milk.jpg   — Memory Milk / Blueberry Milk carton
art/desk/wick.jpg   — The Wagging Wick candle
art/desk/sun.jpg    — Sunscreen packaging
```

if those files exist, use them. set `.obj-art` to
`overflow:hidden; background:none;` and add `.obj-art img { width:
100%; height: 100%; object-fit: cover; display: block; }`. delete the
gradient + `.shape` rules for `.cazy`, `.kiwi`, `.khwa`, `.hot`,
`.milk`, `.wick`, `.sun`. wire each project's `data-spread.img` to the
same file so the modal opens with the real artwork too.

**fallback only if a file is missing.** for each missing one, generate
a single small image (720×720, single product, not a composition).
this is a single-object job, much safer than a panorama. style modifier
for every fallback image:

> warm cream paper background, soft daylight from upper left, gentle
> shadow underneath, top-down 3/4 view, paper grain visible, hand-drawn
> editorial illustration style with subtle gouache + coloured pencil
> texture, ochre + terracotta + cream + espresso palette, indian indie
> design studio aesthetic, no AI gloss, no 3D render look, no glass
> highlights, slight imperfection in the linework, no faces, no text
> visible on the product (we'll layer the typography over it)

then per-object fallback prompts:

1. **Cazy Catze Club (coffee)** — three small-batch coffee cans, kraft
   brown label with a half-asleep cat illustration in the centre,
   hand-set serif logotype "Cazy Catze Club". one can lying on its
   side, two upright. coffee bean scatter beside them.
2. **KiwiKoi Jam** — three glass jam jars on a wooden surface, hand-
   painted gouache fruit labels (kiwi, strawberry, plum), one with the
   lid off and a tiny wooden spoon resting on the edge.
3. **khwa-sau (confectionery)** — a small cream-coloured rectangular
   sweet box with soft serif typography reading "khwa-sau". one open,
   showing two pieces of mithai inside. wrapper paper trailing.
4. **Hot Pot (food)** — a terracotta paper take-home box, illustration
   of steam rising and a small dal-katori on the label, sitting beside
   a stack of warm rotis on a banana leaf.
5. **Memory Milk (dairy)** — a soft pastel milk carton, painterly
   cloud illustration on the front, small jingle "for the days you
   forget where you left them" set under the name in lowercase serif.
   condensation on the surface.
6. **The Wagging Wick (candle)** — a hand-drawn dachshund on a cream
   candle box, the candle (lit) standing beside it, a small wisp of
   smoke.
7. **Sunscreen (skincare)** — a playful lemon-yellow tube and a small
   cream pump bottle. illustration of citrus rind + a beach towel
   pattern. set against the cream paper.

also use the same image for the modal's "left page" hi-res (it
currently shows a placeholder "[a hi-res scan would live here]" for
desk items — wire `data-spread` `img` field for each).

---

## fix 02 — the window has no outside view. give it sky + a switching scene.

right now (hour 18) the window is three colored building divs over a
flat gradient. the brief promised the view changes with time. do this:

- replace the `.window .frame` background with a **gradient that's
  driven by the CSS variables** so it lerps with the rest of the page.
  set up `--sky-near` and `--sky-far` tokens for each palette entry in
  JS — at 09:00 cream-blue, 12:00 bright blue, 15:00 amber, 18:00 rose
  + violet, 21:00 deep indigo, 00:00 ink with a faint star field.
- buildings stay, but their windows light up after 18:00 (toggle a
  body class `.evening` when hour ≥ 18 or < 6; in CSS make `.window
  .window-light { background: var(--lamp); box-shadow: 0 0 12px
  var(--lamp); }` only when `.evening`).
- add **stars** — a single absolutely-positioned SVG with ~40 small
  white circles at random positions, opacity 0 by default, opacity
  .85 when `.dark` body class. add a slow twinkle animation on each.
- add **one moon** — small bone-coloured circle, top-left of window,
  only visible when `.dark`.
- add **rain** during 21:00 (an optional `.weather-rain` body class
  toggled from the now-strip "weather" line — if the weather string
  contains "drizzle" or "monsoon", turn on rain). small diagonal lines
  with a 1.2s loop, low opacity.

copy stays the same. the polaroid + pinned links sit on top — keep
them as they are.

---

## fix 03 — the mug doesn't actually speak. make the steam *become* the letters.

hour 00 right now has a mug SVG on the left and a separate letter card
on the right. they don't connect. the poetic move is missing.

rebuild:

- the mug sits centered, smaller (~140px wide).
- the steam SVG sits above it, wider (~360px), with three curved
  paths.
- the letter text is rendered **on a layer above the steam**, with the
  text following a curved baseline that traces the right-most steam
  path. use SVG `<textPath>` with the existing steam path's `id`.
- the letter text fades in word-by-word over 4 seconds (use
  `text-shadow` reveal or wrap each word in a span with staggered
  `animation-delay`).
- when the user clicks "next →", the current letter "dissolves up"
  (translateY -40px + opacity 0 over .6s) and the next one fades in
  with the same word-by-word effect.
- the steam keeps drifting up regardless.

if `<textPath>` curving is too fiddly, fall back to: render the
letter inside an angled `<div>` with a slight `transform: rotate(-2deg)
skewY(-1deg)` so it visually flows from the steam, with a soft cream
`background: rgba(--panel, .8); backdrop-filter: blur(2px);`.

---

## fix 04 — Bakachcha needs to actually look like a cat.

`.cat` is currently a small abstract shape that animates across the
screen. she's the mascot — she should be visible enough to recognise.

replace the contents of `<div class="cat" id="cat">` with this inline
SVG (a small tabby tabby silhouette):

```html
<svg viewBox="0 0 80 60" width="64" height="48" aria-hidden="true">
  <!-- body -->
  <path d="M8 44 Q 12 28, 26 28 L 54 28 Q 70 28, 72 44 L 72 50 L 8 50 Z"
        fill="var(--cat-grey)"/>
  <!-- head -->
  <circle cx="22" cy="26" r="11" fill="var(--cat-grey)"/>
  <!-- ears -->
  <path d="M14 18 L 12 8 L 20 16 Z" fill="var(--cat-grey)"/>
  <path d="M30 16 L 32 6 L 24 14 Z" fill="var(--cat-grey)"/>
  <!-- tail -->
  <path d="M70 44 Q 80 30, 76 18" stroke="var(--cat-grey)"
        stroke-width="6" fill="none" stroke-linecap="round"/>
  <!-- stripes -->
  <path d="M30 30 L 38 30 M 42 30 L 50 30 M 54 30 L 62 30"
        stroke="rgba(0,0,0,.35)" stroke-width="2" stroke-linecap="round"/>
  <!-- eyes -->
  <circle cx="18" cy="24" r="1.5" fill="#1a1a1a"/>
  <circle cx="26" cy="24" r="1.5" fill="#1a1a1a"/>
  <!-- legs -->
  <rect x="16" y="46" width="6" height="8" fill="var(--cat-grey)"/>
  <rect x="28" y="46" width="6" height="8" fill="var(--cat-grey)"/>
  <rect x="48" y="46" width="6" height="8" fill="var(--cat-grey)"/>
  <rect x="60" y="46" width="6" height="8" fill="var(--cat-grey)"/>
</svg>
```

bump `--cat-grey` to a slightly warmer tone `#9C8E7E`. set
`.cat { width: 64px; height: 48px; filter: drop-shadow(0 2px 0 var(--shadow)); }`.
add a tail-wag keyframe — animate just the tail `<path>` with a
slight `transform-origin: 70px 44px; transform: rotate(...)` cycle.

also: when she walks, make her steps. add a CSS `animation: catbob 0.4s
infinite alternate` that translateY's by 2px. so she bobs as she walks.

on click, instead of just a toast, **she sits down for 3s and a small
speech bubble appears** with one of these lines (rotate):
- "meow. you found me."
- "i was on the kettle. don't tell."
- "the K in KiwiKoi is fine."
- "back to my nap."

---

## fix 05 — the door is a styled div. give it warm light spilling out.

epilogue right now is `<div class="door" aria-hidden="true"></div>` —
a flat rectangle. the brief said "a single illustrated door, slightly
ajar, warm light spilling from behind it." build that:

```html
<div class="door-scene" aria-hidden="true">
  <div class="door-frame">
    <div class="door-panel ajar"></div>
    <div class="door-handle"></div>
    <div class="door-light"></div>
  </div>
  <div class="floor-spill"></div>
</div>
```

CSS:
- `.door-frame`: 220px wide × 360px tall, brick-coloured border, sits
  vertically centered above the form.
- `.door-panel.ajar`: dark espresso wood, transform-origin on the
  hinge (left side), rotated `rotate3d(0,1,0,-22deg)` so it looks
  pushed open. inset shadow.
- `.door-light`: positioned absolutely behind the door panel — a
  radial gradient `from var(--lamp) to transparent`, sized so it
  spills out of the gap. opacity bumps when `.dark` body class is on.
- `.floor-spill`: a wide diagonal `clip-path` polygon of
  `var(--lamp)` at 0.35 opacity, originating from the bottom of the
  door, fanning outward across the floor (~300px wide). soft blur.
- on hover of the door, the angle opens a little wider (-32deg) and
  the spill brightens 20%.

add a tiny floating mote of warm light inside the spill that drifts up
slowly — recycle the dust animation but tinted lamp-yellow.

---

## fix 06 — small wins that compound

these are quick and worth doing:

1. **the title hours i live in the prelude doesn't move.** add a slow
   ambient shimmer — `text-shadow: 0 0 0 currentColor` animating to
   `0 0 24px var(--lamp)` over 4s, looping. subtle.
2. **the curtain reveal** at the top is silent. on first scroll, play
   a faint paper-rustle (a 1.2s decoded WAV, muted by default unless
   the vinyl is already on — preserve user agency).
3. **footnotes only live on hour 06.** scatter 2 more — one in the
   desk outro ("brands i actually like"), one in the mug section
   ("kerning of one word"). same `.fn` markup pattern.
4. **the floorplan's "you" pin doesn't animate when it jumps.** add
   `transition: cx .35s cubic-bezier(.5,.1,.2,1), cy .35s
   cubic-bezier(.5,.1,.2,1);` to `.pin-dot` and `.you`.
5. **the studio-cam timestamps update but don't visibly tick.** when
   they change, briefly highlight the `.ts` with `--lamp` background
   for 600ms then fade back. tiny moment.
6. **add a single recipe-style card to the wall.** a hand-written
   "chai. badly." card with three steps in caveat font:
   `1. water. 2. forget about it. 3. milk in panic.` rotate -3deg.
7. **the ticker is too short.** add 8 more lines from this list:
   - "still thinking about that label"
   - "the cat sat on the cintiq"
   - "anuja called. didn't pick up."
   - "monsoon's two weeks early"
   - "rewrote the bio. twice."
   - "the chai went cold in the cup again"
   - "saved a postcard from the floor"
   - "1 unread email from january"

---

## test before shipping

after layering all six fixes:

1. open the file. let it sit on hour 09 (default). check the desk
   shows real packaging, not gradient cards.
2. scroll all the way down without interacting. watch the colors lerp
   continuously, the cat walk past, the now-strip values change.
3. scroll to hour 18 and watch the window's sky shift. wait for the
   `evening` body class to kick in — buildings should light up.
4. scroll to hour 00. the letters should reveal word-by-word, the
   steam should arc into the text path.
5. click bakachcha mid-walk. she should sit and speak.
6. land at the epilogue. push the door open with hover. the spill
   should brighten.
7. toggle the lamp — entire palette should flip and the door spill
   should intensify.

if anything breaks the existing 12 add-ons, you've gone too far.
roll back that change. the v2 chrome is non-negotiable.

— end of polish prompt —

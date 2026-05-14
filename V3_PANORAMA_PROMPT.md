# v3 — actually become the room

paste this into claude.ai/design as a **new** request, not a continuation
of v2. tell it: "build hours-i-live-v3.html as a fresh file. use the
full content/copy/data from v2 but rebuild around the concept below."

this is the **big one**. v2 was a portfolio that *talks about* a room.
v3 is a room. you scroll, the camera pans across one continuous
illustrated panorama, and the portfolio is embedded inside the room as
real objects. the time of day moves through the same panorama. it is
one drawing, lit seven ways, with a portfolio inside it.

---

## 1. the master illustration

we need **one panoramic illustration**, ~3200×1200 (or two stitched
1600×1200 panels). this is the room, drawn once. layered as separate
PNGs so individual objects can be hovered, lifted, swapped.

generate this in claude.ai/design (or stitch together generated tiles)
with this prompt:

> a single panoramic illustration of a cozy artist's studio room,
> drawn in warm gouache + coloured pencil style on cream paper. left
> to right across the panorama:
>
> **far left:** an unmade bed against the wall, sage-green blanket
> half on the floor. a bedside table with a half-finished mug of chai
> (steam rising), an open sketchbook with three doodles, a paperback
> face-down, an alarm clock reading 06:24, a pair of black-framed
> glasses, a hairtie, a small india-post stamp.
>
> **left of centre:** a tall wooden bookshelf, three shelves, books
> in cream/ochre/terracotta/espresso spines leaned at angles, some
> face-out. a small potted plant on top, a ceramic mushroom and a
> postcard tucked between the books. a tabby cat sleeping on the
> middle shelf. one book is upside down.
>
> **centre:** a wooden desk pushed against the wall. on the desk
> (left to right): a stack of packaging mockups (jam jars, coffee
> cans, a milk carton, a candle box), an open laptop (screen glowing
> a warm cream), a small ceramic lamp (off in the day, on at dusk), a
> cup of pens, paint tubes, masking tape, a small ceramic mug. a
> half-eaten biscuit on a plate beside the laptop. a single cat paw
> entering frame from behind the laptop.
>
> **right of centre:** a large window with curtains pulled back,
> showing a street scene outside — buildings, a tree, the sky. on the
> sill: a polaroid, a small notebook, a camera-roll strip.
>
> **right side:** a wall covered in pinned polaroids, sticky notes,
> a receipt, a torn ticket, a pressed leaf, a takeaway menu. taped
> with washi. one coffee-ring stain.
>
> **far right:** a wooden door, slightly ajar, with warm light
> spilling from behind it onto the floor.
>
> warm cream walls, soft daylight throughout, paper grain, indian
> indie design studio aesthetic, ochre + terracotta + cream +
> espresso palette, hand-drawn imperfect linework, no people, no
> faces, no AI gloss, no 3D render look. illustration only.

claude.ai/design should output this as the master scene at
`art/room/room-day.png`. then ask it to re-light the *same composition*
six more times by adjusting palette + light direction:

- `art/room/room-dawn.png` (06:00) — cool blue-grey, one warm streak
- `art/room/room-morning.png` (09:00) — soft cream wash
- `art/room/room-noon.png` (12:00) — bright golden, hard shadows
- `art/room/room-golden.png` (15:00) — amber, deep ochres
- `art/room/room-dusk.png` (18:00) — rose + violet, lamp begins to glow
- `art/room/room-evening.png` (21:00) — espresso with strong lamp pool
- `art/room/room-night.png` (00:00) — ink blue with tight warm lamp

all seven are the **same drawing**, only the light/palette differs.
this is what makes the time-of-day move convincing.

if the model can't keep composition stable across 7 renders, use the
day version as the base and overlay **multiplied color tints** for
the other six (the same approach v2 already uses for `--bg`).

---

## 2. the architecture — how scroll maps to the room

**this is the key idea.** the panorama is wider than the viewport. as
the user scrolls vertically (yes, vertically — keep the natural scroll
gesture), the **camera pans horizontally** across the room.

implementation:

```
+──────────────────────────────────────────────────────────────────+
│  body (long, ~700vh tall)                                        │
│                                                                  │
│  .stage (position: fixed; inset: 0; overflow: hidden)            │
│    .room-bg (position: absolute; top: 0; left: 0;                │
│              width: 320vw; height: 100%;                         │
│              transform: translateX(-XXvw))                       │
│                                                                  │
│    .room-hotspots (matches .room-bg, holds clickable areas)      │
│  .scenes (the long scroll: just text/copy panels, transparent)   │
│    .scene[data-x="0"]   — prelude (camera at 0%)                 │
│    .scene[data-x="6"]   — bedside (camera at 6%)                 │
│    .scene[data-x="20"]  — shelf  (camera at 20%)                 │
│    .scene[data-x="42"]  — desk   (camera at 42%)                 │
│    .scene[data-x="65"]  — window (camera at 65%)                 │
│    .scene[data-x="80"]  — wall   (camera at 80%)                 │
│    .scene[data-x="95"]  — door   (camera at 95%)                 │
└──────────────────────────────────────────────────────────────────+
```

JS on scroll: compute scroll progress 0..1 across the body. interpolate
between adjacent scene `data-x` values. set `.room-bg.style.transform
= translateX(-${camX}vw)`. the same scroll progress also drives the
time-of-day palette (which already exists in v2 — keep it). result:
**scroll forward → camera pans right + time moves forward**.

scroll is still vertical. the user's gesture is unchanged. but the
visual feels horizontal + temporal.

add gentle **layered parallax**:
- a background wall layer (slower, 0.7× the camera speed)
- a midground furniture layer (1.0×)
- a foreground "on the desk" objects layer (1.15×)
the depth should be felt, not announced.

---

## 3. objects in the room ARE the navigation

every hotspot in the panorama is interactive. hover → it lifts. click
→ a modal spread opens (use v2's modal — it's already perfect).

hotspots (positioned over the panorama):

| pos in room      | object         | opens                              |
| ---------------- | -------------- | ---------------------------------- |
| bedside table    | sketchbook     | "hi, i'm ylee" intro letter        |
| bedside table    | mug + chai     | "on overthinking" letter           |
| bookshelf book 1 | lamp staring   | illustration spread                |
| bookshelf book 2 | toe-ster       | illustration spread                |
| bookshelf book 3 | ribbon         | illustration spread                |
| bookshelf book 4 | am i right?    | illustration spread                |
| bookshelf book 5 | new days       | illustration spread                |
| bookshelf cat    | bakachcha      | letter on the cat                  |
| desk obj 1       | KiwiKoi jam    | packaging spread                   |
| desk obj 2       | Cazy Catze can | packaging spread                   |
| desk obj 3       | khwa-sau box   | packaging spread                   |
| desk obj 4       | Memory Milk    | packaging spread                   |
| desk obj 5       | Wagging Wick   | packaging spread                   |
| desk obj 6       | Hot Pot        | packaging spread                   |
| desk obj 7       | sunscreen      | packaging spread                   |
| desk             | laptop screen  | scrolling carousel of UI projects  |
| desk             | small lamp     | toggles day/night override         |
| desk             | record player  | toggles vinyl audio                |
| window sill      | polaroid       | links to instagram                 |
| window sill      | notebook       | links to cosmos board              |
| window sill      | camera roll    | links to @antiself                 |
| wall             | each polaroid  | hover = caption; click = enlarge   |
| wall             | sticky note    | hover = the line, no action        |
| door             | the door       | epilogue / contact form            |

hotspots are **invisible boxes positioned absolutely over the
panorama**. give each a translucent `outline: 1px dashed
var(--soft); outline-offset: 4px;` on hover so they feel hand-marked.

---

## 4. what happens to the v2 chrome

**keep all of it visible.** the user explicitly said so. but reposition:

- **clock + greeting** — top-right, same.
- **hours-lived counter** — top-right under clock, same.
- **floorplan minimap** — top-right under counter, smaller (90×120),
  doubles as the "where is the camera" indicator. the "you" pin now
  represents the camera position in the room, not section in viewport.
- **now-strip** — left side, slimmer (140px wide).
- **lamp + vinyl buttons** — bottom-right, same.
- **ticker tape** — bottom, full width, same.
- **marginalia** — still appears, but now anchored to the *room*
  (positioned over the panorama via `.room-margin` elements that
  pan with the camera). they appear when the camera is on their part
  of the room.
- **footnotes** — still inline in any text panel; same.
- **bakachcha the walker** — now walks across the room *floor*, not
  the viewport. she's part of the panorama plane.
- **guestbook + epilogue form** — appear when camera is near the
  door area, slide up from the bottom over the panorama.

---

## 5. mobile fallback

on screens < 900px wide, the horizontal-panorama approach breaks. fall
back to **a vertical stack of room vignettes** — each one a cropped
zoom into a part of the panorama (bedside zoom, shelf zoom, desk zoom,
etc). the same hotspots and modal. the time-of-day palette still
shifts. all the chrome compresses to a bottom drawer (clock + lamp +
ticker stay; now-strip collapses to a small "tap to expand" pill;
floorplan collapses to a single dot path).

at < 600px, the marginalia disappears (v2 already does this).

---

## 6. preserve from v2 (do not reinvent)

- the entire **copy deck** (every line of text, every hour title,
  every letter, every margin note, every ticker line, every guestbook
  card) — copy verbatim.
- the **time-of-day palette + lerp logic** in JS.
- the **modal spread** structure with what/tried/kept/change/note.
- the **process rejects** swatches inside the modal.
- the **letter carousel** (4 letters, prev/next, dots).
- the **footnote hover popovers**.
- the **guestbook** with the pin-it form and 6 starting cards.
- the **typography** stack (Cormorant Garamond Italic + Inter +
  Caveat + JetBrains Mono).
- the **cursor + ink trail** (it now trails across the panorama; feels
  right).

---

## 7. new things v3 introduces (beyond v2)

- the **room is the navigation**. portfolio grid is gone.
- **camera pan tied to scroll**.
- **same drawing, seven lights** for time of day.
- **layered parallax** across wall / furniture / desk-objects.
- a **tiny "deep-zoom" on shift-click** of any object — the camera
  pushes in, the panorama scales 1.6×, only that object is in focus.
  scrolling out (or escape) returns to the room view.
- **bakachcha lives in the room** — not floating across the viewport.
  she sleeps on the shelf, walks to the kitchen-side, sits on the
  desk. her position is tied to time of day (morning: kettle; noon:
  sunbeam on desk; evening: lap of an empty chair near the door).
- **the lamp** in the room *actually* turns on at dusk. when the
  camera reaches the dusk section, the lamp's "off" sprite swaps to
  the "on" sprite. that's the moment ylee's voice says "the lamp just
  clicked on." it should land *exactly* when the camera shows the
  lamp.
- the **door at the end opens** as the user scrolls into the final
  section — the door panel rotates progressively from 0deg (closed)
  at scroll 92% to -32deg (ajar, warm light pouring out) at 100%.

---

## 8. what success looks like

if a friend visits without context, they should think:
- "is this a website or an illustration?"
- "wait, the room is shifting."
- "oh — the lamp came on."
- "the cat just walked across."
- "there's stuff *on the desk*."
- "every object opens. this is her portfolio. inside a room."

if they ask "how do i navigate it" — you have failed. the answer
should be "you already are."

---

## 9. when stuck

the panorama composition is the hardest part. if claude.ai/design
struggles to draw one stable wide image, accept this fallback:

- generate the **scene per area** (bedside, shelf, desk, window, wall,
  door) at 1200×900 each.
- stitch them with `display: flex` in a wide flex row, all at 100vh
  tall, with hand-painted "seams" hidden under doorways / corners.
- the camera pan + parallax logic stays the same.

it won't be one continuous drawing — but it will *feel* like one
because the lighting and palette move continuously across all six.

---

## 10. the order to build in

1. master panorama (or 6 stitched panels) at noon-light. test the
   horizontal-pan-on-vertical-scroll. nothing else yet.
2. layer the time-of-day overlay so colors lerp across the room.
3. position hotspots over each object. wire v2's modal back in.
4. add v2's chrome (clock, now-strip, floorplan, ticker, lamp, vinyl,
   marginalia, footnotes).
5. add bakachcha-as-room-resident (not viewport-walker).
6. add the door-opens-on-scroll moment.
7. add deep-zoom on shift-click.
8. mobile fallback.
9. polish the seams.

if a stage breaks, fix it before adding the next. don't pile.

— end of v3 prompt —

# ylee.in — "hours i live"

A complete creative brief for claude.ai/design.
Paste this whole document in. It contains the concept, copy, visual system,
section-by-section builds, and asset direction.

---

## 0. The 30-second pitch (for claude.ai/design to read first)

Build a single-page, scroll-and-explore portfolio website for **ylee** — an
Indian designer & illustrator who makes warm, narrative, hand-drawn work in
packaging, brand identity, editorial illustration, and UI.

The website should NOT look like a portfolio. It should look and feel like
**stepping into ylee's room at different hours of the day**. The big concept
is called **"hours i live"** (borrowed from her own cosmos board name). The
whole site is a single illustrated room rendered in her aesthetic. As the
visitor scrolls, the **light changes** — dawn → morning → noon → golden
hour → dusk → lamp-lit night → midnight. Her portfolio is embedded in the
room as **objects you can hover and open**: books on the shelf are
illustrations, items on the desk are packaging projects, the laptop screen
holds her UI work, polaroids on the wall are personal moments, the window
shows the world outside (her friends, her cosmos board, links out), and the
cat — Bakachcha — wanders the page.

It should feel like reading someone's quietly perfect diary. Intimate,
hand-made, a little neurotic, very warm. The opposite of a slick agency
site.

The voice is **all lowercase, fragmented, self-aware, vulnerable, a little
funny**. Think "i overthink every pixel (so you don't have to)."

Below is everything you need.

---

## 1. Artist dossier

**Name:** ylee
**Domain:** ylee.in (currently redirects to a near-empty Framer page —
we're replacing it)
**Instagram:** @she.is.ylee · 78 posts · "i design, illustrate & overthink
every pixel (so you don't have to) let's collab. i love cats and art
@antiself._"
**Close orbit:** @antiself._ (Anuja) — best friend, photographer, curator
of the cosmos board "hours i live." Their aesthetics rhyme; ylee credits
her in her bio. We can reference Anuja's photography as ambient texture
(window views, polaroids) but the site is ylee's.

**What she does (and what should be on the site):**

1. **Packaging & brand identity**
   - *Cazy Catze Club* — coffee brand labelling
   - *KiwiKoi Jam* — jam jar branding with painterly fruit
   - *khwa-sau* — confectionery brand ("say with us")
   - *Hot Pot* — food packaging
   - *Blueberry Milk / Memory Milk* — soft pastel carton design
   - *The Wagging Wick* — candle brand, hand-drawn dachshund
   - *Sunscreen brand* — playful illustration packaging

2. **Editorial / narrative illustrations**
   - *Lamp Staring* — woman alone in a room, vinyl playing, weekend feel
   - *Toe-ster* — pun illustration (a foot in a toaster)
   - *RIBbon* — pun illustration (ribcage with a pink bow)
   - *AM I RIGHT?* — self-portrait + caption piece
   - *New Days Ordinary Streets* — moody street series
   - *At the end of loveless* — collage piece
   - *Quarter life crisis started* — feet on pavement piece
   - *A French affair* — typographic piece
   - Various warm scenes: people reading, cats by windows, vinyl players,
     coffee + bookshelves, two figures at golden hour, a boy with a book

3. **UI / web / digital**
   - *ylee's cosmos home* — a personal web mockup she's already designed
     (we honour this; "ylee's cosmos" is a phrase she uses)
   - Wallpaper design tutorials ("Illustrate a wallpaper with me")
   - Various dashboard / app mockups

4. **Personal / process**
   - Self-portraits, polaroids, her room, her sketchbook, her cat
     Bakachcha, mugs, lamps, vinyl, books, plane-window cloud sketches

**Aesthetic vocabulary (use these as touchstones):**
- Warm earth tones: cream, ochre, mustard, terracotta, burnt sienna,
  espresso brown, with one cool accent of dusty teal or night blue.
- Hand-drawn, slightly textured (paper grain, pencil edges, gouache feel)
- Cozy domestic interiors: rugs, lamps, plants, mugs of chai, bookshelves
- Cats. Always.
- Lowercase, intimate typography
- A diary energy. A "first cold morning of the year" energy. A
  "rewinding the cassette" energy.

**Voice (study these — write everything on the site in this register):**
- "i design, illustrate & overthink every pixel (so you don't have to)"
- "let's collab"
- "i love cats and art"
- "mugs make me happy"
- "Quarter life crisis started"
- "At the end of loveless"
- "New Days Ordinary Streets"
- "hours i live"
- Rules: all lowercase. comma splices welcome. fragments preferred over
  full sentences. self-aware asides in (parentheses). em-dashes — yes.
  Never corporate. Never "elevate your brand." Never "passionate creative."

---

## 2. The concept: **"hours i live"**

The website is **one continuous illustrated room** — ylee's room — that
the visitor explores. As you scroll vertically, **time of day passes** and
the room's light, palette, and ambient details shift. The portfolio is
embedded in the room as **interactive objects**. Navigation is by
**curiosity**, not by menu.

```
6am  dawn       — sleepy blue, sliver of warm light through curtain
9am  morning    — cream + butter yellow, kettle steam
12pm noon       — full warmth, mustard + sienna, cat naps in sunbeam
3pm  golden     — amber, deep ochres, dust in the light
6pm  dusk       — rose + violet, lamp clicks on
9pm  evening    — espresso brown, lamp-glow, vinyl plays
12am midnight   — ink-blue + cream, single warm lamp pool, stars
```

**The visitor lands at the hour their device clock says it is.** A small
clock in the corner ticks in real time. Scrolling forward moves time
forward. Scrolling backward rewinds. So the site is **literally different
at different times of day** — and you can also drag time forward.

The room is rendered as a wide, panoramic scene. Within it:

| Surface in the room   | What it holds                                 |
| --------------------- | --------------------------------------------- |
| **the desk**          | packaging & brand work                        |
| **the laptop screen** | UI / digital / web work                       |
| **the bookshelf**     | illustrations & editorial pieces              |
| **the wall** (collage)| polaroids, personal moments, behind-the-scenes|
| **the window**        | links out — cosmos board, instagram, friends  |
| **the door**          | contact / "let's collab"                      |
| **the cat (Bakachcha)** | wanders. follow her for easter eggs         |
| **the mug**           | thoughts / micro-blog / notes-from-ylee       |
| **the lamp**          | toggle day/night manually (overrides time)    |
| **the record player** | a soundtrack — ambient lo-fi when on          |

A small running counter in the corner reads:
**"i have lived 196,344 hours. 47 of them were spent on this navigation."**
(The first number is `years_alive * 24 * 365 + (today - dob)*24`, calculated
live. The second is a wink. Both are jokes about her overthinking.)

---

## 3. Visual system

### 3.1 Color palette

Use these exact tokens.

```css
--paper:        #F4EBD8;  /* cream wall / canvas */
--paper-warm:   #ECE0C6;  /* warmer cream for shadow side */
--ochre:        #D9A441;  /* mustard, primary warm */
--sienna:       #C8553D;  /* terracotta, used sparingly for accents */
--brick:        #A4503C;  /* deep terracotta for shadow */
--espresso:     #3D2817;  /* deep brown / text on light */
--bone:         #FAF6F0;  /* near-white, for highlights */
--lamp:         #F4C95D;  /* lamp glow yellow */
--ink:          #1A2332;  /* night blue / text on dark */
--dusk:         #5B4E6E;  /* dusty violet, for evening transitions */
--leaf:         #6B7A4A;  /* sage olive, for plant + accent */
--cat-grey:     #8C8479;  /* Bakachcha's coat */
```

Day mode uses `--paper`, `--ochre`, `--sienna`, `--espresso`. Night mode
flips to `--ink`, `--lamp`, `--bone`, `--dusk`. The transition is
**continuous**, not a toggle — colors lerp as you scroll.

### 3.2 Typography

Pair **one warm serif** with **one humanist sans** and **one handwritten
script** for margin notes. Recommended stack:

- **Display (headings):** *PP Editorial New Italic* — or fallback to
  *Cormorant Garamond Italic*. Used at large sizes for the section titles
  ("the desk", "the shelf"). Italic only, always.
- **Body:** *Söhne* or *Inter* at 16–18px, set in lowercase with generous
  line-height (1.7). Body text should always feel **letter-from-a-friend**,
  not website.
- **Margin notes / annotations:** *Caveat* or *Shadows Into Light* — for
  ylee's handwritten interjections that appear next to her work
  ("this one took 14 drafts ✦", "the cat helped").
- **Numerals & clock:** monospaced — *JetBrains Mono* or *IBM Plex Mono* at
  small sizes only. Used for the live clock and the "hours lived" counter.

Type rules:
- everything except proper nouns lowercase
- generous letter-spacing on display italics
- never use bold; use size and italic and color for hierarchy

### 3.3 Illustration & texture

The whole page should feel like **a single illustration** rather than a
grid of components. Specifically:

- **Paper grain overlay** on every section — a subtle noise/grain texture
  at ~6% opacity, multiplied over backgrounds.
- **Hand-drawn dividers** — wobbly lines, not 1px solid borders.
- **Soft drop shadows** — never harsh; think pencil-shaded shadow under
  every object.
- **Imperfect edges** — corners on cards should be hand-drawn-looking,
  slightly uneven `border-radius` (e.g., `border-radius: 24px 22px 26px
  23px / 25px 23px 25px 22px;`).
- **Sparkles & tiny doodles** — small ✦ ⊹ ✿ ✦ sprinkled at section
  joins. Star, asterisk, comma-like flourishes.

### 3.4 Cursor

Replace the default cursor with a **tiny ink-pen tip**. As the user moves,
**small ink dots** trail behind and fade out in 1.2s. On hoverable objects,
the cursor becomes a **paintbrush**. On clickable text, it becomes a
**small underline mark**. This is part of the "overthinking every pixel"
ethos.

---

## 4. Site map (one page, vertical scroll)

```
┌────────────────────────────────────────────────────────────┐
│   PRELUDE         the door (curtain rises)                 │
│                                                            │
│   HOUR 06:00      she wakes — sketchbook on bedside        │
│                                                            │
│   HOUR 09:00      the desk — packaging & brand work        │
│                   (Cazy Catze, KiwiKoi, khwa-sau, etc.)    │
│                                                            │
│   HOUR 12:00      the laptop — UI & digital work           │
│                                                            │
│   HOUR 15:00      the bookshelf — illustrations            │
│                                                            │
│   HOUR 18:00      the window — friends, cosmos, links out  │
│                                                            │
│   HOUR 21:00      the wall — polaroids, behind-the-scenes  │
│                                                            │
│   HOUR 00:00      the mug — letters from ylee (blog/notes) │
│                                                            │
│   EPILOGUE        the door — let's collab                  │
└────────────────────────────────────────────────────────────┘
```

Each section is **roughly 100vh tall** but blends into the next via
continuous illustrated room.

---

## 5. Section-by-section builds

For each section: copy goes verbatim into the page. Images describe what
to render — use claude.ai/design's image generation when an exact pull
isn't available. All images are warm, hand-illustrated, cream-paper
backgrounds, slightly textured.

---

### 5.1 PRELUDE — the curtain

**Layout:** Full viewport. A soft cream backdrop. Center, a small
illustrated curtained window with sliver of dawn behind it. Below the
window, two lines, large italic display:

> *hours i live*

Underneath, smaller, lowercase serif:

> by ylee. designer, illustrator, professional overthinker.
> (the lamp turns on around 6pm. the cat shows up whenever she wants.)

A whisper of text at the bottom:
> *scroll, or stay. either is fine.* ↓

**Interaction:** As the user begins to scroll, the curtain parts (CSS
clip-path animation) and the room is revealed.

**Top-right corner (sticky on all sections):**
- A live clock: `06:24` in mono.
- Below it, smaller: `you are visiting at dawn ☀︎`
- Below that, smaller still: `i have lived 196,344 hrs. 47 on this nav.`

---

### 5.2 HOUR 06:00 — she wakes

**Scene:** A bedside corner of the room. Crumpled bedsheet, a single mug
of half-finished chai (still steaming faintly — animate the steam), an
open sketchbook with three messy thumbnails, a paperback face-down. Light
is muted blue with one warm streak through the curtain.

**Headline (italic display, large):**
> *i don't believe in mornings. but they keep showing up.*

**Body (left of scene, narrow column):**
> hi, i'm ylee.
> i make things — usually with too much care.
>
> packaging, brand identity, illustrations, websites that should have
> been simpler. i live in the small overlap between **"is this good
> enough"** and **"did i ruin it again."**
>
> the rest of the day is on the other side of this scroll. come further.

**Interactive object:** The sketchbook. Hover → it flips open showing
three doodles that say "ideas," "doubts," "a list of cats i've seen."
Click → nothing happens. It's just the sketchbook. (This is the joke.)

---

### 5.3 HOUR 09:00 — the desk *(packaging & brand work)*

**Scene title (italic display):**
> *the desk — where i pretend to be organised.*

**Layout:** A wide, cluttered illustrated desk. Items on the desk are the
projects. Each is a real photographic crop of her work, **placed as
though it's sitting on the desk** with a soft drop shadow. Arrange them
in a slight angle, not a grid:

1. **Cazy Catze Club** — coffee cans + label mockup
2. **KiwiKoi Jam** — three jam jars with painted fruit labels
3. **khwa-sau** — confectionery box, "say with us"
4. **Hot Pot** — packaging on a wooden surface
5. **Blueberry Milk / Memory Milk** — soft pastel carton
6. **The Wagging Wick** — dachshund candle packaging
7. **Sunscreen brand** — playful illustrated packaging

Each project: **on hover, the desk dims slightly and that object lifts
up with a soft shadow**. A handwritten annotation in `Caveat` font
appears next to it. Examples:

- *Cazy Catze Club:* "their first round of feedback was 'more cat.' i
  obliged."
- *KiwiKoi Jam:* "painted each fruit twice. ate the leftover jam."
- *khwa-sau:* "the type was sitting wrong for three weeks until it
  wasn't."
- *Hot Pot:* "wanted to feel like a sunday afternoon."
- *Memory Milk:* "for the days you forget where you left them."
- *Wagging Wick:* "the dog's name is mochi (in my head)."

**Click any object** → opens a **two-page spread modal** styled like a
sketchbook:
- **left page:** the full project (hi-res image, scrollable carousel of
  process shots if available)
- **right page:** her notes, handwritten:
  - what it was
  - what she tried first
  - what she kept
  - what she'd change
  - a tiny doodle in the margin

**Bottom of section, lowercase serif body:**
> i do this for brands i actually like.
> if you're a brand i'd actually like, *the door is at the bottom.*

---

### 5.4 HOUR 12:00 — the laptop *(UI & digital)*

**Scene title:**
> *the laptop — i swear it's not just safari tabs.*

**Layout:** An illustrated laptop sits open on the desk. The **screen is
a window** into her UI work. Inside the laptop screen, show 3–4 of her
digital projects, cycling slowly (auto-scroll inside the laptop frame
every 4s, or on hover the user controls):

1. *ylee's cosmos home* — her personal web mockup. Honour this — it's
   her own design about her own world.
2. A dashboard mockup
3. A mobile app screen
4. The wallpaper she designed in her "illustrate a wallpaper with me"
   piece

Around the laptop: ambient desk things — a half-eaten biscuit, a
post-it that reads *"figma update broke everything again"*, a small cat
paw entering frame from the right.

**Annotation (handwritten, italic):**
> *the screen is the only thing in the room without a soul.
> i try to give it one anyway.*

---

### 5.5 HOUR 15:00 — the bookshelf *(illustrations)*

**Scene title:**
> *the shelf — built mostly to lean against.*

**Layout:** A wide illustrated bookshelf, three shelves. Books are
stacked, leaned, fallen, some open. **Each "book" on the shelf is an
illustration project.** The book spines show the project name in her
handwriting. Some books have a small object on top (a plant, the cat's
tail, a mug).

Projects to place as books:
- *lamp staring* (spine: ochre with a little lamp icon)
- *toe-ster* (spine: pale pink, tiny toaster)
- *ribbon* (spine: cream, tiny bow)
- *am i right?* (spine: terracotta)
- *new days ordinary streets* (spine: muted grey)
- *at the end of loveless* (spine: deep blue)
- *quarter life crisis started* (spine: rust)
- *a french affair* (spine: cream with rough type)
- *french-window cat* (spine: pale grey)
- *headphones boy + coffee* (spine: olive)
- *vinyl + cat by the rain* (spine: midnight)
- *the woman reading at the table* (spine: warm white)

**Interaction:** Hover → the book tilts out slightly, the spine glows
faintly with `--lamp`. Click → it slides out and **opens at center
screen** as a two-page spread (same template as the desk modal). Left
page: the full illustration. Right page: ylee's notes about it, in her
handwriting.

Sample annotations:
- *lamp staring:* "this one was made during a power cut. the irony."
- *toe-ster:* "the pun came before the drawing. it usually does."
- *ribbon:* "drawn after seeing a friend's ribcage in an x-ray. she's
  fine."
- *quarter life crisis started:* "still in progress, technically."

**Easter egg:** One book on the shelf is upside down. If the user
notices and clicks it, a tiny dialogue appears: *"you noticed. thank
you. ✦ "*

---

### 5.6 HOUR 18:00 — the window *(friends, cosmos, links out)*

**Scene title:**
> *the window — what i look at when i'm not looking at the screen.*

**Layout:** A large illustrated window with curtains pulled back. Beyond
the window, a soft golden-hour scene: a few buildings, a tree, a sliver
of sky. **Pinned to the window frame or sitting on the sill: outbound
links rendered as objects.**

- A polaroid on the sill labelled "anuja" → links to @antiself._ on
  instagram. Tooltip: *"my favourite human. she sees the world the way
  i wish i could."*
- A small notebook labelled "hours i live" → links to her cosmos board.
  Tooltip: *"the inspiration. updated when i can't sleep."*
- A camera roll strip → instagram @she.is.ylee. Tooltip: *"posted twice
  this month. proud."*
- A small envelope → email (you'll fill in). Tooltip: *"the slow way to
  reach me. the only way that works."*
- A tea-stained business card → linkedin (if she has one). Tooltip:
  *"the corporate corner. visit with caution."*

The view **outside the window** changes with time: at noon it's bright,
at golden hour it's amber, at night it's stars and one neighbour's lit
window.

**Annotation in script font, propped against the window:**
> *most of what i make starts here. looking out.*

---

### 5.7 HOUR 21:00 — the wall *(polaroids, behind-the-scenes)*

**Scene title:**
> *the wall — slowly becoming a person.*

**Layout:** A wide section of the wall covered in **polaroids, sketches,
sticky notes, magazine clippings, tickets, dried leaves**. Arranged
imperfectly, slightly overlapping. The wall has visible paper-tape
edges and pin-holes. This is the **process / personal** section — the
non-portfolio.

What to place (use her actual personal IG imagery as polaroids):
- a self-portrait polaroid ("me, mostly")
- a polaroid of her cat ("Bakachcha. yes that's her real name.")
- the "New Days Ordinary Streets" piece pinned crooked
- a small sketch of a plane window cloud
- a sticky note: *"don't redraw it again. ship it."*
- a sticky note: *"the brief said minimal. ignore them."*
- a torn page that reads *"mugs make me happy"* (a quiet nod to anuja)
- a coffee-ring stain on the wall, just because
- a small handwritten list titled "things i would die for" with
  entries: *cats. naps. a good kerning. monsoons. burnt sugar.*

**Annotation, lower right of wall, italic display:**
> *if the portfolio is the answer, this is the working.*

---

### 5.8 HOUR 00:00 — the mug *(letters from ylee)*

**Scene title:**
> *midnight — the mug speaks.*

**Layout:** The room is now lamp-lit, mostly dark. Center of the screen
is a glowing single illustration of a **mug on the desk**, steam rising.
The steam **forms text** — short essays / notes / micro-blogs that
appear like wisps. This is the writing / blog section.

Three or four "letters" can be browsed via small navigation arrows
beside the mug:

**Letter 1 — "on overthinking"**
> i once spent four hours adjusting the kerning of one word that
> nobody saw. the word was "softly." i'd say it was worth it. i'd say
> that about every hour i spend overthinking, actually. i'm not sure
> what that means about me.

**Letter 2 — "on saying yes"**
> i used to say yes to every project, then resent every project. now i
> say yes only to the ones that scare me a little — the small ones,
> the weird ones, the ones with a wagging dog or a quiet brand or a
> friend with an idea. that's where the work is.

**Letter 3 — "on the cat"**
> Bakachcha is the manager of this studio. she has not approved a single
> deliverable. her terms are unclear. she is paid in chin-scratches and
> small fish biscuits. i continue to work for her.

**Letter 4 — "on mornings"**
> i don't believe in mornings. but they keep showing up. this site
> begins at the hour you arrive. so technically, this could be morning
> for you. if it is — i hope your chai is warmer than mine.

Each letter signed in handwriting: *— y*

---

### 5.9 EPILOGUE — the door *("let's collab")*

**Scene title (the largest type on the page, italic display):**
> *the door is open. — slightly. push it.*

**Layout:** A single illustrated door, slightly ajar, warm light
spilling from behind it. Below the door, a soft form:

```
your name      [ ___________ ]
your work      [ ___________ ]
the brief      [ ___________ ]
                                 [ slide me in → ]
```

The button copy rotates randomly on each load between:
- *slide me in →*
- *send it. i'll overthink the rest →*
- *let's collab →*
- *one polite letter, coming up →*

Below the form, small:
> or, if forms aren't your thing — *hello@ylee.in* (or whichever
> address she uses).
>
> i answer within a few days. sometimes within a few hours. once,
> within four minutes. you can take your chances.

**Footer (very small, mono):**
> made by ylee, in 2026. with too much care, on purpose.
> typography: pp editorial new italic + söhne + caveat.
> the cat is real. the rest is illustrated.

---

## 6. Interactions & motion — the things that make it *wow*

Implement these. They are the difference between "nice" and "this is
*alive*."

1. **Time-of-day scroll-link.** The light/color/palette of the room
   lerps continuously as the user scrolls. Use CSS variables driven by
   a `scroll-progress` value. On load, the initial color is set by the
   visitor's local clock (use `new Date().getHours()`).
2. **Live clock + visitor greeting** in the top-right. The greeting
   changes with the hour: dawn → *"early. good."*; morning → *"chai's
   ready."*; noon → *"go eat first."*; golden → *"my favourite hour."*;
   dusk → *"the lamp just clicked on."*; night → *"don't tell me you're
   working."*; midnight → *"insomnia? same."*
3. **Custom cursor — ink pen + trail.** Always on (with mobile
   fallback). 1.2s fade. Becomes a paintbrush on hoverable objects.
4. **Bakachcha the cat.** A small illustrated cat walks across the
   page at random intervals (every 30–90s). She walks in from one
   edge, pauses, sometimes naps on a section, then leaves. If the user
   clicks her, a tiny meow plays (with a permission-aware mute toggle).
   She is also a **scroll easter egg**: scrolling very fast makes her
   sprint across with a streak.
5. **Hover-lift on portfolio objects.** Every interactive object on the
   desk / shelf / wall lifts ~6px with a soft warm shadow, and its
   neighbours subtly dim by 8%. This focusing behaviour is critical to
   the "single illustration" feeling.
6. **Two-page spread modal.** When opening any project, it should look
   like a **book being opened from the desk/shelf**, not a generic
   modal. Animate it: the object lifts to center, then unfolds into a
   spread. Page texture, slight inner shadow at the spine.
7. **Handwritten annotations bloom on hover.** Annotations are written
   in `Caveat`, and they **draw themselves on** — implement with SVG
   `stroke-dasharray` animation or a simple opacity+slight-translate.
8. **The lamp toggle.** A clickable lamp icon in the corner. Click it
   to override time and force night mode (or back). This is the
   user's small act of agency in the room.
9. **The "hours lived" counter** in the corner increments by 1 every
   real-world hour the visitor stays. After 5 minutes of dwell, a soft
   message appears: *"you've stayed a while. thank you. ✦"*
10. **Vinyl on click.** The illustrated record player in the corner of
    the desk, when clicked, starts a small ambient lo-fi loop. **Muted
    by default.** The needle animates onto the record.
11. **Subtle parallax** on the room layers — background (wall) moves
    slowest, mid (furniture) medium, foreground (objects on desk)
    fastest. Use `transform: translateY()` linked to scroll. Keep it
    gentle: no more than 8% offset.
12. **Sound on key moments (optional, muted by default).**
    - A page-turn sound when a project spread opens
    - A soft kettle whistle at the 09:00 section transition
    - A vinyl crackle when the record is on

---

## 7. Copy deck — the exact words

Use this as the source of truth. If you have to invent copy, match this
voice exactly.

| Location                        | Copy                                                       |
| ------------------------------- | ---------------------------------------------------------- |
| Browser tab title               | *ylee — hours i live*                                      |
| Browser tab favicon             | tiny illustrated mug                                       |
| Meta description                | "designer & illustrator. i overthink every pixel, so you don't have to. portfolio, in the form of a room." |
| Curtain headline                | *hours i live*                                             |
| Curtain subhead                 | by ylee. designer, illustrator, professional overthinker.  |
| Curtain caption                 | (the lamp turns on around 6pm. the cat shows up whenever she wants.) |
| Scroll hint                     | *scroll, or stay. either is fine.* ↓                       |
| Top-right clock greetings       | (rotate by hour, see §6.2)                                 |
| 06:00 headline                  | *i don't believe in mornings. but they keep showing up.*   |
| 06:00 body                      | (see §5.2)                                                 |
| 09:00 section title             | *the desk — where i pretend to be organised.*              |
| 09:00 outro                     | i do this for brands i actually like. if you're a brand i'd actually like, *the door is at the bottom.* |
| 12:00 section title             | *the laptop — i swear it's not just safari tabs.*          |
| 12:00 annotation                | *the screen is the only thing in the room without a soul. i try to give it one anyway.* |
| 15:00 section title             | *the shelf — built mostly to lean against.*                |
| 18:00 section title             | *the window — what i look at when i'm not looking at the screen.* |
| 21:00 section title             | *the wall — slowly becoming a person.*                     |
| 21:00 outro annotation          | *if the portfolio is the answer, this is the working.*     |
| 00:00 section title             | *midnight — the mug speaks.*                               |
| Epilogue title                  | *the door is open. — slightly. push it.*                   |
| Form labels                     | your name / your work / the brief                          |
| Form button (random rotation)   | *slide me in →* / *send it. i'll overthink the rest →* / *let's collab →* / *one polite letter, coming up →* |
| Form footer line                | *hello@ylee.in. i answer within a few days. sometimes within a few hours. once, within four minutes.* |
| Site footer                     | made by ylee, in 2026. with too much care, on purpose. typography: pp editorial new italic + söhne + caveat. the cat is real. the rest is illustrated. |

---

## 8. Asset direction (since we can't upload PDFs)

When claude.ai/design generates or sources images, use these prompts.
**Common style modifiers for every image:**
> "warm cream paper background, hand-drawn illustration, soft gouache and
> coloured pencil texture, ochre + terracotta + cream palette, slight
> paper grain, cozy and intimate, no glossy or 3D rendering, no AI
> uncanny-valley faces, subtle imperfect linework, 1990s south-asian
> children's-book feel meets contemporary editorial illustration"

### 8.1 Room scene (single panorama, layered)

**Master prompt:**
> "a wide panoramic illustration of a small cozy artist's room. left
> side: an unmade bed with a sketchbook and a mug of chai on a bedside
> table, a window with curtains half-drawn. center: a wooden desk
> cluttered with packaging mockups (jam jars, coffee cans, milk cartons,
> a candle box, a sunscreen tube), an open laptop, a small lamp, a
> ceramic mug. right side: a tall bookshelf with leaning books in earth
> tones, a small potted plant, a record player. a tabby cat sleeping on
> the desk. warm cream walls. polaroids and sticky notes pinned to one
> wall. a closed wooden door on the far right with a sliver of warm
> light at its base. flat-ish perspective, slight diagonal. textured
> paper, hand-drawn lines, ochre + terracotta + cream + espresso brown
> palette, soft pencil shadows. no people."

Render this **once** as a layered SVG or PNG with the following pieces
addressable separately so they can be lifted on hover:
- background wall (with polaroids)
- desk and objects on it (each packaging mock addressable)
- laptop (screen replaceable with live UI work)
- bookshelf (each book addressable)
- window (with view that swaps by time)
- door
- cat (animatable separately)
- lamp (toggleable)
- record player (animatable separately)
- floor / foreground

### 8.2 Light overlay layers (time of day)

Generate **7 overlay PNGs** at full canvas size, mostly transparent, with
just the right color cast + light direction for each hour. These are
multiplied over the room scene with opacity tweened by scroll position.

- 06:00 — cool blue-grey overlay, one warm streak from window
- 09:00 — soft warm cream wash
- 12:00 — bright golden warmth, hard shadows
- 15:00 — amber, deep ochres
- 18:00 — rose + violet, with the lamp beginning to glow
- 21:00 — espresso brown with strong lamp pool
- 00:00 — deep ink blue with a tight warm lamp pool

### 8.3 Project image placeholders

For each portfolio item, ask claude.ai/design to generate a flat,
warm-toned product mockup or illustration that matches the descriptions
in §1 (Cazy Catze Club coffee cans, KiwiKoi jam jars, etc.). Style
modifier: matches §8 common modifiers. Keep them as if photographed on
the desk — slight overhead angle, soft shadow underneath.

### 8.4 Polaroid wall

Generate ~10 polaroid-style square images in warm muted tones,
each with a subtle hand-written caption on the lower white border. Mix:
- 2 self-portrait-ish silhouettes (no realistic face — use back-of-head
  or hand-with-mug compositions)
- 2 cat polaroids
- 3 still-lifes (mug+book, plant+window, vinyl+lamp)
- 2 urban / monsoon street scenes
- 1 plane-window cloud sketch

### 8.5 Cat sprite

Generate a small tabby cat in **5 frames**: walking right, walking left,
sitting, sleeping curled, stretching. Use the same texture/palette.
These animate as a CSS sprite or simple JS frame swap.

---

## 9. Implementation notes for claude.ai/design

- **Single HTML file** with embedded CSS + a small JS bundle. No
  framework needed; this should feel hand-stitched.
- **Smooth scroll**, but don't over-snap. The user should be able to
  pause mid-section.
- **Performance:** Lazy-load each section's images. The room scene
  should be progressive — show a placeholder warm-cream rectangle, then
  the wall, then the furniture, then the objects, in layers.
- **Mobile:** On screens narrower than 768px, the panoramic room
  becomes a **vertical stack of vignettes** — same content, restacked.
  Cursor effects off. Cat still walks but slower. Custom touch tap
  feedback (small ink-dot bloom on tap).
- **Accessibility:**
  - Honour `prefers-reduced-motion` — disable parallax, time-of-day
    color shift becomes a manual select instead of scroll-tied, cat
    walks less, no auto-shifting cursor.
  - All decorative images have empty `alt=""`. Each portfolio object
    has descriptive alt text.
  - The room is also navigable via a **hidden visible-on-focus skip
    menu** in the top-left: "skip to: desk · shelf · wall · window ·
    contact". Use the same lowercase italic.
- **Dark mode** is replaced by **night-mode** (00:00 hour). It is not
  a separate theme; it's the natural endpoint of the scroll.
- **SEO:** Add structured `Person` schema for ylee. Page title,
  meta description, OG image (use the room scene at golden hour).
- **Domain:** ylee.in — set up a redirect from yleein.framer.website to
  the new build.

---

## 10. What to delete from this brief if you must shorten

If claude.ai/design runs out of token budget, prioritise in this order:

1. Build the room scene + scroll-tied time-of-day. *Non-negotiable.*
2. Build the desk + shelf with portfolio objects + spread modal.
3. Build the window, door, mug-letters, polaroid wall.
4. Add the cat, cursor, vinyl, hours-lived counter.
5. Add sound and the more elaborate easter eggs last.

But **do not** strip the voice. The copy is what makes this ylee. A
beautiful empty room is just a beautiful empty room. The whisper in the
corner is what makes someone stay.

---

## 11. One final note for the designer (a.k.a. claude.ai/design)

ylee's whole thing is that she **overthinks every pixel so others don't
have to**. So please — overthink every pixel. This is the one website
where that's the brief, not the bug. If a corner of a polaroid looks too
clean, mess it up. If a button feels too crisp, soften it. If a section
feels too efficient, slow it down by a beat. Add the comma where there
shouldn't be one. Leave the chai mug half-full.

made with care. for ylee. by a friend.

— end of brief —

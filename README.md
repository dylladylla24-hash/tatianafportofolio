# Tatyana Faradilla R. — personal portfolio

A small, hand-written static website. No build step, no frameworks, no backend.
Open `index.html` in a browser and it runs.

---

## Files

```
tatiporto/
├── index.html              all the text and structure — edit this most
├── css/style.css           the aquarium look: colours and fonts at the top, then each section in page order
├── css/projects.css        project stages + the live project viewer
├── js/main.js              menu, scroll reveals, project filter, copy button, timeline
├── js/projects.js          the live project viewer
├── js/aquarium.js          the 3D aquarium and the octopus (Three.js)
├── js/vendor/three.min.js  Three.js r160, bundled so the site still works offline (MIT licence beside it)
├── assets/
│   ├── fonts/              Instrument Serif, Karla (+ licences); the older fonts are kept but unused
│   ├── images/             photos, project screenshots, octopus.webp / octopus.png, octopus-mark.svg (site icon)
│   └── scenes/             the old Shanghai artwork, no longer used by the page
└── README.md
```

## How the code is written

- **No comments.** The code carries no comments at all; this README is the
  documentation. That includes the three project apps in `projects/`.
- **Every class ends in `_tatyana`**, in the HTML, the CSS and the JavaScript:
  `hero_tatyana`, `btn--solid_tatyana`, `is-open_tatyana` and so on. When you add
  a class, add the suffix in all three places, or the style or behaviour won't
  connect. IDs (`#nav`, `#contact`...) and `data-` attributes have no suffix.
- **The three project apps in `projects/` keep their own class names.** They are
  separate websites shown inside the viewer, not part of the portfolio's code;
  only their comments were removed.

## Running it on Windows

Double-clicking `index.html` works for everything except the "copy email" button,
which browsers only allow on a real address (`http://` or `https://`).

For editing, VS Code with the **Live Server** extension is easiest: right-click
`index.html` → *Open with Live Server*. The page reloads as you save.

---

## What to edit

Sections in `index.html` are in page order. Each one has an `id` you can search
for: `#top`, `#services`, `#skills`, `#projects`, `#experience`, `#education`,
`#about`, `#contact`.

| What you want to change | Where |
|---|---|
| Your introduction, role line, corner notes | `SECTION 1 — INTRODUCTION` |
| The five things you do | `SECTION 2 — WHAT I DO` |
| Skills (just `<li>` items, add or remove freely) | `SECTION 3 — HARD SKILLS` |
| Projects | `SECTION 4 — PROJECTS` |
| Experience (timeline) | `SECTION 5 — EXPERIENCE` |
| Education and languages | `SECTION 5b — EDUCATION & LANGUAGES` |
| How you work | `SECTION 6 — HOW I WORK` |
| Email, WhatsApp, iMessage | `SECTION 7 — CONTACT` |

### Projects (they open live)

Each project lives in its own folder and runs inside the page:

```
projects/
├── hotel-sriwidjaja/   index.html (guest site) + admin.html (admin panel)
├── egg-timer/          index.html
└── tourify/            index.html
```

These files are the original offline builds, unchanged. Clicking a card opens
the real project in a full-screen viewer (`js/projects.js`, `css/projects.css`)
that grows out of the card. "Back to portfolio" (or Esc while the bar has focus)
shrinks it back. Closing removes the project, so its sound and timers stop.

- Ctrl/Cmd-click or middle-click a card still opens the project in a new tab.
- Links like `index.html#project/tourify` open a project directly.
- Hotel Sriwidjaja has two tabs in the viewer. Both pages share browser storage,
  so a booking made on the guest site appears in the admin panel.

### Adding a project

1. Put the project in `projects/<name>/`. Its `index.html` must work on its own.
2. Copy one `<article class="work_tatyana">…</article>` block inside `<div class="works_tatyana">`.
3. Change `data-project` (short id), `data-category` (one or more of `web`, `app`,
   `uiux`, `interior`, `video`, separated by spaces), every `href` into `projects/`,
   the preview images, the texts and the facts (Purpose, Key features, Built with,
   My contribution). The element with `data-origin` is where the viewer grows from.
4. Links with `data-view` become the viewer's tabs; `data-label` is the tab name.
   One `data-view` link means no tabs.
5. `<template class="project__tips_tatyana">` is the "How to try it" list in the viewer.

Filter buttons with no matching project hide themselves and come back once you
add one.

Preview images are real screenshots of each project (`shot-*.jpg`), shown
inside CSS browser and phone frames. `hotel_sriwidjaja.png`,
`eggtimer_d.png` and `school_team_project.png` are no longer used and can be
deleted.

### Adding an experience entry

Copy one `<li class="tl_tatyana">…</li>` block inside `<ol class="timeline_tatyana">` (most recent
first) and fill in the dates, role, organization and description. The glowing
line and the dots light up on their own as you scroll.

### Contact

Each contact method is one `<li class="reach__item_tatyana">` with a link and a Copy
button (`data-copy` is what gets copied).

- WhatsApp: `https://wa.me/6287815055573`, the number in international format
  (country code, no `+`, no leading `0`).
- iMessage: an `sms:` link, which opens Messages on iPhone, iPad and Mac. On other
  devices the click copies the address instead and says why.

---

## Replacing the images

All placeholders live in `assets/images/`. Put your own file in the same folder
and point the `src` at it. Suggested sizes:

| Placeholder | Used for | Good size |
|---|---|---|
| `profilepicture.jpg` | hero photo, shown behind glass | portrait 4:5, face in the upper third |
| `placeholder-workspace.svg` | "How I work" photo | about 1600 × 1000 px |
| `placeholder-project-01…06.svg` | project thumbnails | about 1280 × 960 px (4:3) |

Example:

```html
<img src="assets/images/portrait.jpg" alt="Tatyana at her desk" width="900" height="1150">
```

Keep files under roughly 400 KB each so the page stays fast. Update the `alt` text
to describe the picture — it matters for screen readers and for search engines.

---

## Colours and fonts

Both are at the top of `css/style.css` in one `:root` block.

```css
--abyss: #03111B;   /* deepest water, page base */
--ink:   #E6EFEB;   /* main text */
--light: #BFEDE4;   /* caustic light: focus rings, bubbles */
--coral: #EE5A4F;   /* the octopus: the only warm colour, used for active states */
```

The water colours themselves live at the top of `js/aquarium.js` (`C = { ... }`).

| Font | Used for |
|---|---|
| **Instrument Serif** | the name, section titles, project titles, job titles, the university, email and phone numbers; the italic cut for notes, dates and labels |
| **Karla** | all body text, buttons, navigation |

Both are open source (SIL Open Font License); the licence files are in `assets/fonts/`.
Noisy Walk, Lemon Milk and Pinyon Script are still in the folder but no longer loaded,
so the Noisy Walk licence question no longer applies unless you bring it back.

---

## The aquarium

The whole page sits inside one 3D tank, drawn by `js/aquarium.js` on a canvas behind
the text. Text is always on top of the canvas, so nothing in the water can cover it.

- **Scrolling is the camera.** The camera travels forward and slowly down through the
  tank as you scroll. Each section has a "mark" for the octopus and the camera in the
  `DEFS` list in `js/aquarium.js`: `ox`/`oy` are where the octopus sits on screen
  (-1 left or bottom, 1 right or top), `od` how far away it is, `oyaw`/`opitch` where it
  faces. The `m` values are the phone versions. Change a number, save, reload.
- **The octopus** is built from simple shapes to match the supplied character (glossy
  red head with blush, eyes with two highlights each, a pink ring mouth and eight
  round-tipped tentacles). It drifts, blinks, follows the cursor with its eyes and body,
  turns towards whatever you hover, and its tentacles trail when it moves.
- **Transitions between sections**, in order: the camera pushes deeper into What I do;
  bubbles rise past the lens into Skills; a light beam sweeps into Projects; the water
  ripples as each project arrives; kelp crosses the lens into Experience; the camera
  sinks to the floor for Education; the octopus swims straight across the screen in the
  empty space before Contact; the tank goes quiet and dark at the very end.
- **Hover** anything important and the octopus looks at it, the water ripples and
  the particles part. Project previews tilt towards the cursor.
- **Loading:** darkness, then water, particles, light, the octopus's silhouette, its
  colours, and finally the text. About two seconds.
- **Performance:** fewer particles and plants and no multisampling on phones; if a
  device struggles, the scene lowers its resolution by itself. Add `?quality=low` to the
  address to force the lightest version. Rendering stops while a project is open or the
  tab is hidden.
- **Reduce motion:** with the system setting on, the camera still follows the scroll but
  the transitions, the octopus's swim-past and the drifting are switched off.
- **No WebGL:** the page falls back to a still water gradient with the octopus image.

---

## Putting it online

**GitHub Pages** — create a repository, upload this whole folder, then
Settings → Pages → Branch: `main`, Folder: `/root`. Your site appears at
`https://your-username.github.io/repository-name/`.

**Netlify** — go to app.netlify.com, drag the folder onto the page. Done.

Before publishing, update the `og:` tags in `<head>` so link previews show your
own photo and description.

---

## Notes

- Experience, education and languages come from the resume, word for word.
- **Check before publishing:** the "My contribution" lines for Egg Timer and
  Tourify are not in the resume or the project files. (They used to carry a
  `CONFIRM` comment in `index.html`; that went with all the other comments.)
- The site is responsive down to small phones, keyboard-navigable, and respects
  the system "reduce motion" setting.
- No analytics, no cookies, no trackers.

---



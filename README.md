# Prithviraj Bhori — Résumé Site

A fast, single-page résumé website built with **Vite + React 19**. No UI framework
dependency — just hand-written CSS with design tokens, light/dark themes and a
print stylesheet that turns the page into a clean 3-page A4 PDF.

---

## Quick start

```bash
npm install
npm run dev      # http://localhost:5173
```

```bash
npm run build    # -> dist/
npm run preview  # serve the production build
npm run lint     # oxlint
```

---

## Editing content

**Everything lives in one file:** [`src/data/resume.js`](src/data/resume.js).

| Export          | What it controls                                        |
| --------------- | ------------------------------------------------------- |
| `profile`       | Name, role, tagline, summary, email, phone, location     |
| `contactLinks`  | The contact card in the sidebar                          |
| `socials`       | GitHub / LinkedIn / Dribbble / Behance / X buttons       |
| `experience`    | Internship + training timeline                           |
| `education`     | Degree, college, CGPA, coursework                       |
| `projects`      | The four project cards                                   |
| `hackathons`    | The two hackathon cards                                  |
| `skillGroups`   | Skill chips grouped by category                          |
| `certifications`| The "Continuous learning" card                           |

The page re-renders automatically — save the file and the browser updates.

---

## Placeholders to replace

These are marked `// TODO` in `src/data/resume.js`:

- [ ] `profile.email` — currently `prithviraj@example.com`
- [ ] `profile.phone` — currently `+91 00000 00000`
- [ ] `profile.location` — set to `BTM Layout, Bengaluru, Karnataka`; update
      this if you move
- [ ] `profile.resumeFile` — set to e.g. `/resume.pdf` to make the **Résumé**
      button download your PDF instead of opening the print dialog. Drop the
      file in `public/`.
- [ ] `socials[].href` — every link is currently `#`
- [ ] `profile.summary` — rewrite in your own voice
- [ ] `profile.availability` — the green pill in the hero
- [ ] `education[].period` and `education[].score` — verify your years and CGPA
- [ ] `experience[].start` / `end` — verify the years
- [ ] `experience[].location` — the Rooman Technologies entry is set to
      `Bengaluru, Karnataka`; correct it if the office was elsewhere
- [ ] `projects[]` — the four titles, blurbs and descriptions are written as
      plausible examples; replace them with your actual projects
- [ ] `hackathons[]` — replace the two event names with the ones you attended

---

## Exporting a PDF résumé

1. Click the **Résumé** button (or `Ctrl/Cmd + P`).
2. In the print dialog choose **Save as PDF**, paper size **A4**, margins
   **Default**, and tick **Background graphics**.
3. The print stylesheet hides the nav, buttons, theme toggle and decorative
   gradients, and reorders the page to: header → about → experience → projects
   → hackathons → skills → education.

To force light colours in the PDF regardless of theme, the print stylesheet
already overrides the dark palette.

---

## Deploying

**Vercel / Netlify** — import the repo, set build command `npm run build`,
output directory `dist`. Nothing else to configure.

**GitHub Pages** — build with a base path:

```bash
BASE_PATH=/your-repo-name/ npm run build
```

then push `dist/` to the `gh-pages` branch.

---

## Project structure

```
src/
  data/resume.js        <- all editable content
  components/
    TopBar.jsx          sticky nav, theme toggle, résumé button
    Hero.jsx            intro, stats, calls to action
    Sidebar.jsx         contact + socials + skills (sticky on desktop)
    Experience.jsx      vertical timeline
    Projects.jsx        2-column project card grid
    Hackathons.jsx      hackathon cards
    Education.jsx       degree + continuous-learning cards
    Section.jsx         shared section heading
    Icon.jsx            inline SVG icon set (no icon dependency)
    Footer.jsx
  hooks/
    useTheme.js         light/dark + localStorage
    useScrollSpy.js     highlights the active nav item
  utils/scroll.js       section scrolling that ignores nested scroll areas
  styles.css            design tokens, themes, layout, print styles
```

---

## Design notes

- **Type** — Playfair Display for headings (a classic high-contrast serif),
  Inter for UI/body, JetBrains Mono for dates and metadata.
- **Colour** — light mode is a cool off-white base with an indigo-violet
  accent; dark mode is a near-black base with a periwinkle accent. A sky-blue
  secondary (`--accent-2`) carries through the hero gradient, the timeline
  rule and the background blobs. Both palettes are defined once as CSS custom
  properties in `:root` and `[data-theme='dark']`.
- **Theme** — defaults to your OS preference and is remembered in
  `localStorage` under the `pb-theme` key. A tiny inline script in
  `index.html` applies it before first paint, so there's no flash.
- **Rhythm** — main-column sections are separated by a fading hairline rule
  plus 58px of padding, so the page breathes without feeling loose.
- **Accessibility** — semantic landmarks, a skip link, visible focus rings,
  `aria-expanded` on the mobile menu, and a `prefers-reduced-motion` block.
- **Responsive** — two-column on desktop, stacked below 860px, with a slide-in
  mobile nav.
# Portfolio-2.0
# Portfolio-2.0

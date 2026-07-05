# Cybersecurity Portfolio — `index.html`

An award-style, scroll-driven single-file portfolio for a Master's student in
Cybersecurity. Dark "SOC-at-2AM" aesthetic, GSAP + ScrollTrigger scroll
animations, and Canvas particle/matrix effects. **No build step** — it's one
self-contained `index.html`.

## 1. Where to replace placeholder content

Almost everything lives in two places:

- **`CONFIG` object** (top of the `<script>` block): your `name`, `subtitle`,
  `university`, colors, and all effect-intensity knobs.
- **Content data arrays** (just below `CONFIG`): `SKILL_CARDS`, `SKILL_BARS`,
  `CASES`, `TIMELINE`, `BADGES`, `STATS`. Edit these to change every card,
  project, timeline entry, badge, and stat.

Search the file for these bracketed markers and swap them:

| Marker | What to put |
|---|---|
| `[YOUR NAME]` / `CONFIG.name` | Your name |
| `[UNIVERSITY NAME]` / `CONFIG.university` | Your school |
| `[EMAIL]` | Your email (used in contact links + mailto) |
| `[LINKEDIN URL]`, `[GITHUB URL]`, `[TRYHACKME/HACKTHEBOX PROFILE]` | Your profiles |
| Profile image | Replace the `data:image/svg+xml...` `src` in `#scan-frame` with your photo |
| `[COMPANY NAME]`, `[UNDERGRAD UNIVERSITY]`, `[3.9/4.0]`, `[Top 10]`, etc. | Real details |

The **contact form is front-end only**. It plays the encryption animation then
falls back to `mailto:`. To send real messages, wire a backend or a service
like Formspree in `initForm()` (marked with a `TODO`).

## 2. Adjusting animation intensity

All in the `CONFIG` object:

- `particles` — network-node count (keep under 60 for perf; auto-halved on mobile).
- `particleLinkDist` — distance nodes link at.
- `matrixFontSize` — hero matrix-rain density.
- `typeSpeed`, `decryptSpeed`, `decryptReveal`, `bootLineDelay` — typing / decrypt / boot pacing.

To globally tone effects down, either set `prefers-reduced-motion` in your OS
(the site respects it and switches to simple fades), or lower the values above.
Heavy effects (matrix rain, custom cursor) already auto-disable on touch/small
screens. If the GSAP CDN ever fails to load, the site automatically degrades to
a static, still-functional version.

## 3. Deploy free on GitHub Pages

1. Push this repo to GitHub (this file must be named `index.html` at the root).
2. Repo → **Settings** → **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Select your branch and the `/ (root)` folder, then **Save**.
5. Wait ~1 minute — your site is live at
   `https://<username>.github.io/<repo>/`.

That's it. No build, no dependencies to install — GSAP loads from a CDN at runtime.

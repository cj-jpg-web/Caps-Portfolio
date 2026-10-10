# Caps - Christian Capule

A personal portfolio built with Vue 3, TypeScript, Vite, and Tailwind CSS 4.
It presents creative work, archived video evidence, academic engineering
projects, background, contact options, and a downloadable portrait CV.

## Run and check

Use a current Node.js release compatible with Vite 7 (Node 22.12+).

```sh
npm ci
npm run dev
npm run check
```

`npm run check` runs strict TypeScript checks, in-process Vue component tests,
and the production build. `npm run test` checks component behavior without
starting a browser. `npm run build` performs type checking and compilation.

## Source structure

| Location | Responsibility |
| --- | --- |
| `src/App.vue` | Page composition, skip link, and main landmark |
| `content/profile.json` | Shared identity, contact details, education, and CV URL |
| `content/cv.json` | Confirmed CV descriptions and recognition |
| `src/data/portfolio.ts` | Typed project content and evidence links |
| `src/data/videos.ts` | Archived view/subscriber totals and video descriptions |
| `src/data/toolkit.ts` | Tool names, icon references, and purposes |
| `src/components/Navbar.vue` | Disclosure menu, section navigation, and active state |
| `src/components/CreativeWork.vue` | Three creative project previews |
| `src/components/Engineering.vue` | Two academic project previews |
| `src/components/ProjectDialog.vue` | Project details, original samples, and publication link |
| `src/components/ModalDialog.vue` | Native modal lifecycle and focus restoration |
| `src/components/VideoShowcase.vue` | Playback, hover preview, and full analytics reveal |
| `src/components/Contacts.vue` | Validated email-draft form and direct contact links |
| `src/composables/useToolStrip.ts` | Visibility-aware motion, pause, focus, and reduced motion |
| `src/utils/` | Email draft composition and modal scroll locks |
| `src/styles/` | Base rules, section layouts, dashboard, and visual direction |
| `scripts/generate-cv.py` | Reproducible one-page PDF with the original portrait |
| `scripts/check.mjs`, `tests/portfolio.test.ts` | In-process behavior and source checks |
| `public/` | Local fonts, SVG symbols, images, videos, and documents |

CSS imports are ordered intentionally. `base.css` provides tokens, resets, and
shared controls; `introduction.css` and `showcase.css` provide section layout;
`pulse-dashboard.css` styles the illustrative app; `visual-direction.css` and
`refinement.css` apply the retained art direction and case-study refinements.
Unused selectors and overwritten declarations have been removed conservatively
without reordering the retained cascade. Component styles for the small web
stack remain scoped in `WebStack.vue`.

## Update content

1. Update `content/profile.json` for shared contact/education changes.
2. Update project entries in `src/data/portfolio.ts` and place evidence in
   `public/images` or `public/documents`. Keep team attribution and concept
   labels accurate; add results only when confirmed.
3. Add videos to `src/data/videos.ts` and include the matching MP4, poster,
   and 640/960/1280-pixel thumbnails in `public`.
4. Update `content/cv.json` and run `python scripts/generate-cv.py`
   (requires ReportLab and Pillow). The canonical and legacy CV URLs are
   synchronized by the generator. Render the PDF and inspect it after edits.
5. Run `npm run check` before publishing.

The portfolio is a static site. Its contact form opens an email draft; it
does not send, store, or upload messages. External links use email, telephone,
and GitHub directly. There is no database or unused backend endpoint.

## Verification scope

`AUDIT.md` records the rubric review, repairs, automated checks, and remaining
verification. In-process component tests check Vue state and handlers with a
minimal host renderer. They do not establish browser layout, native focus
trapping, actual email-app launch, or external account availability.

Before submitting, review mobile, tablet, short desktop screens, 200% zoom,
keyboard navigation, touch scrolling, and video playback in your browser.

## Clone into VS Code

Install Node.js 22.12+ (a supported LTS release), Git, and VS Code first.

```sh
git clone https://github.com/cj-jpg-web/Caps-Portfolio.git
cd Caps-Portfolio
code .
npm ci
npm run dev
```

Open the localhost URL printed by Vite (normally http://localhost:5173).
Keep that terminal running. Stop it with Ctrl+C. No API key, account login,
ChatGPT subscription, or environment file is required to run the portfolio.

For the production build:

```sh
npm run check
npm run preview
```

## Publishing later

Deployment is intentionally disabled while the owner reviews localhost.
There is no GitHub Actions deployment workflow in this initial upload.
The public GitHub repository is source code, not yet a live Pages website.

A future GitHub Pages workflow should run `npm ci`, `npm run check`, then
build with `SITE_BASE_PATH=/Caps-Portfolio/` and publish `dist/`.
The repository name and base path are case-sensitive.
On Windows PowerShell, test that build with:

```powershell
$env:SITE_BASE_PATH = '/Caps-Portfolio/'
npm run build
npm run preview
Remove-Item Env:SITE_BASE_PATH
```

Open the preview URL with `/Caps-Portfolio/` appended. Normal local development
uses `/` when `SITE_BASE_PATH` is unset. `src/utils/assets.ts` resolves runtime
asset URLs and Vite rewrites CSS fonts for the configured base.

The CV and social metadata use the intended future GitHub Pages address.
That address will become available only after Pages is configured and deployed.

## Ownership

Portfolio content and original work belong to their respective owners and
credited collaborators. No license is granted by publishing this repository.
See `VISUAL-ASSETS.md` for asset attribution and recreated concept labels.

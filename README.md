# Alan Chen — Personal site

A static React portfolio built with Vite. Content is grounded in the supplied resume, with a dark, typography-led introduction, company logos, categorized tech stack, contact links, and a downloadable PDF.

## Run locally

Requires Node.js 22.12+ (Node 22 is specified in `.nvmrc`).

```sh
npm ci
npm run dev
```

Open the URL printed by Vite. To build and preview production output:

```sh
npm run build
npm run preview
```

The complete static website is generated in `dist/`. No server, database, environment variables, or paid services are required. Fonts load from Google Fonts with local fallbacks.

## Production deployment

This app is maintained independently in `AlanWYChen/swe-personal-site` and is served at
https://alanwychen.github.io/. Its default Vite base is `/`.

`AlanWYChen/AlanWYChen.github.io` includes this repository as the `apps/portfolio`
Git submodule and owns GitHub Pages deployment. After this repository's workflow
validates formatting and production builds, pushes to `main` automatically update this app's submodule
commit in the deployment repository, triggering the combined Pages deployment.
See that repository's README for deployment credentials and manual commands.

The teaching app is maintained separately. Do not add shared navigation, imports,
or a common React router between the apps.

## Deploy to Cloudflare Pages

### Git integration (automatic deployments)

1. Push this project to a GitHub or GitLab repository.
2. In Cloudflare, open **Workers & Pages**, choose **Create application**, then select **Pages** and connect the repository.
3. Configure the build:
   - Framework preset: **React (Vite)**
   - Build command: `npm run build`
   - Build output directory: `dist`
   - Root directory: leave blank when this project is at the repository root.
   - Node version: `22` (use the `NODE_VERSION` build variable if needed).
4. Deploy. Cloudflare assigns a `pages.dev` address; a custom domain is optional.

### Direct upload (no repository required)

1. Run `npm run build`.
2. In Cloudflare Pages, create a **Direct Upload** project.
3. Upload the contents of `dist/` and deploy.

Do not upload the source folder or `node_modules`. Direct Upload and Git-integrated Pages projects have different workflows; choose Git integration initially if you want automatic builds from commits.

Official documentation: https://developers.cloudflare.com/pages/framework-guides/deploy-a-react-site/

## Editing

- `src/main.jsx`: React entry point.
- `src/App.jsx`: page sections and navigation behavior.
- `src/data/portfolio.js`: companies, tech stack, contact profile, and icon mapping.
- `src/components/CompanyCard.jsx`: animated company card interaction.
- `src/styles.css`: layout, colors, typography, responsive behavior.
- `public/alan-chen-resume.pdf`: replace to update the download. This is the original supplied PDF, including its contact details.
- `index.html`: page title, description, and social metadata.
- `public/favicon.svg`: site icon.
- `public/_headers`: security headers applied by Cloudflare Pages.

The company section lists roles without dates or performance metrics. Education is presented without attendance dates. Review the introductory copy before publishing to ensure it reflects your voice.

The site includes visible focus states, a skip link, semantic sections, and reduced-motion support. Contact links include email, LinkedIn, GitHub, and an X placeholder; there is no form backend.

## Logo sources

Local copies of official company assets are stored in `public/logos/`:

- Scrawlr: https://corporate.scrawlr.com/assets/scrawlr-default-logo-CpUOVOM7.png
- UKG: https://commons.wikimedia.org/wiki/File:UKG_(Ultimate_Kronos_Group)_logo.svg (earlier smile wordmark)
- Metergy Solutions: https://cdn.prod.website-files.com/5f9c6d92db1af71866a9ca37/5fb679dc6fab3d4bf5b4be4d_Metergy_TM_Logo_w.svg (Metergy website)

Company marks belong to their respective owners. UKG is rendered in monochrome on the dark background.

Visual reference: https://www.andy-hk.com/ — dark background, large name typography, cyan-blue accents, and generous spacing; original content and implementation.

GitHub Actions builds the site on pushes and pull requests. Publishing uses GitHub Pages; Cloudflare remains an alternative.

Technology logos are locally hosted Devicon SVGs; source URLs and the upstream license are in `public/logos/tech/`. Waterloo’s official reversed colour logo comes from https://uwaterloo.ca/brand/uw-logos/university-logos/all. Technology badges support hover and keyboard-focus highlighting.

## Company introductions and Pick-pic

Company introductions support hover, keyboard focus, tap activation, and Escape. Sources:

- https://corporate.scrawlr.com/projects
- https://www.ukg.com
- https://www.metergysolutions.com

UKG uses the earlier smile wordmark requested by the owner, sourced from https://commons.wikimedia.org/wiki/File:UKG_(Ultimate_Kronos_Group)_logo.svg. UKG announced its subsequent rebrand on October 1, 2025.

The Pick-pic section uses the edited gallery screenshot with the marked word removed. The screenshots with member emails and other demo content are not included. Project copy describes the owner-confirmed project and visible functionality. Source code is linked at https://github.com/AlanWYChen/Pick-Pic.

## Code formatting

Run `npm run format` to format application source, configuration, and documentation, or `npm run format:check` to check formatting without changing files. The project skill pack lives in `.skills/production-engineering-skills/`.

## Favicons and social previews

`public/favicon.svg` is the compact white ac mark with a cyan dot. PNG/ICO fallbacks and the 180px Apple touch icon use the same source.

`public/social-preview.jpg` is a 1200×630 capture of the landing page. Open Graph and large-image card metadata are included in the initial HTML so link crawlers can read them without running React. The absolute URLs and canonical URL target https://alanwychen.github.io/. Update them if moving to a custom domain. Refresh the capture when the landing design changes. Social platforms may cache previous previews; LinkedIn’s Post Inspector can request a refresh.

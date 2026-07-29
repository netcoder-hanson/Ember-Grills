# EMBER — Lagos Suya & Grill House

A single-page landing site for EMBER, a Lagos-based open-flame suya and grill house. Built as static HTML/CSS/JS — no build step, no dependencies to install.

**Live site:** _add your GitHub Pages link here once deployed_

## Features

- Responsive layout, mobile nav with hamburger toggle
- Menu section styled as torn order tickets, with dashed price leaders and a chili heat-scale per dish
- Reservation form (name, phone, party size, date, time, notes) with a front-end confirmation state
- Scroll-triggered reveal animations, respects `prefers-reduced-motion`
- Visible keyboard focus states throughout

## Tech

- Plain HTML, CSS, and vanilla JS — no framework, no bundler
- Fonts loaded from Google Fonts: [Fraunces](https://fonts.google.com/specimen/Fraunces) (display), [Work Sans](https://fonts.google.com/specimen/Work+Sans) (body), [Space Mono](https://fonts.google.com/specimen/Space+Mono) (prices, labels)

## Project structure
.
├── index.html    # everything — markup, styles, and script in one file
└── README.md

## Running locally

Just open `index.html` in a browser. No server or install required.

## Deploying (GitHub Pages)

1. Push this repo to GitHub.
2. In the repo: **Settings → Pages → Source → Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`.
4. Save. Your site will be live at `https://<username>.github.io/<repo-name>/` within a minute or two.

Make sure the HTML file is named `index.html` at the root (or in `/docs`, if you set the Pages folder to `/docs`) — GitHub Pages serves that filename by default.

## Known limitations

- **The reservation form doesn't send anywhere.** Submitting it shows a confirmation ticket in the browser, but no email, SMS, or database is wired up yet. To make it functional, connect it to something like Formspree, a serverless function, or your own backend.
- The address, phone number, hours, and menu prices are placeholders — swap them for the real details before going live.

## Customizing

- **Colors, fonts, spacing:** all defined as CSS custom properties at the top of the `<style>` block in `index.html` (`:root { ... }`) — change once, applies everywhere.
- **Menu items:** each dish is a `.dish` block inside a `.ticket` card — copy/paste the pattern to add items, adjust the `.heat` SVGs to set spice level (`lit` vs `unlit`).
- **Copy:** hero, philosophy ("The Fire"), and CTA text are plain HTML — edit directly.

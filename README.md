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

```
.
├── index.html    # everything — markup, styles, and script in one file
└── README.md
```

## Running locally

Just open `index.html` in a browser. No server or install required.

## Deploying (GitHub Pages)

1. Push this repo to GitHub.
2. In the repo: **Settings → Pages → Source → Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`.
4. Save. Your site will be live at `https://<username>.github.io/<repo-name>/` within a minute or two.

Make sure the HTML file is named `index.html` at the root (or in `/docs`, if you set the Pages folder to `/docs`) — GitHub Pages serves that filename by default.

## Setting up the reservation form (EmailJS)

The reservation form sends straight from the browser to your email using [EmailJS](https://www.emailjs.com) — no backend server needed, and no third-party branding visible to guests.

1. Create a free account at [emailjs.com](https://www.emailjs.com).
2. **Add an email service:** Email Services → Add New Service → connect the inbox you want reservations to land in (Gmail, Outlook, etc.). Note the **Service ID**.
3. **Create an email template:** Email Templates → Create New Template. Use variables matching what the form sends: `{{guest_name}}`, `{{guest_phone}}`, `{{party_size}}`, `{{res_date}}`, `{{res_time}}`, `{{notes}}`. Note the **Template ID**.
4. **Get your public key:** Account → General → note your **Public Key**.
5. Open `index.html`, find this block near the bottom of the `<script>` tag, and fill in your three values:
   ```js
   const EMAILJS_PUBLIC_KEY  = 'YOUR_PUBLIC_KEY';
   const EMAILJS_SERVICE_ID  = 'YOUR_SERVICE_ID';
   const EMAILJS_TEMPLATE_ID = 'YOUR_TEMPLATE_ID';
   ```
6. Commit and push. Submit a test booking on the live site to confirm the email arrives.

The free EmailJS tier covers 200 emails/month, which is plenty for a single restaurant's bookings. Your public key is safe to expose in client-side code by design — it only allows sending through templates you've already configured, not reading your inbox.

## Known limitations

- The address, phone number, hours, and menu prices are placeholders — swap them for the real details before going live.
- Until you complete the EmailJS setup above, the reservation form will show an error message on submit rather than actually sending.

## Customizing

- **Colors, fonts, spacing:** all defined as CSS custom properties at the top of the `<style>` block in `index.html` (`:root { ... }`) — change once, applies everywhere.
- **Menu items:** each dish is a `.dish` block inside a `.ticket` card — copy/paste the pattern to add items, adjust the `.heat` SVGs to set spice level (`lit` vs `unlit`).
- **Copy:** hero, philosophy ("The Fire"), and CTA text are plain HTML — edit directly.

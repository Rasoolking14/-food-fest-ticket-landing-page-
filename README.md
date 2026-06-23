# Cape Town Food Fest — Ticket Landing Page

An interactive, component-based landing page for a fictional Cape Town food festival, built with **Vue 3 + Vite**. It showcases three ticket tiers (Bronze, Silver, Gold), highlights the featured tier, and lets visitors "favourite" tiers to simulate engagement — the foundation for a future ticketing system.

![Cape Town Food Fest landing page](docs/screenshot.png)

> Dark mode is also supported — toggle it from the header.
>
> ![Dark mode](docs/screenshot-dark.png)

## Overview

The page reads its tiers from a single data file and renders each one through a reusable `TicketCard` component, so there is no duplicated markup. Cards are styled as festival ticket stubs — a notched perforation separates the price from the benefits. The featured tier is visually lifted with a coloured border, a slight scale, and a "Most popular" badge. A favourite heart on each card updates a live counter in the header, and visitors can sort by price or filter to featured tiers only.

### Features

- **Data-driven cards** — all tiers render dynamically from `src/data/tickets.js`.
- **Featured tier styling** — distinct border, badge, and scale for the highlighted tier.
- **Favourite interaction** — per-card heart toggle with a live "saved" counter in the header.
- **Sort & filter** — sort by price (low→high / high→low) or featured-first; filter to featured only.
- **Call-to-action buttons** — each card has a tier-specific CTA, passed through a slot so the parent can swap it.
- **Responsive** — three-column grid on desktop, single column on mobile.
- **Dark / light mode** — theme toggle in the header.
- **Motion** — hero ticker, hover lifts, animated favourite pop, and list transitions on sort/filter. Respects `prefers-reduced-motion`.

## Tech

- Vue 3 (`<script setup>` SFCs)
- Vite
- No router, no external UI libraries — plain CSS with design tokens
- State via `ref` / `computed`; tiers passed down with props; favourites/CTA wired with events and a slot

## Project structure

```
src/
├── App.vue                  # state: favourites, sort, filter, theme; computed visibleTickets
├── main.js
├── assets/
│   └── global.css           # design tokens + light/dark theme variables
├── data/
│   └── tickets.js           # single source of truth for event + tiers
└── components/
    ├── AppHeader.vue        # brand, favourite counter, theme toggle
    ├── HeroSection.vue      # event title, details, CTA, ticker
    ├── ControlsBar.vue      # sort + filter controls
    ├── TicketCard.vue       # reusable ticket-stub card (props + slot)
    └── AppFooter.vue
```

## Run locally

Requires **Node.js 18+**.

```bash
# 1. install dependencies
npm install

# 2. start the dev server (hot reload)
npm run dev
```

Then open the URL Vite prints (default <http://localhost:5173>).

### Production build

```bash
npm run build      # outputs to /dist
npm run preview    # serves the built /dist locally
```

## Customising tiers

Edit `src/data/tickets.js`. Add, remove, or reorder entries and the UI updates automatically. Set `featured: true` on any tier to give it the highlighted treatment (designed for one featured tier at a time).

```js
{
  id: 'gold',
  name: 'Gold',
  price: 950,
  featured: false,
  blurb: 'The full table. Chef’s tastings and the rooftop lounge.',
  benefits: ['Everything in Silver', 'Chef’s table tasting menu', '...'],
  cta: 'Get Gold'
}
```

---

This is a demo landing page — tickets are not actually for sale.

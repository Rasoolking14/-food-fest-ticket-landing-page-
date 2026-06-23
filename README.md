# Cape Town Food Fest — Ticket Landing Page

An interactive, component-based landing page for a fictional Cape Town food festival, built with **Vue 3 + Vite**. It showcases three ticket tiers (Bronze, Silver, Gold), highlights the featured tier, and lets visitors "favourite" tiers to simulate engagement — the foundation for a future ticketing system.

![Cape Town Food Fest landing page](docs/screenshot.png)

> Dark mode is also supported — toggle it from the header.
>
> ![Dark mode](docs/screenshot-dark.png)

## Overview

The page reads its tiers from a single data file and renders each one through a reusable `TicketCard` component, so there is no duplicated markup. Cards are styled as festival ticket stubs — a notched perforation separates the price from the benefits. The featured tier is visually lifted with a coloured border, a slight scale, and a "Most popular" badge. A favourite heart on each card updates a live counter in the header, and visitors can sort by price or filter to featured tiers only.

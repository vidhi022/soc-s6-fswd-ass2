# Aavisakar 2026 — Event Landing Page

A responsive Event Landing Page built with **Tailwind CSS** for Silver Oak University's annual innovation and technology festival.

**Live Site:** [vidhi022.github.io/soc-s6-fswd-ass2](https://vidhi022.github.io/soc-s6-fswd-ass2/)

## About the Project

This project was created as part of **SOC Semester 6 — Full Stack Web Development (Assignment 2)**. The goal was to design and develop a responsive event landing page that effectively promotes a college event with event details, schedule, and highlights using a modern, user-friendly interface.

### Why Tailwind CSS?

Tailwind CSS was chosen because it provides utility-first classes that allow rapid UI development directly in HTML without writing custom CSS files. Using the Tailwind CDN means **zero build tools** — the page works by simply opening `index.html` in a browser or deploying to GitHub Pages. This keeps the project simple (2 files total) while still achieving a professional, polished design.

### Why JSON-driven Content?

All event content is loaded from a single `data/event.json` file instead of being hardcoded in HTML. This was a deliberate design decision for two reasons:

1. **Easy updates** — Event organizers can update the event title, schedule, speakers, and contact info by editing one JSON file without touching any HTML or JavaScript.
2. **College-agnostic** — Any college can fork this repository, replace the JSON file with their own event data (name, logo, colors, schedule), and have a fully branded event page without modifying code.

### Why a Single-Page Design?

Event landing pages work best as single-page scrollable sites. Visitors want to quickly scan the event highlights, check the schedule, see who's speaking, and find contact details — all without navigating between pages. Smooth scroll navigation and a sticky navbar make it easy to jump between sections.

## Project Structure

```
soc-s6-fswd-ass2/
├── index.html          ← Complete page: HTML + Tailwind CSS + inline JavaScript
└── data/
    └── event.json      ← All event content (college info, schedule, speakers, etc.)
```

Only **2 files** power the entire site. No build step, no dependencies, no framework.

## Features

### Core (Assignment Requirements)
- **Responsive design** — Looks great on mobile (375px), tablet (768px), and desktop (1280px+) using Tailwind's `sm:`, `md:`, and `lg:` breakpoints
- **Tailwind CSS** — All styling via utility classes, loaded from CDN
- **Event details** — Title, date, time, venue, description, and registration CTA
- **Event schedule** — Color-coded timeline with session types (talks, workshops, competitions, breaks)
- **Speaker profiles** — Card grid with name, role, bio for each speaker
- **JSON-driven content** — Everything loaded from `data/event.json`

### Interactive Enhancements
- **Countdown timer** — Live countdown (days, hours, minutes, seconds) to the event date, powered by `setInterval` and the `eventDate` field in JSON. Shows "Event is Live!" when the date passes.
- **Scroll fade-in animations** — Sections fade in as you scroll using `IntersectionObserver`. Respects `prefers-reduced-motion` for accessibility.
- **Active nav highlighting** — The navbar highlights the current section as you scroll through the page, using a second `IntersectionObserver`.
- **Back-to-top button** — A floating button appears after scrolling 500px and smoothly scrolls back to the top.
- **Mobile hamburger menu** — Navigation collapses into a toggleable menu on small screens, with auto-close on link click.

### Branding & Theming
- **Dynamic college branding** — The `primaryColor` field in JSON controls the navbar, hero gradient, and footer background colors. Change one value to rebrand the entire page.
- **External logo support** — The logo field accepts a URL (renders as `<img>`) or an emoji (renders as text). The SOU logo SVG is loaded directly from their website.

## How It Works

```
Browser loads index.html
    │
    ├── Tailwind CDN loads and applies utility classes
    │
    └── <script> runs:
         │
         ├── Sets up mobile nav toggle, scroll listeners, IntersectionObservers
         │
         └── fetch('data/event.json')
              │
              ├── Success → Populates all sections with JSON data
              │              Starts countdown timer
              │              Applies college brand colors
              │
              └── Failure → Console error (page shows empty sections)
```

## How to Customize for Another College

1. **Fork** this repository
2. **Edit** `data/event.json` with your college and event details:
   - `college.name`, `college.logo`, `college.primaryColor` — your branding
   - `event.title`, `event.date`, `event.eventDate` — your event info
   - `schedule`, `speakers`, `highlights` — your content
3. **Push** to GitHub and enable GitHub Pages
4. Your event page is live — no code changes needed

## Technologies Used

| Technology | Purpose |
|---|---|
| HTML5 | Semantic page structure (`<nav>`, `<section>`, `<footer>`) |
| Tailwind CSS (CDN) | Responsive utility-first styling |
| Vanilla JavaScript | JSON fetching, DOM rendering, interactivity |
| IntersectionObserver API | Scroll animations and active nav detection |
| GitHub Pages | Free static site hosting with HTTPS |

## Browser Compatibility

Works on all modern browsers: Chrome, Firefox, Safari, Edge (desktop and mobile). The `IntersectionObserver` API is supported in all browsers since 2019. Older browsers gracefully degrade — sections appear without animations.

## Author

**Vidhi Gajjar** — Silver Oak University, Semester 6, Full Stack Web Development

## License

This project is created for educational purposes as a college assignment.

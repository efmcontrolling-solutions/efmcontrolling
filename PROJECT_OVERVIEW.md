# Project Overview

## What this project is

This project is a static single-page website for an industrial moisture measurement product.

It is fully contained in one file: `index.html`.

The page is built as a long landing page with multiple sections, a language selector, and a password gate shown before access.

## Technologies used

- HTML5 for structure and content
- CSS3 for design, layout, responsiveness, and animations
- JavaScript for:
  - password gate behavior
  - language switching
  - section reveal effect
  - image lightbox behavior
- Google Fonts:
  - Bebas Neue
  - DM Sans
  - DM Mono
- Embedded assets using Base64:
  - logo image
  - gallery images
  - hero background videos (`webm` and `mp4`)
  - SVG noise texture

## File structure

The project uses a single-file structure:

- `index.html`
  - `<head>` contains fonts, all CSS, and metadata
  - `<body>` contains all page sections and JavaScript
  - all styles and scripts are inline in the same file

## Full page section breakdown

## 1) Password protection overlay

At page load, a full-screen overlay appears first.

It contains:
- title: "Private Access"
- password input
- Enter button
- error message area

The page starts in locked mode using `document.body.classList.add("locked")`.

## 2) Navbar

The navbar is fixed at the top with a blurred background.

It includes:
- brand logo image (Base64 embedded)
- navigation links:
  - Product
  - Industries
  - How It Works
  - Specs
- CTA link: Request
- language selector dropdown button

Behavior:
- Navbar stays fixed while scrolling
- On smaller screens (`max-width: 960px`), nav links are hidden
- Language selector stays available

## 3) Language selector (UI + real text switching)

The selector has a trigger button with:
- current flag
- short label
- dropdown arrow

Dropdown groups:
- Europe
- Asia · Middle East

It contains 30 language options.

Language codes included:
- `en-US`, `en`, `de`, `fr`, `es`, `it`, `pt`, `nl`, `pl`, `cs`, `hu`, `ro`, `bg`, `el`, `sv`, `da`, `no`, `fi`, `uk`, `zh`, `ja`, `ko`, `hi`, `bn`, `ur`, `id`, `vi`, `th`, `tr`, `ar`

How it works:
- Each content node uses `data-i18n` or `data-i18n-html`
- `setLang(code)` reads text from the `LANGS` object
- Text is replaced in the UI when a language is chosen
- The active language button is highlighted
- The trigger updates flag and short label
- Default language is set with `setLang("en-US")`

## 4) Hero section

The hero includes:
- background media area with embedded video sources
- animated grid overlay
- glow effect
- "Real-Time Measurement" badge
- eyebrow text
- large headline
- short supporting paragraph
- two CTA buttons
- key stats (In-Situ, Response Time, Continuous, Process Interruptions)

## 5) Comparison section

This section compares:
- classic measurement (left column)
- inline moisture control (right column)

The layout uses a two-column grid on desktop and one column on small screens.

## 6) Features section

This section shows six feature cards in a grid.

Each card includes:
- icon
- title
- description

Cards have hover effects and top accent-line animation.

## 7) Industries section

This section shows three industry cards:
- Power Plants
- Brick Plants
- Industry

Each card includes:
- icon
- title
- application line
- three benefit bullet points

Inside this area, there is also a gallery block with real installation images and lightbox behavior.

## 8) How it works section

This is a 3-step process:
- Installation
- Measurement
- Control

Desktop uses a connected step layout.
Mobile switches to stacked cards.

## 9) Benefits section

This section presents four economic value items:
- Stable Production
- Consistent Quality
- Less Energy Use
- Lower Operating Costs

## 10) Specs table section

This section uses a table for technical data.

Rows include:
- measuring method
- measuring range
- response time
- temperature range
- interfaces
- locations
- design
- integration

## 11) CTA section

A centered call-to-action block with:
- large heading
- support text
- primary button (`mailto:` link)
- secondary button linking to specs

Background has gradient and radial glow effects.

## 12) Footer

Simple footer with:
- brand text
- copyright line

## Design system

The page uses CSS variables in `:root` as a design system:

- colors:
  - `--bg`
  - `--surface`
  - `--surface2`
  - `--border`
  - `--accent`
  - `--accent2`
  - `--text`
  - `--muted`
- font variables:
  - `--hf` (heading font)
  - `--bf` (body font)
  - `--mf` (mono font)

This makes global styling changes easier and consistent.

## Layout system

The page uses both Flexbox and CSS Grid:

- Flexbox:
  - navbar alignment
  - hero actions
  - hero stats
  - footer alignment
  - many card internal alignments
- Grid:
  - language option lists
  - comparison columns
  - features cards
  - industries cards
  - steps layout
  - benefits cards
  - gallery layout

## Responsiveness

Key breakpoints are defined in CSS:

- `max-width: 960px`
  - nav links hidden
  - many multi-column grids become single column
  - section spacing reduced
- `max-width: 480px`
  - smaller typography and tighter spacing
  - mobile adjustments for navbar, language dropdown, hero, cards, and gallery

Additional component-specific breakpoints also appear in CSS for fine-tuning.

## Images and background effects

This project embeds most media directly in `index.html` using Base64:

- JPEG images in `<img src="data:image/jpeg;base64,...">`
- logo image in Base64
- hero video sources in Base64
- SVG noise texture in CSS background

Quick media count in this project (from `index.html`):
- JPEG images: 9
- PNG images: 0
- SVG backgrounds (data URI): 1
- Embedded videos:
  - WebM: 1
  - MP4: 1

Visual effects include:
- subtle noise texture over page
- gradient overlays
- radial glow circles
- video background with dark overlay

## Animations and interactive effects

Main effects used:

- fade/slide reveal:
  - elements with `.reveal` become visible using IntersectionObserver
- hero intro fade-up animation:
  - key elements animate using `@keyframes fu`
- pulse animation:
  - live dot uses `@keyframes pulse`
- background grid breathing:
  - hero grid uses `@keyframes gp`
- hover effects:
  - buttons lift and glow
  - cards change border/background
  - gallery zoom icon and overlays

## Password protection (important)

The password logic is in an inline script near the top of `<body>`.

Core rule:
- `const correctPassword = "Freelancer100%registered";`

Flow:
- page starts locked with class `locked`
- user enters password
- `checkPassword()` compares input to `correctPassword`
- if correct:
  - overlay is hidden
  - `locked` class is removed
- if wrong:
  - error message "Wrong password" is shown
  - page remains locked

Why wrong password keeps content locked:
- unlock action only runs inside the exact `if (input === correctPassword)` branch
- wrong input never runs unlock steps

Why UI bypass alone is not a true unlock:
- hiding overlay visually is not the same as passing the check logic
- this gate is a front-end UI restriction in client-side code
- the intended unlock path is the JavaScript condition with the correct password value

## Language system behavior

This project contains real UI text switching through the `LANGS` object and `setLang`.

It does not use:
- external translation API
- browser auto-translation service
- backend translation storage

So all translated text is manually embedded in `index.html`.

## Direction support (LTR / RTL)

Direction is controlled per selected language:
- `document.documentElement.dir = l.dir`

From the language config:
- most languages use `ltr`
- RTL is enabled for languages configured with `dir: "rtl"` (for example Arabic and Urdu)

CSS includes RTL-aware rules, such as:
- `body[dir="rtl"] { text-align: right; }`
- arrow marker direction change in industry bullet list

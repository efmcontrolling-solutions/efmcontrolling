# Project Performance and Quality Issues

This file lists only real issues found in the current `index.html`.

It does **not** include solutions.

## 1) Very large single HTML file (2.9 MB)

The whole project is in one file and `index.html` is around **2.9 MB**.

Why this is an issue:
- The browser must download a large file before showing full content.
- Parsing one very large HTML document increases initial load time.
- Slow networks and mobile devices will feel this delay more.

## 2) Heavy media is embedded directly in HTML (Base64)

Media is inline inside the HTML:
- 9 JPEG data URIs
- 1 SVG data URI
- 2 embedded video sources (WebM + MP4)

Why this is an issue:
- Media bytes are mixed into the HTML document itself.
- HTML becomes much heavier than normal.
- Browser cannot treat these assets like separate cache-friendly files.
- Any small HTML change forces re-download of all embedded media data.

## 3) Two full hero video sources are loaded inline

The hero contains both:
- `data:video/webm;base64,...`
- `data:video/mp4;base64,...`

Why this is an issue:
- Video data is very heavy for first page load.
- Autoplay background media can increase CPU/battery usage.
- Low-end devices may show stutter or delayed rendering in hero area.

## 4) Mobile navigation links are hidden without replacement menu

At `max-width: 960px`, `.nav-links` is set to `display: none`.
There is no visible mobile menu button in the navbar for those links.

Why this is an issue:
- Users lose direct access to Product / Industries / How It Works / Specs / Request links on smaller screens.
- Important page navigation is reduced on mobile where it is needed most.

## 5) Password box does not show Enter-key submit behavior

Password check is triggered by button click (`onclick="checkPassword()"`).
No Enter-key handling is implemented for the password input.

Why this is an issue:
- Common login behavior is pressing Enter after typing password.
- Users may think the form is broken if Enter does nothing.
- It creates friction in first interaction with the site.

## 6) Many interactions are mouse/touch-only (`onclick` inline handlers)

The file has many inline `onclick` handlers (language options, gallery items, lightbox controls, etc.).

Why this is an issue:
- Keyboard and assistive-tech interaction can be incomplete for parts of UI.
- It increases risk of inconsistent behavior across interaction methods.
- Inline handler style also makes event behavior harder to audit and scale.

## 7) Lightbox image tiles are click-driven cards, not semantic controls

Gallery items are clickable `div` blocks with `onclick="openLb(...)"`.

Why this is an issue:
- Non-button/non-link interactive blocks can be less accessible.
- Keyboard users may have trouble opening gallery items consistently.
- This can look like a rendering/interaction bug to users who cannot click with pointer.

## 8) Contact action uses placeholder email

Primary CTA uses `mailto:info@example.com`.

Why this is an issue:
- This is not a real business contact.
- Users trying to contact may fail immediately.
- It impacts trust and conversion on a sales-style landing page.

## 9) Large amount of inline CSS + JS in same file

Styles and scripts are embedded directly in `index.html` with long blocks.

Why this is an issue:
- Bigger HTML parse/execute path at startup.
- Harder long-term quality control in one huge document.
- Small edits to one part require shipping the entire page again.

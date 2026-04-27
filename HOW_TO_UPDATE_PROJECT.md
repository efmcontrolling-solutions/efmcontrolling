# How To Update This Project

## Before you start

This project is in one file: `index.html`.

So all updates happen in this file:
- text
- links
- images
- styles
- language content
- password

## 1) Edit headings, paragraphs, buttons, and links

Open `index.html` and find the section you want.

### Change headings

Look for heading tags like:
- `<h1>`
- `<h2>`
- `<h3>`

Edit the text between the tags.

### Change paragraph text

Look for `<p>` tags and update the text.

### Change button text

Buttons are usually:
- `<a class="btn-primary">...</a>`
- `<a class="btn-secondary">...</a>`
- language and password buttons

Edit the visible text inside each button.

### Change links

Update the `href` value.

Examples:
- section link: `href="#specs"`
- email link: `href="mailto:info@example.com"`

## 2) Change colors

All main colors are in CSS variables near the top of `index.html` inside `:root`.

Example variables:
- `--bg`
- `--surface`
- `--accent`
- `--text`
- `--muted`

Update these values to change the full theme quickly.

## 3) Change fonts

Fonts are controlled in two places:

### A) Google Fonts link in `<head>`

There is one `<link>` to Google Fonts.
Change it if you want different font families.

### B) Font CSS variables in `:root`

- `--hf` = heading font
- `--bf` = body font
- `--mf` = mono font

Update these variables to apply fonts across the full page.

## 4) Change images (Base64 to external files)

Many images are currently embedded as Base64 (`data:image/...base64,...`).

To use normal files instead:

1. Put image files in your project folder.
2. Replace `src="data:image..."`
3. Use file paths, for example:
   - `src="images/plant-1.jpg"`
4. Save and refresh.

Do this for:
- navbar logo
- gallery images
- any other embedded image sources

## 5) Add a new language

Language system is inside the script with `const LANGS = { ... }`.

Steps:

1. Add a new language button in the dropdown:
   - `<button class="lang-opt" onclick="setLang('xx')" data-lang="xx">...`
2. Add a new language object in `LANGS` using the same code (`xx`).
3. Include:
   - `flag`
   - `label`
   - `dir` (`ltr` or `rtl`)
   - `name`
   - full `t` translations for all keys
4. Save and test by selecting that language.

Important:
- If translation keys are missing, some text will stay unchanged.

## 6) Modify, add, or remove sections

Each page block is a `<section>...</section>`.

To modify a section:
- edit text and elements inside that section

To add a section:
1. Copy an existing section block.
2. Paste where needed.
3. Change content.
4. Add matching nav link if required.

To remove a section:
1. Delete that section block.
2. Remove related nav link (if it exists).

## 7) Change the password (exact step)

Find this line near the top of `<body>` script:

`const correctPassword = "Freelancer100%registered";`

Replace the text inside quotes with your new password.

Example:

`const correctPassword = "MyNewPassword123";`

What happens after change:
- old password stops working
- only the new password can unlock
- wrong password keeps the page locked

## 8) Adjust layout (Grid and Flexbox)

This project uses:
- CSS Grid for section cards and tables layout
- Flexbox for alignment, button rows, navbar, and footer

To change layout:
- update `grid-template-columns`, `gap`, and related grid styles
- update `display: flex`, `justify-content`, `align-items`, and `flex-wrap`

Check responsive blocks (`@media`) after layout edits.

## 9) Edit the specs table

Specs are in:
- `<table class="specs-table">`

Each row is:
- left cell = label
- right cell = value

To edit:
- change existing `<td>` text

To add row:
1. Copy one `<tr>...</tr>`
2. Paste below
3. Update both cells

To remove row:
- delete that `<tr>...</tr>` block

If you use translations, also update matching translation keys in `LANGS`.

## Quick checklist after updates

- Save `index.html`
- Open page in browser
- Check desktop and mobile views
- Test language switch
- Test password input
- Test buttons and links

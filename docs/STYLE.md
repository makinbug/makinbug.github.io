# Makin'Bug style guide

Stage 5, 30 Oct 2026. The styles live in `assets/css/custom.css`. This page says why they look the way they do.

## What Adi asked for

- A calm, warm look like claude.ai: off-white page, serif headings, plain sans text, lots of space.
- A bit of colour on some things, like mistral.ai, but in softer shades.
- The same colours and fonts on the phone and the laptop.
- Light theme only. No dark theme.
- The old Duda look does not matter.

We take the mood from those sites, not their logos, artwork or layouts.

## Colours

| Name | Hex | Use |
| --- | --- | --- |
| Paper | `#faf9f5` | Page background |
| Sand | `#f0eee6` | Header line, cards, alternate bands, footer |
| Ink | `#1f1e1d` | Headings and main text. Muted text uses `#5e5d59` |
| Bug red | `#c02432` | From the logo. Links, buttons, small marks. Hover `#a51e2b` |
| Soft amber | `#f4c96b` | Colour blocks and accents |
| Soft coral | `#ee9b80` | Colour blocks and accents |

Card tints (the same colours, much lighter): amber `#fbeccb`, coral `#f9dfd3`, red `#f6dcd9`.

The logo keeps its own two colours: icon `#c02432`, name `#611112`.

All text and background pairs pass WCAG AA contrast (4.5 to 1 or better). Bug red on Paper is 5.6 to 1. White on Bug red is 5.9 to 1. Never put text on Soft amber or Soft coral at full strength; use the tints.

## Fonts

Both are free, under the SIL Open Font License, and served from `static/fonts/`. Nothing loads from Google Fonts.

- **Source Serif 4** for headings, weight 500 to 600. Close to the serif on claude.ai.
- **Inter** for all other text, weight 400, and 600 for bold.

Sizes (phone, then laptop):

| Text | Size | Line height |
| --- | --- | --- |
| Home headline | 40px, 64px | 1.1 |
| Page title | 34px, 48px | 1.15 |
| Section heading (h2) | 26px, 32px | 1.25 |
| Card heading (h3) | 20px | 1.3 |
| Body | 17px, 18px | 1.6 |
| Small text | 15px | 1.5 |

## Spacing

- Base step is 8px. Use 8, 16, 24, 32, 48, 64, 96.
- Text column: at most 42rem (about 70 characters a line).
- Wide content (cards, products, gallery): at most 72rem.
- Side margin: 20px on the phone, 32px on the laptop.
- Space between page sections: 64px on the phone, 96px on the laptop.

## Buttons

- Main button: Bug red, white text, 8px round corners, 12px by 20px padding, weight 600. Hover goes to `#a51e2b`.
- Second button: no fill, Ink text, 1px line in `#d6d3c9`, same shape. Hover fills with Sand.
- The eBay button is always the main button. Its text is always "See price and buy on eBay".
- Every link and button shows a 2px Bug red focus ring for keyboard users.

## Cards

- Background: a tint or white, 12px round corners, 24px padding, no shadow.
- Service cards and section cards take a tint in turn: amber, coral, red.
- Review cards: Sand, with a short Bug red line at the top.
- Product rows: white with a 1px line in `#e6e3da`.

## Colour blocks

A row of stepped soft blocks (amber, coral, a small red one) sits under the home headline and above the footer. They are pure CSS, so they cost nothing to load. This is the one bold touch. Don't add more.

## Logo and icons

- `static/img/logo.png`: the long logo, 96px tall, on a clear background. Shown 40px tall on the laptop, 32px on the phone.
- `static/favicon.ico`, `static/favicon-32.png`: browser tab icon.
- `static/apple-touch-icon.png`: icon for a phone home screen, on Paper.
- `static/img/icon.png`: the icon alone, 160px, on a clear background.

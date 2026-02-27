# LinguaWorld — Website Documentation

## Overview

LinguaWorld is a single-file HTML website for an online English teaching platform. Everything (styles, animations, and logic) lives in one file: `index.html`. No build tools, no dependencies to install, no server required. Just open the file in a browser or upload it to any web host.

---

## File Structure

```
lingua-world-v2.html   ← the entire website (HTML + CSS + JS)
README.md              ← this document
```

---

## Sections

The page is organized into the following sections, top to bottom:

| Section | ID | Description |
|---|---|---|
| Navigation | `nav` | Fixed top bar with language switcher and CTA button |
| Hero | `#hero` | Landing screen with animated canvas and globe |
| Stats Strip | — | 4 key numbers (students, countries, satisfaction, teachers) |
| How It Works | `#how` | 4-step process cards |
| Courses | `#courses` | Course cards with shopping cart |
| About | `#about` | Mission, values, and mini stats |
| Our Teachers | `#teachers` | 8 teacher cards + team banner |
| Video | `#video` | Placeholder for future brand video |
| Gallery | `#gallery` | Photo grid (6 items) |
| Reviews | `#reviews` | 6 student testimonials |
| Trial CTA | `#trial` | Free lesson call-to-action |
| Footer | `footer` | Links, contact, socials |

---

## Features

### 🌍 Multi-Language Support
The site supports **6 languages** switchable via the top-right language selector:

| Code | Language |
|---|---|
| EN | English |
| FR | Français |
| AR | العربية (RTL) |
| ES | Español |
| PT | Português |
| JA | 日本語 |

Every piece of text on the page — navigation, hero, sections, footer — is translated. Arabic automatically switches the layout to right-to-left (RTL).

**To add a new language:**
1. Find the `translations` object in the `<script>` tag (search for `const translations`)
2. Add a new key (e.g. `zh`) following the same structure as the existing languages
3. Add the language to the `langMeta` object with its flag emoji and code
4. Add a new `<div class="lang-option">` in the dropdown HTML

---

### 🎨 Hero Canvas Animation
The hero background features a canvas animation with two phases:

- **Intro (first ~6 seconds):** 20 welcome words in different languages crossfade one by one at the center
- **Ambient (ongoing):** All words drift slowly across the canvas using organic smooth noise movement

The animation is defined in `initHeroCanvas()`.

---

### 🛒 Shopping Cart
Courses can be added to a slide-in cart drawer. The cart:
- Tracks selected courses and prevents duplicates
- Calculates the total price
- Is fully client-side (no backend)

**To edit courses** (names, prices, descriptions), find the `courses` array in the script:
```js
const courses = [
  { id:1, emoji:'✨', level:'All Levels', name:'Free Trial Lesson', price:0, ... },
  ...
];
```

---

### ⭐ Reviews
Reviews are rendered dynamically from the `reviews` array in the script. To add or edit a review, find:
```js
const reviews = [
  { emoji:'👩🏻', name:'Yuki T.', country:'🇯🇵 Japan', stars:5, text:'...' },
  ...
];
```

---

## How to Deploy

### Option 1 — Direct upload (simplest)
Upload `lingua-world-v2.html` to any static hosting service:
- **Netlify** — drag and drop the file at [netlify.com/drop](https://netlify.com/drop)
- **Vercel** — via the dashboard or CLI
- **GitHub Pages** — rename to `index.html` and push to a repo
- **Any web host** — upload via FTP/cPanel as `index.html`

### Option 2 — Local preview
Open `lingua-world-v2.html` directly in any modern browser (Chrome, Safari, Firefox, Edge). No server needed.

> ⚠️ **Note:** Google Fonts are loaded from the web. An internet connection is required for the fonts to display correctly.

---

## Customisation Guide

### Changing Colors
All brand colors are defined as CSS variables at the top of the `<style>` block:

```css
:root {
  --warm1: #FF6B35;   /* Orange */
  --warm2: #FFB347;   /* Amber */
  --cool1: #5B5BD6;   /* Indigo */
  --cool2: #9B59B6;   /* Purple */
  --dark:  #1A1523;   /* Background dark */
  --light: #FAF8FF;   /* Background light */
}
```

### Changing the Logo
Search for `Lingua<span>World</span>` in the HTML — there are two instances (nav and footer). Replace with your preferred text or swap for an `<img>` tag.

### Changing Teacher Cards
Each teacher card is hardcoded in the `#teachers` section. Find the `.teacher-card` divs and edit the name, origin, role, tags, flag emoji, and gradient color directly in the HTML.

### Replacing the Video Placeholder
Find the `#video` section and replace the `.video-placeholder` div with an `<iframe>` embed from YouTube or Vimeo:
```html
<iframe width="100%" height="100%"
  src="https://www.youtube.com/embed/YOUR_VIDEO_ID"
  frameborder="0" allowfullscreen>
</iframe>
```

### Updating Contact Info
The email address in the footer is currently a placeholder. Search for `hello@linguaworld.com` and replace it with the real address.

---

## Browser Support

| Browser | Support |
|---|---|
| Chrome 90+ |  Full |
| Safari 15+ |  Full |
| Firefox 90+ |  Full |
| Edge 90+ |  Full |
| iOS Safari 15+ |  Full |
| Samsung Internet |  Full |

---

## Performance Notes

- All assets are either inline or loaded from Google's CDN (fonts)
- The canvas animation uses `requestAnimationFrame` and is GPU-friendly
- Images are emoji-based — no external image requests
- Total file size: ~120 KB uncompressed

---

## Handoff Checklist

Before going live, make sure to:

- [ ] Replace placeholder email with real contact address
- [ ] Add real course pricing and descriptions
- [ ] Replace video placeholder with actual brand video
- [ ] Add real student photos / testimonials if desired
- [ ] Update the footer copyright year if needed
- [ ] Connect the "Book a Trial" buttons to a real booking system (e.g. Calendly)
- [ ] Add a favicon (`<link rel="icon" href="favicon.ico">` in the `<head>`)
- [ ] Set up a real domain and SSL certificate on your host

---

*Built with love — one file, zero dependencies.*

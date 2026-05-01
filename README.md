# Donjons & Jambons — Design System

## Overview

**Donjons & Jambons** (D&J) is a World of Warcraft Retail guild on the **Kirin-Tor EU** server, mixing Alliance and Horde. The guild's philosophy: play when you want, how you want, with zero obligation — fun-first, community-first, no elitism.

The brand blends a **medieval fantasy tavern aesthetic** (WoW-inspired: stone engravings, gold-patinated borders, parchment) with a **playful, irreverent personality** expressed through a large library of custom kawaii "jambon" (ham) mascot emotes.

---

## Sources

- **GitHub codebase**: https://github.com/Jungso-GB/donjons-jambons
  - `index.html` — Full one-page landing site (vanilla HTML/CSS/JS)
  - `assets/style.css` — Complete theme stylesheet
  - `assets/members.js` — Member roster data
- **Uploaded assets** (logo, banner, 40+ custom emotes) — see `assets/` folder
- **Discord server**: https://discord.gg/82b37hw6dh
- **Armory**: https://worldofwarcraft.blizzard.com/fr-fr/guild/eu/kirin-tor/donjons-et-jambons

---

## CONTENT FUNDAMENTALS

### Language & Tone
- **French only** — all copy is in French (the guild is francophone EU)
- **Casual, warm, irreverent** — uses "tu" (never "vous"), slang, humor
- **Self-deprecating yet proud** — jokes about the ham theme constantly but commits to it
- **Anti-elitism voice** — explicit messages like "On valorise les gens, pas leur stuff" and "ton temps, tes règles"
- **Communautaire** — emphasizes belonging, warmth, tavern camaraderie

### Copy examples
- Hero: *"Guilde Retail · Kirin-Tor · Alliance & Horde"*
- About: *"s'amuser sérieusement sans être sérieux"*
- Join: *"La table est mise, les chopes sont pleines. Il manque juste toi."*
- Grade names: Jambon Frais → Jambonneau → Cuisinier → Tavernier (all food/tavern themed)
- Join ritual: type **"mammouth"** in `#futur-jambons` to prove you read the rules

### Casing
- Section titles: Title Case in Cinzel (e.g. "La Guilde", "Ce qu'on fait")
- Body: sentence case
- Badges/labels: UPPERCASE with letter-spacing
- No emoji in UI copy (emoji only in informal Discord/grade icons like 🥩🍖👨‍🍳🍺)

---

## VISUAL FOUNDATIONS

### Color System
- **Background**: `#0f0b07` — near-black warm brown, feels like aged wood
- **Surface**: `#1c1409` — slightly lighter, used for alternating sections
- **Surface-2**: `#261b0d` — card backgrounds, inputs
- **Gold**: `#c9922a` — primary brand accent, borders, icons
- **Gold Light**: `#e8b84b` — headings, hover states, emphasis
- **Red**: `#8b1a1a` — danger, DPS badge color
- **Blue**: `#1a3d6b` — Tank badge color
- **Text**: `#e8dcc8` — warm parchment white
- **Text Muted**: `#8c7b65` — secondary copy, captions
- **Border**: `rgba(201,146,42,0.25)` — all borders use semi-transparent gold

### Typography
- **Display/Titles**: `Cinzel` (Google Fonts) — classical serif, gravure-like, all-caps capable
- **Body**: `Lato` / `Open Sans` — clean humanist sans at 400/700
- **Scale**: clamp-based fluid type. H1: clamp(2.2rem, 6vw, 4rem); H2: clamp(1.6rem, 4vw, 2.4rem); body: 16px base, 1.7 line-height
- **Letter-spacing**: titles +0.04–0.06em; badges +0.06–0.1em

### Backgrounds & Textures
- Pure flat dark colors (no gradients on backgrounds)
- Hero section uses a full-bleed image (`hero.jpg`) with a vignette overlay gradient (top→bottom: 40%→97% opacity dark)
- Banner image (`banniere groupe.jpg`) is a WoW in-game guild photo — warm orange/gold tones

### Animations & Motion
- **Entrées au scroll**: `.reveal` class — `opacity 0→1` + `translateY(24px→0)`, 0.6s ease, triggered by IntersectionObserver
- **Hero logo**: gentle float loop (`translateY 0→-10px→0`), 4s ease-in-out infinite
- **Hero content**: `fadeInUp` 1.1s ease on load
- **Interactions**: `transition: 0.25s ease` on all interactive elements
- **No loops, no particles unless explicitly requested**

### Cards
- Background: `var(--color-surface-2)` `#261b0d`
- Border: `1px solid rgba(201,146,42,0.25)`
- Border-radius: `8px`
- Hover: border-color → `#c9922a`, box-shadow: `0 0 24px rgba(201,146,42,0.15)`, `translateY(-3px)`
- No drop shadows at rest — shadow only on hover

### Buttons
- **Primary**: bg `#c9922a`, text `#0f0b07` (dark on gold), hover: bg `#e8b84b` + gold glow
- **Secondary**: transparent + `1px solid border`, text `#e8dcc8`, hover: border `#c9922a`, text `#e8b84b`
- **Discord**: bg `#5865F2` (Discord blurple), always white text
- Border-radius: `6px`; padding: `13px 28px`; font-weight: 700

### Ornaments & Separators
- Section separators: horizontal gold line (1px, 50% opacity) + central diamond (`10px × 10px`, rotated 45°, gold fill)
- Constructed with CSS `::before`/`::after` pseudo-elements on `.ornament`

### Badges / Role Colors
- **Tank**: blue tint `rgba(26,61,107,0.6)`, text `#7aaef5`
- **Heal**: green tint `rgba(20,90,40,0.5)`, text `#5dcc7a`
- **DPS**: red tint `rgba(139,26,26,0.5)`, text `#f06060`
- **Event badges**: mythic (purple), raid (red), social (gold), farming (green)

### WoW Class Colors
```js
const CLASS_COLORS = {
  "Guerrier": "#C79C6E",     "Paladin": "#F58CBA",
  "Chasseur": "#ABD473",     "Voleur": "#FFF569",
  "Prêtre": "#FFFFFF",       "Chevalier de la mort": "#C41F3B",
  "Chaman": "#0070DE",       "Mage": "#69CCF0",
  "Démoniste": "#9482C9",    "Moine": "#00FF96",
  "Druide": "#FF7D0A",       "Chasseur de démons": "#A330C9",
  "Évocateur": "#33937F"
};
```

### Layout
- Max-width container: `1100px`, centered, `padding: 0 20px`
- Section padding: `80px 20px`
- Mobile-first with grid `auto-fill/minmax`; breakpoints at 640px and 900px
- Navbar: fixed, `68px` height, `backdrop-filter: blur(6px)`

### Corner Radii
- Cards, buttons, inputs: `8px`
- Pill badges: `20px`
- Avatar circles: `50%`

### Imagery
- WoW in-game screenshots: warm, golden-orange tones, fantasy architecture
- Mascot emotes: AI-generated kawaii round ham characters — highly detailed, warm orange/brown palette, always on white/transparent backgrounds
- No gradients on main backgrounds; gradient only as image overlay

---

## ICONOGRAPHY

The brand uses **two distinct icon systems**:

### 1. Custom Kawaii "Jambon" Mascot Emotes (Discord stickers)
~40+ custom AI-generated images of a round ham character in various costumes/expressions. Used on Discord and decoratively on the site. All in `assets/emotes/`.

| File | Description |
|------|-------------|
| `Bienvenue.png` | Ham holding welcome banner (confetti) |
| `zen.png` | Ham meditating on yoga mat |
| `chasseur.png` | Ham as WoW hunter with pet |
| `DH.png` | Demon Hunter ham |
| `heal.png` | Healer ham |
| `Ilmeda.png` | Joker-cosplay ham (chaotic energy) |
| `Muscle.png` / `muscle2.png` | Buff ham flexing |
| `Amour.png` | Romantic ham |
| `Coucou.png` | Waving ham |
| `Dormir.png` | Sleeping ham |
| `Enerve.png` / `venere.png` / `mecontent.png` | Angry/frustrated ham |
| `effraye.png` | Scared ham |
| `Fille.png` / `garcon.png` / `enfant.png` | Gender/age variants |
| `Fee.png` | Fairy ham |
| `lol.png` / `Mdr.png` / `MDR1.png` | Laughing ham |
| `miam.png` | Hungry/food ham |
| `Non.png` / `Oui.png` / `Ok.png` | Response hams |
| `pain-choco.png` | Ham eating pain au chocolat |
| `pecheur.png` | Fishing ham |
| `pouce.png` | Thumbs up ham |
| `question.png` | Confused ham |
| `respect.png` | Respectful ham |
| `Pleurer.png` / `triste.png` | Sad/crying ham |
| `Sommeil.png` / `Soso.png` | Sleepy/meh ham |
| `sportif.png` | Athletic ham |
| `trancheuse.png` | Ham using sausage slicer |
| `tueur.png` | Assassin ham |
| `argent.png` | Rich ham |
| `zen-chat.png` | Zen cat variant |
| `demo.png` | Demo/presentation ham |

### 2. Inline SVG Icons (UI)
All UI icons are **24×24px inline SVGs**, stroke-based (`stroke-width: 1.5`), `stroke-linecap: round`, `stroke-linejoin: round`, colored with `var(--color-gold)`. Used for activity cards, nav, buttons. No external icon library — all hand-crafted in the source HTML.

---

## FILE INDEX

```
README.md                    — This file
SKILL.md                     — Agent skill definition
colors_and_type.css          — CSS custom properties (colors + typography)
assets/
  logo.png                   — Guild crest (two beer mugs on shield, 256×256)
  banniere groupe.jpg        — Guild group photo (WoW screenshot, 1920×1080)
  emotes/                    — 40+ custom kawaii jambon mascot images
preview/
  colors-brand.html          — Brand color palette
  colors-semantic.html       — Semantic / UI colors
  colors-classes.html        — WoW class colors
  type-display.html          — Display type specimens
  type-body.html             — Body type specimens
  type-scale.html            — Full type scale
  spacing-tokens.html        — Spacing, radius, shadow tokens
  components-buttons.html    — Button variants
  components-badges.html     — Badge variants (role, event, class)
  components-cards.html      — Card variants
  components-ornaments.html  — Section ornaments & separators
  brand-logo.html            — Logo + mascot showcase
  brand-emotes.html          — Emote library
ui_kits/
  landing/
    README.md                — Landing page UI kit notes
    index.html               — Full interactive landing page prototype
```

---

## Guild Ranks
1. 🥩 **Jambon Frais** — New member
2. 🍖 **Jambonneau** — Confirmed member
3. 👨‍🍳 **Cuisinier** — Active member
4. 🍺 **Tavernier** — Officer / veteran

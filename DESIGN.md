---
name: Elena & Marcos — Rejería Sevillana
description: A Sevillian wrought-iron wedding invitation — warm plaster white, near-black ironwork, and one confident terracotta accent, framed by hairline grille linework.
colors:
  plaster: "#F4EEE2"
  plaster-deep: "#EAE1CE"
  iron: "#211D17"
  iron-soft: "#4A4235"
  terracotta: "#B84A2B"
  terracotta-deep: "#8F3A21"
  terracotta-light: "#D69C87"
typography:
  display:
    fontFamily: "\"Bodoni Moda\", serif"
    fontSize: "clamp(2.25rem, 13vw, 8rem)"
    fontWeight: 400
    lineHeight: 1.05
    letterSpacing: "0.01em"
  body:
    fontFamily: "\"Archivo\", sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.6
    letterSpacing: "normal"
  label:
    fontFamily: "\"Archivo\", sans-serif"
    fontSize: "13px"
    fontWeight: 400
    lineHeight: 1.4
    letterSpacing: "0.15em"
rounded:
  sm: "2px"
spacing:
  section-y: "6rem"
  section-y-lg: "9rem"
  card-gap: "1rem"
components:
  button-primary:
    backgroundColor: "{colors.terracotta-deep}"
    textColor: "{colors.plaster}"
    rounded: "{rounded.sm}"
    padding: "12px 24px"
  button-primary-hover:
    backgroundColor: "#9C3E23"
    textColor: "{colors.plaster}"
---

# Design System: Elena & Marcos — Rejería Sevillana

## Overview

**Creative North Star: "The Wrought-Iron Courtyard"**

The system reads as a Sevillian townhouse at golden hour: warm lime-plaster walls, near-black iron grillework at every threshold, and a single geranium-terracotta accent carried at full saturation, never diluted toward a "safe" gold. It explicitly refuses the cream-paper-stationery default of generic wedding sites (including this project's own prior "elegante clásico" build) — depth and ornament come from linework and framing, not soft drop shadows or rounded pill shapes.

Ironwork is structural, not decorative-only: the same hairline SVG grille pattern that frames the hero also appears as section dividers (`.grille-divider`) and photo-card corner motifs (`.grille-frame` / `.grille-frame-2`), so the motif is load-bearing across the whole page rather than a one-off hero flourish. Display type (Bodoni Moda) is cut sharp and high-contrast, standing in for the "wrought" quality of the ironwork itself; body/UI type (Archivo) stays plain and grotesk with no italic-script anywhere except the two confirmed voice quotes (hero vow line, footer thank-you), which use `italic` on the display face, not a script font.

**Key Characteristics:**
- Warm plaster-white ground, near-black iron ink, one saturated terracotta accent — never a muted/timid gold.
- Hairline SVG grille-line patterns (data-URI, not external assets) do the work shadows/radius would do elsewhere: framing, dividing, cornering.
- Sharp, minimal corners (`rounded-sm` only) — no pill buttons, no large border-radius anywhere in the build.
- Depth via bordered plaster/iron/terracotta-deep block alternation between sections, not elevation shadows.
- Fixed 4.5:1+ contrast discipline on interactive text (see Colors → Named Rules).

## Colors

Warm, mineral, high-contrast: two neutrals doing double duty as both "paper" and "ink" backgrounds (sections alternate bg-plaster and bg-iron), plus one accent family used only for emphasis and action, never as a large fill.

### Primary
- **Terracotta** (`#B84A2B`): the single accent hue. Used sparingly — icon strokes, the "&" in the hero lockup, milestone dates, price-tier tags, link-underline color on dark sections. Never a large background fill at this exact value (buttons use the deeper step below for contrast).
- **Terracotta Deep** (`#8F3A21`): the accent's working/interactive step — all primary button fills (`bg-terracotta-deep`), paired with `text-plaster` for a verified 6.50:1 contrast ratio. This pairing replaced an earlier `bg-terracotta`/`text-iron` combination (~3.23:1) that failed contrast; the deep+plaster pairing is now the only button treatment in the build.
- **Terracotta Light** (`#D69C87`): the accent's on-dark / on-photo step. Used for the "&" in the hero headline (over the photo), the date line in the hero, and link text on `bg-iron` sections, where full terracotta would sit too dark against near-black.

### Neutral
- **Plaster** (`#F4EEE2`): base page background and "paper" sections (Nuestra Historia, Galería, RSVP). Also the text color on iron/dark sections.
- **Plaster Deep** (`#EAE1CE`): a second, slightly darker paper step used to alternate section rhythm without a hard edge (Info para Invitados, FAQ).
- **Iron** (`#211D17`): primary ink — body text color, dark section backgrounds (La Boda, Mesa de Regalos, footer), and the stroke color of every grille-line SVG on light backgrounds.
- **Iron Soft** (`#4A4235`): a lighter ink step declared in the Tailwind config; not observed in active use on any shipped section — a reserved/unused token, not a defect, but not yet load-bearing either.

### Named Rules
**The One Accent Rule.** Terracotta (in any of its three steps) is the only saturated hue in the system. It never competes with a second accent color; role differentiation (default vs. hover vs. on-dark vs. on-photo) is carried entirely by lightness steps of the same hue.

**The Ironwork-Not-Shadow Rule.** Framing and separation are done with `.grille-frame`/`.grille-divider` hairline linework and flat `border-iron/10–25` hairlines, never with `box-shadow` elevation. The two `box-shadow` uses in the build (scrolled-header shadow, `.btn-iron:hover` shadow) are state-transition feedback on interactive elements, not a general card/surface elevation system — do not extend shadows to static containers.

## Typography

**Display Font:** Bodoni Moda (with `serif` fallback)
**Body Font:** Archivo (with `sans-serif` fallback)

**Character:** A high-contrast, sharp-cut serif (standing in for engraved/wrought ironwork) paired with a plain, confident grotesk for everything functional. No italic-script anywhere — the only italic usage is Bodoni Moda's own italic cut, reserved for the two voice/quote lines.

### Hierarchy
- **Display / Hero** (400, `clamp` from `13vw` mobile to `text-9xl` desktop, leading `1.05`/`0.95`): the couple's names in the hero, set in `tracking-wide-lg` (0.15em).
- **Headline** (400, `text-4xl`–`text-5xl`): section titles (`Un camino compartido`, `La boda`, `Galería`, etc.), always paired directly beneath with a `.grille-divider` line.
- **Title** (400, `text-2xl`–`text-3xl`): milestone/venue/FAQ-question titles within a section.
- **Body** (400, `1rem`/`leading-relaxed`, `iron/80`–`iron/85` opacity on light, `plaster/70`–`plaster/90` on dark): running copy, capped at `max-w-prose` (38rem).
- **Label** (400, `13px`/`text-xs`, `tracking-wide-lg` 0.15em or `tracking-wide-xl` 0.28em, uppercase): nav links, button text, form field labels, countdown unit labels, eyebrow-style date/meta lines.

### Named Rules
**The No-Script Rule.** Script/handwriting faces are excluded system-wide; emphasis and romance are carried by Bodoni Moda's italic cut and generous letter-spacing, never a cursive font.

## Layout

Single-column content stack, `max-w-6xl`/`max-w-4xl`/`max-w-2xl`/`max-w-3xl` containers depending on section density, centered via `mx-auto`, with `px-5 md:px-10` outer gutters. Section vertical rhythm is `py-24` mobile → `py-32`/`py-36` desktop, the largest spacing step in the system and applied consistently to every full-width section. Two-column content (story milestones, ceremony/celebration cards) collapses to a single column below `md`, alternating image/text order per row for visual rhythm rather than a fixed left/right pattern. The header is fixed-position with a scroll-triggered background/contrast swap (`.header-scrolled`) rather than a static bar. Hero height is hardcoded to `100vh`/`100lvh` (not Tailwind-JIT-dependent, not `svh`/`dvh`) specifically to avoid a gap opening as Android Chrome's collapsing toolbar changes the live viewport — a durable mobile-correctness rule for this product line per PRODUCT.md, not a one-off hack.

## Elevation & Depth

Flat by default. Depth is conveyed through section-level tonal alternation (plaster → iron → plaster-deep → plaster → iron) and through the grille linework's framing, not through shadows or blur. The system's only two `box-shadow` uses are transient interaction feedback (fixed-header shadow on scroll; `.btn-iron` hover shadow), never a static resting elevation on cards or containers.

### Named Rules
**The Flat-By-Default Rule.** Cards, photo frames, and form panels sit flush with zero elevation at rest. A shadow appearing on a static, non-interactive element is a build defect, not a variant to reuse.

## Shapes

Corners are sharp almost everywhere; the one softening step in the whole system is `rounded-sm` (Tailwind's 2px), applied only to buttons and RSVP radio pills. Photo frames, grille-framed cards, and dividers are square-cornered, relying on the `.grille-frame` pseudo-element ironwork motif (a corner-scroll SVG line pattern plus a 1px full-perimeter border) for ornament instead of radius or shadow. Borders are hairline and low-opacity (`border-iron/10`–`/25`) throughout — dividers, form field underlines, radio pills, FAQ row separators — never a heavy or colored border outside the terracotta focus ring.

## Components

### Buttons
- **Shape:** sharp with a minimal 2px corner softening (`rounded-sm`).
- **Primary (`.btn-iron`):** `bg-terracotta-deep` / `text-plaster` (6.50:1 contrast, corrected from an earlier failing `bg-terracotta`/`text-iron` ≈3.23:1 pairing), `px-6–8 py-3–4`, `text-[13px]`–`text-sm` uppercase with `tracking-wide-lg`. Used for the header/mobile-menu/RSVP "Confirmar asistencia" and "Enviar confirmación" CTAs — the only filled-button role in the system.
- **Hover / Focus:** hover darkens to `#9C3E23` with a soft diffuse shadow (`0 8px 20px -8px rgba(33,29,23,.45)`) and a `scale(0.97)` press state on `:active`. All focusable elements site-wide get a 2px solid `terracotta` `outline` with 3px offset on `:focus-visible`.
- **Ghost (link style):** `.link-underline` — no fill, a `currentColor` underline that wipes in from the left on hover (260ms). Used for nav links and secondary actions ("Cómo llegar", "Ver lista de regalos").

### Cards / Containers (grille-framed photo cards)
- **Corner Style:** square; ironwork corner motif (`.grille-frame::before`/`::after`) substitutes for radius — a 1px full-perimeter border plus a 34×34px SVG scroll-line corner flourish, doubled on the opposite corner via `.grille-frame-2`.
- **Background:** the photo itself; no card chrome behind images.
- **Shadow Strategy:** none (see Elevation & Depth).
- **Border:** 1px solid iron (`#211D17`) on light-section cards.

### Inputs / Fields
- **Style:** borderless except a single `border-b border-iron/25` underline; transparent background; no radius.
- **Focus:** underline color shifts to `terracotta` on focus.
- **Error:** `text-red-700` inline message beneath the field, hidden by default, toggled by client-side validation — the only non-palette color in the system, reserved strictly for validation error text.

### Navigation
- Desktop: uppercase `13px` label-weight links with `tracking-wide-lg`, `.link-underline` hover treatment; fixed header swaps from photo-legible plaster-on-shadow text to solid iron-on-plaster once scrolled past the hero (`.header-scrolled`).
- Mobile: full-screen overlay menu (`#mobile-menu`), display-face links at `text-2xl`–`3xl`, fade/opacity-driven open state, no slide/drawer animation.

### Grille System (signature component)
The hairline SVG ironwork pattern is the system's one true signature device, expressed as three reusable pieces: `.grille-divider` (a repeating diamond-and-dot lattice used under every section headline, with an `.on-dark` stroke-color variant for iron-background sections), and `.grille-frame`/`.grille-frame-2` (opposite-corner scroll-line flourishes plus a full-perimeter hairline border, wrapping every photo, map embed, and the IBAN plaque). All grille SVGs are inline data-URIs, so the motif never depends on an external asset and scales crisply at any density.

## Do's and Don'ts

### Do:
- **Do** keep the grille linework (`.grille-divider`, `.grille-frame`/`-2`) as the system's only ornamental/framing device — it is reused across hero, story, boda, gallery, and regalo sections, which is what makes it a signature rather than a one-off.
- **Do** pair `bg-terracotta-deep` with `text-plaster` for any filled button or tag; this is the only button-fill pairing in the build and the one verified to clear 4.5:1 contrast.
- **Do** alternate `bg-plaster` / `bg-iron` / `bg-plaster-deep` at the section level to carry rhythm and depth without shadows.
- **Do** use `rounded-sm` as the system's one corner-softening step; every other surface stays sharp-cornered.

### Don't:
- **Don't** introduce a second saturated accent hue alongside terracotta; role differentiation comes from its three lightness steps (`terracotta` / `terracotta-deep` / `terracotta-light`), not a second color family.
- **Don't** add `box-shadow` elevation to static cards or containers; shadows in this system are reserved for transient hover/scroll state feedback only.
- **Don't** use `bg-terracotta` (the mid step) with `text-iron` for any text-bearing fill — this exact pairing was shipped and measured at ≈3.23:1 and replaced for contrast failure; it is a defect this build carried, not a system value to reuse elsewhere.
- **Don't** introduce a script/handwriting typeface; emphasis is carried by Bodoni Moda's italic cut and letter-spacing only.
- **Don't** add kickers/eyebrow label components, glyph icon fonts, or a system display face — none exist in this build; all icons are inline SVG, and the only "meta line" pattern (date under the hero title, milestone dates) is set in the system's own Label type role, not a distinct eyebrow component.

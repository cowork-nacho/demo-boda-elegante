# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Two audiences, depending on the project this demo is shown for:

- **Wedding-planning agencies** evaluating whether to offer this kind of invitation-website service to their own bride/groom clients. They see this as a portfolio sample during a sales conversation with the developer/studio (NGS).
- **Couples planning a wedding directly**, sold to without an agency intermediary, evaluating the finished site as their own future invitation page.

Both audiences are comparing this against generic free templates, Google Sites-built invitations, or other freelance output, and are judging production quality as a proxy for the studio's competence.

## Product Purpose

A single-page wedding invitation website (this instance: fictional couple "Elena & Marcos", Sevilla, 12 June 2027) that functions as a real, deployable invitation — countdown, ceremony/celebration details with maps, photo gallery, guest info, RSVP form, FAQ — while doubling as a portfolio piece. Success is a visitor (agency or couple) concluding the studio can be trusted with a real wedding's digital presence: nothing reads as "demo," "template," or unfinished.

## Positioning

Bespoke, agency-grade craft — the gap between a free template/Google Sites invitation and a real commissioned piece — delivered with zero backend/CMS dependency (static HTML, deployable anywhere, e.g. GitHub Pages) so it stays cheap to produce and host while still reading as premium.

## Operating Context

- Each engagement is typically a new fictional or real couple, a new visual "world" (e.g. this site's "elegante clásico" direction; sibling demos exist in different styles — boho, moderna — under other repos in the same GitHub org), reusing the same content sections (hero/countdown, our story, the wedding, gallery, guest info, gift table, RSVP, FAQ, music, contact, footer).
- Deployed as static sites to GitHub Pages under the `cowork-nacho` GitHub organization; each demo is its own repo.
- RSVP submissions go through FormSubmit (no backend); maps are embedded Google Maps iframes; images are downloaded stock photos (Unsplash/Pexels), never real photos of real people, committed into an `/img` folder.
- Viewed on a real spread of client devices during sales conversations and by end users on their own phones — mobile correctness (including Android Chrome's dynamic viewport/toolbar behavior) is a recurring, real failure point, not a hypothetical.

## Capabilities and Constraints

- No backend, no CMS, no database — pure static HTML/CSS/JS.
- No build step: deployable as-is to GitHub Pages.
- RSVP form must submit somewhere real (FormSubmit) with genuine client-side validation and a non-alert() success state.
- All imagery must be real stock photography with a usable license, never AI-generated or placeholder/lorem-picsum, and must never depict identifiable real people presented as "the couple" or "the guests" — a hard requirement, not a style preference.
- Any placeholder data (IBAN, phone numbers, emails) must be visibly, explicitly marked as an example in the copy itself, not just in code comments.
- Must hold up under real interaction testing (open/close menus repeatedly, resize, scroll) — this demo shipped several rounds of bugs (mobile menu content clipping, header legibility over the hero photo, hero height instability tied to Tailwind's CDN runtime compilation and Android Chrome's collapsing toolbar) discovered only through hands-on device testing, not first-pass review.

## Brand Commitments

- Studio credit line in the footer: "Diseño y desarrollo — NGS".
- No other fixed brand identity across demos; each demo's couple, palette, and typography are project-specific and not meant to persist between engagements.

## Evidence on Hand

- Sibling demos in sibling repos under the `cowork-nacho` org (e.g. `demo-boda-boho`, `demo-boda-moderna`) — useful as working reference implementations when diagnosing cross-browser/viewport bugs, since comparing against a known-good sibling has repeatedly been the fastest way to isolate a real defect from a testing-tool artifact.
- No real client testimonials, case studies, or press — none should be fabricated.

## Product Principles

1. Every demo must be indistinguishable from a real paid commission — no visible "demo" labeling, no Lorem ipsum, no placeholder aesthetic.
2. Static-only, zero-backend by design: this is a durable technical constraint, not a temporary shortcut.
3. Mobile correctness is verified on real interaction patterns (repeated open/close, live resize, actual scroll), because the worst bugs in this product line have consistently been timing/device-specific, not visible in a single static screenshot.
4. Placeholder/example data is always self-disclosing in the visible copy.
5. Photography must never imply real identifiable people are the subject couple or guests.

## Accessibility & Inclusion

No formally required standard confirmed yet. Existing build has already applied WCAG-style contrast fixes (4.5:1 minimum for body text) as good practice; treat that bar as the working default until told otherwise.

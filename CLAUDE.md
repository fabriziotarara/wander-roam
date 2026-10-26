# Wander & Roam — Website Playbook

This file is the shared rulebook for anyone (human or AI) editing wanderroamtravel.com.
Claude Code reads it automatically; Cursor and other AI tools follow it too. If you change
how the site works, update this file in the same pull request.

**Placeholders Fabrizio should fill in when the repo is created:**
- Repo: `https://github.com/fabriziotarara/wander-roam`
- Netlify site name: `wanderroamtravel`
- Where local image files live in the repo: `TODO (folder name)`

---

## What this site is

Marketing site for **Wander & Roam Travel**, a bespoke travel advisory run by
**Courtney Tarara** in Howell, MI, affiliated with **Fora Travel**. Its job is to
introduce Courtney, showcase her specialties, build trust (testimonials, partners),
and get visitors to submit the contact form or visit her Fora profile:
https://www.foratravel.com/advisor/courtney-tarara

## How the site is built (facts, verified Oct 2026)

- **One single page**: everything lives in `index.html` (~45 KB). There are no
  other pages; navigation scrolls to anchored sections on the same page.
- **Hosted on Netlify.** Merging to the `main` branch publishes the live site.
- **Styling: Tailwind CSS** via the CDN script, with the theme defined in the
  inline `tailwind.config` block in the page `<head>`. No build step — edit the
  HTML directly.
- **Fonts (Google Fonts):** "Dancing Script" for display headings (used through
  the `font-serif` class) and "Inter" for body text (`font-sans`).
- **Testimonial slider:** Swiper (loaded from unpkg).
- **Contact form: Netlify Forms.** The form is named `contact` and has fields
  `name`, `email`, `destination`, `message`, plus a hidden `bot-field` honeypot
  and `form-name` hidden input. Submissions arrive through Netlify.
- **Images** currently come from Unsplash URLs, one photo hosted on Fora's
  Cloudinary, and local files. Keep new images consistent with the recipes below.

## Site map (section ids — do not rename these)

The nav links point at these anchors; renaming an id breaks navigation.

| Section id | What it is |
|---|---|
| (hero) | Full-screen photo, "Wander & Roam" headline, tagline "Bespoke journeys, crafted with distinction.", "Start Your Journey" button |
| `#about` | "A Passion For Perfected Travel" — Courtney's intro and photo |
| `#specialties` | "Travel Specialties" — three cards: Bespoke Itineraries, Luxury Resorts, Ocean & River Cruises |
| `#process` | "The Planning Process" — I. Discovery, II. Design, III. Execution |
| `#testimonials` | "From Our Travelers" — Swiper slider of client testimonials |
| `#fora-affiliation` | "Powered by Fora Travel" — explains the Fora benefits, links to Courtney's Fora profile |
| `#partners` | "Proudly Partnered With" — Belmond, Four Seasons, Ritz-Carlton, Virtuoso |
| `#contact` | "Begin Your Journey" — the Netlify contact form |
| footer | Dark footer, auto-updating copyright year, "Affiliated with Fora Travel" link |

## Brand system

**Colors** (defined in the Tailwind config — always use these classes, never new hex codes):
- `brand-dark` — #1a1a1a (headings, footer)
- `brand-sand` — #d1c4b0 (accents, underlines, testimonial border)
- `brand-light` — #f9f9f9 (section backgrounds)
- `brand-gray` — #666666 (secondary text)

**Voice:** elegant, warm, unhurried, personal. First person as Courtney where the
existing copy does ("Welcome! I'm Courtney Tarara…"). Words the site uses:
*bespoke, crafted, curated, distinction, seamless, treasured*. Avoid hype,
exclamation marks, discount/deal language, and anything that sounds like a
mass-market travel agency. US spelling.

**Headings** use the script font (`font-serif`) — keep new headings in the same style.

## Workflow rules (apply to every change, no exceptions)

1. **Never commit directly to `main`.** Work on a branch and open a pull request.
2. **One change per pull request** (one testimonial, one photo swap…). Small PRs
   are easy to preview, approve, and undo.
3. Netlify builds a **Deploy Preview** for every PR. Whoever requested the change
   reviews the preview before merging. **Merging = publishing.**
4. Write plain-language PR titles a non-developer can understand
   ("Add the Hendersons' testimonial", not "feat: update index.html").
5. If a change goes wrong after publishing, revert the PR / roll back the deploy
   in Netlify — never hand-edit the live branch in a panic.

## Recipes

**Change wording**
Find the section by its id, edit only the text, leave all classes and tags
untouched. Check the line still reads well at mobile width (long words in the
script headings can overflow).

**Swap a photo**
Replace the image URL or file, keep the existing sizing/crop parameters and
layout classes, and always write meaningful `alt` text ("Couple watching the
sunset over the Amalfi Coast", not "photo"). For the hero, keep a wide
landscape image at least 1920px across — it's displayed at 85% of screen height.

**Add a testimonial**
In `#testimonials`, duplicate an existing slide inside `#testimonial-slides`
and replace the quote and name. Keep the Swiper slide markup and the
`testimonial-card` styling exactly as the copied slide. Use the client's words
verbatim; first name + last initial or full name per the client's preference.

**Add or edit a specialty**
In `#specialties`, duplicate an existing card and edit its title and text.
The grid is designed around three cards — if a fourth is ever added, check the
layout carefully at mobile and desktop widths in the preview.

**Update partners**
In `#partners`, keep the logo/link treatment identical to the existing entries.
Partner links open in a new tab (`target="_blank" rel="noopener noreferrer"`).

**Change contact details or links**
Courtney's Fora profile URL (above) appears in `#fora-affiliation` and in the
footer. If it ever changes, update both places in the same PR.

## Hard rules — do not do these

- Don't rename or remove section ids (nav links depend on them).
- Don't touch the contact form's wiring: form name `contact`, the `form-name`
  hidden input, and the `bot-field` honeypot must stay exactly as they are, or
  submissions silently stop working.
- Don't remove the "Affiliated with Fora Travel" footer link.
- Don't add frameworks, build tools, or new libraries without Fabrizio's approval.
- Don't hotlink images from random websites; use Unsplash, the repo's image
  folder, or Courtney's own photos.

## Before opening a PR, check

- [ ] Preview builds without errors
- [ ] Page looks right at phone width and desktop width
- [ ] All nav links still scroll to their sections
- [ ] New images have alt text
- [ ] No spelling errors in new copy (read it once, out loud if unsure)

## Known notes (as of Oct 2026)

- The site has **no `sitemap.xml` or `robots.txt`** yet — adding both is a small,
  worthwhile SEO improvement for a future PR.
- One legacy image path from the site's old WordPress setup (`wp-content/uploads/…`)
  is still referenced in the page. Harmless, but worth tidying if that image is
  ever replaced.

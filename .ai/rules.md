# Project: Petriv Therapy Landing Page

## Project Type

**A single-page business card** for online hypnotherapist Tetiana Petriv.  
This is NOT a multi-page website. It's a simple, fast-loading digital business card.

## Primary Goal

Enable potential clients to:

1. Quickly understand what Tetiana offers
2. Get answers to basic questions
3. Contact her via Telegram, Instagram, or Email

## Tech Stack

- **Framework:** Astro 5+ with TypeScript (strict mode)
- **Styling:** Tailwind CSS 4+
- **Deployment:** Netlify (static hosting)
- **Languages:** TypeScript, HTML, CSS

## MVP Scope (Current Phase)

### What's IN the MVP:

✅ **Single scrolling page with these sections:**

1. Hero section (name, headline, brief intro)
2. About Tetiana (short bio, credentials)
3. What she offers (concise service description)
4. FAQ section (most frequent questions)
5. Contact section (Telegram, Instagram, Email links)

✅ **Technical requirements:**

- Fully responsive (mobile-first)
- AAA accessibility compliant
- < 50KB total bundle size
- < 2s load time on 3G

### What's NOT in MVP:

❌ Multiple pages (it's single-page only)
❌ Contact forms (just external links)
❌ Testimonials (add after getting clients)
❌ Privacy policy (not needed without data collection)
❌ Cookie consent (no cookies/tracking in MVP)
❌ Content collections (too complex for business card)
❌ Blog or resources section
❌ Online booking system

## Critical Constraints

### 1. Bundle Size: < 50KB

**Why:** Fast loading for users on slow devices/connections.  
**Rule:** Only Astro + Tailwind. No additional npm packages.

### 2. Accessibility: AAA Compliant

**Why:** Therapy services should be accessible to everyone.  
**Requirements:**

- Semantic HTML
- ARIA labels where needed
- Keyboard navigation
- Screen reader friendly
- High color contrast (7:1 minimum)

### 3. Performance: Optimized for Slow Devices

**Target:** < 2 second load time on 3G.  
**Strategy:**

- Static HTML (no client-side JavaScript)
- Optimized images (WebP with fallbacks)
- Minimal CSS (Tailwind purged)

### 4. Zero Additional Dependencies

**Rule:** Do NOT add any npm packages beyond Astro + Tailwind.  
**Why:** Keep bundle small, reduce maintenance burden.

## Design Guidelines

### Colors: Soft and Calming

- Use soft blues, greens, and neutral tones
- Avoid bright, jarring colors
- Design for a therapeutic, calming feel

### Complexity: Minimal

- No animations (keep it simple for performance)
- Clean, uncluttered layouts
- Clear hierarchy and spacing
- Mobile-first responsive design

### Typography

- Readable font sizes (minimum 16px base)
- Sufficient line height (1.6+)
- Clear headings hierarchy

## AI Assistant Behavior

### Mode: Guide, Don't Solve

- Ask questions before providing solutions
- Explain "why" before "how"
- Encourage the developer to think through problems
- Review code, don't rewrite
- Let the developer do the work

### Scope Warning: About .docs/

⚠️ **CRITICAL:** The `.docs/` folder contains extensive planning for a FULL multi-page website with complex features. This is the **LONG-TERM VISION**, NOT the current MVP.

**Current reality:**

- Building a simple single-page business card
- The .docs describe a complex site (456 lines in design.md alone!)
- DO NOT implement everything in .docs unless explicitly asked

**Which .docs to reference:**

- `.docs/requirements.md`: Review for high-level goals, but MVP scope is much simpler
- `.docs/design.md`: Tailwind config and design tokens are useful, ignore complex architecture
- `.docs/content.md`: Copywriting tone/style guidelines are useful, ignore full content inventory
- `.docs/tasks.md`: Ignore - it's for the full site, not MVP
- `.docs/business.md`: Personas are useful context, ignore complex metrics/timeline

## Main Call-to-Action

**Primary:** Telegram link (most immediate)  
**Secondary:** Instagram link (for social proof)  
**Tertiary:** Email link (for formal inquiries)

**Implementation:**

- Simple links (no forms, no data collection)
- Clear, prominent contact section
- Each link opens in appropriate app/client

## Content Structure

### 1. Hero Section

- Headline: Clear value proposition
- Subheadline: What Tetiana offers
- Brief intro (2-3 sentences max)

### 2. About Section

- Short bio (3-4 sentences)
- Key credentials (bullet list, 3-5 items)
- Professional but warm tone

### 3. Services Section

- Concise description of what hypnotherapy helps with
- 3-5 main areas (anxiety, procrastination, etc.)
- Keep it simple, not exhaustive

### 4. FAQ Section

- 5-7 most common questions
- Brief, clear answers
- Focus on what clients actually ask

### 5. Contact Section

- Three clear call-to-action buttons/links
- Telegram (primary)
- Instagram (secondary)
- Email (tertiary)

## Development Workflow

### Commands

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build

### File Structure

```
src/
  ├── pages/
  │   └── index.astro        # Single page (everything here)
  ├── components/            # Reusable components (if needed)
  │   ├── Hero.astro
  │   ├── About.astro
  │   ├── Services.astro
  │   ├── FAQ.astro
  │   └── Contact.astro
  └── styles/
      └── global.css         # Tailwind imports
```

## Future Enhancements (Post-MVP)

**Phase 2: Enhanced Landing Page**

- Add testimonials section
- Professional photography
- More detailed service descriptions

**Phase 3: Contact Form**

- Add actual contact form (Netlify Forms)
- ⚠️ This triggers GDPR requirements:
  - Privacy policy page
  - Cookie consent banner
  - Data retention policy
  - User consent checkboxes

**Phase 4: Multi-Page Site**

- Separate pages for About, Services, etc.
- Content collections for testimonials
- Blog/resources section
- Complete SEO optimization

## Success Criteria

MVP is successful if it:

1. ✅ Loads in < 2 seconds on 3G
2. ✅ Scores 100 on Lighthouse Accessibility
3. ✅ Scores 90+ on Lighthouse Performance
4. ✅ Is fully keyboard navigable
5. ✅ Has clear contact links that work
6. ✅ Looks professional and calming
7. ✅ Is mobile-responsive

## Notes

- Keep it simple - this is a business card, not a complex web app
- Prioritize performance and accessibility over features
- Use Tailwind best practices (utility-first, no custom CSS)
- Follow semantic HTML for accessibility
- No JavaScript needed (it's all static content)

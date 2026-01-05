# Design Document: Hypnotherapist Landing Page

## Overview

This design outlines a modern, accessible, and GDPR-compliant static website for online hypnotherapist Tetiana Petriv. The site will be built using Astro, a modern static site generator that provides excellent performance, SEO optimization, and developer experience while generating fast, static HTML. The design emphasizes trust-building through professional presentation and showcasing the benefits and technology of online therapy, while maintaining a calm, welcoming aesthetic appropriate for therapeutic services.

The website will be deployed as a static site on Netlify, leveraging Netlify Forms for contact functionality and Netlify's built-in performance optimizations. Astro's component-based architecture and built-in optimizations make it ideal for creating accessible, SEO-friendly, and performant websites that meet modern web standards.

## Architecture

### Technology Stack

- **Framework**: Astro 4.x with TypeScript
- **Styling**: Tailwind CSS with Astro integration
- **Components**: Astro components with optional framework integrations
- **Content**: Markdown for content management
- **Build Process**: Astro's built-in optimization (image optimization, CSS/JS bundling)
- **Deployment**: Netlify static hosting with Astro adapter
- **Forms**: Netlify Forms integration
- **Analytics**: Privacy-focused analytics (Netlify Analytics or Plausible)
- **Performance**: Astro's automatic optimizations (partial hydration, image optimization, asset bundling)

### Site Structure

```
/
├── src/
│   ├── pages/
│   │   ├── index.astro (Homepage)
│   │   ├── about.astro (About Tetiana)
│   │   ├── services.astro (Online Hypnotherapy Services)
│   │   ├── online-sessions.astro (How Online Sessions Work)
│   │   ├── contact.astro (Contact & Online Booking)
│   │   └── privacy.astro (Privacy Policy)
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── Hero.astro
│   │   ├── Services.astro
│   │   ├── Testimonials.astro
│   │   ├── ContactForm.astro
│   │   ├── OnlineSessionInfo.astro
│   │   └── CookieConsent.astro
│   ├── layouts/
│   │   └── Layout.astro
│   ├── styles/
│   │   └── global.css (Tailwind base styles)
│   └── content/
│       ├── testimonials/
│       └── services/
├── public/
│   ├── images/
│   ├── icons/
│   ├── _headers (Netlify headers)
│   └── _redirects (Netlify redirects)
├── astro.config.mjs
├── tailwind.config.mjs
├── netlify.toml
└── package.json
```

### Design Principles

- **Calming Aesthetic**: Soft color palette (blues, greens, neutrals) implemented through Tailwind's color system
- **Professional Credibility**: Clean typography using Tailwind's typography utilities
- **Mobile-First**: Responsive design with Tailwind's responsive prefixes (sm:, md:, lg:, xl:)
- **Performance-First**: Astro's automatic optimizations with Tailwind's CSS purging
- **Accessibility-First**: Tailwind's accessibility utilities and semantic HTML
- **Component-Based**: Reusable Astro components with consistent Tailwind styling
- **Design System**: Consistent spacing, colors, and typography through Tailwind's design tokens

## Components and Interfaces

### Layout Component (Layout.astro)

- **Base HTML Structure**: DOCTYPE, head, body with proper meta tags
- **SEO Integration**: Dynamic meta tags, structured data, Open Graph
- **Global Styles**: CSS reset, typography, accessibility styles
- **Cookie Consent**: GDPR-compliant cookie banner integration
- **Analytics**: Privacy-respecting analytics integration

### Header Component (Header.astro)

- **Navigation**: Simple, uncluttered menu with clear labels including "Online Sessions" page
- **Logo/Branding**: Professional typography-based logo with Tetiana's name
- **Contact CTA**: Prominent email and "Book Online Consultation" button
- **Accessibility**: Skip navigation link, keyboard navigation support
- **Mobile Menu**: Responsive hamburger menu for mobile devices
- **Timezone Indicator**: Display service availability across time zones

### Hero Section Component (Hero.astro)

- **Professional Headshot**: Optimized image with Astro's Image component
- **Value Proposition**: Clear headline about hypnotherapy benefits
- **Credentials**: Brief display of key qualifications
- **Primary CTA**: "Schedule Free Consultation" button
- **Trust Indicators**: Years of experience, client success metrics

### Services Section Component (Services.astro)

- **Service Cards**: Clean cards for different online hypnotherapy specializations (anxiety, procrastination, personal development)
- **Content Integration**: Markdown content from content collections
- **Approach Description**: Explanation of online therapeutic methodology
- **Benefits List**: Clear outcomes clients can expect from online sessions
- **Process Overview**: Step-by-step online treatment approach

### Testimonials Component (Testimonials.astro)

- **Content Collections**: Testimonials managed through Astro content collections
- **Client Stories**: Anonymized success stories with consent, highlighting online therapy experience
- **Quote Format**: Professional testimonial layout
- **Credibility Indicators**: First name + last initial, country (for international reach)
- **Rotating Display**: Multiple testimonials with smooth transitions

### Contact Form Component (ContactForm.astro)

- **GDPR Compliance**: Explicit consent checkboxes for data processing
- **Field Validation**: Client-side validation with TypeScript
- **Timezone Selection**: Allow clients to indicate their timezone for scheduling
- **Accessibility**: Proper labels, error messaging, keyboard navigation
- **Netlify Integration**: Netlify Forms configuration
- **Success Feedback**: Clear confirmation messaging for online consultation booking

### Online Session Info Component (OnlineSessionInfo.astro)

- **Technology Requirements**: List of required software/hardware (video conferencing platform, stable internet)
- **Session Format**: Explanation of how online sessions work
- **Privacy Assurance**: Information about secure, confidential online sessions
- **FAQ Section**: Common questions about online hypnotherapy
- **Getting Started**: Step-by-step guide for first online session

### Footer Component (Footer.astro)

- **Contact Information**: Email, timezone availability
- **Online Session Hours**: Global availability schedule
- **Legal Links**: Privacy policy, terms of service
- **Professional Memberships**: Relevant certification bodies
- **Social Proof**: Professional association logos

## Data Models

### Astro Content Collections

#### Testimonials Collection

```typescript
// src/content/config.ts
import { defineCollection, z } from "astro:content";

const testimonialsCollection = defineCollection({
  type: "content",
  schema: z.object({
    name: z.string(), // First name + last initial
    location: z.string(), // Country or region (for online clients)
    service: z.string(), // Type of hypnotherapy received
    rating: z.number().min(1).max(5),
    featured: z.boolean().default(false),
    publishedDate: z.date(),
    isOnlineClient: z.boolean().default(true), // Highlight online therapy success
  }),
});
```

#### Services Collection

```typescript
const servicesCollection = defineCollection({
  type: "content",
  schema: z.object({
    title: z.string(),
    description: z.string(),
    duration: z.string(), // e.g., "60 minutes"
    price: z.string().optional(),
    benefits: z.array(z.string()),
    order: z.number(), // Display order
    featured: z.boolean().default(false),
  }),
});
```

### Form and Configuration Data

### Contact Form Data

```typescript
interface ContactFormData {
  name: string; // Required, 2-100 characters
  email: string; // Required, valid email format
  timezone?: string; // Optional, for scheduling flexibility
  message: string; // Required, 10-1000 characters
  preferredContact: "email";
  consentGiven: boolean; // Required, GDPR compliance
  timestamp: Date; // Auto-generated
  source: "contact-form";
}
```

### SEO Configuration

```typescript
interface SEOConfig {
  title: string; // Page-specific, 50-60 characters
  description: string; // Page-specific, 150-160 characters
  keywords: string[]; // Relevant online hypnotherapy, procrastination, anxiety terms
  canonicalUrl: string; // Absolute URL
  openGraph: {
    title: string;
    description: string;
    image: string;
    type: "website";
  };
  structuredData: {
    "@type": "ProfessionalService"; // Changed from LocalBusiness
    name: "Tetiana Petriv Online Hypnotherapy";
    description: string;
    serviceType: "Online Hypnotherapy";
    areaServed: "Worldwide"; // Global service
    availableLanguage: string[];
    email: string;
  };
}
```

### Astro Configuration

```typescript
// astro.config.mjs
import { defineConfig } from "astro/config";
import tailwind from "@astrojs/tailwind";
import sitemap from "@astrojs/sitemap";
import netlify from "@astrojs/netlify";

export default defineConfig({
  site: "https://tetiana-hypnotherapy.netlify.app",
  integrations: [
    tailwind({
      applyBaseStyles: false, // Custom base styles
    }),
    sitemap(),
  ],
  image: {
    service: squooshImageService(),
  },
  adapter: netlify(),
});
```

### Tailwind Configuration

```typescript
// tailwind.config.mjs
export default {
  content: ["./src/**/*.{astro,html,js,jsx,md,mdx,svelte,ts,tsx,vue}"],
  theme: {
    extend: {
      colors: {
        primary: {
          50: "#f0f9ff",
          100: "#e0f2fe",
          500: "#0ea5e9",
          600: "#0284c7",
          700: "#0369a1",
        },
        secondary: {
          50: "#f0fdf4",
          100: "#dcfce7",
          500: "#22c55e",
          600: "#16a34a",
          700: "#15803d",
        },
        neutral: {
          50: "#fafafa",
          100: "#f5f5f5",
          500: "#737373",
          600: "#525252",
          900: "#171717",
        },
      },
      fontFamily: {
        sans: ["Inter", "system-ui", "sans-serif"],
        serif: ["Merriweather", "serif"],
      },
      spacing: {
        "18": "4.5rem",
        "88": "22rem",
      },
    },
  },
  plugins: [require("@tailwindcss/forms"), require("@tailwindcss/typography")],
};
```

### Cookie Consent Data

```typescript
interface CookieConsent {
  essential: boolean; // Always true, cannot be disabled
  analytics: boolean; // User choice
  marketing: boolean; // User choice, likely false for therapy
  timestamp: Date; // When consent was given
  version: string; // Consent policy version
}
```

## Correctness Properties

_A property is a characteristic or behavior that should hold true across all valid executions of a system—essentially, a formal statement about what the system should do. Properties serve as the bridge between human-readable specifications and machine-verifiable correctness guarantees._

### Property Reflection

After analyzing all acceptance criteria, several properties can be consolidated to eliminate redundancy:

- **Form submission properties** (2.4, 2.5) can be combined into a comprehensive form behavior property
- **SEO meta tag properties** (3.1, 3.5) can be combined into a single meta tag validation property
- **Accessibility properties** (5.1, 5.2, 5.5, 5.6, 5.7) can be grouped into comprehensive accessibility validation
- **Content optimization properties** (6.1, 6.2, 6.5) can be combined into asset optimization validation
- **Analytics properties** (7.1, 7.2, 7.4) can be consolidated into privacy-compliant analytics behavior

### Correctness Properties

**Property 1: Form Submission Behavior**
_For any_ valid contact form submission, the system should send a notification and display user confirmation
**Validates: Requirements 2.4, 2.5**

**Property 2: SEO Meta Tag Completeness**
_For any_ page on the website, all required SEO meta tags (title, description, Open Graph, Twitter Cards) should be present and properly formatted
**Validates: Requirements 3.1, 3.5**

**Property 3: Keyword Integration**
_For any_ page content and meta tags, relevant hypnotherapy and local area keywords should be naturally integrated
**Validates: Requirements 3.3**

**Property 4: Mobile Responsiveness**
_For any_ viewport size between 320px and 1920px width, the layout should remain functional and visually appropriate
**Validates: Requirements 3.7**

**Property 5: Cookie Consent Compliance**
_For any_ user interaction with cookie preferences, the system should respect choices and only process data with explicit consent
**Validates: Requirements 4.3, 4.4**

**Property 6: Form Data Minimization**
_For any_ data collection form, only essential fields should be required and optional fields should be clearly marked
**Validates: Requirements 4.6**

**Property 7: Image Accessibility**
_For any_ image element on the website, appropriate alternative text should be provided for screen readers
**Validates: Requirements 5.1**

**Property 8: Keyboard Navigation**
_For any_ interactive element, keyboard navigation should provide the same functionality as mouse interaction
**Validates: Requirements 5.2**

**Property 9: Color Contrast Compliance**
_For any_ text and background color combination, the contrast ratio should meet or exceed WCAG AA+ standards (7:1 for normal text, 4.5:1 for large text)
**Validates: Requirements 5.3**

**Property 10: Semantic HTML Structure**
_For any_ page, the heading hierarchy should be logical (h1 → h2 → h3) and semantic HTML elements should be used appropriately
**Validates: Requirements 5.5**

**Property 11: Screen Reader Compatibility**
_For any_ content element, appropriate ARIA attributes and semantic markup should support assistive technologies
**Validates: Requirements 5.6**

**Property 12: Focus Indicators**
_For any_ focusable element, visible focus indicators should be provided for keyboard navigation
**Validates: Requirements 5.7**

**Property 13: Image Optimization**
_For any_ image served by the website, it should be in an optimized format (WebP, AVIF) with appropriate fallbacks
**Validates: Requirements 6.1**

**Property 14: Lazy Loading Implementation**
_For any_ non-critical content below the fold, lazy loading should be implemented to improve initial page load
**Validates: Requirements 6.2**

**Property 15: Offline Functionality**
_For any_ previously visited page, basic content should be available offline through service worker caching
**Validates: Requirements 6.4**

**Property 16: Asset Compression**
_For any_ CSS or JavaScript file, the production version should be minified and compressed
**Validates: Requirements 6.5**

**Property 17: Privacy-Compliant Analytics**
_For any_ analytics tracking event, it should only fire when user has provided consent and respect privacy preferences
**Validates: Requirements 7.1, 7.2, 7.4**

## Error Handling

### Form Validation Errors

- **Client-side validation**: Immediate feedback for invalid inputs
- **Server-side validation**: Backup validation for security
- **Network errors**: Graceful handling of submission failures
- **Spam detection**: Integration with Netlify's spam filtering

### Accessibility Errors

- **Missing alt text**: Build-time validation for image accessibility
- **Color contrast failures**: Automated testing for WCAG compliance
- **Keyboard navigation issues**: Manual and automated testing protocols
- **Screen reader compatibility**: Testing with actual assistive technologies

### Privacy Compliance Errors

- **Cookie consent failures**: Fallback to essential cookies only
- **Data processing without consent**: Strict validation before any data collection
- **Privacy policy updates**: Version control and user notification system

### Performance Errors

- **Slow loading**: Progressive enhancement and graceful degradation
- **Large asset sizes**: Automated optimization and compression
- **Network failures**: Service worker fallbacks and offline functionality

## Testing Strategy

### Dual Testing Approach

The testing strategy employs both unit tests and property-based tests to ensure comprehensive coverage:

**Unit Tests**: Focus on specific examples, edge cases, and integration points

- Form validation with specific invalid inputs
- Cookie consent banner display on first visit
- Structured data markup validation
- Netlify configuration file validation
- Privacy policy content completeness

**Property-Based Tests**: Verify universal properties across all inputs

- Form submission behavior across all valid input combinations
- SEO meta tag presence across all pages
- Accessibility compliance across all interactive elements
- Mobile responsiveness across all viewport sizes
- Image optimization across all image formats

### Property-Based Testing Configuration

**Testing Framework**: Vitest with fast-check for property-based testing
**Test Configuration**: Minimum 100 iterations per property test
**Test Tagging**: Each property test references its design document property

Example test tag format:

```typescript
// Feature: hypnotherapist-landing-page, Property 1: Form Submission Behavior
```

### Testing Tools and Libraries

**Astro Testing**:

- Vitest for unit testing Astro components
- @astro/check for TypeScript and Astro component validation
- Playwright for end-to-end testing

**Accessibility Testing**:

- axe-core for automated accessibility testing
- Pa11y for command-line accessibility testing
- Manual testing with screen readers (NVDA, JAWS, VoiceOver)

**Performance Testing**:

- Lighthouse CI for performance metrics
- WebPageTest for real-world performance analysis
- Astro's built-in bundle analyzer for asset optimization

**SEO Testing**:

- Structured data testing tool validation
- Meta tag analysis and optimization
- Sitemap validation and testing

**Privacy Compliance Testing**:

- Cookie consent flow testing
- GDPR compliance validation
- Data processing consent verification

### Integration Testing

**End-to-End Scenarios**:

- Complete user journey from landing to contact form submission
- Cookie consent flow and preference management
- Mobile device navigation and functionality
- Accessibility user flows with assistive technologies

**Cross-Browser Testing**:

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Accessibility testing across different browser/screen reader combinations

The testing strategy ensures that both specific functionality works correctly (unit tests) and that universal properties hold across all possible inputs (property-based tests), providing comprehensive validation of the website's correctness and compliance requirements.

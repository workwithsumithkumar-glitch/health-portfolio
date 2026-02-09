# Homepage Skeleton & Implementation Tasks
## Dr. Rachana Dubey - Pediatric Neurologist

---

# Part 1: Page Architecture

## Information Hierarchy

```
PRIORITY 1 (Above Fold)
├── Emotional hook + Identity
├── Core value proposition
└── Primary CTA

PRIORITY 2 (First Scroll)
├── Trust signals (quick)
├── What she treats
└── Differentiation

PRIORITY 3 (Engagement)
├── About/Story
├── Credentials (earned trust)
└── Publications/Research

PRIORITY 4 (Action)
├── Contact/Booking
├── Location
└── FAQs

PRIORITY 5 (Footer)
├── Navigation recap
├── Social proof
└── Legal/Contact
```

---

# Part 2: Section-by-Section Wireframe

## Section 1: Hero — "The Welcome"

### Purpose
Transform anxiety into hope within 3 seconds.

### Layout (Desktop)
```
┌─────────────────────────────────────────────────────────────────────┐
│  [Floating Nav]                                                      │
│  Logo        Home  |  About  |  Expertise  |  Research  |  Contact  │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ╭~~~~~~~~~~~~~~~~~~~~~~~~~~~~~╮    ╭─────────────────────────────╮ │
│  │                             │    │                             │ │
│  │  "Every brain tells         │    │   [Dr. Dubey Photo]         │ │
│  │   a story"                  │    │   - Natural, warm           │ │
│  │                             │    │   - With child patient      │ │
│  │  Pediatric Neurology with   │    │   - Or approachable solo    │ │
│  │  compassion, expertise,     │    │                             │ │
│  │  and hope.                  │    │   ~~~~ Neural decoration    │ │
│  │                             │    │                             │ │
│  │  [Book Consultation]        │    ╰─────────────────────────────╯ │
│  │  [Learn About Conditions →] │                                    │
│  │                             │                                    │
│  ╰~~~~~~~~~~~~~~~~~~~~~~~~~~~~~╯                                    │
│                                                                      │
│  ○ ○ ○ ○ ○ ○ ○  (floating particles - subtle)                       │
│                                                                      │
│        ↓ Scroll indicator (animated)                                 │
└─────────────────────────────────────────────────────────────────────┘
```

### Content Elements

**Headline Options:**
1. "Every brain tells a story" (poetic)
2. "Understanding your child's unique mind" (direct)
3. "Where neuroscience meets nurturing care" (balanced)

**Subheadline:**
"Specialized pediatric neurology care in Indore. 25+ years helping children thrive."

**CTAs:**
- Primary: "Book Consultation" → Opens modal/form
- Secondary: "Explore Conditions" → Scrolls to expertise

### Visual Notes
- Background: Warm gradient (pale aqua → soft cream)
- Neural flow lines: Subtle, animated behind content
- Photo: Circular or organic blob mask, not rectangular
- Particles: 5-8 floating circles, very slow drift

---

## Section 2: Trust Bar — "The Reassurance"

### Purpose
Instant credibility without overwhelming.

### Layout
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│    ╭────────╮   ╭────────╮   ╭────────╮   ╭────────╮   ╭────────╮   │
│    │  AIIMS │   │ 25+    │   │  20+   │   │ 4      │   │ ICNA   │   │
│    │  Delhi │   │ Years  │   │ Papers │   │ Countries │ │ Member │   │
│    ╰────────╯   ╰────────╯   ╰────────╯   ╰────────╯   ╰────────╯   │
│                                                                      │
│     DM Neuro     Experience   Research     Trained       Global      │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Content
| Metric | Value | Label |
|--------|-------|-------|
| Training | AIIMS Delhi | D.M. Pediatric Neurology |
| Experience | 25+ | Years of Practice |
| Research | 20+ | Published Papers |
| Global | 4 | Countries Trained |
| Network | ICNA | International Member |

### Visual Notes
- Background: Soft purple (10% opacity)
- Icons: Custom, matching illustration style
- Animation: Counter-up on scroll into view
- Subtle separator lines between items

---

## Section 3: Expertise — "The Constellation"

### Purpose
Show what she treats without medical intimidation.

### Layout Concept: Interactive Constellation
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│    "Conditions We Understand"                                        │
│     Every child's journey is unique                                  │
│                                                                      │
│                        ○ Autism                                      │
│                       ╱                                              │
│           ○ Epilepsy ──── ● CORE ──── ○ Movement                    │
│          ╱                 │           ╲ Disorders                   │
│    ○ Seizures             │            ○ Developmental              │
│                           │              Delays                      │
│              ○ Muscular ──┘                                          │
│                Dystrophy        ○ Headaches                          │
│                                                                      │
│    [Hover on any node to learn more]                                │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Alternative: Card Grid (Simpler)
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│   ╭──────────────╮  ╭──────────────╮  ╭──────────────╮              │
│   │    ⚡        │  │    🧠        │  │    💪        │              │
│   │   Epilepsy   │  │   Autism     │  │   Muscle     │              │
│   │   & Seizures │  │   Spectrum   │  │   Disorders  │              │
│   │              │  │              │  │              │              │
│   │   Learn →    │  │   Learn →    │  │   Learn →    │              │
│   ╰──────────────╯  ╰──────────────╯  ╰──────────────╯              │
│                                                                      │
│   ╭──────────────╮  ╭──────────────╮  ╭──────────────╮              │
│   │    🎯        │  │    🌊        │  │    🔬        │              │
│   │   Movement   │  │   Neuro-     │  │   Rare       │              │
│   │   Disorders  │  │   development│  │   Conditions │              │
│   │              │  │              │  │              │              │
│   │   Learn →    │  │   Learn →    │  │   Learn →    │              │
│   ╰──────────────╯  ╰──────────────╯  ╰──────────────╯              │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Conditions to Feature
1. **Epilepsy & Seizures** — "When the brain speaks unexpectedly"
2. **Autism Spectrum** — "Understanding unique minds"
3. **Muscular Disorders** — "Strength in different forms"
4. **Movement Disorders** — "When motion needs guidance"
5. **Developmental Delays** — "Every milestone matters"
6. **Rare Neurological Conditions** — "Even uncommon stories deserve care"

### Visual Notes
- Custom icons for each condition (soft, illustrative)
- Cards with subtle gradient backgrounds
- Hover: Card lifts, icon animates
- Link to detailed condition pages

---

## Section 4: Story — "The Journey"

### Purpose
Transform credentials into a human story.

### Layout
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│  ╭─────────────────────────────────────────────────────────────────╮│
│  │                                                                 ││
│  │  [Image: Dr. Dubey                "A journey of                 ││
│  │   - candid, warm                   understanding"               ││
│  │   - perhaps with                                                ││
│  │     medical books                 From the halls of AIIMS       ││
│  │     or in conference]             to the Cleveland Clinic,      ││
│  │                                   from Paris to Cambridge —     ││
│  │   ~~~~ neural                     my path has always led        ││
│  │        decorations                back to one place:            ││
│  │                                                                 ││
│  │                                   A child's bedside.            ││
│  │                                                                 ││
│  │                                   I believe every brain has     ││
│  │                                   potential waiting to bloom.   ││
│  │                                                                 ││
│  │                                   [Read Full Story →]           ││
│  │                                                                 ││
│  ╰─────────────────────────────────────────────────────────────────╯│
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Content Strategy
- **Don't list credentials** — Tell why they matter
- **Personal voice** — First person, warm
- **Global journey** — USA, France, UK, Italy training
- **Local commitment** — Serving Indore, MP

### Key Story Beats
1. Started in Bhopal (relatable, local)
2. AIIMS training (excellence)
3. International exposure (global standards)
4. Chose to serve in Indore (commitment)
5. 25+ years later (experience)
6. Still learning, still caring (humility)

---

## Section 5: Global Training — "The World Map"

### Purpose
Visualize international credentials uniquely.

### Layout
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│    "Trained Across Continents"                                       │
│                                                                      │
│         ○ Cambridge, UK                                              │
│          ╲   (2018 - EEG)          ○ Cleveland, USA                 │
│           ╲                        ╱  (2010 - Epilepsy)             │
│            ╲    ╭─────────╮      ╱                                  │
│             ╲   │ [World  │    ╱                                    │
│    Paris ○───── │  Map    │ ──○ San Servolo, Italy                  │
│    (2017)      │ Visual  │    (2018 - Pediatric)                   │
│                 ╰─────────╯                                          │
│                      │                                               │
│                      ○ AIIMS, New Delhi                              │
│                        (2015 - DM Neurology)                         │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Locations to Highlight
| Location | Year | Training |
|----------|------|----------|
| AIIMS, New Delhi | 2015 | D.M. Pediatric Neurology |
| Cleveland Clinic, USA | 2010 | Epilepsy & Electrophysiology |
| Institut de Myologie, Paris | 2017 | Muscle Disorders |
| Cambridge, UK | 2018 | Neonatal EEG |
| San Servolo, Italy | 2018 | Pediatric Epilepsy |

### Visual Notes
- Stylized map (not Google Maps)
- Pulsing dots on locations
- Connecting lines (neural pathway aesthetic)
- Hover reveals training details
- Mobile: Vertical timeline version

---

## Section 6: Research — "The Publications"

### Purpose
Establish academic authority without intimidation.

### Layout
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│    "Contributing to Global Knowledge"                                │
│     Research that shapes how we care                                 │
│                                                                      │
│    ╭─────────────────────────────────────────────────────────────╮  │
│    │  FEATURED IN                                                 │  │
│    │                                                              │  │
│    │  [Lancet Logo]  [Brain Journal]  [Indian Pediatrics]        │  │
│    │                                                              │  │
│    ╰─────────────────────────────────────────────────────────────╯  │
│                                                                      │
│    RECENT PUBLICATIONS                                               │
│                                                                      │
│    ╭──────────────────────────────────────────────────────────────╮ │
│    │  📄 Clinical and molecular spectrum associated with          │ │
│    │     Polymerase-γ related disorders                           │ │
│    │     Journal of Child Neurology, 2022                         │ │
│    ╰──────────────────────────────────────────────────────────────╯ │
│                                                                      │
│    ╭──────────────────────────────────────────────────────────────╮ │
│    │  📄 Consensus Statement on Diagnosis and Management          │ │
│    │     of Febrile Seizures                                      │ │
│    │     Indian Pediatrics, 2021                                  │ │
│    ╰──────────────────────────────────────────────────────────────╯ │
│                                                                      │
│    [View All 20+ Publications →]                                     │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Featured Journals
- The Lancet (most prestigious)
- Brain (top neurology journal)
- Indian Pediatrics
- Frontiers in Public Health

### Visual Notes
- Journal logos in grayscale, color on hover
- Publication cards with subtle left border (magenta)
- Expandable for abstract/summary
- Link to full publication

---

## Section 7: Testimonials — "The Voices"

### Purpose
Social proof through parent stories.

### Layout
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│    "Stories from Families"                                           │
│                                                                      │
│    ╭───────────────────────────────────────────────────────────────╮│
│    │                                                               ││
│    │    "Dr. Dubey didn't just treat my son's epilepsy.           ││
│    │     She treated our family's fear. After two years           ││
│    │     of uncertainty, we finally found hope."                  ││
│    │                                                               ││
│    │              — Priya M., Mother of Arjun (8)                 ││
│    │                                                               ││
│    │    [○ ○ ● ○ ○]  (carousel indicators)                        ││
│    │                                                               ││
│    ╰───────────────────────────────────────────────────────────────╯│
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Testimonial Guidelines
- First names only (privacy)
- Include child's age
- Focus on emotional journey
- Keep concise (2-3 sentences)
- Rotating carousel (auto + manual)

### Visual Notes
- Large quotation marks (decorative, in magenta)
- Soft background (pale aqua)
- Photo optional (silhouette if not)
- Subtle fade transition between testimonials

---

## Section 8: Contact — "The Connection"

### Purpose
Make reaching out feel welcoming, not clinical.

### Layout
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│    ╭────────────────────────╮  ╭───────────────────────────────────╮│
│    │                        │  │                                   ││
│    │  "Let's Start the      │  │   BOOK A CONSULTATION            ││
│    │   Conversation"        │  │                                   ││
│    │                        │  │   Your Name                       ││
│    │  Every journey begins  │  │   ╭─────────────────────────────╮ ││
│    │  with a single step.   │  │   │                             │ ││
│    │                        │  │   ╰─────────────────────────────╯ ││
│    │  📍 Medanta Hospital   │  │                                   ││
│    │     Indore, MP         │  │   Phone Number                    ││
│    │                        │  │   ╭─────────────────────────────╮ ││
│    │  📞 +91 8839708182     │  │   │                             │ ││
│    │                        │  │   ╰─────────────────────────────╯ ││
│    │  📧 rachnadube@        │  │                                   ││
│    │     gmail.com          │  │   Briefly describe your concern   ││
│    │                        │  │   ╭─────────────────────────────╮ ││
│    │  🕐 Mon-Sat            │  │   │                             │ ││
│    │     10am - 6pm         │  │   │                             │ ││
│    │                        │  │   ╰─────────────────────────────╯ ││
│    │                        │  │                                   ││
│    │                        │  │   [Request Appointment]           ││
│    │                        │  │                                   ││
│    ╰────────────────────────╯  ╰───────────────────────────────────╯│
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Form Fields
1. Parent/Guardian Name (required)
2. Phone Number (required)
3. Child's Age
4. Brief Description (optional)
5. Preferred Contact Time

### Visual Notes
- Two-column on desktop, stacked on mobile
- Map embed optional (stylized, not default Google)
- WhatsApp quick link (prominent in India)
- Form has gentle validation, not harsh red errors

---

## Section 9: Footer — "The Foundation"

### Layout
```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│  [Logo]                                                              │
│  Dr. Rachana Dubey                                                   │
│  Pediatric Neurologist                                               │
│                                                                      │
│  ─────────────────────────────────────────────────────────────────  │
│                                                                      │
│  QUICK LINKS        EXPERTISE           CONNECT                      │
│  Home               Epilepsy            📍 Medanta, Indore           │
│  About              Autism              📞 +91 8839708182            │
│  Research           Movement            📧 rachnadube@gmail.com      │
│  Contact            Developmental                                    │
│                                                                      │
│  ─────────────────────────────────────────────────────────────────  │
│                                                                      │
│  © 2024 Dr. Rachana Dubey  |  Privacy  |  Terms                     │
│                                                                      │
│  ~~~~ subtle neural decoration ~~~~                                  │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# Part 3: Mobile Adaptations

## Key Mobile Changes

```
DESKTOP                          MOBILE
─────────────────────────────────────────────────
Two columns            →         Single column
Horizontal nav         →         Hamburger menu
Large hero image       →         Smaller, above text
Constellation map      →         Vertical card list
Side-by-side contact   →         Stacked sections
Floating decorations   →         Reduced/simplified
```

## Mobile Hero
```
┌─────────────────────┐
│      [Menu ☰]       │
├─────────────────────┤
│                     │
│   ╭───────────╮     │
│   │  Photo    │     │
│   ╰───────────╯     │
│                     │
│  "Every brain       │
│   tells a story"    │
│                     │
│  Pediatric          │
│  Neurology with     │
│  compassion.        │
│                     │
│  [Book Consultation]│
│                     │
│  [Learn More ↓]     │
│                     │
└─────────────────────┘
```

---

# Part 4: Implementation Tasks

## Phase 1: Foundation

### Task 1.1: Project Setup
- [ ] Initialize project (Next.js/Astro recommended)
- [ ] Configure Tailwind with custom design tokens
- [ ] Set up fonts (Fraunces + Plus Jakarta Sans)
- [ ] Create color CSS variables
- [ ] Set up component structure

### Task 1.2: Asset Preparation
- [ ] Commission/create neural illustration SVGs
- [ ] Prepare Dr. Dubey photos (warm, natural)
- [ ] Create custom icons for conditions
- [ ] Design logo/wordmark
- [ ] Prepare journal logos (if using)

### Task 1.3: Animation System
- [ ] Set up Framer Motion or GSAP
- [ ] Create reusable animation variants
- [ ] Build scroll-triggered reveal system
- [ ] Create floating particle component
- [ ] Build neural line SVG animations

---

## Phase 2: Core Components

### Task 2.1: Navigation
- [ ] Build floating nav component
- [ ] Create mobile hamburger menu
- [ ] Implement scroll behavior (shrink/show)
- [ ] Add active state indicators
- [ ] Test accessibility (keyboard nav)

### Task 2.2: Hero Section
- [ ] Build responsive hero layout
- [ ] Implement background gradient
- [ ] Add neural decoration SVGs
- [ ] Create floating particles
- [ ] Add scroll indicator animation

### Task 2.3: Card Components
- [ ] Build "Petal Card" base component
- [ ] Create expertise card variant
- [ ] Create publication card variant
- [ ] Create testimonial card variant
- [ ] Add hover animations

### Task 2.4: Form Components
- [ ] Build custom input fields
- [ ] Create textarea component
- [ ] Build button variants
- [ ] Add form validation (gentle)
- [ ] Create success state

---

## Phase 3: Page Sections

### Task 3.1: Trust Bar
- [ ] Build trust metric component
- [ ] Add counter-up animation
- [ ] Create responsive layout
- [ ] Add subtle background

### Task 3.2: Expertise Section
- [ ] Build expertise grid/constellation
- [ ] Create condition cards
- [ ] Add hover interactions
- [ ] Link to detail pages (future)

### Task 3.3: Story Section
- [ ] Build asymmetric layout
- [ ] Add image with organic mask
- [ ] Create pull-quote styling
- [ ] Add read more functionality

### Task 3.4: Global Training
- [ ] Create stylized map component
- [ ] Add location markers
- [ ] Build connecting lines
- [ ] Add hover tooltips
- [ ] Create mobile timeline version

### Task 3.5: Research Section
- [ ] Build journal logo bar
- [ ] Create publication cards
- [ ] Add expandable functionality
- [ ] Link to external papers

### Task 3.6: Testimonials
- [ ] Build testimonial carousel
- [ ] Add auto-rotation
- [ ] Create navigation dots
- [ ] Add swipe support (mobile)

### Task 3.7: Contact Section
- [ ] Build two-column layout
- [ ] Create contact info cards
- [ ] Implement booking form
- [ ] Add form submission logic
- [ ] Create confirmation message

### Task 3.8: Footer
- [ ] Build footer layout
- [ ] Add link columns
- [ ] Create bottom bar
- [ ] Add decorative elements

---

## Phase 4: Polish & Launch

### Task 4.1: Performance
- [ ] Optimize images (WebP, lazy load)
- [ ] Minimize CSS/JS bundles
- [ ] Add loading states
- [ ] Test Core Web Vitals
- [ ] Implement caching

### Task 4.2: Accessibility
- [ ] Run WAVE/axe audit
- [ ] Fix contrast issues
- [ ] Add skip links
- [ ] Test keyboard navigation
- [ ] Add reduced motion support

### Task 4.3: SEO
- [ ] Add meta tags
- [ ] Create Open Graph images
- [ ] Add structured data (Doctor schema)
- [ ] Create sitemap
- [ ] Set up analytics

### Task 4.4: Testing
- [ ] Cross-browser testing
- [ ] Mobile device testing
- [ ] Form submission testing
- [ ] Animation performance testing
- [ ] User testing with parents

### Task 4.5: Launch
- [ ] Set up hosting (Vercel/Netlify)
- [ ] Configure domain
- [ ] Set up SSL
- [ ] Create redirects if needed
- [ ] Launch and monitor

---

# Part 5: Content Requirements

## Text Content Needed

| Section | Content | Owner | Status |
|---------|---------|-------|--------|
| Hero headline | 1 line | Designer | ⬜ |
| Hero subheadline | 2 lines | Designer | ⬜ |
| Trust metrics | 5 items | From CV | ✅ |
| Condition descriptions | 6 x 50 words | Writer | ⬜ |
| About story | 200-300 words | Dr. Dubey | ⬜ |
| Training locations | 5 items | From CV | ✅ |
| Featured publications | 3-5 items | From CV | ✅ |
| Testimonials | 3-5 stories | From patients | ⬜ |
| Contact info | Address, phone, email | From CV | ✅ |

## Visual Assets Needed

| Asset | Specification | Status |
|-------|---------------|--------|
| Dr. Dubey portrait | High-res, warm lighting | ⬜ |
| Dr. Dubey with patient | Candid, consented | ⬜ |
| Neural illustrations | SVG, 5-6 variations | ⬜ |
| Condition icons | SVG, 6 icons | ⬜ |
| Logo/Wordmark | SVG, multiple sizes | ⬜ |
| Background patterns | SVG, tileable | ⬜ |

---

# Part 6: Technical Specifications

## Recommended Stack

```
Framework:     Next.js 14+ (App Router)
Styling:       Tailwind CSS + CSS Variables
Animation:     Framer Motion
Icons:         Custom SVG + Lucide (fallback)
Forms:         React Hook Form + Zod
Hosting:       Vercel
CMS:           Sanity (optional, for blog)
Analytics:     Plausible (privacy-focused)
```

## Performance Targets

| Metric | Target |
|--------|--------|
| Lighthouse Performance | > 90 |
| First Contentful Paint | < 1.5s |
| Largest Contentful Paint | < 2.5s |
| Cumulative Layout Shift | < 0.1 |
| Time to Interactive | < 3s |

## Browser Support

| Browser | Version |
|---------|---------|
| Chrome | Last 2 |
| Firefox | Last 2 |
| Safari | Last 2 |
| Edge | Last 2 |
| Mobile Safari | iOS 14+ |
| Chrome Android | Last 2 |

---

# Part 7: Success Metrics

## Key Performance Indicators

1. **Engagement**
   - Time on page > 2 minutes
   - Scroll depth > 75%
   - Low bounce rate < 40%

2. **Conversion**
   - Form submissions
   - Phone call clicks
   - WhatsApp clicks

3. **Trust**
   - Return visitors
   - Pages per session > 2

4. **Technical**
   - Core Web Vitals pass
   - Zero accessibility errors
   - Mobile usability score 100

---

## Resources & Inspiration

- [Healthcare UX Design Best Practices](https://www.eleken.co/blog-posts/user-interface-design-for-healthcare-applications)
- [Patient Journey Mapping](https://thestory.is/en/journal/patient-journey/)
- [Emotional Design in Healthcare](https://medium.com/design-bootcamp/human-centered-healthcare-the-evolution-of-emotional-design-d15c1fc96de0)
- [Pediatric Website Best Practices](https://wgcontent.com/blog/the-best-pediatric-websites-feature-these-elements/)
- [Healthcare Web Design Trends 2026](https://www.vezadigital.com/post/healthcare-web-design-trends)

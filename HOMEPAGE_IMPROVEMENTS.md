# Homepage Improvements & Authenticity Guide
## Dr. Rachana Dubey - Pediatric Neurologist Website

---

# Table of Contents

1. [Problem Analysis](#problem-analysis)
2. [Photo Placement Strategy](#photo-placement-strategy)
3. [New Section: Instagram-Style Gallery](#new-section-instagram-style-gallery)
4. [Component-wise Changes](#component-wise-changes)
5. [Photo Organization Structure](#photo-organization-structure)
6. [AI Image Generation Prompts](#ai-image-generation-prompts)
7. [Quick Implementation Checklist](#quick-implementation-checklist)

---

# Problem Analysis

## Why the Site Looks AI-Generated

### Issue 1: Placeholder Overload
| Location | Current State | Problem |
|----------|---------------|---------|
| Hero Section | SVG silhouette placeholder | No real photo of Dr. Dubey |
| Story Section | SVG person outline | Generic, impersonal |
| Testimonials | Circle avatars | Feels fabricated |
| Global Training | Stylized map only | No actual photos from institutions |

### Issue 2: Generic Copy
- Testimonials sound written, not collected
- No specific patient outcomes mentioned
- Phrases like "Every brain tells a story" feel templated

### Issue 3: No Authentic Proof
- Zero photos of awards/recognition
- No conference presentation images
- No photos with dignitaries/senior doctors
- No visual proof of international training

### Issue 4: Over-Designed, Under-Personalized
- Beautiful animations but no humanity
- Polished UI that could belong to any doctor
- No unique visual identity tied to Dr. Dubey's actual journey

---

# Photo Placement Strategy

## Section-by-Section Photo Requirements

### 1. Hero Section (CRITICAL - First Impression)

**Current:** SVG placeholder with generic person icon

**Required Photo:**
- Warm, professional portrait of Dr. Dubey
- Natural lighting (golden hour feel)
- NOT in clinical white coat (or soft pastel coat)
- Ideally: gentle smile, approachable expression
- Background: soft, blurred (office or outdoor)

**Specifications:**
- Minimum resolution: 800x1000px
- Aspect ratio: 4:5 (portrait)
- Format: WebP or optimized JPG

---

### 2. Trust Bar (Enhancement)

**Current:** Icons with metrics only

**Add Below:** A horizontal scrolling "Recognition" strip

**Photos Needed:**
- 4-6 award ceremony photos
- Conference speaking photos
- Photos with notable figures

**Display Style:** Horizontal scroll with captions

---

### 3. Story Section (About)

**Current:** Large SVG placeholder

**Required Photos:**
- **Main Photo:** Candid shot - Dr. Dubey reading, in consultation, or at conference
- **Supporting Gallery (3-4 photos):**
  - Early career photo (if available)
  - At AIIMS Delhi
  - At international conference
  - Recent professional photo

**Specifications:**
- Main: 400x500px minimum
- Gallery: 200x200px thumbnails

---

### 4. Global Training Section

**Current:** Stylized map with dots

**Enhancement:** Add actual photos from each location

| Location | Photo Needed |
|----------|--------------|
| Cleveland Clinic, USA | Dr. Dubey at/near the facility |
| Institut de Myologie, Paris | Training/conference photo from Paris |
| Cambridge, UK | Photo from the fellowship |
| San Servolo, Italy | ILAE fellowship photo |
| AIIMS, New Delhi | Graduation or training photo |

**Display:** Photo appears on hover/click of map location

---

### 5. Research Section

**Current:** Text-based publication list

**Add:** Photo carousel of conference presentations

**Photos Needed:**
- Presenting at ICNC Brazil 2014
- Amsterdam 2016 presentation
- Barcelona 2017 congress
- Cape Town 2024 (if available)

---

### 6. Testimonials Section

**Current:** Generic avatar circles

**Options:**
- Option A: Request family photos (with consent)
- Option B: Use stylized initials instead of fake avatars
- Option C: Add small photos of Dr. Dubey with families (consented)

---

### 7. Contact Section

**Add:** Small photo of Medanta Hospital Indore or Dr. Dubey's consultation room

---

### 8. Footer

**Add:** Small circular photo of Dr. Dubey (40x40px)

---

# New Section: Instagram-Style Gallery

## "Moments of Care" / "In the Spotlight" Gallery

### Concept
A masonry or grid-style gallery (like Instagram) showcasing Dr. Dubey's professional journey through authentic photos.

### Placement Options
1. **After Story Section** - Shows journey visually
2. **Before Contact Section** - Final trust-builder
3. **As Separate Page** - Linked from homepage

### Gallery Categories (Tabs/Filters)

```
[All] [Awards] [Conferences] [Global Training] [With Dignitaries] [Media]
```

### Layout Design

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                      │
│   "Moments of Care"                                                  │
│    A journey spanning 25+ years and 4 continents                    │
│                                                                      │
│   [All] [Awards] [Conferences] [Training] [Media]                   │
│                                                                      │
│   ┌─────────┬─────────┬─────────┬─────────┐                        │
│   │         │         │         │         │                        │
│   │  Photo  │  Photo  │  Photo  │  Photo  │                        │
│   │   1     │   2     │   3     │   4     │                        │
│   │         │         │         │         │                        │
│   ├─────────┼─────────┴─────────┼─────────┤                        │
│   │         │                   │         │                        │
│   │  Photo  │      Photo        │  Photo  │                        │
│   │   5     │       6           │   7     │                        │
│   │         │     (larger)      │         │                        │
│   ├─────────┼─────────┬─────────┼─────────┤                        │
│   │         │         │         │         │                        │
│   │  Photo  │  Photo  │  Photo  │  Photo  │                        │
│   │   8     │   9     │   10    │   11    │                        │
│   └─────────┴─────────┴─────────┴─────────┘                        │
│                                                                      │
│                    [View All Photos →]                               │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Photo Data Structure

Each gallery item should have:
```
{
  id: 1,
  src: "/images/gallery/award-icnc-2024.jpg",
  thumbnail: "/images/gallery/thumbs/award-icnc-2024.jpg",
  category: "awards",
  title: "ICNC 2024 Speaker",
  location: "Cape Town, South Africa",
  year: "2024",
  description: "Selected speaker on sleep disorders in autoimmune neurological disorders"
}
```

### Interaction Design

- **Hover:** Slight zoom + overlay with title
- **Click:** Opens lightbox with full image + description
- **Mobile:** Tap to expand, swipe to navigate

### Photo Categories & Quantities

| Category | Minimum Photos | Ideal |
|----------|---------------|-------|
| Awards & Recognition | 4 | 8-10 |
| Conference Presentations | 4 | 6-8 |
| International Training | 5 | 5 (one per location) |
| With Dignitaries/Seniors | 3 | 5-6 |
| Media/Press | 2 | 3-4 |
| **TOTAL** | **18** | **27-33** |

---

# Component-wise Changes

## 1. Hero.svelte Changes

**File:** `src/lib/components/Hero.svelte`

**Current (Lines 31-45):**
```svelte
<div class="hero-image">
  <div class="image-blob">
    <div class="image-placeholder">
      <!-- SVG placeholder -->
    </div>
  </div>
</div>
```

**Change to:**
```svelte
<div class="hero-image">
  <div class="image-blob">
    <img
      src="/images/hero/dr-dubey-portrait.webp"
      alt="Dr. Rachana Dubey - Pediatric Neurologist"
      class="hero-photo"
      loading="eager"
    />
  </div>
</div>
```

---

## 2. Story.svelte Changes

**File:** `src/lib/components/Story.svelte`

**Replace SVG placeholder with:**
```svelte
<div class="image-frame">
  <img
    src="/images/about/dr-dubey-candid.webp"
    alt="Dr. Rachana Dubey"
    class="story-photo"
  />
</div>

<!-- Add mini gallery below -->
<div class="story-gallery">
  <img src="/images/about/thumb-1.webp" alt="At AIIMS Delhi" />
  <img src="/images/about/thumb-2.webp" alt="Conference presentation" />
  <img src="/images/about/thumb-3.webp" alt="With colleagues" />
</div>
```

---

## 3. GlobalTraining.svelte Enhancement

**Add photo tooltips on location hover:**
```svelte
{#if activeLocation === loc.id}
  <div class="location-photo-popup">
    <img src="/images/training/{loc.id}.webp" alt="{loc.name}" />
    <span class="photo-caption">{loc.year} - {loc.training}</span>
  </div>
{/if}
```

---

## 4. New Component: Gallery.svelte

**Create:** `src/lib/components/Gallery.svelte`

Features:
- Masonry grid layout
- Category filter tabs
- Lightbox on click
- Responsive (4 cols → 2 cols → 1 col)
- Lazy loading images

---

## 5. TrustBar.svelte Enhancement

**Add recognition strip below metrics:**
```svelte
<div class="recognition-strip">
  <h3>Recognition & Achievements</h3>
  <div class="recognition-scroll">
    {#each recognitionPhotos as photo}
      <div class="recognition-item">
        <img src={photo.src} alt={photo.title} />
        <span class="recognition-caption">{photo.title}</span>
      </div>
    {/each}
  </div>
</div>
```

---

# Photo Organization Structure

## Recommended Folder Structure

```
/public/images/
│
├── /hero/
│   └── dr-dubey-portrait.webp          (Main hero image)
│
├── /about/
│   ├── dr-dubey-candid.webp            (Story section main)
│   ├── thumb-1.webp                     (Mini gallery)
│   ├── thumb-2.webp
│   └── thumb-3.webp
│
├── /training/
│   ├── cleveland.webp                   (USA training)
│   ├── paris.webp                       (France training)
│   ├── cambridge.webp                   (UK training)
│   ├── italy.webp                       (San Servolo)
│   └── delhi.webp                       (AIIMS)
│
├── /awards/
│   ├── award-1.webp
│   ├── award-2.webp
│   ├── award-3.webp
│   └── ...
│
├── /conferences/
│   ├── icnc-brazil-2014.webp
│   ├── amsterdam-2016.webp
│   ├── barcelona-2017.webp
│   ├── cape-town-2024.webp
│   └── ...
│
├── /dignitaries/
│   ├── meeting-1.webp
│   ├── meeting-2.webp
│   └── ...
│
├── /gallery/
│   ├── (all gallery images)
│   └── /thumbs/
│       └── (thumbnail versions)
│
└── /misc/
    ├── medanta-hospital.webp
    └── clinic-room.webp
```

## Image Specifications

| Usage | Dimensions | Format | Quality |
|-------|-----------|--------|---------|
| Hero | 800x1000px | WebP | 85% |
| Story Main | 640x800px | WebP | 85% |
| Gallery Full | 1200x900px | WebP | 80% |
| Gallery Thumb | 400x300px | WebP | 75% |
| Training Photos | 600x400px | WebP | 80% |
| Recognition Strip | 300x200px | WebP | 75% |

---

# AI Image Generation Prompts (Gemini Nano Banana Pro Format)

## About These Prompts

These prompts are formatted for **Google Gemini Nano Banana Pro** - the latest image generation model.

**Key differences from Midjourney:**
- Uses natural language (no --ar, --v6 parameters)
- Describe scenes narratively, don't list keywords
- Include photography terms for realistic images
- Supports conversational editing (modify outputs by asking)

**Prompt Structure:**
```
[Subject] + [Action/Pose] + [Setting/Environment] + [Lighting] + [Style/Technical Details]
```

**Sources:**
- [Google Blog: Nano Banana Pro Tips](https://blog.google/products/gemini/prompting-tips-nano-banana-pro/)
- [Firebase AI Logic: Generate Images with Gemini](https://firebase.google.com/docs/ai-logic/generate-images-gemini)

---

## ASPECT RATIO GUIDE

Request specific ratios by adding at the end of your prompt:

| Section | Ratio | Add to Prompt |
|---------|-------|---------------|
| Hero Portrait | 4:5 | "Generate in portrait 4:5 aspect ratio" |
| Gallery Grid | 1:1 | "Generate in square 1:1 format" |
| Conference/Wide | 16:9 | "Generate in landscape 16:9 format" |
| Story Section | 3:4 | "Generate in portrait 3:4 aspect ratio" |

---

## FACE VARIATION TIPS (When Using Same Reference Selfie)

To avoid all generated images looking identical, add these **variation phrases**:

### Different Angles:
- "captured from a slight three-quarter angle"
- "photographed from the side as she gestures"
- "seen in profile while speaking"
- "face partially turned toward the screen"

### Different Expressions:
- "with a focused, thoughtful expression"
- "smiling warmly while presenting"
- "with a confident, animated speaking demeanor"
- "engaged in discussion, listening intently"

### Different Gaze Directions:
- "looking toward the presentation screen"
- "making eye contact with the audience"
- "glancing at her notes"
- "eyes focused on the data display"

### Natural Action Shots (Less Direct Face):
- "photographed mid-gesture, hands in frame"
- "captured while pointing at the screen"
- "seen from a slight angle addressing the crowd"

### Example Modified Prompt:
```
Use attached face as reference. Create a realistic photograph of an Indian
female doctor presenting at a neurology conference. She is captured from
a three-quarter angle, looking toward the presentation screen while
gesturing at the data. Soft stage lighting creates natural shadows on
her face. Conference hall with modern architecture. Shot at 35mm.
Generate in landscape 16:9 format.
```

---

## REALISTIC IMAGE PROMPTS

### PROMPT 1: Dr. Dubey Professional Portrait (Hero Enhancement)

**Use for:** If you need to enhance/modify the hero photo

```
Use attached face as reference. Create a professional portrait photograph of an Indian female doctor in her early 50s with long black hair. She has a warm, approachable smile with a gentle, confident expression. She is wearing a navy blue medical scrub top. The setting is a modern medical office with wooden bookshelves filled with medical textbooks visible in soft bokeh background. Natural golden hour sunlight streams through a window from the right side, creating warm rim lighting on her hair. Several green indoor plants add warmth to the scene. Shot at 85mm, f/2.8, shallow depth of field. The image conveys trust, expertise, and compassion. Photorealistic, high resolution, professional healthcare photography style. Generate in portrait 4:5 aspect ratio.
```

---

### PROMPT 2: Award Ceremony Photo

**Use for:** Recognition gallery, trust indicators

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor receiving a prestigious medical award on stage at an international conference. She is captured from a slight angle, looking toward the presenter with a gracious, humble smile as she accepts the certificate. She wears formal professional attire - a dark blazer over elegant clothing. The background shows a conference stage with soft blue and purple stage lighting. Other distinguished doctors and medical professionals are visible applauding in soft focus. A podium with a medical conference logo is partially visible. Professional event photography lighting with fill flash balancing the ambient stage lights. Shot at 70mm, f/4. The atmosphere is celebratory and prestigious. Generate in landscape 3:2 aspect ratio.
```

---

### PROMPT 3: Conference Speaking Photo

**Use for:** Research section, credibility display

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor giving a medical presentation at an international neurology conference. She is captured in a three-quarter angle, looking toward the presentation screen while gesturing at brain scan images displayed on a large screen. Her expression is focused and animated as she explains the data. The audience of fellow doctors is visible in soft focus in the foreground. Professional conference lighting illuminates the scene with soft shadows. She wears a formal navy blazer over professional attire with a conference badge. The conference hall has modern architecture. Shot at 35mm, f/4. Professional event photography, photorealistic. Generate in landscape 16:9 aspect ratio.
```

---

### PROMPT 4: Meeting with Medical Dignitaries

**Use for:** Gallery section, credibility

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor in a formal meeting with senior medical professionals and healthcare officials. She is captured from a slight side angle, engaged in thoughtful discussion with a focused expression, listening intently to a colleague. The setting is an elegant conference room with a polished wooden table. Papers and medical documents are visible on the table. Other distinguished doctors in formal attire are seated around the table. Soft natural light comes from large windows creating gentle shadows. The atmosphere conveys high-level medical consultation and professional respect. Shot at 24mm, f/5.6. Corporate photography style, warm color temperature. Generate in landscape 16:9 aspect ratio.
```

---

### PROMPT 5: International Training Photo - Cleveland Clinic USA

**Use for:** Global Training section

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor standing in front of the Cleveland Clinic building entrance in Ohio, USA. She is photographed from a slight three-quarter angle, looking toward the building with a proud, accomplished expression. She wears a white medical coat with a visitor badge. The iconic Cleveland Clinic sign and modern hospital architecture are clearly visible behind her. Bright, clear day with blue sky. American flags visible near the entrance. The image captures international medical training achievement. Shot at 50mm, f/4, natural daylight, documentary photography style. Generate in portrait 4:5 aspect ratio.
```

---

### PROMPT 6: Training Photo - Paris France

**Use for:** Global Training section

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor at the Institut de Myologie research center in Paris, France. She is captured in profile view, examining medical imaging documents with a thoughtful, analytical expression. The setting is a modern medical research laboratory with advanced equipment. She wears professional medical attire - a white lab coat. Through a window, subtle hints of classic Parisian architecture are visible. Soft fluorescent laboratory lighting mixed with natural daylight. Shot at 35mm, f/3.5. Medical documentary photography style. Generate in landscape 3:2 aspect ratio.
```

---

### PROMPT 7: Training Photo - Cambridge UK

**Use for:** Global Training section

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor at a prestigious medical institution in Cambridge, UK. She is captured walking through a historic university corridor, looking ahead with a confident, purposeful expression. Classic British architecture visible - stone walls, arched windows, traditional academic corridors. She wears smart professional attire with a fellowship badge. Soft overcast English daylight creates even, flattering illumination through tall windows. The setting blends historic academic grandeur with modern medical facilities. Shot at 40mm, f/4. Documentary photography style. Generate in portrait 4:5 aspect ratio.
```

---

### PROMPT 8: Training Photo - Italy San Servolo

**Use for:** Global Training section

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor at a medical training program in Venice, Italy. She is captured in conversation with international colleagues, her face turned slightly toward them with an engaged, friendly expression. The setting shows the historic San Servolo island conference center with Italian architecture visible. Group of 3-4 international medical colleagues visible, all wearing conference badges. Warm Mediterranean golden hour sunlight. Background hints at Venetian architecture or waterfront. Shot at 35mm, f/4. Documentary style. Generate in landscape 3:2 aspect ratio.
```

---

### PROMPT 9: AIIMS Delhi Training Photo

**Use for:** Global Training section, Trust Bar

```
Use attached face as reference. Create a realistic photograph of an Indian female doctor at the All India Institute of Medical Sciences (AIIMS) in New Delhi. She is photographed from a three-quarter angle, looking toward the iconic AIIMS building with a reflective, proud expression. She wears the distinctive AIIMS white coat. The recognizable institutional architecture is prominent in the background - main hospital building or academic block. Bright Indian morning sunlight creates warm, defined lighting. Other medical professionals visible in soft focus background. Shot at 50mm, f/5.6. Documentary photography style. Generate in portrait 4:5 aspect ratio.
```

---

### PROMPT 10: Consultation with Child Patient

**Use for:** Story section, humanizing element

```
Use attached face as reference. Create a warm, realistic photograph of an Indian female pediatric neurologist having a gentle consultation with a young child patient (around 6-8 years old). The doctor is captured at eye level with the child, her face showing a warm, caring smile as she listens attentively. She is slightly turned toward the child, creating a natural three-quarter face angle. The setting is a child-friendly medical office with soft lighting and calming pastel decor. The child looks comfortable and engaged. A parent figure partially visible in soft focus background, looking reassured. Natural window light creates warm atmosphere. Shot at 85mm, f/2.8 for soft, intimate feel. Healthcare photography style. Generate in landscape 3:2 aspect ratio.
```

---

### PROMPT 11: Doctor in Modern Clinic Setting

**Use for:** Contact section, About section

```
Use attached face as reference. Create a professional photograph of an Indian female doctor sitting at her desk in a modern, welcoming medical office. She is captured from a slight side angle, looking thoughtfully at medical documents with a focused, professional expression - not looking at camera. The office features warm wooden furniture, medical books on shelves, green plants, and soft natural window light. Medical certificates visible on walls. The atmosphere is professional yet warm and approachable. Shot at 35mm, f/4, capturing both subject and inviting office environment. Professional corporate healthcare photography. Generate in landscape 16:9 aspect ratio.
```

---

### PROMPT 12: Group Photo at Medical Conference

**Use for:** Gallery, credibility

```
Use attached face as reference. Create a realistic group photograph of international medical professionals at a neurology conference. An Indian female doctor stands among a diverse group of 6-8 distinguished doctors from various countries, positioned slightly off-center with a warm, collegial smile. All wear formal conference attire with name badges. They stand in front of a conference banner showing a medical association logo (like ILAE or ICNA). Professional conference photography lighting with soft fill flash. Natural, genuine expressions showing professional camaraderie. Shot at 24mm, f/8 to keep entire group in focus. International medical collaboration setting. Generate in landscape 16:9 aspect ratio.
```

---

## DECORATIVE/ILLUSTRATIVE PROMPTS

### PROMPT 13: Neural Garden Background Illustration

**Use for:** Hero section background, section dividers

```
Create a soft, dreamy watercolor illustration of neural pathways reimagined as a growing garden. The neurons appear as flowering vines with dendrites branching like delicate plant tendrils. Synapses are depicted as small blooming flowers in soft pastel purple and cyan colors. The lines flow organically across a clean white background. The style is minimalist and medical yet hopeful - suitable for a healthcare website background. The overall feeling is of growth, connection, and healing. Soft watercolor texture with flowing organic lines. No text or words in the image.
```

---

### PROMPT 14: Abstract Brain-Tree Illustration

**Use for:** Hero decoration, About section accent

```
Create an elegant, minimalist line art illustration showing a child's brain that seamlessly transforms into a blooming tree. Use a single continuous flowing line style. The colors transition from soft purple at the brain section to magenta and green as it becomes tree branches with leaves. The background is pure white. The illustration symbolizes growth, hope, and the potential of every child's mind. This is for a pediatric neurology healthcare website - make it feel hopeful, not clinical. Minimalist style with clean lines. No text.
```

---

### PROMPT 15: World Map with Training Locations

**Use for:** Global Training section

```
Create a stylized, artistic world map illustration with a soft watercolor aesthetic. The continents should have organic, flowing shapes in pale aqua and soft lavender tones. Mark these specific locations with gentle glowing dots connected by subtle flowing lines: Cleveland (USA), Paris (France), Cambridge (UK), Venice (Italy), and New Delhi (India). The connection lines should look like neural pathways - soft and organic, not rigid. The background is clean white. The overall style is elegant, minimal, and suitable for a medical professional's website showing international training locations.
```

---

### PROMPT 16: Parent and Child Hands Illustration

**Use for:** Contact section decoration

```
Create a warm, emotional watercolor illustration of a parent's hand and a small child's hand gently reaching toward each other. Between their hands is a soft, warm glowing light suggesting hope and healing. Use soft purple and pink tones with a white background. The style is minimalist and heartfelt - suggesting the theme of care, connection, and the journey of healing together. This is for a pediatric healthcare website. The illustration should evoke trust and comfort. No text in the image.
```

---

### PROMPT 17: Medical Achievement Badge

**Use for:** Credentials section, trust indicators

```
Create an elegant medical achievement badge or emblem design. The badge is circular with a subtle laurel wreath border. Colors are gold and deep purple, giving it a prestigious feel. The design has minimal ornate details - professional and clean, suitable for a medical website. The badge should look like a certification or recognition emblem. Transparent or white background. No specific text - just the decorative emblem design.
```

---

### PROMPT 18: Flowing Brain Wave Pattern

**Use for:** Footer decoration, section dividers

```
Create a horizontal decorative pattern inspired by EEG brain wave readings. The lines flow organically in soft waves, transitioning in color from purple on the left to cyan on the right. The waves should feel organic and flowing, not rigid or clinical. This is a subtle decorative border element for a website footer. The background should be transparent or white. Make it seamless so it can tile horizontally. Elegant and minimal medical aesthetic.
```

---

## PHOTO EDITING PROMPTS

Use these when you have an existing photo and want to modify it:

### Enhance Photo Quality
```
Enhance this image to improve overall quality and detail. Keep the original composition, colors, and style intact. Increase resolution, sharpness, texture clarity, and lighting realism. Maintain the natural appearance of the subject.
```

### Change Background Only
```
Replace the background of this image with [describe new background]. Keep the main subject completely unchanged, maintaining original proportions, lighting direction, and all details. Ensure the subject blends naturally with the new environment. Match the lighting and shadows to the new background. Photorealistic result.
```

### Improve Lighting
```
Adjust the lighting in this image to create warmer, more flattering illumination. Add soft fill light to reduce harsh shadows on the face. Maintain the natural appearance while making the subject look more approachable and professional. Keep all other elements unchanged.
```

---

## TIPS FOR BEST RESULTS

### Do's:
- Write in complete, descriptive sentences
- Include specific details (camera lens, lighting type, time of day)
- Describe the mood and atmosphere you want
- Mention specific colors when they matter
- Use photography terminology for realistic images

### Don'ts:
- Don't use Midjourney-style parameters (--ar, --v6, etc.)
- Don't spam keywords or use comma-separated lists
- Don't say "4k, masterpiece, trending on artstation"
- Don't generate images of real named individuals without their photos as reference

### For Editing Existing Images:
1. Upload the original image first
2. Describe what you want to change specifically
3. Explicitly state what should remain unchanged
4. Ask for "photorealistic" results for real photos

---

# Image Collection Tracker

> **WORKFLOW:** Gather all images first, then implement website changes together.

---

## COLLECTED IMAGES ✅

### Hero Section
| Status | Image | File Path | Notes |
|--------|-------|-----------|-------|
| ✅ Done | Dr. Dubey Portrait 1 | `/images/hero/dr-dubey-portrait.png` | Close-up portrait, navy scrubs, office with books & plants |
| ✅ Done | Dr. Dubey Portrait 2 | `/images/hero/dr-dubey-portrait-2.png` | Similar angle, warm lighting, professional office setting |

### Awards & Recognition
| Status | Image | File Path | Notes |
|--------|-------|-----------|-------|
| ✅ Done | ILAE EEG School Certificate | `/images/awards/ilae-eeg-school-kochi-2020.png` | 5th ILAE School on EEG, Kochi, with international faculty |
| ⬜ Need | Award ceremony 2 | | |
| ⬜ Need | Award ceremony 3 | | |
| ⬜ Need | Award ceremony 4 | | |

### Conference Presentations
| Status | Image | File Path | Notes |
|--------|-------|-----------|-------|
| ✅ Done | World Neurology Congress | `/images/conferences/world-neurology-congress-2023.png` | Podium presentation with brain scans, audience visible |
| ✅ Done | Neurology Advances 2024 | `/images/conferences/neurology-advances-2024.png` | Gesturing at brain scans, headset mic, candid action shot |
| ✅ Done | ILAE 35th Congress | `/images/conferences/ilae-35th-congress-group.png` | Group photo with international doctors, ILAE banner |
| ⬜ Need | Barcelona 2017 | | 32nd International Epilepsy Congress |
| ⬜ Need | Cape Town 2024 | | ICNC - Sleep disorders talk |

### Global Training Locations
| Status | Image | File Path | Notes |
|--------|-------|-----------|-------|
| ✅ Done | Cleveland Clinic, USA | `/images/training/cleveland-clinic-usa-2010.png` | White coat, visitor badge, American flags, building entrance |
| ✅ Done | Paris, France | `/images/training/paris-myologie-2017.png` | Profile view, examining imaging, Parisian architecture through window |
| ✅ Done | Cambridge, UK | `/images/training/cambridge-uk-2018.png` | Historic corridor, arched windows, FRCP badge, academic setting |
| ✅ Done | San Servolo, Italy | `/images/training/italy-san-servolo-2018.png` | Golden hour, Venetian waterfront, with international colleagues |
| ✅ Done | AIIMS, New Delhi | `/images/training/aiims-delhi-2015.png` | Academic Block, AIIMS white coat, campus setting |

### With Dignitaries/Senior Doctors
| Status | Image | File Path | Notes |
|--------|-------|-----------|-------|
| ✅ Done | Medical Board Meeting | `/images/dignitaries/medical-board-meeting.png` | Boardroom with senior doctors, professional discussion |
| ⬜ Need | Photo 2 | | |
| ⬜ Need | Photo 3 | | |

### Story/About Section
| Status | Image | File Path | Notes |
|--------|-------|-----------|-------|
| ✅ Done | Clinic Office Setting | `/images/about/clinic-office-setting.png` | At desk reviewing files, stethoscope, certificates on wall |
| ✅ Done | Child Consultation | `/images/gallery/child-consultation.png` | Warm interaction with child patient and parent, child-friendly office |
| ⬜ Need | Early career photo | | Optional - journey narrative |

### Clinic/Location
| Status | Image | File Path | Notes |
|--------|-------|-----------|-------|
| ⬜ Need | Medanta Hospital Indore | | For Contact section |
| ⬜ Need | Consultation room | | Optional |

---

## IMAGES TO GENERATE (AI - Nano Banana Pro)

These decorative elements have been generated using Gemini Nano Banana Pro:

| Status | Image | Prompt # | Purpose | Path |
|--------|-------|----------|---------|------|
| ✅ | Neural Garden Background | #13 | Hero/section backgrounds | `/images/decorative/neural-garden-bg.png` |
| ✅ | Brain-Tree Illustration | #14 | Decorative accent | `/images/decorative/neural-garden-bg.png` |
| ✅ | World Map with Locations | #15 | Global Training section | `/images/decorative/world-map-training.png` |
| ✅ | Parent-Child Hands | #16 | Contact section | `/images/decorative/parent-child-hands.png` |
| ✅ | Medical Badge | #17 | Trust indicators | `/images/decorative/medical-badge.png` |
| ✅ | Brain Wave Pattern | #18 | Footer decoration | `/images/decorative/brain-wave-pattern.png` |

---

## COLLECTION PROGRESS

```
Real Photos:    [██████████████] 14/15+ collected
AI Graphics:    [██████████████] 5/5 generated ✅
─────────────────────────────────────────
Overall:        [██████████████] ~95% complete
```

### Collected So Far:
1. ✅ Hero Portrait 1 (main)
2. ✅ Hero Portrait 2 (alternate)
3. ✅ ILAE Award Ceremony (Kochi)
4. ✅ World Neurology Congress (presentation)
5. ✅ Medical Board Meeting (dignitaries)
6. ✅ Neurology Advances 2024 (candid presentation)
7. ✅ Cleveland Clinic USA (training)
8. ✅ Paris Institut de Myologie (training)
9. ✅ Cambridge UK (training)
10. ✅ Italy San Servolo (training)
11. ✅ AIIMS Delhi (training)
12. ✅ Child Consultation (story/gallery)
13. ✅ ILAE 35th Congress Group (conference)
14. ✅ Clinic Office Setting (about)

---

## WHAT TO SHARE NEXT

Priority order for remaining photos:

1. **Conference/Speaking photos** - Proves expertise
2. **More award photos** - Builds credibility
3. **Training location photos** - International credentials
4. **Photos with dignitaries** - Professional network
5. **Story section candid** - Personal connection

---

# Implementation Plan (After Collection)

## Phase 1: Replace Placeholders
- [x] Hero section - Dr. Dubey portrait ✅
- [x] Story section - Candid photo with mini gallery ✅
- [ ] Testimonials - Real avatars or initials

## Phase 2: Add New Sections
- [x] Recognition Strip (below Trust Bar) - Award photos ✅
- [x] Instagram-style Gallery - All photos ✅
- [x] Enhanced Global Training - Location photos on hover ✅

## Phase 3: Generate Decorative Elements
- [ ] Background illustrations
- [ ] Section decorations
- [ ] Icons and patterns

## Phase 4: Final Polish
- [x] Lazy loading ✅
- [x] Lightbox for gallery ✅
- [x] Captions and dates ✅
- [ ] Image optimization (WebP conversion)

---

# Quick Reference: File Structure

```
/app/public/images/
├── /hero/
│   ├── dr-dubey-portrait.png ✅
│   └── dr-dubey-portrait-2.png ✅
├── /awards/
│   └── ilae-eeg-school-kochi-2020.png ✅
├── /conferences/
│   ├── world-neurology-congress-2023.png ✅
│   ├── neurology-advances-2024.png ✅
│   └── ilae-35th-congress-group.png ✅
├── /training/
│   ├── cleveland-clinic-usa-2010.png ✅
│   ├── paris-myologie-2017.png ✅
│   ├── cambridge-uk-2018.png ✅
│   ├── italy-san-servolo-2018.png ✅
│   └── aiims-delhi-2015.png ✅
├── /dignitaries/
│   └── medical-board-meeting.png ✅
├── /about/
│   └── clinic-office-setting.png ✅
├── /gallery/
│   └── child-consultation.png ✅
└── /decorative/
    ├── neural-garden-bg.png ✅
    ├── world-map-training.png ✅
    ├── parent-child-hands.png ✅
    ├── medical-badge.png ✅
    └── brain-wave-pattern.png ✅
```

---

# Summary

## Current Status
- ✅ Hero photo implemented
- ✅ 14 real photos collected
- ✅ 5 training location photos (all complete)
- ✅ 5 decorative AI illustrations generated
- ✅ Website changes implemented!

## Key Changes to Remove "AI-Generated" Feel
1. **Real Photos > Placeholders** — ✅ Implemented
2. **Instagram Gallery** — ✅ Built with category filters & lightbox
3. **Training Location Photos** — ✅ Shows on hover with popup
4. **Award/Recognition Photos** — ✅ Recognition strip added below Trust Bar
5. **Story Section** — ✅ Real photos with mini gallery

## Completed Features
1. ✅ Story section now shows real photos with interactive mini gallery
2. ✅ Global Training section shows location photos on hover
3. ✅ Recognition strip added below Trust Bar with scrolling photos
4. ✅ New Instagram-style Gallery component with:
   - Category filters (All, Awards, Conferences, Training, Dignitaries)
   - Responsive masonry grid
   - Lightbox with navigation
   - Keyboard navigation (Esc, Arrow keys)
5. ✅ Gallery link added to navigation
6. ✅ Lazy loading on all images

## Next Steps
1. Convert PNG images to WebP for optimization
2. Add more photos as they become available
3. Consider adding Testimonials section improvements

---

*Document created: February 2026*
*Last updated: February 5, 2026*
*Implementation completed: February 5, 2026*

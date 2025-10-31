# Design Guidelines for Indian Heritage Sites Platform

## Core Design Principles
- **Cultural authenticity** through Indian architectural patterns and motifs
- **Visual hierarchy** prioritizing imagery and exploration (inspired by Google Arts & Culture + Airbnb cards)
- **Warm aesthetic** reflecting India's heritage with modern, clean interface
- **Meaningful gamification** - rewarding without being childish (Duolingo-inspired)

---

## Typography

**Fonts:**
- Primary: Inter or DM Sans
- Accent: Noto Sans Devanagari (Hindi), Noto Sans Telugu
- Display: Playfair Display or Cinzel (site titles)

**Scale:**
```
Hero: 3xl-5xl (48-72px desktop, 32-48px mobile)
Sections: 2xl-3xl (30-40px desktop, 24-32px mobile)
Site Names: xl-2xl (24-30px)
Body: base-lg (16-18px, line-height 1.7-1.8)
Captions: sm-base (14-16px)
```

**Weights:** Regular (400), Medium (500), Semibold (600), Bold (700)

---

## Layout & Spacing

**Spacing Scale (Tailwind units):** 2, 4, 6, 8, 12, 16, 20, 24, 32, 40
- Micro (2, 4): Icon-text gaps
- Component (6, 8, 12): Card padding, form fields
- Section (16, 20, 24): Between page sections
- Hero (32, 40): Key content breathing room

**Containers:**
- Full sections: `w-full` + `max-w-7xl` (1280px)
- Content: `max-w-6xl` (1152px)
- Text: `max-w-4xl`
- Forms: `max-w-md` (448px)

**Responsive Grids:**
```
Site cards: grid-cols-1 md:grid-cols-2 lg:grid-cols-3
Categories: grid-cols-2 sm:grid-cols-3 md:grid-cols-4
Reviews: grid-cols-1 lg:grid-cols-2
Badges: grid-cols-3 sm:grid-cols-4 md:grid-cols-6
```

**Breakpoints:**
- Mobile: 320-767px (single column)
- Tablet: 768-1023px (2 columns)
- Desktop: 1024px+ (3-4 columns)

---

## Components

### Navigation
**Header:** Fixed/sticky, logo left (Ashoka Chakra motif), center nav (Home, Explore, My Passport, Rewards), right (Search, Language flags, Profile)
**Mobile:** Hamburger → slide-out drawer, bottom nav bar for main actions
**Search:** Rounded (`rounded-lg/full`), autocomplete dropdown, recent searches, filter icon right

### Homepage Map
**Container:** Full viewport height (minus header), Leaflet.js
**Legend:** Floating right card (desktop) / bottom drawer (mobile), collapsible, category checkboxes with counts
**Markers:** Gold star (UNESCO - largest), colored category pins, clustered for density, active state = enlarged + bounce animation

### Heritage Site Detail

**Hero Section:**
```
- Full-width carousel (h-96 to h-screen)
- Gradient overlay for text readability
- Display font for site name
- Floating actions: Share, Save, Mark Visited
- Thumbnail navigation strip
```

**Info Grid:** 2-column desktop, 1-column mobile
- Left: Location, Timings, Entry Fees cards
- Right: Weather, Getting There
- Subtle border, `rounded-corners`, `padding-6`

**Description:** 
- `max-w-4xl` centered, `line-height 1.7-1.8`
- Drop cap first letter (manuscript style)
- Pull quotes in accent styling

**Gallery:** Masonry grid (3-4 cols desktop, 2 mobile), lightbox + swipe gestures

### User Profile - Heritage Passport

**Layout:**
1. Header: Large circular avatar, name, tier badge, points
2. Stats Row: 3-card grid (sites visited, reviews, badges)
3. Tabs: Visited Sites, Achievements, Rewards

**Passport Map:** Interactive India map, filled regions, category progress bars (UNESCO: 5/42), trophy wall

**Timeline:** Vertical alternating cards, dotted connector, site thumbnail + date + review snippet

### Check-In Interface
**Modal:** Full-screen mobile / centered desktop
- GPS verification with loading animation
- Photo upload dropzone with preview
- Success: Confetti (3s), points display, share prompt
- Nearby sites carousel

### Reviews

**Card Structure:**
```
- Header: Avatar, name, tier badge, visit date
- Large star rating
- Category ratings (horizontal bars + icons)
- Review text (expandable "Read more")
- Photo grid (2x2 or scrollable)
- Helpful/Not Helpful buttons
```

**Write Form:**
- Large tap targets for stars
- Slider inputs for categories
- Rich text editor (simple formatting)
- Drag-drop photo upload, preview grid
- Character counter (50-1000)

### AI Chatbot
**Float bubble** bottom-right (desktop) / bottom-center (mobile)
**Window:** 400×600px
- Bot avatar header, minimize/close
- Message bubbles: left (bot), right (user)
- Quick chips: "How to reach?", "Tell me history", "Best time to visit"
- Voice input microphone icon
- Typing indicator animation

### Gamification

**Achievement Badges:**
- Circular, Indian motif backgrounds (Rangoli, Mandala, temple carvings)
- Gold/Silver/Bronze borders
- Locked: Grayscale + lock icon
- Unlocked: Full color + subtle glow

**Progress:**
- Circular rings for tier advancement
- Linear bars for category completion
- Animated counter for points

**E-Vouchers:**
- Credit card style: Partner logo, large discount, validity, QR code
- Barcode pattern background texture

### Cards

**Heritage Site Cards:**
```
- Vertical layout: 16:9 image top, content below
- padding-4, category badge overlay (top-left)
- Site name (font-semibold, text-lg)
- Location + pin icon, distance
- Hover: +2px elevation, image zoom
```

**Category Filters:** Icon top, label + count below, equal height, active border highlight

### Forms & Buttons

**Inputs:**
- Floating/top labels, `py-3 px-4`, `rounded-lg`
- Focus ring, error messages below
- Icons inside (left/right)

**Buttons:**
```
Primary: py-3 px-6, semibold
Secondary: Outlined
Icon: Circular/square, padding-2/3
CTAs on images: Backdrop blur background
```

---

## Images

**Required Images:**

1. **Homepage Banner:** Rotating carousel, full-width `h-64` to `h-80`, tagline overlay "Explore India's Living Heritage"

2. **Site Pages:** 
   - Hero: 1920×1080px min, architectural photography
   - Gallery: Wide shots + details + cultural context
   - Natural light, people for scale

3. **Category Icons:** Consistent style (line/filled), color-themed (gold, blue, green, purple, red, orange, teal)

4. **User Content:**
   - Check-ins: Square 1:1 crops
   - Reviews: Various orientations
   - Avatars: Circular crops

5. **Badges:** Circular with Indian architectural motifs, centered achievement icon

**Development Placeholder:** unsplash.com/collections/indian-heritage

---

## Accessibility (WCAG AA)

- Semantic HTML, ARIA labels for map elements
- Keyboard navigation (tab, enter, escape), visible focus indicators (ring)
- Alt text for all images, skip navigation links
- Screen reader announcements for check-in success, points earned
- Min 44px touch targets (mobile)
- Sufficient color contrast ratios

---

## Animations & Interactions

**Use Sparingly:**
```
Check-in success: Confetti (3s)
Badge unlock: Scale-in + glow
Map marker: Bounce on add
Card hover: +2px elevation lift
Page transitions: 300ms fade
Loading: Skeleton screens (not spinners)
```

**Avoid:** Excessive parallax, continuous animations, auto-play carousels, distracting scroll effects

---

## Multilingual Support

**Language Selector:** Flag icons + name dropdown, 3 languages, persistent across sessions, fade animation on switch

---

## Mobile Optimizations

- Bottom fixed navigation bar
- Collapsible map legend (bottom sheet)
- Full-screen modals (check-in, reviews)
- Min 44px tap targets
- Swipe gestures (galleries, carousels)
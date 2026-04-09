# CLAUDE.md — Frontend Website Rules

## Always Do First
- **Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.

## Reference Images
- If a reference image is provided: match layout, spacing, typography, and color exactly. Swap in placeholder content (images via `https://placehold.co/`, generic copy). Do not improve or add to the design.
- If no reference image: design from scratch with high craft (see guardrails below).
- Screenshot your output, compare against reference, fix mismatches, re-screenshot. Do at least 2 comparison rounds. Stop only when no visible differences remain or user says so.

## Local Server (Optional)
- User can double-click the HTML file to open in browser – no server required.
- If user requests live reload, use `npx serve .` or `python -m http.server 8000`.
- Default to no server unless user asks.

## Screenshot Workflow
- Puppeteer is installed at `C:/Users/Abdul/AppData/Local/Temp/puppeteer-test/`. Chrome cache is at `C:/Users/Abdul/.cache/puppeteer/`.
- **Always screenshot from localhost:** `node screenshot.mjs http://localhost:3000`
- Screenshots are saved automatically to `./temporary screenshots/screenshot-N.png` (auto-incremented, never overwritten).
- Optional label suffix: `node screenshot.mjs http://localhost:3000 label` → saves as `screenshot-N-label.png`
- `screenshot.mjs` lives in the project root. Use it as-is.
- After screenshotting, read the PNG from `temporary screenshots/` with the Read tool — Claude can see and analyze the image directly.
- When comparing, be specific: "heading is 32px but reference shows ~24px", "card gap is 16px but should be 24px"
- Check: spacing/padding, font size/weight/line-height, colors (exact hex), alignment, border-radius, shadows, image sizing

## Output Defaults
- Single `index.html` file, all styles inline, unless user says otherwise
- Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Placeholder images: `https://placehold.co/WIDTHxHEIGHT`
- Mobile-first responsive

## Brand Assets
- Always check the `Brand_Assets/` folder before designing. It may contain logos, color guides, style guides, or images.
- If assets exist there, use them. Do not use placeholders where real assets are available.
- If a logo is present, use it. If a color palette is defined, use those exact values — do not invent brand colors.

#### Starcom Design Guardrails
-- **Shadows:** Use subtle shadows only: `box-shadow: 0 4px 12px rgba(0,0,0,0.05)` – nothing dramatic.
- **Typography:** Use ONE font family for everything (Inter or Poppins). B2B corporate sites need consistency, not font contrast.
- **Gradients:** DO NOT use gradients, grain textures, or SVG noise filters. Keep it flat and clean.
- **Animations:** Only animate `transform` and `opacity` on hover (e.g., scale 1.02). Never use `transition-all`. Keep animations minimal.
- **Interactive states:** Every button needs hover state (darker background or subtle scale). Focus-visible for accessibility.
- **Images:** No gradient overlays. No mix-blend modes. Keep product photos clean on white background.
- **Spacing:** Use consistent spacing: 16px, 24px, 32px, 48px, 64px.
- **Depth:** Keep it flat. No layering system needed.

## STARCOM WEBSITE – REQUIRED SECTIONS (IN ORDER)
Build a SINGLE PAGE website with these sections:

1. **Hero Section**
   - Logo text: "Starcom Information COMPUTERS TRADING LLC"
   - Tagline: "Reliable Technology Accessories – Corporate & Retail Supply"
   - CTA Button: "Request a Quote" (links to contact section)

2. **Mission Section**
   - Text: "To provide reliable and efficient technology solutions that keep our clients connected at all times."
   - Three icons below: Long-term relationships | Product reliability | After-sales support

3. **Products Section** (4 cards in 2x2 grid on desktop, 1 column on mobile)
   - Card 1: Computer & Mobile Accessories (Keyboards, mice, headsets, chargers)
   - Card 2: Storage & Memory Solutions (SSDs, HDDs, USB drives, memory cards)
   - Card 3: Peripherals & Connectivity (Routers, switches, hubs, Bluetooth)
   - Card 4: Consumer Electronics Accessories (Cases, screen protectors, power banks)

4. **Why Choose Us Section** (6 cards in 2 rows x 3 columns)
   - Local, responsive team
   - Competitive pricing
   - Genuine products only
   - Fast decisions, no bureaucracy
   - Physical store for verification
   - Personalized service

5.5. **Brands We Deal With Section**
   
   **INSTRUCTION:**
   - Check the `brand_assets/` folder for a file named `brands-image.png` or `brands-image.jpg`
   - If the file exists, display that image as a banner/collage of all brand logos
   - If the image does NOT exist, display placeholder text: "Partnering with leading global technology brands"
   
   **Layout:**
   - Title: "Brands We Deal With"
   - Subtitle: "Partnering with globally trusted technology brands" 
   - Image centered, responsive, rounded corners

6. **Contact Section** (split layout: left contact info, right contact form)
   - Address: Bur Dubai - 23 St - Al Souq Al Kabeer - Dubai - UAE
   - Hours: Sat–Thu 9am–7pm, Fri Closed
   - Phone: +971 50 307 6027
   - Email: info@starcominfo.com
   - Contact form: Name, Email, Message, Submit button

7. **Footer**
   - Social media icons (placeholder – user will add links later)
   - Newsletter signup: "Subscribe for 10% off your first purchase"
   - Copyright: "© 2026 Starcom Information Electronics Trading LLC"

## DO NOT INCLUDE
- Growth charts or graphs
- Global presence map
- Multiple branch locations
- Team member photos
- Blog section
- Pricing tables

## STYLING REQUIREMENTS
- Mobile-first responsive
- Use Tailwind CSS via CDN
- Rounded corners: 8px for cards, 4px for buttons
- Max width container: 1280px, centered with mx-auto
- Padding: 16px on mobile, 32px on desktop
- Background alternates: white → light gray (#F5F7FA) → white


## Hard Rules
- Do not add sections, features, or content not in the reference
- Do not "improve" a reference design — match it unless told to
- Do not stop after one screenshot pass
- Do not use `transition-all`
- Do not use default Tailwind blue/indigo as primary color

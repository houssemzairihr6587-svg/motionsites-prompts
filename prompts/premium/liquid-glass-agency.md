# Liquid Glass Agency

**Category:** Landing Page
**Type:** hero
**Slug:** liquid-glass-agency
**Tier:** Premium
**Page Type:** landing

---

## Prompt

```
Build a dark, premium, single-page landing page for an AI-powered web design agency using React + Vite + Tailwind CSS + shadcn/ui + Framer Motion (motion/react). The page has a luxury editorial aesthetic -- black backgrounds, white text, liquid glass (glassmorphism) effects, and cinematic video backgrounds.

FONTS
Import from Google Fonts:

https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Barlow:wght@300;400;500;600&display=swap
* Headings:Â Instrument SerifÂ (italic) -- used via Tailwind classÂ font-heading
* Body:Â BarlowÂ (weights 300, 400, 500, 600) -- used via Tailwind classÂ font-body
Tailwind config extends fontFamily:

heading: ["'Instrument Serif'", "serif"]
body: ["'Barlow'", "sans-serif"]

COLOR THEME (CSS custom properties, HSL format)

:root {
  --background: 213 45% 67%;
  --foreground: 0 0% 100%;
  --card: 213 45% 62%;
  --card-foreground: 0 0% 100%;
  --primary: 0 0% 100%;
  --primary-foreground: 213 45% 67%;
  --secondary: 213 45% 72%;
  --secondary-foreground: 0 0% 100%;
  --muted: 213 35% 60%;
  --muted-foreground: 0 0% 100% / 0.7;
  --accent: 213 45% 72%;
  --accent-foreground: 0 0% 100%;
  --destructive: 0 84.2% 60.2%;
  --border: 0 0% 100% / 0.2;
  --input: 0 0% 100% / 0.2;
  --ring: 0 0% 100% / 0.3;
  --radius: 9999px;
  --glass-bg: rgba(255, 255, 255, 0.12);
  --glass-border: rgba(255, 255, 255, 0.25);
  --glass-shadow: 0 4px 30px rgba(0, 0, 0, 0.08);
  --glass-blur: 16px;
}

LIQUID GLASS CSS (the core visual effect)
Two utility classes defined in index.css under @layer components:
.liquid-glass (subtle):

.liquid-glass {
  background: rgba(255, 255, 255, 0.01);
  background-blend-mode: luminosity;
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border: none;
  box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1);
  position: relative;
  overflow: hidden;
}
.liquid-glass::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1.4px;
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.45) 0%,
    rgba(255, 255, 255, 0.15) 20%,
    rgba(255, 255, 255, 0) 40%,
    rgba(255, 255, 255, 0) 60%,
    rgba(255, 255, 255, 0.15) 80%,
    rgba(255, 255, 255, 0.45) 100%
  );
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
.liquid-glass-strong (more prominent, used on CTA buttons):

.liquid-glass-strong {
  background: rgba(255, 255, 255, 0.01);
  background-blend-mode: luminosity;
  backdrop-filter: blur(50px);
  -webkit-backdrop-filter: blur(50px);
  border: none;
  box-shadow: 4px 4px 4px rgba(0, 0, 0, 0.05),
    inset 0 1px 1px rgba(255, 255, 255, 0.15);
  position: relative;
  overflow: hidden;
}
.liquid-glass-strong::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1.4px;
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.5) 0%,
    rgba(255, 255, 255, 0.2) 20%,
    rgba(255, 255, 255, 0) 40%,
    rgba(255, 255, 255, 0) 60%,
    rgba(255, 255, 255, 0.2) 80%,
    rgba(255, 255, 255, 0.5) 100%
  );
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
The ::before pseudo-element creates a gradient border effect using the mask-composite trick (thin glowing border that fades in the middle).

ASSETS & MEDIA URLS
Hero background video (MP4, CloudFront):

https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260307_083826_e938b29f-a43a-41ec-a153-3d4730578ab8.mp4
Poster image: /images/hero_bg.jpeg (local file in public/images/)
StartSection video (HLS via Mux):

https://stream.mux.com/9JXDljEVWYwWu01PUkAemafDugK89o01BR6zqJ3aS9u00A.m3u8
Stats section video (HLS via Mux, displayed desaturated):

https://stream.mux.com/NcU3HlHeF7CUL86azTTzpy3Tlb00d6iF3BmCdFslMJYM.m3u8
CTA/Footer section video (HLS via Mux):

https://stream.mux.com/8wrHPCX2dC3msyYU9ObwqNdm00u3ViXvOSHUMRYSEe5Q.m3u8
Feature GIFs (imported from src/assets/):
* feature-1.gifÂ -- used in FeaturesChess row 1 (right side)
* feature-2.gifÂ -- used in FeaturesChess row 2 (left side)
Logo icon: src/assets/logo-icon.png (12x12 Tailwind = h-12 w-12)

SECTION-BY-SECTION BREAKDOWN
1. NAVBAR (fixed, floating)
* Fixed position:Â fixed top-4 left-0 right-0 z-50, horizontal paddingÂ px-8 lg:px-16, verticalÂ py-3
* Left: Logo image (h-12 w-12)
* Center (desktop only,Â hidden md:flex): Navigation links inside aÂ liquid-glass rounded-full px-1.5 py-1Â pill container
    * Links: "Home", "Services", "Work", "Process", "Pricing"
    * Each link:Â px-3 py-2 text-sm font-medium text-foreground/90 font-body
    * Last item: white solid button "Get Started" withÂ ArrowUpRightÂ icon,Â bg-white text-black rounded-full px-3.5 py-1.5 text-sm
2. HERO SECTION
* Container:Â relative overflow-visible, fixed heightÂ 1000px
* Background video:Â <video>Â tag with autoPlay, loop, muted, playsInline. PositionedÂ absolute left-0 w-full h-auto object-contain z-0Â withÂ top: 20%. Source is the CloudFront MP4 URL. Poster isÂ /images/hero_bg.jpeg.
* Dark overlay:Â absolute inset-0 bg-black/5 z-0
* Bottom gradient fade:Â absolute bottom-0, height 300px,Â linear-gradient(to bottom, transparent, black)
* ContentÂ (z-10, centered,Â paddingTop: 150px):
    * Badge pill:Â liquid-glass rounded-full px-1 py-1Â with inner white "New" badge (bg-white text-black rounded-full px-3 py-1 text-xs font-semibold) and text "Introducing AI-powered web design."
    * HeadingÂ (BlurText component): "The Website Your Brand Deserves" --Â text-6xl md:text-7xl lg:text-[5.5rem] font-heading italic text-foreground leading-[0.8] max-w-2xl tracking-[-4px], animated word-by-word from bottom with blur, delay 100ms
    * SubtextÂ (motion.p): "Stunning design. Blazing performance. Built by AI, refined by experts. This is web design, wildly reimagined." -- blur-in animation, delay 0.8s,Â text-sm md:text-base text-white font-body font-light leading-tight
    * CTA buttonsÂ (motion.div, delay 1.1s):
        * "Get Started" --Â liquid-glass-strong rounded-full px-5 py-2.5Â withÂ ArrowUpRightÂ icon
        * "Watch the Film" -- text-only withÂ PlayÂ icon (filled)
    * Partners barÂ at bottom (mt-auto pb-8 pt-16): "Trusted by the teams behind" liquid-glass pill, then 5 partner names rendered inÂ text-2xl md:text-3xl font-heading italic text-whiteÂ withÂ gap-12 md:gap-16: Stripe, Vercel, Linear, Notion, Figma
3. BlurText COMPONENT (custom animated text)
* Splits text by words or letters
* Uses IntersectionObserver to trigger on scroll
* Each word/letter is aÂ <motion.span>Â that animates fromÂ {filter: 'blur(10px)', opacity: 0, y: 50}Â (when direction=bottom) throughÂ {filter: 'blur(5px)', opacity: 0.5, y: -5}Â toÂ {filter: 'blur(0px)', opacity: 1, y: 0}
* Staggered by index with configurable delay (default 200ms per element)
* Step duration 0.35s per keyframe step
4. START SECTION ("How It Works")
* Full-width section with HLS video background usingÂ hls.jsÂ library
* Video: autoPlay, loop, muted, playsInline,Â absolute inset-0 w-full h-full object-cover
* Top and bottom gradient fades (200px each, black to transparent)
* Content centered (z-10, minHeight 500px):
    * Badge: "How It Works" inÂ liquid-glass rounded-full px-3.5 py-1
    * Heading: "You dream it. We ship it." --Â text-4xl md:text-5xl lg:text-6xl font-heading italic tracking-tight leading-[0.9]
    * Subtext: "Share your vision. Our AI handles the rest--wireframes, design, code, launch. All in days, not quarters." --Â text-white/60 font-body font-light text-sm md:text-base
    * CTA: "Get Started"Â liquid-glass-strong rounded-full px-6 py-3
5. FEATURES CHESS (alternating rows)
* Section header: "Capabilities" badge + "Pro features. Zero complexity." heading
* Row 1Â (flex, content left / image right):
    * Title: "Designed to convert. Built to perform."
    * Body: "Every pixel is intentional. Our AI studies what works across thousands of top sites--then builds yours to outperform them all."
    * Button: "Learn more"Â liquid-glass-strong
    * Gif:Â https://motionsites.ai/assets/hero-finlytic-preview-CV9g0FHP.gif download and placeÂ insideÂ liquid-glass rounded-2xl overflow-hidden
* Row 2Â (flex-row-reverse, content right / image left):
    * Title: "It gets smarter. Automatically."
    * Body: "Your site evolves on its own. AI monitors every click, scroll, and conversion--then optimizes in real time. No manual updates. Ever."
    * Button: "See how it works"Â liquid-glass-strong
    * gif:Â https://motionsites.ai/assets/hero-wealth-preview-B70idl_u.gif download and placeÂ insideÂ liquid-glass rounded-2xl overflow-hidden
6. FEATURES GRID ("Why Us")
* Section header: "Why Us" badge + "The difference is everything." heading
* 4-column grid (grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6), each card isÂ liquid-glass rounded-2xl p-6:
    1. Icon:Â ZapÂ -- "Days, Not Months" -- "Concept to launch at a pace that redefines fast. Because waiting isn't a strategy."
    2. Icon:Â PaletteÂ -- "Obsessively Crafted" -- "Every detail considered. Every element refined. Design so precise, it feels inevitable."
    3. Icon:Â BarChart3Â -- "Built to Convert" -- "Layouts informed by data. Decisions backed by performance. Results you can measure."
    4. Icon:Â ShieldÂ -- "Secure by Default" -- "Enterprise-grade protection comes standard. SSL, DDoS mitigation, compliance. All included."
    * Each icon sits in aÂ liquid-glass-strong rounded-full w-10 h-10Â circle
7. STATS SECTION
* HLS video background (Mux URL), displayed withÂ filter: saturate(0)Â (desaturated/B&W)
* Top and bottom gradient fades (200px each)
* Content:Â liquid-glass rounded-3xl p-12 md:p-16Â card with 4-column grid:
    * "200+" / "Sites launched"
    * "98%" / "Client satisfaction"
    * "3.2x" / "More conversions"
    * "5 days" / "Average delivery"
    * Values:Â text-4xl md:text-5xl lg:text-6xl font-heading italic
    * Labels:Â text-white/60 font-body font-light text-sm
8. TESTIMONIALS
* Section header: "What They Say" badge + "Don't take our word for it." heading
* 3-column grid (md:grid-cols-3 gap-6), each card isÂ liquid-glass rounded-2xl p-8:
    1. "A complete rebuild in five days. The result outperformed everything we'd spent months building before." -- Sarah Chen, CEO, Luminary
    2. "Conversions up 4x. That's not a typo. The design just works differently when it's built on real data." -- Marcus Webb, Head of Growth, Arcline
    3. "They didn't just design our site. They defined our brand. World-class doesn't begin to cover it." -- Elena Voss, Brand Director, Helix
    * Quote:Â text-white/80 font-body font-light text-sm italic
    * Name:Â text-white font-body font-medium text-sm
    * Role:Â text-white/50 font-body font-light text-xs
9. CTA + FOOTER
* HLS video background (Mux URL)
* Top and bottom gradient fades (200px each)
* Content (z-10, centered):
    * Heading: "Your next website starts here." --Â text-5xl md:text-6xl lg:text-7xl font-heading italic leading-[0.85]
    * Subtext: "Book a free strategy call. See what AI-powered design can do. No commitment, no pressure. Just possibilities."
    * Two buttons:
        * "Book a Call" --Â liquid-glass-strong rounded-full px-6 py-3
        * "View Pricing" --Â bg-white text-black rounded-full px-6 py-3
    * Footer bar (mt-32 pt-8 border-t border-white/10):
        * Left: "(c) 2026 Studio. All rights reserved."Â text-white/40 text-xs
        * Right: "Privacy", "Terms", "Contact" linksÂ text-white/40 text-xs

KEY DEPENDENCIES

{
  "motion": "^12.35.0",
  "hls.js": "^1.6.15",
  "lucide-react": "^0.462.0",
  "react-router-dom": "^6.30.1"
}
Icons used from lucide-react: ArrowUpRight, Play, Zap, Palette, BarChart3, Shield

OVERALL PAGE STRUCTURE

<div bg-black>
  <div z-10>
    <Navbar />           -- fixed floating nav
    <Hero />             -- 1000px tall, CloudFront MP4 video bg
    <div bg-black>
      <StartSection />   -- HLS video bg, "How It Works"
      <FeaturesChess />  -- alternating text/gif rows
      <FeaturesGrid />   -- 4-card grid
      <Stats />          -- HLS video bg (desaturated), stats card
      <Testimonials />   -- 3-card grid
      <CtaFooter />      -- HLS video bg, CTA + footer
    </div>
  </div>
</div>

ANIMATION PATTERNS
1. BlurTextÂ (heading): Word-by-word stagger from bottom with gaussian blur dissolve, IntersectionObserver triggered
2. Hero subtext:Â motion.pÂ withÂ filter: blur(10px) -> blur(0px),Â opacity: 0 -> 1,Â y: 20 -> 0, delay 0.8s, duration 0.6s
3. Hero CTA buttons: Same blur-in pattern, delay 1.1s
4. All video backgrounds: autoPlay, loop, muted, playsInline with top/bottom black gradient fades (200px typically, 300px on hero bottom)

DESIGN PATTERNS USED THROUGHOUT
* Every section badge:Â liquid-glass rounded-full px-3.5 py-1 text-xs font-medium text-white font-body
* Every section heading:Â text-4xl md:text-5xl lg:text-6xl font-heading italic text-white tracking-tight leading-[0.9]
* Every body text:Â text-white/60Â orÂ text-white/70,Â font-body font-light text-sm md:text-base
* Primary CTA:Â liquid-glass-strong rounded-fullÂ withÂ ArrowUpRightÂ icon
* Secondary CTA:Â bg-white text-black rounded-full
* Card containers:Â liquid-glass rounded-2xl
* Video overlay fades: alwaysÂ linear-gradient(to bottom/top, black, transparent)Â withÂ pointer-events-none

```
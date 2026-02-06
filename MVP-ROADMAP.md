# ⚡ Haoma — 3-Hour Hackathon MVP Roadmap

**Event:** v0 Prompt to Production @ Picnic HQ, Amsterdam  
**Date:** Friday, Feb 7, 2026 | 9:30 AM — 1:30 PM (~3 hrs build time)  
**Tool:** v0 (Next.js + React + Tailwind + shadcn/ui)  
**Builder:** Juan (solo)

---

## 🎯 MVP Goal

A working demo that shows: **Symptom → AI Plant Recommendations → Preparation Guide → Product Finder → Store Map → Start Protocol.**

Core wow factor: **the preparation comparison table + combination checker.** Nobody else has this in a consumer-friendly format.

---

## 🧠 v0 Prompt Framework (from Vercel's official guide)

Every prompt should include:
1. **Product Surface** — What you're building (components, data, actions)
2. **Context of Use** — Who uses it, when, to make what decision
3. **Constraints** — Platform, colors, layout, visual tone

---

## ⏱️ Build Timeline

### Phase 1: Core UI Shell (0:00 — 0:45) ⏰ 45 min

**v0 Prompt 1 — Home + Symptom Input**
```
Build a mobile health app home screen for "Haoma" — an AI herbalist app.

PRODUCT SURFACE:
- App header with leaf emoji logo 🌿 and name "Haoma"
- Tagline: "Your AI Herbalist"
- Large search input with placeholder "What's bothering you?"
- Row of tappable symptom chips below search: Sleep, Anxiety, Digestion, Energy, Pain, Focus, Immunity (with emoji icons)
- "Recent Searches" section showing 3 past queries with timestamps
- Bottom navigation bar: Home (active), My Plants, Protocol, Profile

CONTEXT OF USE:
Used by health-conscious millennials (25-40) who prefer natural remedies over pharmaceuticals.
They open the app when they have a specific symptom (can't sleep, anxious, stomach issues) and want quick plant-based recommendations.
Typically used at home in the evening when symptoms bother them.

CONSTRAINTS:
- Mobile-first (iPhone sized, 390px width)
- Color palette: primary green #2d6a4f, light green #ecfdf5, white backgrounds, gray #6b7280 for secondary text
- Use shadcn/ui components
- Rounded corners (16px on cards, 24px on search input)
- Clean, calming wellness aesthetic (think Calm app meets WebMD)
- Font: system default, clear hierarchy
```

**v0 Prompt 2 — Results + Plant Cards**
```
Build a plant recommendation results page for the Haoma herbalist app.

PRODUCT SURFACE:
- Green header bar showing the user's query: "Can't sleep, feeling anxious"
- Subtitle: "5 plants found • AI-powered"
- Back button in header
- Scrollable list of 5 plant recommendation cards, each showing:
  • Plant emoji icon (🌸🌼🌾🌿💜)
  • Plant name (bold): "Valerian"
  • Botanical name (italic, gray): "Valeriana officinalis"
  • One-line benefit: "Natural sedative for deep, restful sleep"
  • Match score badge: "92% match" in green pill
  • Evidence badge: "Clinical" or "Traditional" or "Both" in blue pill
  • Small form icons showing available forms: 🫖💊💧
- Cards are tappable (show hover/press state)
- Same bottom nav as home screen

CONTEXT OF USE:
User just typed their symptoms and is scanning results to find the best plant match.
They're comparing options quickly — match percentage helps them decide.
They'll tap the top result to learn more.

CONSTRAINTS:
- Mobile-first (390px width)
- Cards: white background, subtle shadow, 12px rounded corners
- Match badge: background #d1fae5, text #065f46
- Evidence badge: background #dbeafe, text #1e40af
- Header: solid #2d6a4f green
- Scrollable list with 16px padding

SAMPLE DATA for the 5 cards:
1. Valerian | V. officinalis | "Natural sedative for deep sleep" | 92% | Clinical | 🫖💊💧
2. Passionflower | P. incarnata | "Calms racing thoughts, eases anxiety" | 87% | Both | 🫖💊
3. Ashwagandha | W. somnifera | "Reduces cortisol, adaptogenic stress relief" | 81% | Clinical | 💊🧪
4. Chamomile | M. chamomilla | "Gentle anxiety relief, aids digestion" | 76% | Both | 🫖💧
5. Lavender | L. angustifolia | "Soothes nerves, mild sedative" | 72% | Both | 🫖💧
```

**Deliverable:** Navigable home → results flow with static data.

---

### Phase 2: Plant Detail + Preparation Guide (0:45 — 1:30) ⏰ 45 min

**v0 Prompt 3 — Plant Detail with Tabs (THE KEY SCREEN)**
```
Build a plant detail page with 3 tabs for the Haoma herbalist app. This is the core feature.

PRODUCT SURFACE:
- Hero section: light green gradient background, large plant emoji 🌸, plant name "Valerian", botanical name "Valeriana officinalis"
- Back button top-left
- 3 tabs below hero: "Overview" | "How to Take" | "Combines With"
- Tab content area below

TAB 1 - Overview (default active):
- Description: "One of the most studied herbal sedatives. Used for centuries to treat insomnia and nervous restlessness. Works by increasing GABA levels in the brain."
- Key Compounds section with pill badges: "Valerenic acid", "Isovaleric acid", "Hesperidin", "GABA"
- Effectiveness rating: 4 out of 5 stars with label "Strong clinical evidence"
- "📅 Recommended: 2-4 weeks for full effect"
- Large CTA button: "▶️ Start Protocol" (green, full width)

TAB 2 - How to Take (THIS IS THE DIFFERENTIATOR):
- Comparison showing 4 preparation forms as cards:

Form 1 - Tea 🫖:
  Dosage: "2-3g dried root"
  Preparation: "Steep 10-15 min in hot water"
  When: "1 hour before bed"
  Onset: "30-60 min"
  Duration: "4-6 hours"
  Best for: "Mild sleep issues"

Form 2 - Capsule 💊:
  Dosage: "300-600mg"
  Preparation: "Swallow with water"
  When: "30 min before bed"
  Onset: "20-45 min"
  Duration: "6-8 hours"
  Best for: "Consistent daily dosing"

Form 3 - Tincture 💧:
  Dosage: "1-2ml (20-40 drops)"
  Preparation: "In water or under tongue"
  When: "2x daily or before bed"
  Onset: "15-30 min"
  Duration: "3-4 hours"
  Best for: "Quick absorption"

Form 4 - Extract 🧪:
  Dosage: "150-300mg standardized"
  Preparation: "Swallow with water"
  When: "As directed"
  Onset: "20-40 min"
  Duration: "6-8 hours"
  Best for: "Maximum potency"

- Yellow warning box at bottom:
  "⚠️ Side Effects & Cautions"
  "Headache, dizziness, stomach upset (rare). Avoid with sedatives, alcohol, before surgery. Not for pregnancy/breastfeeding."

TAB 3 - Combines With:
- Green section "✅ Synergies" with 3 cards:
  • 🌼 Passionflower → "Enhanced sleep quality & duration"
  • 🍃 Lemon Balm → "Reduced anxiety + better sleep onset"
  • 🌿 Chamomile → "Gentle calming synergy"
- Yellow section "⚠️ Use with Caution" with 1 card:
  • 🌴 Kava → "Risk of excessive sedation"
- Green section "💡 Pre-built Stacks" with 2 cards:
  • "🌙 Deep Sleep Stack" — Valerian + Passionflower + Magnesium — "1hr before bed • 2-4 weeks"
  • "😌 Calm Mind Stack" — Valerian + Lemon Balm + L-Theanine — "2x daily • Reduces anxiety"

CONTEXT OF USE:
User tapped a plant from results and wants to understand HOW to actually use it.
The "How to Take" tab is the killer feature — no other app compares forms side-by-side.
They're deciding: should I buy tea, capsules, or tincture?

CONSTRAINTS:
- Mobile-first (390px width)
- Use shadcn Tabs component
- Hero gradient: from #ecfdf5 to #d1fae5
- Form cards: gray background #f9fafb, 10px rounded corners
- Warning box: yellow background #fef3c7, amber text #92400e
- Synergy cards: left border green #10b981
- Caution cards: left border yellow #f59e0b
- Stack cards: light green background #ecfdf5
```

**Deliverable:** Full plant detail with preparation comparison — the differentiator.

---

### Phase 3: Product Finder + Store Map (1:30 — 2:15) ⏰ 45 min

**v0 Prompt 4 — Product Finder**
```
Build a product finder page for the Haoma herbalist app showing where to buy Valerian products.

PRODUCT SURFACE:
- Green header with "← Valerian" back link and title "🛒 Find Products"
- Filter chips below header: All (active), 🫖 Tea, 💊 Capsule, 💧 Tincture
- Scrollable list of 4 product cards, each showing:
  • Product name (bold): "Valerian Root 500mg Capsules"
  • Brand (gray): "Holland & Barrett"
  • Price (large, green): "€12.99"
  • Form badge: "💊 60 caps"
  • Stock badge: "🟢 In Stock" (green) or "🟡 Low Stock" (yellow)
  • Star rating: "★ 4.5"
  • Two buttons: "Buy Online →" (green, primary) and "📍 Store" (gray, secondary)
- Bottom nav

CONTEXT OF USE:
User decided they want Valerian and now needs to buy it.
They're comparing prices and checking what's in stock nearby.
They want to either buy online (affiliate link) or find a local store.

CONSTRAINTS:
- Mobile-first (390px width)
- Product cards: white background, 10px rounded corners, subtle shadow
- Stock "In Stock": background #d1fae5, text #065f46
- Stock "Low Stock": background #fef3c7, text #92400e
- Buy button: background #2d6a4f, white text
- Store button: background #f3f4f6, dark text
- Price: font-size 18px, font-weight bold, color #2d6a4f

SAMPLE DATA for 4 products:
1. "Valerian Root 500mg Capsules" | Holland & Barrett | €12.99 | 💊 60 caps | 🟢 In Stock | ★ 4.5
2. "Valerian Root Tea" | Jacob Hooy | €4.50 | 🫖 50g loose | 🟢 In Stock | ★ 4.8
3. "Valerian Tincture 50ml" | De Tuinen | €8.95 | 💧 Tincture | 🟡 Low Stock | ★ 4.2
4. "Solgar Valerian 520mg" | Bol.com | €16.99 | 💊 100 caps | 🟢 In Stock | ★ 4.6
```

**v0 Prompt 5 — Store Map**
```
Build a store locator page for the Haoma herbalist app showing Amsterdam herb shops.

PRODUCT SURFACE:
- Map placeholder area (green/gray gradient rectangle, 160px tall) with pin emojis 📍 scattered and one 📌 for user location
- "Amsterdam Centrum" label in corner of map
- Below map: scrollable list of 4 store cards, each showing:
  • Numbered circle (1, 2, 3, 4) in green
  • Store name (bold): "Jacob Hooy & Co"
  • Address (gray): "Kloveniersburgwal 12"
  • Meta line: "Mon-Sat 9-18 • 3 products"
  • Distance (green, right-aligned): "0.3 km"
- Divider lines between store cards
- Bottom nav

CONTEXT OF USE:
User wants to buy locally instead of online.
They're checking which store is closest and has the products they need.
They'll tap "Get Directions" to navigate.

CONSTRAINTS:
- Mobile-first (390px width)
- Map area: placeholder div with gradient background (no actual map needed)
- Number circles: 22px, background #2d6a4f, white text
- Store name: font-weight 600
- Distance: color #2d6a4f, font-weight 600
- Subtle divider lines between cards

SAMPLE DATA for 4 stores:
1. Jacob Hooy & Co | Kloveniersburgwal 12 | Mon-Sat 9-18 | 3 products | 0.3 km
2. De Tuinen | Kalverstraat 134 | Mon-Sat 9:30-18 | 2 products | 0.5 km
3. Holland & Barrett | Damrak 81 | Mon-Sun 9-21 | 5 products | 0.8 km
4. Ekoplaza | Sarphatistraat 27 | Mon-Sat 8-20 | 2 products | 1.2 km
```

**Deliverable:** Product cards with prices + store list with real Amsterdam locations.

---

### Phase 4: Protocol + Polish (2:15 — 3:00) ⏰ 45 min

**v0 Prompt 6 — Protocol Tracker + Daily Check-in**
```
Build a protocol tracking page for the Haoma herbalist app showing daily check-in.

PRODUCT SURFACE:
- Light green gradient background for entire screen
- Header: "🌸 Valerian Protocol"
- Subheader: "💊 Capsule 300mg • Before bed"
- Large day counter: "Day 5" (big text) with "of 28 days" below
- Streak badge: "🔥 5-day streak" in yellow/amber pill
- Progress bar (18% filled, green on gray)
- Section: "How do you feel today?"
- Row of 5 emoji buttons: 😫 😕 😐 🙂 😊 (🙂 is selected/highlighted)
- 3 symptom sliders with labels and values:
  • "Sleep Quality" — slider at 70% — "7/10"
  • "Time to Fall Asleep" — slider at 60% — "6/10"
  • "Anxiety Level" — slider at 40% — "4/10"
- Large CTA button: "✅ Check In" (green, full width)
- Bottom nav with Protocol tab active

CONTEXT OF USE:
User is on day 5 of their Valerian protocol.
They open the app each morning to log how they slept.
The streak and progress bar motivate them to stay consistent.
They're tracking whether the herb is actually working.

CONSTRAINTS:
- Mobile-first (390px width)
- Background: gradient from #ecfdf5 to white
- Day counter: font-size 36px, font-weight 800, color #2d6a4f
- Streak badge: background #fef3c7, text #92400e
- Progress bar: height 6px, background #e5e7eb, fill #2d6a4f, rounded
- Emoji buttons: 24px, selected one has green border and slightly larger
- Sliders: green fill, gray track, green dot handle
- Check In button: background #2d6a4f, white text, 12px rounded corners
```

**v0 Prompt 7 — Paywall Modal (if time permits)**
```
Build a paywall modal overlay for the Haoma herbalist app.

PRODUCT SURFACE:
- Semi-transparent dark overlay behind modal
- White modal card (centered, 90% width, rounded corners)
- Header: "🔓 Unlock Full Access"
- Price: "€7.99/month" (large, green)
- Benefits list with checkmarks:
  ✓ Unlimited plant searches
  ✓ Full preparation guides
  ✓ Product finder with prices
  ✓ Protocol tracking & streaks
  ✓ Herb combination checker
- Primary button: "Start 7-Day Free Trial" (green, full width)
- Secondary link: "Maybe Later" (gray text, below button)
- Small print: "Cancel anytime. No commitment."

CONTEXT OF USE:
User hit the free limit (3 searches) and sees this paywall.
They need to decide if the app is worth €7.99/month.
The free trial reduces friction.

CONSTRAINTS:
- Modal: white background, 24px rounded corners, 24px padding
- Overlay: background rgba(0,0,0,0.5)
- Price: font-size 24px, color #2d6a4f
- Checkmarks: color #10b981
- Trial button: background #2d6a4f, white text, full width
- "Maybe Later": color #6b7280, no underline
```

**Deliverable:** Complete demo flow with tracking and paywall.

---

## 🗃️ Hard-Coded Demo Data

### Plants (5 for MVP)

| Plant | Symptoms | Evidence |
|-------|----------|----------|
| **Valerian** | Insomnia, anxiety, stress | Clinical |
| **Chamomile** | Anxiety, digestion, sleep | Both |
| **Ashwagandha** | Stress, energy, focus | Clinical |
| **Ginger** | Digestion, nausea, inflammation | Both |
| **Lavender** | Anxiety, sleep, headache | Both |

### Stores (4 Amsterdam locations)
Jacob Hooy, De Tuinen, Holland & Barrett, Ekoplaza — real addresses.

### Products (4 for MVP)
Mix of capsules, tea, tincture across Holland & Barrett, Jacob Hooy, De Tuinen, Bol.com.

---

## 🏆 Demo Script (2 min pitch)

1. **Open app** → "What's bothering you?" → Type: "I can't sleep and I feel anxious"
2. **Results appear** → "Haoma recommends Valerian (92% match) — AI-powered"
3. **Tap Valerian** → Show Overview tab → "Description, compounds, clinical evidence"
4. **Switch to "How to Take" tab** → "HERE'S THE KILLER FEATURE — compare tea vs capsule vs tincture side by side. Dosage, timing, onset, duration. No other app does this."
5. **Switch to "Combines With"** → "Valerian + Passionflower = enhanced sleep. We warn about dangerous combos too."
6. **Product Finder** → "Find it at Jacob Hooy, 300m from here, €4.50 for tea, in stock"
7. **Start Protocol** → "Track your progress over 4 weeks with daily check-ins, streaks, symptom graphs"
8. **Show Paywall** → "Free users get 3 lookups/month. €7.99/month unlocks everything. Plus affiliate revenue from every purchase link."
9. **Close:** "Haoma — your AI herbalist in your pocket."

---

## ✅ MVP Feature Checklist

| # | Feature | Priority | Status |
|---|---------|----------|--------|
| 1 | Home + symptom input | P0 | ⬜ |
| 2 | Plant recommendation cards | P0 | ⬜ |
| 3 | Plant detail — Overview tab | P0 | ⬜ |
| 4 | Plant detail — How to Take tab | P0 | ⬜ |
| 5 | Plant detail — Combines tab | P0 | ⬜ |
| 6 | Product finder with prices | P1 | ⬜ |
| 7 | Store map (Amsterdam) | P1 | ⬜ |
| 8 | Protocol tracker + check-in | P1 | ⬜ |
| 9 | Paywall modal | P2 | ⬜ |

**P0** = Must have for demo  
**P1** = Should have (makes it compelling)  
**P2** = Nice to have (if time permits)

---

## 🚫 NOT in MVP

- User authentication (use local state)
- Real AI API calls (hard-code responses)
- Live product scraping (all pre-filled)
- Real map integration (placeholder + list)
- Navigation between screens (demo each screen separately if needed)

---

## 💡 v0 Tips

1. **Start simple** — Get the layout right first, then add details
2. **Iterate fast** — Don't rewrite the whole prompt, just say "make the button bigger" or "change the green to #2d6a4f"
3. **Use Design Mode** — For quick visual tweaks (colors, spacing), use v0's Design Mode instead of prompting
4. **Copy-paste data** — Include exact sample data in prompts so v0 doesn't invent wrong values
5. **One screen at a time** — Build each screen as a separate chat/generation, then combine later

---

*Updated: 2026-02-06 — Prompts optimized for v0 using Vercel's official framework*

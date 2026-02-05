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

## ⏱️ Build Timeline

### Phase 1: Core UI Shell (0:00 — 0:45) ⏰ 45 min

**v0 Prompt 1 — Home + Symptom Input**
```
Build a mobile-first health app called "Haoma" with a green/earth-tone theme.
Home screen with:
- Logo and tagline "Your AI Herbalist"
- Search bar: "What's bothering you?" with natural language input
- Quick symptom chips below: Sleep, Anxiety, Digestion, Energy, Pain, Focus, Immunity
- Bottom nav: Home, My Plants, Protocol, Profile
- Clean, modern, wellness-app aesthetic (think Calm meets WebMD)
```

**v0 Prompt 2 — Results + Plant Cards**
```
Plant recommendation results page. Show 3-5 plant cards in a scrollable list.
Each card:
- Plant illustration placeholder (use a leaf emoji or icon)
- Name (e.g., "Valerian") + botanical name in italic
- Match score badge (e.g., "92% match") in green
- One-line benefit: "Natural sedative for deep sleep"
- Evidence badge: "Clinical" / "Traditional" / "Both" 
- Small icons showing available forms (tea, capsule, tincture)
- Tap to expand/navigate to detail
Use shadcn Card components. Mobile-first.
```

**Deliverable:** Navigable home → results flow with static data.

---

### Phase 2: Plant Detail + Preparation Guide (0:45 — 1:30) ⏰ 45 min

**v0 Prompt 3 — Plant Detail with Tabs**
```
Plant detail page with 3 tabs: "Overview", "How to Take", "Combines With".

Overview tab:
- Plant name, botanical name, large illustration area
- Description paragraph
- Key compounds as pills/badges
- Effectiveness rating (stars or bar)
- "Start Protocol" CTA button

"How to Take" tab — THIS IS THE KEY FEATURE:
- Comparison table with columns: Form, Dosage, Preparation, When, Onset, Best For
- Rows for: Tea (🫖), Capsule (💊), Tincture (💧), Extract (🧪)
- Use real Valerian data:
  Tea: 2-3g dried root, steep 10-15 min, 1hr before bed, 30-60min onset
  Capsule: 300-600mg, swallow with water, 30min before bed, 20-45min onset
  Tincture: 1-2ml (20-40 drops), in water/sublingual, 2x daily, 15-30min onset
  Extract: 150-300mg standardized, swallow, as directed, 20-40min onset
- Side effects section with warning icon
- "Who should avoid" section

"Combines With" tab:
- Green section "✅ Synergies" with cards: "Passionflower → Enhanced sleep", "Lemon Balm → Reduced anxiety"
- Yellow section "⚠️ Cautions" with cards: "Kava → Excessive sedation risk"
- Red section "❌ Avoid" with cards: (none for Valerian, show empty state)
- "Pre-built Stacks" section: "Deep Sleep Stack: Valerian + Passionflower + Magnesium"

Use Tabs component from shadcn. Mobile-first layout.
```

**Deliverable:** Full plant detail with preparation comparison — the differentiator.

---

### Phase 3: Product Finder + Store Map (1:30 — 2:15) ⏰ 45 min

**v0 Prompt 4 — Product Finder**
```
Product finder section showing purchasable products for a plant.
List of product cards, each showing:
- Product name: "Valerian Root 500mg Capsules"
- Brand: "Holland & Barrett"  
- Price: "€12.99"
- Stock badge: green "In Stock" / yellow "Low Stock" / red "Out of Stock"
- Form icon (capsule/tea/tincture)
- Star rating (4.5 ⭐)
- Two buttons: "Buy Online" (primary) and "Find in Store" (secondary, map icon)

Include 5-6 example products across different stores:
- Holland & Barrett Valerian 500mg - €12.99 - In Stock
- Jacob Hooy Valerian Tea - €4.50 - In Stock  
- iHerb Nature's Answer Valerian - €9.95 - Online Only
- Bol.com Solgar Valerian - €16.99 - In Stock
- De Tuinen Valerian Tincture - €8.95 - Low Stock
- Ekoplaza Bio Valerian Tea - €5.49 - In Stock

Add filters: Form (All/Tea/Capsule/Tincture), Sort (Price/Rating/Distance)
Mobile-first, use shadcn components.
```

**v0 Prompt 5 — Store Map**
```
Store locator map for Amsterdam. Show a static map area (placeholder) with a list of stores below.
Each store card:
- Store name + type badge (Chain/Independent)
- Address
- Distance: "0.8 km"
- Opening hours: "Mon-Sat 9:00-18:00"
- "Products available" count badge
- "Get Directions" button

Include these real Amsterdam stores:
1. Jacob Hooy & Co — Kloveniersburgwal 12 — 0.3 km — Independent
2. De Tuinen — Kalverstraat 134 — 0.5 km — Chain
3. Holland & Barrett — Damrak 81 — 0.8 km — Chain
4. Ekoplaza — Sarphatistraat 27 — 1.2 km — Chain
5. Albert Cuyp Market (Herb stands) — Albert Cuypstraat — 1.8 km — Market

For the map area, use a placeholder div with map styling. We'll integrate Google Maps later.
```

**Deliverable:** Product cards with prices + store list with real Amsterdam locations.

---

### Phase 4: Protocol + Polish (2:15 — 3:00) ⏰ 45 min

**v0 Prompt 6 — Start Protocol + Daily Check-in**
```
Protocol tracking screen. Two states:

State 1 - Setup:
- "Start Your Valerian Protocol"
- Selected form: Capsule (with option to change)
- Dosage: 300mg (auto-filled from preparation guide)
- Duration selector: 2 weeks / 4 weeks / 8 weeks
- Symptoms to track (checkboxes): Sleep Quality, Time to Fall Asleep, Night Waking, Morning Freshness
- "Start Protocol" button

State 2 - Daily Check-in:
- Day counter: "Day 5 of 28" with progress bar
- Streak: "🔥 5 days"
- "How do you feel today?" — 5 emoji scale (😫😕😐🙂😊)
- Symptom sliders (1-10) for each tracked symptom
- Notes text area
- "Check In" button
- Mini graph showing trend over days (simple line chart)

Mobile-first, warm/green tones, encouraging copy.
```

**v0 Prompt 7 — Final Polish**
```
Add to the app:
1. Onboarding splash: "Welcome to Haoma 🌿" with 3 carousel slides:
   - "Tell us your symptoms"
   - "Get personalized plant recommendations" 
   - "Track your healing journey"
2. Paywall modal (triggered on 4th search):
   - "Unlock Full Access"
   - Price: €7.99/month
   - Benefits list: Unlimited searches, Preparation guides, Product finder, Protocol tracking
   - "Start Free Trial" button
   - "Maybe Later" link
3. Legal disclaimer footer on all screens:
   "⚠️ Educational only. Not medical advice. Consult your healthcare provider."
```

**Deliverable:** Complete demo flow from onboarding to daily tracking.

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

Each plant gets full data: 4 preparation forms, 2-3 combinations, side effects, contraindications.

### Stores (5 Amsterdam locations)
Pre-filled with real addresses, approximate coordinates, real opening hours.

### Products (6-8 per plant)
Mix of Holland & Barrett, Jacob Hooy, iHerb, Bol.com, De Tuinen, Ekoplaza.
Real-ish prices based on actual market rates.

---

## 🏆 Demo Script (2 min pitch)

1. **Open app** → "What's bothering you?" → Type: "I can't sleep and I feel anxious"
2. **Results appear** → "Haoma recommends Valerian (92% match) — show the AI analysis"
3. **Tap Valerian** → Show overview → **Switch to "How to Take" tab** → "Here's the killer feature — compare tea vs capsule vs tincture side by side"
4. **Show "Combines With"** → "Valerian + Passionflower = enhanced sleep. We warn about dangerous combos too."
5. **Product Finder** → "Find it at Jacob Hooy, 300m from here, €4.50 for tea, in stock"
6. **Start Protocol** → "Track your progress over 4 weeks with daily check-ins"
7. **Paywall** → "Free users get 3 lookups/month. €7.99 unlocks everything."
8. **Close:** "Haoma — your AI herbalist in your pocket. Monetized through subscriptions + affiliate revenue from every purchase link."

---

## ✅ MVP Feature Checklist

| # | Feature | Priority | Status |
|---|---------|----------|--------|
| 1 | Home + symptom input | P0 | ⬜ |
| 2 | Plant recommendation cards | P0 | ⬜ |
| 3 | Plant detail — Overview | P0 | ⬜ |
| 4 | Plant detail — Preparation guide | P0 | ⬜ |
| 5 | Plant detail — Combinations | P0 | ⬜ |
| 6 | Product finder with prices | P1 | ⬜ |
| 7 | Store map (Amsterdam) | P1 | ⬜ |
| 8 | Protocol tracker + check-in | P1 | ⬜ |
| 9 | Paywall modal | P2 | ⬜ |
| 10 | Onboarding carousel | P2 | ⬜ |

**P0** = Must have for demo  
**P1** = Should have (makes it compelling)  
**P2** = Nice to have (if time permits)

---

## 🚫 NOT in MVP

- User authentication (use local state)
- Real AI API calls (hard-code responses, show the prompt structure)
- Live product scraping (all pre-filled)
- Real map integration (placeholder + store list)
- Push notifications
- Social features
- Full gamification system

---

## 📋 Pre-Hackathon Prep (Feb 5-6)

- [ ] Research exact dosage data for 5 plants (clinical sources)
- [ ] Collect real product data from Holland & Barrett NL, Jacob Hooy, iHerb
- [ ] Get real Amsterdam store addresses + hours
- [ ] Prepare plant combination data (synergies, cautions, avoids)
- [ ] Draft all v0 prompts (refine based on v0 capabilities)
- [ ] Practice the 2-minute demo pitch
- [ ] Test v0 credit usage to budget the $10 credits across 7 prompts

---

*Last updated: 2026-02-05*

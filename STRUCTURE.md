# 🏗️ Haoma — App Structure

## Core User Flow

```
[Symptom Input] → [AI Analysis] → [Plant Recommendations] → [Plant Detail]
                                                                   ↓
                                              [Preparation Guide] ← → [Combinations]
                                                                   ↓
                                              [Product Finder] → [Store Map]
                                                                   ↓
                                              [Start Protocol] → [Daily Check-in]
```

---

## Screens

### 1. 🏠 Home / Symptom Input
- Search bar: "What's bothering you?" (natural language)
- Quick symptom chips: Sleep, Anxiety, Digestion, Energy, Pain, Focus, Immunity
- Recent searches / saved protocols
- Daily check-in reminder banner

### 2. 🌿 Plant Recommendations (AI Results)
- List of 3-5 recommended plants, ranked by relevance
- Each card shows:
  - Plant name + botanical name
  - Match score (e.g., 92% match)
  - Key benefit tagline
  - Primary form icon (tea/capsule/tincture)
  - "Evidence" badge (Traditional / Clinical / Both)
- Filter: by form, evidence level, availability

### 3. 📋 Plant Detail Card
Tabbed layout:

#### Tab: Overview
- Plant image (illustration style)
- Description (2-3 sentences)
- Key compounds (e.g., "Valerenic acid, isovaleric acid")
- Traditional uses vs modern research
- Effectiveness rating (based on clinical evidence)

#### Tab: How to Take (PREPARATION GUIDE)
Comparison table across forms:

| Form | Dosage | How to Prepare | When to Take | Onset | Duration | Best For |
|------|--------|---------------|--------------|-------|----------|----------|
| 🫖 Tea | 2-3g dried root | Steep 10-15 min, hot water | 1hr before bed | 30-60 min | 4-6 hrs | Mild sleep issues |
| 💊 Capsule | 300-600mg | Swallow with water | 30 min before bed | 20-45 min | 6-8 hrs | Consistent dosing |
| 💧 Tincture | 1-2ml (20-40 drops) | In water or under tongue | 2x daily | 15-30 min | 3-4 hrs | Quick absorption |
| 🧪 Extract | 150-300mg (standardized) | Swallow with water | As directed | 20-40 min | 6-8 hrs | Maximum potency |

- ⚠️ Side effects & contraindications
- 🚫 Who should avoid (pregnancy, medications, conditions)
- 📅 Recommended duration (e.g., "2-4 weeks for full effect")

#### Tab: Combines With
- ✅ **Synergies:** Plants that enhance this one
  - e.g., "Valerian + Passionflower → Enhanced sleep quality"
  - e.g., "Valerian + Lemon Balm → Reduced anxiety + better sleep"
- ⚠️ **Cautions:** Combinations to be careful with
  - e.g., "Valerian + Kava → Excessive sedation"
- ❌ **Avoid:** Dangerous interactions
  - e.g., "St. John's Wort + SSRIs → Serotonin syndrome risk"
  - e.g., "St. John's Wort + Birth control → Reduced effectiveness"
- 💡 **Pre-built Stacks:** Curated combinations for goals
  - "Deep Sleep Stack: Valerian + Passionflower + Magnesium"
  - "Calm Focus Stack: L-Theanine + Ashwagandha + Bacopa"
  - "Gut Reset Stack: Slippery Elm + Chamomile + Ginger"

### 4. 🛒 Product Finder
- Products for the selected plant, across forms
- Each product card:
  - Product name + brand
  - Form (capsule/tea/tincture/extract)
  - Price (€)
  - Store name + logo
  - Stock status: 🟢 In Stock / 🟡 Low Stock / 🔴 Out of Stock / ⚪ Check Online
  - [Buy Online] button (affiliate link)
  - [Directions] button (maps link to nearest store)
- Sort by: price, rating, distance
- Filter by: form, store, in-stock only

### 5. 🗺️ Store Map (Amsterdam)
- Map with pins for herbal/supplement stores
- Store list with:
  - Name, address, distance
  - Opening hours
  - Which recommended products they carry
- Stores: Jacob Hooy, De Tuinen, Holland & Barrett, Ekoplaza, Albert Cuyp market, local apotheek

### 6. 📊 Protocol Tracker
- Active protocol card (plant + form + dosage + duration)
- Daily check-in: "How do you feel today?" (1-5 scale + symptom tracking)
- Progress graph (symptom severity over time)
- Streak counter (days on protocol)
- Notes field for observations

### 7. 🏆 Gamification (Post-MVP)
- 🌱 Plant Collector: Unlock plants you've tried
- 🔥 Streak badges: 7-day, 30-day, 90-day
- 🧪 A/B Mode: Compare two remedies head-to-head
- 📈 Health score trending
- 🏅 Achievements: "Herbalist Apprentice", "Plant Master", etc.

---

## Data Structure

### Plants
```typescript
interface Plant {
  id: string;
  name: string;                    // "Valerian"
  botanicalName: string;           // "Valeriana officinalis"
  image: string;                   // illustration URL
  description: string;
  keyCompounds: string[];          // ["Valerenic acid", "Isovaleric acid"]
  symptoms: string[];              // ["insomnia", "anxiety", "stress"]
  matchScore?: number;             // AI-calculated per query
  evidenceLevel: 'traditional' | 'clinical' | 'both';
  
  preparations: Preparation[];
  combinations: Combination[];
  contraindications: string[];
  sideEffects: string[];
  avoidIf: string[];               // ["Pregnant", "Taking sedatives"]
  recommendedDuration: string;     // "2-4 weeks"
}

interface Preparation {
  form: 'tea' | 'capsule' | 'tincture' | 'extract' | 'powder' | 'oil';
  dosage: string;                  // "300-600mg"
  howToPrepare: string;            // "Steep 10-15 min in hot water"
  whenToTake: string;              // "30 min before bed"
  onsetTime: string;               // "20-45 min"
  duration: string;                // "6-8 hrs"
  bestFor: string;                 // "Consistent dosing"
}

interface Combination {
  plantId: string;
  plantName: string;
  type: 'synergy' | 'caution' | 'avoid';
  effect: string;                  // "Enhanced sleep quality"
  notes?: string;
}
```

### Products
```typescript
interface Product {
  id: string;
  plantId: string;
  name: string;                    // "Valerian Root 500mg"
  brand: string;                   // "Holland & Barrett"
  form: 'tea' | 'capsule' | 'tincture' | 'extract' | 'powder' | 'oil';
  price: number;                   // 12.99
  currency: string;                // "EUR"
  url: string;                     // product page (affiliate link)
  store: Store;
  stockStatus: 'in_stock' | 'low_stock' | 'out_of_stock' | 'online_only';
  rating?: number;                 // 4.5
  reviewCount?: number;
}

interface Store {
  id: string;
  name: string;                    // "Holland & Barrett"
  type: 'chain' | 'independent' | 'online';
  address?: string;
  lat?: number;
  lng?: number;
  openingHours?: string;
  website: string;
  affiliateProgram?: string;       // "iherb" | "bolcom" | "amazon"
}
```

### Protocols & Tracking
```typescript
interface Protocol {
  id: string;
  userId: string;
  plantId: string;
  form: string;
  dosage: string;
  startDate: Date;
  targetDuration: number;          // days
  symptoms: string[];              // tracked symptoms
  active: boolean;
}

interface DailyCheckIn {
  id: string;
  protocolId: string;
  date: Date;
  overallFeeling: 1 | 2 | 3 | 4 | 5;
  symptomScores: Record<string, number>;  // { "insomnia": 3, "anxiety": 2 }
  notes?: string;
  tookRemedy: boolean;
}
```

### Pre-built Stacks
```typescript
interface HerbStack {
  id: string;
  name: string;                    // "Deep Sleep Stack"
  goal: string;                    // "Improve sleep quality"
  plants: {
    plantId: string;
    form: string;
    dosage: string;
    timing: string;
  }[];
  duration: string;                // "2-4 weeks"
  notes: string;
}
```

---

## AI Prompt Structure

### Symptom Analysis Prompt
```
You are Haoma, an AI herbalist. Given user symptoms, recommend 3-5 medicinal plants.

For each plant, provide:
- Name and botanical name
- Match score (0-100) based on symptom relevance
- Primary benefit for the described symptoms
- Evidence level (traditional, clinical, or both)
- Recommended form for this specific case
- Key safety considerations

User symptoms: "{user_input}"

Respond in JSON format matching the Plant interface.
Important: Include disclaimers. You are not a doctor. This is educational.
```

### Combination Check Prompt
```
Check the safety of combining these herbs: {herb_list}

For each pair, classify as:
- synergy: they enhance each other
- caution: use carefully, monitor effects  
- avoid: dangerous interaction

Include specific effects and any relevant clinical evidence.
```

---

## Revenue Model

### Subscription Tiers
| Feature | Free | Premium (€7.99/mo) |
|---------|------|---------------------|
| Symptom lookups | 3/month | Unlimited |
| Plant details | Basic | Full (preparations, combos) |
| Product finder | ❌ | ✅ |
| Store map | ❌ | ✅ |
| Protocol tracking | 1 active | Unlimited |
| Pre-built stacks | Preview only | Full access |
| Combination checker | ❌ | ✅ |

### Additional Revenue
- **Affiliate links:** iHerb (5-10%), Bol.com (3-8%), Amazon.nl (3-7%)
- **Local shop partnerships:** Featured placement for Amsterdam stores
- **Data insights (future):** Anonymized trend data for supplement brands

---

## Legal

⚠️ **Mandatory disclaimer on every screen:**
> "Haoma provides educational information about traditional and herbal remedies. This is not medical advice. Always consult a healthcare professional before starting any supplement. Do not replace prescribed medication without consulting your doctor."

- Terms of Service: No liability for health outcomes
- GDPR compliant: EU data storage, user data deletion
- Health claims: Compliant with EU regulations (no cure/treat claims)

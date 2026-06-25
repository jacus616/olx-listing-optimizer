---
name: olx-listing-optimizer
description: >
  Generates optimized, bot-safe OLX.pl listing descriptions for electronics, consoles, and gadgets.
  Uses keyword-rich titles (70 char limit), structured descriptions with technical specs,
  and avoids moderator trigger words that send listings to manual review.
  Three modes: (1) Create new listing, (2) Audit existing listing + score 0-100,
  (3) A/B title variants, (4) Market price calculator.
  Triggers on "napisz opis na OLX", "opis na OLX", "zoptymalizuj ogłoszenie OLX",
  "stwórz opis ogłoszenia", "OLX opis", "opis pod algorytmy", "sprawdź ogłoszenie",
  "audyt opisu", "popraw opis", "warianty tytułu", "jaka cena", "ile wystawić",
  "cena rynkowa", or any task involving writing/improving/pricing a product listing for OLX.pl.
---

# OLX Listing Optimizer

## Purpose
Generate product listing descriptions optimized for OLX.pl search algorithm and safe from automated moderation flags. Maximizes visibility (search ranking) while avoiding manual review triggers.

## Trigger Conditions
- User mentions "OLX", "opis ogłoszenia", "napisz opis", "zoptymalizuj"
- User wants to create or improve a product listing
- User wants SEO-friendly product descriptions for Polish market

## Input Required
Ask the user for (if not provided):
1. **Product name/model** — exact name, color, variant
2. **Condition** — new/used, any defects
3. **What's included** — box, cables, accessories
4. **Key selling points** — any modifications, upgrades, special features
5. **Price intent** — fixed or negotiable
6. **Shipping preference** — pickup only, shipping available, InPost/OLX delivery
7. **Category** — electronics, consoles, phones, etc.

## Workflow

### Step 1: Research Product Specs
If the user provides a specific product model, search for detailed specs:
```
web_search("<model> specifications specs 2025 2026")
web_search("<model> opinie parametry techniczne")
```
Extract: processor, RAM, display, battery, storage, connectivity, dimensions, weight.

### Step 2: Research Comparable Products
Find similar products to reference in the description for search visibility:
```
web_search("<model> similar alternatives competitor handheld console")
```
Identify: comparable models, common search terms buyers use.

### Step 3: Generate Title (max 70 chars)

**Rules:**
- Include: brand + model + key spec + condition/state
- NO: Caps Lock (except brand names), emojis, exclamation marks, words like "okazja", "hit", "super"
- Format: `[Brand] [Model] [Key Spec] [State/Color]`
- Must contain searchable keywords buyers actually use

**Examples:**
- `Retroid Pocket Flip 2 8GB RAM skonfigurowany do gry`
- `PlayStation 4 Slim 1TB czarny stan idealny z gierkami`
- `iPhone 13 128GB biały bez rys idealny stan`

### Step 4: Generate Description

**Structure (in order):**

```
[HOOK — 1 sentence, product name + key benefit + condition]

[COMPARISON/SIMILARITY — reference to popular known products for search visibility]
Format: "TEN SAM PROCESOR CO [Popular Model]" or "PODOBNA KONSTRUKCJA DO [Known Product]"

[TECHNICAL SPECS — bullet list, 5-10 items]
- Processor/Chipset
- RAM / Storage
- Display size & type
- Battery
- Connectivity
- Dimensions/Weight
- Color/Variant
- Any special features

[CONDITION — honest, specific]
- Physical state
- Functional state
- Any modifications/upgrades
- Known issues (if any — honesty builds trust)

[WHAT'S INCLUDED — complete list]
- Main device
- Accessories
- Box
- Cables

[SALE TERMS]
- Price negotiability
- Shipping options
- Location
- Call to action
```

**Length target:** 400-1000 characters (sweet spot for OLX algorithm)

### Step 5: Safety Check — Bot/MODERATION Avoidance

**NEVER include these in OLX listings:**

| Forbidden | Reason | Safe Alternative |
|-----------|--------|------------------|
| "okazja", "hit", "super", "ekskluzywne" | Trigger spam filter | neutral description |
| Excessive caps lock | Triggers moderation | Normal capitalization |
| "kup teraz", "ostatnia sztuka" | Pressure tactics = spam | "dostępne w ograniczonej ilości" (if true) |
| Emojis in title | Triggers filter | No emojis in title |
| "sprzedam szybko", "pilnie" | Suggests scam | Omit |
| Phone numbers/email in description | Triggers filter | Use OLX messaging |
| "wymiana", "zamienię" without clear intent | May trigger WTT filter | Only if actually offering trade |
| Excessive punctuation "!!!" | Triggers filter | Single periods |
| URLs to external sites | Triggers filter | No external links |
| "najlepsza cena", "najtaniej" | Unverifiable claim | Omit |
| Repetitive keyword stuffing | Detected by NLP | Natural language, keywords once |

**ALWAYS include:**
- Accurate category-specific technical details
- Honest condition description
- Complete package list
- Location info
- Natural Polish language (not machine-translated)

### Step 6: Algorithm Optimization (SEO for OLX)

**Title keywords** — most important for search ranking. Include:
- Brand name (spelled correctly)
- Model number/name
- Key specs (RAM, storage, color)
- Condition (nowy/używany, stan)

**Description keywords** — secondary for search. Include:
- Alternative names/brands (if relevant)
- Compatible systems/games ("emuluje PS2", "działa z Nintendo Switch")
- Use cases ("do gier", "do podróży", "dla dzieci")
- Technical terms buyers search for

**Natural keyword density** — use each keyword 1-2 times maximum. OLX uses NLP (word embeddings) — synonyms and related terms help, but stuffing hurts.

### Step 7: Output Format

Output the result as a ready-to-copy text with clear sections:

```
TYTUŁ (max 70 znaków):
[title]

OPIS:
[description]
```

Save to file if user requests: `/home/hermes/workspace/olx_opis_[product_name].txt`

## Supported Product Categories

### Gaming Consoles & Handhelds
- Retro consoles (PS1, PS2, SNES, N64, etc.)
- Modern consoles (PS4, PS5, Switch, Xbox)
- Handhelds (Retroid, Anbernic, AYN, Miyoo, Steam Deck)
- Key specs: processor, RAM, screen, battery, emulation capability

### Phones & Tablets
- Key specs: model, storage, RAM, screen size, battery, condition grade
- Include: IMEI status, battery health %, original accessories

### Computers & Laptops
- Key specs: CPU, RAM, GPU, storage type/screen, OS
- Include: battery cycle count (laptops), any upgrades

### 3D Printers
- Key specs: model, build volume, resolution, LCD condition
- Include: any modifications, spare parts included

### General Electronics
- Adapt the structure to the specific product type
- Focus on specs buyers actually search for

## Key Pitfalls

1. **Title over 70 chars** — OLX truncates, looks unprofessional. Count carefully.
2. **Vague descriptions** — "good condition" means nothing. Be specific: "no scratches on screen, battery holds 80% capacity"
3. **Missing location context** — always include city/region
4. **Forgetting shipping info** — buyers filter by shipping availability
5. **Copy-paste templates** — OLX detects duplicate descriptions across listings. Each description must be unique.
6. **Not checking current market terms** — product names evolve (e.g., "Retroid Pocket Flip 2" not just "Flip 2")
7. **Ignoring category-specific search terms** — consoles: buyers search by emulation capability; phones: by storage size and color
8. **Mixing into wrong repo** — this skill lives in `jacus616/olx-listing-optimizer`, NOT in Kleinanzeige repo or any other project repo. Each project = separate repo.

## Advanced Techniques

### For High-Value Items (>500 PLN)
- Add "faktura/paragon" mention if available
- Mention warranty status if applicable
- Include reason for selling (builds trust)

### For Retro/Collectible Items
- Reference specific games it can run (for consoles)
- Mention rarity if genuinely rare
- Include original region/PAL/NTSC if relevant

### For Bundled Listings
- List each item separately with individual condition
- State clearly what's NOT included
- Price as bundle but mention flexibility

## Feature 1: Adut Istniejącego Ogłoszenia (Audit Mode)

**Trigger:** User sends OLX listing URL and asks to check/improve it. Keywords: "sprawdź ogłoszenie", "audyt opisu", "popraw opis", "czy ten opis jest ok", "zoptymalizuj to ogłoszenie".

### Workflow

#### Step A: Fetch the Listing
Use browser to open the OLX listing URL and extract:
- Current title
- Current description
- Price
- Category
- Photos (alt text for context)

#### Step B: Analyze Against Checklist

**Title audit:**
- [ ] Length ≤ 70 chars?
- [ ] Contains brand + model?
- [ ] Contains key specs (RAM, storage, color)?
- [ ] No trigger words (okazja, hit, super, caps lock, emojis)?
- [ ] Contains searchable keywords buyers use?

**Description audit:**
- [ ] Length 400-1000 chars?
- [ ] Structured with headers/bullets?
- [ ] Includes technical specs?
- [ ] Honest condition description?
- [ ] Complete package list?
- [ ] Location mentioned?
- [ ] Shipping options mentioned?
- [ ] No trigger words?
- [ ] No phone numbers/URLs?
- [ ] Natural Polish language?

**SEO audit:**
- [ ] Key search terms from title appear in description?
- [ ] Compatible systems/games mentioned?
- [ ] Use cases included?
- [ ] No keyword stuffing?

#### Step C: Generate Score (0-100)

```
SCORE BREAKDOWN:
- Title quality: /20
  - Contains brand+model: +5
  - Contains key specs: +5
  - Under 70 chars: +5
  - No trigger words: +5
- Description quality: /40
  - Proper length (400-1000): +10
  - Structured format: +10
  - Technical specs included: +10
  - Honest condition: +5
  - Complete package list: +5
- SEO: /25
  - Keywords in title: +10
  - Keywords in description: +5
  - Compatible systems mentioned: +5
  - Use cases included: +5
- Safety: /15
  - No trigger words: +5
  - No off-platform contact: +5
  - No competitor links: +5
```

#### Step D: Output Format

```
AUDYT OGŁOSZENIA OLX
=====================

LINK: [url]

TYTUŁ (X/70 znaków):
[current title]
[✅/❌] [checklist items]

OPIS (X znaków):
[✅/❌] [checklist items]

SCORE: X/100
- Tytuł: X/20
- Opis: X/40
- SEO: X/25
- Bezpieczeństwo: X/15

GŁÓWNE PROBLEMY:
1. [problem + fix suggestion]
2. [problem + fix suggestion]

SUGEROWANE POPRAWKI:
TYTUŁ: [improved title]
OPIS: [improved description — full text]
```

### Pitfalls for Audit Mode
1. **Don't be vague** — "add more specs" is useless. Say "add: Snapdragon 865, 8GB RAM, 5000mAh battery"
2. **Don't rewrite everything if score >75** — only fix what's broken
3. **Respect seller's style** — if description is already good, don't change it just to change it
4. **Check photos too** — if description says "stan idealny" but photos show scratches, flag it

---

## Feature 2: A/B Warianty Tytułów

**Trigger:** User wants multiple title options to test. Keywords: "warianty tytułu", "A/B tytuł", "który tytuł lepszy", "testuj tytuły".

### Workflow

Generate 3-5 title variants with different keyword arrangements:

**Variant strategies:**
1. **Brand-first** (most common): `Retroid Pocket Flip 2 8GB RAM Ice Blue`
2. **Spec-first** (for search): `Konsola przenośna 8GB RAM Snapdragon 865 gotowa do gry`
3. **Condition-first** (for buyers filtering by state): `Retroid Pocket Flip 2 stan idealny kompletny zestaw`
4. **Use-case first** (for gift/emotion searches): `Do gier retro i nowoczesnych 5.5" AMOLED 8GB RAM`
5. **Comparison first** (for brand-aware buyers): `Jak AYN Thor ale lepiej — Flip 2 8GB RAM Ice Blue`

### Rules for each variant
- Max 70 chars
- No trigger words
- Contains at least 2 searchable keywords
- Unique angle/approach

### Output Format

```
WARIANTY TYTUŁÓW (A/B TEST)
============================

1. [title] (X znaków)
   → Keywords: [list]
   → Angle: [brand/spec/condition/use-case/comparison]

2. [title] (X znaków)
   → Keywords: [list]
   → Angle: [angle]

3. [title] (X znaków)
   → Keywords: [list]
   → Angle: [angle]

ZALECENIE:
Najlepszy do testu: wariant X
Powód: [rationale]
```

### Pitfalls for A/B Titles
1. **Don't generate too many** — 3-5 is enough, more causes analysis paralysis
2. **Each must be genuinely different** — not just word shuffle, different angle
3. **Track results** — suggest user notes which variant gets more views after 7 days

---

## Feature 3: Integracja z Aktualnymi Cenami Rynkowymi

**Trigger:** User wants pricing suggestion. Keywords: "jaka cena", "ile wystawić", "cena rynkowa", "kalkulator ceny", "czy opłaca się".

### Workflow

#### Step A: Research Market Prices

**OLX.pl prices:**
```
web_search("<model> cena OLX.pl 2026 używany")
```
Parse results to find price range and median.

**Vinted.pl prices:**
```
web_search("<model> Vinted.pl cena 2026")
```

**Allegro (fallback):**
```
web_search("<model> Allegro używany cena 2026")
```

#### Step B: Calculate Recommended Price

```
MARKET DATA:
- OLX.pl: min=X zł, median=Y zł, max=Z zł
- Vinted.pl: min=X zł, median=Y zł, max=Z zł
- Base price = LOWER(OLX median, Vinted median)

PRICING STRATEGIES:
1. SZYBKA SPRZEDAŻ (quick sale): base × 0.85
2. STANDARDOWA: base × 1.0
3. CIERPLIWA (patient): base × 1.15
4. Z NEGOCJACJĄ: base × 1.2 (pozostawia miejsce na obniżkę ~15%)

For listings with "do negocjacji":
- Suggested start: base × 1.15
- Expected final: base × 0.95-1.0
- Floor (minimum accept): base × 0.8
```

#### Step C: Factor in Condition & Completeness

| Factor | Price Adjustment |
|--------|-----------------|
| Complete set (box, cables, manual) | +15-25% |
| Missing box | -10% |
| Missing cables | -5% |
| Missing controller | -10-15% |
| Visible cosmetic damage | -10-20% |
| Modified (root, overclock, custom firmware) | +5-15% (niche buyers) |
| Rare color/edition | +10-30% |
| Bundle (multiple items) | -10-15% per item vs individual |

#### Step D: Output Format

```
KALKULATOR CENY
================

PRODUKT: [model]
STAN: [condition]
KOMPLETNOŚĆ: [complete/partial]

CENY RYNKOWE:
- OLX.pl: X-Y zł (median: Z zł)
- Vinted.pl: X-Y zł (median: Z zł)
- Cena bazowa: Z zł (LOWER of medians)

ZALECANA CENA STARTOWA: X zł
- Szybka sprzedaż: X zł
- Standardowa: X zł
- Z negocjacją: X zł (floor: X zł)

UWAGI:
- [any factors affecting price]
- [seasonal demand note if relevant]
- [competing listings count if known]

MARŻA:
- Przy cenie X zł, koszt zakupu Y zł → zysk: Z zł (W%)
- Koszt wysyłki: 7.5€ (~32 zł) — wlicz w cenę lub daj "darmowa wysyłkę"
```

### Pitfalls for Pricing
1. **Don't suggest below purchase cost** — always verify the math makes sense for reseller
2. **Don't use international prices** — Polish market has different pricing (often higher for retro)
3. **Check competing listings count** — if 50+ similar listings, price competitively
4. **Seasonal awareness** — consoles sell better in Nov-Dec (gifts) and Jun-Aug (summer holidays)
5. **Don't forget shipping** — if buyer pays, include it in margin calculation

---

## Output Language
Always Polish (pl). Use natural Polish phrasing — not translated English. Technical terms can stay in English if that's how Poles search for them (e.g., "Snapdragon 865", "Hall Effect sticks", "AMOLED").

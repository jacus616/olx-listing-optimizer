---
name: olx-listing-optimizer
description: >
  Generates optimized, bot-safe OLX.pl listing descriptions for electronics, consoles, and gadgets.
  Uses keyword-rich titles (70 char limit), structured descriptions with technical specs,
  and avoids moderator trigger words that send listings to manual review.
  Triggers on "napisz opis na OLX", "opis na OLX", "zoptymalizuj ogłoszenie OLX",
  "stwórz opis ogłoszenia", "OLX opis", "opis pod algorytmy", or any task involving
  writing/improving a product listing for OLX.pl.
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

## Output Language
Always Polish (pl). Use natural Polish phrasing — not translated English. Technical terms can stay in English if that's how Poles search for them (e.g., "Snapdragon 865", "Hall Effect sticks", "AMOLED").

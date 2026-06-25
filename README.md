# OLX Listing Optimizer

Bot-safe SEO description generator for OLX.pl listings. Creates optimized titles and descriptions that rank well in OLX search while avoiding automated moderation triggers.

## What it does

- Generates keyword-rich titles (70 char limit)
- Creates structured descriptions with technical specs
- Avoids moderation trigger words (spam, urgency, off-platform contact)
- Optimized for OLX's NLP-based search algorithm

## Usage

Load the skill and ask to write an OLX description for any product:

```
"napisz opis na OLX dla Retroid Pocket Flip 2"
"stwórz ogłoszenie OLX dla PS4 Slim 1TB"
"zoptymalizuj opis na OLX dla iPhone 13"
```

## Skill structure

```
.
├── SKILL.md                          # Main skill definition
└── references/
    ├── moderation-safe-words.md      # Trigger words to avoid + safe alternatives
    └── listing-templates.md          # Templates by product category
```

## Supported categories

- Gaming handhelds (Retroid, Anbernic, AYN, Miyoo, Steam Deck)
- Retro consoles (PS1/2/3, SNES, N64, GameCube, Dreamcast)
- Modern consoles (PS4, PS5, Switch, Xbox)
- Phones & tablets
- 3D printers
- General electronics

## Key rules

1. **Title**: brand + model + key spec + condition (max 70 chars)
2. **Description**: 400-1000 chars, structured with headers and bullet points
3. **No trigger words**: okazja, hit, pilnie, caps lock, phone numbers, URLs
4. **Natural language**: Polish phrasing, not machine-translated
5. **Unique per listing**: never copy-paste identical descriptions

## Requirements

- Hermes Agent with skill system
- web_search for product specs research

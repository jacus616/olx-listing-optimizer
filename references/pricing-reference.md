# Pricing Calculator — Reference Data

## Polish Market Pricing Sources

### Priority order
1. **OLX.pl** — best for modern items (PS4/5, Switch, phones, laptops)
2. **Vinted.pl** — best for retro (PS1/2, SNES, N64, GBA, DS)
3. **Allegro** — use only when OLX + Vinted return no results

### Search patterns for price research
```
"<model> cena OLX.pl 2026"
"<model> używany cena OLX"
"<model> Vinted.pl cena"
"<model> Allegro używany"
```

### Price extraction from search results
- OLX: prices in format `X XXX zł` or `X zł`
- Vinted: prices in format `XX zł`
- Filter out: accessories, parts-only, "za sztukę" listings
- Take median of 5-10 comparable listings

## Condition Grades (Polish market standard)

| Grade | Description | Price vs "stan idealny" |
|-------|-------------|------------------------|
| Nowy | Sealed, never used | 100-120% |
| Stan idealny | No signs of use, looks new | 100% (baseline) |
| Bardzo dobry | Minor signs of use, fully functional | 85-95% |
| Dobry | Visible wear, everything works | 70-85% |
| Używany | Heavy wear, functional | 55-70% |
| Uszkodzę | Not working / parts only | 20-40% |

## Completeness Adjustments

| What's missing | Price reduction |
|----------------|-----------------|
| Original box | -10% |
| Power adapter/charger | -8% |
| Cables (AV/USB/HDMI) | -5% |
| Controller (console) | -10-15% |
| Manual | -3% |
| Games (if bundled) | Add 30-50% of game value |

## Seasonal Demand

| Period | Demand | Price adjustment |
|--------|--------|------------------|
| November-December (gift season) | High | +10-20% |
| June-August (summer/holidays) | Medium-High | +5-10% |
| January-February (post-holiday) | Low | -5-10% |
| March-May | Medium | Baseline |

## Shipping Cost Reference

| Method | Cost | Notes |
|--------|------|-------|
| InPost Paczkomat | 12-15 zł | Most common, buyer prefers |
| DHL Paket | ~32 zł (7.5€) | Kleinanzeige standard |
| Poczta Polska | 10-18 zł | Cheapest, slowest |
| OLX Delivery | Varies | Platform-handled |
| Odbiór osobisty | 0 zł | Preferred for local |

## Margin Targets

| Scenario | Target margin |
|----------|--------------|
| Quick sale (need cash) | 15-20% |
| Standard resale | 25-35% |
| Patient (can wait) | 35-50% |
| Rare/collectible | 50-100%+ |

## When to Promote (paid boost)

| Listing price | Promote if | Expected ROI |
|---------------|-----------|--------------|
| <100 zł | Rarely | Low ROI |
| 100-300 zł | If <5 competing listings | Medium ROI |
| 300-500 zł | If <10 competing listings | Good ROI |
| >500 zł | Usually worth it | High ROI |

# OLX Listing Optimizer

Generator opisów ogłoszeń na OLX.pl — zoptymalizowany pod algorytmy wyszukiwania i bezpieczny dla automatycznej moderacji.

## Co robi

- Tworzy tytuły z słowami kluczowymi (limit 70 znaków)
- Generuje strukturalne opisy ze specyfikacją techniczną
- Unika słów triggerujących moderację (spam, presja, kontakt poza platformą)
- Zoptymalizowany pod algorytm NLP OLX

## Użycie

Wczytaj skill i poproś o opis na OLX dla dowolnego produktu:

```
"napisz opis na OLX dla Retroid Pocket Flip 2"
"stwórz ogłoszenie OLX dla PS4 Slim 1TB"
"zoptymalizuj opis na OLX dla iPhone 13"
```

## Struktura skilla

```
.
├── SKILL.md                          # Definicja skilla
└── references/
    ├── moderation-safe-words.md      # Słowa do unikania + bezpieczne alternatywy
    └── listing-templates.md          # Szablony per kategoria produktu
```

## Obsługiwane kategorie

- Konsolki przenośne (Retroid, Anbernic, AYN, Miyoo, Steam Deck)
- Konsole retro (PS1/2/3, SNES, N64, GameCube, Dreamcast)
- Konsole nowoczesne (PS4, PS5, Switch, Xbox)
- Telefony i tablety
- Drukarki 3D
- Elektronika ogólna

## Główne zasady

1. **Tytuł**: marka + model + kluczowa specyfikacja + stan (max 70 znaków)
2. **Opis**: 400-1000 znaków, strukturalny z nagłówkami i listami
3. **Bez słów triggerujących**: okazja, hit, pilnie, caps lock, numery telefonów, URL-e
4. **Naturalny język**: polski, nie maszynowe tłumaczenie
5. **Unikalne ogłoszenia**: nigdy nie kopiuj identycznego opisu

## Wymagania

- Hermes Agent z systemem skilli
- web_search do researchu specyfikacji produktu

# Canadian Coin Database

**The most comprehensive open dataset of Royal Canadian Mint coins -- 5,791 entries from 1858 to present.**

![Coins](https://img.shields.io/badge/coins-5%2C791-blue)
![Years](https://img.shields.io/badge/years-1858--2026-green)
![License](https://img.shields.io/badge/license-CC--BY--4.0-lightgrey)
![Updated](https://img.shields.io/badge/updated-March%202026-orange)

---

## Overview

A structured, machine-readable dataset of every coin issued by the Royal Canadian Mint and its predecessors, spanning 168 years of Canadian coinage. Includes circulation coins, bullion programs, numismatic issues, proof sets, and pre-Confederation provincial coinage from Newfoundland, New Brunswick, Nova Scotia, and the Province of Canada.

This dataset is maintained as part of the [Canadian Coin Heads](https://canadiancoinheads.com) project.

## Quick Stats

| Category | Count |
|----------|-------|
| Circulation | 1,110 |
| Collectible / Numismatic | 4,174 |
| Bullion | 215 |
| Subscription | 157 |
| Set | 94 |
| Roll | 41 |
| **Total** | **5,791** |

## What's Included

Each coin entry contains factual metadata sourced from the Royal Canadian Mint catalog and cross-referenced with standard numismatic references:

- **Identification**: name, year, denomination, unique ID
- **Physical specs**: metal, purity, weight (grams), diameter (mm), edge type, composition detail
- **Cataloging**: category, series, finish
- **Attribution**: monarch, obverse designer, reverse designer
- **Production**: mintage figures

## Data Format

### coins.json / coins.csv

Available in both JSON and CSV. Each entry follows this structure:

```json
{
  "id": "1-cent-1858",
  "name": "1 cent 1858",
  "year": 1858,
  "denomination": "1 cent",
  "category": "circulation",
  "metal": "copper",
  "purity": null,
  "weight_g": 4.54,
  "diameter_mm": 25.4,
  "mintage": 421000,
  "series": "Pre-Confederation Coinage",
  "monarch": "Victoria",
  "obverse_designer": "Leonard Charles Wyon",
  "reverse_designer": "Leonard Charles Wyon",
  "edge": "Plain (smooth)",
  "finish": "Circulation",
  "composition": "95% copper, 4% tin, 1% zinc",
  "country": "Canada"
}
```

### series.json

70 coin series with year ranges, metal types, and production status. See [Data Dictionary](schema/data-dictionary.md) for full field descriptions.

## Coverage

| Era | Period | Description |
|-----|--------|-------------|
| Pre-Confederation | 1858-1867 | Province of Canada (1c, 5c, 10c, 20c) |
| Provincial | 1861-1947 | Newfoundland, New Brunswick, Nova Scotia, PEI |
| Dominion / Federal | 1870-present | All federal circulation denominations (1c through $2) |
| Commemorative | 1935-present | Silver dollars, quarters, special issues |
| Bullion | 1979-present | Silver/Gold/Platinum Maple Leaf programs |
| Modern Numismatic | 1990s-present | Proof, specimen, coloured, hologram issues |

Coverage includes the complete Ottawa branch mint sovereigns (1908-1919), all decimal coinage denominations, and major commemorative programs.

## Usage

### Python

```python
import json

with open("data/coins.json") as f:
    coins = json.load(f)

# All gold coins
gold = [c for c in coins if c["metal"] == "gold"]
print(f"{len(gold)} gold coins")

# Silver Maple Leafs
sml = [c for c in coins if c["series"] == "Silver Maple Leaf"]

# Coins by monarch
victoria = [c for c in coins if c["monarch"] == "Victoria"]
```

### JavaScript

```javascript
const coins = require('./data/coins.json');

// Circulation coins with mintage data
const circulation = coins.filter(c =>
  c.category === 'circulation' && c.mintage
);

// Coins by decade
const sixties = coins.filter(c => c.year >= 1960 && c.year < 1970);
```

### pandas

```python
import pandas as pd

df = pd.read_csv("data/coins.csv")
df.groupby("metal")["mintage"].describe()
```

## Citation

If you use this dataset in research, publications, or applications, please cite:

```
Canadian Coin Database. (2026). Canadian Coin Heads.
Available at: https://github.com/Robby955/canadian-coin-database
Website: https://canadiancoinheads.com
```

## Related

- [Canadian Coin Heads](https://canadiancoinheads.com) -- Browse the full catalog with images, melt values, and series guides
- [iOS App](https://apps.apple.com/app/canadian-coin-heads/id6740244078) -- AI-powered coin identification on iPhone

## License

This dataset is released under the [Creative Commons Attribution 4.0 International License](LICENSE) (CC-BY-4.0).

You are free to use, share, and adapt this data for any purpose, including commercial use, provided you give appropriate attribution.

## Contributing

Found an error? Missing a coin? Please [open an issue](https://github.com/Robby955/canadian-coin-database/issues) with:

- The coin ID or description
- The correction or addition
- A reference source (RCM catalog page, Charlton Standard Catalogue entry, etc.)

All corrections are verified against primary sources before merging.

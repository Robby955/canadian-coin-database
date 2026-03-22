# Data Dictionary

## coins.json / coins.csv

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string | Yes | Unique identifier. Format: `{denomination}-{year}` for circulation (e.g., `1-cent-1858`), descriptive slug for others (e.g., `silver-maple-leaf-2024`). |
| `name` | string | Yes | Human-readable coin name (e.g., "1 cent 1858", "Silver Maple Leaf 2024"). |
| `year` | integer | No | Year of issue. Null for undated coins or sets without a specific year. Range: 1858-2026. |
| `denomination` | string | No | Face value denomination (e.g., "1 cent", "5 cents", "25 cents", "$1", "$2", "$50"). Null for sets or non-standard denominations. |
| `category` | string | Yes | Classification: `circulation`, `collectible`, `bullion`, `subscription`, `set`, or `roll`. |
| `metal` | string | No | Primary metal composition: `silver`, `gold`, `copper`, `nickel`, `steel`, `platinum`, `palladium`, `bronze`, `brass`, `bi-metallic`, `other`. Null if unknown. |
| `purity` | string | No | Metal purity as a decimal string (e.g., ".9999", ".925", ".800"). Null for base metal coins where purity is not applicable. |
| `weight_g` | float | No | Weight in grams. Null if not published by the Royal Canadian Mint. |
| `diameter_mm` | float | No | Diameter in millimeters. Null if not published. |
| `mintage` | integer | No | Total number of coins struck. Null if unpublished or not yet reported. For some early coins, this is an estimate from standard references. |
| `series` | string | No | Series name (e.g., "Silver Maple Leaf", "Pre-Confederation Coinage", "Birds of Canada"). Null if the coin is not part of a named series. |
| `monarch` | string | No | Reigning monarch depicted on obverse: `Victoria`, `Edward VII`, `George V`, `George VI`, `Elizabeth II`, `Charles III`. Null for coins without a monarch portrait. |
| `obverse_designer` | string | No | Designer of the obverse (portrait) side. |
| `reverse_designer` | string | No | Designer of the reverse side. |
| `edge` | string | No | Edge type: `Reeded`, `Plain (smooth)`, `Interrupted reeding`, `Lettered`, etc. |
| `finish` | string | No | Production finish: `Circulation`, `Proof`, `Specimen`, `Brilliant Uncirculated`, `Reverse Proof`, `Matte`, etc. |
| `composition` | string | No | Detailed alloy composition (e.g., "92.5% silver, 7.5% copper", "Multi-Ply Plated Steel"). More specific than `metal`. |
| `country` | string | Yes | Issuing country. Always `Canada` in this dataset. Included for compatibility with multi-country numismatic databases. |

### Null Handling

Null values indicate one of:

- **Not applicable**: e.g., `purity` is null for base metal coins because purity is not a meaningful specification for copper or steel coinage
- **Not published**: e.g., `mintage` is null when the Royal Canadian Mint has not yet published production figures
- **Unknown**: e.g., `reverse_designer` is null when attribution has not been established in standard references

Consumers should treat null as "no data available" rather than "zero" or "empty string."

## series.json

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string | Yes | Unique series identifier (slug format, e.g., `silver-maple-leaf`). |
| `name` | string | Yes | Series name (e.g., "Silver Maple Leaf"). |
| `category` | string | Yes | Series category: `circulation`, `bullion`, `collectible`, etc. |
| `year_start` | integer | Yes | First year of issue. |
| `year_end` | integer | No | Last year of issue. Null if the series is still active. |
| `status` | string | Yes | `active` (still being produced) or `complete` (no longer issued). |
| `denomination` | string | No | Standard denomination for the series (e.g., "$5" for Silver Maple Leaf). |
| `metal` | string | No | Primary metal (e.g., "silver", "gold"). |
| `weight_oz` | float | No | Standard weight in troy ounces. |
| `purity` | string | No | Standard purity (e.g., ".9999"). |
| `designer` | string | No | Original reverse designer. |
| `total_coins` | integer | No | Total number of distinct coins in the series. Null for open-ended series. |

## Known Gaps

The following fields have a higher proportion of null values by design:

- **`purity`** (~1,183 nulls): Base metal coins (copper, nickel, steel) correctly have no purity value
- **`series`** (~1,923 nulls): Many coins, particularly one-off commemoratives, are not part of a named series
- **`reverse_designer`** (~2,878 nulls): Designer attribution is unavailable for many early and some modern coins
- **`mintage`**: Recent issues may not yet have published mintage figures; some historical figures are estimates
- **`weight_g`** and **`diameter_mm`**: Generally complete for circulation and bullion; may be missing for some collector sets

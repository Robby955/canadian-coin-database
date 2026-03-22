# Methodology

## Sources

The primary data source is the Royal Canadian Mint catalog ([mint.ca](https://www.mint.ca)). Each entry is cross-referenced against established numismatic references:

- **Coins and Canada** (coinsandcanada.com) -- Comprehensive Canadian coin encyclopedia with mintage figures, varieties, and historical context
- **Saskatoon Coin Club** (saskatooncoinclub.ca) -- Detailed denomination-by-denomination reference tables for Canadian circulation coinage
- **Numista** (numista.com) -- International numismatic database with community-verified specifications
- **Charlton Standard Catalogue of Canadian Coins** -- The standard print reference for Canadian numismatics, used for verification of mintage figures and variety identification

For pre-Confederation coinage (Province of Canada, New Brunswick, Nova Scotia, Newfoundland, Prince Edward Island), additional references include provincial mint records and the Haxby & Willey standard references.

## Collection Process

The database represents a systematic catalog of all coinage issued by the Royal Canadian Mint and its predecessors from 1858 to present. The collection process follows these principles:

1. **Completeness**: Every denomination and year combination struck for circulation is included, along with bullion programs, numismatic issues, commemoratives, and collector sets.

2. **Verification**: Each coin's specifications (weight, diameter, composition, mintage) are verified against at least two independent sources. Where sources disagree, the Royal Canadian Mint's published specifications take precedence.

3. **Mintage figures**: Sourced from RCM annual reports, the Charlton Standard Catalogue, and established online references. For early coinage (pre-1900), some figures are estimates based on surviving records.

4. **Categorization**: Coins are classified into six categories (circulation, collectible, bullion, subscription, set, roll) based on their intended distribution channel and collector market positioning.

## Update Frequency

The database is updated weekly via an automated pipeline:

- **New issues**: Added as released by the Royal Canadian Mint, typically within one week of announcement
- **Mintage updates**: Annual mintage reports are incorporated when published by the RCM (typically mid-year for the previous year's figures)
- **Corrections**: Applied continuously as identified through community reports, reference cross-checking, and automated validation

## Quality Assurance

Data integrity is maintained through multiple mechanisms:

- **Automated validation**: Scripts check for data consistency, including valid year ranges per denomination, reasonable mintage figures, valid metal/purity combinations, and required field completeness
- **Cross-reference checks**: Periodic audits compare database entries against the Charlton Standard Catalogue, Coins and Canada, and the Saskatoon Coin Club reference tables
- **Community corrections**: Errors reported via GitHub Issues are verified against primary sources before applying fixes
- **Denomination audits**: Each denomination's year range is audited against known production gaps (years where coins were not struck) to ensure no phantom entries exist and no real issues are missing

## Known Limitations

- **Mintage estimates**: Some pre-1900 mintage figures are estimates based on surviving records. Where exact figures are unavailable, the best available estimate from standard references is used.
- **Composition detail**: Exact alloy compositions for some modern commemorative and collectible issues may be incomplete where the RCM has not published full specifications.
- **Varieties**: This dataset catalogs coins at the year/denomination level. Die varieties, error coins, and minor variations (e.g., large date vs. small date) are not included as separate entries.
- **Pricing**: Market values, melt values, and dealer pricing are intentionally excluded. These change daily and are better served by dedicated pricing services.
- **Images**: Coin images are not included in this dataset. The [Canadian Coin Heads website](https://canadiancoinheads.com) provides images for browsing.

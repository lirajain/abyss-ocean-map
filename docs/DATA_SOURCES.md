# Data Sources & Attribution

Abyss is designed to sit on top of open marine-biodiversity data. In this prototype the hotspots are hand-curated from well-documented species aggregations, but each is tagged with the kind of platform such a record would really come from. This page lists those platforms, why they matter, and how to credit them if you wire them in for real.

## The five source layers in Abyss

| Layer in app | Platform | What it is | API / access |
|--------------|----------|------------|--------------|
| **OBIS research surveys** | [OBIS](https://obis.org/) - Ocean Biodiversity Information System | The world's largest open database of marine species records, from research surveys and museums. | Free REST API at `api.obis.org` |
| **GBIF aggregated records** | [GBIF](https://www.gbif.org/) - Global Biodiversity Information Facility | Aggregates hundreds of millions of species occurrences, including marine. | Free REST API at `api.gbif.org` |
| **Happywhale photo-ID** | [Happywhale](https://happywhale.com/) | Citizen-science photo-identification of individual whales and dolphins; flows into OBIS-SEAMAP. | Contact Happywhale for data access |
| **iNaturalist divers** | [iNaturalist](https://www.inaturalist.org/) | Community observations from divers, snorkelers and beachgoers worldwide. | Free REST API at `api.inaturalist.org` |
| **NOAA live cams & expeditions** | [NOAA Ocean Exploration](https://oceanexplorer.noaa.gov/) and partners such as [explore.org](https://explore.org/livecams/oceans) and [OrcaLab](https://orcalab.org/) | Live camera and hydrophone feeds, plus expedition sightings. | Public live streams; embed per each site's terms |

## Suggested first integration: OBIS

OBIS is the natural first live hookup. A single query returns real occurrences with species, coordinates and date:

```
https://api.obis.org/v3/occurrence?scientificname=Megaptera%20novaeangliae&size=100
```

Each record includes `decimalLatitude`, `decimalLongitude`, `eventDate` and `scientificName` - enough to drop a real, dated marker on the map. GBIF works similarly via `https://api.gbif.org/v1/occurrence/search`.

## How to attribute

If you build live data into Abyss, please credit the source both in the UI and in any derived dataset:

- **OBIS**: "Ocean Biodiversity Information System (OBIS), obis.org" and cite the specific datasets returned.
- **GBIF**: use the citation string GBIF returns with each download (it includes a DOI).
- **iNaturalist**: credit observers and note the license on each observation (many are CC-BY / CC-BY-NC).
- **Happywhale**: reach out for a data-sharing agreement before ingesting their photo-ID data.
- **NOAA / explore.org / OrcaLab**: embed live feeds per each provider's embedding terms; do not re-host streams.

## A note on accuracy

Species ranges and seasons shift with ocean conditions and climate. Treat every hotspot as "typically around here, around this time," not a guarantee. If you spot a record in Abyss that is wrong or outdated, please open an issue or a pull request - accuracy is a community effort.

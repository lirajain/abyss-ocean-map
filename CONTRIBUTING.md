# Contributing to Abyss 🐋

First off - thank you. Abyss gets better every time someone adds a species, fixes a bug, or makes a creature swim a little more beautifully. This guide keeps things smooth for everyone.

By taking part you agree to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## Ways to contribute

You do not need to be a marine biologist or a senior engineer. Great contributions include:

- **New hotspots or species** - add a real aggregation with its location, season and a source.
- **Better creature art** - improve the inline SVG sprites or add new ones (seahorse, orca, penguin, octopus...).
- **Real data hookups** - wire a source to a live API (OBIS is the priority - see the roadmap).
- **Accessibility** - keyboard navigation, reduced-motion support, colour-contrast fixes.
- **Bug fixes and polish** - anything that makes it smoother, especially on mobile.
- **Docs** - typos, clearer explanations, translations.

## Getting set up

Abyss is a single `index.html` file with no build step.

```bash
# 1. Fork the repo on GitHub, then clone your fork
git clone https://github.com/YOUR-USERNAME/abyss-ocean-map.git
cd abyss-ocean-map

# 2. Start from the develop branch
git checkout develop

# 3. Create a branch for your change
git checkout -b feature/add-orca-sprite

# 4. Serve it locally and open http://localhost:8000
python3 -m http.server 8000
```

Edit `index.html`, refresh the browser, done. No `npm install`.

## Adding a hotspot

Find the `D` array in `index.html` and add an object. Every field matters:

```js
{
  n:"Humpback Whale",                 // display name
  sci:"Megaptera novaeangliae",       // scientific name
  t:"whale",                          // type: whale | dolphin | shark | ray | turtle | other
  e:"🐋",                              // emoji shown on the marker
  lat:-18.65, lng:-173.98,            // real coordinates
  loc:"Vava'u, Tonga",                // human-readable place
  src:"Happywhale",                   // source: OBIS | GBIF | Happywhale | iNaturalist | NOAA
  m:[7,8,9,10],                       // months present (1-12), or "all" for year-round
  depth:"0-40 m",                     // typical depth
  story:"One or two sentences...",    // the story shown in the info card
  fact:"A surprising fun fact...",    // the 'Did you know?' line
  obs:"How it was observed.",         // observation credit
  live:"https://..."                  // OPTIONAL - only for NOAA live-cam entries
}
```

Please make hotspots **real**: a genuine species at a genuine location with a genuine season, and pick the `src` that best matches where such a record would actually come from. If you can, drop a link to a source in your pull request description.

## Pull request checklist

- [ ] Branch is based on `develop` and PRs target `develop`.
- [ ] The app still opens and runs with no console errors.
- [ ] New hotspots use real coordinates, seasons and a plausible source.
- [ ] Text uses a hyphen (`-`), not an em dash.
- [ ] One focused change per PR where possible - easier to review.

## Style notes

- Keep everything in the single `index.html` file - that simplicity is a feature.
- Vanilla JS, no frameworks. No new build tooling without discussion first.
- Match the existing formatting and naming.

## Reporting bugs and ideas

Open an [issue](https://github.com/lirajain/abyss-ocean-map/issues) using one of the templates. For bugs, tell us your browser and what you expected versus what happened. For ideas, describe the "omg wow" you are imagining.

Not sure where to start? Look for issues tagged `good first issue`.

Happy diving. 🌊

# New England Water Quality

The drinking water compliance record for 1,151 New England towns, mapped from the U.S. EPA
Safe Drinking Water Information System (SDWIS).

**Live:** https://aep1992.github.io/ne-water-map/

## What this is

Every community water system in the six New England states files its compliance record with a state
primacy agency, which forwards it to EPA. This map reads that record back out, town by town:
health-based violations, monitoring and reporting violations, measured exceedances against federal
limits, and 90th-percentile lead and copper tap results.

- **Source:** EPA ECHO SDWA quarterly download, 2026 Q2 refresh (published July 2026)
- **Coverage:** 1,151 towns, 2,565 active community water systems, across MA / ME / NH / VT / CT / RI
- **Window:** violations with a non-compliance begin date of 1 Jan 2020 or later
- **Coordinates:** U.S. Census Bureau 2022 Gazetteer (places and county subdivisions)

Full methodology, exclusions, known data-quality issues and reproduction steps are in the **Method**
panel on the site itself.

## What it deliberately does not say

The bands describe a **compliance record, not a health risk.** A town shown as "No violations
recorded" met its reporting requirements in the window. It does not mean nothing is present in the
water, and it does not mean everything was tested for.

Everything here was measured in a water system, at compliance sample points, on particular dates.
None of it was measured at any individual tap. Between a treatment plant and a kitchen faucet there
is a distribution network, a service line whose material the utility may not know, the building's own
plumbing, and the fixture itself. Lead in particular almost never originates at the source; it is
picked up on the way. A public record describes the system. Only a sample from a tap describes that
tap.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire application: map, panel, town detail, methodology |
| `towns.json` | Aggregated per-town records built from the SDWIS extract |

No build step and nothing to install. Leaflet, the basemap tiles and the typeface load from their own
CDNs at runtime.

## Running it locally

```
python -m http.server 8191
```

Then open <http://localhost:8191>. It has to be served over HTTP rather than opened as a file,
because the page fetches `towns.json`.

## Deep links

Any town can be linked directly:

```
https://aep1992.github.io/ne-water-map/?town=WARREN&state=VT
```

## Attribution

Basemap tiles © OpenStreetMap contributors, © CARTO. Compliance data: U.S. EPA, public domain.
Boundary references: U.S. Census Bureau, public domain. Built with Leaflet.

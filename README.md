# DFW Site Selection Explorer

An interactive ArcGIS Dashboard for exploring candidate sites for a ~800,000 SF regional
distribution centre in the Dallas–Fort Worth MSA — scenario selector, ranked candidates, live
indicators, and criterion-contribution charts.

> **Status: in progress.** The analysis that feeds this dashboard is still running. This
> repository holds the specification and the build scripts; the published dashboard and
> screenshots land in weeks 6–8.

## What it will do

Let a non-technical reader — a broker, a corporate real-estate executive, an economic-development
officer — interrogate the ranking themselves rather than take a static map on trust. Change the
weighting scenario and watch the shortlist reorder. Select a candidate and see *why* it scored
where it did.

## Planned layout

| Element | Content |
|---|---|
| **Header** | Title and a scenario selector — `Balanced`, `LaborFirst`, `AccessFirst` |
| **Map** | Candidates symbolised by `score_class`; recommended site outlined; service areas and stores toggleable |
| **List** | Candidates ranked; selecting one filters every other widget and zooms the map |
| **Indicators** | Composite score, rank, 30-minute labour pool, unemployment rate, minutes to interchange, mean minutes to stores, SFHA %, land value per acre |
| **Serial chart** | Top 10 by composite score |
| **Stacked bar** | Weighted criterion contributions for the selected candidate — shows what actually drove the score |
| **Gauge** | `top10_freq` — how often this site lands in the top 10 across 1,000 Monte Carlo weight draws |
| **Details** | Site profile text |
| **Mobile layout** | A separate arrangement for phones |

The stacked bar and the gauge are the two that matter most. The first turns a single composite
number back into the eleven criteria behind it. The second answers the question a sceptical
reader should ask: *would a slightly different set of weights give a different answer?*

## Data behind it

Hosted feature layers published from the study's file geodatabase, in EPSG:3857:

`SiteScores` · `Shortlist` · `ServiceAreas_Driving` · `ServiceAreas_Truck` · `Stores_DSG`

Each carries a `run_id` tracing back to the exact pipeline run and git commit that produced it.

## Repository layout

```
scripts/       dashboard build (arcgis.apps.dashboard) and layer publishing
screenshots/   captures of the published dashboard
```

Scripted rather than hand-built so the dashboard can be rebuilt from the analysis, not just
edited in place.

## Credentials

None in this repository, ever. Publishing authenticates through ArcGIS Pro's active portal
session, or a named GIS profile held in the OS keystore.

## Status detail

| Item | State |
|---|---|
| Specification | ✅ |
| Layer publishing script | ◻ week 6 |
| Dashboard build script | ◻ week 6 |
| Interactivity + mobile layout | ◻ week 7, finished in the builder |
| Public URL | ◻ |
| Screenshots | ◻ |

## License

MIT — see [LICENSE](LICENSE).

---

A component of [dsg-dfw-site-selection](https://github.com/ndeogobernard/dsg-dfw-site-selection),
a DFW regional-DC site-selection system.

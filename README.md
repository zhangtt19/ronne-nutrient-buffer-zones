# Rönne catchment: nutrient loads and riparian buffer zones

**A QGIS analysis linking nutrient-source estimates, streamside mitigation areas and municipal cost allocation.**

[中文说明](README.zh-CN.md) · [Full figure gallery](docs/FIGURES.md) · [Workflow and assumptions](docs/METHODS.md) · [Data tables](data/README.md)

![Candidate buffer zones](figures/buffer-zones.png)

## From catchment diagnosis to spatial intervention

Where could riparian buffer zones be placed to reduce phosphorus losses, and how would different principles distribute their costs between municipalities? I combined land cover, stream networks, municipal boundaries, point-source loads and outlet measurements in QGIS 3.44.3.

The analysis first estimates diffuse nitrogen and phosphorus loads from land-cover areas and export coefficients. Adding point-source loads allows a comparison with reported outlet loads. It then identifies cultivated land within 20 m of first- and second-order streams, calculates potential phosphorus retention and compares four cost-sharing principles.

## Nutrient loads

| Load, tonnes/year | Nitrogen | Phosphorus |
|---|---:|---:|
| Estimated diffuse sources | 1,707.8 | 32.7 |
| Point sources | 214.9 | 3.6 |
| Combined estimate | 1,922.7 | 36.3 |
| Reported outlet load | 2,496.0 | 51.0 |

The coefficient-based totals are lower than outlet loads by 573.3 tonnes N/year and 14.7 tonnes P/year. This comparison helps identify the limitations of a simplified catchment inventory. Cultivated land is a major target for phosphorus mitigation even though forest occupies the largest area.

## Buffer zones and estimated costs

The spatial workflow is **merge streams → create 20 m buffers → dissolve overlaps → intersect land cover → retain cultivated land → recalculate area**.

![20 m buffer detail](figures/buffer-detail.png)

| Output | Reported result |
|---|---:|
| Candidate buffer area | 808.8 ha |
| Potential phosphorus retention | 3,235 kg/year |
| Establishment cost | 13,749,855 SEK |
| Compensation component | 323,526 SEK |
| Combined cost estimate | 14,073,381 SEK |

Retention assumes 4 kg P/(ha·year). Establishment and compensation use 1.70 SEK/m² and 400 SEK/ha respectively. Reported totals use the underlying unrounded areas. The compensation rate has no specified recurrence period in the source calculation; the combined value is therefore presented as a cost estimate, without labelling it an annual cost.

## Who carries the cost?

![Municipal shares under four allocation principles](figures/cost-allocation.png)

I compared shares based on catchment area, diffuse phosphorus loads, buffer-zone area and stream length. For example, Ängelholm's share varies from 17.2% by catchment area to 24.6% by buffer-zone area. The choice of principle changes the allocation even when the total budget stays fixed.

This is a spatial screening and planning study. Retention is an estimate based on a uniform coefficient; implementation would require local checks of terrain, drainage pathways, land availability and performance.

The repository contains the maps, workflows and result tables. See the [method guide](docs/METHODS.md) for inputs and processing steps.

Analysis: **Tianshu Zhang**.

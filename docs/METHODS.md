# Processing workflow / 处理流程

[Project](../README.md) · [中文说明](../README.zh-CN.md)

## Inputs

Land-cover polygons and nutrient-export coefficients; first- and second-order streams; catchment and municipal boundaries; point-source N/P loads; reported outlet N/P loads. Area and length calculations require a suitable projected coordinate system and consistent units.

## Steps

1. Clip land cover to the catchment. Calculate area by land-cover class. Multiply hectares by class-specific export coefficients to obtain diffuse loads; convert kg to tonnes before comparison.
2. Sum point-source loads within the study boundary, combine with diffuse loads and compare with outlet loads. Preserve the difference as an inventory gap; do not force the totals to agree.
3. Merge selected streams, buffer them by 20 m and dissolve overlapping buffers. Intersect the result with cultivated land. Recalculate areas after intersection so overlaps and removed land are not counted twice.
4. Estimate potential P retention as eligible area in hectares × 4 kg/(ha·year).
5. Calculate establishment cost as eligible area in m² × 1.70 SEK/m², and the compensation component as eligible area in ha × 400 SEK/ha.
6. Intersect with municipal boundaries. Derive each municipality's share separately for catchment area, diffuse P load, buffer area and stream length; multiply each share by the same total cost to compare allocation principles.

## Interpretation

The tables preserve the reported rounded figures. Small differences can arise when calculations are repeated from rounded area values. Nutrient loads and buffer retention are coefficient-based estimates. The outlet comparison is an assessment of inventory agreement, not a calibrated nutrient-transport model.

The present repository provides the analytical workflow, figures and tabulated results. It does not contain a packaged QGIS project with all input layers.

## 中文要点

先统一坐标和单位，再做裁剪、缓冲、融合与相交。面积必须在空间运算后重新计算；成本计算尤其要区分平方米与公顷。以相同总预算对比四套市镇权重，才能区分“需要多少钱”和“由谁承担”的问题。

现有成果提供完整的分析路径、图件与结果表；目前未附带包含全部输入图层的 QGIS 工程包。

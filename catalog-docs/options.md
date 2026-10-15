---
title: Options
description: 'Reference for Funnel panel options.'
sidebar_position: 3
---

Funnel adds its own options to the panel editor, and it enables most of the standard field options. The custom options are in the **Funnel** and **Time comparison** categories. Some options show only for a specific layout or when the data has a comparison period.

## Panel options

| Option                     | Type   | Default         | Description                                                                                                                                                                                                                       |
| -------------------------- | ------ | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Layout**                 | Radio  | `Classic`       | Choose how the funnel is drawn. **Classic** is a centered funnel with labels on the left and percentages on the right. **Flow** is one section per step with details next to a continuous, smoothly narrowing funnel.             |
| **Orientation**            | Radio  | `Vertical`      | Choose the direction of the steps. **Vertical** shows steps from top to bottom with the funnel on the right. **Horizontal** shows steps from left to right with the funnel below the details. Shows only for the flow layout.     |
| **Sorting**                | Radio  | `Descending`    | Choose how to sort the steps by value. **Descending** sorts from highest to lowest, **Ascending** sorts from lowest to highest, and **None** applies no sorting.                                                                  |
| **Show retention rate**    | Toggle | `Off`           | Show retention rate instead of drop-off rate in gap labels and tooltips. In the flow layout, the conversion of each step shows retention instead of drop-off.                                                                     |
| **Show percentages**       | Toggle | `On`            | Show the percentage column next to the funnel bars. Shows only for the classic layout.                                                                                                                                            |
| **Funnel to display**      | Radio  | `Newest period` | Choose which period to show when the data has a comparison period. **Newest period** shows the newest period and its change from the oldest period. **Oldest period** shows the oldest period and its change from the newest one. |
| **A favorable outcome is** | Radio  | `Higher`        | Choose which direction of change is favorable. **Higher** shows increases as favorable. **Lower** shows decreases as favorable.                                                                                                   |

The **Funnel to display** and **A favorable outcome is** options are in the **Time comparison** category. They show only for the flow layout, and only when the data has a comparison period from Grafana Time comparison. For details, refer to [Time comparison](./time-comparison.md).

## Standard field options

Funnel enables these standard field options:

- **Unit**
- **Min**. Defaults to `0`. Keep this value, because the percentages and the width of the funnel depend on it.
- **Max**
- **Decimals**
- **Display name**
- **Color scheme**. Defaults to **Green-Yellow-Red (by value)**, and you can color by value or by series.
- **Value mappings**
- **Data links**. Only the flow layout shows data links. Refer to [Layouts](./layouts.md#data-links).

Funnel doesn't offer the **No value** and **Thresholds** options. For what these options do, refer to the Grafana documentation.

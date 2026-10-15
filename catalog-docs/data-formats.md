---
title: Data formats
description: 'Learn what data formats the Funnel panel accepts.'
sidebar_position: 2
---

The Funnel panel works with any data source that returns data frames with numeric fields. Each numeric field becomes one step in the funnel, so the way you shape your query results decides which steps you get.

## Supported data shape

Every data frame that reaches the panel needs at least one numeric field. The panel ignores fields of other types, such as strings and times. The panel shows one value for each numeric field, so use a transformation such as **Reduce** or **Rows to fields** when a query returns more than one value for a step.

Use one of these shapes.

### One frame for each step

Use one query for each step. Each query returns a frame with a single numeric field. Name the query or frame after the step, or set **Display name** in the standard field options, so the step has a readable label. This is the most common way to query the data.

#### Example

| Frame name  | Value |
| ----------- | ----- |
| Sent        | 52300 |
| Viewed      | 35679 |
| Clicked     | 15690 |
| Add to cart | 5596  |
| Purchased   | 3290  |

Each row above is a separate frame with one numeric field named `Value`.

### One frame with one field for each step

Use one frame with one numeric field for each step. The field names are the step names, and each field holds one value.

#### Example

| Sent  | Viewed | Clicked | Add to cart | Purchased |
| ----- | ------ | ------- | ----------- | --------- |
| 52300 | 35679  | 15690   | 5596        | 3290      |

### One frame with rows of steps

Some queries return one frame with two fields: one field with the step names and one field with the values. This is common when you query a pre-built view that holds the aggregated data for the funnel, for example when heavy queries run on a regular basis.

Add the **Rows to fields** transformation to turn this into one frame with one field for each step, which is the shape in the previous section.

#### Example

| Label       | Value |
| ----------- | ----- |
| Sent        | 52300 |
| Viewed      | 35679 |
| Clicked     | 15690 |
| Add to cart | 5596  |
| Purchased   | 3290  |

### Data that the panel can't use

If no data frames reach the panel, it shows **No data**. If any frame has no numeric field, the panel shows an **Unsupported data** message that explains this requirement. For help with both, refer to [Troubleshooting](./troubleshooting.md).

### Data for time comparison

The flow layout can compare the funnel with an earlier period when you turn on Grafana Time comparison. For a comparison, each period needs exactly one non-negative numeric value for each step, and both periods need the same steps. Refer to [Time comparison](./time-comparison.md).

> [!NOTE]
> The panel sets **Min** to `0` by default, which the percentages depend on. If you change **Min** to `auto`, the percentages and drop-off values are wrong. Refer to [Percentages or drop-off values look wrong](./troubleshooting.md#percentages-or-drop-off-values-look-wrong).

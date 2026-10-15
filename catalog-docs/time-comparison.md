---
title: Time comparison
description: 'Compare the Funnel panel with an earlier period using Grafana Time comparison.'
sidebar_position: 5
---

The flow layout can compare the funnel with an earlier period. It shows one funnel at a time, and each step shows its change from the other period.

![The flow layout with Time comparison, showing the change of each step compared to the day before](./img/panel-comparison.png)

## Enable Time comparison

The panel uses the comparison period that Grafana adds, so there is nothing to set up in the panel itself:

1. Set **Layout** to **Flow**.
1. Enable **Time comparison** in the time settings of the panel.

To go back to a single funnel, disable **Time comparison**.

Time comparison needs Grafana 12.3 or later. Grafana 12.3 also needs the `panelTimeSettings` and `timeComparison` feature toggles.

> [!NOTE]
> A plain **Time shift** changes the time range of the whole panel. It doesn't give the panel a second period to compare with. The classic layout always shows the current period only.

## What the panel shows

Each step shows its change from the other period:

- The count change, for example `+1200 (+3.5%)`, and the count of the other period.
- The change of the drop-off or retention rate in percentage points, for example `+2.1 pp`.

A header above the steps shows the overall conversion from the first to the last step, and its change.

Grafana shows the compared period next to the panel title, for example **Compared to day before**. A change shows as `—` when it can't be calculated, for example when the count of the other period is zero.

## Options

When the panel has a comparison period, these options show in the **Time comparison** category:

- **Funnel to display** shows the newest or the oldest period. The steps are sorted by the displayed period.
- **A favorable outcome is** sets the colors. With **Higher**, increases are green and decreases are red. With **Lower**, the colors are the other way around.

## Data requirements

Each period needs one non-negative numeric value for each step, and both periods need the same steps. Transformations such as **Reduce** and **Rows to fields** work with Time comparison. If the data doesn't meet these requirements, the panel shows a warning above the single funnel. Refer to [Troubleshooting](./troubleshooting.md#time-comparison-shows-a-warning).

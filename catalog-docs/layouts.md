---
title: Layouts
description: 'Choose between the classic and flow layouts of the Funnel panel, and add data links to steps.'
sidebar_position: 4
---

The panel has two layouts. Select one with the **Layout** option in the **Funnel** category of the panel editor.

## Classic layout

The classic layout is a centered funnel with the step labels on the left and the percentage of each step on the right. A gap between two bars shows the drop-off from one step to the next. Turn on **Show retention rate** to show the retention instead.

- Hover a bar to show a tooltip with the label, value and percentage of the step.
- Hover a gap to show the drop-off or retention between the two steps.
- Turn off **Show percentages** to hide the percentage column.

The percentage compares a step with the largest value, as long as **Min** is `0` and **Max** is not set. The classic layout doesn't show data links.

## Flow layout

The flow layout draws the funnel as one continuous band that narrows smoothly from step to step. Each step shows:

- The name of the step.
- The value of the step.
- The conversion from the previous step, as drop-off or retention. Use **Show retention rate** to switch between them.

The percentage of the first step is shown next to the band. Hover a step to highlight it in the band.

Use the **Orientation** option to show the steps from top to bottom (**Vertical**) or from left to right (**Horizontal**).

![The flow layout with a horizontal orientation, showing five steps from Sent to Purchased with the drop-off between steps](./img/panel.png)

The flow layout is also the only layout that can compare the funnel with an earlier period. Refer to [Time comparison](./time-comparison.md).

## Data links

Add links to the steps with the standard **Data links** field option. Only the flow layout shows data links.

In the flow layout, hover or focus a step to show a menu button in its corner. Click the button to open the data links of that step. Grafana resolves variables in a link, such as `${__field.displayName}`, when you open the menu.

To add links to a single step, use an override that matches the step by name and sets **Data links**. For a working example, refer to [Examples](./examples.md#flow-layout-with-data-links).

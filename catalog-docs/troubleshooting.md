---
title: Troubleshooting
description: 'Troubleshoot the Funnel panel.'
sidebar_position: 7
---

Find the symptom you see in the panel, then follow the steps to fix it.

## Percentages or drop-off values look wrong

**Symptom:** The percentages don't match your values. For example, the last step always shows a 100% drop-off and 0% retention, or the percentages are lower than they should be.

**Cause:** The percentage of each step is calculated from the range of the data, from **Min** to the largest value. If **Min** is set to `auto`, Grafana uses the lowest value in the data as the minimum, so the lowest step always ends up at 0%.

**Solution:**

1. Open the panel editor and find the **Standard options** section.
1. Set **Min** to `0`.

The panel sets **Min** to `0` by default, so this happens when someone changed the value.

## The panel shows no data

**Symptom:** The panel shows **No data**.

**Cause:** The queries didn't return any data frames.

**Solution:**

1. Run the queries in the panel editor and check that each one returns a result for the selected time range.
1. If a transformation removes all the data, disable the transformations one by one to find which one does it.

## The panel shows an unsupported data message

**Symptom:** The panel shows an **Unsupported data** message that says every data frame needs at least one numeric field.

**Cause:** At least one data frame has no numeric field. This happens, for example, when a query returns only text or time fields, or when a numeric value is returned as text.

**Solution:**

1. Check the result of each query in the **Table view** of the panel editor.
1. Make sure every frame has a numeric field, and convert text values to numbers in the query or with a transformation.
1. If the data has one row for each step, add the **Rows to fields** transformation. Refer to [Data formats](./data-formats.md#one-frame-with-rows-of-steps).

## Some steps are missing or don't have the name I expect

**Symptom:** The funnel has fewer steps than you expect, or a step has a label such as `Value`.

**Cause:** Each numeric field is one step, and the panel ignores fields of other types. A step label comes from the field display name, so a frame without a useful name gives a generic label.

**Solution:**

1. Make sure each step is a numeric field, with one field for each step.
1. Name the queries or fields after the steps, or set **Display name** in the standard field options.

## The percentage column or the data links are missing

**Symptom:** The percentage column isn't visible, or the data links don't appear.

**Cause:** Both depend on the layout and on the options:

- The classic layout shows the percentage column only when **Show percentages** is on. The flow layout shows the percentage next to the band instead of in a column.
- Only the flow layout shows data links. In the flow layout, hover or focus a step to show the menu button.

**Solution:** Turn on **Show percentages** for the classic layout, or switch **Layout** to **Flow** to use data links. Refer to [Layouts](./layouts.md).

## Time comparison shows no change or no options

**Symptom:** The panel doesn't show the change from an earlier period, or the **Time comparison** options are missing.

**Cause:** Only the flow layout compares periods, and only when Grafana adds a comparison period to the data. A plain **Time shift** doesn't add one.

**Solution:**

1. Set **Layout** to **Flow**.
1. Enable **Time comparison** in the time settings of the panel. This needs Grafana 12.3 or later with the `panelTimeSettings` and `timeComparison` feature toggles.

## Time comparison shows a warning

**Symptom:** A warning shows above a single funnel, with one of these messages:

- **Time comparison needs the results of the current period**
- **Current and previous funnel steps do not match**
- **Comparison needs one non-negative numeric value per step**

**Cause:** The panel can't pair the steps of the two periods. The data of the current period is missing, the two periods have different steps, or a step doesn't have exactly one non-negative numeric value.

**Solution:**

1. Check that the queries return data for both periods.
1. Make sure both periods have the same steps with the same names.
1. Use a transformation such as **Reduce** or **Rows to fields** so that each step has one value.

For the requirements, refer to [Time comparison](./time-comparison.md#data-requirements).

## Get more help

If none of these steps fix the problem, [create an issue](https://github.com/mckn/mckn-funnel-panel/issues/new) in the plugin repository.

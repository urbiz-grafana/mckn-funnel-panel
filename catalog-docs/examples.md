---
title: Examples
description: 'Worked examples of the Funnel panel.'
sidebar_position: 6
---

These examples are `dashboard.json` panel excerpts that come from the dashboards the plugin repository provisions for development. For the full JSON, refer to the [funnel examples dashboard](https://github.com/mckn/mckn-funnel-panel/blob/main/provisioning/dashboards/panels.json) and the [checkout funnel demo dashboard](https://github.com/mckn/mckn-funnel-panel/blob/main/provisioning/dashboards/funnel-demo.json).

## Basic example

This panel uses the classic layout with one query that returns a step name and a value for each row. The **Rows to fields** transformation turns the rows into one field for each step. The example uses the Static data source (`marcusolsson-static-datasource`), so you can reproduce it without a real data source.

```json
{
  "type": "mckn-funnel-panel",
  "title": "Funnel",
  "options": {
    "sorting": "descending"
  },
  "fieldConfig": {
    "defaults": {
      "color": { "mode": "palette-classic" },
      "min": 0
    },
    "overrides": []
  },
  "targets": [
    {
      "datasource": { "type": "marcusolsson-static-datasource" },
      "refId": "A",
      "frame": {
        "name": "Sent",
        "fields": [
          {
            "name": "Label",
            "type": "string",
            "values": ["Sent", "Viewed", "Clicked", "Add to cart", "Purchased"]
          },
          {
            "name": "Value",
            "type": "number",
            "values": [52300, 35679, 15690, 5596, 3290]
          }
        ]
      }
    }
  ],
  "transformations": [{ "id": "rowsToFields", "options": {} }]
}
```

## Common variations

### Flow layout with a horizontal orientation

This variation uses the same query and transformation as the basic example. It changes the layout to flow and the orientation to horizontal.

```json
{
  "options": {
    "layout": "flow",
    "orientation": "horizontal",
    "sorting": "descending",
    "showRemainedPercentage": false
  }
}
```

![The flow layout with a horizontal orientation, showing five steps from Sent to Purchased with the drop-off between steps](./img/panel.png)

### Flow layout with data links

This variation uses the flow layout with a vertical orientation and adds two data links to every step. The first link opens a dashboard with the step as a variable. The second link opens a search in a new tab. Replace the dashboard URL with the URL of your own dashboard.

```json
{
  "options": {
    "layout": "flow",
    "orientation": "vertical",
    "sorting": "descending",
    "showRemainedPercentage": false
  },
  "fieldConfig": {
    "defaults": {
      "links": [
        {
          "title": "Show ${__field.displayName} details",
          "url": "/d/NtsITqb4z/funnel-examples?orgId=1&var-step=${__field.displayName}&var-value=${__value.raw}"
        },
        {
          "targetBlank": true,
          "title": "Search for ${__field.displayName}",
          "url": "https://grafana.com/search/?query=${__field.displayName}"
        }
      ]
    }
  }
}
```

### Flow layout with Time comparison

This variation compares the funnel with the day before. It uses the TestData data source, which returns one value for each step every 10 minutes, and the **Reduce** transformation to sum the values of each step. Setting `timeCompare` to `1d` turns on Grafana Time comparison for the panel. Refer to [Time comparison](./time-comparison.md).

```json
{
  "type": "mckn-funnel-panel",
  "timeCompare": "1d",
  "options": {
    "layout": "flow",
    "orientation": "vertical",
    "sorting": "descending",
    "showRemainedPercentage": false,
    "comparisonPeriod": "newest",
    "outcomeDirection": "higher"
  },
  "targets": [
    {
      "datasource": { "type": "grafana-testdata-datasource" },
      "refId": "A",
      "scenarioId": "predictable_csv_wave",
      "csvWave": [
        { "name": "Sent", "timeStep": 600, "valuesCSV": "1200,1350,1500,1100,1400,1600,1250" },
        { "name": "Viewed", "timeStep": 600, "valuesCSV": "840,810,1050,660,980,1280,750" },
        { "name": "Clicked", "timeStep": 600, "valuesCSV": "420,324,578,264,441,704,300" },
        { "name": "Add to cart", "timeStep": 600, "valuesCSV": "168,113,231,79,176,317,90" },
        { "name": "Purchased", "timeStep": 600, "valuesCSV": "101,57,150,40,106,206,45" }
      ]
    }
  ],
  "transformations": [
    {
      "id": "reduce",
      "options": {
        "mode": "reduceFields",
        "reducers": ["sum"],
        "includeTimeField": false
      }
    }
  ]
}
```

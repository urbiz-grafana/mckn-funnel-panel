![GitHub](https://img.shields.io/github/license/mckn/mckn-funnel-panel)
![Version](https://img.shields.io/github/package-json/v/mckn/mckn-funnel-panel)

# Funnel Panel

Grafana panel to create funnel charts

![Screenshot](https://raw.githubusercontent.com/mckn/mckn-funnel-panel/83b6605fa913001f965ff951892c9bdf13429f07/src/img/panel.png)

## What are funnel charts?

A funnel chart is a specialized chart type that demonstrates the flow of e.g. users through a business or sales process. The chart takes its name from its shape, which starts from a broad head and ends in a narrow neck. The number of users at each stage of the process are indicated from the funnel’s width as it narrows.

Use the panel to see how many users, orders or events make it through each step of a process, and where the rest drop off. It works with any data source that returns a numeric field for each step.

## Features

- Two layouts: a classic centered funnel, and a flow layout that draws one continuous band with the details of each step next to it.
- Vertical and horizontal orientation in the flow layout.
- Sort the steps from highest to lowest, from lowest to highest, or keep the order of the data.
- Show the drop-off or the retention from one step to the next.
- Open data links from any step in the flow layout.
- Compare the funnel with an earlier period using Grafana Time comparison, with the change of each step and of the overall conversion (Grafana 12.3 or later).
- Colors from the standard Grafana color schemes, by value or by series.

For how to shape your data, configure the panel and fix common problems, refer to the [Documentation tab](https://grafana.com/grafana/plugins/mckn-funnel-panel/docs/).

## Contributing

- For bugs or enhancements please create an [issue](https://github.com/mckn/mckn-funnel-panel/issues/new).

---
name: U-C Area Building Sprawl Over The Years Project
tools: [Python, HTML, vega-lite]
image: assets/pngs/uc-project.png
description: These are two visualizations that showcase the sprawl of buildings within the U-C area over the last 130 years, as well as their respective square footage
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart.json" style="width: 100%"></vegachart>

<vegachart schema-url="{{ site.baseurl }}/assets/json/line_chart.json" style="width: 100%"></vegachart>

## Search The Data & Methods

## Space for write ups 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/vitaluiuc2023/vitaluiuc2023.github.io/blob/main/python_notebooks/analysis_main.ipynb" text="The Analysis" %}
</div>


---
name: Urbana-Champaign Constructed Buildings By Category 1870-2019
tools: [Python, HTML, vega-lite, Altair]
image: assets/pngs/uc-project.png
description: This is a project dedicated to showcasing the construction emphasis between developers within the Urbana-Champaign are from the 1870-2019 time period. 
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# Plot 1: Urbana-Champaign Constructed Buildings By Category 1870-2019 (Vega-Lite/Altair Plot)

Utilizing the content for this week's homework, I decided to select a different dataset from the previous week to get more practice with other ideas (as well as the extra credit!). My initial idea upon stumbling on the buildings dataset was that given the University's founding taking officially in 1870, I wanted to visualize the sprawl of additional infrastructure that was taking place subsequent to that moment. This is the inspiration for this first visualization. 

I decided the best way to execute this would be to first filter the dataset by U-C only, followed by utilizing the count function to add up each year with its respective buildings in a stacked bar. The visualization would have been riskier if it featured a city of bigger sprawl, but my initial tweaks of the plot revealed that some years peaked at 10 buildings most which is why I thought it was safe to keep the format I came up with. I utilized ALtair in full to execute this homework, with only this first plot needing a recreation in vega-lite given the no current support of interactive Altair plots being possible without extensive HTML manipulation like we discussed in class. 

For max interactivity, I knew that I want the user to be able to select the color scheme of their choice. Given that our Jekyll template is dark, I wanted colors that contrasted well with dark colors. I came up on official Altair/Vega-Lite documentation that I will link at the bottom of the plot which I used for reference where I picked out the current 5 possible options. I think that darkening the background of the viz out via helps it instead of the blarring white default color. For encoding types, I went with ```X``` being my Years and declared it as an Ordinal to showcase necessity for order. For ```Y```, I declared my buildings sum as a quantitative. When it came to ```color```, I went with using the use description of the buildings as the parameter by which the colors would be dispersed; declaring it a nominal. I likewise added a ```tooltip``` that just showed the same information whenever you would hover over a particular area to highlight specifically the category of use in question and the total quantity within said year so it would be more interpretable despite the scale being small. I finalized the plot with title adjustments and an X-axis label flip so that the years would be readable, opting for a ```mark_bar()``` to be the vizualization holding all of these. 

For actual transformation within the Python Notebook, I merely filtered and grouped as mentioned earlier. A simple ```for loop``` granted me the possibility of splitting the years in decades, after which I declared my interaction widgets and defined the ```on_change()``` and ```update_chart()``` functions paired with the ```output()``` widget that was introduced during the Week 5 material content. I utilized this setup to be the one that granted my plot interactivity. 

<vegachart schema-url="{{ site.baseurl }}/assets/json/visualization.vl.json" style="width: 100%"></vegachart>

I converted the plot to vega-lite since the Altair native JSON import would look like this; going to discuss this with Professor Naiman 11/18 in-class to make sure this is okay. 

### Failed Imported Altair Plot Showcase 
<vegachart schema-url="{{ site.baseurl }}/assets/json/chart.json" style="width: 100%"></vegachart>
As visible, there is no interactivity present. The possibility to add it is there, but not without extensive HTML modifications.<br><br>
#### Links to material referenced for Plot #1: <br>
<a href="https://altair-viz.github.io/user_guide/customization.html#chart-themes">Color Themes</a> <br>
<a href="https://altair-viz.github.io/user_guide/data.html">General Vega-lite/Altair Data Use Showcase</a>

# Plot 2: Urbana-Champaign Construction Square Footage Per Decade Line Chart (Altair Plot)

To better help visualize the significance in certain time periods, I decided to use a similar approach when it came to summing buildings. I decided to use the square footage to see how significant the size of these said buildings would be within the same time periods. A bunch of buildings would not be significant in Urbana-Champaign's growth unless their square footage was of significance, which is what this visualization would help me contrast that.

I started off by declaring a new placeholder column called ```Decade``` within my DataFrame. This would take each year and divide it by a base of 10 to truncate any uneven year to a corresponding decade by remultiplying that value by a 10 afterwards. I used this column during a ```groupby``` call by ```Decade``` following ```Square Footage``` and a ```sum()``` statement to get the square footage per decades calculated and ready for my visualization. The rest of the plot follows a similar logical approach as the previous one. I decided to use ```mark_line()``` to achieve my intended goal. My encodings included ```X```, ```Y``` and ```tooltip```. I decided to leave my ```color``` for the line default, but did add some blue under the curve shading via an additional ```mark_area```. For ```X``` and ```Y``` in both ```mark```s, I used the ```Decades``` as my ordinal X and the summed up ```Square Footage``` as a quantitative. ```Tooltip``` followed the same declaration as the first plot. Final touch ups included another X-axis label flip like the first plot and appropiate title. 

Having this visualization is important because it showcases a determined trend with two clear peak decades: 1920 and 1960. We could claim that during the Roaring 20s, the area reached its potential at that time, with the next big sprawl being around 1960. This would have been right after all the people deployed during WWII would go on to pursue education, thus the need to accomodate an incoming influx of future generations of students as academia became an important factor within American societal values. Likewise, any emerging industries would have an area to establish themselves in.  

<vegachart schema-url="{{ site.baseurl }}/assets/json/line_chart.json" style="width: 100%"></vegachart>

In overall, I think both of these visualizations contain information that complement each other, giving an impactful insight into the growth of Urbana-Champaign as an area over the last 100 plus years. The interactivity allows for a shift in colors if the differentiation between different types of buildings is hard to establish, as well as a 10 year range that facilitates a closer look within given timeframes without making the plot too overwhelming with every single year listed on there. 

## Search The Data & Methods

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis" %}
</div>


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


# Plot 1: U-C Area Constructed Buildings By Category 1870-2019 (Altair Plot)

Utilizing the content for this week's homework, I decided to select a different dataset from the previous week to get more practice with other ideas (as well as the extra credit!). My initial idea upon stumbling on the buildings dataset was that given the University's founding taking officially in 1870, I wanted to visualize the sprawl of additional infrastructure that was taking place subsequent to that moment. This is the inspiration for this first visualization. 

I decided the best way to execute this would be to first filter the dataset by U-C only when I was messing with it in Excel. With a bit of luck, the massive dataset was narrowed to a mere ~330 buildings, from where I decided to take a look at the documented range with the data at hand. It is here where I learned that the dataset would be running from 1870-2019 in years, giving me the idea to represent decades collectively instead of each year individually. Some years peaked at 10 buildings most, which is why I thought a bar chart would be a feasible way to represent this over the span of all the ranges that will follow. Upon looking at documentation and programming notation, I decided to fully stick with Altair since it resembled Python. I originally plotted the interactive portion of this assignment utilizing ```ipywidgets``` before I realized that Jekyll probably does not have a Python-based backend installed (big thank you to Professor Naiman for pointing this out during 11/18 session).

Given that our Jekyll template is dark, I wanted colors schemes that contrasted well for a potential user to choose from. I came up on official Altair/Vega-Lite documentation that I will link at the bottom of the plot, which I ended up using for reference where I picked out the current 3 possible options. For encoding types, I went with ```X``` being my Years Construced and declared it as an Ordinal to showcase necessity for order. For ```Y```, I simply declared a ```count()``` statement for all buildings within a specific year to be listed. When it came to ```color```, I went with using the use description of the buildings as the parameter by which the colors would be dispersed; declaring it a nominal. I likewise added a ```tooltip``` that just showed the same information whenever you would hover over a particular area to highlight specifically the category of use in question and the total quantity within said year so it would be more interpretable despite the scale being naturally small. I finalized the plot with title adjustments and an X-axis label flip so that the years would be readable, opting for a ```mark_bar()``` to be the vizualization holding all of these. 

<vegachart schema-url="{{ site.baseurl }}/assets/json/bar_chart.json" style="width: 100%"></vegachart>

### Failed IPywidgets Based Plot Showcase 
<vegachart schema-url="{{ site.baseurl }}/assets/json/chart.json" style="width: 100%"></vegachart>
This is a showcase of my original attempt trying to use the ```ipywidgets``` mentioned previously as my interactivity tool. As visible, there is no interactivity present. I figured I would include this to showcase the difference between pure Altair vs. Altair + Python. It was worth a shot at least! I still left the original code block I intended to use within the notebook in case it was interesting to see how I did it with Python as well. <br><br>
#### Links to material referenced for Plot #1: <br>
<a href="https://altair-viz.github.io/user_guide/customization.html#chart-themes">Color Themes</a> <br>
<a href="https://altair-viz.github.io/user_guide/data.html">General Vega-lite/Altair Data Use Showcase</a>

# Plot 2: U-C Constructed Buildings Square Footage Per Decade 1870-2019 (Altair Plot)

For my second plot, I decided to showcase the square footage to demonstrate what the size of these said buildings would have been. Given the many year ranges, I wanted to ensure that mere quantity of buildings did not imply a proportional size growth trend. That is to say, a bunch of buildings would not be significant in Urbana-Champaign's growth unless their square footage was of significance, which is what I was hoping this visualization would help me contrast and evaluate.

I started off by declaring a new placeholder column called ```Decade``` within my DataFrame. This would take each year and divide it by a base of 10 to truncate any uneven year to a corresponding decade by remultiplying that value by a 10 afterwards. I used this column during a ```groupby``` call by ```Decade``` following ```Square Footage``` and a ```sum()``` statement to get the square footage per decades calculated and ready for my visualization. The rest of the plot follows a similar logical approach as the previous one. I decided to use ```mark_line()``` to achieve my intended goal. My encodings included ```X```, ```Y``` and ```tooltip```. I decided to leave my ```color``` for the line default, but did add some blue under the curve shading via an additional ```mark_area```. For ```X``` and ```Y``` in both ```mark```s, I used the ```Decades``` as my ordinal X and the summed up ```Square Footage``` as a quantitative. ```Tooltip``` followed the same declaration as the first plot. Final touch ups included another X-axis label flip like the first plot and appropiate title. 

With this visualization, we can clearly see that 1920 and 1960 have peaks in them. We could claim that during the Roaring 20s, the area attracted individuals that were willing to put money into big development. The next big sprawl being around 1960, coming right after WWII veterans would go on to pursue education, thus perhaps a sprawl to deal with the incoming influx of future generations of students as academia became an important factor within American societal values. 
<vegachart schema-url="{{ site.baseurl }}/assets/json/line_chart.json" style="width: 100%"></vegachart>

In overall, I think both of these visualizations contain information that complement each other, giving an impactful insight into the growth of Urbana-Champaign as an area over the last 100 plus years. The interactivity allows for a shift in colors if the differentiation between different types of buildings is hard to establish, as well as a 10 year range that facilitates a closer look within given timeframes without making the plot too overwhelming with every single year listed on there (besides the first initial overall showcase).

 As far as overlap with Homework #5 goes, I believe the most I have done is reutilize the group approach for my data transformation. Other than that, I tried to be original with this submission for both plots and don't believe it overlaps massively (if at all).

## Search The Data & Methods

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/jnaiman/online_cv_public/blob/main/python_notebooks/test_generate_plots.ipynb" text="The Analysis" %}
</div>


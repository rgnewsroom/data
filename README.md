# Data

Data is fun. This repo is here to help you figure out the best way to use it. Here is a general workflow for a story with data involved.

## General workflow

### 1 - Get it

The first step is to find the data. You can either stumble upon it or, if you know exists, ask nicely/FOIA for it.

When you are trying to acquire data it's important to figure out the format of the data before you get it. Your default format should always be **CSV**, or comma-separated values. This is a text format of a basic spreadsheet and Excel can open it easily. Several other data visualizers accept CSV easily.

You want to avoid expensive formats like SPSS which requires software to retrieve or flat PDFs which cannot be used at all. When in doubt, ask the web team.

### 2 - Clean, analyze, verify

Once you have the data you probably want to get it into a format that is easy to analyze and verify. There are many ways to go about this. The simplest and most common is just shoving it into Excel. That's a great first step. You may also want to try out [Google Fusion Tables](https://support.google.com/fusiontables/answer/2571232). Once you have it in a useable program you'll want to clean the data, AKA: make sure it all works properly.

### 3 - Viz

Now that you have analyzed the data and understand it better, it's time to visualize it. This can get extremely complicated or can stay very simple, it's up to the data and the story. Check out our collection of [useful tools and links](https://github.com/rgnewsroom/data/wiki/Useful-tools-and-links). For 95 percent of all data you probably want either a map or a bar chart. Simple solutions for these are Google Fusion Tables (maps and graphs, seriously, they're awesome), [StoryMapJS](https://github.com/rgnewsroom/data/wiki/How-to-edit-StoryMapJS-packages) (map only) or [plotly](https://plot.ly/) (graphs only).

### 4 - Embed

Now that you have completed your data viz, you need to embed it into your story. To do so you need to find the embed code for your visualization. Now, each service hides embed codes in different places but generally they are under a 'Publish' or 'Share' button/menu. If not, Google the service and figure out how to get the embed code.

Then paste that code into the WebHTML DTtag field if you want it at the top, above the headline, or in the WebEmbed field if you want it below the story.

## Useful tools and links

### Charts and graphs

Tool | Description | Difficulty (1-10) | Responsive | $$$
---  | --- | --- | --- | ---
[Chartist.js](https://github.com/gionkunz/chartist-js) | Simple responsive charts | :question: | :white_check_mark: | :question:
[cssplot](https://github.com/asciimoo/cssplot/) | CSS charts base library | :question: | :white_check_mark: | :question:
[C3.js](http://c3js.org) | Unofficially: D3-based chart library that eliminates the need to write D3 code. Officially: D3-based reusable chart library. | 5 | :white_check_mark: | :white_check_mark:
[Chart.js](http://www.chartjs.org/) | Simple, clean and engaging charts for designers and developers | | :white_check_mark: | :question: | :white_check_mark: 
[Dygraphs.js](http://dygraphs.com/) | The Dygraphs.js library allows developers to create interactive charts using the X and Y axis to display powerful diagrams. The more data being parsed, the higher the functionality of the graph. Line graphs only. | :question: | :question: | :question:
[D3.js](https://github.com/mbostock/d3) | D3 is capable of creating stunning graphics via dynamically updating the DOM. | 5 |  :white_check_mark:  |
[Epoch](http://fastly.github.io/epoch/) | A general purpose real-time charting library for building beautiful, smooth, and high performance visualizations. | :question: | :question: |
[InfoVis a.k.a. JIT](http://philogb.github.io/jit/) | The JavaScript InfoVis Toolkit provides tools for creating Interactive Data Visualizations for the Web. | :question: | :question: |
[The Google Visualization API](https://developers.google.com/chart/) | Display live data on your site: Google’s Visualization API can be called with barely any code. | 2 | :question: | :question:
[Springy.js](http://getspringy.com/) | Springy.js is a JavaScript library that relies on an algorithm to create force-directed graphs, resulting in nodes reacting in a spring-like manner on the web page. | :question: | :question: |
[dimple](http://dimplejs.org/) | The aim of dimple is to open up the power and flexibility of d3 to analysts. |:question: | :question: |
[Sigma](http://sigmajs.org/) | Sigma is a JavaScript library dedicated to graph drawing. It makes easy to publish networks on Web pages, and allows developers to integrate network exploration in rich Web applications. | :question: | :white_check_mark: |
[Raphaël](http://raphaeljs.com/) | Raphaël is a small JavaScript library that should simplify your work with vector graphics on the web. | :question: | :question: |
[gRaphaël](http://g.raphaeljs.com/) | gRaphaël’s goal is to help you create stunning charts on your website. | :question: | :question: |
[Ember Charts](http://addepar.github.io/#/ember-charts/overview) | A charting library built with the Ember.js and d3.js frameworks. | :question: | :question: |
[plot.ly](https://plot.ly/) | Online GUI but can also be used with Python for interactives. Online GUI is in beta and cannot embed graph. May be able to soon. Has great spreadsheet and graphing interfaces. [Python docs](http://nbviewer.ipython.org/github/plotly/python-user-guide/blob/master/s0_getting-started/s0_getting-started.ipynb) look a lot more extensive than online stuff. | online: 1 python: :question: | :white_check_mark: |
[matplotlib (Python)](http://www.randalolson.com/2014/06/28/how-to-make-beautiful-data-visualizations-in-python-with-matplotlib/?utm_source=Python+Weekly+Newsletter&utm_campaign=3010720f4e-Python_Weekly_Issue_146_July_3_2014&utm_medium=email&utm_term=0_9e26887fc5-3010720f4e-312712941) | Seems to be a simple way to create graphics. | 6 | :white_check_mark: |

### Maps

Tool | Description | Difficulty (1-10) | Responsive | $$$
---  | --- | --- | --- | ---
[Topline](https://github.com/ajam/topline) | A jQuery wrapper for ProPublica's Stateline library, adding some no-fuss tooltips, legends and source lines. | :question: | :white_check_mark: | Free 
[Mapbox GL](https://www.mapbox.com/blog/mapbox-gl/) | Mapbox is an open source mapping platform for developers and designers at enterprise scale. | :question: | :question: | :white_check_mark:
[StoryMap JS](http://storymap.knightlab.com/) | Super easy way to tell a story using a map. Each location acts as a slide. Note: has streets | 1 | :white_check_mark: |
[Polymaps](http://polymaps.org/) | Polymaps is a free JavaScript library for making dynamic, interactive maps in modern web browsers. | :question: | :question: |
[Leaflet](http://leafletjs.com/) | An Open-Source JavaScript Library for Mobile-Friendly Interactive Maps. Requires you to find map tiles. | :question: | :question: |
**GitHub:** [View GeoJSON/TopoJSON Source](https://github.com/blog/1865-view-geojson-topojson-source) | July 23, 2014 | | |
**GitHub:** [GeoJSON rendering improvements](https://github.com/blog/1541-geojson-rendering-improvements) | June 26, 2013 | | |
**GitHub:** [There's a map for that](https://github.com/blog/1528-there-s-a-map-for-that) | June 13, 2013 | | |
[heatmap.js](http://www.patrick-wied.at/static/heatmapjs/) | Dynamic Heatmaps for the Web. | :question: | :question: |
[ColorBrewer 2.0](http://colorbrewer2.org/) | A website that's got mapping-specfic color picking and generating tools. | | | |

### Tables

Tool | Description | Difficulty (1-10) | Responsive | $$$
---  | --- | --- | --- | ---
[Ember Table](http://addepar.github.io/#/ember-table/overview) | Ember table allows you to render very large data sets by only rendering the rows that are being displayed. | 2 | :white_check_mark: |
[DataTables](http://datatables.net) | Responsive, tables that take a number of data types | 2 | :white_check_mark: |

### Page design

Tool | Description | Difficulty (1-10) | Responsive | $$$
---  | --- | --- | --- | ---
[Odyssey](http://cartodb.github.io/odyssey.js/) | A simple way for journalists, designers, and creators to weave interactive stories. Note: no streets, only cities | 2 | :white_check_mark: |
[Present your ideas](http://slides.com/) | Slides is a place for creating, presenting and sharing presentations. | 3 | :question: | [Freemium](http://slides.com/pricing)
[Snapshot.js](https://github.com/Wildhoney/Snapshot.js) | Node.js app for slicing and dicing paginated chunks of data with easy sorting and filtering. | :question: | :question: |
[Parsehub.com](https://www.parsehub.com/) | Turn dynamic websites into APIs | 2 | :question: | [Freemium](https://www.parsehub.com/pricing)
 
### Potential data sources:

* [The GDELT Project: A Global Database of Society](http://gdeltproject.org/)

### [Knight Lab Publishers' Toolbox](http://projects.knightlab.com/#toolbox):

* TimelineJS - Beautifully crafted timelines that are easy and intuitive to use.
* SoundCiteJS - Making inline audio easy and seamless.
* twXplorer - A smarter way to search Twitter.
* StoryMapJS - Maps that tell stories and are easy to build.
* JuxtaposeJS - Before/after slider that takes the best of all the others.

### [Mozilla OpenNews Source Code Index](http://source.opennews.org/code/)
An index to the open code being written in journalism, fully tagged and searchable.

### Useful/Interesting:

* [Present your ideas](http://slides.com/): Slides is a place for creating, presenting and sharing presentations.
* [Snapshot.js](https://github.com/Wildhoney/Snapshot.js): Node.js app for slicing and dicing paginated chunks of data with easy sorting and filtering.
* [heatmap.js](http://www.patrick-wied.at/static/heatmapjs/): Dynamic Heatmaps for the Web.
* [Parsehub.com](https://www.parsehub.com/): Turn dynamic websites into APIs
* [sheetlabs](https://sheetlabs.com): Turn your spreadsheets into APIs effortlessly.
* [Elm](http://elm-lang.org/): Elm is great for 2D and 3D games, diagrams, widgets, and websites. Graphs and charts

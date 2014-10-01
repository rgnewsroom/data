# [DataTables](http://datatables.net/)

## Getting started

This example will be using the workflow to change print quick facts into a [DataTable](http://datatables.net/). The page in question was published 9/26/14 and can be found [here](http://pages.registerguard.com/farm-harvest-entertainment/).

### 1) Get your data

In this example we're taking paragraph of information and breaking it up into a format that DataTables can recognize. You can think of it as taking a sentence like: `Mary has five apples and two oranges while Billy has 3 apples and one orange.` While this sentence makes sense, it can also be displayed as tabular data:

| Name | Apples | Oranges|
| ---- |:------:| ------:|
| Mary | 5      | 2      |
| Billy | 3     | 1      |

This example is really easy, but when you have 20 quick facts that are each 100 words long, manual input would take too long.

So let's take a look at an example quick read:

```
Bush’s Fern View Farms: 90536 Territorial Highway, Junction City; 541-935-6362. Fall harvest highlights include a U-pick pumpkin patch, a hay maze (no charge), freshly pressed apple cider made from farm apples, 15 to 20 varieties of apples, and plenty of fall décor, including corn stalks and gourds. Open through Oct. 31. Weekend hours: 11 a.m. to 6 p.m. Saturdays and noon to 5 p.m. Sundays.
```

On top of this information there are also colored dots next to name of the farm indicating whether or not the farm has: U-pick pumpkin patches, special features, rides, seasonal treats, or fall décor.

So go ahead and copy and paste all of the quick facts into a text editor like Sublime Text 3 or Text Edit.

### 2) Clean the data and analyze it. Then verify it looks good.

Now, let's take a step back and ask ourselves, what do we want this table to look like? What fields do we want to include? In this case we want Farm (text/link), U-pick pumpkin patches (checkmark), special features (checkmark), rides (checkmark), seasonal treats (checkmark), fall décor (checkmark), address (text), phone (text), description (long text).

That's a lot of information and we can already tell that it's not going to display well all together in one table, but we can address that later. For now we need to break up the grafs into something we can use. Usually, the simplest way to go about that is to create a CSV that we can pull into Excel and edit. But in order to create a CSV we need to figure out how we can manipulate the current structure into comma separated values.

In the quick read above you can see the format goes Name: Address; Phone. Description. **Note: There are commas in the Description so we'll need to account for these.**

Let's go ahead and Find & Replace all of the commas in the Description with something like: `@#$`. That way we can go back later and find the commas and put them back in.

Now, let's go in and Find & Replace all of the colons and semicolons with commas. That way we can at least separate those fields. Then do a Find on periods. Replace each one after the Phone with a comma.

Save that text file as something.csv and try opening it in Excel. If it worked your info should be somewhat formatted correctly. Go ahead and give the table a headings and make sure all of the data is formatted nicely. You may have to go in and clean more.

Go ahead and replace your `@#$` string back to commas. **Note: When you save the CSV again you'll want to make sure that the fields are wrapped in quotes. This will allow the description to have commas within it and not break.**

Add columns for the checkmarks you need to add. Add the `&check;` HTML character to the fields which need it based off of what the quick reads say. This process is manual, sorry.

At this point you should have all of the data that you want! Order the columns how you want them to appear in the table.

**Verify that all of the data is correct and accurate. This is journalism.**

[My CSV](https://github.com/rgpages/farm-harvest-entertainment/blob/gh-pages/harvest.csv).

### 3) Visualize it (with DataTables)

Now, DataTables accepts a whole bunch of [data formats and you can read up on them here](http://datatables.net/examples/data_sources/index.html). I chose to use an external JSON array queried by AJAX because I found a [good example](http://datatables.net/examples/data_sources/ajax.html) of how to implement that. Also, I wanted an easy to edit data file outside of the index. This will allow me to re-use the template and just call the new data file.

Since I opted to do JSON we have to convert the CSV to JSON. If you [Google "csv to json"](https://www.google.com/webhp?#q=csv+to+json) there are a bunch of options. I chose [this one](http://www.convertcsv.com/csv-to-json.htm) for no real reason. Mostly, it was first.

![json](https://cloud.githubusercontent.com/assets/4853944/4425153/65b601f2-45a6-11e4-8197-320bdfe23ea7.gif)

Copy and past and copy and paste. I don't think I changed any defaults and I chose the JSON array.

Now, create a new text file and type:

```json
{
    "data":
}
```

Paste the JSON array after the colon. If you want to check it go use a [JSON linter](http://jsonlint.com/) and it'll get formatted too!

Save that file as data.json or something and include it in your site folder. Include CSS and JS resources for DataTables and the extension [Responsive](http://datatables.net/extensions/responsive/).

Make a table:

```html
<table id="datatable" class="display responsive" width="100%">
	<thead>
		<tr>
			<th class="all">Farm</th>
			<th class="none">Address</th>
			<th class="none">Phone</th>
			<th class="min-tablet-l">U-pick pumpkins</th>
			<th class="min-tablet-l">Mazes & events</th>
			<th class="min-tablet-l">Rides</th>
			<th class="min-tablet-l">Seasonal treats</th>
			<th class="min-tablet-l">Fall d&eacute;cor</th>
			<th class="none">Description</th>
			<th class="all">More info</th>
		</tr>
	</thead>
</table>
```

Note the table class responsive and the th classes. These make sure the columns you want display at the breakpoints you want. See [here] for more info on that.

You'll also note that I have a column called "More info". This is an empty column I added in to the CSV and then redid the JSON file so that I could have a column for the Responsive `+`. See [here](http://datatables.net/extensions/responsive/examples/child-rows/right-column.html) for more info on that.

This is how I instantiated the table:

```javascript
$(document).ready(function() {
	$('#datatable').dataTable( {
		"ajax": 'data.json', // get data
		"paging": false, // We only have 20 so we don't want paging (it breaks at 10)
		"info": false, // Turn off the header and stuff
		"oLanguage": {
			"sSearch": "" //This kills the Search label, below I mess with the search box
		},
		"responsive": {
			"details": {
				"type": 'column',
				"target": 9 // targets the column with id 9 to put the `+`
			}
		},
		"columnDefs": [ {
			"className": 'control',
			"orderable": false, // turn off the controls for that column
			"targets": 9
		}]
	});

        // this is where I mess with the search box
	$('#datatable_filter input').attr("placeholder", "Search... (example)").wrap("<div class='bat_wrap pure-form'></div>").addClass("pure-input-rounded");
});
```

Here is the styling I changed:

```css
/* DataTables array */
#datatables{
	text-align: center;
	font-family: Arial, sans-serif;
}
#datatables_filter{
	float: none; /* search box stuff */
}
#datatables_filter label input{
	width: 100%;
	margin: 0;
}

/* This stuff styles the Responsive + to become what mine looks like */
#datatables_wrapper td.control:before{
	left: 0;
	height: auto;
	width: 100%;
	margin: 0;
	position: relative;
	color: black;
	border: none;
	line-height: auto;
	box-shadow: none;
	content: 'Expand';
	background-color: rgba(0,0,0,0);
	text-decoration: underline;
}

/* Styles child rows */
#datatables_wrapper .child li{
	text-align: left;
	max-width: 600px;
	margin: 0 auto;
}

table.dataTable.no-footer{
	border-bottom: 1px solid #dddddd;
}
```

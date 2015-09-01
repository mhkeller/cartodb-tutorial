Maps and Data
=============

> Adapted and updated from the [Nicar '14 session](https://github.com/csvsoundsystem/nicar-cartodb-postgis) by Andrew Hill and Michael Keller


# Your account

http://`LOGIN_NAME`.cartodb.com

# Introduction to CartoDB

[CartoDB](http://cartodb.com) is an open source tool hosted as an online service. Anyone can create a free account and for those more adventurous, the source is available on [GitHub](http://github.com/CartoDB/CartoDB).

![cartodb_intro](https://github.com/csvsoundsystem/nicar-cartodb-postgis/blob/gh-pages/assets/gifs/cartodb_intro.gif)

#### Tutorials

You can find a long list of tutorials, both written and video, on [the CartoDB website](http://developers.cartodb.com/tutorials.html)

#### Documentation

As you learn more about CartoDB, start digging into the [online documentation](http://developers.cartodb.com/documentation/apis-overview.html)

CartoDB allows you to make more than just maps, it can help you build entire geospatial applications. There is an easy to use [Javascript library](http://developers.cartodb.com/documentation/cartodb-js.html) that you can use to integrate maps, geospatial data, and SQL queries into your website. 

#### Support

As you start expirementing more you'll want to know about the [GIS StackExchange](http://gis.stackexchange.com/questions/tagged/cartodb). If you tag questions with ```cartodb```, ```postgis``` or both you will get great help from the community. Just remember to keep question titles short and descriptive. Same goes for the question content, keep it short and to the point. Include links to code (preferably code that wont disappear in the future) or include portions of relevant code for potential helpers to better understand your problem.


### Using the dashboard

The CartoDB dashboard is broken down into a few different interfaces. 

##### The table manager

This is the first page you see when you load your account. It is where you will drag new files for upload or create new blank tables. You can see and delete existing datasets here.

##### The table view

When you load a new dataset or load an old one, you'll be brought to the table view. The table view lets you look at the ```columns``` and ```rows``` of your data. You can edit individual values. You can change column names and types. You can filter your data and query it using ```SQL```.

##### Map view

From any table, you can click ```Map``` to see the map of the data. As long as your data contained some geospatial information, it should appear on the map. From here, you can style and edit your geospatial data. It is a good place for prototyping published visualizations.

##### "Maps"

Whenever you want to publish a map or combine multiple map layers into a single map to be published, you'll create what is called a ```Map```. Maps live above datasets. They are linked directly to the data in your tables, but you can change the styles and filters of a map as much as you like. Maps do not take up more space on your account. So from one dataset, you can publish many visualizations.

### Importing data

Importing data into CartoDB is easy! All you need is a file in a supported format (CSV, KML, GeoJSON, and Shapefile are all good ones) either online or on your desktop. You can drag local files right to your browser to import. Remote files you can import by pasting the URL into the import field.

#### Datasets

| File          | Dataset name     | Geom type |
| ------------- |:----------------:|:---------:|
| [counties_ne.zip](https://github.com/csvsoundsystem/nicar-cartodb-postgis/raw/gh-pages/data/counties_ne.zip) | Nebraska Counties   | polygons |
| [postoffices_ne.zip](https://github.com/csvsoundsystem/nicar-cartodb-postgis/blob/gh-pages/data/postoffices_ne.zip?raw=true) | US Post Offices | points |

##### Four ways to get data into CartoDB

1. Drag and drop a file or a ZIP to you dashboard
2. Import from a URL
3. Add new data to a row in your tables or by drawing on the map
4. Use authenticated [SQL API](http://developers.cartodb.com/documentation/sql-api.html) calls to write data

![import](https://github.com/csvsoundsystem/nicar-cartodb-postgis/blob/gh-pages/assets/gifs/import.gif)

#### First data import

Let's start by importing the dataset of Nebraska Counties.

1. Right click the [counties_ne.zip link](http://csvsoundsystem.github.io/nicar-cartodb-postgis/data/counties_ne.zip), copy URL to clipboard
2. Go to your CartoDB dasboard in the table manager
3. Click ```New table```
4. Paste the data URL into the form field
5. Click ```Create table```

## Creating maps

### Basic map styling

##### Choropleths, Category maps, Bubble maps

![styling](https://github.com/csvsoundsystem/nicar-cartodb-postgis/blob/gh-pages/assets/gifs/styling.gif)

There are many styles possible in CartoDB. The tool includes a simple style wizard for you to apply and customize just some of these. When you grow out of the wizard, you'll want to dig into the CSS editor to really customize your maps.

##### Infowindows and legends

You can add infowindows and legends to any maps you create. There are some nice simple tools for you to create and customize. As you learn more though, you can also take advantage of full HTML templating to make them look and behave exactly as you want.

![infowindows and legends](https://github.com/csvsoundsystem/nicar-cartodb-postgis/blob/gh-pages/assets/gifs/legends.gif)

### Maps

Let's start by importing the second dataset of Nebraska Post Offices. Go back to your table manager, then

1. Right click the [postoffices_ne.zip link](http://csvsoundsystem.github.io/nicar-cartodb-postgis/data/postoffices_ne.zip), copy URL to clipboard
2. Go to your CartoDB dasboard in the table manager
3. Click ```New table```
4. Paste the data URL into the form field
5. Click ```Create table```

Now that we have our Post Office dataset, let's create a visualization. You do this by clicking the ```VISUALIZE``` button in the upper right. Next, give your visualization a name. This will take you to a new visualization where you can publish you can finalize design, add new layers, or publish your map.

### Combine layers

Visualizations allow you to mix multiple datasets into a layered map. You can add a new layer by clicking the plus sign directly above the right-hand menu.

![infowindows and legends](https://github.com/csvsoundsystem/nicar-cartodb-postgis/blob/gh-pages/assets/gifs/layers.gif)

You can reorder the layers on the map by dragging layers up through the stack. Each layer can be styled and edited independantly. You can also add interactivity and legends for the layers. 

### Publish maps

Right away you can get a public link for your visualization. Where the button ```VISUALIZE``` used to be, it should new say ```PUBLISH```. From there you can get the menu for publishing maps.

![infowindows and legends](https://github.com/csvsoundsystem/nicar-cartodb-postgis/blob/gh-pages/assets/gifs/visualize.gif)

##### Links, embeds, CartoDB.js

Publishing maps can be as simple as getting the sharable URL. The interface also gives you an ```embed``` option for adding maps to your blog or website. It also has an ```API``` option, for using your visualization with our [CartoDB.js](http://developers.cartodb.com/documentation/cartodb-js.html) library. CartoDB.js will allow you to integrate highly customized maps directly into your website. For now, sharable URLs and map embeds should get you pretty far.


# Introduction to SQL

SQL stands for Structured Query Language and is used to work with large datasets. We're using a dialect of SQL called [PostgreSQL](http://www.postgresql.org/docs/9.4/interactive/index.html). It's a more powerful version of SQL. To make PostgreSQL know about maps and geospatial things, we use an extention called [PostGIS](http://postgis.net/).

## Operators

* `>` e.g. `SELECT * FROM table WHERE year > 1880`
* `<`
* `=`
* `AND`
* `OR`
* `IS NULL` e.g. `SELECT * FROM table WHERE year IS NULL`
* `IS NOT NULL` e.g. `SELECT * FROM table WHERE year IS NOT NULL`


### Filtering, ordering, limiting

Let's start working with historic Post Offices in Nebraska: `postoffices_ne`.

Click on the `SQL` tab we can start doing some basic querying.

##### Filtering: `WHERE`

SQL can filter using the `WHERE` command. These commands can be read like a sentence, subsitituing the `*` for the words "all columns". For example, the first one would read as "Select all columns from our postoffices_ne spreadsheet where the year is less than 1860."

````sql
SELECT * FROM postoffices_ne WHERE yr_est < 1860

SELECT * FROM postoffices_ne WHERE elev < 400

-- filter by two conditions
SELECT * FROM postoffices_ne WHERE yr_est > 1860 AND yr_est < 1870

-- filter by with an OR
SELECT * FROM postoffices_ne WHERE yr_est > 1890 OR elev < 300

-- More complex OR and AND
SELECT * FROM postoffices_ne WHERE (yr_est > 1870 AND yr_est < 1899) OR elev > 1400

-- Filtering by a string value
SELECT * FROM postoffices_ne WHERE county = 'FILLMORE COUNTY'
````

**Note: Notice how string names are in single quotes. We've been pretty agnostic between single and double quotes. SQL, however, pays close attention. Always put strings in single quotes. Double quotes are used to identify column names. This is optional, but in case our columns needed to be case-sensitive, you could do the last query like this:**

````sql
SELECT * FROM postoffices_ne WHERE "County" = 'FILLMORE COUNTY'
````

##### Ordering: `ORDER BY`

Order by yr_est made

````sql
SELECT * FROM postoffices_ne ORDER BY yr_est

SELECT * FROM postoffices_ne ORDER BY yr_est DESC
````

You can also set `ASC` for ascending, which is the default.

##### Limiting: `LIMIT`

Instead of showing every row, you can limit your query. This can be useful to make your queries faster or decrease the files size of your data export.

Grab the first five

````sql
SELECT * FROM postoffices_ne LIMIT 5
````

This data isn't in any order though, so that query isn't very helpful. This will grab the five oldest.

````sql
SELECT * FROM postoffices_ne ORDER BY yr_est LIMIT 5
````

Or you can grab the five highest

````sql
SELECT * FROM postoffices_ne ORDER BY elev DESC LIMIT 5
````

Or find the average year established

````sql
SELECT avg(yr_est) FROM postoffices_ne 
````

### Selecting, counting

##### Selecting

We've been doing `SELECT` statements to create a view on our database. You might have noticed the `*`, which means "Get all columns". You can also only retrieve specific columns by name.

````sql
SELECT county, yr_est, elev FROM postoffices_ne LIMIT 10
````

Because this is a spatially-aware database, we also have a column that holds our lat/lng. PostGIS usually refers to this column as `geom` or `the_geom` in CartoDB.

````sql
SELECT county, yr_est, elev, the_geom FROM postoffices_ne LIMIT 10
````

##### Counting

Let's say you want to know some aggregate information, like how many rows you have

````sql
SELECT count(*) FROM postoffices_ne

SELECT count(*) FROM postoffices_ne WHERE yr_est > 1880
````

Let's import some new data for this, **rename the table to `inspection_data`.

* NYC Restaurant reviews (download it in xls format) — https://nycopendata.socrata.com/Health/DOHMH-New-York-City-Restaurant-Inspection-Results/xx67-kt59

One of the most powerful abilities of SQL is to `GROUP BY` different elements in your data.

Let's count how many restaurant inspects exist per borough

````sql
SELECT count(*) FROM inspection_data GROUP BY boro
````

How about borough and cuisine type?

````sql
SELECT count(*) FROM inspection_data GROUP BY boro, cuisine_description
````

How about by grade

````sql
SELECT count(*) FROM inspection_data GROUP BY grade, cuisine_description
````

You can do a few different **aggregate** functions such as the max, min, avg or sum. 

````sql
SELECT max(elev) FROM postoffices_ne

SELECT min(elev) FROM postoffices_ne

SELECT avg(elev) FROM postoffices_ne
````

**Note: Some SQL environments require each line to be terminated with `;` like in JavaScript. CartoDB is very forgiving, however.

#### Exercises

* Find some data on NYC Open Data and map it. 
* Find some incident level data analyze it through aggregate functions

#### More resources

The PostgreSQL documentation has a great walkthrough of the language. Going through the Preface, Chapter 1 Tutorial and Chapter 2 The SQL Language for a start: <http://www.postgresql.org/docs/9.4/interactive/index.html>


## Updating data

So far, we've just been SELECTing data, which creates a view on our table — it doesn't modify our data.

If we want to modify the data, maybe to clean it, we run an `UPDATE` statement.

````sql
UPDATE friends SET location = replace(location, '(', '')

-- Make a new column `latitude`

UPDATE friends SET 	latitude = split_parts(location, ',', 1)

UPDATE friends SET 	longitude = split_parts(location, ',', 2)
````

## Where to find data

* NYC Data: <http://www.nyc.gov/html/dcp/html/bytes/applbyte.shtml>
* NY State: <http://gis.ny.gov/?nysgis=>
	* Almost every state has a GIS clearinghouse that will have shapefile data
* Environmental / geographical : <http://www.naturalearthdata.com>
* Census data + shapefiles: <http://censusreporter.org/>
* Census Tigerline data. All congressional districts, counties etc: <http://www.census.gov/geo/maps-data/data/tiger-line.html>
	* More direct link: http://www.census.gov/cgi-bin/geo/shapefiles2014/main

## BONUS: Joining data

* <https://github.com/Vizzuality/CartoDB-Tutorials/tree/master/joining-data>

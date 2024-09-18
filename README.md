# python-api-challenge
"What is the weather like as we approach the equator?" In the first part of this week's challenge, I am going to show evidence that as you approach the equator, the weather gets hotter. Additionally, I will analyze the correlation between latitude and various weather measurements such as humidity, wind speed and cloudiness.

Then, in the second half of this week's challenge, use geoviews to illustrate locations on a map that I'd ideally vacation to based on filtering a data set of locations around parameters suchs as my ideal temperature and humidity.


## How I went about it.

## 1. WeatherPy

Within the notebook titled "WeatherPy.ipynb", numpy.random.uniform was called on a range of latitude and longitudes to generate coordinates for number of places around the globe. 

<p align="center">
<img src="Images\Screenshot 2024-09-17 160243.png" width="500px">
</p>

Those coordinates were then use to search via API in geoapify's database for the associated Cities. A data frame is created containing the randomly generated cities and saved to a csv. Then, using geoapify, various information such as a city's max temperature or its humidity is extracted and stored into the data frame to be used for analyzing their correlation to latitude.


<p align="center">
<img src="Images\Screenshot 2024-09-17 160322.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 160357.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 160420.png" width="500px">
</p>

The created datafame used for analysis

<p align="center">
<img src="Images\Screenshot 2024-09-17 160436.png" width="500px">
</p>

Scatter plots were used to analyze the relationship between a city's latitude and various metrics.

Latitude Vs. Temperature
<p align="center">
<img src="Images\Screenshot 2024-09-17 160611.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 173355.png" width="500px">
</p>

Latitude Vs. Cloudiness
<p align="center">
<img src="Images\Screenshot 2024-09-17 160733.png" width="500px">
</p>

Latitude Vs. Wind Speed
<p align="center">
<img src="Images\Screenshot 2024-09-17 160747.png" width="500px">
</p>

Latitude Vs. Humidity
<p align="center">
<img src="Images\Screenshot 2024-09-17 173746.png" width="500px">
</p>



To Further analyze the relationship between latitude and these metrics, the data is seperated into Northern and Southern hemisphere for a more accurate assessment of their differences. A linear regression model is plotted onto the scatter plots and the r-values of the models are assessed.

Latitude Vs. Temperature
<p align="center">
<img src="Images\Screenshot 2024-09-17 160915.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 160933.png" width="500px">
</p>

Discussion about the linear relationship:

Upon reviewing the regression model, we can see evidence that as you a approach 0 degrees Latitude, the equator, Max temperatures increase. Furthermore, for both the north and south hemisphere, we see an r-value above .7. This presents a case for strong correlation between temperature and latitude.  

Latitude Vs. Humidity
<p align="center">
<img src="Images\Screenshot 2024-09-17 175844.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 175859.png" width="500px">
</p>

Discussion about the linear relationship:

It appears that the relationship between Latitude and Humidity is not linear. Here we see an r-value less than 0.3, which suggest none or very little correlation between the them. Furthermore, in the sample drawn for the southern hemisphere, it seems humidity is contrated around 80. With an x (latitude) coefficient of 0.07 calculated for the sample drawn, as latitude goes up and down humidity would not be very responsive.


Latitude Vs. Cloudiness
<p align="center">
<img src="Images\Screenshot 2024-09-17 180150.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 180206.png" width="500px">
</p>

Discussion about the linear relationship:
The relationship between latitude and cloudiness does no appear to be linear and the correlation (r-value) between the two ranges from none/very weak to week. 

As more of a discussin than an analysis, I want to say this makes sense because clouds formation is probably heavily influenced moisture in the air and moisture in the air is likely tied to a city's proximity to bodies of water. Therefore, two cities on the same latitude but having vastly different proximities to water may experience vastly different cloudiness. I believe this can be observed in both the northern and southern figures as latitude points are experiencing multiple cloudiness data entries. 

Latitude Vs. Wind Speed
<p align="center">
<img src="Images\Screenshot 2024-09-17 182917.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 182941.png" width="500px">
</p>

Discussion about the linear relationship:

In the Northern hemisphere, wind speed seems to have a very week correlation with Latitude as my current sample generated an r-value of about 0.05. This suggest that the relationship betweeen the two is not lineaer and the graph captures that.

The southern hemisphere on the other hand is a little less obvious given my sample. While the (absolute) r-value generated is about 0.33, suggesting a weak correlation, a decent concentration of the obseervation is centered around the regression model. This may be a case of having to use discretion on the significance of latitude on wind speeds in the south as at a glance, this model may be heavily influenced by outliers preventing a closer fitting model.

As more of a discussion, I'm not sure if southern hemisphere's data has less variance than the north because theres generally less landmass/cities in the souther hemispere. 


## 2. VacationPy

The saved data frame of cities is then read into a second python script, VacationPy where I use the data frame to map locations I'd ideally vacate to using geoviews. To start, the cities data frame is plotted onto a map for visualizations using hvplots.

<p align="center">
<img src="Images\Screenshot 2024-09-17 185120.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-17 185139.png" width="500px">
</p>

Next, the data was filtered to a subset of locations I would ideally vacate to given various parameters suchs as the locations humidity and max temperature. Using Geoapify API, the nearest hotel to a city's listed coordinates within 10km radius is recorded into the Data frame in a new column.

<p align="center">
<img src="Images\Screenshot 2024-09-18 003422.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-18 003501.png" width="500px">
</p>

<p align="center">
<img src="Images\Screenshot 2024-09-18 004635.png" width="500px">
</p>

Finally, those cities I would like to vation to are plotted onto a map with interactive hover points that detail a city's coordinates, humidity, country and nearest hotel

<p align="center">
<img src="Images\Screenshot 2024-09-18 004946.png" width="500px">
</p>





## closing and challenges
This week's assignment was mostly straight forward as it went over topics covered in class and the provided sample script was thorough. That said, I still faced a few challenges.

Firstly, I had to define a code that could perform linear regression given appropriate arguments. While I managed this, I was not sure how to include a title and annotations within the code without causing conflicts later on. Especially for the annotations, it just seemed eaiser to coordinate it after the graph was plotted so that it did not overlay/clutter with useful information. Then, I was not sure how to extract variables that were defined within this regressing function for later use. To make it work, I had to have my regression code "return" the slope value of a line as output so I can use it as needed.

A second issue I ran into was that when using annotate, it would print the text I wanted in the graph. I tried playing with the arguments annotate received but I could not find the one that removed the printed text.

Lastly, I only had notes for dropping columns from a data frame, but I wanted something that selected the columns to keep instead. Watching the youtube videdo below I came across .filter() (its possible this came up in class and I didnt make note of it). So I am crediting the video below for me using .filter().
 https://www.youtube.com/watch?v=kB7FV-ijdqE -  Filtering Columns and Rows in Pandas | Python Pandas Tutorials by Alex The Analyst

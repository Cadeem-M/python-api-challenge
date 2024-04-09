# python-api-challenge
"What is the weather like as we approach the equator?" In the first part of this week's challenge, I am going to show evidence that as you approach the equator, the weather gets hotter. Additionally, I will analyze the correlation between latitude and various weather measurements such as humidity, wind speed and cloudiness.

Then, in the second half of this week's challenge, use geoviews to illustrate locations on a map that I'd ideally vacation to based on filtering a data set of locations around parameters suchs as my ideal temperature and humidity.


## How I went about it.
To go about this week's challenge, numpy.random.uniform was called on a range of latitude and longitudes to generate coordinates for number of places around the globe. Those coordinates were then use to search via API in geoapify's database for the associated Cities. A data frame is created containing the randomly generated cities and saved to a csv. Then, using geoapify, various information such as a city's max temperature or its humidity is extracted and stored into the data frame to be used for analyzing their correlation to latitude.

The saved data frame of cities is then read into a second python script where I use the data frame to map locations I'd ideally vacatae to using geoviews.



## closing and challenges
This week's assignment was mostly straight forward as it went over topics covered in class and the provided sample script was thorough. That said, I still faced a few challenges.

Firstly, I had to define a code that could perform linear regression given appropriate arguments. While I managed this, I was not sure how to include a title and annotations within the code without causing conflicts later on. Especially for the annotations, it just seemed eaiser to coordinate it after the graph was plotted so that it did not overlay/clutter with useful information. Then, I was not sure how to extract variables that were defined within this regressing function for later use. To make it work, I had to have my regression code "return" the slope value of a line as output so I can use it as needed.

A second issue I ran into was that when using annotate, it would print the text I wanted in the graph. I tried playing with the arguments annotate received but I could not find the one that removed the printed text.

Lastly, I only had notes for dropping columns from a data frame, but I wanted something that selected the columns to keep instead. Watching the youtube videdo below I came across .filter() (its possible this came up in class and I didnt make note of it). So I am crediting the video below for me using .filter().
 https://www.youtube.com/watch?v=kB7FV-ijdqE -  Filtering Columns and Rows in Pandas | Python Pandas Tutorials by Alex The Analyst

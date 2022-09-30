# Miniproject 2

### [Assignment](assignment.md)

## Project/Goals
This project pulls restaurants, bars, landmarks, and arts & entertainment business data in a 3km radius from my parents house in Barrhaven, Ottawa. The information is pulled from seperate sources, Foursquare and Yelp, to build a database. The data from each source are compared to draw conclusions on quality and coverage of the area.

## Process
### Testing & choosing POI categories
-Created a function to pull the APIs
-As the limit of results was only 50 per call, I ran 5 calls with varying categories to collect the POIs that I wanted (restaurants, bars, landmarks, and arts & entertainment)
### Parse and Normalize 
-Read through the output files and then nornalized the data. From reading the output json it was aparent that the "categories" key inlcuded a nested dictionary with additional features. 
-Normalized a seperate table for the categories data
-Concatenated the normalized data from each of the 5 calls into one master df and one category df.
### Create Database
-Create a database to store all 4 tables into sqlite3 (two foursquare, two yelp)
-Created the 4 tables from the 4 dfs
-Tested simple queries. 

## Results
-I used pandas to analyse the data.
-At the surface I would say that the foursquare API has better coverage than Yelp. Yelp does not have data for international locations. Yelp serves north american and their most popular destinations such as western europe. 
-After comparing the data from both souces, I would still say that Foursquare has more quality data because:
    1. Their rating system is out of 10 with increments of 0.1 which based on the data produces a better insight on the rating of the retaurants. The yelp rating is out of 5 with only 0.5 increments. I feel that this rating system is less effective. 
    2. Foursquare returns a distance column, which makes filtering by distance more accessible. Say I want to find all the restaurants with a rating > 8.0 within 1km, this can easily be done without any further calculations. Yelp does provide the lat,long of the POI, but it's nested and would take some geo-math to calculate the distance. 
    3. As someone who is familiar with the data, I can concur that the foursquare results are in fact very popular restaurants in the area. I don't think the yelp results are of high enough quality to provide a conpetitive response. 

The best feature of the yelp data set was the review_count column. I find this strengthened a given rating. 

## Challenges 
-The further along in the process I got, the more I was able to re-shape what I wanted my data to produce. This was bittersweet because as I ran out of time I had better and more clear ideas of how to structure the data.
-For example, I structured my data in the following way to easily answer the "top 10 restaurants", but knew this was not "clean" data. After thinking about it, I did come up with a better way to structure my tables, but it was too late to change.
![Alt text](/images/DB_structure.jpg "DB_structure")
-My .schema file is empty, not sure if that is purposeful.

## Future Goals
-This is how I should have structured by database:
![Alt text](/images/ideal_DB_structure.jpg "ideal_DB_structure")
-would like to combine the lists to have one row for each place and their ratings from each site

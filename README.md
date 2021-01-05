# Muddling-through-Berlins-sublet-shadow-prices

This project maps room prices in Berlin from WG-Gesucht and compares them with the BAföG housing rate: Since the fall semester 2019/2020, students in Berlin with full BAföG entitlement receive 861€ per month from the government. In addition to the 427€ for basic needs and 109€ for the statutory health insurance, students receive 325€ for housing costs. Comparing room prices on WG-Gesucht to this amount highlights how high housing costs for students have become in contrast to what the government deems reasonable, partly because flatshare rooms posted on WG-Gesucht find ways to circumvent housing price regulations from the city, such as the recently passed rent price cap. 
To this end, we scrape room postings from the beginning of the Fall Semester 2020 (October-November) in Berlin, match their addresses with polygons and map the resulting dataframe as a Berlin heatmap in relation to how much higher/lower room prices are comapred to the BAföG housing rate.

Have a look at this presentation for an intuitive overview of the project: https://drive.google.com/file/d/1NsjDQEjSBXxnV9UrgtHOm0HLD5WJkuv7/view?usp=sharing

## Step 1: Building a web scraper for the website WG-Gesucht 

As a first step for the project, we scraped the room price, number of roommates, district, street and house numer of room postings in Berlin. In order to avoid needing to click on each posting with the Selenium package, we only scraped the available information from the overview pages using the BeautifulSoup package. In total, we scraped ~2400 room postings between October and November. 


## Step 2: Data cleaning

After scraping the room posting information, we cleaned the data as much of the scraped information still had undesired html content or was not given in a standardized way. 


## Step 3: Geocoding 

Then we created an account for the Google Maps Platform to use the free credit on the generated API-key to geocode (convert addresses into earth coordinates) our data. We did this by building a function that creates the fitting url for each of our addresses to request the geo-information on an address from the API and extracts only the longitude and latitude data points. Then, we used this function on our dataset. 


## Step 4: Visualisation (MAIN FILE TO RUN)

In order to run the visualisation, the following steps have to be first followed:
1) Install/load the packages in the packages file.
2) Upload the scraped and cleaned dataframe (df_final_polygone.csv)
3) Upload the shapefile of Berlin (neighbourhoods.geojson)

We first prepare the dataframe for the visualisation, by dropping observations with missing geocode (some adresses were too incomplete for Google Maps to find), splitting the geo information into latitude in longitude and creating a subset of the data with only the room prices and the geoinformation. 
We then load the shapefile of Berlin to obtain geoinformation on postal codes. 
We then perform a spatial join between our geodataframe from WG-gesucht and the shapefile, in order to match which adresses are located in which postal code area.
We also drop all observations with a price below 200€, as we noticed the data included some weekly, instead of only monthly, rents.

For the visualisation, we choose four different plots. First, a basic plot of our WG-gesucht data on the shapefile, to get a better idea of the distribution of adresses in the city. Second, a heatmap of the aggregated prices in our data per postal code. Third, we create a variable of the price difference between the room prices and the BAföG housing rate for students and again plot this as a heatmap. And fourth, plot create categories of how affordable different postal codes are for students receiving BAföG government aid, and also plot this as a heatmap. 

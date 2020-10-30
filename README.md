# Muddling-through-Berlins-sublet-shadow-prices


## 1. Step (done): Building a web scraper for the website WG-Gesucht 

As a first step for our project, we need to scrape the room price, number of roommates, district, street and house numer of room postings in Berlin. To do that, we first tried out Selenium to access each single jobposting and scrape the information from there. This was quite messy and eventually we figured out that all the information we need is actually already included in the overview pages of the room postings - without needing to click on each posting itself. We therefore switched to BeautifulSoup. Since we realised that the total number of over 6000 postings in Berlin includes many undeleted ones from earlier years, we also decided to only scrape only postings from 2020 (the first 60 pages) - and then optionally extend that by adding new postings later on. 

### Team contributions so far
- Draft of slides and presentation of project pitch (Clara)
- Revisions and design support of presentation slides (Golo, Gero)
- Assessment of the WG-Gesucht website, division of web scraping task into smaller, concrete steps and first attempts (Gero, Clara)
- Web scraping attempt using Selenium (Golo)
- Final web scraping code with BeautifulSoup (Gero, Golo)
- Preparation of github repository and midt-term report/readme file (Clara) 

### Tasks that we plan to do for this step in the coming 2 weeks: 
- Clean the existing dataframe - one variable currently contains three of the information types we need and needs to be entangled (Gero)
- Create a loop that repeats the code and adds new postings to the dataframe in an automated way - once per day/week (Clara, Golo)


## 2. Step (to follow): Comparing the apartment/room prices to a rent price indicator 

We initially planned to store the scraped information in a dataframe and then build a program that types this information into a comparator website for the Berlin rent price cap. These websites then print out how much higher/lower the respective apartment price is to what it should cost - which we then wanted to visualize. 

After trying out many of the comparator websites we realized that building such a program is quite complicated, and that, more importantly, the results rely on many assumptions about the standards in the respective apartment, making the results of the analysis hard to interpret and unreliable. We therefore decided to compare our scraped room prices with the BAföG housing rate: Since the fall semester 2019/2020, students in Berlin with full BAföG entitlement receive 861€ per month from the government. In addition to the 427€ for basic needs and 109€ for the statutory health insurance, students receive 325€ for housing costs. Comparing room prices on WG-Gesucht to this amount highlights how high housing costs have become in contrast to what the government deems reasonable, partly because flatshare rooms posted on WG-Gesucht find ways to circumvent housing price regulations from the city, such as the recently passed rent price cap. In this scenario, we also don't need to compute the net rent price of entire flats, but simply use the full room price (including utilities) indicated at the very top of each posting. 

### Tasks that we plan to do for this step in the coming 2 weeks: 
- Create a variable in the dataframe that deducts the room price of each listing from the 325€ BAföG housing cost rate


## 3. Step (to follow): Visualising room price information in a (possibly interactive) map of Berlin

One of our ideal, dream rolemodels for such a map can be found here: https://interaktiv.morgenpost.de/so-alt-wohnt-berlin/
We are considering to use "dash" at the moment, but will also think about other options in the coming weeks. 

### Tasks that we plan to do for this step in the coming 2 weeks: 
- Get familiar with dash and research other potential options how to visualise the data (everyone)

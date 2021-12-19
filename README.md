# Analysis of Travel Destinations

:bar_chart:
### For the whole presentation of my approach/ workflow and the interactive visualization of the insights, please see this Tableau story:

https://public.tableau.com/views/TravelDestinationAnalysis/Story1?:language=de-DE&publish=yes&:display_count=n&:origin=viz_share_link

### :memo: Observation in data quality

- Acceptable data quality one can good work with to get insights about travel destinations users are interested in 
- Original data set contained:  231.493 rows and 11 columns
- After cleaning: 29 % less rows and 2 deleted columns 
- Null values: 
  - 24% in User_city_source2: Dropped these rows, as this information is crucial for the origin-destination analysis 
  - 39% in trip_duration: Removing negative values and replacing zeros with the overall mean (14 days) 
- Redundant columns: user_source_city1 and user_source_country1 have not been considered for further analysis. Same information as in user_city_source2.
- Decided to continue origin-destination analysis with user_city_source2 as it contains more unique cities and less null values 

### :bulb: Insights and search trends

- 231.493 searches for travel destination have been conducted between 27.07.2019 and 15.09.2019 
- Searches from 7.025 different user cities to 1.011 destination
- Most popular user cities are Dubai, Jeddah, Riyadh & destinations are Cairo, Istanbul, Abu Dhabi
- Most searches/flights within the Arabic countries, short-distance flights and short term searches (days to departure) 
- Average days to departure over all destinations is 28 days. But there is a trend, that searches are more short-term at the beginning of the period  (at end July, beginning August) and develop to more long-term searches from end of August on.
- This could show, the spontaneous searches for summer holidays for end August/September. This affects especially destinations like Cairo or Abu Dhabi where summer is too hot in August. 
- Searches for European destinations, e.g. Paris develop the other way round, they become more short-time towards the end of the observed period


### :dna: Correlation between data points 

- Analyzing correlation with Pearson correlation coefficient for numerical variables of data set days_to_departure, trip_duration and distance
- No correlation/ dependence between any numerical variable

- Analyzing correlation with Chi Square Test of Independence, including hypothesis testing for nominal/categorical variables user_city_source2, user_country_source2, website_language, searched_destination 
- Chi Squared Test shows correlation between user_city_source2 and searched_destination (asserted p-value 0.0)
- Chi Squared Test shows correlation between user_country_source2 and searched_destination ( asserted p-value 0.0) 
- Chi Squared Test shows correlation between website_language  and searched_destination (asserted p-value 0.0)
- But I found a limitation of the Chi Square Test for this data set as one condition for its use is not meet: no more than 20% of the cells should have an expected count of less than 5 / cells in the contingency table should have q frequency of 5 or less.
- Approach to solve this: Applied test only on rows where the combination website_language and searched_destination appears at least 6 times. P-values remained 0.0

- Idea for further statistical test to apply: likelihood ratio test (G-test)



### 💻 Data Set

- user_ID: Unique User ID
- user_city_source1: User City from Source 1
- user_country_source1: User Country from Source 1
- search_ts: Time the user performed the search
- user_city_source2: User City from Source 2
- user_country_source2: User Country from Source 2
- website_language: Search Language
- days_to_departure: Days to departure from search_ts
- trip_duration: Duration of the searched trip in days (start date - end date). The data set provided does not have these dates
- searched_destination: Search Destination
- distance: Distance of search destination from User City 


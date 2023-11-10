# Project #3 : Strategic Placement of New Offices

# Introduction

This project seeks to identify the optimal location for a gaming company's offices based on specific predefined criteria. The decision-making process relies on data analysis and the utilization of geospatial information.

<br>
 
# Data Source
<br>

The data used for the project includes:

- A mongodb database containing information on over 18.000 companies worldwide.

- A geojson file of London's neighborhoods from GitHub.

- External sources such as Skyscanner searches to supplement the analysis.


<br>

# Workflow & methodology

**Initial exploration**: The src/exploration notebook focuses on the analysis of the "companies" collection through queries to mongodb. This initial exploration aims to select the appropriate city and define three potential office locations.

**Requests to Foursquare**: The src/requests_to_collections notebook contains functions to retrieve information, using Foursquare API, related to the location of various points of interest based on the given criteria. This requests are converted into a suitable format and incorporated into mongodb as collections. 

**Analysis**: In src/analysis notebook, the requested data is cross-referenced with the London neighborhoods' geojson to analyze the content of each neighborhood and decide on the final location.

**Visualization**: The src/visualization.py component focuses on creating maps that offer a better understanding of the analysis and support the decision made.

<br>

# Requirements/Libraries Used:
This code was written in Python/Jupyter Notebook, using the following libraries:
<br>
- pandas
- json
- requests
- folium

<br>


# Initial criteria

The following list contains the given criteria based on the employees requests: 

- 20 Designers : nearby companies that also do design
- Nearby schools since 30% of the company staff have at least 1 child
- 15 Developers: near successful tech startups that have raised at least 1 Million dollars
- 20 Account Managers: ease of travelling 
- 10 Executives: a starbucks not too far
- Party places for all the employees
- CEO: Close by vegan restaurant
- Office dog: dog hairdresser
- Maintenance guy: a basketball stadium should be around 10 Km


The following matrix shows the criteria used to make the location decision. They are positioned based on their priority and their ease of meeting. A criterion is considered a priority if it affects a larger number of staff members in the company.

<br>

![criteria_matrix](https://github.com/patriciazapatab/project-3/blob/main/images/criteria_matrix.png?raw=true)

<br>

# Analysis and results

### City selection

The selection of the city was based on the number of companies related to design and video games in each location. The three cities with the most companies were San Francisco, New York, and London.

To decide among these three cities it was taken into account the easiness for travelling, particularly to Asian countries were the gaming industry is strong and helds many events. For instance, we compared the prices to fligh to the Global Gaming Expo Asia in Macau on June 2024. 

![flight_costs](https://github.com/patriciazapatab/project-3/blob/main/images/flights_comparison.png?raw=true)


Due to travel times and costs, London is chosen as the ideal city to locate the new offices. 


### Neighborhood selection

Once selected the city, those design or video games companies in London that had raised more than 1M$ were filtered. This left us with three companies with valid addresses in London, which were considered as possible locations.

These companies were situated in the neighborhoods of Camden, Kensington & Chelsea. Next step was to compare the meeting of other criteria such as places to party, schools, Starbucks and vegan restaurants in each neighborhood. For this, a London neighborhoods geojson was crossed with the foursquare queries. The selected companies locations were considered as the middle point and venues were looked in a 1km radius. The radius was selected as a close enough distance to go walking from the offices. 


![neighborhood_maps](https://github.com/patriciazapatab/project-3/blob/main/images/radius_maps.png?raw=true)


The following table resumes the count of each time of criteria in each neighborhood:
<br>

![count_table_marked](https://github.com/patriciazapatab/project-3/blob/main/images/count_table_marked.png?raw=true)


As marked, Camden excels in all the considered criteria. It has more clubs and bars for after-work activities, more schools for all age groups, more Starbucks for executives, and a larger offering of healthy and vegan restaurants in the area. Consequently, Camden is selected as the ideal location for the new offices.




### Other considerations

To meet all staff needs, it would be necessary to have a nearby dog salon and a basketball stadium within 10 km from the office.

These two criteria were not prioritized, but some solutions are proposed to meet them. A mobile groomer could be scheduled to visit the office periodically for dog grooming. Additionally, the staff's interest in basketball could be leveraged for team-building activities, such as attending an important basketball game together.


# Conclusions

After finalizing the analysis and visualization of the data the following conclusions are extracted:

 - New offices will be located in the vibrant neighborhood of Camden in the City of London
 
 - The chosen city has a good environment for gaming organizations and growing companies

- London is recognized as a global travel hub with extensive worldwide connectivity

- The new location offers many afterwork options, education facilities for all ages are easily accessible from the office as well as vegan restaurants and nearby Starbucks

- Workarounds are possible to meet criteria not met by the new location.


# Links of interest

- London geojson: https://github.com/natzar/European-Neighborhoods-Json-Coords/blob/master/london.json
- Presentation: https://www.canva.com/design/DAFzZSc_DSA/pUF8cUp-j3QCQ-0kAvqZWg/edit
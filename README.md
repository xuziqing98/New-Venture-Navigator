# Coursera Applied Data Science Capstone Project
### The Battle of Neighbourhood: Where to start the business in Guangzhou?

### Introduction 

In our lives, people are diverse. Some people prefer a cozy lifestyle and choose to work for someone else. However, some people are passionate about challenges, and they start their own businesses to follow their dreams and fulfill their passion. Types of entrepreneurship are diverse, such as opening restaurants, coffee shops, IT companies and so on. Then, a significant problem arises, namely, in which specific location to recommend entrepreneurs to start their businesses. For example, if you want to open a restaurant in Toronto, it is recommended that you open a restaurant on Yonge St, as restaurants are clustered in that area.

The goal of the project is to segment and cluster the neighbourhoods by exploring and comparing the neighbourhoods. By analyzing the clusters, we can figure out the best-recommended location to start a specific type of business. As my hometown is Guangzhou, in this project, we will focus on the neighbourhoods in Guangzhou. Definitely, we can also apply this application to other cities.

### Data

- Neighbourhood data of Guangzhou extracted from: https://en.wikipedia.org/wiki/List_of_township-level_divisions_of_Guangdong  
  - districts information
  - subdistricts information
- Geospatial Coordinates of Guangzhou Neighbourhoods will be obtained by using the **geocode** package. Geospatial Coordinates data is important for getting venues data.
- Venues data of each Neighbourhood will be retrieved by using **Foursquare API**

### Methodology
- Data Requirement
The basic requirement of a neighbourhood should contain its borough, city, latitude, longitude.
- Data Collection
Guangzhou’s neighbourhood data can be collected from Wikipedia, as shown in figure 1. Using requests library, a HTML file is returned  by sending a HTML request to that specific Wikipedia link, listed in the Data section. Then, BeautifulSoup library is needed to extract useful information. The neighbourhood data is written into a csv file. Then, the next step is to transform the extracted data into pandas dataframe, as shown in figure 2.

- Data Understanding and Analysis
  - Geospatial data for each neighbourhood is missing for further exploration. The solution is to use geopy library to get geospatial data for each neighbourhood, as shown in figure 3. Then, with the geospatial data, neighbourhoods can be plotted in the map, as shown in figure 4.
  - Venues information nearby each neighbourhood is required to make a clustering. In this project, the Foursquare API was used to search for the nearby venues of each neighbourhood in a radius of 500 meters. Only venue name and venue category are extracted, as shown in figure 5.
  - Based on the dataset shown in figure 5, creating a new table with top 10 venues for each neighbourhood is required for modeling, as shown in figure 6.
- Modeling and Evaluation
Since the goal is to determine the location to start up a specific type of business, K-MEANS could be a good option. K-MEANS will divide all neighbourhoods into K clusters based on venue categories. In each cluster, neighbourhoods are similar to each other and dissimilar to objects in other clusters. We can analyze the data of each cluster to get insight of the pattern of venues. Then, we could recommend a location for a specific type of business. In the project, I choose K to be 5.

### Result
- Cluster 1 (Red): In this cluster, restaurants (Chinese, Dim Sum, Cantonese, Fast Food), metro station, and stores(shopping mall, convenience store) are most recommended.
- Cluster 2 (Purple): In this cluster, the types of business are diverse. Based on the result, it is likely to be an area for entertainment. Cafe, Restaurant, Shopping Mall, Resort, Park, and Sport Court are recommended.
- Cluster 3 (Blue): In this cluster, Opening a Chinese Restaurant is most recommended as the first most common venues are Chinese Restaurants for most of the neighbourhood in this cluster. Department Store and Women's Store are also recommended.
- Cluster 4 (Mint Green): In this cluster, Opening a hotel is most recommended as the first most common venues are hotels for most of the neighbourhood in this cluster. From the result, the neighbourhoods in this cluster are likely to be areas for tourism. Starting up a tourism-relative business is recommended.
- Cluster 5: In this cluster, Opening a Restaurant is most recommended as the most of the common venues are about dining. However, Cantonese Food is most popular.

### Discussion
As we see in the result section, the number of neighbourhoods in cluster 2 is much more than in the other clusters. The type of venues are diverse in cluster 2, so it is not easy to make a recommendation in the area covered by cluster 2. Using a bigger K may get a better result.

### Conclusion
Overall, as demonstrated in the result section, we can effectively make a recommendation for entrepreneurs to start up different types of business. I hope this can be applied to different cities worldwidely.

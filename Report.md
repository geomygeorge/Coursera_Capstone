# Neighborhood analysis for Airbnb listing in Bristol, United Kingdom



## Introduction

Joanna and Jeff are couple lives in Bristol, United Kingdom.

Jeff is a football coach and Joanna works nearby Tesco.

They want to list their spare rooms  in Airbnb, for additional income. 

Before listing, they want to analyze existing Airbnb listings in Bristol area. 

Typical questions in their mind are:

> What is the distribution of Airbnb listing in Bristol?
>
> What are the characteristics of highly concentrated listing, if there are any?
>
> What is the range of listing prices in Bristol?

They discussed their idea and questions in their mind with one of their friend Anderson.

Anderson is a Data scientist, agreed to help them out.

## Data

[Inside Airbnb](http://insideairbnb.com/new-york-city/) is  an independent, non-commercial set of tools and data that allows you to  explore how Airbnb is really being used in cities around the world.

By analyzing publicly available information about a city's Airbnb's  listings, Inside Airbnb provides filters and  key metrics so you can  see how Airbnb is being used to compete with the residential housing  market.

Bristol Airbnb listing data set consists of **2500+ listings**, which are compiled on 19 May, 2019.

It consists of many useful fields like:

- Neighbourhood

- Geo coordinate of the property

- Room type

- Price

  

  **Example from Bristol Airbnb dataset**

  |      | id     | name                               | host_id | host_name | neighbourhood_group | neighbourhood | latitude | longitude | room_type    | price | minimum_nights | number_of_reviews | last_review | reviews_per_month | calculated_host_listings_count | availability_365 |
  | ---- | ------ | ---------------------------------- | ------- | --------- | ------------------- | ------------- | -------- | --------- | ------------ | ----- | -------------- | ----------------- | ----------- | ----------------- | ------------------------------ | ---------------- |
  | 0    | 70820  | City View - Sarah's double room.   | 360195  | Sarah     | NaN                 | Windmill Hill | 51.43994 | -2.59173  | Private room | 28    | 7              | 138               | 2019-05-03  | 2.03              | 5                              | 59               |
  | 1    | 117122 | City Centre-Waterside Retreat      | 591555  | Marcus    | NaN                 | Clifton       | 51.45051 | -2.61054  | Private room | 65    | 1              | 131               | 2019-03-17  | 1.37              | 1                              | 356              |
  | 2    | 146407 | Sunny Central Artist Cottage (Dbl) | 708175  | Orla      | NaN                 | Southville    | 51.44131 | -2.60271  | Private room | 38    | 2              | 65                | 2019-04-28  | 0.80              | 2                              | 23               |

#### Fetch nearby venues using Forsquare APIs

This data set is supplied with Neighbourhood json file. 

By using Forsquare APIs, near by venues of each neighborhood can be fetched. Which will be used to provide characteristics for each listings.



## Methodology

### Exploratory data analysis

>**Which areas of Bristol have the most Airbnb properties?**
>
>Answer: Ashely, Central and Clifton

![1560374604894](C:\Users\GeomyGeorge\AppData\Roaming\Typora\typora-user-images\1560374604894.png)

> **Which are the most expensive areas?**	
>
> Answer: Central, Clifton Down and Hotwells & Harbourside

![1560375305518](C:\Users\GeomyGeorge\AppData\Roaming\Typora\typora-user-images\1560375305518.png)



> **What are the most common property and room types?**

![1560375961137](C:\Users\GeomyGeorge\AppData\Roaming\Typora\typora-user-images\1560375961137.png)



> **Most common venues in Bristol Neighborhood - Fetched using Foursquare API**	

![1560376251011](C:\Users\GeomyGeorge\AppData\Roaming\Typora\typora-user-images\1560376251011.png)

### Preparing data for Airbnb listing clustering

To cluster property listing, data is prepared by merging property listing data (sourced from inside airbnb dataset) with venue details from foursquare apis.

Each property listing is enriched by adding venues from the neighborhood, where the property is belongs to.

*Final data frame consists of 2558 rows and  117 columns*

##### Clustering algorithm used: 

K-Means

##### Reason for choosing: 

Data set consists of continuous variables.

K-Means is one of the simplest model based on centroids

 

> **What is the optimal no. of clusters?**
>
> Find the optimal no of clusters by using 'Elbow method'

![](C:\MyWork\Learning\Data Science\Coursera\IBM\capstone_presenation\Elbow.png)

##### No. of features used for clustering: 151



## Result

After applying clustering on the data set, Airbnb listing is mapped on Bristol

![1560378100469](C:\Users\GeomyGeorge\AppData\Roaming\Typora\typora-user-images\1560378100469.png)

## Discussion

With above clustering result, east clusters are examined further and provided a summary of each clusters.

#### Cluster Analysis

| Cluster | Price                                                        | Room Type             | Minimum Nights                         | Avg. yearly availability | Most common Venues                                     |
| ------- | ------------------------------------------------------------ | --------------------- | -------------------------------------- | ------------------------ | ------------------------------------------------------ |
| 0       | Low priced listings.Mostly below £40                         | All Private rooms     | Mostly 1 night                         | 162 days                 | Very few venues. Only Cafes are available.             |
| 1       | Medium priced listings. Peaks nearly £100                    | Whole property        | Mostly  2 nights                       | 47 days                  | Most happening place with lots of pubs and parks       |
| 2       | Low priced listings mostly less than £50                     | 99% are private rooms | Mainly 1 night                         | 42 days                  | Most happening place with lots of pubs and parks       |
| 3       | Mix of pricings. Peak near £50. Many listings spotted above £100 | Whole property        | 1 & 2 nights are equal                 | 302 days                 | Lots of venues found. Eateries, parks and playgrounds. |
| 4       | Low priced listings mostly less than £50                     | 99% are private rooms | Mostly 1 night. Also peaks in 2 nights | 276 days                 | Lots of venues found. Pubs, Parks, Indian restaurants. |

## Conclusion 

With above clustering analysis, it is noted that Clusters 1,2 and 3 are most sought after listings in Bristol with plenty of amenities around.

Property type of listings in Cluster 3, are whole properties and it is available for most of the time in an year.

If someone need whole property rent, they can look into Cluster 3.


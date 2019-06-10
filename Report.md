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
> Where will our listing stand, if we list our property ?

They discussed their idea and questions in their mind with one of their friend Anderson.

Anderson is a Data scientist, agreed to help them out.

## Data

[Inside Airbnb](http://insideairbnb.com/new-york-city/) is  an independent, non-commercial set of tools and data that allows you to  explore how Airbnb is really being used in cities around the world.

By analyzing publicly available information about a city's Airbnb's  listings, Inside Airbnb provides filters and  key metrics so you can  see how Airbnb is being used to compete with the residential housing  market.

Bristol Airbnb listing data set consists of 2500+ listings, which are compiled on 19 May, 2019.

It consists of many useful fields like:

- Neighbourhood
- Geo coordinate of the property
- Room type
- Price

#### Fetch nearby venues

This data set is supplied with Neighbourhood geojson file. 

By using Forsquare APIs, near by venues of each neighborhood can be fetched. Which will be used to provide characteristics for each listings.


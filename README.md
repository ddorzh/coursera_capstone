# Coursera Applied Data Science Capstone 

Using Foursquare data to describe Postal Code districts in London, UK and develop district classification.

## Introduction and business problem

London, UK is a large and diverse metropolitan area, home to people of different origins from across the world. Historically, postcode districts in the UK carries a lot of significance in eyes of property buyers and renters. It ‘signals’ information about area, individual property and by extension its owner. Whist this perception is often simplistic and changes quickly over time Postcode districts still feature heavily in mass media and various property-related publications, and attract genuine audience interest. 

Business problem for this capstone project is to describe each London postcode district from perspective of eating out options that it offers and grouping areas together by similarity of their ‘eating out’ profile. Such descriptions could do well in mass media publications, blog posts and for attracting web traffic. It may also become a component of solution for retail and leisure chains location planning, including spotting opportunities and understanding areas of potential expansion. 



## Data 
List of London postal districts and their names was taken from a Wikipedia page:

```
https://en.wikipedia.org/wiki/London_postal_district
```

Each district was passed to Foursquare's 'Explore' API endpoint. 
The request was filtered by two types of venues: 'food' and 'coffee'.

Foursquare returned up to 50 venues for each district case.
Venues we're all collected into a single dataset and de-duplicated by unique ID as some venues appeared in more than one Explore calls.

Districts that had fewer than 30 venues returned were dropped from analysis.

## Methodology

Exploratory statistics showed that composition of categories, and total number of venues varied by district.

For next step, I transformed the list of venues to feature matrix describing each district.
Having noticed that many venue categories appeared only a few times I did the following: 

- Dropped all venues where category appeared fewer than 3 times (approx. 80 were dropped).
- Used a Truncated SVD technique to reduce sparsely populated features from approx. 100 to 10 preserving 85% of the original variance.

Truncated SVD is a simple way to 'extract' variance from a wide matrix whilst preserving most of information.
I used 10 components to achieve 85% of variance captured, additional components were adding little (e.g. next 10 would only add 5%).
No specific methodology was used to arrive to 10 components due to shortness of time, but common techniques are 'elbow' etc. that could be used in this step.

I then put the reduced matrix into a k-means clustering to run a few clustering suggestions. 
I ran 4,5,6 and 7 clusters. 

In all solutions I had a large cluster for outer (residential) districts, and smaller clusters in central and west London.
I stopped at 4 clusters, as they are easily interpretable and overlap with common-sense understanding of London areas.


## Results

Exploratory analysis showed that business areas on London are overflowing with coffee and cafes, sandwich shops etc. to cater for workforce. In addition, areas of South-West, West and East London area well catered by good selection and number of eating out places, pubs and coffee shops.

By far the largest pattern is in residential districts in outer London, particularly in South, East and North. 
These have relatively few and unsophisticated selections of local Cafes, Pizza and Indian restaurants.

When added into a clustering:
	 Business districts of London were grouped together very clearly pointing where office blocks are, extremely high on coffee shops (Cluster 0)
	
	 Low-density and low-variety outer districts formed largest cluster (Cluster 1)
	 Trendier South-West and part of East London were labelled together into Cluster 2 with good number of coffee shops and variety of eateries.
	 West and parts of South London were grouped into a medium-density Cluster 3.
	


## Observations 

With an additional API call (and time) it would be valuable to supplement venue information with average price point and user rating to give richer picture of areas where they are located. However, even now it's easy for anyone to see how well different areas are penetrated by different type of eateries. Residential 'towns' of South-West, parts of East and West London are well catered for reflecting their 'town' feel with well developed High Street. Whereas most of outer districts are rather low-penetrated by eateries and offer low variety of favourites - Italian, Indian and various Cafes.

This descriptive piece can be used by anyone who's thinking of moving to discover whether their target area similar or different to where they currently live, or even discover new areas that they haven't considered previously.

## Conclusion

To conclude, Eating-out establishments mapping overlap very well to existing preconceptions of where 'livelier' areas are, either in town or just outside. With a few more data points (e.g. price points, rating), and more rigour in feature engineering it could become a very interesting tool for producing pieces of content for online publications, blog posts, and property industry.












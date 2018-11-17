# Coursera Applied Data Science Capstone 

Using Foursquare data to describe Postal Code districts in London, UK.

## Introduction and business problem

London, UK is a large and diverse metropolitan area, home to people of different origins from across the world. Historically, postcode districts in the UK carries a lot of significance in eyes of property buyers and renters. It ‘signals’ information about area, individual property and by extension its owner. Whist this perception is often simplistic and changes quickly over time Postcode districts still feature heavily in mass media and various property-related publications, and attract genuine audience interest. 

Business problem for this capstone project is to describe each London postcode district from perspective of eating out options that it offers, highlighting any particular skew and grouping areas together by similarity of their ‘eating out’ profile. Such descriptions would do well in mass media publications, blog posts and for attracting web traffic. It may also become a component of solution for retail and leisure chains location planning, including spotting opportunities and understanding areas of potential expansion. 



## Data description

List of London postcode districts will be produced from open source data, e.g. as below:

```
http://data.ordnancesurvey.co.uk/ontology/postcode/PostcodeDistrict
```

Each district will be assigned a geographical centroid, which will then be passed on to Foursquare Search API. A list of eating out establishments will be returned and transformed to features describing the postcode district. 

Features will be further reduced through PCA to isolate key components, which in turn will be passed to unsupervised learning algorithm.


## COVID-19 Data Exploration Using SQL

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/derekbonilla/COVIDproject/blob/main/COVID%20Project.sql)

### About the ***Our World in Data COVID-19*** dataset
The variables represent all of the main data related to confirmed cases, deaths, hospitalizations, and testing, as well as other variables of potential interest.

The columns in this dataset are:

Our World in Data has made a [full codebook](https://github.com/owid/covid-19-data/blob/master/public/data/owid-covid-codebook.csv) available, with a description and source for each variable in the dataset.


### Getting The Data
For training purposes, I formatted the downloaded dataset into two different CSV files, [coviddeaths.csv](https://github.com/owid/covid-19-data/blob/master/public/data/owid-covid-codebook.csv) and [covidvaccinations.csv](https://github.com/owid/covid-19-data/blob/master/public/data/owid-covid-codebook.csv). My intention was to perform fundamental SQL statements at the beginning and later progress into other techniques like JOINS.


### Importing The Datasets Into PostgreSQL

```javascript
CREATE TABLE coviddeaths
(
iso_code text,
continent text,
location text,
date date,
population numeric,
total_cases numeric,
new_cases numeric
);

```


```javascript
if (isAwesome){
  return true
}
```
### 3. Support the selection of appropriate statistical tools and techniques

<img src="images/dummy_thumbnail.jpg?raw=true"/>

### 4. Provide a basis for further data collection through surveys or experiments

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

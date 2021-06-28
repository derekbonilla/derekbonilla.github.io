## COVID-19 Data Exploration Using SQL

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/derekbonilla/COVIDproject/blob/main/COVID%20Project.sql)

### About the ***Our World in Data COVID-19*** dataset

| <!-- -->    | <!-- -->    |
|-------------|-------------|
| Timespan         | January 28, 2020 - June 25, 2021         |
| Dataset         | Our World in Data COVID-19         |
| Link         | https://ourworldindata.org/covid-deaths         |

The variables represent all of the main data related to confirmed cases, deaths, hospitalizations, and testing, as well as other variables of potential interest.

The columns in this dataset are:

`iso_code`, `continent`, `location`, `date`, `total_cases`, `new_cases`, `new_cases_smoothed`, `total_deaths`, `new_deaths`, `new_deaths_smoothed`, `total_cases_per_million`, `new_cases_per_million`, `new_cases_smoothed_per_million`, `total_deaths_per_million`, `new_deaths_per_million`, `new_deaths_smoothed_per_million`, `reproduction_rate`, `icu_patients`, `icu_patients_per_million`, `hosp_patients`, `hosp_patients_per_million`, `weekly_icu_admissions`, `weekly_icu_admissions_per_million`, `weekly_hosp_admissions`, `weekly_hosp_admissions_per_million`, `total_tests`, `new_tests`, `total_tests_per_thousand`, `new_tests_per_thousand`, `new_tests_smoothed`, `new_tests_smoothed_per_thousand`, `positive_rate`, `tests_per_case`, `tests_units`, `total_vaccinations`, `people_vaccinated`, `people_fully_vaccinated`, `new_vaccinations`, `new_vaccinations_smoothed`, `total_vaccinations_per_hundred`, `people_vaccinated_per_hundred`, `people_fully_vaccinated_per_hundred`, `new_vaccinations_smoothed_per_million`, `stringency_index`, `population`, `population_density`, `median_age`, `aged_65_older`, `aged_70_older`, `gdp_per_capita`, `extreme_poverty`, `cardiovasc_death_rate`, `diabetes_prevalence`, `female_smokers`, `male_smokers`, `handwashing_facilities`, `hospital_beds_per_thousand`, `life_expectancy`, `human_development_index`, `excess_mortality`

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

### Time For Exploration

```javascript
SELECT location, date, total_cases,total_deaths, (total_deaths/total_cases)*100 AS DeathPercentage
FROM public.coviddeaths
WHERE location LIKE '%States%'
AND continent IS NOT null
ORDER BY 1,2
```

With this SQL query I put up the Total Cases against the Total Deaths to find the Death Percentage (likelihood of dying if contracted COVID-19). In the United States, as of June 25, 2021, this percentage was 1.79% vs 5.16% at the same time in 2020.

<img src="images/dummy_thumbnail.jpg?raw=true"/>

```javascript
SELECT SUM(new_cases) AS total_cases, SUM(CAST(new_deaths AS int)) AS total_deaths, SUM(CAST(new_deaths AS int))/SUM(New_Cases)*100 AS DeathPercentage
FROM public.coviddeaths
--WHERE location LIKE '%states%'
WHERE continent IS NOT null
--GROUP BY date
ORDER BY 1,2
```
<img src="images/dummy_thumbnail.jpg?raw=true"/>
Data shows that globally the current Death Percentage as 2.17%


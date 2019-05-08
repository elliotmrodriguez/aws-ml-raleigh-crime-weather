# aws-ml-raleigh-crime-weather

Predicting crime in Raleigh based on weather. Data from 2013.

Inspired by the [Example Project](https://github.com/aws-samples/amazon-sagemaker-architecting-for-ml/tree/master/Example-Project) used in AWS SageMaker Architecting for ML course.

One can look in Academic Researcher or [Google](https://www.google.com/search?q=crime+increase+when+temperature+rises) and read lots of research papers and articles describing how temperature increases affect propensity to commit crime (especially violent crime).

This project aims to establish a link between temperatures and weather conditions in Raleigh to see if one can predict increases or decreases in crime throughout the city.

## Data Sets

Under the datasets folder are the two datasets used for this project:

- [Raleigh Police Incidents - SRS](https://data-ral.opendata.arcgis.com/datasets/raleigh-police-incidents-srs/data?orderBy=INC_DATETIME) - while the link to the dataset covers January 2005 to June 2014, the data set used here is only for the year 2013. Also note that specific location informastion is not provided to protect the identities of minors and sexual violence victims.
- [NOAA Weather For Raleigh 2013](https://www.ncdc.noaa.gov/cdo-web/webservices/v2#datasets) - queries for temperature highs and lows, precipitation, and more across all Raleigh area weather stations. Note that stations identified as in the Raleigh area do not necessarily fall within the city limits (Fuquay Varina, Apex, Cary, and other areas are included with the data). Because the police incident dataset includes latitutes and longitudes but not crime locations, we cannot exact locations and temperatures at crime sites.

## Modeling Strategy

- Break up crimes by type and by day, correct any sampling issues
- Average temperature highs and lows across all areas
- Link both data sets
- Assess using multi-class classification whether the weather forecast also can predict an increase in a given set of crimes

## Issues/Difficulties

- NOAA data collection only supports a small set of data at a time, and does not support basic web scraping techniques, so my initial data queries were collected manually
- NOAA API requests only support JSON responses
- Raleigh crime data does not have specific location data
- Potential for data variance in the weather data set (in calculating averages, for example - it is not known as of this writing whether a couple of degrees in either direction is statisitically significant)

## Future Enhancements/Ideas

- Sort out web scrape so we can request JSON and convert to CSV
- Isolate locations with provided lat/long in police incidents dataset and cross reference weather stations for more precise temperature data
- Add other data from previous years
- Trend analysis based on previous years (temperature increases, specific crime increases)

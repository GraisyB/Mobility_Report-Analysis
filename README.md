# Mobility_Report-Analysis

Data:

``SELECT *
FROM `bigquery-public-data.covid19_google_mobility.mobility_report` 
LIMIT 100 ``

Meta:

* Understanding the data set? Is it time series? What is the granularity of the data?
``SELECT *
FROM `bigquery-public-data.covid19_google_mobility.mobility_report` 
WHERE country_region_code = 'IN'
AND sub_region_2 = 'Bangalore Urban'
ORDER BY date``

Business Questions Answered
* Average change in baseline for Bangalore Urban for retail indicator?
``SELECT 
avg(retail_and_recreation_percent_change_from_baseline) as retail_change
FROM `bigquery-public-data.covid19_google_mobility.mobility_report`
WHERE 1=1
    AND country_region_code = 'IN'
    AND sub_region_2 = 'Bangalore Urban'``
* Average change in baseline for Bangalore for all indicators in 2020 and 2021?
``SELECT substr(string(date),1,4) as year
,avg(retail_and_recreation_percent_change_from_baseline) as retial_change
,avg(parks_percent_change_from_baseline) as parks_change
,avg(grocery_and_pharmacy_percent_change_from_baseline) as grocery_change
,avg(transit_stations_percent_change_from_baseline) as transit_change
,avg(residential_percent_change_from_baseline) as residential_change
FROM `bigquery-public-data.covid19_google_mobility.mobility_report`
WHERE 1=1
    and country_region_code = 'IN'
    and sub_region_2 = 'Bangalore Urban'
GROUP BY year``
* US and India comparison on all indicators

* Peaks and dips in India (change from baseline)

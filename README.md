# ETL Project - TECHNICAL REPORT- Crime Data Analysis

## Introduction

I analysed the crime data for two large US cities, namely Boston, Los Angeles. For the scope of this project, I concentrated on 
September 2015 data. We took two datasets from two different sources mentioned below and transformed them to create the dataframes 
about the Incident Details, Offense Details and the Location Details. We loaded the analysed data into the sqlite database.  
Loaded table data is used to Visualize such as "Comparison data of top ten streets with most crimes between Boston and LA"

## Extract 

My first dataset is from Kaggle.com.  This dataset contain "Crimes in Boston"

[Crimes in Boston](https://www.kaggle.com/ankkur13/boston-crime-data "Crimes in Boston")

My second dataset is from data.lacity.org which has data of Crimes in LA from the year 2010 to present. 

[Crime Data from 2010 to Present- Los Angeles](https://data.lacity.org/A-Safe-City/Crime-Data-from-2010-to-Present/y8tr-7khq "Crime Data from 2010 to Present")

I decided to choose September of 2015 as those timeframes were common between the dataset and had adequate 
amount of data needed for the project.

## Transform

* Offense Code group - was not found in both the csv files so could not use it . 

* Date Occurred column - was in different format so we had to format it to the same format.

* The fields had null values so we had to do dropna to cleanup the nan values.

* The location column had latitude and longitude in the same column so we had to split the values in separate columns

* The data types of the latitude and the longitude columns were by default set to 'string' so we had to convert those columns to 'float' to create the heat map.

* We had to rename the columns to common column names so that two cities dataframes can be inserted to the same table


## Load

I decided to use SQLlite to load our transformed data, because the data retrieved from the csv files are structured. 
I used SQLAlchemy to interact with the SQLlite databse. The database was named as crime.db. We created "Incident_Details", 
"Offense_Details" and "Location_Details" to best represent the data from transformed dataset. 

Provided below is the data of each table we created , after we retrieved the loaded data from SQLlite database and 
converted to DataFrames. 

#### Incident_Details:


  | ID |INCIDENT_NUMBER| OCCURRED_ON_DATE  | STREET                         | OFFENSE_CODE    |
  | -- | ------------- | ---------------   |--------------------------------| --------------- |
  | 1  | I152105605	   |2015-09-01 00:00:00|	CLEVELAND PL	                |2629             |           
  | 2  | I152072583	   |2015-09-01 00:00:00|	SELDEN ST	    	              |3114             |
  | 3  | I152079669	   |2015-09-01 00:00:00|	THOMAS PARK	                  |3115             |
  | 4  | I162077971	   |2015-09-01 00:00:00|	COLONEL MICHAEL J. MCDONO	    |1106             |
  | 5  |I162087104	   |2015-09-01 00:00:00|	FILOMENA RD		                |1107             |


#### Offense_Details:

|OFFENSE_NUM| OFFENSE_CODE  | OFFENSE_DESCRIPTION             |
|---------- | ------------- | --------------------------------|
| 1         |	2629	        | HARASSMENT                      |
| 2         | 1102	        | FRAUD - FALSE PRETENSE / SCHEME |
| 3         |	1102	        | FRAUD - FALSE PRETENSE / SCHEME |
| 4         |	1102	        | FRAUD - FALSE PRETENSE / SCHEME |
| 5         |	1107	        | FRAUD - IMPERSONATION           |

#### Location_Details:

| LOCATION_NUM  | CITY            | LAT          | LONG            | STREET          |
| ------------- | --------------- |------------- | --------------- | --------------- |
| 1             | Boston          |42.31514179   | -71.06704709    | COLUMBIA RD     |
| 2             | Boston          |42.34438811   | -71.1405858     | ALLSTON ST      |
| 3             | Boston          |42.30443502   | -71.06862907    | TOPLIFF ST      |
| 4             | Boston          |42.29089749   | -71.06156671    | SEMONT RD       |
| 5             | Boston          |42.27882383   | -71.09777223    | COLORADO ST     |




## Visualize 


<img src="https://github.com/arsasvk/ETLproject/blob/master/Images/Street%20names%20with%20Top%20ten%20highest%20crime%20counts_September%202015.png" alt="Streets Vs Crime counts in Sep 2015" height="50%" width="50%">
This visualization show a comparison of top ten streets with most crime counts between the Boston and Los Angeles during Sept 2015. 


### Built With

* Pandas
* Matplotlib
* SQL Alchemy
* SQLlite

### Author 

* Meenakshi Nadimuthu

Project Team: 
  Ana Sofia Galan
  Juan Eduardo Delgado
  Alfredo Velarde
  
Our project will gather data from the following sources:
- Usage of bicycles in Mexico City, from the Ecobici program. 
- Air quality, from Mexico City's Environmental Agency. 
- Temperature in Mexico City, from the National Center for Environmental Information. 

Mexico City’s Air Temperature, Ecobici usage and air quality from January 2019 to August 2019

Extract
-	From the National Center for Environmental Information we extracted through and API the information on Temperature in Mexico City. From NOOA we created an arrangement on the information we required to extract precipitation and temperature.
For every type of information, we required, a call back to the API was made. The information gathered was appended into a list.
-	For the usage on Ecobici, we extracted the information on csv format from the official website of Ecobici program.
Each row corresponds to a single bicycle usage. 
-	As for the information on air quality in Mexico City, these databases where extracted from Mexico City's Environmental Agency as XMLs and where transformed to a csv format.
The information extracted included all the observations registered per each station. 

Transform
-	We created a data frame with the all the dates from January 2019 to August 2019. In this data frame we appended the information extracted from NOOA API. 
-	For the information from Air Quality, first we had to change all data points containing the values -99 to 0, since these are null values. After all values where changed, an average was performed in order to have a single data point per day.
-	 For Ecobici, we appended the different databases into a single data frame and kept the columns we required: day, average on user’s age and total amount of bicycles used per day.
-	After the three data frames where created, we merged the information from the different sources into a single data frame using as primary key the dates and dropping the columns that weren’t required. At the end the information kept was:
o	Date
o	Precipitation
o	TempAvg
o	TempMin
o	TempMax
o	Bici
o	Edad_Usuario
o	n_CO
o	n_UVA
o	n_UVB

Load
-	To load the final data base, we chose SQL since this is a more structured layout. 
-	We created a connection to the data base using sqlalchemy. 
-	Using pgAdmin, we created the table required to receive the date frame created. 
-	We set the date as the table index, and the loaded the information to sqlpostgres.

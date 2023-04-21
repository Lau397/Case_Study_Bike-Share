# **Study Case: Cyclistic**

*Company's description:* Cyclistic is a bike-share company in Chicago that'd like to grow its success through maximizing the number of annual memberships.

As part of Cyclistic's marketing strategy they created flexible pricing plans:
 - single-ride passes
 - full-day passes
 - annual memberships  

Customers who purchase single-ride or full-day passes are referred to as **casual riders**. Customers who purchase annual memberships are **Cyclistic** members.

# Business task
### What we're trying to solve is the following Cyclistic's goal: ***Design marketing strategies aimed at converting casual riders into annual members.***
 
 The marketing analyst team needs to better understand how annual members and casual riders differ, why
 casual riders would buy a membership, and how digital media could affect their marketing tactics. The manager and their team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

# **ASK**
What we're trying to solve is that we want Cyclistic to become more successful by making casual riders more interested in becoming annual members.
* How do annual members and casual riders use Cyclistic bikes diferently?

# **PREPARE**
## Data sources
The data selected is from March 2023 available at: https://divvy-tripdata.s3.amazonaws.com/index.html
In which the trip data such as; started_at, ended_at, start_station_id, end_station_id, geolocation, among others is registered in an Excel file.

The data seems reliable in a way that values make sense and that, generally, it is consistent in each column of data registered. The data is also very recent at the moment of writing this and the information registered in the file is easy to understand.

## Data manipulation

### 🌟**Organizing data**
The data provided was examined initially by checking general statistics, size of the data frame, and the columns that are given. The latter were studied to determine if all of them are going to be useful in the data analysis process. 

The type of data for each column, making sure that the information in them made sense for all of them. 

In the cases where the data type was not correct then type casting was excuted to assign the correct type to that column, which was the case of the time columns, such as; started_at, ended_at. Finally, the format of the datetime columns was revised to see what math operations can be executed and what insights are possible to get from this data.

### 🌟**Data cleaning**
Most of the data was good in terms of consistency. The presence of other special characters in the data, was not the case for this dataframe, as in the previous step we verified that the data type was consistent for all the columns. 

The presence of duplicated data was revised and later on, the columns with data that were not considered relevant for the analysis such as the location (station names), were removed. 

Same thing for the NaN values, these were checked in the dataframe, having found only 183 of these in two columns that are going to be considered in the analysis: ending latitude and ending longitude. For these existing NaN, it was decided to keep them all since these were considered a very small percentage (0.07%) out of the total data available, so it was best to keep them and assign them their repective mean value instead.











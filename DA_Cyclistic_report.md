# **Study Case: Cyclistic** 🚲📖 

This is the report for the data analysis project, a company named Cyclistic.

***Company's description:*** *Cyclistic is a bike-share company in Chicago that'd like to grow its success through maximizing the number of annual memberships.*

As part of Cyclistic's marketing strategy they created flexible pricing plans:
 - single-ride passes
 - full-day passes
 - annual memberships  

Customers who purchase single-ride or full-day passes are referred to as **casual riders**. Customers who purchase annual memberships are **Cyclistic members**.

# **Business task** 💼
### What we're trying to solve is the following Cyclistic's goal: ***Design marketing strategies aimed at converting casual riders into annual members.***
 
 * The marketing analyst team needs to better understand how annual members and casual riders differ, why
 casual riders would buy a membership, and how digital media could affect their marketing tactics. The manager and their team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

# **1. ASK**
What we're trying to solve is that we want Cyclistic to become more successful by making casual riders more interested in becoming annual members.
* How do annual members and casual riders use Cyclistic bikes diferently?

# **2. PREPARE**
## Data sources 🗂
The data selected is from March 2023 available at: https://divvy-tripdata.s3.amazonaws.com/index.html
In which the trip data such as; started_at, ended_at, start_station_id, end_station_id, geolocation, among others is registered in an Excel file.

The data seems reliable in a way that values make sense and that, generally, it is consistent in each column of data registered. The data is also very recent at the moment of writing this and the information registered in the file is easy to understand.

To make sure the data is going to be ready to analyze, a data cleaning process will be done.

To work on this project the following tools are used:
* Jupyter Notebook
* Anaconda: Visual Studio
* Python version: 3.9.13
* Python libraries that will be installed as the Data Analysis progresses
* Git/GitHub to save the project remotely

# **3. PROCESS**
## Data manipulation 📚

For this step, the following Python libraries were used (in that order) to accomplish further analysis of the data:          
    ✔ Pandas   
    ✔ Datetime  
    ✔ GeoPy        
    ✔ Matplotlib         
    ✔ NumPy    

### 🌟**Organizing data**
The data provided was examined initially by checking general statistics and size of the dataframe. The Cyclistic's dataframe provided was found to have 258678 rows and 13 columns in total.

The dataframe columns were studied to determine if all of them are going to be useful in the data analysis process or not. 

The type of data for each column was printed in the code in order to make sure that the information in them made sense for all of them. 

In the cases where the data type was not correct then type casting was excuted to assign the correct type to that column, which was the case of the time columns, such as; started_at, ended_at. Finally, the format of the datetime columns was revised to see what math operations can be executed and what insights are possible to get from this data.

Two aditional columns were created for further analysis using the information in the original dataframe: 
- The column 'time_of_day' to know what time of the day the users used Cyclistic's service most often.
- The column 'day_of_week' to know what day of the week is more frequent by customers.
- The column 'day_of_month' to find how frequent the customers are during the month.

These three columns were obtained using the 'started_at' column.

Other features from the dataframe were identified:
- The column 'rideable_type' has 3 different types of bikes: electric, classic and docked.
- The column 'member_casual' has 2 different types of users: annual members and casual members.
- The type of user most registered in the dataframe is: annual members with a ~76% from the total (casual members with ~24%).

### 🌟**Data cleaning**
Most of the data was good in terms of consistency. The presence of other special characters in the data, was not the case for this dataframe, as in the previous step we verified that the data type was consistent for all the columns. 

The presence of duplicated data was revised and later on, the columns with data that were not considered relevant for the analysis such as the location (station names), were removed. 

The NaN values, these were checked in the dataframe, having found only 183 of these in two columns that are going to be considered in the analysis: ending latitude and ending longitude. For these existing NaN, it was decided to keep them all since these were considered a very small percentage (0.07%) out of the total data available, so it was best to keep them and assign them their respective mean value instead.

* Further data manipulation included as well calculating the time length of each customer ride registered. The difference between the columns 'started_at' and 'ended_at' was transformed in seconds and then, to the same units, minutes. 
* GeoPy a Python library was installed and imported to obtained the distance for each ride in order to study it further along the data analysis. This was possible thanks to the longitude and latitude values present in the data frame, using 'geopy.distance.geodesic'.
* Columns that were no longer going to be used after doing any of the previous processes mentioned were dropped, and new columns with the latest results were created.

# **4. ANALYZE**
## Analysis summary 🤓
The analysis began with a data study as detailed as possible, through the statistics after any transformations and the plots by the end of the Jupyter Notebook. 
* First, the categorical data was identified. Columns: rideable_type and member_casual. The stations names, after taking a look at the information there, it was explicit that there was no pattern for these names, as these vary a lot and are different points within the city, so these were not considered and dropped from the dataframe.
* The amount of unique values of the categorical data was:
    - For the rideable_type column: electric_bike ➡ 148575, classic_bike ➡ 107083, and docked_bike ➡ 3020
    - For the member_casual column: member ➡ 196477 (~76%), and casual ➡ 62201 (~24%)
* No duplicated data was found.
* Two columns were not in the correct data type: 'started at' and 'ended at'. These were changed to the correct datetime type.
* NaN values were checked in the dataframe for the columns end_lat and end_lng, these NaN values were replaced by the mean of each column.

Comparisons were made through statistics of features. The results are as follows:

### **4.1. Comparing between type of customers versus time length***
* On average, customers have a traveled time of:
    - Casual users = 21m 24.74s 
    - Annual members = 09m 46.51s
### **4.2. Comparing between type of bikes versus time length**
* On average, the traveled time length for each bike is:
    - Electric bikes = 09m 46.51s
    - Classic bikes = 14m 18.06s
    - Docked bikes = 02h 12m 22.62s
### **4.3. Comparing between type of customers versus time of the day***
* The most frequent time of the day where customers used Cyclistic:
    - Casual users = Afternoon 
    - Annual members = Morning
### **4.4. Comparing between type of bikes versus time of the day**
* The most frequent time of the day where the different types of bike were used:
    - Electric bikes = Morning
    - Classic bikes = Morning
    - Docked bikes = Afternoon
### **4.5. Comparing between type of customers versus day of the week***
Here, 0 is Monday and 6 is Sunday
* On average, the day of the week where each bike is more frequent to be used by customers is:
    - Casual users = 2.96   (Thursday)
    - Annual members = 2.97 (Thursday)
### **4.6. Comparing between type of bikes versus day of the week**
Here, 0 is Monday and 6 is Sunday
* On average, the day of the week where each bike is more frequent to be used by customers is:
    - Electric bikes = 2.75 (Thursday)
    - Classic bikes = 2.71  (Thursday)
    - Docked bikes = 3.17   (Thursday)
### **4.7. Comparing between type of customers versus day of the month***
* On average, the day of the month where each bike is more frequent to be used by customers is:
    - Casual users = 16.45   (By the middle of the month, 3rd week)
    - Annual members = 16.31 (By the middle of the month, 3rd week)
### **4.8. Comparing between type of bikes versus day of the month**
* On average, the day of the month where each bike is more frequent to be used by customers is:
    - Electric bikes = 16.55 (By the middle of the month, 3rd week)
    - Classic bikes = 16.04  (By the middle of the month, 3rd week)
    - Docked bikes = 16.73   (By the middle of the month, 3rd week)            
### **4.9. Comparing between type of customers versus distance traveled**
* On average, customer have a distance traveled of:
    - Casual users = 1.78km
    - Annual members = 1.85km
### **4.10. Comparing between type of bikes versus distance traveled**
* On average, the distance traveled length for each bike is:
    - Electric bikes = 1.92km
    - Classic bikes = 1.71km
    - Docked bikes = 2km

At this point, we can tell a difference already between the type of customers and the types of bikes which is the main element in Cyclistic's service. Besides that, we have now more idea about the customers' preferences and needs when it comes to use Cyclistic, being that, analyzing other features such as the day of the week, month, and time of the day. All of these discoveries will be relevant to stablish the differences that can help casual users improve their experience in Cyclistic by becoming annual members.

# **5. SHARE**
For this data, histograms and bar graphs were chosen as the type of plots that will represent the results, due to the fact that we have categorical features and is easier to make comparisons between features with this type of plot. 

## Key findings 🔍

![Image](images\users_freq_users.png)
* The amount of the data registered in the dataframe for annual members is greater than for the casual riders, which is 76% and 24% repectively.

![Image](images\daytime_freq_bothusers.png)
* Annual members take their trips either in the morning or afternoon more frequently. Casual riders tend to mantain the usage of Cyclistic's service in the morning, afternoon and evening.

![Image](bike_freq_bothusers.png)
* The electric bike is the most used out of the 3 possible types offered. Docked bike has only been used by casual riders.
* Annual members have a shorter traveled time compared to the casual members.


# **6. ACT**











# **Conclusions** 🖊
**✔**  
**✔**  
**3.**  When the statistics were described, the majority of the users either annual members and casual users tend to use the service for no longer than 1 day, except for a few cases. This may tell us as well that customers have a single-ride or full-day trips more often.
*The docked bike takes longer than the classic bike. Being the electric the...
*On average, casual users have a bigger traveled time length by two times (~21 mins), compared to annual members (~10 mins). This could be depending on the distance traveled and/or the type of bike they used.
*Related to the previous result, on average, casual and annual members use the service for less than a day.
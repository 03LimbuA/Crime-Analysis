# Crime-Analysis

This exploratory data analysis project, inspired by and following the tutorial of Youtube Channel [Mo Chen](https://www.youtube.com/@mo-chen), examines a tabular dataset containing records from the Boston Police Department's crime incident reports (2015-2018), including details such as, the type, time, and location of the incidents.
The official dataset is sourced from [Kaggle Crime data analysis](https://www.kaggle.com/code/sevgisarac/crime-data-analysis).

For this project, I used Google Colab, leveraging its Jupyter Notebook interface to write and execute Python code. This setup allowed me to analyse the data interactively and visualise the results from the analysis. The complete Google Colab notebook, displaying the coding and resulting data visualisations, can be accessed [here](https://github.com/03LimbuA/Crime-Analysis/blob/main/CrimeANALYSIS.ipynb).

## Setting up the environment
- Since we're using Python for this project, we import some essential libraries (numpy for numerical operations, pandas for data manipulation, matplotlib for creating visualisations, seaborn for statistical data visualisation, %matplotlib inline allows us to see the plots/results immediately below the code cells that produce them and not in a separate window).
- Next, we use a 'for loop' to find the correct encoding to use in order to read our CSV file that contains the dataset we are using for this project. By default, 'pandas' uses utf-8 encoding; in this case, utf-8 encoding doesn't work in reading our CSV file. The 'for loop' gives us back all the encodings that we can use to read our file - we'll pick one from the list (ISO-8859-11) and use that.
<img src="https://github.com/user-attachments/assets/9beff80a-4be4-48a8-bd16-5ff242237798" width="260" height="150"> 

- We use 'crime.head()' to quickly inspect the table we're working with (e.g., we can see the columns and the values in the columns)
- 'crime.shape' allows us to see the shape of the data we're working with - we find that our data has 319,073 rows and 17 columns
- 'crime.duplicated().sum()' shows us the no. of duplicated rows (23 rows) and we eliminate these duplicated rows by using 'crime.drop_duplicates(inplace=True)' - we now have 319,050 rows
- 'crime' shows us the beginning and end of the data frame (pandas, by default, gives us 10 rows of data)
- 'crime.info()' gives us back summary information on the dataframe (e.g., the column, non-NULL counts, column's data type)
<img width="300" alt="Screenshot 2025-01-20 at 17 47 16" src="https://github.com/user-attachments/assets/9ed6f455-be8d-452a-b240-9cae7c4a94e4" />

- For this analysis, we want to be able to easily extract date time information from the column, and we can only do so if it's a date time column. So, we use the 'to_datetime()' function to convert the OCCURED_ON_DATE column, and using the '.info()' shows us that it has worked
- Next, we extract the year, month, weekday, hour, minute - the below image shows an example of this (extracted year, image doesn't show all the rows outputted)
<img width="150" alt="Screenshot 2025-01-20 at 17 54 10" src="https://github.com/user-attachments/assets/f3d9233c-15c8-4a72-a9fb-d4ce57664e27" />

- Next, we use '.describe()' to get back information on the numeric columns
<img src="https://github.com/user-attachments/assets/f238e420-333d-40f6-bdcd-8e26927a6b49" width="500" height="150">

- And, we use 'crime.describe(include='object')' to get back information on the NON-numerical columns
<img width="629" alt="Screenshot 2025-01-20 at 17 56 51" src="https://github.com/user-attachments/assets/5d988aa5-75b6-4e84-a519-b53bb0a0bb7c" />

- Looking at the non-numerical columns, we can see that the count of incident_numbers is 319,050, but for unique incident_numbers we get a lower count of 282,517, which suggests that we have duplicate entries for incident_number - this is likely due to there being multiple types of crimes committed within a single incident. Additionally, looking at the DISTRICT column, we see that we have 12 unique dristicts, and the top district (most occuring) is B2.

- '.columns' returns the columns in our data frame
- we check for columns with missing values ('DISTRICT', 'SHOOTING', 'UCR_PART', 'STREET', 'Lat', 'Long')
- we use a 'for loop' to check for the no. of unique values in each column
<img width="270" alt="Screenshot 2025-01-20 at 18 13 56" src="https://github.com/user-attachments/assets/67f8594b-0116-4f8c-9996-6111d4ea4ebb" />

## The Analysis
- We find that the most common crime in terms of offense groups are Motor Vehical Accident Responses, and the least common crime is Burglary (no property taken)
<img width="300" alt="Screenshot 2025-01-20 at 19 29 27" src="https://github.com/user-attachments/assets/5d3aeae0-420c-4a03-98fc-010996164ec0" />

- Next, we look at the top 10 most common crimes in terms of offense groups as a percentage of all crimes, and we visualise the results as a bar chart
<img width="240" alt="Screenshot 2025-01-20 at 19 33 05" src="https://github.com/user-attachments/assets/71096ad2-e79e-4f57-b3c8-d024664c2a30" />

<img width="308" alt="Screenshot 2025-01-20 at 20 26 19" src="https://github.com/user-attachments/assets/3b481910-5b6f-4709-aeae-a411422260ff" />




- Next, we look at what the most common and least common offense descriptions are, through using the '.value_counts()' function
<img width="248" alt="Screenshot 2025-01-20 at 19 37 19" src="https://github.com/user-attachments/assets/fd30488c-bf84-43c8-b447-6a57d23cbcc2" />

-Once again, we look at the most common offense descriptions as a percentage of all crimes, and we visualise the results as a bar chart


<img width="308" alt="Screenshot 2025-01-20 at 19 38 43" src="https://github.com/user-attachments/assets/72b4c56c-49d3-4e7d-96c8-eeb477804926" />

- Next, we look at the number of crimes recorded for each year (remember, the datatset contains records from 2015-2018), we use the '.groupby()' and '.count()' functions - the results show us that the most crimes were committed in 2017
<img width="308" alt="Screenshot 2025-01-20 at 19 41 08" src="https://github.com/user-attachments/assets/a876c1e7-ec5e-4daf-8132-9a56b8f0335a" />


- Next, we'll investigate whether there are more crimes committed on specific weekdays. Again, we use the '.groupby()' and '.count()' functions. We can see that the weekday with the most crimes recorded is Friday; however, there seems to be no significant difference amongst the weekdays in terms of no. of crimes recorded (all within 40,0000-50,0000 range).
<img width="248" alt="Screenshot 2025-01-20 at 19 44 04" src="https://github.com/user-attachments/assets/d20b0e0d-e5dc-4927-ae97-4bde227e73e5" />
<img width="308" alt="Screenshot 2025-01-20 at 19 45 04" src="https://github.com/user-attachments/assets/930940b5-4b7e-4e8f-b9cf-3c684a12db5a" />


- Next, we'll investigate whether there are more crimes committed on specific times of the day. We can see that there's a significant decrease in the no. of crimes recorded during 1am - 5am, and that the highest no. of crimes are recorded late in the evening between 3pm - 6pm.
<img width="308" alt="Screenshot 2025-01-20 at 19 51 01" src="https://github.com/user-attachments/assets/e6af9666-17a0-4b30-8b82-8026a4fe481b" />


- Next, we'll investigate on what days and during which time of the day most crimes are committed - we visualise this through a heat map (we use the imported 'seaborn' library to do this). We can see that most crimes occur on Mon, Tues, Sat, Sun, between 4pm - 6pm.
<img width="310" alt="Screenshot 2025-01-20 at 19 56 59" src="https://github.com/user-attachments/assets/323d7094-6415-418e-8d81-daa7a17bed95" />


- Next, we'll examine which months recorded no. of crimes below average, and which months, on average, did the most crimes occur. First, we find the average no. of crimes per month (7976.25 crimes). Then, we create a table (grouping Month and Year) showing the months in each year (2015-2018) and the recorded no. of crimes for each of those months. Next, we highlight values less than the average no. of crimes per month (7976.25 crimes) **blue** , and value with **more** than the average are highlighted **green**
<img width="300" alt="Screenshot 2025-01-20 at 20 06 16" src="https://github.com/user-attachments/assets/032ba06f-0f91-4adc-b6fb-c2a95e713484" />

- Additionally, we investigate which districts recorded the most crimes on a yearly basis, using the '.groupby()' (grouping district and year) and '.count()' functions. We'll visualise the results through a heat map. We can see that district B2 recorded the highest no. of crimes between 2016-2017, along with districts C11 and D4.
<img width="310" alt="Screenshot 2025-01-20 at 20 09 19" src="https://github.com/user-attachments/assets/403cfc4a-d807-42f6-9396-388b39bcb4fd" />


## The code
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from encodings.aliases import aliases

%matplotlib inline

alias_values = set(aliases.values())

for encoding in set(aliases.values()):
    try:
        df=pd.read_csv("crime.csv", nrows=10, encoding=encoding)
        print('successful', encoding)
    except:
        pass

crime = pd.read_csv("/content/crime.csv", encoding="ISO-8859-11")

crime.head()

crime.shape

crime.duplicated().sum()

crime.drop_duplicates(inplace=True)

crime.shape

crime

crime.info()

crime.OCCURRED_ON_DATE.dt.year

crime.OCCURRED_ON_DATE.dt.month

crime.OCCURRED_ON_DATE.dt.weekday

crime.OCCURRED_ON_DATE.dt.hour

crime.OCCURRED_ON_DATE.dt.minute

crime.describe()

crime.describe(include='object')

crime.columns[np.sum(crime.isnull()) != 0]

print('Missing values in each column \n')
crime[crime.columns].isnull().sum()

crime.columns[np.sum(crime.isnull()) == 0]

for col in crime.columns:
    unique_count = crime[col].nunique()
    print(col + " has " + str(unique_count) + " unique values")

crime.OFFENSE_CODE_GROUP.value_counts()

offense_group_vals = crime.OFFENSE_CODE_GROUP.value_counts()[:10]

display(offense_group_vals / crime.shape[0])

(offense_group_vals / crime.shape[0]).plot(kind='bar', color='pink');
plt.title('Top 10 Offense Groups (as % of all crimes)');

crime.OFFENSE_CODE_GROUP.value_counts().sort_values(ascending=True)[:10]

crime.OFFENSE_DESCRIPTION.value_counts()

offense_description_vals = crime.OFFENSE_DESCRIPTION.value_counts()[:10]

display(offense_description_vals / crime.shape[0])

(offense_description_vals / crime.shape[0]).plot(kind='bar', color='pink');
plt.title('Top 10 Offense Descriptions (as % of all crimes)');

crime.groupby('YEAR').count()['INCIDENT_NUMBER'].plot(kind='bar', color='pink');
plt.title('Number of crimes');

display(crime.groupby('DAY_OF_WEEK').count()['INCIDENT_NUMBER'].sort_values(ascending=False));

crime.groupby('DAY_OF_WEEK').count()['INCIDENT_NUMBER'].sort_values(ascending=False).plot(kind='bar', color='pink');

crime.groupby('HOUR').count()['INCIDENT_NUMBER'].plot(kind='bar', color='pink');

week_and_hour = crime.groupby(['HOUR','DAY_OF_WEEK']).count()['INCIDENT_NUMBER'].unstack()

week_and_hour = week_and_hour[['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']]

sns.heatmap(week_and_hour, cmap=sns.cubehelix_palette(as_cmap=True));

avg_crime = crime.groupby(['YEAR', 'MONTH']).count()['INCIDENT_NUMBER'].mean()
print("The average number of crimes is " + str(avg_crime))

year_and_month = crime.groupby(['MONTH', 'YEAR']).count()['INCIDENT_NUMBER'].unstack()

def style_negative(v, props=''):
    return props if v < avg_crime else None
s2 = year_and_month.style.applymap(style_negative, props='color:blue;')\
              .applymap(lambda v: 'opacity: 20%;' if (v < 0.3) and (v > -0.3) else None)
s2

def highlight_max(s, props=''):
    return np.where(s == np.nanmax(s.values), props, '')
s2.apply(highlight_max, props='color:white;background-color:darkgreen', axis=0)

district_and_year = crime.groupby(['DISTRICT', 'YEAR']).count()['INCIDENT_NUMBER'].unstack()

sns.heatmap(district_and_year, cmap=sns.cubehelix_palette(as_cmap=True));

avg_crime_district = crime.groupby(['DISTRICT', 'YEAR']).count()['INCIDENT_NUMBER'].mean()
print("The average crime per district per year is: " + str(avg_crime_district))

def style_negative(v, props=''):
    return props if v < avg_crime_district else None
s3 = district_and_year.style.applymap(style_negative, props='color:blue;')\
              .applymap(lambda v: 'opacity: 20%;' if (v < 0.3) and (v > -0.3) else None)
s3

def highlight_max(s, props=''):
    return np.where(s == np.nanmax(s.values), props, '')
s3.apply(highlight_max, props='color:white;background-color:darkgreen', axis=0)
```

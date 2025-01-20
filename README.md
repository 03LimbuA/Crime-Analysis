# Crime-Analysis

This explaratory data analysis project, inspired by and following the tutorial of Youtube Channel [Mo Chen](https://www.youtube.com/@mo-chen) examines a tabular dataset containing records from the Boston Police Department's crime incident reports (2015-2018), including details such as, the type, time, and location of the incidents.
The official dataset is sourced from [Kaggle Crime data analysis](https://www.kaggle.com/code/sevgisarac/crime-data-analysis).

For this project, I used Google Colab, leveraging its Jupyter Notebook interface to write and execute Python code. This setup allowed me to analyse the data interactively and visualise the results from the analysis. The complete Google Colab notebook, displaying the coding and resulting data visualisations, can be accessed [here](https://github.com/03LimbuA/Crime-Analysis/blob/main/CrimeANALYSIS.ipynb).

## The Process
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
Looking at the non-numerical columns, we can see that the count of incident_numbers is 319,050, but for unique incident_numbers we get a lower count of 282,517, which suggests that we have duplicate entries for incident_numbber - this is likely due to there being multiple types of crimes committed within a single incident. Additionally, looking at the DISTRICT column, we see that we have 12 unique dristicts, and the top district (most occuring) is B2.

- '.columns' returns the columns in our data frame
- we check for columns with missing values ('DISTRICT', 'SHOOTING', 'UCR_PART', 'STREET', 'Lat', 'Long')
- we use a 'for loop' to check for the no. of unique values in each column
<img width="270" alt="Screenshot 2025-01-20 at 18 13 56" src="https://github.com/user-attachments/assets/67f8594b-0116-4f8c-9996-6111d4ea4ebb" />

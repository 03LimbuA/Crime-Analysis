# Crime-Analysis

This explaratory data analysis project, inspired by and following the tutorial of Youtube Channel [Mo Chen](https://www.youtube.com/@mo-chen) examines a tabular dataset containing records from the Boston Police Department's crime incident reports (2015-2018), including details such as, the type, time, and location of the incidents.
The official dataset is sourced from [Kaggle Crime data analysis](https://www.kaggle.com/code/sevgisarac/crime-data-analysis).

For this project, I used Google Colab, leveraging its Jupyter Notebook interface to write and execute Python code. This setup allowed me to analyse the data interactively and visualise the results from the analysis. The complete Google Colab notebook, displaying the coding and resulting data visualisations, can be accessed [here](https://github.com/03LimbuA/Crime-Analysis/blob/main/CrimeANALYSIS.ipynb).

## The Process
- Since we're using Python for this project, we import some essential libraries (numpy for numerical operations, pandas for data manipulation, matplotlib for creating visualisations, seaborn for statistical data visualisation, %matplotlib inline allows us to see the plots/results immediately below the code cells that produce them and not in a separate window).
- Next, we use a 'for loop' to find the correct encoding to use in order to read our CSV file that contains the dataset we are using for this project. By default, 'pandas' uses utf-8 encoding; in this case, utf-8 encoding doesn't work in reading our CSV file 

# Data-Science-Assesment-R-
This Repository includes the main assessment of masters level , that is need to be done in R 
Introduction to Data Science 11372 & 11516
Final Assessment - Take Home Exam
Instructions for students
Part A - Data Science Questions (12 marks)
Part B –Data Preparation, exploring and modelling (78 marks)
Data Description:
Data Copyright:
Task 1: Data Preparation and Wrangling: (21 marks)
Task 2: Exploratory Data Analysis: (35 marks)
Task 3: Data-Driven Modelling: (14 marks)
Task 4 - Insights (8 marks)
Deliverables
Assignment Due: 15 May 2022

This version of the assignment instructions is for Post Graduates

Instructions for students
This is a take-home assignment.
The assignment is organised into two parts, where the first part is composed of general questions to assess your understanding of the Data Science principles and the other part is code-based questions, which you will need to write R-code snippets for.
Both parts must be attempted and reported in your submission. You will provide a .rmd file that includes aspects of your formal reporting (e.g., an introduction, assumptions) using the markdown syntax, mixed with your R Code and results. All questions must be included in this report.
Both the .rmd and knitted ,html files should be submitted as a one compressed file (e.g. *.ZIP) on the Canvas website of the unit by the due date of the assignment.
The submitted file should be renamed as [studentID_lastname_final_assessment.zip], where “studentID” is your university ID and “lastname” is your lastname.
The assignment will be open from Tuesday, the 26th of April (23:59) until Sunday, the 15th of May (23:59).
This assignment has 100 marks in total and weighs 40% of the final grade of the unit, where 50% of the assignment marks is compulsory to pass the unit.
The assignment will cover the learning outcomes and taught contents of the unit.
Note: Marking (10 Marks) is included for overall presentation of the of the submission, including coding style (for examples see Google’s R Style Guide )

Part A - Data Science Questions (12 marks)
There are four questions in this part, with differing marks. All answers must be recorded in an Rmarkdown file then exported to PDF/HTML file.

(3 marks) From your understanding of ethical data science, mention three principles of a code of ethics that any data scientist should consider.

Write your answer as:
P1:___________________________________________________________________
P2:___________________________________________________________________
P3:___________________________________________________________________
(3 marks) To build a visualisation using the ggplot2 library, we use the following template:

ggplot(data= [dataset], mapping = aes(x = [x-variable], y = [y-variable]))+
  geom_xxx() +
  other options 
Based on the above template, mention the main components of building a graph using ggplot2 and describe the meaning of each of these components.

Write your answer as:
______________________________________________________________________
______________________________________________________________________
______________________________________________________________________
______________________________________________________________________
______________________________________________________________________
(3 marks) Describe three properties of the correlation coefficient of two variables

Write your answer as:
1.  ___________________________________________________________________
2.  ___________________________________________________________________
3.  ___________________________________________________________________
(3 marks) Imagine we have a dataset that lists the heights of the fathers and their sons. You have built a linear model that encodes the relationship between the fathers’ heights and the sons’ heights as follows:

lm(son ~ father, data = heights_data)

Call:
lm(formula = son ~ father, data = heights_data)

Coefficients:
(Intercept)    father  
70.45       0.50  
The estimated coefficient (i.e. intercept and slope), which describes the relationship between the fathers’ and sons’ heights can be interpreted as:

Write your answer as:
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
Part B –Data Preparation, exploring and modelling (78 marks)
In this part, you are given four data files in the CSV format. These files are collected from the internet for the COVID-19 pandemic for different regions and countries around the world for the period between 1/1/2020 and 5/5/2020. The data are described below. However, please note that the data is quite messy. You are asked to write R code to import and wrangle these data files and put them in reasonable format to conduct analysis and do data-driven modelling on them. This part is consisted of four tasks, that are listed below in details. You are asked to write R-code for all of questions in each task.

Data Description:
The four CSV files are described in the following table:



Data Copyright:
The data has been scrapped from different places on the internet with a focus on:

https://github.com/owid/covid-19-data/tree/master/public/data/
https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases
https://www.worldometers.info/coronavirus/
https://en.wikipedia.org/wiki/Gross_domestic_product
Task 1: Data Preparation and Wrangling: (21 marks)
Load and read the data from the CSV files and store them into dataframes named appropriately.

Tidy up the dataframe driven from the file “Recovered.csv” to be compatible with the dataframe driven from the file “Covid19.csv”, i.e., every observation should have a record of recovered patients in one country in a single day.

Change the column names in the dataframes were loaded from the following files accordingly.



Ensure that all dates variables are of date data type and with the same format across the dataframes.

Considering the master dataframe is the one loaded from file “Covid19.csv”, add new 5 variables to it from the other files (Recovered.csv, Tests.csv, Countries.csv). The 5 new added variables should be named (“Recovered”, “NewTests”, “Population”, “GDP”, “GDPCapita”) accordingly.

[Hint: you may use the merge function to facilitate the alignment of the data of the different dataframes. You may use this format: merge(x=df1,y=df2,all.x=TRUE), where df1 and df2 are the dataframes to be merged]

Check for NAs in all dataframes and change them to Zero.

Using existing “Date” variable; add month and week variables to the master dataframe. [Hint: you may use functions from lubridate package]

[Hint: To ensure that this task has been finished correctly, when you run head(covid19_data), you should get results such as in the below image]

 ***

Task 2: Exploratory Data Analysis: (35 marks)
Add four new variables to the master dataframe (“CumCases”, “CumDeaths”, “CumRecovered”, “CumTests”). These variables should reflect the cumulative relevant data up to the date of the observation; i.e., CumCases for country “X” at Date “Y” should reflect the total number of cases in country “X” since the beginning of recording data till the date “Y”.

[Hint: first arrange by date and country, then for each new variable to be added you need to group by country and mutate the new column using the cumsum function]

Add two new variables to the master dataframe (“Active”, “FatalityRate”). Active variable should reflect the infected cases that has not been closed yet (by either recovery or death), and it could be calculated from (CumCases – (CumDeaths + CumRecovered)). On the other hand, FatalityRate variable should reflect the percentages of death to the infected cases up to date and it could be calculated from (CumDeaths / CumCases).

Add four new variables to the master dataframe (“Cases_1M_Pop”, “Deaths_1M_Pop”, “Recovered_1M_Pop”, “Tests_1M_Pop”) These variables should reflect the cumulative relevant rate per one million of the corresponding country population, (i.e Cases_1M_Pop for country “X” at Date “Y” should reflect the total number of new cases up to date “Y” per million people of country “X” population)

[Hint: Cases_1M_Pop = CumCases*(10^6) / Population)]

Find the day with the highest reported death toll across the world. Print the date and the death toll of that day.

Build a graph to show how the cumulative data of (Infected Cases, Deaths, Recovered, Tests) change over the time for the whole world collectively.

[Hint: Use geom_line as a geometry function, use log for the Y axis for better presentation, Use different colour to distinguish between new cases, deaths, and recovered]

Extract the data corresonding to the last day (05/05/2020) and save it in a separate dataframe and name it “lastDay_data”.

[Hint: use filter function with Date = “2020-05-05”]

Based on the data of the last day, extract the records of the top 10 countries worldwide that have current active cases, total confirmed cases, and fatality rate in separate dataframes (i.e., top10activeW, top10casesW, top10fatalityW, top10testsMW).

[Hint: you can use head(arranged_data, n=10) to get the top 10 records]

Based on the data of the last day, print the up to date confirmed, death, recovered cases as well as the tests for every continent.

Build a graph to show the total number of cases over the time for the top 10 countries that have been obtained in question 7 (Use log for Y axis for better presentation).

[Hint: first you need to get the data of the top-10 countries and then plot their lines]

Build a graph for the top 10 countries with current highest active cases which was obtained previously in question 7. The graph should have one subgraph (i.e., using facet function) for each of these countries, every subgraph should show how the new cases, new deaths, and new recovered cases were changing over the time (Use log for Y axis for better presentation, Use different colour to distinguish between new cases, deaths, and recovered).

[hint: geom_line function with date on x_axis and each of the values of the variables in y_axis]

Build a graph for the top 10 countries with current highest total tests per one million of the population which was obtained previously in question 7. This graph should present total number of infected cases, total tests so far, and the total tests per million of the population for each country.

[hint: you can use bar chart to achieve this task]

Build a graph to present the statistics of all continents which was obtained previously in question 8 (Use log for Y axis for better presentation, Use Continent in the legend, make sure x-axis labels does not overlap).

Task 3: Data-Driven Modelling: (14 marks)
Based on the data of the last day, that you have extracted in the previous task, create a separate dataframe named “cor_data” with the data of these variables (CumCases, CumTests, Population, GDP, GDPCapita).

[Hint: you can use select function on the lastday_data dataframe]

Compute the correlation matrix between the variables of the “cor_data” and visualise this correlation matrix.

visualise the distribution of the cumulative cases in the cor_data with and without changing the scale of the x axis to log transformation.

[Hint: you can use the geom_histrogram function]

Divide the cor_data into training and testing, where training data represent 65% of the number of rows.

Train a linear regression model to predict cumulative cases from the GDP of the countries. Then, evaluate this model on the test data and print the root mean square error value.

Train another linear regression model to predict cumulative cases from all the other variables. Then, evaluate this model on the test data and print the root mean square error value.

Interpret the two models and write a small report of highlighting the differences between using the two models. For example, in which cases we should use the first model and in which cases the second one is better to use.

Task 4 - Insights (8 marks)
Imagine you have been asked to plan for a dashboard that shall show the trends and the main figures of the different Covid19 waves that happened world wide, so far. Given the current data in this assignment is only covering the first wave of the Covid19, how would you augment this data? What are the other sources of data that you will rely on? What types of figures will you be focusing on to show in your dashboard? and why?

Write the report as follows:

1. Objectives:
-----------------------------------------
-----------------------------------------
-----------------------------------------

2. List of data sources to augment the existing data:
-----------------------------------------
-----------------------------------------
-----------------------------------------

3. Set of figures/tables to show in the dashboard:
-----------------------------------------
-----------------------------------------
-----------------------------------------

4. Analysis strategy:
-----------------------------------------
-----------------------------------------
-----------------------------------------
Deliverables
You are required to submit a compressed (e.g. ZIP) file to Canvas with the following files:

Single .rmd file with the markdown report & code for Tasks in all parts

A HTML or PDF document generated by knitting your .rmd file,

Please follow the following structure to name the submitted zip file:

[studentID_lastname_final_assignment.zip]

Replace the studentID with your university ID and lastname with your name.Introduction to Data Science 11372 & 11516
Final Assessment - Take Home Exam
Instructions for students
Part A - Data Science Questions (12 marks)
Part B –Data Preparation, exploring and modelling (78 marks)
Data Description:
Data Copyright:
Task 1: Data Preparation and Wrangling: (21 marks)
Task 2: Exploratory Data Analysis: (35 marks)
Task 3: Data-Driven Modelling: (14 marks)
Task 4 - Insights (8 marks)
Deliverables
Assignment Due: 15 May 2022

This version of the assignment instructions is for Post Graduates

Instructions for students
This is a take-home assignment.
The assignment is organised into two parts, where the first part is composed of general questions to assess your understanding of the Data Science principles and the other part is code-based questions, which you will need to write R-code snippets for.
Both parts must be attempted and reported in your submission. You will provide a .rmd file that includes aspects of your formal reporting (e.g., an introduction, assumptions) using the markdown syntax, mixed with your R Code and results. All questions must be included in this report.
Both the .rmd and knitted ,html files should be submitted as a one compressed file (e.g. *.ZIP) on the Canvas website of the unit by the due date of the assignment.
The submitted file should be renamed as [studentID_lastname_final_assessment.zip], where “studentID” is your university ID and “lastname” is your lastname.
The assignment will be open from Tuesday, the 26th of April (23:59) until Sunday, the 15th of May (23:59).
This assignment has 100 marks in total and weighs 40% of the final grade of the unit, where 50% of the assignment marks is compulsory to pass the unit.
The assignment will cover the learning outcomes and taught contents of the unit.
Note: Marking (10 Marks) is included for overall presentation of the of the submission, including coding style (for examples see Google’s R Style Guide )

Part A - Data Science Questions (12 marks)
There are four questions in this part, with differing marks. All answers must be recorded in an Rmarkdown file then exported to PDF/HTML file.

(3 marks) From your understanding of ethical data science, mention three principles of a code of ethics that any data scientist should consider.

Write your answer as:
P1:___________________________________________________________________
P2:___________________________________________________________________
P3:___________________________________________________________________
(3 marks) To build a visualisation using the ggplot2 library, we use the following template:

ggplot(data= [dataset], mapping = aes(x = [x-variable], y = [y-variable]))+
  geom_xxx() +
  other options 
Based on the above template, mention the main components of building a graph using ggplot2 and describe the meaning of each of these components.

Write your answer as:
______________________________________________________________________
______________________________________________________________________
______________________________________________________________________
______________________________________________________________________
______________________________________________________________________
(3 marks) Describe three properties of the correlation coefficient of two variables

Write your answer as:
1.  ___________________________________________________________________
2.  ___________________________________________________________________
3.  ___________________________________________________________________
(3 marks) Imagine we have a dataset that lists the heights of the fathers and their sons. You have built a linear model that encodes the relationship between the fathers’ heights and the sons’ heights as follows:

lm(son ~ father, data = heights_data)

Call:
lm(formula = son ~ father, data = heights_data)

Coefficients:
(Intercept)    father  
70.45       0.50  
The estimated coefficient (i.e. intercept and slope), which describes the relationship between the fathers’ and sons’ heights can be interpreted as:

Write your answer as:
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
_____________________________________________________________________
Part B –Data Preparation, exploring and modelling (78 marks)
In this part, you are given four data files in the CSV format. These files are collected from the internet for the COVID-19 pandemic for different regions and countries around the world for the period between 1/1/2020 and 5/5/2020. The data are described below. However, please note that the data is quite messy. You are asked to write R code to import and wrangle these data files and put them in reasonable format to conduct analysis and do data-driven modelling on them. This part is consisted of four tasks, that are listed below in details. You are asked to write R-code for all of questions in each task.

Data Description:
The four CSV files are described in the following table:



Data Copyright:
The data has been scrapped from different places on the internet with a focus on:

https://github.com/owid/covid-19-data/tree/master/public/data/
https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases
https://www.worldometers.info/coronavirus/
https://en.wikipedia.org/wiki/Gross_domestic_product
Task 1: Data Preparation and Wrangling: (21 marks)
Load and read the data from the CSV files and store them into dataframes named appropriately.

Tidy up the dataframe driven from the file “Recovered.csv” to be compatible with the dataframe driven from the file “Covid19.csv”, i.e., every observation should have a record of recovered patients in one country in a single day.

Change the column names in the dataframes were loaded from the following files accordingly.



Ensure that all dates variables are of date data type and with the same format across the dataframes.

Considering the master dataframe is the one loaded from file “Covid19.csv”, add new 5 variables to it from the other files (Recovered.csv, Tests.csv, Countries.csv). The 5 new added variables should be named (“Recovered”, “NewTests”, “Population”, “GDP”, “GDPCapita”) accordingly.

[Hint: you may use the merge function to facilitate the alignment of the data of the different dataframes. You may use this format: merge(x=df1,y=df2,all.x=TRUE), where df1 and df2 are the dataframes to be merged]

Check for NAs in all dataframes and change them to Zero.

Using existing “Date” variable; add month and week variables to the master dataframe. [Hint: you may use functions from lubridate package]

[Hint: To ensure that this task has been finished correctly, when you run head(covid19_data), you should get results such as in the below image]

 ***

Task 2: Exploratory Data Analysis: (35 marks)
Add four new variables to the master dataframe (“CumCases”, “CumDeaths”, “CumRecovered”, “CumTests”). These variables should reflect the cumulative relevant data up to the date of the observation; i.e., CumCases for country “X” at Date “Y” should reflect the total number of cases in country “X” since the beginning of recording data till the date “Y”.

[Hint: first arrange by date and country, then for each new variable to be added you need to group by country and mutate the new column using the cumsum function]

Add two new variables to the master dataframe (“Active”, “FatalityRate”). Active variable should reflect the infected cases that has not been closed yet (by either recovery or death), and it could be calculated from (CumCases – (CumDeaths + CumRecovered)). On the other hand, FatalityRate variable should reflect the percentages of death to the infected cases up to date and it could be calculated from (CumDeaths / CumCases).

Add four new variables to the master dataframe (“Cases_1M_Pop”, “Deaths_1M_Pop”, “Recovered_1M_Pop”, “Tests_1M_Pop”) These variables should reflect the cumulative relevant rate per one million of the corresponding country population, (i.e Cases_1M_Pop for country “X” at Date “Y” should reflect the total number of new cases up to date “Y” per million people of country “X” population)

[Hint: Cases_1M_Pop = CumCases*(10^6) / Population)]

Find the day with the highest reported death toll across the world. Print the date and the death toll of that day.

Build a graph to show how the cumulative data of (Infected Cases, Deaths, Recovered, Tests) change over the time for the whole world collectively.

[Hint: Use geom_line as a geometry function, use log for the Y axis for better presentation, Use different colour to distinguish between new cases, deaths, and recovered]

Extract the data corresonding to the last day (05/05/2020) and save it in a separate dataframe and name it “lastDay_data”.

[Hint: use filter function with Date = “2020-05-05”]

Based on the data of the last day, extract the records of the top 10 countries worldwide that have current active cases, total confirmed cases, and fatality rate in separate dataframes (i.e., top10activeW, top10casesW, top10fatalityW, top10testsMW).

[Hint: you can use head(arranged_data, n=10) to get the top 10 records]

Based on the data of the last day, print the up to date confirmed, death, recovered cases as well as the tests for every continent.

Build a graph to show the total number of cases over the time for the top 10 countries that have been obtained in question 7 (Use log for Y axis for better presentation).

[Hint: first you need to get the data of the top-10 countries and then plot their lines]

Build a graph for the top 10 countries with current highest active cases which was obtained previously in question 7. The graph should have one subgraph (i.e., using facet function) for each of these countries, every subgraph should show how the new cases, new deaths, and new recovered cases were changing over the time (Use log for Y axis for better presentation, Use different colour to distinguish between new cases, deaths, and recovered).

[hint: geom_line function with date on x_axis and each of the values of the variables in y_axis]

Build a graph for the top 10 countries with current highest total tests per one million of the population which was obtained previously in question 7. This graph should present total number of infected cases, total tests so far, and the total tests per million of the population for each country.

[hint: you can use bar chart to achieve this task]

Build a graph to present the statistics of all continents which was obtained previously in question 8 (Use log for Y axis for better presentation, Use Continent in the legend, make sure x-axis labels does not overlap).

Task 3: Data-Driven Modelling: (14 marks)
Based on the data of the last day, that you have extracted in the previous task, create a separate dataframe named “cor_data” with the data of these variables (CumCases, CumTests, Population, GDP, GDPCapita).

[Hint: you can use select function on the lastday_data dataframe]

Compute the correlation matrix between the variables of the “cor_data” and visualise this correlation matrix.

visualise the distribution of the cumulative cases in the cor_data with and without changing the scale of the x axis to log transformation.

[Hint: you can use the geom_histrogram function]

Divide the cor_data into training and testing, where training data represent 65% of the number of rows.

Train a linear regression model to predict cumulative cases from the GDP of the countries. Then, evaluate this model on the test data and print the root mean square error value.

Train another linear regression model to predict cumulative cases from all the other variables. Then, evaluate this model on the test data and print the root mean square error value.

Interpret the two models and write a small report of highlighting the differences between using the two models. For example, in which cases we should use the first model and in which cases the second one is better to use.

Task 4 - Insights (8 marks)
Imagine you have been asked to plan for a dashboard that shall show the trends and the main figures of the different Covid19 waves that happened world wide, so far. Given the current data in this assignment is only covering the first wave of the Covid19, how would you augment this data? What are the other sources of data that you will rely on? What types of figures will you be focusing on to show in your dashboard? and why?

Write the report as follows:

1. Objectives:
-----------------------------------------
-----------------------------------------
-----------------------------------------

2. List of data sources to augment the existing data:
-----------------------------------------
-----------------------------------------
-----------------------------------------

3. Set of figures/tables to show in the dashboard:
-----------------------------------------
-----------------------------------------
-----------------------------------------

4. Analysis strategy:
-----------------------------------------
-----------------------------------------
-----------------------------------------
Deliverables
You are required to submit a compressed (e.g. ZIP) file to Canvas with the following files:

Single .rmd file with the markdown report & code for Tasks in all parts

A HTML or PDF document generated by knitting your .rmd file,

Please follow the following structure to name the submitted zip file:

[studentID_lastname_final_assignment.zip]

Replace the studentID with your university ID and lastname with your name.

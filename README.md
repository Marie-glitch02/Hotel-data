# Title: Cleaning data in R

## Background for this activity
In this activity, I had a scenario, and focus on cleaning real data in R, will learn more about data cleaning functions and perform basic calculations to gain initial insights into your data.

## The scenario

In this scenario, I am a junior data analyst working for a hotel booking company. I have been asked to clean a .csv file that was created after querying a database to combine two different tables from different hotels. In order to learn more about this data, I am going to need to use functions to preview the data's structure, including its columns and rows.

## Step 1: Load packages

In order to start cleaning your data, you will need to  by install the required packages. If you have already installed and loaded `tidyverse`, `skimr`, and `janitor` in this session, feel free to skip the code chunks in this step.

```{r}
install.packages("tidyverse")
install.packages("skimr")
install.packages("janitor")
```

Once a package is installed, you can load it by running the `library()` function with the package name inside the parentheses:

```{r}
library(tidyverse)
library(skimr)
library(janitor)
```

## Step 2: Import data

The data you have been asked to clean is currently an external .csv file. In order to view and clean it in `R`, you will need to import it. The `tidyverse` library `readr` package has a number of functions for "reading in" or importing data, including .csv files. 

In the chunk below, you will use the `read_csv()` function to import data from a .csv file in the project folder called "hotel_bookings.csv" and save it as a data frame called `bookings_df`:

If this line causes an error, copy in the line setwd("projects/Course 7/Week 3") before it. 

```{r}
bookings_df <- read_csv("hotel_bookings.csv")
```

## Step 3: Getting to know your data

Before you start cleaning your data, take some time to explore it. You can use several functions that you are already familiar with to preview your data, including the `head()` function in the code chunk below:

```{r}
head(bookings_df)
```

You can also summarize or preview the data with the `str()` and `glimpse()` functions to get a better understanding of the data by running the code chunks below:

```{r}
str(bookings_df)
```

```{r}
glimpse(bookings_df)
```

You can also use `colnames()` to check the names of the columns in your data set. Run the code chunk below to find out the column names in this data set:

```{r}
colnames(bookings_df)
```

Some packages contain more advanced functions for summarizing and exploring your data. One example is the `skimr` package, which has a number of functions for this purpose. For example, the `skim_without_charts()` function provides a detailed summary of the data. Try running the code below:

```{r}
skim_without_charts(bookings_df)
```

## Step 4: Cleaning your data

Based on the functions you have used so far, how would you describe your data in a brief to your stakeholder? Now, let's say you are primarily interested in the following variables: 'hotel', 'is_canceled', and 'lead_time'. Create a new data frame with just those columns, calling it `trimmed_df` by adding the variable names to this code chunk:

```{r}
trimmed_df <- bookings_df %>% 
  select( , , )
```

Remember to check the solutions doc if you are having trouble filling out any of these code chunks. 

You might notice that some of the column names aren't very intuitive, so you will want to rename them to make them easier to understand. You might want to create the same exact data frame as above, but rename the variable 'hotel' to be named 'hotel_type' to be crystal clear on what the data is about

Fill in the space to the left of the '=' symbol with the new variable name:

```{r}
trimmed_df %>% 
  select(hotel, is_canceled, lead_time) %>% 
  rename( = hotel)
```

Another common task is to either split or combine data in different columns. In this example, you can combine the arrival month and year into one column using the unite() function:

```{r}
example_df <- bookings_df %>%
  select(arrival_date_year, arrival_date_month) %>% 
  unite(arrival_month_year, c("arrival_date_month", "arrival_date_year"), sep = " ")
```

## Step 5: Another way of doing things

You can also use the`mutate()` function to make changes to your columns. Let's say you wanted to create a new column that summed up all the adults, children, and babies on a reservation for the total number of people. Modify the code chunk below to create that new column:  

```{r}
example_df <- bookings_df %>%
  mutate(guests = )

head(example_df)
```

Great. Now it's time to calculate some summary statistics! Calculate the total number of canceled bookings and the average lead time for booking - you'll want to start your code after the %>% symbol. Make a column called 'number_canceled' to represent the total number of canceled bookings. Then, make a column called 'average_lead_time' to represent the average lead time. Use the `summarize()` function to do this in the code chunk below:

```{r}

example_df <- bookings_df %>%


head(example_df)
```
## Activity Wrap Up
I now have experience cleaning and analyzing data in R. I've used basic cleaning functions like rename() and clean_names(), and performed basic calculations on real data. I plan to continue practicing these skills by modifying code chunks in the Rmd file or using this code as a starting point for my own projects. One of the reasons R is so powerful for data analysis is its ability to perform various tasks, like importing data, creating and viewing data frames, and cleaning data, all in one place.

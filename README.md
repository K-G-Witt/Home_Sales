# Home_Sales
The Home_Sales project aims to calucate average prices for of homes by build and sales year using parquet and partitioning techniques to speed up processing time.


## Installation and Run Instructions:
For this project, **Google Colaboratory** was used. Therefore, you may need to create and sign in to **Google Drive** and **Google Colaboratory** before commencing:

### Google Drive:
1. In your browser, navigate to **drive.google.com**.
2. If you have not previously signed up for Google Drive, create an account. Otherwise, sign in using your Google credentials.

### Google Colaboratory:
1. Once signed in to **Google Drive**, click on **+ New**, **More**, **+ Connect more apps**. 
2. In the **Google Workspace Marketplace** search bar, type **Colaboratory**.
3. Click on **Colaboratory** to install **Google Colaboratory**.
4. Follow the installation instructions.
5. From now on, when you sign in to **Google Drive** and click on **+ New** and then **More**, you will see an option to launch **Google Colabortory**.


## Usage Instructions:
This repo contains the following:
1. **Home_Sales.ipynb:** a python script, executed in JupyterLab, to reproduce the analyses below (not used).
2. **Home_Sales_colab.ipynb:** a python script, executed in **Google Colab**, to reproduce the analyses below (used).


## Overview of the Analysis:
The overall purposes of this analysis is to use **SparkSQL** to determine key metrics about home sales data sourced from the following AWS S3 bucket:
https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.2/22-big-data/home_sales_revised.csv

**PySpark** was also used to create temporary table views, partition the data using parquet, cache and uncache a temporary table, and verify that the table has been uncached. These steps were undertaken to explore the effect these steps had on reducing processing time.


## Results:
1. The average price for a four-bedroom house sold for each year, rounded to two decimal places:

![screenshot_1](https://github.com/user-attachments/assets/3cd5a4bd-6391-496c-b939-c3b89d9d1204)


2. The average price of a home with three beedrooms and three bathrooms for each year the home was built, rounded to two decimal places:

![screenshot_2](https://github.com/user-attachments/assets/79b51609-582b-4897-83a9-c7bb325585bf)


3. The average price of a home with three bedrooms, three bathrooms, two floors, and greater than or equal to 2,000 square feet for each year the home was built, rounded to two decimal places:

![screenshot_3](https://github.com/user-attachments/assets/d81fd329-934d-4846-92aa-f57b507d8ac6)


4. The average price of a home per "view" rating for homes with an average home price greater than or equal to $350,000, rounded to two decimal places:

![screenshot_4](https://github.com/user-attachments/assets/63152cf4-c7e9-4884-8402-92cc374f45ac)


### Compairing runtimes:
* **Original:** 2.04 seconds.
* **Cached:** 0.81 seconds.
* **Parquet and Partitioned:** 1.09 seconds.


## Summary:
As the **home_sales_revised.csv** is not particularly large (2.6MB), consisting of 33,287 home sales (i.e., rows) and 11 features( e.g., columns), run times between the various approaches used in this project were not noticable. However, caching the table in memory did result in a significant improvement in run time, as would be expected.


## Credits:
This code was compiled and written by me for the home_sales project in the 2024 Data Analytics Boot Camp hosted by Monash University.

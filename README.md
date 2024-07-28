# Home_Sales
The Home_Sales project aims to calucate average prices for of homes by build and sales year using parquet and partitioning techniques to speed up processing time.


## Installation and Run Instructions:
You may need to create an sign into **Google Drive** and **Google Colaboratory** before commencing:

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


What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms? Round off your answer to two decimal places.

What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.

What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.


### Compiling, Training, and Evaluating the Model"
* Number of neurons, layers, and activation functions used: detailed in the **Overall Model Performance** section separately for the initial model and the optimised model.
* Ability to achieve the target model performance: as detained in the **Overal Model Performance** section, despite optimisation using **keras-tuner** the performance of the optimal model remained 73%, lower than the target model performance of 75%.
* Steps taken to increase model performance: as detailed in the **Overal Model Performance** section, after optimisation the number of hidden layers was increased from 2 to 6, the number of neurons per layer was reduced from between 30-80 to between 5-9, and the activation functions were reduced in complexity from relu to sigmoid.


### Overall Model Performance:
#### Initial Model:
The hyperparameters of the initial model are as follows:
* Number of input features: len(X_train[0]);
* Input layer: neurons = 80, activation function = relu;
* Second hidden layer: neurons = 30, activation function = relu;
* Output layer: neurons = 1, activation function = sigmoid.

Overall, using these hyperparameters, the accuracy of the initial model is 0.73, indicating that it correctly classifies 73% of the instances.


#### Optimised Model:
The hyperparameters of the optimised model are as follows:
* Number of input features: len(X_train[0]);
* Input layer: neurons = 7, activation function = sigmoid;
* Second hidden layer: neurons = 9, activation function = sigmoid;
* Third hidden layer: neurons = 5, activation function = sigmoid;
* Fourth hidden layer: neurons = 7, activation function = sigmoid;
* Fifth hidden layer: neurons 9, activation function = sigmoid;
* Sixth hidden layer: neurons = 9, activation function = sigmoid;
* Output layer: neurons = 1, activation function = sigmoid.

Overall, the accuracy of the optimised model is also 0.73, indicating that, despite tuning, the model still only correctly classifies 73% of the instances.


## Summary:
The optimised neural network model performs acceptably well in predicting successful grant applicants, with an the overall accuracy of 73%. However, despite auto-optimisation, the model performance remained at 73%, slightly lower than the target performance of 75%. Given this, it may be approriate to attempt classification using a more complex model, such as Random Forest. This method not only will help improve classificaiton accuracy, it may also help in the identification of which variables are explain the most or least in determining whether a funding applicant is likely to succeed in their venture or not.


## Credits:
This code was compiled and written by me for the deep-learning-challenge project in the 2024 Data Analytics Boot Camp hosted by Monash University. Additional credits are declared below.

### Saving model outputs as HDF5 file:
https://www.tensorflow.org/tutorials/keras/save_and_load#hdf5_format (Accessed 22 July 2024).

### keras tuner for auto-optimisation of model hyperparameters:
https://keras.io/guides/keras_tuner/getting_started/ (Accessed 22 July 2024).

# Cryptocurrencies 
*Unsupervised Machine Learning CryptoCurrency Analysis* 
## Project Overview 
For this project we are using several models of **Unsupervised Machine Learning** on a cryptocurrency data in order to discover 
patterns and groups in data.   The purpose of this analysis is to create a report that includes what cryptocurrencies are on the 
trading market and how they could be grouped in order to create a classification system for potential new investments into the 
cryptocurrency market. 
 
#### Resources: 
-  Data sources:  **crypto_data.csv** (very large data file)
-  Sofware: **Jupyter Notebook**
-  Languages: **Python**
-  Libraries: **SKLearn/Scikit-learn**, **Pandas**, **Plotly**, **Maptplotlib**
-  Environment: **Python 3.7**
 
## Procedure and Results 
I order to use unsupervised machine learning models on the data, the data needs to be processed in order to fit the machine learning
models.  There is no known output and the unsupervised ML is ideal for that type of analysis.  

#### Step 1:  Reprocessing the Data 
Before using data on unsupervised ML algorithms, the data has to pre-processed properly in order to avoid any errors and to 
ensure we are getting the right results.  
These steps include:
 - **data selection** such as what data is available, what data is missing, and what data can be removed.
 - **data processing** such as organizing the data by formatting, cleaning, and sampling.
 - **data transformation** such as transforming data into a simpler format for storage and future use, like a CSV, spreadsheet, or database file.

Requirements for a useable dataset are below.  This becomes our "to do" list for preparing the data.   
 -  **Null values and missing data:**  Unsupervised learning models can't handle null values or missing data.  Drop null or mising values or
make a decision and drop the entire column.
-  **Datatype:** All data has to be converted to numerical data type. 
-  **Duplicates:** Remove duplicates, they aren't telling us anything new and can skew the results.    
-  **Scaled values:** Data has been manipulated to ensure that the variance between the numbers won't skew the results.   When features have different 
scales they can have disproportionate impact onthe model.  The unscaled value could lead to messy graphs.  Therefore, it is important to 
understand when to scale and normalize data.  For example, if four columns of data are single digits, and the fifth column is in the millions, 
we would need to scale the fifth column to align the other four (A). 

#### Step 2:  Feature Elimination, Feature Extraction & Reducing Data Dimensions using PCA 
Having too many features in the dataset when working with unsupervised ML can cause **overfitting**.  To avoid this, we can use the process
of reducing features also known as **dimensionality reduction**.  There are two options for coping with too many features:  **elimination** and 
**extraction**.  

**Feature Elimination** removes a good amount of features so the model won't be run using every column.  
**Feature Extraction** combines all features into a new set that is ordered by how well they predict our original variable.  
**PCA** is statristical technique to sped up machine learning algorithms when the number of input features (or dimensions) is too high. 
PCA reduces the number of dimensions by transforming a large set of variables into a smaller one that contains most of the information in 
the original large set (B).
The first step in  PCA is to standardize these features by using the StandardScaler library.  After the date has been standardized to 
use PCA to reduce the number of features (argument of n_components) in order to get a smaller set of dimensions called principal ***components.***
Thse new components are new main dimensions of variation that contain most of the information in the original dataset(B).  
Explained Variance Ration tells us how much information can be attributed to each principal component: for example the first principal component
contains 72.77% of the variance and the second contains 23.03%.  Together, they contain 95.80% of the information (B).  

#### Step 3:  Clustering Cryptocurrencies Using K-means and finding the Best Value using Elbow Curve
**Clustering** is a type of unsupervised learning that groups data points together (C). 
**K-means** is an unsupervised learning algorithm used to identify and solve clustering issues.  K represents how many clusters there will be. 
These clusters are then determined by the means of all the points that will belong to the cluster.  The K-means algorithm groups the data into
K clusters, where belonging to a cluster is baesd on some similarity or distance measure to a centroid.  The centroid is found by taking the mean
mean of all the x-values in the cluster, and the mean of all the y-values in a cluster (D). 
**Elbow Curve** is an easy method for determining the best number for K-means.  To create the elbow curve, two values are needed - a list 
of K values and a list of inertia values.  Loop through the 10 values for K, for example and determine the inertia: range(1, 11) (E).  
**Inertia** is one of the most common objective functions to use wehn creating an elbow curve.  The inertia is measuring the amount of 
variation in the dataset. The inertia measuring the amount of variation in the dataset. Inertia is the objective fucntion to plot K values against. (E).  

#### Step 4:  Visualizing Cryptocurrencies Results and Interpretation
Visualizing the clusters helps to graphically understand how they are arranged.   

**3D graph and PCA visualization** iFor 3D visualization we used **3D scatter plot** with **Plotly Express**.  Three principal components
(on x, y, and z axis), that were created with PCA algorithm are plotted on the graph. These 3 components contains most of the information 
in the original large data set.  As we can see the form of the graph, cryptocurrency is clustered in 4 groups with similar characteristics.  When 
we hover over the specific element the graph shows label with Coin Name and its Algorithm.  

<p align="center">
  <img width="600" height="500" src="https://github.com/mjrotter4445/CryptoCurrencies/blob/main/Graphics/Figure1_Crypto%203Dviz.gif">
</p>
<p align="center">
Figure 1-Cryptocurrencies clustered in 4 main groups-video
</p>

**2D visualization and correlation between Total Coins Suply and Total Coins Mined**
For 2D visualization I used hvPlot, a graphing library that allows deeper exploration of the data.  This graph has Total Coins Supply 
on y-axis and Total Coins Mined on x-axis. From the graph we can see correlation between those two components.  Different colors indicate different 
classes that crypto coins belong to.  When we hover over the specific element the graph shows labels with Coin Name and its Class.  


<p align="center">
  <img width="800" height="400" src="https://github.com/mjrotter4445/CryptoCurrencies/blob/main/Graphics/fig2_2dvideo.gif">
</p>
<p align="center">
Figure 2-Interactive Correlation between Total Coins Supply and Total Coins Mined
</p>



<p align="center">
  <img width="600" height="300" src="https://github.com/mjrotter4445/Working-File/blob/main/Fig3_clust_df_tradable_crypto.jpg">
</p>
<p align="center">
Figure 3-Table of Tradable Crypto Coins
</p>
  
**References**:   
Module 18:  
(A) 18.2.5 Data Processing 
(B) 18.5.2 Principal Component Analysis (PCA)
(C) 18.3.1 Clustering Data
(D) 18.3.2 K-means Algorithm 
(E) 18.4.1 Elbow Curve

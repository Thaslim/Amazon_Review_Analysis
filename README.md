# Sentiment Analysis and Recommender System on Amazon Reviews

Sentiment Analysis and Recommender System based on Amazon Reviews for Home and Kitchen Dataset.

## Overview
The number of people who prefer online shopping is rapidly increasing due to the technological advancement and convenience of shopping anywhere at any time. The recent studies show that the most of all online shoppers use reviews to decide on what products to buy. Reviews not only help customers, but it also helps to strengthen sellers' trustworthiness. Amazon is the world’s largest retailer with millions of products. This project deals with the study of statistical analysis of reviews and ratings by Amazon users.

   ### Project Goals:
   1. Do topic modeling(LDA) on review comments
   2. Build a recommendation system using collaborative filtering (ALS) method and topic modeling (LDA) method and compare their respective results
   3. Use topics generated from LDA and analyze sentiment of the reviews in order to score products by the topics mentioned in their reviews.

## Data Collection and Preparation

The [amazon review datasets](https://nijianmo.github.io/amazon/index.html) are freely available online. For this analysis we used a dataset specific to the “Home and Kitchen” category. Initially we explored the complete review data which had 21million entries, later we decided to work on a smaller subset which had 7million entries, due to technical difficulties faced by some of us.
The dataset has following fields – reviewerID - the id of the user, asin - Amazon product id, reviewerName - name of the user, vote - the number of times the review was voted helpful, reviewText - the actual content of the review, overall - the rating of the product ranging from 1 to 5, summary - the title of the review, unixReviewTime - the time of the review in Unix format, reviewTime - the time of the review, style -a dictionary of the product metadata, e.g., "Format" is "Hardcover" , image - images that users post after they have received the product.

Link to the preprocessed dataset => [Home & Kitchen Preprocessed Data](https://drive.google.com/drive/folders/1YIFgIOtMTuOEHUJEJfFV_mLE8lwz8unC?usp=sharing)

## Topic Modeling with [LDA](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation)

### Steps to run Topic_modeling.ipynb
The dataset contains roughly 6 million data points. GPU is preferred for faster execution.(used HPC access provided by sjsu)
#### Required packages:
     python version 3.6.10
     pip install gensim
     pip install pandas
     pip install nltk and download(stopwords, wordnet corpuses)
     pip install pyLDAvis
##### [Download](https://github.com/Thaslim/Amazon_Review_Analysis/blob/master/LDA%20-%20Recommender/Topic_Modeling_grouped.ipynb) Topic_Modeling_grouped.ipynb and run it using jupyter notebook It will save generated model, corpus, and dictionary.
##### [Download](https://github.com/Thaslim/Amazon_Review_Analysis/blob/master/LDA%20-%20Recommender/Recommendation_LDA.ipynb) Recommendation_LDA.ipynb and run it with Jupyter Notebook to get recommendations
## [Visualize](https://thaslim.github.io/Amazon_Review_Analysis/)  generated topic

## [Recommender system](https://en.wikipedia.org/wiki/Recommender_system) using [ALS](https://spark.apache.org/docs/latest/mllib-collaborative-filtering.html)

### Steps to run file using Apache Spark:
Spark is implemented on Hadoop that is HDFS (hadoop distributed file system). Following versions of Java and Python needs to  be maintained to run recommendation system (ALS) file.
#### Packages:
    1. Maintain java 8 version. java version "1.8.0_102" (brew cask install java8)
    2. Upgrade python to latest version (brew upgrade python)
    3. Install pyspark. (pip3 install pyspark)
   
#### Run the following commands on your terminal:
    1. pip3 show pyspark
   
     Gives below output:

      Name: pyspark
      Version: 2.4.5
      Summary: Apache Spark Python API
      Home-page: https://github.com/apache/spark/tree/master/python
      Author: Spark Developers
      Author-email: dev@spark.apache.org
      License: http://www.apache.org/licenses/LICENSE-2.0
      Location: /opt/anaconda3/lib/python3.7/site-packages
      Requires: py4j
      Required-by: 

    2. vi ~/.bash_profile
    3. export SPARK_HOME= /opt/anaconda3/lib/python3.7/site-packages/pyspark
    4. export PATH=$SPARK_HOME/bin:$PATH
    5. pip3 install findspark
    6. jupyter notebook

### ALS for recommendations:
   1. Item Based Collaborative Filtering
   2. User Based Collaborative Filtering

Dataset after preprocessing for ALS => [ALS_AmazonRantings and ALS_AmazonTitles](https://drive.google.com/drive/folders/1YIFgIOtMTuOEHUJEJfFV_mLE8lwz8unC?usp=sharing)

##### Now download the files:

   1. [Recommendation System (Item Based)](https://github.com/Thaslim/Amazon_Review_Analysis/blob/master/ALS%20Recommendation%20System/Step3_ALS%20Collaborative%20Filtering%20(User%20Based).ipynb) file and run using jupyter notebook.

   2. [Recommendation System (User Based)](https://github.com/Thaslim/Amazon_Review_Analysis/blob/master/ALS%20Recommendation%20System/Step4_ALS%20Collaborative%20Filtering%20(Item%20Based).ipynb) file and run using jupyter notebook.

## Topic Modeling and Sentiment Analysis
1. Topic Modelling and Sentiment Analysis using VADER
2. Topic Modelling and Sentiment Analysis using TextBlob

### Steps to run Topic Modelling and Sentiment Analysis files using TextBlob

### Steps to run Topic Modelling and Sentiment Analysis files using TextBlob
    1. Install the following libraries using pip3: 
      pip3 install pandas
      pip3 install pickle
      pip3 install numpy
      pip3 install TextBlob
      pip3 install gensim
      pip3 install spacy
      pip3 install pyLDAvis

    2. Download the file from the path and update the file path in 'mallet_path' variable. 
      File Path : http://mallet.cs.umass.edu/dist/mallet-2.0.8.zip

    3. Open a Python console and do the following: 
      import nltk
      nltk.download()
      Select stopwords from the Corpora tab in the GUI that opens and click on download. 

    4. Run the file [LDA And Sentiment Analysis for Single product using textblob](LDA_Sentiment_Similar_Products_Sheets.ipynb) for results
   
    5. Run the file [LDA And Sentiment Analysis for group of similar products using textblob](https://github.com/Thaslim/Amazon_Review_Analysis/blob/master/Topic%20Modelling%20and%20Sentiment%20Analysis/Sentiment%20Analysis%20TextBlob/LDA_Sentiment_Single_Product_B00FLYWNYQ_Cooker.ipynb) for results
  


[Topic Modeling with sentiment Analysis](https://github.com/Thaslim/Amazon_Review_Analysis/blob/master/Sentiment%20Analysis/Amazon_Reviews_Topic_Modeling.ipynb) 

## Tableau for Visualizations
Used tableau for making visualizations on our large dataset holding millions of data.

### Setting up [Tableau](https://www.tableau.com/academic/students/) for visualization
      1. Downloaded Tableau desktop-free version available for students.
      2. MySql workbench latest version is installed. 
      3. Install pymysql and sqlalchemy
      4. Open jupyter Notebook, load the preprocessed dataset into pandas dataframe
      5. Run the following command to establish connection to mysql server
            from sqlalchemy import create_engine
            import pymysql
            engine = create_engine("mysql+pymysql://{user}:{pw}@localhost/{db}".format(user="root",pw="pwd",db="DB_Name"))
      6. Insert whole DataFrame into MySQL using the following line
            df.to_sql('Table_name', con = engine, if_exists = 'append', chunksize = 1000)
      7. Open Tableau select Datasource from MySql server, Open worksheet and start plotting!
 
### Visualizations : 
1. Sum of ratings for each product to show teh top products having highest ratings. The bars in this plot are labeled by number of records per each productID.
2. Change in ratings and reviews over the years
3. Overall Rating distribution
4. Fetching Ratings distribution in a month.


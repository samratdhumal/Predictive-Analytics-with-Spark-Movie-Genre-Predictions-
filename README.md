# Predictive Analytics with Spark (Movie Genre Predictions)
## Technology Used: Spark
##    The objective of this assignment is to get started with predictive Analytics with Apache Spark. The goals of the assignment are to use Spark Libraries to implement an end to end Predictive Analytics Pipeline and introduce you to the data science competition platform Kaggle.


		
## Movie Genre Prediction

### 1.	PART 1 - Basic Model
#### Setup
●	We have executed this assignment in the provided VM setup without any additional changes. We used Spark version 2.4.0 and Hadoop version 2.7 to create the model as provided in the VM.
#### Preprocessing
●	We started our analysis by importing various pyspark libraries such as pyspark.sql, pyspark.ml, Pandas, and re.<br />
●	We loaded train, test, and mapping data from a csv file using pandas and loaded it into a pyspark dataframe.<br />
●	Next we took the mapping dataframe and genre column from the train dataframe. Now for each element in the mapping dataframe we checked if it is the same as the element in the row of genre. If it is the same we gave it a value of 1, else a value of 0 is assigned. This way we got twenty values for each row in genre as a list. This step is to convert our labels i.e. genre column in the form we want for processing data and generating output in the format given in sample.csv.<br />
●	Next we took the data frame created in the above step and combined it with the train dataframe using index.<br />
●	For the next step we took a plot column from the train and test dataframe. First we converted the whole string to lowercase. Then we tokenized the string to get individual words from the string. Lastly we removed stop words, punctuations, and blank spaces from vectors created. After completing this process for the train data we only retained ‘movie_id’, ‘plot_output’, and ‘map_list’ columns and for test data we only retained ‘movie_id’ and ‘plot_output’ columns.

#### Term Document Matrix
●	We used the CountVectorizer method on the plot_output column. We considered 500 words(vocal size=500) and also we used minDF=20 to remove words coming from more than 20 plots of the movie. minDf is used to remove document specific stop words.<br />
●	We transformed both train and test data using the CountVectorizer model.

#### Basic Model
●	From the map_list column we divided each value of genre in different columns to fit twenty Logistic Regression models.<br />
●	In the basic model we fit a logistic regression model and gathered predictions in different columns.<br />
●	After prediction of all genres we combined all predictions in one column as a list.<br />
#### Macro F1 Score 
●	0.84088

### 2.	PART 2 - Use TF-IDF to improve the model 
#### Preprocessing
●	We followed the same steps of preprocessing as done in part 1.
	
#### Term Frequency-Inverse Document Frequency
●	We used hashingTF and IDF to create term frequency vectors for train and test dataframes.
#### Model
●	From the map_list column we divided each value of genre in different columns to fit twenty Logistic Regression models.<br />
●	In the model we fit a logistic regression model and gathered predictions in different columns.<br />
●	After prediction of all genres we combined all predictions in one column as a list.
#### Macro F1 Score 
●	0.93955
### 3.	PART 3 - Custom Feature Engineering
#### Preprocessing
●	We followed the same steps of preprocessing as done in part 1.
#### Word2Vec
●	We used Word2Vec with parameters including VectorSize=100, i.e. we consider 100 words for prediction and minCount=5, i.e. ignore all words that came less than 5 times in document to create term frequency vectors for train and test dataframes.
#### Model
●	From the map_list column we divided each value of genre in different columns to fit twenty Logistic Regression models.<br />
●	In the model we fit a logistic regression model and gathered predictions in different columns.<br />
●	After prediction of all genres we combined all predictions in one column as a list.

#### Macro F1 Score 
●	0.94271

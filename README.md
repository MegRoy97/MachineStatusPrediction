# MachineStatusPrediction
A multiclass multioutput problem that tries to predict whether any failure occurred or not and the type of failure that has occurred for a given machine

# The dataset used:
	Dataset used is the following: Machine Predictive Maintenance Classification [Dataset to predict machine failure (binary) and type (multiclass)]
                      
# Data source: 
  Kaggle.com

# Number of samples and features
                      Number of samples: 10k rows
                      Number of features: 10 columns – 8 independent variables, 2 dependent variables

# Data characteristics:
<ul>
 <li>Most of the columns were numeric, except Product ID which has been used as an index in this project and Type which mentions product quality of the machine. </li>
 <li>Dependent variables are the columns Target (mentions whether failure happened or not) and Failure Type (mentions the type of failure that has occurred)</li>
 <li>The data itself is extremely skewed – 97% of the rows are marked as ‘no failure’ while the other 3% is marked as different types of failures.</li>
</ul>

# The preprocessing steps:
<ul>
<li>The data had quite a few rows which were marked with the incorrect output. After studying the CSV file, it is seen that some ‘Random Failures’ in Failure Type column have been marked as 0 in Target column, when they should be marked as 1. And some rows, where Target is marked as 1 (failure), Failure Type has been marked as 'No Failure’. This had to be corrected.</li>

<li>Dropped the column UDI as it was doing the same work as Product ID (i.e., providing a form of indexing)</li>

  <li>Used LabelEncoder to convert Type and Failure Type columns to numeric values</li>

<li>Since columns Air Temperature [K] and Process Temperature [K] have high correlation, PCA has been used to generate two new columns that ensure the importance of the columns are retained which handling the issue of high correlation.</li>
</ul>

# Modelling and Results

The dataset did not have different training and test files, so the original dataset is divided into a 80-20 training and test ratio 

Since the dataset is incredibly skewed, it is desirable to split the dataset into train and test sets in a way that preserves the same proportions of examples in each class as observed in the original dataset. The options shuffle and stratify in the train_test_split function to handle this to some extent. 

Sklearn’s Pipeline, MultiOutputClassifier and Logistic Regression are used for the modelling

The score of the model using the training dataset is 0.936 or 93.6%

The score of the model using test dataset is 0.964 or 96.4%

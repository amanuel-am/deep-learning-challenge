# deep-learning-challenge
The CSV contains more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special considerations for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

the project comprises of :
- Data Preprocessing
- model building using neural network and 
- model optimization

# Data preprocessing
1. for the first model Dropped the non-beneficial ID columns, 'EIN' and 'NAME'.  Choose a cutoff value of 500 for application types to be replaced and 1000 for classification column. Converted categorical data to numeric with `pd.get_dummies`. splitted the preprocessed Data into training and Test dataset.

2. For the optimized model name column is not dropped instead 'SPECIAL_CONSIDERATIONS'and 'STATUS' are dropped in addition to 'EIN' column. created bins for the 'ASK_AMT' with labels = ['Very Low', 'Low', 'Medium', 'High', 'Very High', 'Extreme']. splitted the preprocessed Data into training and Test dataset.


# Compiling, Training, and Evaluating the Model
1. the original model has two hidden layers with 12 and 24 neurons consequetively
 - Accuracy 73%

Model: "sequential"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense (Dense)               (None, 12)                528       
                                                                 
 dropout (Dropout)           (None, 12)                0         
                                                                 
 dense_1 (Dense)             (None, 24)                312       
                                                                 
 dropout_1 (Dropout)         (None, 24)                0         
                                                                 
 dense_2 (Dense)             (None, 1)                 25        
                                                                 
=================================================================
Total params: 865
Trainable params: 865
Non-trainable params: 0
_________________________________________________________________

2. the otimized model uses three hidden layers with 12, 24 and 12 neurons consequetively
 - Accuracy 77.9%

 Model: "sequential_1"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense_4 (Dense)             (None, 12)                3192      
                                                                 
 dropout_2 (Dropout)         (None, 12)                0         
                                                                 
 dense_5 (Dense)             (None, 24)                312       
                                                                 
 dropout_3 (Dropout)         (None, 24)                0         
                                                                 
 dense_6 (Dense)             (None, 12)                300       
                                                                 
 dense_7 (Dense)             (None, 1)                 13        
                                                                 
=================================================================
Total params: 3,817
Trainable params: 3,817
Non-trainable params: 0
_________________________________________________________________


# SUMMARY
overall the optimized model showed better Accuracy because it comprises of important features from the dataset and the network has more layers and neurons.
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
- The model starts with an input layer that accepts a number of input features.
- Two hidden layers are included to capture complex patterns in the data:
- The first hidden layer contains 12 neurons (nodes), each applying a ReLU activation function and regularization to prevent overfitting.
- The second hidden layer contains 24 neurons, also using ReLU activation and regularization.
- Dropout layers are added after each hidden layer to randomly drop out some neurons during training, which helps prevent overfitting and improves the model's generalization to new data.
- The output layer contains a single neuron with a sigmoid activation function, which outputs a probability score indicating whether the organization successfully used the funding.

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


 - Accuracy 73%

 - The initial model, with an accuracy of 73%, correctly predicts whether the funding was used effectively in 73 out of 100 cases. This is a decent start, but there is room for improvement. The accuracy indicates that while the model captures some patterns in the data, it may still miss or misinterpret certain relationships, leading to incorrect predictions in about 27% of cases.



2. the otimized model uses three hidden layers with 12, 24 and 12 neurons consequetively
- Adding a third hidden layer increases the model's depth, enabling it to learn more complex patterns. While too many layers might lead to overfitting, three layers strike a balance.
- First Hidden Layer (12 neurons): Starting with a relatively small number of neurons in the first hidden layer allows the model to begin capturing simple patterns in the data. 
- Second Hidden Layer (24 neurons): The increase to 24 neurons in the second layer allows the model to capture more complex patterns and interactions between the features.
- Third Hidden Layer (12 neurons): The reduction back to 12 neurons in the third layer is strategic. It serves as a funnel to compress the learned information before it is passed to the output layer, potentially improving generalization by reducing the likelihood of overfitting.

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

 - Accuracy 77.9%

- After optimizing the model by adding an additional hidden layer and fine-tuning the number of neurons and regularization techniques, the accuracy improved to 77.9%. This represents a significant enhancement in the model’s ability to correctly classify whether the funding was used effectively. The nearly 5% increase in accuracy means that the model now makes fewer mistakes, correctly predicting outcomes in almost 78 out of 100 cases.

 


# SUMMARY
overall the optimized model showed better Accuracy because it comprises of important features from the dataset and the outcomes from both models provide insight into their effectiveness and reliability. While the initial model provides a baseline understanding, the optimized model demonstrates a clear improvement in predictive capability. This increase in accuracy not only signifies better model performance but also translates to real-world benefits, such as more effective use of resources, improved decision-making, and greater confidence in the model's outputs. Overall, the optimized model's higher accuracy represents a meaningful advancement in both technical performance and practical application.

# Exploring alternative model
Using a Random Forest model to solve the problem offers a balance between performance and interpretability, making it a strong alternative to a deep neural network. While it may not capture extremely complex patterns as effectively as a neural network, its robustness to overfitting, ability to handle non-linear relationships, and ease of interpretation make it a compelling choice for this problem, particularly when transparency and computational efficiency are key concerns.
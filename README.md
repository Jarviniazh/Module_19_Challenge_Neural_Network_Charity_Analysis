# Neural Network Charity Analysis

## Overview
### Purpose
This project aims to help Beks, a data scientist and programmer from the nonprofit foundation Alphabet Soup, to predict where to make investment in the future. I will create a binary classifier that is capable of predicting whether applicants will be successful if funded. After processing the investment data over past 20 years, I will design and train a deep learning neural network to predict which organizations are worth funding.   

## Results
- **Data Processing**
  - Target: IS_SUCCESSFUL - 1=The money used effectively, 0=The money didn't use effectively
  - Features: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS(Was eliminated during Attempt 1&4), ASK_AMT 
  - Unnecessary variables: EIN, NAME, SPECIAL_CONSIDERATIONS(Attempt 1&4)
 
- **Compiling, Training, and Evaluating the Model**
  <br> At the first trail, I simply dropped EIN and NAME, the unrelated columns. Then create 2 hidden layer with 80 and 30 neurons respectively. The accuracy score was 0.7247 not over ideal 75%.
  <p align="center">
  <img src="https://github.com/Jarviniazh/Module_19_Challenge_Neural_Network_Charity_Analysis/blob/main/Resources/D2_Accuracy.png"> 
  </p>
  <br> Therefore I would like to test whether could I increase the model performance:
  
  - Attempts to improve the model performance
    - **Attempt 1**: Adjust the input data by dropping one more column - SPECIAL_CONSIDERATIONS, and bucketing ASK_AMT into 8 groups.<br> The accuracy score decreased to 0.719.
    <p align="center">
    <img src="https://github.com/Jarviniazh/Module_19_Challenge_Neural_Network_Charity_Analysis/blob/main/Resources/D3_Atp1_Accuracy.png">
    </p>
    
    - **Attempt 2**: Add 1 more hidden layer, and increase the number of neurons in each layer to 80.<br> The accuracy score 0.7248 was close to the initial model.
    <p align="center">
    <img src="https://github.com/Jarviniazh/Module_19_Challenge_Neural_Network_Charity_Analysis/blob/main/Resources/D3_Atp2_Accuracy.png">
    </p> 
    
    - **Attempt 3**: Change the activation function from ReLU to Tanh.<br> The accuracy score slightly increased to 0.7252 
    <p align="center">
    <img src="https://github.com/Jarviniazh/Module_19_Challenge_Neural_Network_Charity_Analysis/blob/main/Resources/D3_Atp3_Accuracy.png">
    </p>
    
    - **Attempt 4**: Try to combine previous attempts together and modify some features in neural network model. First I dropped the SPECIAL_CONSIDERATIONS column, then added 1 more hidden layer, and increased the number of neurons in each layer to 80. Besides, I changed the testing and training split rate to 0.6 and added a dropout layer before each hidden layer to prevent overfitting. Last but not least, defined a larger batch size to save processing time. <br> The accuracy score increased to 0.73, which was the highest until now. 
    <p align="center">
    <img src="https://github.com/Jarviniazh/Module_19_Challenge_Neural_Network_Charity_Analysis/blob/main/Resources/D3_Atp4_Accuracy.png">
    </p>
    
  - Neural Network Model with best performance (Attempt 4)
    - Number of neurons in each layer: 80
    - Number of layers: 3
    - Activation function: Rectified Linear Unit (ReLU) 

## Summary   
None of the optimization attempts in this analysis were able to produce a model with a predictive accuracy level of 75% or higher. This might be caused by too many feature variables were put into the model. The number of neurons in the hidden layers may need to be adjusted, as well as the number of epochs. 

Instead of using deep learning model, a random forest classifier. The random forest classifier is able to achieve comparable predictive accuracy on large tabular data with less code and faster performance. With sufficient number of estimators and tree depth, it might get a better performance with less computational capacity.

# Neural_Network_Charity_Analysis
Designing, evaluating, and attempting to optimize a neural network model. 

## Overview
The purpose of this analysis is to design a model that will help predict whether different charities will be successful if funded by a philanthropic organization. 

## Results

### Data Preprocessing
- Target: The column IS_SUCCESSFUL contains two values, 0 for 'false' (the charity is not successful) and 1 for 'true' (the charity is successful). This column is the target variable. 
- Features: The following columns are considered the feature variables for the initial model: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT.
- Variables to remove: The columns EIN and NAME are identifiers and do not add relevent information so they are removed from the data set. 

### Compiling, Training, and Evaluating the Model
- The original model contained two hidden layers with 80 and 30 neurons respectively. The relu activation function was used for both hidden layers, and the sigmoid function was used for the output layer. 
- Unfortunately the model was not able to achieve the target performance of 75% accuracy. The original model's accuracy was 72.49%  and the maximum acheieved even after several optimization attempts was 72.9%
- The following steps were taken to try to increase model performance:
    - **Binning the ASK_AMT column:** the vast majority of the values in this column were exactly $5000, so binning was used to create separate columns for ASK_AMT_5000 and ASK_AMT_OVER_5000. This resulted in the accuracy increasing marginally to 72.75%
    ![ask_amt_binning](https://user-images.githubusercontent.com/99051640/184456709-c203a9e7-37d6-468d-9804-41e583ec4fe4.png)
    
    - **Adding a third hidden layer:** The number of neurons was aslo changed to be 75 for the first, 38 for the second, and 19 for the third layer.This model still outperformed the original at 72.69% accuracy but dropped below the previous attempt with only 2 hidden layers.
    ![third_hidden_layer](https://user-images.githubusercontent.com/99051640/184456796-e5f758d2-89f4-4124-8aef-f88a5cf19681.png)

    - **Reducing the number of neurons significantly and using different activation functions:** The two original hidden layers were changed to contain 8 neurons in the first layer, and 5 in the second. Also, the activation functions in the hidden layers were both changed to 'tanh'. These changes combined with the first step of binning the ASK_AMT variable resulted in the highest model accuracy achieved, 72.9%.
        - When the changes were made separately, no increase was seen. 
        - When changing the hidden layer neurons to 15 and 8, the model's accuracy dropped.
    ![tanh_functions](https://user-images.githubusercontent.com/99051640/184456863-aec15f1a-1ebd-4310-be4f-616755bce67e.png)

## Summary

Unfortunately the model did not achieve the target accuracy of 75%. The accuracy did however improve slightly from 72.49% to 7.9%. It is possible that a different machine learning model could help achieve a higher accuracy and be a better fit for the aim of this analysis. 



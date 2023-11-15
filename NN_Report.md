# deep-learning-challenge

## Overview:
 * The purpose of this analysis is to develop a Machine Learning model from the Tensor Flow/Keras API that can accurately identify which applicants of the non-profit foundation AlphabetSoup will be successful or unsuccessful. Will the resources of the foundation be put to good use in the future, Or will applicants waste them? This model should allow AlphabetSoup to determine if an applicant will be a worthwhile investment.

## Results:
### Data Preprocessing
  * After recieving a CSV of all previous applications and their variables, outcomes, etc. the data was processed before the model was created.
      * Target Variables includ: A binary categorical classification of 0 (unsuccessful) or 1 (successful). Found in the "IS_SUCCESSFUL" column.
      * Feature Variables include: "APPLICATION_TYPE",	"AFFILIATION",	"CLASSIFICATION",	"USE_CASE",	"ORGANIZATION",	"INCOME_AMT",	"ASK_AMT".
      * Removed Variables include: "EIN", "NAME", "STATUS", "SPECIAL_CONSIDERATIONS"
      * The data was OneHotEncoded using the Pandas .get_dummies() method, resulting in 37 features in total.
      * The data was then standardized using a Standard Scaler, and split up between features and target so that the data can be properly passed into the model.
  * (After evaluating the first poorly performing model, the data was also processed (before One Hot Encoding) using the Principal Component Analysis method)

### Compiling, Training, and Evaluating the Model
  * The first model compiled for this dataset included 3 layers:
    - First Layer: Input layer with 3 neurons, 36 input units, and using the "tanh" activation function.
    - Second Layer: Hidden layer with 4 neurons and using the "tahn" activation function.
    - Output Layer: Final layer with 1 neuron and using the "sigmoid" activation function to result in a binary classification.
  * Performance?
    - The performance of this model was sub-optimal, resulting in an accuracy of around 72% and a loss of 56%.
  * Corrective Measures.
    - (Code located in Starter_Code_Optimized.ipynb)
    - To ensure a better performing model I pre-processed the data using PCA analysis to reduce the number of columns in the dataset down to a managable 3, then set up a HyperParameter Tuning function to determine the preferred number of layers, neurons, activation functions, etc. This process ran for about 44 minutes.
    - Using the second highest scoring model I compiled a new model based on those specifcations and trained it over 20 epochs. The resulting model scored a loss of 3% and an accuracy: of 98.89%.

### Summary: Summarize the overall results of the deep learning model. 
  * The second model results in an extremely accurate prediction of applicants and their chances of running a successful campaign. The  resources of AlphabetSoup are far more likely to be put to successful and productive use in the future when evaluated with this model.
  * Note: This model is EXTREMELY accurate, which could imply that while the model is functional, it could also be overfit to the data, meaning that applicants whose specifications stary too far from what the previous data includes could result in an incorrect classification.
  * Recommendation: A more refined model that might be less accurate but still results in a low percentage of loss might be needed. 

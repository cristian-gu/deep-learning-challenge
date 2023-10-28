1. Overview

The purpose of this analysis is to use nueral netweorks to help AlphabetSoup accurately predict whether applicants will be successful if funded. The complexity of nueral networks will require the analyst to properly rearrange the dataset, and fine tune our keras model parameters to obtain a more accurate prediction.

2. Results

- Data Preprocessing:
    - The target variables include the "IS_SUCCESSFUL" series as that is the outcome we are trying to analyze for

    - The feature list includes: "APPLICATION_TYPE", "AFFILIATION", "CLASSIFFICATION", "USE_CASE", "ORGANIZATION", "STATUS", "INCOME_AMT", "SPECIAL_CONSIDERATIONS", "ASK_AMT"
        - These all contained different unique categorical values (besides the ASK_AMT field) and are responsible for producing different perceptrons when calculated for among the entire dataset

    - The only features that showed to not have any weight for helping our model predict the "IS_SUCCESSFUL" outcome were "EIN" and "NAME" fields.

- Compiling, Training, and Evaluating the Model:
    - Currently, the following parameters were selected for our keras neural network model:
        - Keras layers: 3 hidden layers, 1 output layer
            - This was in an attempt to give the data more tranformations through iterations of mathemtaical computations and smooth out the signal
        - neurons for each layer: 475
            - Through testing from 6 - 500, the 20 and 475 seemed to give the best results so far
        - activation functions: 3 relu, 1 sigmoid
            - in conjunction with the transformation layers, by keeping the functions consistent proved to keep the model more accurate.

    - Ultimately, was unable to obtain the target performance

    - Steps taken to improve model performance:
        - Initially, reducing the amount of dimensions would seem to increase the amount of accuracy. By not changing to many factors, I reduced the binning groups of the Application type field by combingng the unique factors that had counts less than 1000. I inspected the data features to see what other factors I could reduce the dimensions on and the "Income AMT" field had a few unique categorical values with low counts, almost insignificant to the counts of the other values within the list and decided to combine those under the 500 threshold. So to avoid any uneccessary high variances, by reducing the feature size after my dataset had been dummified, we would hope to retrieve a dataset with less noise and avoid overfitting. I also incorporated an extra keras layer in hopes more transformations were needed. The last factor that would need to be inspected was then the number of EPOCHS, which overall would only get better results from having a high iteration count when executing. However, after reviewal of the accuracy score, most attempts seemed to reduce accuracy. 

3. Summary

Although we were not able to obtain the most accurate neural network model (Only recieving a score of .7261), we could possibly perform better attempts which includes increasing the current neurons in the model as it may not have enough information to give accurate predictions. The loss however does increase substantially at a high epoch size above 700 so the next recommendation would be to figure out the optimal nueron size and right activation layer configuration, but also avoid reducing any more features as that I believe the variance of unique value counts for the original fields are okay. Another option would be to use the keras hyperparameter model as that gives the library to create a more automated method of deciding the size of the node layers and choose the precise activation function to use.
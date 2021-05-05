# Mortality Prediction

## Project Description
The project predicts in ICU and in hospital mortality for any EHR data. The inputs to the project are static patient features - 
1. Age
2. Gender
3. Ethnicity
4. Insurance
5. Type of admission
6. First Care Unit
7. Diagnosis codes in ICD9 format

With any new EHR data the model can be trained and tested. New embeddings can be generated for the new data. After training the embeddings can be used in other models for similar tasks. The prediciton model is quite similar to Word2Vec model (NGrams). Each patients Stay is treated as one single sentence with the above 7 features. Using the 7 features label is predicted. The 7 features first go through an embedding layer then into two fully connected layers to predict one single label probability. Although the project used MIMIC III and used MIMIC III Extraction process as described in the paper MIMIC-Extract: A Data Extraction, Preprocessing, and Representation Pipeline for MIMIC-III by Wang Shirly, et el. but it is designed for using any EHR data.

## Project Goals
1. To develop a generic data pipeline and Model to predict multiple possibilities from EHR data like
    1. In ICU Mortality
    2. In Hospital Mortality
    3. Length of Stay
    4. etc.
2. To generate embeddings for EHR data features. Re-using the embeddings across different models.

## Differences between baseline model and model in this project
1. The mortality prediction models as described in the paper MIMIC-Extract: A Data Extraction, Preprocessing, and Representation Pipeline for MIMIC-III by Wang Shirly, et al. use complex models like GRU or use lot of features like charts features in Random Forest and Linear Regression. The current proposed model use very less number of features and predicts with a better accuracy and F-1 Score on the same dataset.
2. The current model is not temporal where as baselines models were temporal.
3. The baseline models are very slow while current model is very simple and fast. Baseline models take around 40-45 minutes for training and testing where as the current model takes less than 10 minutes for training and testing.
4. The baseline models do not rely on embedding layers and hence embeddings of features cannot be produced from those models. The current model produces feature embeddings which can be useful for other models or transfer learning.

## Requirements

## Results

## Steps to run the notebook

1. Modify the below code according to the dataset columns present in the EHR data being used. The diagnosis codes should be in ICD9 format and in a single vector within pandas dataframe. Paste this modified code as the first cell of the notebook.

```python
# columns to keep as input features in the dataset
static_columns = ['gender', 'ethnicity', 'age', 'insurance', 'admission_type', 'first_careunit', 'icd9_codes']

#icd9 codes column name
icd9 = 'icd9_codes'

# prediciton label column in the dataset
target = 'mort_hosp'
```
2. Load the dataset as a pandas dataframe keep the dataframe's name as d7. A sample using MIMIC-III Extract is provided in the notebook.
3. Run the data transformation and cleansing steps after loading the dataframe.
4. Divide the dataset into three datasets - train, validation and test. This can be done either on the basis of subject_ids as in MIMIC III dataset or based on the some ratio. Both ways are provided in the notebook. For the prior seperate files containing subject_id lists need to be present.
5. Run the training part.
6. Test the model on test dataset.

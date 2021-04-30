# Mortality Prediction

This is a very simple and fast prediciton model. The model is based on Word2Vec and uses the features as one single sentence. Each sentence comprosis of certain static features and icd9 codes for diagnosis.

```python
# columns to keep as input features in the dataset
static_columns = ['gender', 'ethnicity', 'age', 'insurance', 'admission_type', 'first_careunit', 'icd9_codes']

#icd9 codes column name
icd9 = 'icd9_codes'

# prediciton label column in the dataset
target = 'mort_hosp'
```

Change the above code according to the dataset available.
Rename the columns to the columns present in your dataset.
Run the code.

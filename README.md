# The purpose of this analysis is too compare and contrast different machine learninhg models, and contemplate there strengths and weaknesses.

## This project involves the use of several models these are enumerated and displayed below.

### 1. RandomOverSampler
[NaiveRandomOversampling.png](NaiveRandomOversampling.png)
### 2. 
### 3. 
### 3. 
### 3. 
### 3. 
### 3. 
### 3. 
### 3. 
### 3. 
### 3. 




### Naive Random Oversampling


```python
from imblearn.over_sampling import RandomOverSampler

# Display the confusion matrix
from sklearn.metrics import confusion_matrix
y_pred = model.predict(X_test)
confusion_matrix(y_test, y_pred)

```




    array([[  77,   24],
           [8527, 8577]], dtype=int64)




```python
# Calculated the balanced accuracy score
# YCH
from sklearn.metrics import balanced_accuracy_score
balanced_accuracy_score(y_test, y_pred)
```




    0.6319189420111329




```python
# Print the imbalanced classification report
# YCH
from imblearn.metrics import classification_report_imbalanced
print(classification_report_imbalanced(y_test, y_pred))
```

                       pre       rec       spe        f1       geo       iba       sup
    
      high_risk       0.01      0.76      0.50      0.02      0.62      0.39       101
       low_risk       1.00      0.50      0.76      0.67      0.62      0.37     17104
    
    avg / total       0.99      0.50      0.76      0.66      0.62      0.37     17205
    
    

### SMOTE Oversampling


```python
# Resample the training data with SMOTE
# YCH
from imblearn.over_sampling import SMOTE
X_resampled, y_resampled = SMOTE(random_state=1, sampling_strategy='auto').fit_resample(
    X_train, y_train
)
Counter(y_resampled)
```




    Counter({'loan_status': 1})




```python
# Train the Logistic Regression model using the resampled data
# YCH
model = LogisticRegression(solver='lbfgs', random_state=1)
model.fit(X_resampled, y_resampled)
```




    LogisticRegression(random_state=1)




```python
# Calculated the balanced accuracy score
# YCH
y_pred = model.predict(X_test)
balanced_accuracy_score(y_test, y_pred)
```




    0.6607336365067751




```python
# Display the confusion matrix
# YCH
confusion_matrix(y_test, y_pred)
```




    array([[  79,   22],
           [7880, 9224]], dtype=int64)




```python
# Print the imbalanced classification report
# YCH
print(classification_report_imbalanced(y_test, y_pred))
```

                       pre       rec       spe        f1       geo       iba       sup
    
      high_risk       0.01      0.78      0.54      0.02      0.65      0.43       101
       low_risk       1.00      0.54      0.78      0.70      0.65      0.41     17104
    
    avg / total       0.99      0.54      0.78      0.70      0.65      0.41     17205
    
    

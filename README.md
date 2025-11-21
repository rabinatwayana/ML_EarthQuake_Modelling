# Project: Modeling Earthquake Damage
### Dataset Description

The data was collected during the post-earthquake field surveys conducted by the Nepal National Planning Commission and partners following the 2015 Gorkha earthquake. Trained enumerators visited the affected areas and collected information on the level of damage, structural characteristics (foundation, roof, building materials), household information, age, location information, and building use for over 250,000 buildings. The damage level for buildings is categorized from low damage to almost complete destruction.

### Why the data was collected

Although the primary goal of the survey was to identify beneficiaries eligible for government assistance for housing reconstruction, it also collected other useful socio-economic information which serves different uses including training ML tasks. After disasters, government and humanitarian organization usually need rapid and reliable estimates of building damage to prioritize emergency response, assess vulnerability to guide future preparedness and plan recovery operations.

### Application Domain

The data was collected as part of a national post-disaster assesment effort so it's aplication domain falls under disaster risk management, specifically post-disaster damage assessment. By understanding which features contribute most to level of damages, the project can provide insight useful for improving building construction in earthquake-prone areas.

### Learning task to study

The target variable 'damage_grade' represents a discrete numerical value that indicates the level of damage to building. The damage_grade contains distinct values from 1-3. This problem is formulated as a multi-class classification task with the aim of predicting one of several damage grades for each building.

### Model Training and evaluation

The DummyClassifier(Baseline), RandomForest, and HistGradientBoostingClassifier model was trained and evaluated.


 ### Results

#### 10.1 Metric Comparision

**Train Metric**
| S.N | Metric      |DummyClassifier (Baseline)|RF(Default) | RF(GridSearchCV)| RF(Optuna) |HGBC(Default) |HGBC (GridSearchCV)| HGBC (Optuna)|
|-----|-------------|---|---|---|---|--|---|--|
| 1   | Macro F1     | 0.3318|0.9866|0.7921|0.7783|0.6613|0.7125|0.7164|
| 2   | Macro Precision  | 0.3318|0.9880|0.7625|0.7478|0.7238|0.7677|0.7699|
| 3   | Macro Recall    | 0.3318|0.9852|0.8454|0.8340|0.6289|0.6800|0.6845|
| 4   | Accuracy   | 0.4431|0.9873|0.8057|0.7928|0.7233|0.7577|0.7605|

**Test Metric**

| S.N | Metric      |DummyClassifier (Baseline) | RF(Default)|RF(GridSearchCV)| RF(Optuna)|HGBC(Default)|HGBC (GridSearchCV) | HGBC (Optuna) |
|-----|-------------|----|---|---|---|--|---|--|
| 1   | Macro F1     | 0.3361|0.6319|**0.6713**|0.6705|0.6414|0.6649|0.6662|
| 2   | Macro Precision    | 0.3362|0.6673|0.6510|0.6491|0.7048|0.7185|0.7189|
| 3   | Macro Recall    | 0.3361|0.6100|0.7048|0.7078|0.6100|0.6351|0.6368|
| 4   | Accuracy   | 0.4468|0.6947|0.7021|0.7007|0.7113|0.7259|0.7277|

DummyClassifier baseline metrics confirm that all other models provide strong predictive value.

Random Forest (Default): Highest training scores (Macro F1: 0.99) but much lower test performance (Macro F1: 0.63), showing severe overfitting.

Random Forest (GridSearchCV & Optuna): Tuning reduces overfitting and improves generalization. Both GridSearchCV and Optuna results comparable metrics on the test set, better than default and also overfitting has been reduced.

HGBC (Default): There is relatively low difference between training (Macro F1: 0.66) and test metrics (Macro F1: 0.64) which means the model demonstrates a well-controlled fit. 

HGBC (GridSearchCV & Optuna): Tuning enhances generalization performance. The Optuna-tuned model is slightly better than GridSearchCV based.

After tuning the hyperparameters, the performance of both models has been improved. Between RF and HGBC, HGBC tuned models  slightly outperform default and Random Forest, balancing bias-variance tradeoff well. 

### Algorithm recommendation

If we were to recommend a model for deployment in a company or research institute, we would suggest the HistGradientBoostingClassifier. The primary reason is that this model does not casue overfitting with its default parameters, unlike the RandomForest model, which tends to highly overfit without tuning. Furthermore, even after hyperparameter tuning, HistGradientBoostingClassifier delivers competitive test performance while still remaining less prone to overfitting compared to RandomForest.

 Titanic Survival Prediction

This project explores the Titanic passenger data and trains a Random Forest classifier to predict whether a passenger survived. The analysis and charts are in [`nb.ipynb`](./nb.ipynb); the source data are [`train.csv`](./train.csv) and [`test.csv`](./test.csv).

Validation results

The model was evaluated on a 20% holdout from the training data (179 passengers):

| Metric | Score |
| Accuracy | 84.36% |
| ROC-AUC | 0.883 |
| Weighted F1-score | 0.84 |
| Survived-class precision / recall | 0.82 / 0.77 |

These are the results recorded in the notebook, not a guarantee of performance on unseen data. The Random Forest is not assigned a `random_state`, so rerunning training may produce slightly different scores.

Most important features

The notebook reports Random Forest impurity-based feature importance:

| Feature | Importance | Why it may help predict survival |
| Fare | 32.0% | May reflect passengers' wealth, ticket type, and access to better-positioned accommodation and who had access to lifeboats. |
| Title | 21.7% | Extracted from names; helps distinguish groups such as Mr, Mrs, Miss, and Master, which carry age and social-role information. |
| Sex | 13.4% | Survival differed substantially between male and female passengers. |
| AgeGroup | 10.0% | Groups age into categories; children were more likely to be prioritized. |
| Pclass | 8.4% | Passenger class is associated with accommodation and access to evacuation areas. |
| SibSp | 6.8% | The number of siblings/spouses aboard can capture family-group effects. |
| Embarked | 3.9% | Port of embarkation may indirectly capture passenger demographics. |
| Parch | 3.8% | The number of parents/children aboard can also reflect family-group effects. |

These values describe how the fitted forest used the features; they do not show that a feature caused survival. In particular, Fare and Title can act as proxies for other passenger characteristics, and impurity-based importance can favor continuous or high-cardinality features.

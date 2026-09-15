1. Differentiate between variables that are usable and variables that are not usable.

Unusable
  - Unnamed: 32 : blank column from the CSV
  - id: not related with any clinical data and would cause overfitting

Target
  - diagnosis

Usable variables
  - The remaining feature columns

---

7. Based on your analysis results, how many optimal features can be used? Which features are they?

- Selected 19 Features
  - Mean metrics: radius_mean, texture_mean, perimeter_mean, area_mean, compactness_mean, concavity_mean, concave points_mean
  - Standard error metrics: radius_se, perimeter_se, area_se
  - Worst/Extremes metrics: radius_worst, texture_worst, perimeter_worst, area_worst, smoothness_worst, compactness_worst, concavity_worst, concave points_worst, symmetry_worst


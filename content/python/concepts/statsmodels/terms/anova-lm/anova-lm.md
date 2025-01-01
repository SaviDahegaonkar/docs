---
Title: 'Anova-lm'
Description: 'Perform analysis of variance on one or more fitted linear models using the statsmodels library in Python.'
Subjects:
  - 'Data Science'
  - 'Machine Learning'
  - 'Python'
  - 'Statistics'
Tags:
  - 'ANOVA'
  - 'Data Analysis'
  - 'Linear Models'
  - 'Python'
  - 'Statsmodels'
CatalogContent:
  - 'learn-python-3'
  - 'paths/data-science'
---

**`anova_lm()`** is the function in Python's `[statsmodels](https://www.codecademy.com/resources/docs/python/statsmodels)` library, which produces an ANOVA table for one or more fitted linear models. ANOVA is the method which applies statistics to find out if there are differences between means of three or more groups. Researchers and analysts can use `anova_lm` to calculate the effect of categorical variables on a continuous outcome and compare nested models.

## Syntax

```pseudo
statsmodels.stats.anova.anova_lm(*args, **kwargs)
```

- `*args`: One or more fitted model results (e.g., from OLS) to perform ANOVA on.
- `**kwargs`: Optional keyword arguments to customize the ANOVA test, such as scale, test, typ and robust.

## Example

This example demonstrates how to use the `anova_lm()` function in the `statsmodels` library to perform analysis of variance on a fitted linear model.

```py
import statsmodels.api as sm
from statsmodels.formula.api import ols
from statsmodels.stats.anova import anova_lm
import pandas as pd

# Load example data
data = sm.datasets.get_rdataset('iris').data

# Rename columns to make them Python-friendly
data.rename(columns=lambda x: x.replace('.', '_'), inplace=True)

# Fit a linear model
model = ols('Sepal_Length ~ Petal_Length + Petal_Width', data=data).fit()

# Perform ANOVA
anova_results = anova_lm(model, typ=2)

# Print the ANOVA table
print(anova_results)
```

This example produces an ANOVA table showing `sum of squares`, `degrees of freedom`, `F-statistics`, and `p-values`, helping to assess the significance of each predictor in the model.

```shell
                                            sum_sq     df          F        PR(>F)
Petal_Length   9.934196    1.0  61.150938  9.414477e-13
Petal_Width    0.644340    1.0   3.966300  4.827246e-02
Residual      23.880694  147.0        NaN           NaN
```
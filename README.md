# Socio-economic factors associated with the number of suicides in the world"
Python-based analysis project on topic "Socio-economic factors associated with the number of suicides in the world"

## Project structure

- In the datasets folder you will find the datasets used in the study

- Data preprocessing information is represented in the jupyter notebook by markdown entries.

- The "models" folder contains saved trained ML models, data for them and a dictionary for decoding categorical variables.

</br>

---

## Intro

This project was inspired by preventing or, at least, minimizing suicide rates in the world and was done as the final project on the [HSE](https://www.hse.ru/en/) university discipline "Data Analysis on Python" </br>
Presentation, [full version](https://docs.google.com/presentation/d/1E8ZC6B7z8T3rOFHFSbCSj3BqbGwDn7rP4yi0Jklsz6k/edit?usp=sharing)

</br>

---

## Methods and python packages applied

- Data processing ([pandas](https://pandas.pydata.org/))
- Interactive plots ([plotly](https://plotly.com/python/plotly-express/)) <img src="README_resources\plotly_express_regression.gif" alt= “” width="40%" height="value" style="display: block">
- Static plots ([matplotlib](https://matplotlib.org/))
- Statistic criteria ([scipy.stats](https://docs.scipy.org/doc/scipy/reference/stats.html))
- Linear regression and multiple comparison ([statsmodels](https://www.statsmodels.org/stable/index.html))
- Machine learning (Decision Tree model and validation) ([sklearn](https://scikit-learn.org/stable/))
- Built model serialization ([pickle](https://docs.python.org/3/library/pickle.html))

</br>

---

## Datasets

Three datasets are used, joined by country and year of observation:

- [Suicide Rates Overview (1985 to 2021)](https://www.kaggle.com/datasets/omkargowda/suicide-rates-overview-1985-to-2021) - main dataset </br>
  From this dataset suicides_per_100k as target variable is used.
- [Global Trends in Mental Health Disorder](https://www.kaggle.com/datasets/thedevastator/uncover-global-trends-in-mental-health-disorder) </br>
  Variables of different mental disorders are used, mainly depression, alcoholism and rates.
- [Inflation, Interest and Unemployment Rate](https://www.kaggle.com/datasets/prasertk/inflation-interest-and-unemployment-rate)
  Mainly unemployment and inflation prices rates are used.

</br>

---

## Stated hypotheses and results

1. The suicide rate differs statistically significantly across age groups. ✅
2. The suicide rate differs statistically significantly across generational groups. ✅
3. The suicide rate differs statistically significantly by gender. ✅
4. The suicide rate differs statistically significantly across wealth groups in the country. ✅
5. The suicide rate is negatively statistically significantly associated with the human development index (HDI) ⁉️
6. The suicide rate is positively statistically significantly associated with the rates of psychiatric disorders in the country. ✅
7. The level of GDP per capita is negatively statistically significantly associated with the suicide rate and with the rates of psychiatric disorders in the country.
   ❌
8. The suicide rate in rich countries is greater than or equal to that in poor countries. ✅
9. The suicide rate is positively statistically significantly associated with inflation and unemployment rates. ⁉️

</br>

---

## Built regression model and its results

</br>

$R^2$ - the proportion of the variation in the dependent variable that is predictable from the independent variable(s) </br>
$RMSE$ - root mean square error, basic regression metric, showing error in absolute values </br>
$RMSLE$ - Root Mean Squared Logarithmic Error, used in model validation for decreasing the impact of outliers in target variable </br>
<b>min_samples_split</b> - The minimum number of samples required to split an internal node </br>
<b>max_depth</b> - The maximum depth of the tree </br>

</br>

[Halving search](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.HalvingGridSearchCV.html) with grid of parameters in model fitting was used.

<img src="README_resources\halving_search.png" alt= “” width="50%" height="value" style="display: block">

</br>


Metrics of final regression model:
| Predictors | $R^2$ | $RMSE$ | $RMSLE$ | min_samples_split | max_depth
| ------------------------------------------------------------------------------ | ------- | ------- | ------- | --- | --- |
| age, generation, gender, country income level, alcoholism rate, depression rate | 0.86158 | 1.10141 | 0.30066 | 103 | 20 |

</br>

Final model explains 86% of the variability in the data, predicts the magnitude of the suicide rate (per 100,000 population) with an absolute mean error of 1.1 points.

The inclusion of variables whose relationship with the target variable was statistically confirmed (partiularly in case of alcoholism and depression rates) favorably influenced the predictive power of the model.

</br>

generation predictor values:
| | |
| --- | --- |
|Generation Z | 1997-2012|
|Millennials| 1981-1996|
|Generation X| 1965-1980|
|Boomers | 1946-1964|
|Silent| 1928-1945|
|G.I. Generation | 1901-1927|

</br>

---
## Summarizing
1. Project goals were achieved: 
    - Statistically significant socio-economic factors have been found that affect the rate of suicide (per 100,000 population)
    - A model has been built that predicts the value of the target variable with high accuracy
2. Interesting observations made:
    - Men are the most risky group.
    - Younger social groups have a lower risk of suicide.
    - Rates of psychiatric abnormalities help improve the prognosis of the suicide rate.
3. A basis for further research has been obtained: a detailed analysis of each of the divisions of observations is possible - by age, sex and generations.


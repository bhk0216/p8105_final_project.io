Report
================
Stella Koo
2024-11-26

# Members

Stella Koo (bk2959), Yonghao YU (yy3564)

# Motivation

# Initial Questions

# Data

The Heart Disease datasets were obtained from UC Irvine’s Machine
Learning Repository that can be accessed
[here](https://archive.ics.uci.edu/dataset/45/heart+disease). This
directory contains four datasets focused on heart disease diagnosis,
each representing a distinct geographic location and with attributes
recorded as numeric values. The data was gathered from the following
four locations:

    1. Cleveland Clinic Foundation (cleveland.data)
    2. Hungarian Institute of Cardiology, Budapest (hungarian.data) 
    3. V.A. Medical Center, Long Beach, CA (long-beach-va.data) 
    4. University Hospital, Zurich, Switzerland (switzerland.data)

Although the original datasets contain 76 raw attributes, the source
provides processed datasets with 14 carefully selected variables that
have been widely utilized and cited in numerous research studies. This
project will focus on these processed datasets, which include the
following attributes:

    1. age: age in years
    2. sex: sex (1 = male; 0 = female)
    3. cp: chest pain type (1 = typical angina; 2 = atypical angina; 3 = non-anginal pain; 4 = asymptomatic)
    4. trestbps: resting blood pressure (in mm Hg on admission to the hospital)
    5. chol: serum cholestoral in mg/dl
    6. fbs: fasting blood sugar > 120 mg/dl (1 = true; 0 = false)
    7. restecg: resting electrocardiographic results (0 = normal; 1 = having ST-T wave abnormality; 2 = showing probable or definite left ventricular hypertrophy by Estes' criteria)
    8. thalach: maximum heart rate achieved
    9. exang: exercise induced angina (1 = yes; 0 = no)
    10. oldpeak: T depression induced by exercise relative to rest
    11. slope: slope of the peak exercise ST segment (1 = upsloping; 2 = flat, 3 = downsloping)
    12. ca: number of major vessels (0-3) colored by flourosopy
    13. thal: 3 = normal; 6 = fixed defect; 7 = reversable defect
    14. num: diagnosis of heart disease (0 = < 50% diameter narrowing; 1 = > 50% diameter narrowing)

# Exploratory Analysis

## Data Cleaning and Preprocessing

The first step in the analysis was data cleaning, which involved
handling any missing values across the datasets. After addressing
missing data, descriptive statistics were computed for each variable to
gain an understanding of the data’s distribution. Based on this
analysis, a selection of key variables for further investigation was
made. The final variables chosen for analysis were:

- Age (`age`)
- Resting Blood Pressure (`trestbps`)
- Maximum Heart Rate Achieved (`thalach`)
- Depression Induced by Exercise (`oldpeak`)
- Sex (`sex`)
- Chest Pain Type (`cp`)
- Fasting Blood Sugar (`fbs`)
- Resting Electrocardiographic Results (`restecg`)
- Exercise Induced Angina (`exang`)

Additionally, the heart disease status variable (`num`) was transformed
into a binary format, with 0 indicating no heart disease and 1
indicating the presence of heart disease. This was done to ensure
consistency across the datasets.

The datasets were merged into a single dataset, and an additional column
indicating the region of the data was introduced. This column helped
streamline the analysis, allowing us to perform regional comparisons
more efficiently.

## Initial Visualization

The next step involved visualizing the overall data distribution.
Specifically, `age` and `sex` were plotted against heart disease status
(`num`) to get a general sense of participant distribution across
regions. The initial visualization revealed that there were
significantly more male participants than female participants. This
finding suggested that sex may not be a strong predictor of heart
disease status, and its role in the model should be carefully
considered.

## Variable Categorization

Variables were then categorized into continuous and discrete types:

- **Continuous variables:** Age (`age`), Resting Blood Pressure
  (`trestbps`), Maximum Heart Rate Achieved (`thalach`), Depression
  Induced by Exercise (`oldpeak`)
- **Discrete variables:** Sex (`sex`), Chest Pain Type (`cp`), Fasting
  Blood Sugar (`fbs`), Resting Electrocardiographic Results (`restecg`),
  Exercise Induced Angina (`exang`)

## Continuous Variables

To assess potential multicollinearity, pairwise correlations between
continuous variables were computed per region. The results showed no
signs of multicollinearity, as all correlation coefficients were below
the threshold of 0.7.

Following this, each continuous variable was compared with the heart
disease status (`num`) using box plots. These visualizations helped to
examine the distribution of continuous variables across the two
categories of heart disease status (0 and 1), providing insight into
potential differences between the groups across the regions.

Key findings emerged from the exploratory data analysis:

- T depression and maximum heart rate exhibit consistent trends across
  regions, with clear separation between heart disease statuses, making
  them strong predictors.
- Resting blood pressure shows significant overlap between groups in all
  regions, reducing its standalone predictive power.
- Age is a strong predictor in some regions (Cleveland, Hungary) but
  weaker in others (Long Beach, Switzerland).

Building on these insights, regression analysis was conducted to further
investigate the relationships between the diagnostic attributes and
heart disease status.

## Discrete Variables

# Modelling Analysis

## Variable Selection

### For continuous case

For continuous variables, we use mean and standard deviation (std) to
describe the distribution in overall samples, samples of control(num =
0), and samples of case(num = 1). Then, we use t-test to examine whether
the means of these variables are significantly different between case
group and control group (significance level = 0.05). \### For discrete
case For binary and categorical variables, we use count (n) and
percentage (pct) to describe the distribution in overall samples,
samples of control(num = 0), and samples of case(num = 1). Then, as the
data meet the assumption, we use chi-sq test to examine whether the
distribution of these variables are significantly different between case
group and control group (significance level = 0.05).

Based on the result of both continuous and discrete cases, we can find
that except fbs, the rest of all other binary and categorical features
are significantly different between case and control.

# Discussion
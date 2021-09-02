# Ben Poh Project 1: Standardized Test Analysis

### Introduction

SAT and ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

---

### Problem Statement

You are working for the state education board and your main responsibility is to increase SAT/ACT scores in your state. There are two main areas your stakeholders would like you to explore:
    1.  Your stakeholders have heard that increasing participation rates will result in a fall in SAT/ACT scores. They are concerned that if they increase participation rates (such as via mandatory test policies), the state will have lower mean test scores. Investigating trends in participation rates and test scores, please find out if this is true.
    2. Your stakeholders think that states with higher elementary and secondary school state budgets have higher SAT/ACT scores and increasing the state budgets in this area will improve test scores as schools have more funding to better focus on these tests. 

The analysis in this project will aim to visualise and answer these two problem statements.

---

### Datasets

#### Provided Data

These are the 5 datasets used in the analysis. The include ACT and SAT participation rates and scores by state in 2017 and 2018, and elementary and secondary education budger per capita by state in 2016 and 2017. 

For the budget data, we are using data from the preceding year because we want to study the impact of that budget on test results in the ensuing year. For example, a budget for FY 2016 will be evaluated against test results in 2017.

* [`act_2017.csv`](./data/act_2017.csv): 2017 ACT Scores by State
* [`act_2018.csv`](./data/act_2018.csv): 2018 ACT Scores by State
* [`sat_2017.csv`](./data/sat_2017.csv): 2017 SAT Scores by State
* [`sat_2018.csv`](./data/sat_2018.csv): 2018 SAT Scores by State
* [`budget_2016_2017.csv`](./data/budget_2016_2017.csv): 2016 and 2017 Elementary and Secondary Education Budget Per Capita by State

#### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**state**|*string*|combined_everything|All 50 states in USA + D.C.|
|**sat_2017_participation**|*float*|combined_everything|SAT participation rates measured as a percentage of high school seniors who graduated in that state in 2017|
|**sat_2018_participation**|*float*|combined_everything|SAT participation rates measured as a percentage of high school seniors who graduated in that state in 2018|
|**act_2017_participation**|*float*|combined_everything|ACT participation rates measured as a percentage of high school seniors who graduated in that state in 2017|
|**act_2018_participation**|*float*|combined_everything|ACT participation rates measured as a percentage of high school seniors who graduated in that state in 2018|
|**sat_2017_ebrw**|*integer*|combined_everything|SAT average Evidence-Based Reading and Writing score of that state in 2017|
|**sat_2017_math**|*integer*|combined_everything|SAT average Math score of that state in 2017|
|**sat_2017_total**|*integer*|combined_everything|SAT average Total (EBRW + Math) score of that state in 2017|
|**act_2017_english**|*float*|combined_everything|ACT average English score of that state in 2017|
|**act_2017_math**|*float*|combined_everything|ACT average Math score of that state in 2017|
|**act_2017_reading**|*float*|combined_everything|ACT average Reading score of that state in 2017|
|**act_2017_science**|*float*|combined_everything|ACT average Science score of that state in 2017|
|**act_2017_composite**|*float*|combined_everything|ACT average Composite (average scores from 4 sections) score of that state in 2017|
|**sat_2018_ebrw**|*integer*|combined_everything|SAT average Evidence-Based Reading and Writing score of that state in 2017|
|**sat_2018_math**|*integer*|combined_everything|SAT average Math score of that state in 2018|
|**sat_2018_total**|*integer*|combined_everything|SAT average Total (EBRW + Math) score of that state in 2018|
|**act_2018_composite**|*float*|combined_everything|ACT average Composite (average scores from 4 sections) score of that state in 2018|
|**budget_per_capita_2016**|*integer*|combined_everything|USD budget per capita for elementary and secondary schools per state in FY16|
|**budget_per_capita_2017**|*integer*|combined_everything|USD budget per capita for elementary and secondary schools per state in FY17|
|**sat_total_change**|*float*|combined_everything|Change in SAT Total scores from 2017 to 2018|
|**act_composite_change**|*float*|combined_everything|Change in ACT Composite scores from 2017 to 2018|
|**budget_change**|*float*|combined_everything|Change in elementary and secondary education budget by state from 2017 to 2018|

---

### Brief Summary Analysis

The analysis is split into two main parts (1) participation rates and (2) budget, each compared against test scores. I have shaped two hypotheses to test:
   1. Increasing participation rates will not result in a fall in SAT/ACT scores
   2. increasing the state's education budgets will not improve test scores

A few key results below:
    - Inverse relationship between SAT and ACT participation rates - students take one test or the other.
    - Negative correlation between participation rates and scores. 
    - Furthermore, an increase in participation rates in from one year to the next will lead to an immediate fall in score.
    - No observable correlation between budget and SAT score, but some positive correlation with ACT scores.
    - A change in budget in the preceding year does not translate to an immediate change in test scores in the next year.

---

### Conclusion

To answer the two hypotheses from the problem statement, we can conlude that:
   1. We can reject our first hypothesis - in fact, there is an observable negative correlation thatt increaseing participation rates will lower test scores for both SAT and ACT.
   2. We cannot definitively reject our second hypothesis because there are no clear trends to indicate that increasing the budget will improve test scores. Further investigations is required to validate this.

---


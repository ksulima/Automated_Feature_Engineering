## Introduction

In this project my goal is to apply automated feature engineering. The idea is to understand this approach to shorten a time spent on this step, which usually takes substantial part of overall time in real-life project. For this purpose I used library [Featuretools](https://www.featuretools.com/) and went through code available in official repository.      
The other goal is to overcome very common problem of limited local machine computation power. To do that, I use [Dask](http://dask.pydata.org/en/latest/docs.html) to parallel tasks and optimize usuage of my local CPU and memory. In other places, I run my calculation on AWS EC2. I use t2.2xlarge instance (8 vCPUs and 32 Memory(GiB)) with Deep Learning AMI (Ubuntu). 

As a model to train, I used implementation of Gradient boosting [xgboost](https://xgboost.readthedocs.io/en/latest/index.html).

## Dataset
Dataset is from Kaggle competition Home Credit Default Risk. 
It includes 7 relational tables, some of them with over 13 mln rows or 120 columns. Tables contain data with e.g. credit cards balances, transaction history, payments etc. It is extensive enough to meet problems I plan to resolve.

More information about dataset can be found [here](https://www.kaggle.com/c/home-credit-default-risk). 

### Steps:
- EDA - general look at data to explore basic information about dataset. `EDA.ipynb`
- Feature engineering - generate features definitions in a automated way with an open-source library [Featuretools](https://www.featuretools.com/). `automated_feature_engineering.ipynb`
- Computation - partiotioning of data and computation with [Dask](http://dask.pydata.org/en/latest/docs.html) `parallel_computation_dask.ipynb`
- Feature selection `feature_selection.ipynb`
- Hyperparameters optimalization for xgboost model with random search. `xgb_random_search.ipynb`
- Hyperparameters tunning and evaluation. `xqb_params_optimalization.ipynb`

## Conclusion

Library Featuretools allowed me to handle data from seven relatonal tables and very efficiently create set of 1.8k features. I could much faster take next steps in project (i.e. feature selection, hyperparameter optimalization,tunning) and receive preliminary results.
I haven't performed traditional manual feature engineering therefore I cannot directly compare two methods, but I estimate, that with this approach time to first evaluation shorten about 5x times. Although automated engineering probably will not completely eliminate necessity of manual time-consuming feature engineering, it let you quickly measure potential of some approach and start iterative process of building final solution.

In addition I parallelized computations with Dask to speed up computation on my local computer.




<img src="/images/fit_time_test_score.png" width="550">

<img src="/images/auc.png" width="550">

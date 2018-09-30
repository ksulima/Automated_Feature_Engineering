## Introduction

In this project my goal is to apply automated approach to feature engineering. The idea is to find out a way to shorten a time spent on this step, which usually takes substantial part of overall time in real-life project. For this purpose I test library [Featuretools](https://www.featuretools.com/).      
The other goal is to overcome very common problem of limited local machine computation power. To do that, I use [Dask](http://dask.pydata.org/en/latest/docs.html) to parallel tasks and optimize usuage of my local CPU and memory. In other places, I run my calculation on AWS EC2. I use t2.2xlarge instance (8 vCPUs and 32 Memory(GiB)) with Deep Learning AMI (Ubuntu). 

As a model to train, I used implementation of Gradient boosting [xgboost](https://xgboost.readthedocs.io/en/latest/index.html).

## Dataset
I decided on dataset from Kaggle competition Home Credit Default Risk. 
It includes 7 relational tables, some of them with over 13 mln rows or 120 columns. Tables contain data with e.g. credit cards balances, transaction history, payments etc. It is extensive enough to meet problems I plan to resolve.

More information about dataset can be found [here](https://www.kaggle.com/c/home-credit-default-risk). 

### Steps:
- [EDA](Automated_Feature_Engineering/blob/master/notebooks/EDA.ipynb) - general look at data to explore basic information about dataset.
- Feature engineering - generate features definitions in a automated way with an open-source library [Featuretools](https://www.featuretools.com/). 
- Computation - partiotioning of data and computation with [Dask](http://dask.pydata.org/en/latest/docs.html)
- Feature selection
- Hyperparameters optimalization with random search.
- Hyperparameters tunning.

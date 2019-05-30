# MTSDataModel

MTSDataModel is a Python class that stores and manipulates economic multivariate time series data. Essentially it works as a wrapper on pandas library; it the core of MTSDataModel instanceobject is a pandas data frame that stores the data. Several data manipulation actions can be performed on the data frame.

## Installation

Using pre-existing Anaconda installation, we set up a new conda enviroment for MTSDataModel. See tested versions of Anaconda, conda and Python in release notes. See requirements.txt for packages and their versions that will be installed.

```
conda config --append envs_dirs my_custom_path
conda create my_env python=3.6.7
conda activate my_env
cd path/to/MTSDataModel
conda install -y --file requirements.txt

# Open Python instance, install needed R packages via rpy2
# This still needs to be automated
from rpy2.robjects.packages import importr
utils = importr('utils')
utils.install_packages('wavelets')
```

## Loading data into data model

Data is read in from a .csv file. This file needs to be in long format and contain following columns:
 - date column (string)
 - level 1 name column  for variable/feature, e.g. GDP (string)
 - level 2 name column for entity, e.g. country (string)
 - value column (numeric).

It is assumed for the input data that
 - each individual time series does not contain breaks
 - NAs can be present at start and end of individual time series. 

MTSDataModel initilizes to a data frame with two-leveled multi-index columns. First level is meant to represent variable names. Second level is meant to represent entity level (e.g. country, company etc.).

## Data manipulations

Several data manipulation operation can be performed on the initialized data frame within MTSDataModel object. These operations can be performed on different variables and/or entities.

### Data pre-processing

Methods available for pre-processing of data are
 - DeflateVariables()
 - DetrendVariables()

### Feature engineering

Methods available for pre-processing of data are
 - MRADecomposition()
 - SumVariables()
 - ReduceVariableDimension()


Remaining useful life (RUL) prediction is the study of predicting when something is going to fail, given its present state. The problem has a prophetic charm associated with it. While a soothsayer can make a prediction about almost anything (including RUL of a machine) confidently, many people will not accept the prediction because of its lack of scientific basis. Here, we will try to solve the problem with scientific reasoning. 

A component (or a machine) is said to have failed when it can no longer perform its desired task to the satisfaction of the user. For example, Li-Ion battery of an electric vehicle is said to have failed when it requires frequent recharging to travel a small distance. Similarly, a bearing of a machine is said to have failed, if level of vibration produced at the bearing goes above some acceptable limit. Other examples can be thought of for different applications. The goal then is to predict beforehand when something is going to fail. Knowledge of a component's expected time of failure will help us prepare well for the inevitable. In industrial setting, where any unplanned shutdown of a critical component has huge monetary cost, knowing when a machine is going to fail will result in significant monetary gains. 

There are many techniques developed over the years to predict RUL of a component. All those techniques can be broadly divided into two categories.

* Model Based Methods
* Data-Driven Methods

In model based methods, we try to formulate a mathematical model of the system under consideration. Then using that model we try to predict RUL of the component. Though model based methods are used in some cases, there are many other applications where formulating a full mathematical model of the system is extremely difficult. In some cases, the underlying physics is so complex that we have to make many simplifying assumptions. Whether the simplifying assumptions are justified or not is determined by collecting real data from the machine. Therefore, it requires extensive domain knowledge and thus is a territory of only a select few who can actually do these things.

In contrast, in data-driven methods all information about a machine is gained from the data collected from it. With readily available sensors we can collect huge amounts of data for almost any application. By analyzing that data we can get an idea about the condition of the machine. That will help us in making an informed decision about the RUL of the machine. In this process we make no assumptions about the machine. Increasingly, data-driven methods are getting better at making reliable predictions. As the name of the project suggests, we will only focus on data-driven methods for RUL prediction. The problem of RUL prediction is also know as prognosis in some fields. Some people also call it prognostics. We will only use the term RUL prediction. In the beginning, we will mainly focus on predicting RUL of mechanical components. Later we will explore other application areas.

### Aim of the project

Like my previous project on [fault diagnosis](https://biswajitsahoo1111.github.io/cbm_codes_open/), aim of this project is to produce reproducible results for RUL prediction. RUL prediction is a broad subject that can be applied to many problems such as RUL prediction of Li-Ion batteries, RUL prediction of machinery bearings, RUL prediction of machine tool, etc. We will start with mechanical applications and then gradually move to other applications over time. As our aim is reproducibility, we will use publicly available datasets. Interested readers can download the data and use our code to get exact results as we have obtained. As we will use well known datasets, readers might observe that, in some cases, our results are in fact worse than some reported results elsewhere. Our goal is not to verify someone else's claim. If someone else claims a better result, onus is on them to demonstrate their result. Here, whatever results I have claimed can be reproduced by readers by just running the jupyter notebooks after downloading relevant data.

This is an ongoing project and modifications and additions of new techniques will be done over time. **Python** and **R** are two popular programming languages that are used in machine learning applications. We will use **Python** to demonstrate our results. At a later stage we might add equivalent **R** code. To implement deep learning models, we will use **Tensorflow**.


## Results using [NASA's Turbofan Engine Degradation Dataset](https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-data-repository/#turbofan)

---------------------------------------------------------------

We will first apply classical machine learning methods (so-called shallow learning methods) to obtain results and then apply deep learning based methods. [Dataset description and preprocessing](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_data_description_and_preprocessing.ipynb) steps can be found at [this link](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_data_description_and_preprocessing.ipynb). We will use the same preprocessing steps, with minor changes, in all notebooks. We strongly encourage readers to first go over [data preparation notebook](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_data_description_and_preprocessing.ipynb) before using results notebooks. In the table below, we report Root Mean Square Error (RMSE) values. **Click on the number to view the corresponding notebook**.

**Note on last column of following table**: The last column specifies the degradation model used in the notebooks. There are two common degradation models that are used for this particular turbofan dataset: Linear degradation model and Piecewise linear degradation model. For more details about both, see [this](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_data_description_and_preprocessing.ipynb). When we use piecewise linear degradation model, we have to assume an early RUL value. This is nothing but the value of RUL that is assumed when the component is relatively new. In literature, different people use different early RUL values. In our examples, when we specify an early RUL value, that means that we apply the same early RUL across all 4 datasets. 


|Method|FD001|FD002|FD003|FD004|Degradation Model|
|:-----:|:-----:|:-----:|:------:|:------:|:-----:|
|Gradient Boosting|[19.06](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD001_xgboost_piecewise_linear_degradation_model.ipynb)|[28.97](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD002_xgboost_piecewise_linear_degradation_model.ipynb)|[20.55](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD003_xgboost_piecewise_linear_degradation_model.ipynb)|[29.49](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD004_xgboost_piecewise_linear_degradation_model.ipynb)|Piecewise Linear (Early RUL = 125)|
|Random Forest|[19.15](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD001_random_forest_piecewise_linear_degradation_model.ipynb)|[29.00](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD002_random_forest_piecewise_linear_degradation_model.ipynb)|[20.53](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD003_random_forest_piecewise_linear_degradation_model.ipynb)|[29.75](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD004_random_forest_piecewise_linear_degradation_model.ipynb)|Piecewise Linear (Early RUL = 125)|
|Gradient Boosting|[33.24](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD001_xgboost_linear_degradation_model.ipynb)<sup>* </sup>|[29.88](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD002_xgboost_linear_degradation_model.ipynb)|[47.94](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD003_xgboost_linear_degradation_model.ipynb)<sup>* </sup>|[40.34](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD004_xgboost_linear_degradation_model.ipynb)<sup>*</sup>|Linear|



<sup>*</sup>See the notebook to get a complete picture.

## Enter Deep Learning

------------------------------

In this section, we will apply deep learning to predict RUL of Turbofan dataset. Due to the nondeterministic nature of operations used in deep learning and dependence of libraries like `Tensorflow` on computer architecture, readers might obtain slightly different results than those in the notebooks. For reproducibility of our results, we also share the saved models of each notebook. All saved models for Turbofan dataset can be found at this [link](https://github.com/biswajitsahoo1111/rul_codes_open/tree/master/saved_models/cmapss). A notebook describing the steps to use the saved models can be found [here](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_using_saved_model_deep_learning.ipynb).


|Method|FD001|FD002|FD003|FD004|Degradation Model|
|:-----:|:-----:|:-----:|:------:|:------:|:-----:|
|1D CNN|[15.77](https://github.com/biswajitsahoo1111/rul_codes_open/blob/master/notebooks/cmapss_notebooks/CMAPSS_FD001_1D_CNN_piecewise_linear_degradation_model.ipynb)|-|-|-|Piecewise Linear (Early RUL = 125)|

(This table will be updated gradually.)

### Why have I used only Jupyter notebooks?

These notebooks are for educational purposes only. Our experiments are relatively small scale and can be run in a reasonable amount of time in a notebook. I personally love the interactive nature of jupyter notebooks. We can see what we are doing. So the answer to the above question is: personal choice. I also don't intend to deploy these, at least for the time being, in a production environment. Readers who wish to build deployment ready systems should bear in mind that they have to do many other things than just run an algorithm in a jupyter notebook.

## Some other related stuff

-------------------------------------

1. [Data-Driven Fault Diagnosis](https://biswajitsahoo1111.github.io/cbm_codes_open/)

2. [Fault diagnosis of machines (A non-technical introduction)](https://biswajitsahoo1111.github.io/post/fault-diagnosis-of-machines/)

3. [Blog articles by yours truly](https://biswajitsahoo1111.github.io/categories/blog/)

--------------------------------------

For attribution, cite this project as
```
BibTeX citation
@misc{sahoo2018datadrivenrul,
  author = {Sahoo, Biswajit},
  title = {Data-Driven Remaining Useful Life (RUL) Prediction},
  url = {https://biswajitsahoo1111.github.io/rul_codes_open/},
  year = {2018}
}
```
Readers should cite original datasets separately.

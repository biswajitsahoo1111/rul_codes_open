# Frequently asked Questions (FAQs)
* [Why are there only Jupyter Notebooks in this repository?](#why-are-there-only-jupyter-notebooks-in-this-repository)
* [How to preprocess data for a different RUL prediction problem?](#how-to-preprocess-data-for-a-different-rul-prediction-problem)
* [Why is the degradation curve linear for CMAPSS dataset? Can a nonlinear degradation curve be used?](#why-is-the-degradation-curve-linear-for-cmapss-dataset-can-a-nonlinear-degradation-curve-be-used)
* [My question is not listed in the FAQs. How can I ask it?](#my-question-is-not-listed-in-the-faqs-how-can-i-ask-it)



## Why are there only Jupyter Notebooks in this repository?

Jupyter notebooks offer a great way to interactively code and see instantly as to what we are doing. The author loves jupyter notebooks hence the choice. These notebooks are for educational purposes only. Our experiments are relatively small scale and can be run in a reasonable amount of time in a notebook. However, readers who wish to build deployment ready systems should bear in mind that they have to do many other things than just run an algorithm in a jupyter notebook.

## How to preprocess data for a different RUL prediction problem?

Data preprocessing methods are problem specific and depends on how data are stored. The data preprocessing method used in this project may not work for your dataset. There is no universal data preprocessing method that would work for all RUL prediction problems. So, depending on the data format and problem definition, you may have to use your own data preprocessing method. That might be a modified version of the code used in this project or completely different. 

## Why is the degradation curve linear for CMAPSS dataset? Can a nonlinear degradation curve be used?

RUL Degradation curves need not always be linear. In different applications, nonlinear degradation curves are in fact used. For the turbofan engine degradation dataset (CMAPSS), it so happens that linear degradation curve is the most natural choice. Readers who have some familiarity with the dataset would know that the degradation is measured by remaining flight cycles. So, for example, if the current RUL now is 192, after one flight cycle, it would be 191. After another flight cycle, it would be 190, and so on. That way it would gradually decrease to zero. So the degradation curve naturally becomes linear. As a slight variation (or some sort of hack to improve prediction accuracy), a piecewise linear degradation curve is also used in practice. In piecewise linear degradation, any RUL value above a number (say, 125) is considered too high. So all the RUL values above 125 are replaced by 125. Once one reaches RUL value of 125, then it linearly degrades to 0. So to sum up, for the turbofan dataset (CMAPSS), linear degradation curve is a natural choice. But for other cases it might indeed be nonlinear.
## My question is not listed in the FAQs. How can I ask it?

Please ask your questions in the comments section below. Otherwise (if you don't want your questions to be made public), you can privately email your questions to the [author](https://biswajitsahoo1111.github.io/) directly.
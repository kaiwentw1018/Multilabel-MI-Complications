# Multi-label Neural Model for Prediction of Myocardial Infarction Complications with Resampling and Explainability
This repository is the official implementation of [Multi-label Neural Model for Prediction of Myocardial Infarction Complications with Resampling and Explainability]. 

The figure below shows the pipeline system that summarizes the whole predictive modeling process: 
<p align="center">
<img src="Pipeline.PNG" width="700">
</p>

## Data Processing
This [notebook]() documents how the dataset was processed as delineated in the paper, which incudes the following sections: 
* Remove features with significant missingness (>25%)
* Feature selection
* Data imputation (with MICE, PMM, Mean/Mode, regression, kNN and evaluated with NRMSE)
* Splitting the dataset into test/train subsets
* Outcome label space reconstruction

## Training
The following multi-label models were trained and the results evaluated:  
* Neural Network (NN)
* Random k-labelsets (RAKEL): RakelD, RakelO
* Multi-Label Support Vector Machines (MLTSVM)
* Label powerset [(LP)](https://github.com/kaiwentw1018/Multilabel-MI-Complications/blob/main/Training/LP.ipynb)
* Majority voting (MV)
* Binary relevance k-nearest neighbor (BRkNN): BRkNNa, BRkNNb
* Binary relevance (BR)
* Classifier chains (CC)
* Multi-label k-Nearest Neighbours (MlkNN)
* Multi-output classifier [(MOC)](https://github.com/kaiwentw1018/Multilabel-MI-Complications/blob/main/Training/MOC.ipynb)
* Multi-label fuzzy adaptive resonance associative map [(MLARAM)](https://github.com/kaiwentw1018/Multilabel-MI-Complications/blob/main/Training/MLARAM.ipynb)
* Label space partition ensemble classifier (LSPEC)


## Results
Our models achieve the following performances:
<p align="center">
<img src="Results/Results.png" width="400">
</p>

### Shapley Analysis 
Take "lethal outcome" as an example, the beeswarm plot below provides an overview of the impact of the features on the prediction, with each dot representing the Shapley value of every feature for all samples. The pink dots of positive Shapley values indicate that the higher values of the said feature pushes the model to a positive prediction, whereas the those of negative Shapley values push the prediction in the opposite direction. The duration of arterial hypertension, time elapsed from the beginning of the attack of CHD to the hospital, and quantity of myocardial infarctions in the anamnesis were observed to be the most important features that lead to a prediction of death while the presence of an anterior myocardial infarction pushes the model to a negative prediction. 

<p align="center">
<img src="Results/LethalOutcomeShap.png" width="600">
</p>

The figure below shows the average absolute of the Shapley values over the whole testing dataset for all five prediction outcomes. The duration of arterial hypertension, exertional angina pectoris in the anamnesis, and presence of an anterior/inferior infarction were observed to be the most important features for all five outcomes. 
<p align="center">
<img src="Results/OverallShap.png" width="600">
</p>

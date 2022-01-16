# Multi-label Neural Model for Prediction of Myocardial Infarction Complications with Resampling and Explainability
This repository is the official implementation of [Multi-label Neural Model for Prediction of Myocardial Infarction Complications with Resampling and Explainability]. 

## Data Processing
This [notebook]() documents how the dataset was processed as delineated in the paper, which incudes the following sections: 
* Remove features with significant missingness (>25%)
* Feature selection
* Data imputation (with MICE, PMM, Mean/Mode, regression, kNN and evaluated with NRMSE)
* Splitting the dataset into test/train subsets
* Outcome label space reconstruction

## Training


## Evaluation


## Results
Our models achieve the following performances:

### [AMI Prediction Using Processed ECG-ViEW II](https://drive.google.com/drive/folders/1-WcMjYm-jhuvE1vDpW76HkYW-xrOuPQ6?usp=sharing)

### Shapley Analysis 
Take "lethal outcome" as an example, the beeswarm plot below provides an overview of the impact of the features on the prediction, with each dot representing the Shapley value of every feature for all samples. The pink dots of positive Shapley values indicate that the higher values of the said feature pushes the model to a positive prediction, whereas the those of negative Shapley values push the prediction in the opposite direction. The duration of arterial hypertension, time elapsed from the beginning of the attack of CHD to the hospital, and quantity of myocardial infarctions in the anamnesis were observed to be the most important features that lead to a prediction of death while the presence of an anterior myocardial infarction pushes the model to a negative prediction. 

<p align="center">
<img src="Results/LethalOutcomeShap.png" width="600">
</p>

The figure below shows the average absolute of the Shapley values over the whole testing dataset for all five prediction outcomes. The duration of arterial hypertension, exertional angina pectoris in the anamnesis, and presence of an anterior/inferior infarction were observed to be the most important features for all five outcomes. 
<p align="center">
<img src="Results/OverallShap.png" width="600">
</p>

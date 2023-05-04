# radiomics-for-srs-model-interpretability-data-share
Open-source sample labels, observer appearance labels, and predicted probability data associated with the results presented in the manuscript "Assessment of Brain Metastasis Qualitative Appearance Interobserver Variability and Comparison to MRI Radiomics for Stereotactic Radiosurgery Outcome Prediction"


## Data Description

### Root Directory
**Sample Labels.xlsx** - Provides a list of the patient and brain metastasis ID for each brain metastasis (sample) in the study.
Samples are uniquely identified using the patient ID and metastasis ID pair.
For each sample, the ground truth label of it progressed post-SRS is provided.
If the value is "1", the sample is positive, meaning that the brain metastasis progressed post-SRS.
If the sample progressed, the date of progression is provided.
The date of patient death/loss to follow-up is also given for the censorship data needed for Kaplan-Meier analysis.
The SRS dose and fractionation is given for each sample, as required by the RPA model.
The qualitative appearance label assigned to each sample for each of the five observers is also provided.

### A. Radiomic Expert 1 Appearance Experiments
Each file contains the predicted label probabilities from the machine learning model for each sample for all the "Radiomic Expert 1 Appearance Experiments".
The filename describes which appearance label was being predicted, and so what the "positive label" represents.
The filename also describes if the file contains probabilities from the testing datasets or out-of-bag (OOB) samples from the training dataset.
As bootstrapped resampling was performed, each of the 250 iterations had their own results, which are stored in separate sheets within each file.
The training and testing on the entire dataset results needed to calculate the AUC_0.632+ correction are also included in a separate sheet.the testing dataset's samples ("Testing Dataset Results").

### B. Radiomic Consensus Appearance Experiments
These files are structured identically to those from "A. Radiomic Expert 1 Appearance Experiments", except they are from the "Radiomic Consensus Appearance Experiments".

### C. Radiomic Progression Experiment
These files are structured the same as the previous folders, except that since they are for the "Radiomic Progression Experiment", only one label is being predicted, post-SRS progression.
Therefore only two files, one for the testing datasets and one for the OOB datasets are needed.

### D. Radiomic and Clinical Progression Experiment
These files are structured identically to those from "C. Radiomic Progression Experiment", except they are from the "Radiomic and Clinical Progression Experiment".


## Data Usage

With the data shared within this repository, a user would be able to reproduce the full error metric analysis presented in the accompanying manuscript.
For each experiment, the predicted probabilities and ground truths labels for the OOB datasets can be used to construct a receiver operating characteristic (ROC) curve based on the training dataset to choose an optimal operating point.
The predicted probabilities and ground truths labels from the testing dataset can then be used to construct an ROC curve based on the testing dataset.
The area-under-the-ROC-curve (AUC) can be found directly from this ROC curve, and the misclassification rate, false negative rate, and false positive rate can be found using the optimal operating point found using the OOB dataset previously.
The positive label confidences and ground truths labels per iteration for bootstrapped resampled testing datasets can also be used to calculate the corrected AUC_0.632+ value.
The predicted probabilities can also be used directly for use in the RPA models and for comparison across appearance labels by taking the per sample average predicted probability across bootstrapped iterations and then using these values as described in the manuscript and shown in Fig. S2.


## Contact Information
Author: David A. DeVries

Email: ddevrie8@uwo.ca

Organization: Western University/London Health Sciences Centre, London ON CA
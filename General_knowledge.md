# Metrics for measuring the prediction performance
### TP/FP/TN/FN
TP:
FP:
TN:
FN:

### What is the AUC - ROC Curve?
When we need to check or visualize the performance of the multi-class classification problem, we use the AUC (Area Under The Curve) ROC (Receiver Operating Characteristics) curve. It is one of the most important evaluation metrics for checking any classification model’s performance. It is also written as AUROC (Area Under the Receiver Operating Characteristics)

AUC - ROC curve is a performance measurement for the classification problems at various threshold settings. ROC is a probability curve and AUC represents the degree or measure of separability. It tells how much the model is capable of distinguishing between classes. Higher the AUC, the better the model is at predicting 0s as 0s and 1s as 1s. By analogy, the Higher the AUC, the better the model is at distinguishing between patients with the disease and no disease.
The ROC curve is plotted with TPR against the FPR where TPR is on the y-axis and FPR is on the x-axis.

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/ROC.png?raw=true)

Defining terms used in AUC and ROC Curve.
TPR (True Positive Rate) / Recall /Sensitivity

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/TPRrecall.png?raw=true)

Specificity

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/specificity.png?raw=true)

FPR

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/FPR.png?raw=true)

As we know, ROC is a curve of probability. So let's plot the distributions of those probabilities:
Note: Red distribution curve is of the positive class (patients with disease) and the green distribution curve is of the negative class(patients with no disease).

different composition of the AUROC and distribution of TP/TN 

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve.png?raw=true)

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve2.png?raw=true)

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve3.png?raw=true)

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve4.png?raw=true)


### The relation between Sensitivity, Specificity, FPR, and Threshold.

Sensitivity and Specificity are inversely proportional to each other. So when we increase Sensitivity, Specificity decreases, and vice versa.

Sensitivity⬆️, Specificity⬇️ and Sensitivity⬇️, Specificity⬆️

When we decrease the threshold, we get more positive values thus it increases the sensitivity and decreasing the specificity.
Similarly, when we increase the threshold, we get more negative values thus we get higher specificity and lower sensitivity.
As we know FPR is 1 - specificity. So when we increase TPR, FPR also increases and vice versa.

TPR⬆️, FPR⬆️ and TPR⬇️, FPR⬇️


### How to use the AUC ROC curve for the multi-class model?
In a multi-class model, we can plot N number of AUC ROC Curves for N number classes using the One vs ALL methodology. So for example, If you have three classes named X, Y, and Z, you will have one ROC for X classified against Y and Z, another ROC for Y classified against X and Z, and the third one of Z classified against Y and X.

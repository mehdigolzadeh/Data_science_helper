# Metrics for measuring the prediction performance
## model evaluation in Classification
### TP/FP/TN/FN
In binary classification we have two classes: the so-called positive and negative classes. It is useful to talk about classification metrics using the confusion matrix, which we tally after setting a classification threshold for our binary classifier. The confusion matrix has 4 values, corresponding to the 4 combinations of true and predicted classes. Here’s a typical confusion matrix, with TP, FP, FN and TN representing the four combinations:

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/confmatrix.png?raw=true)

Let’s look at a toy example: our data are images of pets, either a dog (🐶), or a cat (🐱). Our classifier detects a pet in each photo, and we would like to measure its performance. 
Here is the confusion matrix of our photo classifier. We have a total of 24 photos, 18+2=20 dog photos, and 3+1=4 cat photos.

### Precision, Recall, and F1-score
The **Precision** is the proportion of true positives out of all detected positives, or simply TP/(TP+FP). 
In our case, dog photos are the positive class, and 18 out of 18+3 photos that were classified as dogs actually contain dogs. The precision is thus 18/21=86%. 

The **recall** is the number of true positives that are correctly classified (TP/(TP+FN)). From the above matrix it is easy to see that there are 20 true positives, and 18 of them are successfully detected. Thus, the recall is 18/(18+2), or 90%.

The **accuracy**: what proportion of photos — both Positive and Negative — were correctly classified? so the general formula for accuracy is (TP+TN)/(TP+TN+FP+FN).

Finally, the **F1-score** is the harmonic mean of the precision and recall. This computes to 88%. Fantastic classifier, right? Hold your horses. Take a look again at the matrix, specifically at the classification of cat photos. Only 1 out of 4 cat photos was successfully detected. Moreover, 2 of the 3 photos classified as cats are actually dogs. So why is the F1-score so high?


**F1-score = 2 × (precision × recall)/(precision + recall)**


Precision and recall ( and by extension, the F1-score, which is a function of the two) consider one class , the positive class, to be the class we are interested in. They use only three of the values in the confusion matrix: TP, FP, and FN. The 4th value — TN — is not used in these metrics. You can put any value in the TN cell —0, 100, infinity — and the precision, recall and F1-score will not change.

To see how the class imbalance affects the accuracy, imagine that now instead of 4 cat photos, we had 100 sets of these 4 photos for a total of 400 photos. Since we use the same classifier, 100 out of 400 of the photos will be correctly classified, and 300 will be misclassified. 

A quick calculation shows that the accuracy is now a much lower (100+18)/(400+20)=28%, because cats are now the majority class. A new class proportion will also influence the precision (but not the recall — check!), and thus the F1-score.

What is more important, precision or recall? This really depends on your specific classification problem. Imagine, for example, that your classifier needs to detect diabetes in human patients. “Positive” means the patient has diabetes. “Negative” means that the patient is healthy. (I know, it’s confusing. But that’s medical lingo!). In this case, you probably want to make sure that your classifier has high recall, so that as many diabetics as possible are correctly detected. Take another example — say you are building a video recommendation system, and your classifier predicts Positive for a relevant video and Negative for non-relevant video. You want to make sure that almost all of the recommended videos are relevant to the user, so you want high precision. Life is full of trade-offs, and that’s also true of classifiers. There’s usually a trade-off between good precision and good recall. You usually can’t have both.


### Macro/Weighted/Micro
The next step is combining the per-class F1-scores into a single number, the classifier’s overall F1-score. There are a few ways of doing that. Let’s begin with the simplest one: an arithmetic mean of the per-class F1-scores. This is called the macro-averaged F1-score, or the macro-F1 for short, and is computed as a simple arithmetic mean of our per-class F1-scores:

**Macro-F1 = (F1-class1 + F1-class2 + F1-class3) / num-class --> Same for Macro-precsision and Macro-recall**

When averaging the macro-F1, we gave equal weights to each class. We don’t have to do that: in weighted-average F1-score, or weighted-F1, we weight the F1-score of each class by the number of samples from that class. In our case, we have a total of 25 samples: 6 Cat, 10 Fish, and 9 Hen. The weighted-F1 score is thus computed as follows:

**Weighted-F1 = (num-class1 × F1-class1 + num-class2 × F1-class2 + num-class3 × F1-class) / num-class1+num-class2+num-class3 --> Same for Macro-precsision and Macro-recall**



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

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve.png?raw=true)![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve1-1.png?raw=true)

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve2.png?raw=true)![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve2-1.png?raw=true)

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve3.png?raw=true)![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve3-1.png?raw=true)

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve4.png?raw=true)![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/roccurve4-1.png?raw=true)


### The relation between Sensitivity, Specificity, FPR, and Threshold.

Sensitivity and Specificity are inversely proportional to each other. So when we increase Sensitivity, Specificity decreases, and vice versa.

Sensitivity⬆️, Specificity⬇️ and Sensitivity⬇️, Specificity⬆️

When we decrease the threshold, we get more positive values thus it increases the sensitivity and decreasing the specificity.
Similarly, when we increase the threshold, we get more negative values thus we get higher specificity and lower sensitivity.
As we know FPR is 1 - specificity. So when we increase TPR, FPR also increases and vice versa.

TPR⬆️, FPR⬆️ and TPR⬇️, FPR⬇️


### How to use the AUC ROC curve for the multi-class model?
In a multi-class model, we can plot N number of AUC ROC Curves for N number classes using the One vs ALL methodology. So for example, If you have three classes named X, Y, and Z, you will have one ROC for X classified against Y and Z, another ROC for Y classified against X and Z, and the third one of Z classified against Y and X.

### Matthews Correlation Coefficient
So far, we’ve seen some issues with the classic metrics: accuracy is sensitive to class imbalance; precision, recall, and F1-score are asymmetric. So what’s one to do? If both classes are of interest, one can treat a binary classification problem as a multi-class problem with 2 classes, and then calculate the corresponding multi-class metrics: micro- or macro-averaged precision, recall, and F1-score. 
For binary classification, there is another (and arguably more elegant) solution: treat the true class and the predicted class as two (binary) variables, and compute their correlation coefficient (in a similar way to computing correlation coefficient between any two variables). The higher the correlation between true and predicted values, the better the prediction. This is the phi-coefficient (φ), rechristened Matthews Correlation Coefficient (MCC) when applied to classifiers. Computing the MCC is not rocket science:

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/mcc.png?raw=true)

Some nice properties of MCC can be easily derived from this formula: when the classifier is perfect (FP = FN = 0) the value of MCC is 1, indicating perfect positive correlation. Conversely, when the classifier always misclassifies (TP = TN = 0), we get a value of -1, representing perfect negative correlation (in this case, you can simply reverse the classifier’s outcome to get the ideal classifier). In fact, MCC value is always between -1 and 1, with 0 meaning that the classifier is no better than a random flip of a fair coin. MCC is also perfectly symmetric, so no class is more important than the other; if you switch the positive and negative, you’ll still get the same value.
MCC takes into account all four values in the confusion matrix, and a high value (close to 1) means that both classes are predicted well, even if one class is disproportionately under- (or over-) represented.

for our example:

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/mccexample.png?raw=true)



## Model evaluation in regression
### R Square/Adjusted R Square

R Square measures how much of variability in dependent variable can be explained by the model. It is square of Correlation Coefficient(R) and that is why it is called R Square.

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/r2.png?raw=true)

R Square is calculated by the sum of squared of prediction error divided by the total sum of square which replace the calculated prediction with mean. R Square value is between 0 to 1 and bigger value indicates a better fit between prediction and actual value.

R Square is a good measure to determine how well the model fits the dependent variables. However, it does not take into consideration of overfitting problem. If your regression model has many independent variables, because the model is too complicated, it may fit very well to the training data but performs badly for testing data. That is why Adjusted R Square is introduced because it will penalise additional independent variables added to the model and adjust the metric to prevent overfitting issue.(sklearn)[https://scikit-learn.org/stable/modules/generated/sklearn.metrics.r2_score.html]


### Mean Square Error(MSE)/Root Mean Square Error(RMSE)

While R Square is a relative measure of how well the model fits dependent variables, Mean Square Error is an absolute measure of the goodness for the fit.

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/MSE.png?raw=true)

MSE is calculated by the sum of square of prediction error which is real output minus predicted output and then divide by the number of data points. It gives you an absolute number on how much your predicted results deviate from the actual number. You cannot interpret much insights from one single result but it gives you an real number to compare against other model results and help you select the best regression model.
Root Mean Square Error(RMSE) is the square root of MSE. It is used more commonly than MSE because firstly sometimes MSE value can be too big to compare easily. Secondly, MSE is calculated by the square of error, and thus square root brings it back to the same level of prediction error and make it easier for interpretation.

"""
from sklearn.metrics import mean_squared_error
import math
print(mean_squared_error(Y_test, Y_predicted))
print(math.sqrt(mean_squared_error(Y_test, Y_predicted)))
MSE: 2017904593.23
RMSE: 44921.092965684235
"""

### Mean Absolute Error(MAE)

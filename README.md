## Title: Predicting Corporate Failure in Times of Crisis

<br clear="both">

<div align="center">
  <img height="300" width="100%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/Financial_Crisis.jpg" />
</div>

### 1. Background and Scope

This project is an extension of the initial project where I predicted the bankruptcy of JSE companies using Machine Learning models (you can find the initial project [here](https://github.com/GodfreyElia/Bankruptcy-Prediction-Using-Machine-Learning/tree/main)).

I believe that the practical utility of bankruptcy prediction models lies in their ability to predict failure when it matters the most - in times of crises. Most corporate failure analysts and researchers hypothesise that times of crises negatively impact the performance of predictive models as company failure in these times is often unexpected and sudden. This means that during crises, companies may file for bankruptcy without showing indications of previous financial distress. Thus, using back-testing (modeling based on historical data), predictive models may easily misclassify candidates of bankruptcy for nonbankruptcy.

#### Scope

This project endeavours to compare how the 8 models covered in the [previous project](https://github.com/GodfreyElia/Bankruptcy-Prediction-Using-Machine-Learning/tree/main) fared when predicting failure in times of crises. I identified two crisis periods: the 2008 global credit crisis and the recent global health pandemic (Covid-19). Owing to the generous dataset which span 512 JSE companies from 1997 until 2022, I could easily isolate companies that failed around the crisis periods. 2007 – 2009 was the reference timeframe for the credit crisis (financial crisis as is now popularly known in literature) while 2019 – 2021 was selected as the reference point for the Covid-19 pandemic. Furthermore, the bankrupt companies were strictly all the companies that filed for bankruptcy during the selected crises periods, however, the nonbankrupt companies were all firms from the same period and a few randomly selected firms from the dataset to maintain balance.

<br clear="both">

<div align="Left">
  <img height="60%" width="75%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/GFC.png"  />
</div>
<br>
 Fig 1a. 2008 Global financial crisis data balance
<br>
<br clear="both">

<div align="Left">
  <img height="60%" width="75%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/Covid-19%20Data%20Balance.png"  />
</div>
<br>
  Fig 1b. 2008 Global financial crisis data balance

### 2. Findings and Discussion

#### 2.1. Accuracy
<br clear="both">

<div align="Left">
  <img height="60%" width="75%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/Accuracy.png"  />
</div>
<br>

Figure 2 compares the accuracy of the 7 models used in this paper to predict bankruptcy of JSE companies one year prior to failure. The vertical axis reports the accuracy of the models in percentage, while the horizontal axis reports the type of model used.
<br>
<br>
A quick glance at the accuracies of the models reveals a decrease in the performance of all the models during the Covid-19 pandemic (with the exception of the logit and the SVM classifiers) relative to their performance during non-crisis periods. On the other hand, with exception of Random Forest, Boosting, and Logistic Regression, the rest of the models underperformed their non-crisis period thresholds. On average, the accuracy of the models have decreased by over 3% during the COVID-19 pandemic and only 1% during the credit crisis. This finding agrees with scholars who assert that crisis periods weaken the predictive strengths of classifiers by introducing sudden bankruptcies into the dataset.

Other key observations include that the Random Forest, Boosting, and SVM models are the most consistent classifiers, either outperforming or closely trailing their non-crisis period performance. Furthermore, there is a notable decline in the performance of the bagging model, and a sharp rise in performance of the logit classfier during the crises. The reason for this contradiction is that the bagging model is a nonlinear classifier and so its predictive accuracy is period dependent, meanwhile, the logi model is linear and thus is resilient to business cycles and crises. 

Finally, I observe an anomally in the predictive power of the kNN model. The expectation for the kNN model was that its performance would increase owing to the small dataset that was used to train and test the data. This is largely because the kNN does not predict perse, but instead "memorises" the data and classifies the test data based on its memory.

#### 2.2. Type 1 Error
<br clear="both">

<div align="Left">
  <img height="60%" width="75%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/Type%201%20Error.png"  />
</div>
<br>
Figure 3 compares the type 1 errors of the 7 models used in this paper to predict bankruptcy of JSE companies one year prior to event during two global crisis periods. The vertical axis reports the false positive rate of the models in percentage, while the horizontal axis reports the type of model used.
<br>
<br>
To begin with, type 1 error (false positive rate) measures the proportion of negative cases (bankrupt companies in this occasion) that were wrongly classified as positive (non-bankrupt). We observe that the ensemble models had a superior ability to correctly classify bankrupt companies during Covid-19 pandemic, with a false positive rate of less than 3% on average which was below their non-crisis period. This was also the case for the SVM and Logit classifiers. Meanwhile, the kNN and ANN models experienced difficulty in classifying bankrupt companies during the same period. However, except for the SVM model, the rest of the models experienced type 1 errors that were above their non-crisis periods. On the average, the misclassification rate of the bankruptcy companies rose by 9% from non-crisis period during Covid-19.
<br>
<br>
Finally, it is interesting to notice that the SVM and the Bagging model did show a somewhat overt propensity to predict companies as bankrupt especially in the credit crisis period. This can be seen by observing the type II errors of the models given in the table below. By simply looking that panel B type 2 errors, we can quickly observe that the two models respectively predicted 19% and 25% of the non-bankrupt companies 
as bankrupt, which could as explain the higher true negative rate.

<br clear="both">

<div align="Left">
  <img height="60%" width="75%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/Overall-metrics.png"  />
</div>
<br>

Figure 4 shows a summary for the metrics used to assess the models.

#### 2.3. Receiver Operating Characteristics (ROC)

<br clear="both">

<div align="Left">
  <img height="60%" width="75%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/COVID-19.png"  />
</div>
<br>
Fig. 5a: ROC during Covid-19
<br>
<br clear="both">

<div align="Left">
  <img height="60%" width="75%" src="https://github.com/GodfreyElia/Modeling-Crises/blob/main/File/GFC-ROC.png"  />
</div>
<br>
Fig. 5b ROC during GFC-2008
<br>
<br>
By observing the ROCs of the models in the two periods, we observe strong predictive strengths among all ensemble models and base learners with the overall lowest predictive strength coming from the Logistic regression model. This appears counterintuitive as the Logit model indicated superior accuracies in both periods. Thus, judging solely based on the ROC for which model to use during crises may prove to be difficult.

#### 3. Conclusion

Based on the above findings, it is safe to conclude that the Covid-19 pandemic had a slightly larger impact on the predictive models compared to the the credit crises. This can be seen in larger decline in accuracies of the models and the increase in type 1 errors in the models in the Covid-19 period compared to the credit crises.

Furthermore, I believe any choice of these four models (and indeed, the average prediction of these four models) would be ideal to use in times of crises: Random forest, Boosting, SVM, and Logistic regression.

----
### Thank you tonnes for reading this project!

Visit [here](https://github.com/GodfreyElia) for more projects.


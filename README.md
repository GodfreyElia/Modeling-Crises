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

Figure 2 compares the accuracy of the eight models used in this paper to predict bankruptcy of JSE companies one year prior to failure. The vertical axis reports the accuracy of the models in percentage, while the horizontal axis reports the type of model used.
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


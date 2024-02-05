
# Algorithmic Trading

This jupyter notebook is application of machine learning techniques to optimize trading algorithms. It began with importing essential libraries for data manipulation, statistical calculations and machine learning modeling implementation.


## Base Line Trading Model
In the first part of programing, a baseline performance for trading algorithm is established by applying simple moving average (SMA). To calculate startegy return we generated signals by comparing the actual returns of provided data set.Trading algorithm have been automated using two machine learning techniques i.e. Support Vector Machine (SVM) and Logistic Regression Model (LRM) based upon the staregy returns and actual returns.

* Strategy returns under SVM are perfoming better than actual results. Recall is high for buying but is not reflecting sufficient score for selling portfolio.

* Strategy returns generated via LRM are more fluctuating than SVM particularly by the end of 2021 when the actual returns are increasing, our startegy returns are going downwards.

##### Summary 
Effectivess of trading stategy and peformance of automated models through their cumulative retun plots and classification reports generated by the models reflects that SVM model performs a bit better than the LRM model since it has a higher accuracy score. Further more, startegy returns are exceeding the actual returns. However, the LRM model does a better job predicting profitable short opportunities, as evidenced by its higher recall score on the `-1.0` class in contrast to SVM. 

|SVM Base Line                                                | LRM Base Line                      |
| -----------------------------------                         | ----------------------------------- |
| ![image_1](SVM_BaseLine.png)                                | ![image_2](LRM_BaseLine.png) |


|SVM Base Line                                                | LRM Base Line  
| -----------------------------------                         | ----------------------------------- |
| ![image_3](svm.png)                                         | ![image_2](lrm.png) |


## Tunning The Model:

In this part, model's input features are tuned to identify the optimal parameters that yields the most favorable trading solution. The optimal parameters are selected based upon the comparison of cumulative products of the startegy returns and classification reports of models.


### Alternate 1 (Adjusting Size of Training Data)

* Tune the Model's training period from 3 Months to 6 Months while keeping the SMA windows unchanged.

As compared with original training period of three months, change in period to six months decreased the startegy returns for testing data.

  * From 2016-2019: Strategy return was consistent with Actual returns.
  * From 2019-2020: Actual returns exceeded startegy returns.
  * From 2020-2021 :Startegy return is performing better than actual results.

* Classification Report:
  * Model's accuracy score is 56%. 
  * Buying : It shows very high recall peformance of 98% while precision is moderate (56%).
  * Selling: Model's precision score is only 44% while recall is .02.

### Alternate 2 (Adjusting the SMA Window and Training period)
* Tune the trading algorithm by adjusting the SMA short term window and training period'.

   * Adjusted Short Term Window : 20
   * Adjusted Long Term Window: 100
   * Traing period : 9 Months
   
Altough these parameteres resulted poor Strategy Returns than actual returns under SVM. Ironically, with these parameters,  logistic Regression Model generated opposite results and startegy returns exceeded actual returns. 
 
* Classification Report:
  * Model's accuracy score is 55%. 
  * Buying : It shows  high recall of 90% while precision is moderate (56%).
  * Selling: Model's precision score is only 44% while recall increased to 11%.



###  Alternate 3 (Fine Tuned Model)

 * Adjusted Short Term Window : 7
 * Adjusted Long Term Window: 50
 * Traing period : 3 Months
 
 |SVM Fine Tuned                                                   | LRM Fine Tuned                    |
 | -----------------------------------                             | ----------------------------------- |
 | ![image_5](SVM_Tuned.png)                                       | ![image_6](LRM_Tuned.png) |

 |SVM Fine Tuned                                                   | LRM Fine Tuned                    |
 | -----------------------------------                             | ----------------------------------- |
 | ![image_7](svm1.png)                                            | ![image_8](lrm1.png) |
 

## Conclusion:

Our trading stategy is a simple cross over strategy where computer generated the signals to buy or sell the based upon actual results. Model will buy the stock when actual return is greater than 0 and vice versa. After doing the quick analysis and based upon the limited information, it can be concluded that smaller windows of time are more sensitive to changes in the price data due to the fewer number of data points, and larger time periods are less sensitive to daily changes. With the provided data set, the proposed machine learning models with longer SMA windows seemed to introduce overfitting in the models. SVM models with three months training data and short to medium SMA window is more smoother in startegy returns while LRM is more efficient in showing the categorical performance. The SVM closely resembles the actual returns which perfectly makes sense as it takes into consideration more recent changes. In contrast, the LRM has comparatively more lag and loosely resembles the actual return curve. Ultimately, which model is best may depend on which class we care most about predicting, as well as which has better overall economic returns compared to a long-only investment.

 
 




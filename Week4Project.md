---
title: "Untitled"
author: "Ken Gu"
date: "2017年3月12日"
output: html_document
---
The goal of this report is to predicting manner(class) based on the other variables
First: Model build strategy (how I built my model)
1.1 to select  Classification Trees/ bagging / s latent Dirichlet allocation (LDA) models
1.2 Before execute the prediction function, I use dplyr to read/clean the data

Second: (how I used cross validation)
2.1 Split the training set to 'train' and 'testing' set based on 70% and 30% 

Third: (what you think the expected out of sample error)
3.1 I use all 3 models to predict on the testing set to get the accuracy result

Fourth: (why I make choice on selection model)
4.1 I select the model with the highest accuracy on the testing test.







```
## Confusion Matrix and Statistics
## 
##           Reference
## Prediction    A    B    C    D    E
##          A 1296  228  279  238   95
##          B   55  419   52  194  212
##          C  156  262  620  171  216
##          D  165  230   75  361  211
##          E    2    0    0    0  348
## 
## Overall Statistics
##                                           
##                Accuracy : 0.5172          
##                  95% CI : (0.5044, 0.5301)
##     No Information Rate : 0.2845          
##     P-Value [Acc > NIR] : < 2.2e-16       
##                                           
##                   Kappa : 0.3842          
##  Mcnemar's Test P-Value : < 2.2e-16       
## 
## Statistics by Class:
## 
##                      Class: A Class: B Class: C Class: D Class: E
## Sensitivity            0.7742   0.3679   0.6043  0.37448  0.32163
## Specificity            0.8005   0.8919   0.8343  0.86161  0.99958
## Pos Pred Value         0.6067   0.4496   0.4351  0.34645  0.99429
## Neg Pred Value         0.8992   0.8546   0.9090  0.87549  0.86739
## Prevalence             0.2845   0.1935   0.1743  0.16381  0.18386
## Detection Rate         0.2202   0.0712   0.1054  0.06134  0.05913
## Detection Prevalence   0.3630   0.1584   0.2421  0.17706  0.05947
## Balanced Accuracy      0.7874   0.6299   0.7193  0.61805  0.66061
```

```
## Confusion Matrix and Statistics
## 
##           Reference
## Prediction    A    B    C    D    E
##          A 1650   21    3    4    0
##          B    6 1107   20    3    4
##          C    3    9  999   40    3
##          D   14    1    4  912    3
##          E    1    1    0    5 1072
## 
## Overall Statistics
##                                           
##                Accuracy : 0.9754          
##                  95% CI : (0.9711, 0.9792)
##     No Information Rate : 0.2845          
##     P-Value [Acc > NIR] : < 2.2e-16       
##                                           
##                   Kappa : 0.9688          
##  Mcnemar's Test P-Value : 3.418e-08       
## 
## Statistics by Class:
## 
##                      Class: A Class: B Class: C Class: D Class: E
## Sensitivity            0.9857   0.9719   0.9737   0.9461   0.9908
## Specificity            0.9934   0.9930   0.9887   0.9955   0.9985
## Pos Pred Value         0.9833   0.9711   0.9478   0.9764   0.9935
## Neg Pred Value         0.9943   0.9933   0.9944   0.9895   0.9979
## Prevalence             0.2845   0.1935   0.1743   0.1638   0.1839
## Detection Rate         0.2804   0.1881   0.1698   0.1550   0.1822
## Detection Prevalence   0.2851   0.1937   0.1791   0.1587   0.1833
## Balanced Accuracy      0.9895   0.9825   0.9812   0.9708   0.9947
```

```
## Confusion Matrix and Statistics
## 
##           Reference
## Prediction    A    B    C    D    E
##          A 1275  204  190   67   58
##          B   64  696   78   90  191
##          C  166  119  637  123   80
##          D  152   49  104  595  152
##          E   17   71   17   89  601
## 
## Overall Statistics
##                                          
##                Accuracy : 0.6464         
##                  95% CI : (0.634, 0.6586)
##     No Information Rate : 0.2845         
##     P-Value [Acc > NIR] : < 2.2e-16      
##                                          
##                   Kappa : 0.5518         
##  Mcnemar's Test P-Value : < 2.2e-16      
## 
## Statistics by Class:
## 
##                      Class: A Class: B Class: C Class: D Class: E
## Sensitivity            0.7616   0.6111   0.6209   0.6172   0.5555
## Specificity            0.8768   0.9109   0.8996   0.9071   0.9596
## Pos Pred Value         0.7107   0.6220   0.5662   0.5656   0.7560
## Neg Pred Value         0.9025   0.9070   0.9183   0.9236   0.9055
## Prevalence             0.2845   0.1935   0.1743   0.1638   0.1839
## Detection Rate         0.2167   0.1183   0.1082   0.1011   0.1021
## Detection Prevalence   0.3048   0.1901   0.1912   0.1788   0.1351
## Balanced Accuracy      0.8192   0.7610   0.7602   0.7622   0.7575
```

```
# After comparision, select model 2, as it has the highest accuracy

# Step 5: Predict 20 different test cases


```r
predFinal <- predict(modelFit2, datacleantest)
```



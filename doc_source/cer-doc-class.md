# Custom Classifier Metrics<a name="cer-doc-class"></a>

Amazon Comprehend provides you with metrics to help you estimate how well a custom classifier should work for your job\. They are based on training the classifier model, and so while they accurately represent the performance of the model during training, they are only an approximation of the API performance during classification\. 

Metrics are included any time metadata from a trained custom classifier is returned\. 

**Note**  
Please refer to [Metrics: Precision, Recall, and FScore](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_fscore_support.html) for an understanding of the underlying Precision, Recall, and F1 score metrics\. These metrics are defined at a class level\. We have used **macro** averaging for combining these metrics together to come up with the test set P,R,F1, as discussed below\.

We support the following metrics: 
+ **Accuracy**
+ **Macro Precision**
+ **Macro Recall**
+ **Macro F1 Score**

**Accuracy**

Accuracy is reported at the corpus level\. This indicates that it indicates the percentage of labels from the test data that are predicted exactly right by the model\. This is also called *micro*\-averaging\. 

For example


| Actual Label | Predicted Label | Right/Wrong | 
| --- | --- | --- | 
|  1  |  1  |  Right  | 
|  0  |  1  |  Wrong  | 
|  2  |  3  |  Wrong  | 
|  3  |  3  |  Right  | 
|  2  |  2  |  Right  | 
|  1  |  1  |  Right  | 
|  3  |  3  |  Right  | 

The accuracy consists of the number of "rights" / overall test samples = 5/7 = 0\.714, or 71\.4%

**Macro Precision, Macro Recall, Macro F1**

Macro Precision, Macro Recall, and Macro F1 are also defined at a corpus level\. These calculate metrics for each label, and finds their unweighted mean\. This does not take label imbalance into account\.
+ **Macro Precision**: Precision is defined as the number of documents correctly classified, over the total number of classifications for the class\.\. The macro average is macro\-averaged per class precision\.
+ **Macro Recall**: Recall is defined as the number of classifications correctly identified over the same number plus the number of false negatives\. Macro recall just averages the recall of all the classes together\.
+ **Macro F1**: F1 score is a harmonic mean of the Precision and Recall metrics\. The Macro F1 score is the macro average of F1 scores of all the classes

This is demonstrated in the following example:

Given a test set with the following samples:

```
"label_1":400,"label_2":300, "label_3":30000,"label_4":20,"label_5":10,
```

If our classifier gets following :

```
Precision of "label_1": 0.75, label_2: 0.80, label_3: 0.90, label_4: 0.50, label_5: 0.40
Recall of "label_1": 0.70, label_2 : 0.70,label_3 :  0.98, label_4 : 0.80, label_5 : 0.10
F1 of "label_1": 0.724, label_2: 0.824, label_3: 0.94, label_4: 0.62, label_5: 0.16

Macro Precision = (0.75 + 0.80 + 0.90 + 0.50 + 0.40)/5 = 0.67
Macro Recall = (0.70 + 0.70 + 0.98 + 0.80 + 0.10)/5 = 0.656
Macro F1 = (0.724 + 0.824 + 0.94 + 0.62 + 0.16)/5 = 0.6536
```

Macro weighted values give equal weight to each of the classes, irrespective of their presence in the test data\. A very uncommon class can have equal influence on final score as the most commonly occuring class, such as a class which is present in 75% of the examples\.

One common usecase where macro averaging would give us more info over weighted metrics or the accuracy metric discussed above, is in case of extremely skewed datasets where the under\-represented classes are very important\. For example: in a cancer detection usecase where 95% of the samples would be negative, a very naive model which simply scores every sample as negative would score 95% on accuracy and 95% weighted precision, recall, and F1\. But this wouldn't be very informative, where as a macro precision would compute this to be 50% because of its average of 1 for negative class and 0 for positive class\. Note that the positive class is extremely important in this usecase\. 

## Improving Your Custom Classifier's Performance<a name="improving-metrics-doc"></a>

The metrics provide an insight into how your custom classifier will perform during a classification job\. If the metrics are low, it's very likely that the classification model might not be effective for your usecase\. If this happens, you have several options to improve your classifier performance\.

1. In your training data, provide more concrete data that can easily separate the categories\. For example, provide documents that can best represent the label in terms of unique words/sentences\. 

1. Add more data for under\-represented labels in your training data\.

1. Try to reduce skew in the categories\. If the largest label in your data is more than 10X the documents that are in the smallest label, try to increase the number of documents in the smallest and make sure to get the skew ratio down to at least 10:1 between highly represented and least represented classes\. You can also try removing few documents from highly represented classes as well\.
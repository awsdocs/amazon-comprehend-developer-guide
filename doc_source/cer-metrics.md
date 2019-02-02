# Custom Entity Recognizer Metrics<a name="cer-metrics"></a>

Amazon Comprehend provides you with metrics to help you estimate how well an entity recognizer should work for your job\. They are based on training the recognizer model, and so while they accurately represent the performance of the model during training, they are only an approximation of the API performance during entity discovery\. 

Metrics are returned any time metadata from a trained entity recognizer is returned\. 

Three metrics are available: 
+ **Precision**
+ **Recall**
+ **F1 Score**

Currently, Amazon Comprehend does not support multiple custom entity types\. These metrics are computed against the single custom entity type supported\. As a result, we are not computing micro or macro precision/recall/f1 score\.

**Precision**

This indicates how many times the model's entity identification is truly a good identification\. It is a percentage of the total number of identifications\. 

Precision is defined as the number of entities correctly identified, over the total number of attempted identifications\. 

For example, say you are searching for city names in the following sentence: 

```
John Smith lives in San Francisco, works in San Diego, and owns a house in Seattle.
```

The model returns "San Francisco" and "Smith", identified as cities from the sentence\. 

Precision is based on true positives \(tp\) and false positives \(fp\) and it is calculated as 

precision = tp / \(tp \+ fp\)\.

In this case, the precision would be 50%, as one entity was correct out of the two identified by the model\. One true positive and one false positive\.

 **Recall**

Recall is defined as the number of entities correctly identified \(true positives\) over the same number plus the number of false negative \(fn\) predictions\. It is calculated as

recall = tp / \(tp \+ fn\)

In our example, searching for city names in the sentence: 

```
John Smith lives in San Francisco, works in San Diego, and owns a house in Seattle.
```

The model returns "San Francisco" and "Smith", identified as cities from the sentence\. This is one true positive predition \("San Francisco"\) and two false negatives \("San Diego", and "Seattle"\)\.

In this case, recall is the ratio of `1 / (1 + 2)`, or 33\.33%, as one classification was a true positive, out of a possibility of three positives in the test set\.

**F1 Score** 

This is a combination of the Precision and Recall metrics, which measures the overall accuracy of the model for custom entity recognition\. The F1 score is the harmonic mean of the Precision and Recall metrics: 

F1 = 2 \* Precision \* Recall / \(Precision \+ Recall\) 

**Note**  
Intuitively, the harmonic mean penalizes the extremes more than the simple average or other means \(example: `P` = 0, `R` = 1 could be achieved trivially by predicting all possible spans\. Here, the simple average would be 0\.5, but `F1` would penalize it as 0\)\. 

In the example above, `P` = 50% and `R` = 33\.33%, therefore `F1` = 2 \* 0\.5 \* 0\.3333 / \(0\.5 \+ 0\.3333\)\. 

The F1 Score is \.3975, or 39\.75%\.

## Improving Custom Entity Recognizer Performance<a name="cer-performance"></a>

These metrics provide an insight into how accurately the trained model will perform when you use it to identify entities\. Here are a few options you can use to improve your metrics if they are lower than your expectations:

1. Depending on whether you use [Annotations](cer-annotation.md) or [Entity Lists](cer-entity-list.md), make sure to follow the guidelines in the respective documentation to improve data quality\. If you observe better metrics after improving your data and re\-training the model, you can keep iterating and improving data quality to achieve better model performance\.

1. If you are using an Entity List, consider using Annotations instead\. The increased context of the annotations can often improve your metrics\.

1. If you are sure there is not a data quality issue, and yet the metrics remain unreasonably low, please submit a support request\.
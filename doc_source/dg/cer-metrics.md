# Custom Entity Recognizer Metrics<a name="cer-metrics"></a>

Amazon Comprehend provides you with metrics to help you estimate how well an entity recognizer should work for your job\. They are based on training the recognizer model, and so while they accurately represent the performance of the model during training, they are only an approximation of the API performance during entity discovery\. 

Metrics are returned any time metadata from a trained entity recognizer is returned\. 

Amazon Comprehend supports training a model on up to 12 entities at a time\. When metrics are returned from a trained entity recognizer, scores are computed against both the recognizer as a whole \(global metrics\) and for each individual entity \(entity metrics\)\.

Three metrics are available, both as global and entity metrics: 
+ **Precision**

  This indicates how many times the model makes a correct entity identification compared to the number of attempted identifications\. This shows how many times the model's entity identification is truly a good identification\. It is a percentage of the total number of identifications\. 

  In other words, precision is based on *true positives \(tp\)* and *false positives \(fp\)* and it is calculated as *precision = tp / \(tp \+ fp\)*\.

  For example, if a model predicts that two examples of an entity are present in a document, where there's actually only one, the result is one true positive and one false positive\. In this case, *precision = 1 / \(1 \+ 1\)*\. The precision is 50%, as one entity is correct out of the two identified by the model\. 
+  **Recall**

  This indicates how many times the model makes a correct entity identification compared to the number of instances of that the entity is actually present \(as defined by the total number of correct identifications *true positives \(tp\)* and missed identifcations *false negatives \(fn\)*\. 

   It is calculated as *recall = tp / \(tp \+ fn\)*\. For example if a model correctly identifies one entity, but misses two other instances where that entity is present, the result is one true positive and two false negatives\. In this case, *recall = 1 / \(1 \+ 2\)*\. The recall is 33\.33%, as one entity is correct out of a possible three examples\.
+ **F1 Score** 

  This is a combination of the Precision and Recall metrics, which measures the overall accuracy of the model for custom entity recognition\. The F1 score is the harmonic mean of the Precision and Recall metrics: *F1 = 2 \* Precision \* Recall / \(Precision \+ Recall\) *\.
**Note**  
Intuitively, the harmonic mean penalizes the extremes more than the simple average or other means \(example: `precision` = 0, `recall` = 1 could be achieved trivially by predicting all possible spans\. Here, the simple average would be 0\.5, but `F1` would penalize it as 0\)\. 

  In the examples above, `precision` = 50% and `recall` = 33\.33%, therefore `F1` = 2 \* 0\.5 \* 0\.3333 / \(0\.5 \+ 0\.3333\)\. The F1 Score is \.3975, or 39\.75%\.

**Global and Individual Entity Metrics**

The relationship between global and individual entity metrics can be seen when analyzing the following sentence for entities that are either a *place* or a *person*

```
John Washington and his friend Smith live in San Francisco, work in San Diego, and own 
    a house in Seattle.
```

In our example, the model makes the following predictions\.

```
John Washington = Person
Smith = Place
San Francisco = Place
San Diego = Place
Seattle = Person
```

However, the predictions should have been the following\.

```
John Washington = Person
Smith = Person  
San Francisco = Place
San Diego = Place
Seattle = Place
```

The individual entity metrics for this would be:

```
entity:  Person
  True positive (TP) = 1 (because John Washington is correctly predicted to be a 
    Person).
  False positive (FP) = 1 (because Seattle is incorrectly predicted to be a Person, 
    but is actually a Place).
  False negative (FN) = 1 (because Smith is incorrectly predicted to be a Place, but 
    is actually a Person).
  Precision = 1 / (1 + 1) = 0.5 or 50%
  Recall = 1 / (1+1) = 0.5 or 50%
  F1 Score = 2 * 0.5 * 0.5 / (0.5 + 0.5) = 0.5 or 50%
  
entity:  Place
  TP = 2 (because San Francisco and San Diego are each correctly predicted to be a 
    Place).
  FP = 1 (because Smith is incorrectly predicted to be a Place, but is actually a 
    Person).
  FN = 1 (because Seattle is incorrectly predicted to be a Person, but is actually a 
    Place).
  Precision = 2 / (2+1) = 0.6667 or 66.67%
  Recall = 2 / (2+1) = 0.6667 or 66.67%
  F1 Score = 2 * 0.6667 * 0.6667 / (0.6667 + 0.6667) = 0.6667 or  66.67%
```

The global metrics for this would be:

Global:

```
Global:
  TP = 3 (because John Washington, San Francisco and San Diego are predicted correctly. 
    This is also the sum of all individual entity TP).
  FP = 2 (because Seattle is predicted as Person and Smith is predicted as Place. This 
    is the sum of all individual entity FP).
  FN = 2 (because Seattle is predicted as Person and Smith is predicted as Place. This 
    is the sum of all individual FN).
  Global Precision = 3 / (3+2) = 0.6 or 60%  
    (Global Precision = Global TP / (Global TP + Global FP))
  Global Recall = 3 / (3+2) = 0.6 or 60% 
    (Global Recall = Global TP / (Global TP + Global FN))
  Global F1Score = 2 * 0.6 * 0.6 / (0.6 + 0.6) = 0.6 or 60% 
    (Global F1Score = 2 * Global Precision *  Global Recall / (Global Precision + 
    Global Recall))
```

## Improving Custom Entity Recognizer Performance<a name="cer-performance"></a>

These metrics provide an insight into how accurately the trained model will perform when you use it to identify entities\. Here are a few options you can use to improve your metrics if they are lower than your expectations:

1. Depending on whether you use [Annotations](cer-annotation.md) or [Entity Lists](cer-entity-list.md), make sure to follow the guidelines in the respective documentation to improve data quality\. If you observe better metrics after improving your data and re\-training the model, you can keep iterating and improving data quality to achieve better model performance\.

1. If you are using an Entity List, consider using Annotations instead\. The increased context of the annotations can often improve your metrics\.

1. If you are sure there is not a data quality issue, and yet the metrics remain unreasonably low, please submit a support request\.
# Custom Classifier Metrics<a name="cer-doc-class"></a>

Amazon Comprehend provides you with metrics to help you estimate how well a custom classifier should work for your job\. They are based on training the classifier model, and so while they accurately represent the performance of the model during training, they are only an approximation of the API performance during classification\. 

Metrics are included any time metadata from a trained custom classifier is returned\. 

**Note**  
Please refer to [Metrics: Precision, Recall, and FScore](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_fscore_support.html) for an understanding of the underlying Precision, Recall, and F1 score metrics\. These metrics are defined at a class level\. We have used **macro** averaging for combining these metrics together to come up with the test set P,R,F1, as discussed below\.

Amazon Comprehend creates a [Confusion Matrix](conf-matrix.md) as part of the custom classifier model training\. This is placed in the output file specified in the [ CreateDocumentClassifier ](API_CreateDocumentClassifier.md) operation and can be used to assess how well the model works\.

We also support the following metrics: 
+ **Accuracy**
+ **Precision \(Macro Precision\)**
+ **Recall \(Macro Recall\)**
+ **F1 Score \(Macro F1 Score\)**
+ **Hamming Loss**
+ **Micro Precision**
+ **Micro Recall**
+ **Micro F1 Score**



These can be seen on the **Classifier Details** page in the console\.

![\[Custom Classifier Metrics\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/classifierperformance.png)

## Accuracy<a name="class-accuracy-metric"></a>

Accuracy indicates the percentage of labels from the test data that are predicted exactly right by the model\. In other words, this is the fraction of the labels that were correct recognized\. It is computed by dividing the number of labels in the test documents that were correctly recognized by the total number of labels in the test documents\.

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

The accuracy consists of the number of "rights" divided by the number of overall test samples = 5/7 = 0\.714, or 71\.4%

## Precision \(Macro Precision\)<a name="class-macroprecision-metric"></a>

Precision is a measure of the usefulness of the classifier results in the test data\. It's defined as the number of documents correctly classified, divided by the total number of classifications for the class\. High precision means that the classifier returned substantially more relevant results than irrelevant ones\. 

The `Precision` metric is also known as *Macro Precision*\. 

This is demonstrated in the following test set:


| Label | Sample Size | Label Precision | 
| --- | --- | --- | 
|  Label\_1  |  400  |  0\.75  | 
|  Label\_2  |  300  |  0\.80  | 
|  Label\_3  |  30000  |  0\.90  | 
|  Label\_4  |  20  |  0\.50  | 
|  Label\_5  |  10  |  0\.40  | 

The Precision \(Macro Precision\) metric for the model is therefore:

```
Macro Precision = (0.75 + 0.80 + 0.90 + 0.50 + 0.40)/5 = 0.67
```

## Recall \(Macro Recall\)<a name="class-macrorecall-metric"></a>

This indicates the percentage of correct categories in your text that the model can predict\. This metric comes from averaging the recall scores of all available labels\. Recall is a measure of how complete the classifier results are for the test data\. 

High recall means that the classifier returned most of the relevant results\. 

The `Recall` metric is also known as *Macro Recall*\.

This is demonstrated in the following test set:


| Label | Sample Size | Label Recall | 
| --- | --- | --- | 
|  Label\_1  |  400  |  0\.70  | 
|  Label\_2  |  300  |  0\.70  | 
|  Label\_3  |  30000  |  0\.98  | 
|  Label\_4  |  20  |  0\.80  | 
|  Label\_5  |  10  |  0\.10  | 

The Recall \(Macro Recall\) metric for the model is therefore:

```
Macro Recall = (0.70 + 0.70 + 0.98 + 0.80 + 0.10)/5 = 0.656
```

## F1 Score \(Macro F1 Score\)<a name="class-macrof1score-metric"></a>

 A combination of the Precision and Recall metrics\. The F1 score is the harmonic mean of the Precision and Recall metrics\. This score is based on the Precision and Recall created by the averaging method and is also known as the Macro F1 score\. A measure of how accurate the classifier results are for the test data\. It is derived from the `Precision` and `Recall` values\. The `F1Score` is the harmonic average of the two scores\. The highest score is 1, and the worst score is 0\. 

The `F1 Score` metric is also known as the *Macro F1 Score*\.

This is demonstrated in the following test set:


| Label | Sample Size | Label F1 Score | 
| --- | --- | --- | 
|  Label\_1  |  400  |  0\.724  | 
|  Label\_2  |  300  |  0\.824  | 
|  Label\_3  |  30000  |  0\.94  | 
|  Label\_4  |  20  |  0\.62  | 
|  Label\_5  |  10  |  0\.16  | 

The F1 Score \(Macro F1 Score\) for the model is therefore as follows:

```
Macro F1 Score = (0.724 + 0.824 + 0.94 + 0.62 + 0.16)/5 = 0.6536
```

## Hamming Loss<a name="class-hammingloss-metric"></a>

The fraction of labels that are incorrectly predicted\. Also seen as the fraction of wrong labels compared to the total number of labels\. Scores closer to zero are better\.

## Micro Precision<a name="class-microprecision-metric"></a>

As Precision above, except that instead of averaging the precision scores of all available labels, this is based on the overall score of all precision scores added together\.

## Micro Recall<a name="class-microrecall-metric"></a>

As Recall above, except that instead of averaging the recall scores of all labels, this is based on the overall score of all recall scores added together\.

## Micro F1 Score<a name="class-microf1score-metric"></a>

As F1 Score above, but instead a combination of the Micro Precision and Micro Recall metrics\.

## Improving Your Custom Classifier's Performance<a name="improving-metrics-doc"></a>

The metrics provide an insight into how your custom classifier will perform during a classification job\. If the metrics are low, it's very likely that the classification model might not be effective for your use case\. If this happens, you have several options to improve your classifier performance\.

1. In your training data, provide more concrete data that can easily separate the categories\. For example, provide documents that can best represent the label in terms of unique words/sentences\. 

1. Add more data for under\-represented labels in your training data\.

1. Try to reduce skew in the categories\. If the largest label in your data is more than 10X the documents that are in the smallest label, try to increase the number of documents in the smallest and make sure to get the skew ratio down to at least 10:1 between highly represented and least represented classes\. You can also try removing few documents from highly represented classes as well\.

**Confusion Matrix**

A confusion matrix can give a very good indication on the classes for which adding more data would help model performance\. A higher fraction of samples for a label shown along the diagonal of the matrix shows that the classifier is able to classify that label more accurately\. If this number is lower \(if the label class has a higher fraction of its samples in the non\-diagonal portion of the matrix\), you can try to add more samples\. For example, if 40 percent of label A samples are classified as label D, adding more samples for both label A and label D will enhance the performance of the classifier\. For more information, see [Confusion Matrix](conf-matrix.md)\.
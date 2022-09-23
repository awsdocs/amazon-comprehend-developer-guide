# Custom classifier metrics<a name="cer-doc-class"></a>

Amazon Comprehend provides you with metrics to help you estimate how well a custom classifier should work for your job\. They are based on training the classifier model, and so while they accurately represent the performance of the model during training, they are only an approximation of the model performance during classification\. 

Metrics are included any time metadata from a trained custom classifier is returned\. 

**Note**  
Please refer to [Metrics: Precision, recall, and FScore](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_fscore_support.html) for an understanding of the underlying Precision, Recall, and F1 score metrics\. These metrics are defined at a class level\. We have used **macro** averaging for combining these metrics together to come up with the test set P,R,F1, as discussed below\.

Amazon Comprehend creates a [Confusion matrix](#conf-matrix) as part of the custom classifier model training\. This is placed in the output file specified in the [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateDocumentClassifier.html) operation and can be used to assess how well the model works\.

**Topics**
+ [Metrics](#cer-doc-class-metrics)
+ [Improving your custom classifier's performance](#improving-metrics-doc)
+ [Confusion matrix](#conf-matrix)

## Metrics<a name="cer-doc-class-metrics"></a>

Amazon Comprehend supports the following metrics: 

**Topics**
+ [Accuracy](#class-accuracy-metric)
+ [Precision \(macro precision\)](#class-macroprecision-metric)
+ [Recall \(macro recall\)](#class-macrorecall-metric)
+ [F1 score \(macro F1 score\)](#class-macrof1score-metric)
+ [Hamming loss](#class-hammingloss-metric)
+ [Micro precision](#class-microprecision-metric)
+ [Micro recall](#class-microrecall-metric)
+ [Micro F1 score](#class-microf1score-metric)

These can be seen on the **Classifier Details** page in the console\.

![\[Custom Classifier Metrics\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/classifierperformance.png)

### Accuracy<a name="class-accuracy-metric"></a>

Accuracy indicates the percentage of labels from the test data that are predicted exactly right by the model\. In other words, this is the fraction of the labels that were correctly recognized\. It is computed by dividing the number of labels in the test documents that were correctly recognized by the total number of labels in the test documents\.

For example


| Actual label | Predicted label | Right/Wrong | 
| --- | --- | --- | 
|  1  |  1  |  Right  | 
|  0  |  1  |  Wrong  | 
|  2  |  3  |  Wrong  | 
|  3  |  3  |  Right  | 
|  2  |  2  |  Right  | 
|  1  |  1  |  Right  | 
|  3  |  3  |  Right  | 

The accuracy consists of the number of "rights" divided by the number of overall test samples = 5/7 = 0\.714, or 71\.4%

### Precision \(macro precision\)<a name="class-macroprecision-metric"></a>

Precision is a measure of the usefulness of the classifier results in the test data\. It's defined as the number of documents correctly classified, divided by the total number of classifications for the class\. High precision means that the classifier returned substantially more relevant results than irrelevant ones\. 

The `Precision` metric is also known as *Macro Precision*\. 

This is demonstrated in the following test set:


| Label | Sample size | Label precision | 
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

### Recall \(macro recall\)<a name="class-macrorecall-metric"></a>

This indicates the percentage of correct categories in your text that the model can predict\. This metric comes from averaging the recall scores of all available labels\. Recall is a measure of how complete the classifier results are for the test data\. 

High recall means that the classifier returned most of the relevant results\. 

The `Recall` metric is also known as *Macro Recall*\.

This is demonstrated in the following test set:


| Label | Sample size | Label recall | 
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

### F1 score \(macro F1 score\)<a name="class-macrof1score-metric"></a>

The F1 score is derived from the `Precision` and `Recall` values\. It measures the overall accuracy of the classifier\. The highest score is 1, and the lowest score is 0\. 

Amazon Comprehend calculates the *Macro F1 Score*\. It is the unweighted average of the label F1 scores\. Using the following test set as an example:


| Label | Sample size | Label F1 score | 
| --- | --- | --- | 
|  Label\_1  |  400  |  0\.724  | 
|  Label\_2  |  300  |  0\.824  | 
|  Label\_3  |  30000  |  0\.94  | 
|  Label\_4  |  20  |  0\.62  | 
|  Label\_5  |  10  |  0\.16  | 

The F1 Score \(Macro F1 Score\) for the model is calculated as follows:

```
Macro F1 Score = (0.724 + 0.824 + 0.94 + 0.62 + 0.16)/5 = 0.6536
```

### Hamming loss<a name="class-hammingloss-metric"></a>

The fraction of labels that are incorrectly predicted\. Also seen as the fraction of wrong labels compared to the total number of labels\. Scores closer to zero are better\.

### Micro precision<a name="class-microprecision-metric"></a>

Original: 

As Precision above, except that instead of averaging the precision scores of all available labels, this is based on the overall score of all precision scores added together\.

### Micro recall<a name="class-microrecall-metric"></a>

As Recall above, except that instead of averaging the recall scores of all labels, this is based on the overall score of all recall scores added together\.

### Micro F1 score<a name="class-microf1score-metric"></a>

As F1 Score above, but instead a combination of the Micro Precision and Micro Recall metrics\.

## Improving your custom classifier's performance<a name="improving-metrics-doc"></a>

The metrics provide an insight into how your custom classifier will perform during a classification job\. If the metrics are low, it's very likely that the classification model might not be effective for your use case\. If this happens, you have several options to improve your classifier performance\.

1. In your training data, provide more concrete data that can easily separate the categories\. For example, provide documents that can best represent the label in terms of unique words/sentences\. 

1. Add more data for under\-represented labels in your training data\.

1. Try to reduce skew in the categories\. If the largest label in your data is more than 10X the documents that are in the smallest label, try to increase the number of documents in the smallest and make sure to get the skew ratio down to at least 10:1 between highly represented and least represented classes\. You can also try removing few documents from highly represented classes as well\.

## Confusion matrix<a name="conf-matrix"></a>

When a custom classifier model is trained, Amazon Comprehend creates a confusion matrix that provides metrics on how well the model performed in training\. This enables you to assess how well the classifier will perform when run\. This matrix shows a matrix of labels as predicted by the model compared to actual labels and is created using 10 to 20 percent of the documents submitted to test the trained model\.

A confusion matrix can give a very good indication on the classes for which adding more data would help model performance\. A higher fraction of samples for a label shown along the diagonal of the matrix shows that the classifier is able to classify that label more accurately\. If this number is lower \(if the label class has a higher fraction of its samples in the non\-diagonal portion of the matrix\), you can try to add more samples\. For example, if 40 percent of label A samples are classified as label D, adding more samples for both label A and label D will enhance the performance of the classifier\. For more information, see [Confusion matrix](#conf-matrix)\.

The format of the confusion matrix produced varies, depending on if you train your classifier using multi\-class or multi\-label mode\.

### Confusion matrix for multi\-class mode<a name="m-c-matrix"></a>

Recall that in multi\-class classification, the individual classes are mutually exclusive and each document is expected to have one and only one label assigned to it\. For example, an animal can be a dog or a cat, but not both at the same time\.

Consider the following example of a confusion matrix for a multi\-class trained classifier:

```
  A B X Y <-(predicted label)
A 1 2 0 4
B 0 3 0 1
X 0 0 1 0
Y 1 1 1 1
^
|
(actual label)
```

In this case, the model predicted the following:
+ One "A" label was correctly identified, two "A" labels were incorrectly identified as actually "B" labels, and four "A" labels were incorrectly identified as "Y" labels\.
+ Three "B" labels were correctly identified, and one "B" label was incorrectly identified as a "Y" label\.
+ One "X" was correctly identified\.
+ One "Y" label was incorrectly identified as an "A" label, one was incorrectly identified as a "B" label, one was incorrectly identified as an "X" label, and one was correctly identified as a "Y" label\.

In this matrix, the correctly identified labels are shown on the diagonal line \(A:A, B:B, X:X, and Y:Y\) so you can easily check the table for prediction errors because they will be represented as values outside this diagonal\. In this case, you can see that the model correctly identifies "X" labels \(although the sample is very small\) and can correctly identify "B" labels 75% of the time\. However, it incorrectly identifies "A" labels 86% of the time and correctly identifies "Y" labels at a rate no better than random chance\.

The confusion matrix is presented in JSON format and for the above example is shown as the following:

```
{
 "type": "multi_class",
 "confusion_matrix": [
 [1, 2, 0,4],
 [0, 3, 0, 1],
 [0, 0, 1, 0],
 [1, 1, 1, 1]],
 "labels": ["A", "B", "X", "Y"],
 "all_labels": ["A", "B", "X", "Y"]
}
```

### Confusion matrix for multi\-label mode<a name="m-l-matrix"></a>

Recall that in multi\-label classification, the individual labels represent different categories, but these categories are somehow related\. For example, a movie can be just an action movie, or it can be an action movie, a science fiction movie, and a comedy, all at the same time\.

Consider the following example of a confusion matrix for a multi\-class trained classifier\.

In this example, there are three possible labels: `Comedy`, `Action`, and `Drama`\. Unlike the multi\-class confusion matrix, the multi\-label confusion matrix creates one 2x2 matrix for each label as shown below\.

```
Comedy                   Action                   Drama 
     No Yes                   No Yes                   No Yes   <-(predicted label)                                      
 No  2   1                No  1   1                No  3   0                                                         
Yes  0   2               Yes  2   1               Yes  1   1   
 ^                        ^                        ^
 |                        |                        |
 |-----------(was this label actually used)--------|
```

In this case, the model returned the following for the `Comedy` label:
+ Two instances where a `Comedy` label was not present and was correctly predicted to not be present\. True negative \(TN\)\.
+ Zero instances where a `Comedy` label was predicted to be present but was not\. False positive \(FP\)\.
+ One instance where a `Comedy` label was predicted to be absent but was present\. False negative \(FN\)\.
+ Two instances where a `Comedy` label was present were correctly predicted to be present\. True positive \(TP\)\. 

As with the multi\-class confusion matrix above, the correctly identified labels here are shown on the diagonal line \(Yes:Yes and No:No\)\. You can easily check the table for prediction errors because they will be represented as values outside this diagonal\. In this case, you can see that the model correctly identifies `Comedy` labels as present 40% of the time and can correctly identify their absence to the same degree \(40%\)\. However, it incorrectly identifies `Comedy` labels as being present 20% of the time\. It did not incorrectly identify a `Comedy` label as absent when it was not\.

The confusion matrix is presented in JSON format and for the above example is shown as the following:

```
{
"type": "multi_label",
"confusion_matrix": [
 [[2, 1],        
 [0, 2]],
 [[1, 1],        
 [2, 1]],      
 [[3, 0],        
 [1, 1]]
], 
"labels": ["Comedy", "Action", "Drama"]
"all_labels": ["Comedy", "Action", "Drama"]
}
```



**The CreateDocumentClassifier API**

The confusion matrix is available when running the [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateDocumentClassifier.html) API operation\. When the operation is run, the confusion matrix is shown in the `confusion_matrix.json` file, located at `s3://user-defined-path/unique-value/output/output.tar.gz` where the user\-defined\-path is the `S3Uri` value of the `OutputDataConfig` parameter in the [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateDocumentClassifier.html) operation\. 
# Confusion Matrix<a name="conf-matrix"></a>

When a custom classifier model is trained, Amazon Comprehend creates a confusion matrix that provides metrics on how well the model performed in training\. This enables you to assess how well the classifier will perform when run\. This matrix shows a matrix of labels as predicted by the model compared to actual labels and is created using 10 to 20 percent of the documents submitted to test the trained model\.

The format of the confusion matrix produced varies, depending on if you train your classifier using multi\-class or multi\-label mode\.

## Confusion Matrix for Multi\-Class Mode<a name="m-c-matrix"></a>

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

## Confusion Matrix for Multi\-Label Mode<a name="m-l-matrix"></a>

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

The confusion matrix is available when running the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) API\. When the operation is run, the confusion matrix is shown in the `confusion_matrix.json` file, located at `s3://user-defined-path/unique-value/output/output.tar.gz` where the user\-defined\-path is the `S3Uri` value of the `OutputDataConfig` parameter in the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation\. 
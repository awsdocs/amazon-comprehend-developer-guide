# ClassifierEvaluationMetrics<a name="API_ClassifierEvaluationMetrics"></a>

Describes the result metrics for the test data associated with an documentation classifier\.

## Contents<a name="API_ClassifierEvaluationMetrics_Contents"></a>

 ** Accuracy **   <a name="comprehend-Type-ClassifierEvaluationMetrics-Accuracy"></a>
The fraction of the labels that were correct recognized\. It is computed by dividing the number of labels in the test documents that were correctly recognized by the total number of labels in the test documents\.  
Type: Double  
Required: No

 ** F1Score **   <a name="comprehend-Type-ClassifierEvaluationMetrics-F1Score"></a>
A measure of how accurate the classifier results are for the test data\. It is derived from the `Precision` and `Recall` values\. The `F1Score` is the harmonic average of the two scores\. The highest score is 1, and the worst score is 0\.   
Type: Double  
Required: No

 ** HammingLoss **   <a name="comprehend-Type-ClassifierEvaluationMetrics-HammingLoss"></a>
Indicates the fraction of labels that are incorrectly predicted\. Also seen as the fraction of wrong labels compared to the total number of labels\. Scores closer to zero are better\.  
Type: Double  
Required: No

 ** MicroF1Score **   <a name="comprehend-Type-ClassifierEvaluationMetrics-MicroF1Score"></a>
A measure of how accurate the classifier results are for the test data\. It is a combination of the `Micro Precision` and `Micro Recall` values\. The `Micro F1Score` is the harmonic mean of the two scores\. The highest score is 1, and the worst score is 0\.  
Type: Double  
Required: No

 ** MicroPrecision **   <a name="comprehend-Type-ClassifierEvaluationMetrics-MicroPrecision"></a>
A measure of the usefulness of the recognizer results in the test data\. High precision means that the recognizer returned substantially more relevant results than irrelevant ones\. Unlike the Precision metric which comes from averaging the precision of all available labels, this is based on the overall score of all precision scores added together\.  
Type: Double  
Required: No

 ** MicroRecall **   <a name="comprehend-Type-ClassifierEvaluationMetrics-MicroRecall"></a>
A measure of how complete the classifier results are for the test data\. High recall means that the classifier returned most of the relevant results\. Specifically, this indicates how many of the correct categories in the text that the model can predict\. It is a percentage of correct categories in the text that can found\. Instead of averaging the recall scores of all labels \(as with Recall\), micro Recall is based on the overall score of all recall scores added together\.  
Type: Double  
Required: No

 ** Precision **   <a name="comprehend-Type-ClassifierEvaluationMetrics-Precision"></a>
A measure of the usefulness of the classifier results in the test data\. High precision means that the classifier returned substantially more relevant results than irrelevant ones\.  
Type: Double  
Required: No

 ** Recall **   <a name="comprehend-Type-ClassifierEvaluationMetrics-Recall"></a>
A measure of how complete the classifier results are for the test data\. High recall means that the classifier returned most of the relevant results\.   
Type: Double  
Required: No

## See Also<a name="API_ClassifierEvaluationMetrics_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
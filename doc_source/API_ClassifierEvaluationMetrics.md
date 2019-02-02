# ClassifierEvaluationMetrics<a name="API_ClassifierEvaluationMetrics"></a>

Describes the result metrics for the test data associated with an documentation classifier\.

## Contents<a name="API_ClassifierEvaluationMetrics_Contents"></a>

 **Accuracy**   <a name="comprehend-Type-ClassifierEvaluationMetrics-Accuracy"></a>
The fraction of the labels that were correct recognized\. It is computed by dividing the number of labels in the test documents that were correctly recognized by the total number of labels in the test documents\.  
Type: Double  
Required: No

 **F1Score**   <a name="comprehend-Type-ClassifierEvaluationMetrics-F1Score"></a>
A measure of how accurate the classifier results are for the test data\. It is derived from the `Precision` and `Recall` values\. The `F1Score` is the harmonic average of the two scores\. The highest score is 1, and the worst score is 0\.   
Type: Double  
Required: No

 **Precision**   <a name="comprehend-Type-ClassifierEvaluationMetrics-Precision"></a>
A measure of the usefulness of the classifier results in the test data\. High precision means that the classifier returned substantially more relevant results than irrelevant ones\.  
Type: Double  
Required: No

 **Recall**   <a name="comprehend-Type-ClassifierEvaluationMetrics-Recall"></a>
A measure of how complete the classifier results are for the test data\. High recall means that the classifier returned most of the relevant results\.   
Type: Double  
Required: No

## See Also<a name="API_ClassifierEvaluationMetrics_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/ClassifierEvaluationMetrics) 
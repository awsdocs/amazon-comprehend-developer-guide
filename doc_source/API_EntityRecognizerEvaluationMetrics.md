# EntityRecognizerEvaluationMetrics<a name="API_EntityRecognizerEvaluationMetrics"></a>

Detailed information about the accuracy of an entity recognizer\. 

## Contents<a name="API_EntityRecognizerEvaluationMetrics_Contents"></a>

 ** F1Score **   <a name="comprehend-Type-EntityRecognizerEvaluationMetrics-F1Score"></a>
A measure of how accurate the recognizer results are for the test data\. It is derived from the `Precision` and `Recall` values\. The `F1Score` is the harmonic average of the two scores\. For plain text entity recognizer models, the range is 0 to 100, where 100 is the best score\. For PDF/Word entity recognizer models, the range is 0 to 1, where 1 is the best score\.   
Type: Double  
Required: No

 ** Precision **   <a name="comprehend-Type-EntityRecognizerEvaluationMetrics-Precision"></a>
A measure of the usefulness of the recognizer results in the test data\. High precision means that the recognizer returned substantially more relevant results than irrelevant ones\.   
Type: Double  
Required: No

 ** Recall **   <a name="comprehend-Type-EntityRecognizerEvaluationMetrics-Recall"></a>
A measure of how complete the recognizer results are for the test data\. High recall means that the recognizer returned most of the relevant results\.  
Type: Double  
Required: No

## See Also<a name="API_EntityRecognizerEvaluationMetrics_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerEvaluationMetrics) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerEvaluationMetrics) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityRecognizerEvaluationMetrics) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerEvaluationMetrics) 
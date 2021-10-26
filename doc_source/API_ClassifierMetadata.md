# ClassifierMetadata<a name="API_ClassifierMetadata"></a>

Provides information about a document classifier\.

## Contents<a name="API_ClassifierMetadata_Contents"></a>

 ** EvaluationMetrics **   <a name="comprehend-Type-ClassifierMetadata-EvaluationMetrics"></a>
 Describes the result metrics for the test data associated with an documentation classifier\.  
Type: [ ClassifierEvaluationMetrics ](API_ClassifierEvaluationMetrics.md) object  
Required: No

 ** NumberOfLabels **   <a name="comprehend-Type-ClassifierMetadata-NumberOfLabels"></a>
The number of labels in the input data\.   
Type: Integer  
Required: No

 ** NumberOfTestDocuments **   <a name="comprehend-Type-ClassifierMetadata-NumberOfTestDocuments"></a>
The number of documents in the input data that were used to test the classifier\. Typically this is 10 to 20 percent of the input documents, up to 10,000 documents\.  
Type: Integer  
Required: No

 ** NumberOfTrainedDocuments **   <a name="comprehend-Type-ClassifierMetadata-NumberOfTrainedDocuments"></a>
The number of documents in the input data that were used to train the classifier\. Typically this is 80 to 90 percent of the input documents\.  
Type: Integer  
Required: No

## See Also<a name="API_ClassifierMetadata_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ClassifierMetadata) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ClassifierMetadata) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ClassifierMetadata) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ClassifierMetadata) 
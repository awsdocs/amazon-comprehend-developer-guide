# DocumentClassifierFilter<a name="API_DocumentClassifierFilter"></a>

Provides information for filtering a list of document classifiers\. You can only specify one filtering parameter in a request\. For more information, see the [ ListDocumentClassifiers ](API_ListDocumentClassifiers.md) operation\.

## Contents<a name="API_DocumentClassifierFilter_Contents"></a>

 ** DocumentClassifierName **   <a name="comprehend-Type-DocumentClassifierFilter-DocumentClassifierName"></a>
The name that you assigned to the document classifier  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: No

 ** Status **   <a name="comprehend-Type-DocumentClassifierFilter-Status"></a>
Filters the list of classifiers based on status\.  
Type: String  
Valid Values:` SUBMITTED | TRAINING | DELETING | STOP_REQUESTED | STOPPED | IN_ERROR | TRAINED`   
Required: No

 ** SubmitTimeAfter **   <a name="comprehend-Type-DocumentClassifierFilter-SubmitTimeAfter"></a>
Filters the list of classifiers based on the time that the classifier was submitted for processing\. Returns only classifiers submitted after the specified time\. Classifiers are returned in descending order, newest to oldest\.  
Type: Timestamp  
Required: No

 ** SubmitTimeBefore **   <a name="comprehend-Type-DocumentClassifierFilter-SubmitTimeBefore"></a>
Filters the list of classifiers based on the time that the classifier was submitted for processing\. Returns only classifiers submitted before the specified time\. Classifiers are returned in ascending order, oldest to newest\.  
Type: Timestamp  
Required: No

## See Also<a name="API_DocumentClassifierFilter_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DocumentClassifierFilter) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DocumentClassifierFilter) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DocumentClassifierFilter) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DocumentClassifierFilter) 
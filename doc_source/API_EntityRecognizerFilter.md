# EntityRecognizerFilter<a name="API_EntityRecognizerFilter"></a>

Provides information for filtering a list of entity recognizers\. You can only specify one filtering parameter in a request\. For more information, see the [ListEntityRecognizers](API_ListEntityRecognizers.md) operation\./>

## Contents<a name="API_EntityRecognizerFilter_Contents"></a>

 **Status**   <a name="comprehend-Type-EntityRecognizerFilter-Status"></a>
The status of an entity recognizer\.  
Type: String  
Valid Values:` SUBMITTED | TRAINING | DELETING | STOP_REQUESTED | STOPPED | IN_ERROR | TRAINED`   
Required: No

 **SubmitTimeAfter**   <a name="comprehend-Type-EntityRecognizerFilter-SubmitTimeAfter"></a>
Filters the list of entities based on the time that the list was submitted for processing\. Returns only jobs submitted after the specified time\. Jobs are returned in ascending order, oldest to newest\.  
Type: Timestamp  
Required: No

 **SubmitTimeBefore**   <a name="comprehend-Type-EntityRecognizerFilter-SubmitTimeBefore"></a>
Filters the list of entities based on the time that the list was submitted for processing\. Returns only jobs submitted before the specified time\. Jobs are returned in descending order, newest to oldest\.  
Type: Timestamp  
Required: No

## See Also<a name="API_EntityRecognizerFilter_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerFilter) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerFilter) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/EntityRecognizerFilter) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerFilter) 
# DocumentClassificationJobFilter<a name="API_DocumentClassificationJobFilter"></a>

Provides information for filtering a list of document classification jobs\. For more information, see the [ListDocumentClassificationJobs](API_ListDocumentClassificationJobs.md) operation\. You can provide only one filter parameter in each request\.

## Contents<a name="API_DocumentClassificationJobFilter_Contents"></a>

 **JobName**   <a name="comprehend-Type-DocumentClassificationJobFilter-JobName"></a>
Filters on the name of the job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobStatus**   <a name="comprehend-Type-DocumentClassificationJobFilter-JobStatus"></a>
Filters the list based on job status\. Returns only jobs with the specified status\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 **SubmitTimeAfter**   <a name="comprehend-Type-DocumentClassificationJobFilter-SubmitTimeAfter"></a>
Filters the list of jobs based on the time that the job was submitted for processing\. Returns only jobs submitted before the specified time\. Jobs are returned in descending order, newest to oldest\.  
Type: Timestamp  
Required: No

 **SubmitTimeBefore**   <a name="comprehend-Type-DocumentClassificationJobFilter-SubmitTimeBefore"></a>
Filters the list of jobs based on the time that the job was submitted for processing\. Returns only jobs submitted after the specified time\. Jobs are returned in ascending order, oldest to newest\.  
Type: Timestamp  
Required: No

## See Also<a name="API_DocumentClassificationJobFilter_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DocumentClassificationJobFilter) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DocumentClassificationJobFilter) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DocumentClassificationJobFilter) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DocumentClassificationJobFilter) 
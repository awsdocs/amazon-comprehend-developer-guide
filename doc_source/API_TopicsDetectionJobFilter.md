# TopicsDetectionJobFilter<a name="API_TopicsDetectionJobFilter"></a>

Provides information for filtering topic detection jobs\. For more information, see [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md)\.

## Contents<a name="API_TopicsDetectionJobFilter_Contents"></a>

 **JobName**   <a name="comprehend-Type-TopicsDetectionJobFilter-JobName"></a>
  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobStatus**   <a name="comprehend-Type-TopicsDetectionJobFilter-JobStatus"></a>
Filters the list of topic detection jobs based on job status\. Returns only jobs with the specified status\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 **SubmitTimeAfter**   <a name="comprehend-Type-TopicsDetectionJobFilter-SubmitTimeAfter"></a>
Filters the list of jobs based on the time that the job was submitted for processing\. Only returns jobs submitted after the specified time\. Jobs are returned in ascending order, oldest to newest\.  
Type: Timestamp  
Required: No

 **SubmitTimeBefore**   <a name="comprehend-Type-TopicsDetectionJobFilter-SubmitTimeBefore"></a>
Filters the list of jobs based on the time that the job was submitted for processing\. Only returns jobs submitted before the specified time\. Jobs are returned in descending order, newest to oldest\.  
Type: Timestamp  
Required: No

## See Also<a name="API_TopicsDetectionJobFilter_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/TopicsDetectionJobFilter) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/TopicsDetectionJobFilter) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/TopicsDetectionJobFilter) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/TopicsDetectionJobFilter) 
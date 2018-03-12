# Amazon Comprehend API Permissions: Actions, Resources, and Conditions Reference<a name="comprehend-api-permissions-ref"></a>

Use the following table as a reference when setting up [Access Control](auth-and-access-control.md#access-control) and writing a permissions policy that you can attach to an IAM identity \(an identity\-based policy\)\. The list includes each Amazon Comprehend API operation, the corresponding action for which you can grant permissions to perform the action, and the AWS resource for which you can grant the permissions\. You specify the actions in the policy's `Action` field, and you specify the resource value in the policy's `Resource` field\. 

To express conditions, you can use AWS\-wide condition keys in your Amazon Comprehend policies\. For a complete list of AWS\-wide keys, see [Available Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

**Note**  
To specify an action, use the `comprehend:` prefix followed by the API operation name, for example, `comprehend:DetectEntities`\.

If you see an expand arrow \(**↗**\) in the upper\-right corner of the table, you can open the table in a new window\. To close the window, choose the close button \(**X**\) in the lower\-right corner\.


**Amazon Comprehend API and Required Permissions for Actions**  

| Amazon Comprehend API Operations | Required Permissions \(API Actions\) | Resources | 
| --- | --- | --- | 
| [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md) | comprehend:BatchDetectDominantLanguage | \* | 
| [BatchDetectEntities](API_BatchDetectEntities.md) | comprehend:BatchDetectEntities | \* | 
| [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md) | comprehend:BatchDetectKeyPhrases | \* | 
| [BatchDetectSentiment](API_BatchDetectSentiment.md) | comprehend:BatchDetectSentiment | \* | 
| [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) | comprehend:DescribeTopicsDetectionJob | \* | 
| [DetectDominantLanguage](API_DetectDominantLanguage.md) | comprehend:DetectDominantLanguage | \* | 
| [DetectEntities](API_DetectEntities.md) | comprehend:DetectEntities | \* | 
| [DetectKeyPhrases](API_DetectKeyPhrases.md) | comprehend:DetectKeyPhrases | \* | 
| [DetectSentiment](API_DetectSentiment.md) | comprehend:DetectSentiment | \* | 
| [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) | comprehend:ListTopicsDectectionJobs | \* | 
| [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) | comprehend:StartTopicsDetectionJob | \* | 
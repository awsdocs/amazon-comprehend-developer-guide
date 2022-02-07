# Amazon Comprehend API Permissions: Actions, Resources, and Conditions Reference<a name="comprehend-api-permissions-ref"></a>

Use the following table as a reference when setting up [Access Control](auth-and-access-control.md#access-control) and writing a permissions policy that you can attach to an IAM identity \(an identity\-based policy\)\. The list includes each Amazon Comprehend API operation, the corresponding action for which you can grant permissions to perform the action, and the AWS resource for which you can grant the permissions\. You specify the actions in the policy's `Action` field, and you specify the resource value in the policy's `Resource` field\. 

To express conditions, you can use AWS\-wide condition keys in your Amazon Comprehend policies\. For a complete list of AWS\-wide keys, see [Available Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

**Note**  
To specify an action, use the `comprehend:` prefix followed by the API operation name, for example, `comprehend:DetectEntities`\.

Use the scroll bars to see the rest of the table\.


**Amazon Comprehend API and Required Permissions for Actions**  

| Amazon Comprehend API Operations | Required Permissions \(API Actions\) | Resources | 
| --- | --- | --- | 
| [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md) | comprehend:BatchDetectDominantLanguage | \* | 
| [BatchDetectEntities](API_BatchDetectEntities.md) | comprehend:BatchDetectEntities | \* | 
| [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md) | comprehend:BatchDetectKeyPhrases | \* | 
| [BatchDetectSentiment](API_BatchDetectSentiment.md) | comprehend:BatchDetectSentiment | \* | 
| [BatchDetectSyntax](API_BatchDetectSyntax.md) | comprehend:BatchDetectSyntax | \* | 
| DescribeDominantLanguageDetectionJob | comprehend:DescribeDominantLanguageDetectionJob | \* | 
| DescribeEntitiesDetectionJob | comprehend:DescribeEntitiesDetectionJob | \* | 
| DescribeKeyPhrasesDetectionJob | comprehend:DescribeKeyPhrasesDetectionJob | \* | 
| DescribeSentimentDetectionJob | comprehend:DescribeSentimentDetectionJob | \* | 
| [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) | comprehend:DescribeTopicsDetectionJob | \* | 
| [DetectDominantLanguage](API_DetectDominantLanguage.md) | comprehend:DetectDominantLanguage | \* | 
| [DetectEntities](API_DetectEntities.md) | comprehend:DetectEntities | \* | 
| [DetectKeyPhrases](API_DetectKeyPhrases.md) | comprehend:DetectKeyPhrases | \* | 
| [DetectSentiment](API_DetectSentiment.md) | comprehend:DetectSentiment | \* | 
| [DetectSyntax](API_DetectSyntax.md) | comprehend:DetectSyntax | \* | 
| ListDominantLanguageDetectionJobs | comprehend:ListDominantLanguageDetectionJobs | \* | 
| ListEntitiesDetectionJobs | comprehend:ListEntitiesDetectionJobs | \* | 
| ListKeyPhrasesDetectionJobs | comprehend:ListKeyPhrasesDetectionJobs | \* | 
| ListSentimentDetectionJobs | comprehend:ListSentimentDetectionJobs | \* | 
| [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) | comprehend:ListTopicsDetectionJobs | \* | 
| StartDominantLanguageDetectionJob | comprehend:StartDominantLanguageDetectionJob | \* | 
| StartEntitiesDetectionJob | comprehend:StartEntitiesDetectionJob | \* | 
| StartKeyPhrasesDetectionJob | comprehend:StartKeyPhrasesDetectionJob | \* | 
| StartSentimentDetectionJob | comprehend:StartSentimentDetectionJob | \* | 
| [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) | comprehend:StartTopicsDetectionJob | \* | 
| StopDominantLanguageDetectionJob | comprehend:StopDominantLanguageDetectionJob | \* | 
| StopEntitiesDetectionJob | comprehend:StopEntitiesDetectionJob | \* | 
| StopKeyPhrasesDetectionJob | comprehend:StopKeyPhrasesDetectionJob | \* | 
| StopSentimentDetectionJob | comprehend:StopSentimentDetectionJob | \* | 
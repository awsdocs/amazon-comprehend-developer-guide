# Amazon Comprehend Medical API Permissions: Actions, Resources, and Conditions Reference<a name="comprehend-api-permissions-ref-med"></a>

Use the following table as a reference when setting up [Access Control](auth-and-access-control-med.md#access-control-med) and writing a permissions policy that you can attach to an IAM identity \(an identity\-based policy\)\. The list includes each Amazon Comprehend Medical API operation, the corresponding action for which you can grant permissions to perform the action, and the AWS resource for which you can grant the permissions\. You specify the actions in the policy's `Action` field, and you specify the resource value in the policy's `Resource` field\. 

To express conditions, you can use AWS condition keys in your Amazon Comprehend Medical policies\. For a complete list of keys, see [Available Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

**Note**  
To specify an action, use the `comprehendmedical:` prefix followed by the API operation name, for example, `comprehendmedical:DetectEntities`\.

If you see an expand arrow \(**↗**\) in the upper\-right corner of the table, you can open the table in a new window\. To close the window, choose the close button \(**X**\) in the lower\-right corner\.


**Amazon Comprehend Medical API and Required Permissions for Actions**  

| Amazon Comprehend Medical API Operations | Required Permissions \(API Actions\) | Resources | 
| --- | --- | --- | 
| [DescribeEntitiesDetectionV2Job](API_medical_DescribeEntitiesDetectionV2Job.md) | comprehendmedical:DescribeEntitiesDetectionV2Job | \* | 
| [DescribePHIDetectionJob](API_medical_DescribePHIDetectionJob.md) | comprehendmedical:DescribePHIDetectionJob | \* | 
| [DetectEntities](API_medical_DetectEntities.md) | comprehendmedical:DetectEntities | \* | 
| [DetectEntitiesV2](API_medical_DetectEntitiesV2.md) | comprehendmedical:DetectEntitiesV2 | \* | 
| [DetectPHI](API_medical_DetectPHI.md)  | comprehendmedical:DetectPHI | \* | 
| [ListEntitiesDetectionV2Jobs](API_medical_ListEntitiesDetectionV2Jobs.md)  | comprehendmedical:ListEntitiesDetectionV2Jobs | \* | 
| [ListPHIDetectionJobs](API_medical_ListPHIDetectionJobs.md)  | comprehendmedical:ListPHIDetectionJobs | \* | 
| [StartEntitiesDetectionV2Job](API_medical_StartEntitiesDetectionV2Job.md)  | comprehendmedical:StartEntitiesDetectionV2Job | \* | 
| [StartPHIDetectionJob](API_medical_StartPHIDetectionJob.md)  | comprehendmedical:StartPHIDetectionJob | \* | 
| [StopEntitiesDetectionV2Job](API_medical_StopEntitiesDetectionV2Job.md)  | comprehendmedical:StopEntitiesDetectionV2Job | \* | 
| [StopPHIDetectionJob](API_medical_StopPHIDetectionJob.md)  | comprehendmedical:StopPHIDetectionJob | \* | 
| [InferICD10CM](API_medical_InferICD10CM.md)  | comprehendmedical:InferICD10CM | \* | 
| [InferRxNorm](API_medical_InferRxNorm.md)  | comprehendmedical:InferRxNorm | \* | 
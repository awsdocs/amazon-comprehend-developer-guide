# Comprehend Medical API Permissions: Actions, Resources, and Conditions Reference<a name="comprehend-api-permissions-ref-med"></a>

Use the following table as a reference when setting up [Access Control](auth-and-access-control-med.md#access-control-med) and writing a permissions policy that you can attach to an IAM identity \(an identity\-based policy\)\. The list includes each Comprehend Medical API operation, the corresponding action for which you can grant permissions to perform the action, and the AWS resource for which you can grant the permissions\. You specify the actions in the policy's `Action` field, and you specify the resource value in the policy's `Resource` field\. 

To express conditions, you can use AWS\-wide condition keys in your Comprehend Medical policies\. For a complete list of AWS\-wide keys, see [Available Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

**Note**  
To specify an action, use the `comprehendmedical:` prefix followed by the API operation name, for example, `comprehendmedical:DetectEntities`\.

If you see an expand arrow \(**↗**\) in the upper\-right corner of the table, you can open the table in a new window\. To close the window, choose the close button \(**X**\) in the lower\-right corner\.


**Comprehend Medical API and Required Permissions for Actions**  

| Comprehend Medical API Operations | Required Permissions \(API Actions\) | Resources | 
| --- | --- | --- | 
| [DetectEntities](API_hera_DetectEntities.md) | comprehendmedical:DetectEntities | \* | 
| [DetectPHI](API_hera_DetectPHI.md)  | comprehendmedical:DetectPHI | \* | 
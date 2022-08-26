# PutResourcePolicy<a name="API_PutResourcePolicy"></a>

Attaches a resource\-based policy to a custom model\. You can use this policy to authorize an entity in another AWS account to import the custom model, which replicates it in Amazon Comprehend in their account\.

## Request Syntax<a name="API_PutResourcePolicy_RequestSyntax"></a>

```
{
   "PolicyRevisionId": "string",
   "ResourceArn": "string",
   "ResourcePolicy": "string"
}
```

## Request Parameters<a name="API_PutResourcePolicy_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [PolicyRevisionId](#API_PutResourcePolicy_RequestSyntax) **   <a name="comprehend-PutResourcePolicy-request-PolicyRevisionId"></a>
The revision ID that Amazon Comprehend assigned to the policy that you are updating\. If you are creating a new policy that has no prior version, don't use this parameter\. Amazon Comprehend creates the revision ID for you\.  
Type: String  
Length Constraints: Maximum length of 64\.  
Pattern: `[0-9A-Fa-f]+`   
Required: No

 ** [ResourceArn](#API_PutResourcePolicy_RequestSyntax) **   <a name="comprehend-PutResourcePolicy-request-ResourceArn"></a>
The Amazon Resource Name \(ARN\) of the custom model to attach the policy to\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier|entity-recognizer)/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: Yes

 ** [ResourcePolicy](#API_PutResourcePolicy_RequestSyntax) **   <a name="comprehend-PutResourcePolicy-request-ResourcePolicy"></a>
The JSON resource\-based policy to attach to your custom model\. Provide your JSON as a UTF\-8 encoded string without line breaks\. To provide valid JSON for your policy, enclose the attribute names and values in double quotes\. If the JSON body is also enclosed in double quotes, then you must escape the double quotes that are inside the policy:  
 `"{\"attribute\": \"value\", \"attribute\": [\"value\"]}"`   
To avoid escaping quotes, you can use single quotes to enclose the policy and double quotes to enclose the JSON names and values:  
 `'{"attribute": "value", "attribute": ["value"]}'`   
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 20000\.  
Pattern: `[\u0009\u000A\u000D\u0020-\u00FF]+`   
Required: Yes

## Response Syntax<a name="API_PutResourcePolicy_ResponseSyntax"></a>

```
{
   "PolicyRevisionId": "string"
}
```

## Response Elements<a name="API_PutResourcePolicy_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [PolicyRevisionId](#API_PutResourcePolicy_ResponseSyntax) **   <a name="comprehend-PutResourcePolicy-response-PolicyRevisionId"></a>
The revision ID of the policy\. Each time you modify a policy, Amazon Comprehend assigns a new revision ID, and it deletes the prior version of the policy\.  
Type: String  
Length Constraints: Maximum length of 64\.  
Pattern: `[0-9A-Fa-f]+` 

## Errors<a name="API_PutResourcePolicy_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** ResourceNotFoundException **   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

## Examples<a name="API_PutResourcePolicy_Examples"></a>

### Example resource\-based policy for a custom model<a name="API_PutResourcePolicy_Example_1"></a>

The following example shows a resource\-based policy for a custom model in Amazon Comprehend\. The policy allows an entity in another AWS account to import the model that the policy is attached to\. The policy specifies the authorized entity for the `Principal` attribute, and it specifies the ARN of the model version for the `Resource` attribute\.

#### <a name="w96aac57c17d155c15b3b5"></a>

```
{
  "Version": "2017-01-01",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "comprehend:ImportModel",
      "Resource": [
        "arn:aws:comprehend:us-west-2:111122223333:document-classifier/foo/version/*"
      ],
      "Principal": {
        "AWS": "arn:aws:iam::444455556666:root"
      }
    }
  ]
}
```

## See Also<a name="API_PutResourcePolicy_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/PutResourcePolicy) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/PutResourcePolicy) 
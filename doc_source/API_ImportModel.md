# ImportModel<a name="API_ImportModel"></a>

Creates a new custom model that replicates a source custom model that you import\. The source model can be in your AWS account or another one\.

If the source model is in another AWS account, then it must have a resource\-based policy that authorizes you to import it\.

The source model must be in the same AWS region that you're using when you import\. You can't import a model that's in a different region\.

## Request Syntax<a name="API_ImportModel_RequestSyntax"></a>

```
{
   "DataAccessRoleArn": "string",
   "ModelKmsKeyId": "string",
   "ModelName": "string",
   "SourceModelArn": "string",
   "Tags": [ 
      { 
         "Key": "string",
         "Value": "string"
      }
   ],
   "VersionName": "string"
}
```

## Request Parameters<a name="API_ImportModel_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [DataAccessRoleArn](#API_ImportModel_RequestSyntax) **   <a name="comprehend-ImportModel-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Management \(IAM\) role that allows Amazon Comprehend to use Amazon Key Management Service \(KMS\) to encrypt or decrypt the custom model\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 ** [ModelKmsKeyId](#API_ImportModel_RequestSyntax) **   <a name="comprehend-ImportModel-request-ModelKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt trained custom models\. The ModelKmsKeyId can be either of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Pattern: `^\p{ASCII}+$`   
Required: No

 ** [ModelName](#API_ImportModel_RequestSyntax) **   <a name="comprehend-ImportModel-request-ModelName"></a>
The name to assign to the custom model that is created in Amazon Comprehend by this import\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: No

 ** [SourceModelArn](#API_ImportModel_RequestSyntax) **   <a name="comprehend-ImportModel-request-SourceModelArn"></a>
The Amazon Resource Name \(ARN\) of the custom model to import\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier|entity-recognizer)/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: Yes

 ** [Tags](#API_ImportModel_RequestSyntax) **   <a name="comprehend-ImportModel-request-Tags"></a>
Tags to be associated with the custom model that is created by this import\. A tag is a key\-value pair that adds as a metadata to a resource used by Amazon Comprehend\. For example, a tag with "Sales" as the key might be added to a resource to indicate its use by the sales department\.  
Type: Array of [Tag](API_Tag.md) objects  
Required: No

 ** [VersionName](#API_ImportModel_RequestSyntax) **   <a name="comprehend-ImportModel-request-VersionName"></a>
The version name given to the custom model that is created by this import\. Version names can have a maximum of 256 characters\. Alphanumeric characters, hyphens \(\-\) and underscores \(\_\) are allowed\. The version name must be unique among all models with the same classifier name in the account/AWS Region\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: No

## Response Syntax<a name="API_ImportModel_ResponseSyntax"></a>

```
{
   "ModelArn": "string"
}
```

## Response Elements<a name="API_ImportModel_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ModelArn](#API_ImportModel_ResponseSyntax) **   <a name="comprehend-ImportModel-response-ModelArn"></a>
The Amazon Resource Name \(ARN\) of the custom model being imported\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier|entity-recognizer)/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?` 

## Errors<a name="API_ImportModel_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** KmsKeyValidationException **   
The KMS customer managed key \(CMK\) entered cannot be validated\. Verify the key and re\-enter it\.  
HTTP Status Code: 400

 ** ResourceInUseException **   
The specified resource name is already in use\. Use a different name and try your request again\.  
HTTP Status Code: 400

 ** ResourceLimitExceededException **   
The maximum number of resources per account has been exceeded\. Review the resources, and then try your request again\.  
HTTP Status Code: 400

 ** ResourceNotFoundException **   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 ** ResourceUnavailableException **   
The specified resource is not available\. Check the resource and try your request again\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

 ** TooManyTagsException **   
The request contains more tags than can be associated with a resource \(50 tags per resource\)\. The maximum number of tags includes both existing tags and those included in your current request\.   
HTTP Status Code: 400

## See Also<a name="API_ImportModel_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ImportModel) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ImportModel) 
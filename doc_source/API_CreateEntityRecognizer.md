# CreateEntityRecognizer<a name="API_CreateEntityRecognizer"></a>

Creates an entity recognizer using submitted files\. After your `CreateEntityRecognizer` request is submitted, you can check job status using the [DescribeEntityRecognizer](API_DescribeEntityRecognizer.md) API\. 

## Request Syntax<a name="API_CreateEntityRecognizer_RequestSyntax"></a>

```
{
   "[ClientRequestToken](#comprehend-CreateEntityRecognizer-request-ClientRequestToken)": "string",
   "[DataAccessRoleArn](#comprehend-CreateEntityRecognizer-request-DataAccessRoleArn)": "string",
   "[InputDataConfig](#comprehend-CreateEntityRecognizer-request-InputDataConfig)": { 
      "[Annotations](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-Annotations)": { 
         "[S3Uri](API_EntityRecognizerAnnotations.md#comprehend-Type-EntityRecognizerAnnotations-S3Uri)": "string"
      },
      "[Documents](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-Documents)": { 
         "[S3Uri](API_EntityRecognizerDocuments.md#comprehend-Type-EntityRecognizerDocuments-S3Uri)": "string"
      },
      "[EntityList](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-EntityList)": { 
         "[S3Uri](API_EntityRecognizerEntityList.md#comprehend-Type-EntityRecognizerEntityList-S3Uri)": "string"
      },
      "[EntityTypes](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-EntityTypes)": [ 
         { 
            "[Type](API_EntityTypesListItem.md#comprehend-Type-EntityTypesListItem-Type)": "string"
         }
      ]
   },
   "[LanguageCode](#comprehend-CreateEntityRecognizer-request-LanguageCode)": "string",
   "[RecognizerName](#comprehend-CreateEntityRecognizer-request-RecognizerName)": "string",
   "[Tags](#comprehend-CreateEntityRecognizer-request-Tags)": [ 
      { 
         "[Key](API_Tag.md#comprehend-Type-Tag-Key)": "string",
         "[Value](API_Tag.md#comprehend-Type-Tag-Value)": "string"
      }
   ],
   "[VolumeKmsKeyId](#comprehend-CreateEntityRecognizer-request-VolumeKmsKeyId)": "string",
   "[VpcConfig](#comprehend-CreateEntityRecognizer-request-VpcConfig)": { 
      "[SecurityGroupIds](API_VpcConfig.md#comprehend-Type-VpcConfig-SecurityGroupIds)": [ "string" ],
      "[Subnets](API_VpcConfig.md#comprehend-Type-VpcConfig-Subnets)": [ "string" ]
   }
}
```

## Request Parameters<a name="API_CreateEntityRecognizer_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-ClientRequestToken"></a>
 A unique identifier for the request\. If you don't set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-InputDataConfig"></a>
Specifies the format and location of the input data\. The S3 bucket containing the input data must be located in the same region as the entity recognizer being created\.   
Type: [EntityRecognizerInputDataConfig](API_EntityRecognizerInputDataConfig.md) object  
Required: Yes

 ** [LanguageCode](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-LanguageCode"></a>
 The language of the input documents\. All documents must be in the same language\. Only English \("en"\) is currently supported\.   
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: Yes

 ** [RecognizerName](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-RecognizerName"></a>
The name given to the newly created recognizer\. Recognizer names can be a maximum of 256 characters\. Alphanumeric characters, hyphens \(\-\) and underscores \(\_\) are allowed\. The name must be unique in the account/region\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: Yes

 ** [Tags](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-Tags"></a>
Tags to be associated with the entity recognizer being created\. A tag is a key\-value pair that adds as a metadata to a resource used by Amazon Comprehend\. For example, a tag with "Sales" as the key might be added to a resource to indicate its use by the sales department\.   
Type: Array of [Tag](API_Tag.md) objects  
Required: No

 ** [VolumeKmsKeyId](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-VolumeKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt data on the storage volume attached to the ML compute instance\(s\) that process the analysis job\. The VolumeKmsKeyId can be either of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Required: No

 ** [VpcConfig](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-VpcConfig"></a>
Configuration parameters for an optional private Virtual Private Cloud \(VPC\) containing the resources you are using for your custom entity recognizer\. For more information, see [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)\.   
Type: [VpcConfig](API_VpcConfig.md) object  
Required: No

## Response Syntax<a name="API_CreateEntityRecognizer_ResponseSyntax"></a>

```
{
   "[EntityRecognizerArn](#comprehend-CreateEntityRecognizer-response-EntityRecognizerArn)": "string"
}
```

## Response Elements<a name="API_CreateEntityRecognizer_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EntityRecognizerArn](#API_CreateEntityRecognizer_ResponseSyntax) **   <a name="comprehend-CreateEntityRecognizer-response-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*` 

## Errors<a name="API_CreateEntityRecognizer_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **KmsKeyValidationException**   
The KMS customer managed key \(CMK\) entered cannot be validated\. Verify the key and re\-enter it\.  
HTTP Status Code: 400

 **ResourceInUseException**   
The specified name is already in use\. Use a different name and try your request again\.  
HTTP Status Code: 400

 **ResourceLimitExceededException**   
The maximum number of recognizers per account has been exceeded\. Review the recognizers, perform cleanup, and then try your request again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

 **TooManyTagsException**   
The request contains more tags than can be associated with a resource \(50 tags per resource\)\. The maximum number of tags includes both existing tags and those included in your current request\.   
HTTP Status Code: 400

 **UnsupportedLanguageException**   
Amazon Comprehend can't process the language of the input text\. For all custom entity recognition APIs \(such as `CreateEntityRecognizer`\), only English is accepted\. For most other APIs, such as those for Custom Classification, Amazon Comprehend accepts text in all supported languages\. For a list of supported languages, see [Languages Supported in Amazon Comprehend](supported-languages.md)\.   
HTTP Status Code: 400

## See Also<a name="API_CreateEntityRecognizer_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/CreateEntityRecognizer) 
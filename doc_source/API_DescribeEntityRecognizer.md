# DescribeEntityRecognizer<a name="API_DescribeEntityRecognizer"></a>

Provides details about an entity recognizer including status, S3 buckets containing training data, recognizer metadata, metrics, and so on\.

## Request Syntax<a name="API_DescribeEntityRecognizer_RequestSyntax"></a>

```
{
   "[EntityRecognizerArn](#comprehend-DescribeEntityRecognizer-request-EntityRecognizerArn)": "string"
}
```

## Request Parameters<a name="API_DescribeEntityRecognizer_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [EntityRecognizerArn](#API_DescribeEntityRecognizer_RequestSyntax) **   <a name="comprehend-DescribeEntityRecognizer-request-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

## Response Syntax<a name="API_DescribeEntityRecognizer_ResponseSyntax"></a>

```
{
   "[EntityRecognizerProperties](#comprehend-DescribeEntityRecognizer-response-EntityRecognizerProperties)": { 
      "[DataAccessRoleArn](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-DataAccessRoleArn)": "string",
      "[EndTime](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-EndTime)": number,
      "[EntityRecognizerArn](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-EntityRecognizerArn)": "string",
      "[InputDataConfig](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-InputDataConfig)": { 
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
      "[LanguageCode](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-LanguageCode)": "string",
      "[Message](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-Message)": "string",
      "[RecognizerMetadata](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-RecognizerMetadata)": { 
         "[EntityTypes](API_EntityRecognizerMetadata.md#comprehend-Type-EntityRecognizerMetadata-EntityTypes)": [ 
            { 
               "[Type](API_EntityRecognizerMetadataEntityTypesListItem.md#comprehend-Type-EntityRecognizerMetadataEntityTypesListItem-Type)": "string"
            }
         ],
         "[EvaluationMetrics](API_EntityRecognizerMetadata.md#comprehend-Type-EntityRecognizerMetadata-EvaluationMetrics)": { 
            "[F1Score](API_EntityRecognizerEvaluationMetrics.md#comprehend-Type-EntityRecognizerEvaluationMetrics-F1Score)": number,
            "[Precision](API_EntityRecognizerEvaluationMetrics.md#comprehend-Type-EntityRecognizerEvaluationMetrics-Precision)": number,
            "[Recall](API_EntityRecognizerEvaluationMetrics.md#comprehend-Type-EntityRecognizerEvaluationMetrics-Recall)": number
         },
         "[NumberOfTestDocuments](API_EntityRecognizerMetadata.md#comprehend-Type-EntityRecognizerMetadata-NumberOfTestDocuments)": number,
         "[NumberOfTrainedDocuments](API_EntityRecognizerMetadata.md#comprehend-Type-EntityRecognizerMetadata-NumberOfTrainedDocuments)": number
      },
      "[Status](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-Status)": "string",
      "[SubmitTime](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-SubmitTime)": number,
      "[TrainingEndTime](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-TrainingEndTime)": number,
      "[TrainingStartTime](API_EntityRecognizerProperties.md#comprehend-Type-EntityRecognizerProperties-TrainingStartTime)": number
   }
}
```

## Response Elements<a name="API_DescribeEntityRecognizer_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EntityRecognizerProperties](#API_DescribeEntityRecognizer_ResponseSyntax) **   <a name="comprehend-DescribeEntityRecognizer-response-EntityRecognizerProperties"></a>
Describes information associated with an entity recognizer\.  
Type: [EntityRecognizerProperties](API_EntityRecognizerProperties.md) object

## Errors<a name="API_DescribeEntityRecognizer_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_DescribeEntityRecognizer_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeEntityRecognizer) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DescribeEntityRecognizer) 
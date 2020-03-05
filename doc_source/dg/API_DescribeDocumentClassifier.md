# DescribeDocumentClassifier<a name="API_DescribeDocumentClassifier"></a>

Gets the properties associated with a document classifier\.

## Request Syntax<a name="API_DescribeDocumentClassifier_RequestSyntax"></a>

```
{
   "[DocumentClassifierArn](#comprehend-DescribeDocumentClassifier-request-DocumentClassifierArn)": "string"
}
```

## Request Parameters<a name="API_DescribeDocumentClassifier_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [DocumentClassifierArn](#API_DescribeDocumentClassifier_RequestSyntax) **   <a name="comprehend-DescribeDocumentClassifier-request-DocumentClassifierArn"></a>
The Amazon Resource Name \(ARN\) that identifies the document classifier\. The [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation returns this identifier in its response\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

## Response Syntax<a name="API_DescribeDocumentClassifier_ResponseSyntax"></a>

```
{
   "[DocumentClassifierProperties](#comprehend-DescribeDocumentClassifier-response-DocumentClassifierProperties)": { 
      "[ClassifierMetadata](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-ClassifierMetadata)": { 
         "[EvaluationMetrics](API_ClassifierMetadata.md#comprehend-Type-ClassifierMetadata-EvaluationMetrics)": { 
            "[Accuracy](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-Accuracy)": number,
            "[F1Score](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-F1Score)": number,
            "[HammingLoss](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-HammingLoss)": number,
            "[MicroF1Score](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-MicroF1Score)": number,
            "[MicroPrecision](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-MicroPrecision)": number,
            "[MicroRecall](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-MicroRecall)": number,
            "[Precision](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-Precision)": number,
            "[Recall](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-Recall)": number
         },
         "[NumberOfLabels](API_ClassifierMetadata.md#comprehend-Type-ClassifierMetadata-NumberOfLabels)": number,
         "[NumberOfTestDocuments](API_ClassifierMetadata.md#comprehend-Type-ClassifierMetadata-NumberOfTestDocuments)": number,
         "[NumberOfTrainedDocuments](API_ClassifierMetadata.md#comprehend-Type-ClassifierMetadata-NumberOfTrainedDocuments)": number
      },
      "[DataAccessRoleArn](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-DataAccessRoleArn)": "string",
      "[DocumentClassifierArn](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-DocumentClassifierArn)": "string",
      "[EndTime](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-EndTime)": number,
      "[InputDataConfig](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-InputDataConfig)": { 
         "[LabelDelimiter](API_DocumentClassifierInputDataConfig.md#comprehend-Type-DocumentClassifierInputDataConfig-LabelDelimiter)": "string",
         "[S3Uri](API_DocumentClassifierInputDataConfig.md#comprehend-Type-DocumentClassifierInputDataConfig-S3Uri)": "string"
      },
      "[LanguageCode](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-LanguageCode)": "string",
      "[Message](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-Message)": "string",
      "[Mode](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-Mode)": "string",
      "[OutputDataConfig](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-OutputDataConfig)": { 
         "[KmsKeyId](API_DocumentClassifierOutputDataConfig.md#comprehend-Type-DocumentClassifierOutputDataConfig-KmsKeyId)": "string",
         "[S3Uri](API_DocumentClassifierOutputDataConfig.md#comprehend-Type-DocumentClassifierOutputDataConfig-S3Uri)": "string"
      },
      "[Status](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-Status)": "string",
      "[SubmitTime](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-SubmitTime)": number,
      "[TrainingEndTime](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-TrainingEndTime)": number,
      "[TrainingStartTime](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-TrainingStartTime)": number,
      "[VolumeKmsKeyId](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-VolumeKmsKeyId)": "string",
      "[VpcConfig](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-VpcConfig)": { 
         "[SecurityGroupIds](API_VpcConfig.md#comprehend-Type-VpcConfig-SecurityGroupIds)": [ "string" ],
         "[Subnets](API_VpcConfig.md#comprehend-Type-VpcConfig-Subnets)": [ "string" ]
      }
   }
}
```

## Response Elements<a name="API_DescribeDocumentClassifier_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DocumentClassifierProperties](#API_DescribeDocumentClassifier_ResponseSyntax) **   <a name="comprehend-DescribeDocumentClassifier-response-DocumentClassifierProperties"></a>
An object that contains the properties associated with a document classifier\.  
Type: [DocumentClassifierProperties](API_DocumentClassifierProperties.md) object

## Errors<a name="API_DescribeDocumentClassifier_Errors"></a>

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

## See Also<a name="API_DescribeDocumentClassifier_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribeDocumentClassifier) 
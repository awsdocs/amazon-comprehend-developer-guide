# DescribeDocumentClassifier<a name="API_DescribeDocumentClassifier"></a>

Gets the properties associated with a document classifier\.

## Request Syntax<a name="API_DescribeDocumentClassifier_RequestSyntax"></a>

```
{
   "DocumentClassifierArn": "string"
}
```

## Request Parameters<a name="API_DescribeDocumentClassifier_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ DocumentClassifierArn ](#API_DescribeDocumentClassifier_RequestSyntax) **   <a name="comprehend-DescribeDocumentClassifier-request-DocumentClassifierArn"></a>
The Amazon Resource Name \(ARN\) that identifies the document classifier\. The [ CreateDocumentClassifier ](API_CreateDocumentClassifier.md) operation returns this identifier in its response\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: Yes

## Response Syntax<a name="API_DescribeDocumentClassifier_ResponseSyntax"></a>

```
{
   "DocumentClassifierProperties": { 
      "ClassifierMetadata": { 
         "EvaluationMetrics": { 
            "Accuracy": number,
            "F1Score": number,
            "HammingLoss": number,
            "MicroF1Score": number,
            "MicroPrecision": number,
            "MicroRecall": number,
            "Precision": number,
            "Recall": number
         },
         "NumberOfLabels": number,
         "NumberOfTestDocuments": number,
         "NumberOfTrainedDocuments": number
      },
      "DataAccessRoleArn": "string",
      "DocumentClassifierArn": "string",
      "EndTime": number,
      "InputDataConfig": { 
         "AugmentedManifests": [ 
            { 
               "AnnotationDataS3Uri": "string",
               "AttributeNames": [ "string" ],
               "DocumentType": "string",
               "S3Uri": "string",
               "SourceDocumentsS3Uri": "string",
               "Split": "string"
            }
         ],
         "DataFormat": "string",
         "LabelDelimiter": "string",
         "S3Uri": "string",
         "TestS3Uri": "string"
      },
      "LanguageCode": "string",
      "Message": "string",
      "Mode": "string",
      "ModelKmsKeyId": "string",
      "OutputDataConfig": { 
         "KmsKeyId": "string",
         "S3Uri": "string"
      },
      "SourceModelArn": "string",
      "Status": "string",
      "SubmitTime": number,
      "TrainingEndTime": number,
      "TrainingStartTime": number,
      "VersionName": "string",
      "VolumeKmsKeyId": "string",
      "VpcConfig": { 
         "SecurityGroupIds": [ "string" ],
         "Subnets": [ "string" ]
      }
   }
}
```

## Response Elements<a name="API_DescribeDocumentClassifier_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ DocumentClassifierProperties ](#API_DescribeDocumentClassifier_ResponseSyntax) **   <a name="comprehend-DescribeDocumentClassifier-response-DocumentClassifierProperties"></a>
An object that contains the properties associated with a document classifier\.  
Type: [ DocumentClassifierProperties ](API_DocumentClassifierProperties.md) object

## Errors<a name="API_DescribeDocumentClassifier_Errors"></a>

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

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_DescribeDocumentClassifier_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeDocumentClassifier) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribeDocumentClassifier) 
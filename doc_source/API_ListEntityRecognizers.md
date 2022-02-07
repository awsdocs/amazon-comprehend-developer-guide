# ListEntityRecognizers<a name="API_ListEntityRecognizers"></a>

Gets a list of the properties of all entity recognizers that you created, including recognizers currently in training\. Allows you to filter the list of recognizers based on criteria such as status and submission time\. This call returns up to 500 entity recognizers in the list, with a default number of 100 recognizers in the list\.

The results of this list are not in any particular order\. Please get the list and sort locally if needed\.

## Request Syntax<a name="API_ListEntityRecognizers_RequestSyntax"></a>

```
{
   "Filter": { 
      "RecognizerName": "string",
      "Status": "string",
      "SubmitTimeAfter": number,
      "SubmitTimeBefore": number
   },
   "MaxResults": number,
   "NextToken": "string"
}
```

## Request Parameters<a name="API_ListEntityRecognizers_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListEntityRecognizers_RequestSyntax) **   <a name="comprehend-ListEntityRecognizers-request-Filter"></a>
Filters the list of entities returned\. You can filter on `Status`, `SubmitTimeBefore`, or `SubmitTimeAfter`\. You can only set one filter at a time\.  
Type: [EntityRecognizerFilter](API_EntityRecognizerFilter.md) object  
Required: No

 ** [MaxResults](#API_ListEntityRecognizers_RequestSyntax) **   <a name="comprehend-ListEntityRecognizers-request-MaxResults"></a>
 The maximum number of results to return on each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListEntityRecognizers_RequestSyntax) **   <a name="comprehend-ListEntityRecognizers-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListEntityRecognizers_ResponseSyntax"></a>

```
{
   "EntityRecognizerPropertiesList": [ 
      { 
         "DataAccessRoleArn": "string",
         "EndTime": number,
         "EntityRecognizerArn": "string",
         "InputDataConfig": { 
            "Annotations": { 
               "S3Uri": "string",
               "TestS3Uri": "string"
            },
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
            "Documents": { 
               "InputFormat": "string",
               "S3Uri": "string",
               "TestS3Uri": "string"
            },
            "EntityList": { 
               "S3Uri": "string"
            },
            "EntityTypes": [ 
               { 
                  "Type": "string"
               }
            ]
         },
         "LanguageCode": "string",
         "Message": "string",
         "ModelKmsKeyId": "string",
         "RecognizerMetadata": { 
            "EntityTypes": [ 
               { 
                  "EvaluationMetrics": { 
                     "F1Score": number,
                     "Precision": number,
                     "Recall": number
                  },
                  "NumberOfTrainMentions": number,
                  "Type": "string"
               }
            ],
            "EvaluationMetrics": { 
               "F1Score": number,
               "Precision": number,
               "Recall": number
            },
            "NumberOfTestDocuments": number,
            "NumberOfTrainedDocuments": number
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
   ],
   "NextToken": "string"
}
```

## Response Elements<a name="API_ListEntityRecognizers_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EntityRecognizerPropertiesList](#API_ListEntityRecognizers_ResponseSyntax) **   <a name="comprehend-ListEntityRecognizers-response-EntityRecognizerPropertiesList"></a>
The list of properties of an entity recognizer\.  
Type: Array of [EntityRecognizerProperties](API_EntityRecognizerProperties.md) objects

 ** [NextToken](#API_ListEntityRecognizers_ResponseSyntax) **   <a name="comprehend-ListEntityRecognizers-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListEntityRecognizers_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidFilterException **   
The filter specified for the operation is invalid\. Specify a different filter\.  
HTTP Status Code: 400

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_ListEntityRecognizers_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListEntityRecognizers) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ListEntityRecognizers) 
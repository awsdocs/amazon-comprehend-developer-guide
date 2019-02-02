# ListDocumentClassifiers<a name="API_ListDocumentClassifiers"></a>

Gets a list of the document classifiers that you have created\.

## Request Syntax<a name="API_ListDocumentClassifiers_RequestSyntax"></a>

```
{
   "[Filter](#comprehend-ListDocumentClassifiers-request-Filter)": { 
      "[Status](API_DocumentClassifierFilter.md#comprehend-Type-DocumentClassifierFilter-Status)": "string",
      "[SubmitTimeAfter](API_DocumentClassifierFilter.md#comprehend-Type-DocumentClassifierFilter-SubmitTimeAfter)": number,
      "[SubmitTimeBefore](API_DocumentClassifierFilter.md#comprehend-Type-DocumentClassifierFilter-SubmitTimeBefore)": number
   },
   "[MaxResults](#comprehend-ListDocumentClassifiers-request-MaxResults)": number,
   "[NextToken](#comprehend-ListDocumentClassifiers-request-NextToken)": "string"
}
```

## Request Parameters<a name="API_ListDocumentClassifiers_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListDocumentClassifiers_RequestSyntax) **   <a name="comprehend-ListDocumentClassifiers-request-Filter"></a>
Filters the jobs that are returned\. You can filter jobs on their name, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [DocumentClassifierFilter](API_DocumentClassifierFilter.md) object  
Required: No

 ** [MaxResults](#API_ListDocumentClassifiers_RequestSyntax) **   <a name="comprehend-ListDocumentClassifiers-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListDocumentClassifiers_RequestSyntax) **   <a name="comprehend-ListDocumentClassifiers-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListDocumentClassifiers_ResponseSyntax"></a>

```
{
   "[DocumentClassifierPropertiesList](#comprehend-ListDocumentClassifiers-response-DocumentClassifierPropertiesList)": [ 
      { 
         "[ClassifierMetadata](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-ClassifierMetadata)": { 
            "[EvaluationMetrics](API_ClassifierMetadata.md#comprehend-Type-ClassifierMetadata-EvaluationMetrics)": { 
               "[Accuracy](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-Accuracy)": number,
               "[F1Score](API_ClassifierEvaluationMetrics.md#comprehend-Type-ClassifierEvaluationMetrics-F1Score)": number,
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
            "[S3Uri](API_DocumentClassifierInputDataConfig.md#comprehend-Type-DocumentClassifierInputDataConfig-S3Uri)": "string"
         },
         "[LanguageCode](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-LanguageCode)": "string",
         "[Message](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-Message)": "string",
         "[Status](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-Status)": "string",
         "[SubmitTime](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-SubmitTime)": number,
         "[TrainingEndTime](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-TrainingEndTime)": number,
         "[TrainingStartTime](API_DocumentClassifierProperties.md#comprehend-Type-DocumentClassifierProperties-TrainingStartTime)": number
      }
   ],
   "[NextToken](#comprehend-ListDocumentClassifiers-response-NextToken)": "string"
}
```

## Response Elements<a name="API_ListDocumentClassifiers_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DocumentClassifierPropertiesList](#API_ListDocumentClassifiers_ResponseSyntax) **   <a name="comprehend-ListDocumentClassifiers-response-DocumentClassifierPropertiesList"></a>
A list containing the properties of each job returned\.  
Type: Array of [DocumentClassifierProperties](API_DocumentClassifierProperties.md) objects

 ** [NextToken](#API_ListDocumentClassifiers_ResponseSyntax) **   <a name="comprehend-ListDocumentClassifiers-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListDocumentClassifiers_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidFilterException**   
The filter specified for the `ListDocumentClassificationJobs` operation is invalid\. Specify a different filter\.  
HTTP Status Code: 400

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_ListDocumentClassifiers_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListDocumentClassifiers) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/ListDocumentClassifiers) 
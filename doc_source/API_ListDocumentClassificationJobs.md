# ListDocumentClassificationJobs<a name="API_ListDocumentClassificationJobs"></a>

Gets a list of the documentation classification jobs that you have submitted\.

## Request Syntax<a name="API_ListDocumentClassificationJobs_RequestSyntax"></a>

```
{
   "[Filter](#comprehend-ListDocumentClassificationJobs-request-Filter)": { 
      "[JobName](API_DocumentClassificationJobFilter.md#comprehend-Type-DocumentClassificationJobFilter-JobName)": "string",
      "[JobStatus](API_DocumentClassificationJobFilter.md#comprehend-Type-DocumentClassificationJobFilter-JobStatus)": "string",
      "[SubmitTimeAfter](API_DocumentClassificationJobFilter.md#comprehend-Type-DocumentClassificationJobFilter-SubmitTimeAfter)": number,
      "[SubmitTimeBefore](API_DocumentClassificationJobFilter.md#comprehend-Type-DocumentClassificationJobFilter-SubmitTimeBefore)": number
   },
   "[MaxResults](#comprehend-ListDocumentClassificationJobs-request-MaxResults)": number,
   "[NextToken](#comprehend-ListDocumentClassificationJobs-request-NextToken)": "string"
}
```

## Request Parameters<a name="API_ListDocumentClassificationJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListDocumentClassificationJobs_RequestSyntax) **   <a name="comprehend-ListDocumentClassificationJobs-request-Filter"></a>
Filters the jobs that are returned\. You can filter jobs on their names, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [DocumentClassificationJobFilter](API_DocumentClassificationJobFilter.md) object  
Required: No

 ** [MaxResults](#API_ListDocumentClassificationJobs_RequestSyntax) **   <a name="comprehend-ListDocumentClassificationJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListDocumentClassificationJobs_RequestSyntax) **   <a name="comprehend-ListDocumentClassificationJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListDocumentClassificationJobs_ResponseSyntax"></a>

```
{
   "[DocumentClassificationJobPropertiesList](#comprehend-ListDocumentClassificationJobs-response-DocumentClassificationJobPropertiesList)": [ 
      { 
         "[DataAccessRoleArn](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-DataAccessRoleArn)": "string",
         "[DocumentClassifierArn](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-DocumentClassifierArn)": "string",
         "[EndTime](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-EndTime)": number,
         "[InputDataConfig](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-InputDataConfig)": { 
            "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
            "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
         },
         "[JobId](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-JobId)": "string",
         "[JobName](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-JobName)": "string",
         "[JobStatus](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-JobStatus)": "string",
         "[Message](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-Message)": "string",
         "[OutputDataConfig](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-OutputDataConfig)": { 
            "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
         },
         "[SubmitTime](API_DocumentClassificationJobProperties.md#comprehend-Type-DocumentClassificationJobProperties-SubmitTime)": number
      }
   ],
   "[NextToken](#comprehend-ListDocumentClassificationJobs-response-NextToken)": "string"
}
```

## Response Elements<a name="API_ListDocumentClassificationJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DocumentClassificationJobPropertiesList](#API_ListDocumentClassificationJobs_ResponseSyntax) **   <a name="comprehend-ListDocumentClassificationJobs-response-DocumentClassificationJobPropertiesList"></a>
A list containing the properties of each job returned\.  
Type: Array of [DocumentClassificationJobProperties](API_DocumentClassificationJobProperties.md) objects

 ** [NextToken](#API_ListDocumentClassificationJobs_ResponseSyntax) **   <a name="comprehend-ListDocumentClassificationJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListDocumentClassificationJobs_Errors"></a>

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

## See Also<a name="API_ListDocumentClassificationJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListDocumentClassificationJobs) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/ListDocumentClassificationJobs) 
# EndpointFilter<a name="API_EndpointFilter"></a>

The filter used to determine which endpoints are returned\. You can filter jobs on their name, model, status, or the date and time that they were created\. You can only set one filter at a time\. 

## Contents<a name="API_EndpointFilter_Contents"></a>

 ** CreationTimeAfter **   <a name="comprehend-Type-EndpointFilter-CreationTimeAfter"></a>
Specifies a date after which the returned endpoint or endpoints were created\.  
Type: Timestamp  
Required: No

 ** CreationTimeBefore **   <a name="comprehend-Type-EndpointFilter-CreationTimeBefore"></a>
Specifies a date before which the returned endpoint or endpoints were created\.  
Type: Timestamp  
Required: No

 ** ModelArn **   <a name="comprehend-Type-EndpointFilter-ModelArn"></a>
The Amazon Resource Number \(ARN\) of the model to which the endpoint is attached\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier|entity-recognizer)/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: No

 ** Status **   <a name="comprehend-Type-EndpointFilter-Status"></a>
Specifies the status of the endpoint being returned\. Possible values are: Creating, Ready, Updating, Deleting, Failed\.  
Type: String  
Valid Values:` CREATING | DELETING | FAILED | IN_SERVICE | UPDATING`   
Required: No

## See Also<a name="API_EndpointFilter_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EndpointFilter) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EndpointFilter) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EndpointFilter) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EndpointFilter) 
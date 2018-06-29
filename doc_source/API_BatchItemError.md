# BatchItemError<a name="API_BatchItemError"></a>

Describes an error that occurred while processing a document in a batch\. The operation returns on `BatchItemError` object for each document that contained an error\.

## Contents<a name="API_BatchItemError_Contents"></a>

 **ErrorCode**   <a name="comprehend-Type-BatchItemError-ErrorCode"></a>
The numeric error code of the error\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **ErrorMessage**   <a name="comprehend-Type-BatchItemError-ErrorMessage"></a>
A text description of the error\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **Index**   <a name="comprehend-Type-BatchItemError-Index"></a>
The zero\-based index of the document in the input list\.  
Type: Integer  
Required: No

## See Also<a name="API_BatchItemError_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/BatchItemError) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/BatchItemError) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/BatchItemError) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/BatchItemError) 
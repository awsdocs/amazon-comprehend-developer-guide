# BatchDetectSentimentItemResult<a name="API_BatchDetectSentimentItemResult"></a>

The result of calling the [BatchDetectSentiment](API_BatchDetectSentiment.md) operation\. The operation returns one object for each document that is successfully processed by the operation\.

## Contents<a name="API_BatchDetectSentimentItemResult_Contents"></a>

 **Index**   
The zero\-based index of the document in the input list\.  
Type: Integer  
Required: No

 **Sentiment**   
The sentiment detected in the document\.  
Type: String  
Valid Values:` POSITIVE | NEGATIVE | NEUTRAL | MIXED`   
Required: No

 **SentimentScore**   
The level of confidence that Amazon Comprehend has in the accuracy of its sentiment detection\.  
Type: [SentimentScore](API_SentimentScore.md) object  
Required: No

## See Also<a name="API_BatchDetectSentimentItemResult_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/BatchDetectSentimentItemResult) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/BatchDetectSentimentItemResult) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/BatchDetectSentimentItemResult) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/BatchDetectSentimentItemResult) 
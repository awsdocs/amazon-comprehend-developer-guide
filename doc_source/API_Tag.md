# Tag<a name="API_Tag"></a>

A key\-value pair that adds as a metadata to a resource used by Amazon Comprehend\. For example, a tag with the key\-value pair ‘Department’:’Sales’ might be added to a resource to indicate its use by a particular department\. 

## Contents<a name="API_Tag_Contents"></a>

 ** Key **   <a name="comprehend-Type-Tag-Key"></a>
The initial part of a key\-value pair that forms a tag associated with a given resource\. For instance, if you want to show which resources are used by which departments, you might use “Department” as the key portion of the pair, with multiple possible values such as “sales,” “legal,” and “administration\.”   
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 128\.  
Required: Yes

 ** Value **   <a name="comprehend-Type-Tag-Value"></a>
 The second part of a key\-value pair that forms a tag associated with a given resource\. For instance, if you want to show which resources are used by which departments, you might use “Department” as the initial \(key\) portion of the pair, with a value of “sales” to indicate the sales department\.   
Type: String  
Length Constraints: Minimum length of 0\. Maximum length of 256\.  
Required: No

## See Also<a name="API_Tag_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/Tag) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/Tag) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/Tag) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/Tag) 
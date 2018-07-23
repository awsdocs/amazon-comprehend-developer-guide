# Detecting Syntax<a name="get-started-api-syntax"></a>

To parse text to extract the individual words and determine the parts of speech for each word, use the [DetectSyntax](API_DetectSyntax.md) operation\. To parse the syntax of up to 25 documents in a batch, use the [BatchDetectSyntax](API_BatchDetectSyntax.md) operation\. For more information, see [Using the Batch APIs](get-started-batch.md)\.

**Topics**
+ [Detecting Syntax Using the AWS Command Line Interface\.](#get-started-api-syntax-cli)
+ [Detecting Syntax Using the AWS SDK for Java](#get-started-api-syntax-java)
+ [Detecting Parts of Speech Using the AWS SDK for Python \(Boto\)](#get-started-api-pos-python)
+ [Detecting Syntax Using the AWS SDK for \.NET](#get-started-api-syntax-c-sharp)

## Detecting Syntax Using the AWS Command Line Interface\.<a name="get-started-api-syntax-cli"></a>

The following example demonstrates using the `DetectSyntax` operation with the AWS CLI\. This example specifies the language of the input text\. 

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\. 

```
aws comprehend detect-syntax \
   --region region \
   --language-code "en" \
   --text "It is raining today in Seattle."
```

Amazon Comprehend responds with the following:

```
{
    "SyntaxTokens": [
        {
            "Text": "It", 
            "EndOffset": 2, 
            "BeginOffset": 0, 
            "PartOfSpeech": {
                "Tag": "PRON", 
                "Score": 0.8389829397201538
            }, 
            "TokenId": 1
        }, 
        {
            "Text": "is", 
            "EndOffset": 5, 
            "BeginOffset": 3, 
            "PartOfSpeech": {
                "Tag": "AUX", 
                "Score": 0.9189288020133972
            }, 
            "TokenId": 2
        }, 
        {
            "Text": "raining", 
            "EndOffset": 13, 
            "BeginOffset": 6, 
            "PartOfSpeech": {
                "Tag": "VERB", 
                "Score": 0.9977611303329468
            }, 
            "TokenId": 3
        }, 
        {
            "Text": "today", 
            "EndOffset": 19, 
            "BeginOffset": 14, 
            "PartOfSpeech": {
                "Tag": "NOUN", 
                "Score": 0.9993606209754944
            }, 
            "TokenId": 4
        }, 
        {
            "Text": "in", 
            "EndOffset": 22, 
            "BeginOffset": 20, 
            "PartOfSpeech": {
                "Tag": "ADP", 
                "Score": 0.9999061822891235
            }, 
            "TokenId": 5
        }, 
        {
            "Text": "Seattle", 
            "EndOffset": 30, 
            "BeginOffset": 23, 
            "PartOfSpeech": {
                "Tag": "PROPN", 
                "Score": 0.9940338730812073
            }, 
            "TokenId": 6
        }, 
        {
            "Text": ".", 
            "EndOffset": 31, 
            "BeginOffset": 30, 
            "PartOfSpeech": {
                "Tag": "PUNCT", 
                "Score": 0.9999997615814209
            }, 
            "TokenId": 7
        }
    ]
}
```

## Detecting Syntax Using the AWS SDK for Java<a name="get-started-api-syntax-java"></a>

The following Java program detects the syntax of the input text\. You must specify the language of the input text\.

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectSyntaxRequest;
import com.amazonaws.services.comprehend.model.DetectSyntaxResult;
 
public class App
{
	public static void main( String[] args )
	{
 
		String text = "It is raining today in Seattle.";
		String region = "region"
 
		// Create credentials using a provider chain. For more information, see
		// https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html
		AWSCredentialsProvider awsCreds = DefaultAWSCredentialsProviderChain.getInstance();
 
		AmazonComprehend comprehendClient =
				AmazonComprehendClientBuilder.standard()
						.withCredentials(awsCreds)
						.withRegion(region)
						.build();
 
		// Call detectSyntax API
		System.out.println("Calling DetectSyntax");
		DetectSyntaxRequest detectSyntaxRequest = new DetectSyntaxRequest()
				.withText(text)
				.withLanguageCode("en");
		DetectSyntaxResult detectSyntaxResult = comprehendClient.detectSyntax(detectSyntaxRequest);
		detectSyntaxResult.getSyntaxTokens().forEach(System.out::println);
		System.out.println("End of DetectSyntax\n");
		System.out.println( "Done" );
	}
}
```

## Detecting Parts of Speech Using the AWS SDK for Python \(Boto\)<a name="get-started-api-pos-python"></a>

The following Python program detects the parts of speech in the input text\. You must specify the language of the input text\.

```
import boto3
import json
 
comprehend = boto3.client(service_name='comprehend', region_name='region')
text = "It is raining today in Seattle"
 
print('Calling DetectSyntax')
print(json.dumps(comprehend.detect_syntax(Text=text, LanguageCode='en'), sort_keys=True, indent=4))
print('End of DetectSyntax\n')
```

## Detecting Syntax Using the AWS SDK for \.NET<a name="get-started-api-syntax-c-sharp"></a>

The \.NET example in this section uses the [AWS SDK for \.NET](http://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](http://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS Guide for \.NET Developers](http://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

```
using System;
using Amazon.Comprehend;
using Amazon.Comprehend.Model;
 
namespace Comprehend
{
	class Program
	{
		static void Main(string[] args)
		{
			String text = "It is raining today in Seattle";
 
			AmazonComprehendClient comprehendClient = new AmazonComprehendClient(Amazon.RegionEndpoint.region);
 
			// Call DetectSyntax API
			Console.WriteLine("Calling DetectSyntax\n");
			DetectSyntaxRequest detectSyntaxRequest =  new DetectSyntaxRequest()
			{
				Text = text,
				LanguageCode = "en"
			};
			DetectSyntaxResponse detectSyntaxResponse = comprehendClient.DetectSyntax(detectSyntaxRequest);
			foreach (SyntaxToken s in detectSyntaxResponse.SyntaxTokens)
			Console.WriteLine("Text: {0}, PartOfSpeech: {1}, Score: {2}, BeginOffset: {3}, EndOffset: {4}",
					e.Text, e.PartOfSpeech, e.Score, e.BeginOffset, e.EndOffset);
			Console.WriteLine("Done");
		}
	}
}
```
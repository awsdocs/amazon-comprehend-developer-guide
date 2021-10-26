# Running Real\-Time Custom Classification<a name="cc-real-time-analysis"></a>

Once you've created an endpoint, you can run real\-time analysis using your custom model\. There are two different ways to run real\-time analysis from the console, shown below, as well as the CLI method\. 

**\(Procedure A\) To run real\-time analysis using a custom model \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Real\-time analysis**\.

1. Under **Input type**, choose **Custom** for **Analysis type**\. 

1. For **Select endpoint**, choose the endpoint that you want to use\. This endpoint is linked to a specific custom model\. 

1. Enter the text you want to analyze\. 

1. Choose **Analyze**\. The text analysis based on your custom model is displayed, along with a confidence assessment of the analysis\. 

**\(Procedure B\) To run real\-time analysis using a custom model \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Customization** and then choose **Custom classification**\.

1. From the **Classifiers** list, choose the name of the custom model for which you want to update the endpoint and follow the link\. The custom model details page is displayed\.

1. Navigate to the **Endpoints** list, choose the name of the endpoint you want to use for real\-time analysis and follow the link\. The endpoint details page is displayed\.

1. Choose **Use in real\-time analysis**\. 

1. For **Input text**, enter the text you want to analyze\. 

1. Choose **Analyze**\. The text analysis based on your custom model is displayed, along with a confidence assessment of the analysis\. 





**To run real\-time analysis using a custom model \(AWS CLI\)**

The following example demonstrates using the *ClassifyDocument* operation with the AWS CLI\. 

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend classify-document \
    --endpoint-arn arn:aws:comprehend:region:account-id:endpoint/endpoint name \
    --text 'From the Tuesday, April 16th, 1912 edition of The Guardian newspaper: The maiden voyage of the White Star liner Titanic, 
    the largest ship ever launched ended in disaster. The Titanic started her trip from Southampton for New York on Wednesday. Late 
    on Sunday night she struck an iceberg off the Grand Banks of Newfoundland. By wireless telegraphy she sent out signals of distress, 
    and several liners were near enough to catch and respond to the call.'
```

Amazon Comprehend responds with the following:

```
{
   "Classes": [ 
      { 
         "Name": "string",
         "Score": 0.9793661236763
      }
   ]
}
```
# Real\-time analysis for custom classification \(console\)<a name="custom-sync"></a>

After you build and train a custom classifier model, you can run real\-time \(synchronous\) analysis for custom classification\. Because the analysis is synchronous, you can build real\-time applications using a custom model\.

You create an endpoint to run real\-time analysis using a custom model\. An endpoint includes managed resources that makes your custom model available for real\-time inference\. The level of throughput assigned to an endpoint is measured in *Inference units*, each of which represents data throughput of 100 characters per second\. You can provision the endpoint with up to 10 inference units\. You can scale the endpoint throughput either up or down by updating the endpoint\. 

After you have completed your real\-time analysis, delete the endpoint because the charge for it continues as long as it's active\. You can create another endpoint when you are ready to run further real\-time analysis\.

For more information on endpoint cost, see [Amazon Comprehend Pricing](https://aws.amazon.com/comprehend/pricing/)\.

After you create an endpoint, you can monitor it with Amazon CloudWatch, update it to change its inference units, or delete it when you no longer need it\. For more information, see [Managing Amazon Comprehend endpoints](manage-endpoints.md)\.

**Topics**
+ [Creating an endpoint for custom classification](#create-endpoint)
+ [Running real\-time custom classification](#cc-real-time-analysis)

## Creating an endpoint for custom classification<a name="create-endpoint"></a>

You need to create an endpoint to run real\-time analysis using a custom model\. 

**To create an endpoint \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Endpoints** and choose the **Create endpoint** button\. A **Create endpoint** screen opens\.

1. Give the endpoint a name\. The name must be unique within the AWS Region and account\.

1. Choose a custom model you want to attach the new endpoint to\. From the dropdown, you can search by model name\.
**Note**  
You need to create a model before you can attach an endpoint to it\. If you don't have a model yet, go to **Custom classification** or **Custom entity recognition** to create one\. 

1. \(Optional\) To add a tag to the endpoint, enter a key\-value pair under **Tags** and choose **Add tag**\. To remove this pair before creating the endpoint, choose **Remove tag**

1. Enter the number of inference units \(IUs\) to assign to the endpoint\. Each unit represents a throughput of 100 characters per second for up to 2 documents per second\. 

1. \(Optional\) If you are creating a new endpoint, you have the option to use the IU estimator\. It can be difficult to understand how many inference units you require depending on the throughput or the number of characters you want to analyze per second— especially at scale\. This optional step can help you determine how many IUs to request\. 
**Note**  
The range for available IUs is 1 to 10\. The maximum characters you can analyze per second is 1000\. 

1. From the **Purchase summary**, review your estimated hourly, daily, and monthly endpoint cost\. 

1. Select the checkbox if you understand that you will be charged for the endpoint from the time it starts until it is deleted\.

1. Choose **Create endpoint**

**To create an endpoint \(AWS CLI\)**

The following example demonstrates using the *CreateEndpoint* operation with the AWS CLI\. 

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend create-endpoint \
    --desired-inference-units number of inference units \
    --endpoint-name endpoint name \
    --model-arn arn:aws:comprehend:region:account-id:model/example \
    --tags Key=My1stTag,Value=Value1
```

Amazon Comprehend responds with the following:

```
{
   "EndpointArn": "Arn"
}
```

## Running real\-time custom classification<a name="cc-real-time-analysis"></a>

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
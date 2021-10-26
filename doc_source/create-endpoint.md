# Creating an Endpoint for Custom Classification<a name="create-endpoint"></a>

Once you have a custom model created and trained, all you need is an endpoint to enable real\-time analysis using that model\. 

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
# Real\-time analysis for custom entity recognition \(console\)<a name="detecting-cer-real-time"></a>

With Amazon Comprehend, you can quickly detect custom entities in individual text documents by running real\-time analysis\. Unlike asynchronous batch jobs that analyze large documents or large sets of documents, real\-time analysis is useful for applications that process small bodies of text as they arrive\. For example, you can immediately detect custom entities in social media posts, support tickets, or customer reviews\.

Before you can detect custom entities, you must train a custom entity recognition model\. For more information about these models, see [Training recognizer models](training-recognizers.md)\. 



You create an endpoint to run real\-time analysis using a custom model\. After you create the endpoint, your custom model is available for real\-time analysis, and you can detect entities by using the Amazon Comprehend console, the Amazon Comprehend API, the AWS CLI, or the AWS SDKs\.

## Creating an endpoint for custom entity detection<a name="detecting-cer-real-time-create-endpoint"></a>

 You create an endpoint to make your custom model available for real\-time analysis\.

To meet your text processing needs, you assign *inference units* to the endpoint, and each unit allows a throughput of 100 characters per second for up to 2 documents per second\. You can then adjust the throughput up or down\. 

The cost of real\-time analysis is based on the throughput of an endpoint and the duration of time it is active\. For more information on endpoint cost, see [Amazon Comprehend Pricing](https://aws.amazon.com/comprehend/pricing/)\.

After you create an endpoint, you can monitor it with Amazon CloudWatch, update it to change its inference units, or delete it when you no longer need it\. For more information, see [Managing Amazon Comprehend endpoints](manage-endpoints.md)\.

### Creating an Endpoint with the Console<a name="detecting-cer-real-time-create-endpoint-console"></a>

**To create an endpoint \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Endpoints** and choose the **Create endpoint** button\. A **Create endpoint** screen opens\.

1. Give the endpoint a name\. The name must be unique within the AWS Region and account\.

1. Choose a custom model you want to attach the new endpoint to\. From the dropdown, you can search by model name\.
**Note**  
You need to create a model before you can attach an endpoint to it\. If you don't have a model yet, go to **Custom entity recognition** to create one\. 

1. \(Optional\) To add a tag to the endpoint, enter a key\-value pair under **Tags** and choose **Add tag**\. To remove this pair before creating the endpoint, choose **Remove tag**

1. Enter the number of inference units \(IUs\) to assign to the endpoint\. Each unit represents a throughput of 100 characters per second for up to 2 documents per second\. 

1. \(Optional\) If you are creating a new endpoint, you have the option to use the IU estimator\. It can be difficult to understand how many inference units you require depending on the throughput or the number of characters you want to analyze per second— especially at scale\. This optional step can help you determine how many IUs to request\. 
**Note**  
The range for IUs is 1 to 10\. The maximum characters you can analyze per second is 1000\. 

1. From the **Purchase summary**, review your estimated hourly, daily, and monthly endpoint cost\. 

1. Select the checkbox if you understand that you will be charged for the endpoint from the time it starts until it is deleted\.

1. Choose **Create endpoint**

### Creating an Endpoint with the AWS CLI<a name="detecting-cer-real-time-create-endpoint-examples"></a>

To create an endpoint by using the AWS CLI, use the `create-endpoint` command:

```
$ aws comprehend create-endpoint \
> --desired-inference-units number of inference units \
> --endpoint-name endpoint name \
> --model-arn arn:aws:comprehend:region:account-id:model/example \
> --tags Key=Key,Value=Value
```

If your command succeeds, Amazon Comprehend responds with the endpoint ARN:

```
{
   "EndpointArn": "Arn"
}
```

For more information about this command, its parameter arguments, and its output, see [https://docs.aws.amazon.com/cli/latest/reference/comprehend/create-endpoint.html](https://docs.aws.amazon.com/cli/latest/reference/comprehend/create-endpoint.html) in the AWS CLI Command Reference

## Running real\-time custom entity detection<a name="detecting-cer-real-time-run"></a>

After you create an endpoint for your custom entity recognizer model, you can run real\-time analysis to quickly detect entities in individual bodies of text\.

### Detecting entities with the console<a name="detecting-cer-real-time-run-console"></a>

Complete the following steps to detect custom entities in your text by using the Amazon Comprehend console\.

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Real\-time analysis**\.

1. In the **Input text** section, for **Analysis type**, choose **Custom**\. 

1. For **Select endpoint**, choose the endpoint that is associated with the entity\-detection model that you want to use\.

1. Under **Input text**, provide the text you want to analyze\.

1. Choose **Analyze**\. The text analysis based on your custom model is displayed, along with a confidence assessment of the analysis\. 

### Detecting entities with the AWS CLI<a name="detecting-cer-real-time-run-examples"></a>

To detect custom entities by using the AWS CLI, use the `detect-entities` command:

```
$ aws comprehend detect-entities \
> --endpoint-arn arn \
> --language-code en \
> --text  "Andy Jassy is the CEO of Amazon."
```

If your command succeeds, Amazon Comprehend responds with the analysis\. For each entity that Amazon Comprehend detects, it provides the entity type, text, location, and confidence score\.

For more information about this command, its parameter arguments, and its output, see [https://docs.aws.amazon.com/cli/latest/reference/comprehend/detect-entities.html](https://docs.aws.amazon.com/cli/latest/reference/comprehend/detect-entities.html) in the AWS CLI Command Reference
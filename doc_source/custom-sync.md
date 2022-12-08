# Real\-time analysis for custom classification \(console\)<a name="custom-sync"></a>

You can use the Amazon Comprehend console to run real\-time analysis using a custom classification model\.

You create an endpoint to run the real\-time analysis\. An endpoint includes managed resources that makes your custom model available for real\-time inference\.

For information about provisioning endpoint throughput, and the associated costs, see [Using Amazon Comprehend endpoints](using-endpoints.md)\.

**Topics**
+ [Creating an endpoint for custom classification](#create-endpoint)
+ [Running real\-time custom classification](#cc-real-time-analysis)

## Creating an endpoint for custom classification<a name="create-endpoint"></a>

**To create an endpoint \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Endpoints** and choose the **Create endpoint** button\. A **Create endpoint** screen opens\.

1. Give the endpoint a name\. The name must be unique within the current Region and account\.

1. Choose a custom model that you want to attach the new endpoint to\. From the dropdown, you can search by model name\.
**Note**  
You must create a model before you can attach an endpoint to it\. If you don't have a model yet, see [Training classification models](training-classifier-model.md)\.

1. \(Optional\) to add a tag to the endpoint, enter a key\-value pair under **Tags** and choose **Add tag**\. To remove this pair before creating the endpoint, choose **Remove tag**

1. Enter the number of inference units \(IUs\) to assign to the endpoint\. Each unit represents a throughput of 100 characters per second for up to two documents per second\. For information about how to provision IUs, see [Using Amazon Comprehend endpoints](using-endpoints.md)\. 

1. \(Optional\) If you are creating a new endpoint, you have the option to use the IU estimator\. Depending on the throughput, or the number of characters you want to analyze per second, it can be hard to know how many inference units you need\. This optional step can help you determine how the number of IUs to request\. 
**Note**  
The range for available IUs is 1–10\. The maximum characters that you can analyze per second is 1000\. 

1. From the **Purchase summary**, review your estimated hourly, daily, and monthly endpoint cost\. 

1. Select the check box if you understand that your account incurs charges for the endpoint from the time it starts until you delete it\.

1. Choose **Create endpoint**

## Running real\-time custom classification<a name="cc-real-time-analysis"></a>

Once you've created an endpoint, you can run real\-time analysis using your custom model\. There are two ways to run real\-time analysis from the console\. You can input text or upload a file, as shown in the following\. 

**To run real\-time analysis using a custom model \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Real\-time analysis**\.

1. Under **Input type**, choose **Custom** for **Analysis type**\. 

1. Under **Custom model type**, choose **Custom classification**\. 

1. For **Endpoint**, choose the endpoint that you want to use\. This endpoint links to a specific custom model\. 

1. To specify the input data for analysis, you can input text or upload a file\.
   + To enter text:

     1. Choose **Input text**\.

     1. Enter the text that you want to analyze\. 
   + To upload a file:

     1. Choose **Upload file** and enter the file name to upload\.

     1. \(Optional\) Under **Advanced read actions**, you can override the default actions for text extraction\. For details, see [Setting text extraction options](idp-set-textract-options.md)

1. Choose **Analyze**\. Amazon Comprehend analyzes the input data using your custom model\. Amazon Comprehend displays the discovered classes, along with a confidence assessment for each class\. 
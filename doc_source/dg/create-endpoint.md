# Creating an Endpoint<a name="create-endpoint"></a>

Once you have a custom model created and trained, all you need is an endpoint to enable real\-time analysis using that model\. 

**To create an endpoint \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Customization** and then choose **Custom Classification**\.

1. From the **Classifiers** list, choose the name of the custom model for which you want to create the endpoint and follow the link\. The **Endpoints** list on the custom model details page is displayed\.
**Note**  
Previously created endpoints are shown on the models detail page, along with the model with which they're associated\.

1. Under **Endpoints**, choose **Create endpoint**\. 

1. Give the endpoint a name\. The name must be unique within the AWS Region and account\.

1. Enter the number of inference units to assign to the endpoint\. Each unit represents a throughput of 100 characters per second for up to 2 documents per second\. You can assign up to a maximum of 10 inference units per endpoint\. 
**Note**  
The throughput you assign the endpoint affects your costs\. For more details, see [Amazon Comprehend Pricing](https://aws.amazon.com/comprehend/pricing)\.

1. \(Optional\) To add a tag to the endpoint, enter a key\-value pair under **Tags** and choose **Add tag**\. To remove this pair before creating the endpoint, choose **Remove tag**\.

1. Choose **Create endpoint**\. The **Endpoints** list is displayed, with the new endpoint showing **Creating**\. Once it shows **Ready**, the endpoint can be used for real\-time analysis\.

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
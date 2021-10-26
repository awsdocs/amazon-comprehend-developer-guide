# Real\-time Analysis with Custom Classification<a name="custom-sync"></a>

Once a custom model has been trained, you can create an endpoint to gain real\-time insights into your content\. While the process of training the custom model and creating the endpoint are asynchronous, these insights are provided synchronously\. This enables you to build real\-time applications using a custom model\.

An endpoint allows you to create an Amazon Comprehend\-managed resource that makes your custom model available for real\-time inference\. You have full control over the endpoint and specify the throughput in increments of 100 characters per second when you create it\. You can then adjust the throughput up or down to suit your needs\. The cost of real\-time analysis is based on the throughput of an endpoint and the duration of time it is active\. You then delete the endpoint when it's no longer needed\. All endpoint\-related costs cease when the endpoint is deleted\. For more information on endpoint cost, see [Amazon Comprehend Pricing](https://aws.amazon.com/comprehend/pricing/)\.

Your endpoint uses inference units as a measure of the throughput of a an endpoint\. Each inference unit provides you with a throughput of 100 characters per second for up to 2 documents per second\. You can scale the endpoint throughput either up or down by updating the endpoint\. If the endpoint is no longer required, you can delete the endpoint\.

Once you've created a custom model \(classifier\), you set up real\-time analysis with that custom model with the following process:

1. [Creating an Endpoint ](create-endpoint.md) 

1. [Running Real\-time Analysis with an Endpoint](cc-real-time-analysis.md) 

1. [Deleting an Endpoint](deleting-endpoint.md) 

## Managing your Endpoint<a name="endpoint-managing"></a>

Depending on your needs, you may find it necessary to adjust the throughput of your endpoint after creating it\. This can be achieved by updating the endpoint to increase or decrease the number of inference units provisioning it\. 

For more information on updating your endpoint, see [Updating an Endpoint ](update-endpoint.md)\.

You can detemine when to best adjust your endpoint's throughput by monitoring its use using the Cloudwatch console\.

**To monitor your endpoint using Cloudwatch**

1. Sign in to the and open the [Cloudwatch console](https://console.aws.amazon.com/cloudwatch/)\.

1. On the left, choose **Metrics**\.

1. Under **Metrics**, choose **Comprehend**\.  
![\[Cloudwatch metric\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/cloudwatch-metrics1.png)

   The Cloudwatch console will show the dimensions for the metrics\. 

1. Choose the EndpointArn dimension\.   
![\[Cloudwatch dimension\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/cloudwatch-metrics2.png)

The console will display **ConsumedInferenceUnits**, **ProvisionedInferenceUnits**, and **InferenceUtilization** for each of your endpoints\.

![\[Cloudwatch metric name\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/cloudwatch-metrics3.png)

Based on the Cloudwatch metrics, you can also set up autoscaling to automatically adjust the throughput of your endpoint\. For more information about using autoscaling with your endpoints, see [Autoscaling with Endpoints](comprehend-autoscaling.md)\.

**Important**  
It is important to remember that the cost for real\-time custom classification is based on both the throughput you set and the length of time the endpoint is active\. If you are no longer using the endpoint, or are not using it for an extended period, you should delete the endpoint to avoid incurring additional cost\. Alternately, you can set up a auto scaling policy to reduce your costs\. For more information, see [Autoscaling with Endpoints](comprehend-autoscaling.md)\.
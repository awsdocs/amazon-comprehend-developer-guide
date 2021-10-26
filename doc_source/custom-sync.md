# Real\-time Analysis with Custom Classification<a name="custom-sync"></a>

Once a custom model has been trained, you can create an endpoint to gain real\-time insights into your content\. While the process of training the custom model and creating the endpoint are asynchronous, these insights are provided synchronously\. This enables you to build real\-time applications using a custom model\.

An endpoint allows you to create an Amazon Comprehend\-managed resource that makes your custom model available for real\-time inference\. You have full control over the endpoint and specify the throughput in increments of 100 characters per second when you create it\. You can then adjust the throughput up or down to suit your needs\. The cost of real\-time analysis is based on the throughput of an endpoint and the duration of time it is active\. You then delete the endpoint when it's no longer needed\. All endpoint\-related costs cease when the endpoint is deleted\. For more information on endpoint cost, see [Amazon Comprehend Pricing](https://aws.amazon.com/comprehend/pricing/)\.

Your endpoint uses inference units as a measure of the throughput of a an endpoint\. Each inference unit provides you with a throughput of 100 characters per second for up to 2 documents per second\. You can scale the endpoint throughput either up or down by updating the endpoint\. If the endpoint is no longer required, you can delete the endpoint\.

**Topics**
+ [Creating an Endpoint for Custom Classification](create-endpoint.md)
+ [Running Real\-Time Custom Classification](cc-real-time-analysis.md)
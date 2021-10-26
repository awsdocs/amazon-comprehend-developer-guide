# Creating a Real\-time Custom Classification Request<a name="getting-started-console-endpoint"></a>

In addition to using the custom document classifier to run asynchronous jobs, you can also use it to run synchronous custom classification requests to gain real\-time insight into the categories in your document\. This requires first that you create an endpoint and set the level of data throughput for it, and then to run the real\-time analysis\.

**Note**  
Using real\-time analysis will result in additional cost to your account\. This cost is determined by how long the endpoint is operating and the level of throughput you determine\. 

The level of throughput assigned to an endpoint is measured in *Inference units*, each of which represents data throughput of 100 characters per second\. You can provision the endpoint with up to 10 inference units\. This level of throughput can be adjust to meet your needs by updating the endpoint\.

Once you have completed your real\-time analysis, you should delete the endpoint because the charge for it will continue as long as it's active\. You can easily create another endpoint whenever you need it\.

**To create an endpoint**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Customization** and then choose **Custom Classification**\.

1. From the **Classifiers** list, choose the name of the custom model for which you want to create the endpoint and follow the link\. The **Endpoints** list on the custom model details page is displayed\.
**Note**  
Previously created endpoints are shown on the models detail page, along with the model with which they're associated\.

1. Under **Endpoints**, choose **Create endpoint**\. 

1. Give the endpoint a name\. The name must be unique within the AWS Region and account\.

1. Enter the number of inference units to assign to the endpoint\. Each unit represents a throughput of 100 characters per second\. You can assign up to a maximum of 10 inference units per endpoint\.

1. \(Optional\) To add a tag to the endpoint, enter a key\-value pair under **Tags** and choose **Add tag**\. To remove this pair before creating the endpoint, choose **Remove tag**\.

1. Choose **Create endpoint**\. The **Endpoints** list is displayed, with the new endpoint showing **Creating**\. Once it shows **Ready**, the endpoint can be used for real\-time analysis\.

**To run a real\-time custom classification request**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Real\-time analysis**\.

1. Under **Input type**, choose **Custom** for **Analysis type**\. 

1. For **Select endpoint**, choose the endpoint that you want to use\. This endpoint is linked to a specific custom model\. 

1. Enter the text you want to analyze\. 

1. Choose **Analyze**\. The text analysis based on your custom model is displayed, along with a confidence assessment of the analysis\. 

**To update your endpoint**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Customization** and then choose **Custom classification**\.

1. From the **Classifiers** list, choose the name of the custom model for which you want to update the endpoint and follow the link\. The custom model details page is displayed\.

1. Navigate to the **Endpoints** list, choose the name of the endpoint you want to update and follow the link\. 

1. Choose **Edit**\.

1. Enter the updated number of inference units to assign to the endpoint\. Each unit represents a throughput of 100 characters per second\. You can assign up to a maximum of 10 inference units per endpoint\. 
**Note**  
The cost of using an endpoint is based on the amount of time operating and the throughput \(based on the number of inference units\. Increasing the number of inference units will thus increase the cost of operation\. For more information, see [Amazon Comprehend Pricing](https://aws.amazon.com/comprehend/pricing)\.

1. Choose **Edit endpoint**\. The endpoint details page is displayed\. 

1. Confirm that the endpoint is updating by choosing the model name from the breadcrumbs at the top of the page\. On the custom model details page, navigate to the **Endpoints** list and verify that it shows **Updating** next to the endpoint\. When the update is complete, it will show **Ready**\.

**To delete your endpoint**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Customization** and then choose **Custom classification**\.

1. From the **Classifiers** list, choose the name of the custom model associated with the endpoint you want to delete and follow the link\. The custom model details page is displayed\.

1. Navigate to the **Endpoints** list, choose the name of the endpoint to delete and follow the link\. 

1. Choose **Delete**\.
**Note**  
All endpoints associated with a custom model must be deleted before that model itself can be removed\.

1. Choose **Delete** again to confirm the deletion\. The custom model details page is displayed\. Confirm that the endpoint you deleted shows **deleting** next to it\. When it's deleted, the endpoint is removed from the **Endpoints** list\.
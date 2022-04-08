# Monitoring Amazon Comprehend endpoints<a name="manage-endpoints-monitor"></a>

Depending on your needs, you might need to adjust the throughput of your endpoint after creating it\. This can be achieved by updating the endpoint's inference units \(IUs\)\. When you edit an endpoint, you can add more IUs to an endpoint, or you can decrease the IUs\. A single endpoint can have 1 to 10 IUs\. 

For more information on updating your endpoint, see [Updating Amazon Comprehend endpoints](manage-endpoints-update.md)\.

To view all of your endpoints, see [Overview of Amazon Comprehend endpoints](manage-endpoints-overview.md)\.

You can determine how to best adjust your endpoint's throughput by monitoring its usage with the Amazon CloudWatch console\.

**Monitor your endpoint usage with CloudWatch**

1. Sign in to the AWS Management Console and open the [CloudWatch console](https://console.aws.amazon.com/cloudwatch/)\.

1. On the left, choose **Metrics** and select **All metrics**\.

1. Under **All metrics**, choose **Comprehend**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/cloudwatch-metrics1.png)

   The CloudWatch console will show the dimensions for the metrics\. 

1. Choose the **EndpointArn** dimension\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/cloudwatch-metrics2.png)

   The console displays **ConsumedInferenceUnits**, **ProvisionedInferenceUnits**, and **InferenceUtilization** for each of your endpoints\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/cloudwatch-metrics3.png)

1. Set the Statistic column for **ConsumedInferenceUnits** and **InferenceUtilization** to **Sum**\.

1. Set the Statistic column for **ProvisionedInferenceUnits** to **Average**\.

1. Change the Period column for all metrics to **1 Minute**\.

1. Select **InferenceUtilization** and select the arrow to move it to a separate **Y Axis**\.

   Your graph is ready for analysis\. 

     


Based on the CloudWatch metrics, you can also set up auto scaling to automatically adjust the throughput of your endpoint\. For more information about using auto scaling with your endpoints, see [Auto scaling with endpoints](comprehend-autoscaling.md)\. 


+ **ProvisionedInferenceUnits**\- This metric represents the number of average provisioned IUs at the time the request was made\. 
+ **ConsumedInferenceUnits** \- This is based on the usage of each request submitted to the service that was successfully processed\. This can be helpful when you compare what you're consuming against your provisioned IUs\. The value for this metric is calculated by taking the number of characters processed and dividing it by the number of characters that can be processed in a minute for 1 IU\. 
+ **InferenceUtilization** \- This is emitted per request\. This value is calculated by taking the consumed IUs defined in **ConsumedInferenceUnits** and dividing it by **ProvisionedInferenceUnits** and converting to a percentage out of 100\. 

**Note**  
 All of the metrics are emitted only for successful requests\. The metric won't appear if it's from a request that is throttled or fails with an internal server error or a customer error\. 
# Overview of Amazon Comprehend endpoints<a name="manage-endpoints-overview"></a>

The endpoints page from Amazon Comprehend console provides you a global view of your endpoints\. From the endpoints overview page, you can view all of your endpoints in one place to understand your endpoint usage versus your actual resource usage\. On the top right of the endpoints page you can specify what endpoints you want to view— all of them, custom classifier endpoints, or your custom entity endpoints\.

You can create, update, monitor, and delete endpoints from this page\. From the endpoints overview section, you can view a list of your endpoints, what custom models the endpoints are hosting, their creation time, the provisioned throughput, and the status of the endpoint\. When you select a specific endpoint from the endpoint overview table, the endpoint details are displayed\. 

Also, if you are a [AWS Business Support](https://aws.amazon.com/premiumsupport/plans/business/) or an [AWS Enterprise Support](https://aws.amazon.com/premiumsupport/plans/enterprise/) customer, you have access to Trusted Advisor checks specific to your endpoints\. To learn more, see [Using Trusted Advisor with Amazon Comprehend](manage-endpoints-trusted-advisor.md)\. For a complete list of checks and descriptions, see the [Trusted Advisor Best Practices](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/best-practice-checklist/)\.

For more information on managing your endpoints, see the following topics\. 
+ [Monitoring Amazon Comprehend endpoints](manage-endpoints-monitor.md)
+ [Updating Amazon Comprehend endpoints](manage-endpoints-update.md)
+ [Using Trusted Advisor with Amazon Comprehend](manage-endpoints-trusted-advisor.md)
+ [Deleting Amazon Comprehend endpoints](manage-endpoints-delete.md)

**Important**  
The cost for real\-time custom classification is based on both the throughput you set and the length of time the endpoint is active\. If you are no longer using the endpoint, or are not using it for an extended period, you should set up an auto scaling policy to reduce your costs\. Or, if you are no longer using an endpoint you can delete the endpoint to avoid incurring additional cost\. For more information, see [Auto scaling with endpoints](comprehend-autoscaling.md)\.
# Using Trusted Advisor with Amazon Comprehend<a name="manage-endpoints-trusted-advisor"></a>

AWS Trusted Advisor is an online tool that provides recommendations to help you provision your resources following AWS best practices\.

If you have a Basic or Developer Support plan, you can use the Trusted Advisor console to access all checks in the Service Limits category and six checks in the Security category\. If you have a Business or Enterprise Support Plan, you can use the Trusted Advisor console and the [AWS Support API](https://docs.aws.amazon.com/awssupport/latest/user/Welcome.html) to access all of the Trusted Advisor checks\.

Amazon Comprehend supports the following Trusted Advisor checks to help customers optimize the cost and the security of their Amazon Comprehend endpoints by providing actionable recommendations\.

## Amazon Comprehend Underutilized Endpoints<a name="manage-endpoints-trusted-advisor-underutilized-endpoints"></a>

The **Amazon Comprehend Underutilized Endpoints** check evaluates the throughput configuration of your endpoints\. This check alerts you when endpoints are not actively used for real\-time inference requests\. An endpoint that isn’t used for more than 15 days is considered underutilized\. All endpoints accrue charges based on both the throughput set and the length of time that the endpoint is active\. For the endpoint not used in last 15 days, we recommend that you define a scaling policy for the resource using [Application Autoscaling](https://docs.aws.amazon.com/autoscaling/application/userguide/what-is-application-auto-scaling.html)\. For an endpoint that hasn't been used in the last 30 days and does have an auto scaling policy defined we recommend that you use asynchronous inference or delete it\. These check results are automatically refreshed once every day and can be viewed under the **CostOptimization** category on the Trusted Advisor console\.

**To view the utilization status of all your endpoints and the corresponding recommendations**

1. Sign in to the AWS Management Console and open the Trusted Advisor console\.

1. In the navigation pane, choose the **CostOptimization** check category\.

1. On the category page, you can view the summary for each check category:
   + **Action recommended \(red\)** – Trusted Advisor recommends an action for the check\.
   + **Investigation recommended \(yellow\)** – Trusted Advisor detects a possible issue for the check\.
   + **No problems detected \(green\)** – Trusted Advisor doesn't detect an issue for the check\.
   + **Excluded items \(gray\)**– The number of checks that have excluded items, such as resources that you want a check to ignore\.

1. Choose **Amazon Comprehend Underutilized Endpoints check** to view the check description and the following details:
   + **Alert Criteria** – Describes the threshold when a check will change status\.
   + **Recommended Action** – Describes the recommended actions for this check\.
   + **Resource Table:** A table that lists your endpoint details and the status for each based on your recommendations\.

1. In the Resource table, if an endpoint is flagged with a **Investigation Recommended** because of a **Not used in last 30 days** warning, you can navigate to the Endpoint Details page on the Amazon Comprehend console\.
   + If you do not want to use this endpoint anymore, choose **Delete**\.
   + Choose **Delete** again to confirm the deletion\. The custom model details page is displayed\. Confirm that the endpoint you deleted shows **deleting** next to it\. When it has deleted, the endpoint is removed from the **Endpoints** list\. 

1. In the Resource table on the Trusted Advisor console, if an endpoint is flagged with an **Investigation Recommended** status because it hasn't been used in the last 15 days, and if it has AutoScaling disabled, you can navigate to the Endpoint Details page on the Amazon Comprehend console to adjust the endpoint\.
   + If you want to reduce the throughput configured for this endpoint, click **Edit**\. Enter the updated number of inference units to assign to the endpoint, then select the checkbox to acknowledge and then choose **Edit Endpoint\.** When the update is complete, the status will show as **Ready**\. 
   + If you want to automatically set endpoint provisioning on your endpoint instead of manually adjusting the throughput configuration, we recommend you use **Application Autoscaling**\.

1. In the Resource table on the Trusted Advisor console, if an endpoint is flagged with the **No problems detected** status because of the **Used Actively** reason, then it implies the endpoint is being utilized actively for running real\-time inference requests and no actions are recommended\.

Here's an example which shows the CostOptimization category view on the Trusted Advisor console:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/TA_cost_optimization_new.png)

## Amazon Comprehend Endpoint Access Risk<a name="manage-endpoints-trusted-advisor-endpoint-access-risk"></a>

The **Amazon Comprehend Endpoint Access Risk** check evaluates the AWS Key Management Service \(AWS KMS\) key permissions for an endpoint where the underlying model was encrypted using customer managed keys\. If the customer managed key is disabled or the key policy was changed to alter the allowed permissions for Amazon Comprehend, the endpoint availability might be affected\. If the key has been disabled, we recommend that you enable it\. If the key policy has been altered and you wish to continue using this endpoint, we recommend that you update the key policy\. The check results are automatically refreshed multiple times during the day\. This check can be viewed under the **Fault Tolerance** category of the Trusted Advisor console\.

**To view the AWS KMS key status of your Amazon Comprehend endpoints**

1. Sign in to the AWS Management Console and open the Trusted Advisor console\.

1. In the navigation pane, choose the **FaultTolerance** check category\.

1. On the category page, you can view the summary for each check category:
   + **Action recommended \(red\)** – Trusted Advisor recommends an action for the check\.
   + **Investigation recommended \(yellow\)**– Trusted Advisor detects a possible issue for the check\.
   + **No problems detected \(green\)** – Trusted Advisor doesn't detect an issue for the check\.
   + **Excluded items \(gray\)** – The number of checks that have excluded items, such as resources that you want a check to ignore\.

1. Choose Amazon Comprehend Endpoint Access Risk Check and you can view the check description and the following details:
   + **Alert Criteria**– Describes the threshold when a check will change status\.
   + **Recommended Action** – Describes the recommended actions for this check\.
   + **Resource Table:** A table that lists your KMS encrypted endpoint details and the status for each one based on if there are recommended actions\.

1. In the Resource table, if an endpoint is flagged with an **Action Recommended** status, select the link in the KMS KeyId column and you will be redirected to the corresponding AWS KMS key page\.
   + To enable a disabled AWS KMS key, choose **Key Actions**, and select **Enable**\.
   + If the Key Status is listed as **Enabled**, update the key policy by choosing **Switch to policy view** in the Key Policy section\. Edit the key policy document to provide the necessary permissions to Amazon Comprehend and then choose **Save changes**\. 

Here's an example of the FaultTolerance category view on the Trusted Advisor console:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/TA_fault_tolerance_checks_new.png)

These checks and their results can also be viewed by referring the Trusted Advisor section of the AWS Support API\.

To learn more about setting up alarms using CloudWatch, see: [Creating Trusted Advisor alarms using CloudWatch](https://docs.aws.amazon.com/awssupport/latest/user/cloudwatch-metrics-ta.html)\. For a full set of Trusted Advisor Best Practice Checks, see: [AWS Trusted Advisor best practice checklist\.](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/best-practice-checklist/)
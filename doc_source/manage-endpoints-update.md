# Updating an Endpoint with Amazon Comprehend<a name="manage-endpoints-update"></a>

Frequently, the level of throughput you need changes after creating an endpoint, or your first estimation of your needs changes\. When this happens, it may be necessary to update your endpoint to adjust the throughput up or down\. Throughput is governed by the number of inference units with which you've provisioned your endpoint\. Each inference unit represents a throughput of 100 characters per second for up to 2 documents per second\. You might also want to update the version of the model associated with the endpoint\. When you edit an endpoint, you can choose a different version of the model for the endpoint\.

It can also be helpful to add tags to your endpoint to help keep them organized\. This can also be done while updating your endpoint\. For more information on endpoints, see [Tagging your resources](tagging.md)

**To update an endpoint \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Endpoints**\.

1. From the **Classifiers** list, choose the name of the custom model from which you want to update the endpoint and follow the link\. The model details page displays\.

1. From the model details page, select the version details\. The endpoints list displays\. 

1. Select the endpoint checkbox for your endpoint\. At the top right of the endpoints table, select the **Actions** icon\.

1. Choose **Edit**\. You can update provisioned IUs and edit tags\. 

1. Save your changes\.

1. To edit the number of inference units with which the endpoint is provisioned, choose **Edit**\.

1. Enter the updated number of inference units to assign to the endpoint\. Each unit represents a throughput of 100 characters per second\. You can assign up to a maximum of 10 inference units per endpoint\. 
**Note**  
The cost of using an endpoint is based on the amount of time operating and the throughput \(based on the number of inference units\. Increasing the number of inference units will thus increase the cost of operation\. For more information, see [Amazon Comprehend Pricing](https://aws.amazon.com/comprehend/pricing)\.

1. Choose **Edit endpoint**\. The endpoint details page is displayed\. 

1. Confirm that the endpoint is updating by choosing the model name from the breadcrumbs at the top of the page\. On the custom model details page, navigate to the **Endpoints** list and verify that it shows **Updating** next to the endpoint\. When the update is complete, it will show **Ready**\.

   The following example demonstrates using the *UpdateEndpoint* operation with the AWS CLI\. 

   The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

   ```
   aws comprehend update-endpoint \
       --desired-inference-units updated number of inference units \
       --desired-model-arn arn:aws:comprehend:region:account-id:model type/model name \
       --desired-data-access-role-arn arn:aws:iam:account id:role/role name
       --endpoint-arn arn:aws:comprehend:region:account id:endpoint/endpoint name
   ```

   If the action is successful, Amazon Comprehend responds with an HTTP 200 response with an empty HTTP body\.

1. To edit the custom model attached to your endpoint, from the custom model details page, navigate to the **Endpoints** list\.

1. Select the endpoint you want to change and select **Edit**\.

1. From the endpoint settings page, under **Select classifier model** or **Select recognizer model** depending on your endpoint, you can search for a model in the dropdown\. Select the model you want\.

1. Under **Select version** you can search for the model version you want\. Select the version\.

1. Select **Edit endpoint** to save\. 
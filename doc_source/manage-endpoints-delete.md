# Deleting Amazon Comprehend endpoints<a name="manage-endpoints-delete"></a>

Once you no longer need your endpoint, you should delete it so that you stop incurring costs from it\. You can easily create another endpoint whenever you need it from the **Endpoints** section\.

**To delete an endpoint \(console\)**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. From the left menu, choose **Endpoints**\.

1. From the **Endpoints table** locate the endpoint you want to delete\. You can search or filter all of the endpoints to find the one you need\. 

1. Select the endpoint checkbox for the endpoint you want to delete\. At the top right of the endpoints table, select the **Actions** icon\.

1. Choose **Delete**\.

1. Choose **Delete** again to confirm the deletion\. The endpoints page is displayed\. Confirm that the endpoint you deleted shows **Deleting** next to it\. When it's deleted, the endpoint is removed from the **Endpoints** list\.





**To delete an endpoint \(AWS CLI\)**

The following example demonstrates using the *DeleteEndpoint* operation with the AWS CLI\. 

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend delete-endpoint \
    --endpoint-arn arn:aws:comprehend:region:account-id endpoint/endpoint name
```

If the action is successful, Amazon Comprehend responds with an HTTP 200 response with an empty HTTP body\.
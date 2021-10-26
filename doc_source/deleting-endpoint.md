# Deleting an Endpoint<a name="deleting-endpoint"></a>

Once you no longer need your endpoint, you should delete it so that you stop incurring costs from it\. You can easily create another endpoint whenever you need it\.

**To delete an endpoint \(console\)**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Customization** and then choose **Custom classification**\.

1. From the **Classifiers** list, choose the name of the custom model associated with the endpoint you want to delete and follow the link\. The custom model details page is displayed\.

1. Navigate to the **Endpoints** list, choose the name of the endpoint to delete and follow the link\. 

1. Choose **Delete**\.
**Note**  
All endpoints associated with a custom model must be deleted before that model itself can be removed\.

1. Choose **Delete** again to confirm the deletion\. The custom model details page is displayed\. Confirm that the endpoint you deleted shows **deleting** next to it\. When it's deleted, the endpoint is removed from the **Endpoints** list\.

**To delete an endpoint \(AWS CLI\)**

The following example demonstrates using the *DeleteEndpoint* operation with the AWS CLI\. 

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend delete-endpoint \
    --endpoint-arn arn:aws:comprehend:region:account-idendpoint/endpoint name
```

If the action is successful, responds with an HTTP 200 response with an empty HTTP body\.
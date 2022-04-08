# Permissions required for a custom asynchronous analysis job<a name="tagging-resources"></a>

**Important**  
If you have an IAM policy which restricts model access, you won't be able to complete an inference job with a custom model\. Your IAM policy should be updated to having a wildcard resource for a custom async analysis job\.

If you are using the [StartDocumentClassificationJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartDocumentClassificationJob.html) and [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartEntitiesDetectionJob.html) APIs, you need to update your IAM policy unless you are currently using wildcards as resources\. If you are using a [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartEntitiesDetectionJob.html) using a pretrained model this does not impact you and you don't need to make any changes\. 

The following example policy contains an **outdated** reference\. 

```
{
    "Action": [
        "comprehend:StartDocumentClassificationJob",
        "comprehend:StartEntitiesDetectionJob",
    ],
    "Resource": [
        "arn:aws:comprehend:us-east-1:123456789012:document-classifier/myClassifier",
        "arn:aws:comprehend:us-east-1:123456789012:entity-recognizer/myRecognizer"
    ],
    "Effect": "Allow"
}
```

This is the **updated** policy you need to use to sucessfully run StartDocumentClassificationJob and StartEntitiesDetectionJob\.

```
{
    "Action": [
        "comprehend:StartDocumentClassificationJob",
        "comprehend:StartEntitiesDetectionJob",
    ],
    "Resource": [
        "arn:aws:comprehend:us-east-1:123456789012:document-classifier/myClassifier",
        "arn:aws:comprehend:us-east-1:123456789012:document-classification-job/*",
        "arn:aws:comprehend:us-east-1:123456789012:entity-recognizer/myRecognizer",
        "arn:aws:comprehend:us-east-1:123456789012:entities-detection-job/*"
    ],
    "Effect": "Allow"
}
```
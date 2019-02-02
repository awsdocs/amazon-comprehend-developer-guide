# Guidelines and Limits<a name="guidelines-and-limits-med"></a>

## Important Notice<a name="important-notice-x1"></a>

Amazon Comprehend Medical is not a substitute for professional medical advice, diagnosis, or treatment\. Amazon Comprehend Medical provides confidence scores that indicate the level of confidence in the accuracy of the detected entities\. You should identify the right confidence threshold for your use case, and use high confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately\-trained human reviewers\. For example, Amazon Comprehend Medical should not be used in patient care scenarios without trained medical professionals reviewing results for accuracy and exercising their medical judgment\.

Keep in mind the following information when using Comprehend Medical\.

## Supported Regions<a name="limits-regions-med"></a>

For a list of AWS Regions where Comprehend Medical is available, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#comprehend-med_region) in the *Amazon Web Services General Reference*\.

## Throttling<a name="limits-throttling-med"></a>

For information about throttling for Comprehend Medical and to request a limit increase, see [ Amazon Comprehend Limits ](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_amazon_comprehend_medical) **Amazon Comprehend Medical Limits** in the *Amazon Web Services General Reference*\. 

## Overall Limits<a name="limits-all-med"></a>

All Comprehend Medical operations have the following limits:


| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Document size \(UTF\-8 characters\) | 20,000 bytes | 

Comprehend Medical processes one block of each text document at a time, synchronously\. Only documents in English \(EN\) are supported\.
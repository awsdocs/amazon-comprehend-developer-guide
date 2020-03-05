# Guidelines and Quotas<a name="guidelines-and-limits-med"></a>

## Important Notice<a name="important-notice-x1"></a>

Amazon Comprehend Medical is not a substitute for professional medical advice, diagnosis, or treatment\. Amazon Comprehend Medical provides confidence scores that indicate the level of confidence in the accuracy of the detected entities\. Identify the right confidence threshold for your use case, and use high confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately trained human reviewers\. Use Amazon Comprehend Medical in patient care scenarios only after trained medical professionals have reviewed results for accuracy and sound medical judgment\.

Keep in mind the following information when using Amazon Comprehend Medical\.

## Supported Regions<a name="limits-regions-med"></a>

For a list of AWS Regions where Amazon Comprehend Medical is available, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#comprehend-med_region) in the *Amazon Web Services General Reference*\.

## Throttling<a name="limits-throttling-med"></a>

For information about throttling and quotas for Amazon Comprehend Medical, and to request a quota increase, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html )\. 

## Overall Quotas<a name="limits-all-med"></a>

Character encoding for Amazon Comprehend Medical is in UTF\-8\. All Amazon Comprehend Medical operations have the following quotas:


| Description | Quota | 
| --- | --- | 
| Maximum document size \(UTF\-8 characters\) for DetectEntity and DetectPHI operations\. | 20,000 bytes | 
| Maximum size of batch jobs \(all files\) | 10 Gb | 
| Minimum size of batch jobs \(all files\) | 1 byte | 
| Maximum individual file size for batch jobs | 40 Kb | 
| Maximum number of files for batch jobs | 5 million | 

Amazon Comprehend Medical processes one block of each text document at a time, synchronously\. Only documents in English \(EN\) are supported\.
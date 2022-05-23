# Labeling PII entities<a name="how-pii-labels"></a>

When you run PII detection, Amazon Comprehend returns the labels of identified PII entity types\. For example, if you submit the following input text to Amazon Comprehend:

*Hello Paulo Santos\. The latest statement for your credit card account 1111\-0000\-1111\-0000 was mailed to 123 Any Street, Seattle, WA 98109\.*

The output includes labels that represent PII entity types along with a confidence score of the accuracy\. In this case, the document text "Paul Santos", "1111\-0000\-1111\-0000" and "123 Any Street, Seattle, WA 98109" generate the labels `NAME`, `CREDIT_DEBIT_NUMBER`, and `ADDRESS` respectively as PII entity types\. For more information about supported entity types, see [PII universal entity types](how-pii.md#how-pii-types)\.

Amazon Comprehend provides the following information for each label:
+ The label name of the PII entity type\.
+ A score that estimates the probability that the detected text is labeled as a PII entity type\.

The input text example above results in the following JSON output\.

```
{
    "Labels": [
        {
            "Name": "NAME",
            "Score": 0.9149109721183777
        },
        {
            "Name": "CREDIT_DEBIT_NUMBER",
            "Score": 0.5698626637458801
        }
         {
            "Name": "ADDRESS",
            "Score": 0.9951046109199524
        }
    ]
}
```
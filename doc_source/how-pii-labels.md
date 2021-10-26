# Label Documents with Personally Identifiable Information \(PII\)<a name="how-pii-labels"></a>

You can use Amazon Comprehend to check for the presence of personally identifiable information \(PII\) in your text document, which refers to entity types representing personal data that could be used to identify an individual, such as name, address, bank account number, or phone number\. If PII is found in your text document, Amazon Comprehend returns the labels of identified PII entity types\. 

For example, you can label a document with PII by submitting the following input text to Amazon Comprehend:

*Hello Paulo Santos\. The latest statement for your credit card account 1111\-0000\-1111\-0000 was mailed to 123 Any Street, Seattle, WA 98109\.*

When Amazon Comprehend completes its analysis, it returns output that labels the document with PII\.

For example, the output includes labels that represent PII entity types along with a confidence score of the accuracy\. In this case, the document text "Paul Santos", "1111\-0000\-1111\-0000" and "123 Any Street, Seattle, WA 98109" are represented by the labels `NAME`, `CREDIT_DEBIT_NUMBER`, and `ADDRESS` respectively as PII entity types\. For more information about supported entity types, see [PII Entity Types](how-pii.md#how-pii-types)\.

## Label Documents with PII Entity Types<a name="how-pii-label-doc"></a>

To label documents with PII, submit a [ ContainsPiiEntities ](API_ContainsPiiEntities.md) request, and include the input text in your request body\. Your input text can include up to 50,000 bytes of UTF\-8 encoded characters\. Amazon Comprehend returns a list of labels of identified PII entity types as shown by the following example response:

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

Amazon Comprehend provides the following for each label:
+ The label name of the PII entity type\.
+ A score that estimates the probability that the detected text is labeled as a PII entity type\.
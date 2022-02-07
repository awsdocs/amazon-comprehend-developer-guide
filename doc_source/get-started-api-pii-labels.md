# Labeling Documents with Personally Identifiable Information \(PII\)<a name="get-started-api-pii-labels"></a>

To label documents with personally identifiable information \(PII\), use the Amazon Comprehend [ContainsPiiEntities](API_ContainsPiiEntities.md) operation\.

## Labeling Documents with PII Using the AWS Command Line Interface<a name="get-started-api-pii-label-cli"></a>

The following example uses the `ContainsPiiEntities` operation with the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend contains-pii-entities \
--text "Hello Paul Santos. The latest statement for your credit card \
account 1111-0000-1111-0000 was mailed to 123 Any Street, Seattle, WA \
 98109." \
--language-code en
```

Amazon Comprehend responds with the following:

```
{
    "Labels": [
        {
            "Name": "NAME",
            "Score": 0.9149109721183777
        },
        {
            "Name": "CREDIT_DEBIT_NUMBER",
            "Score": 0.8905550241470337
        }
         {
            "Name": "ADDRESS",
            "Score": 0.9951046109199524
        }
    ]
}
```
# PII real\-time analysis \(API\)<a name="realtime-pii-api"></a>

Amazon Comprehend provides real\-time synchronous API operations to analyze personally identifiable information \(PII\) in a document\.

**Topics**
+ [Locating PII real\-time entities \(API\)](#realtime-pii-api-locate)
+ [Labeling PII real\-time entities \(API\)](#realtime-pii-api-labels)

## Locating PII real\-time entities \(API\)<a name="realtime-pii-api-locate"></a>

To locate PII in a single document, you can use the Amazon Comprehend [DetectPiiEntities](API_DetectPiiEntities.md) operation\. Your input text can include up to 5,000 bytes of UTF\-8 encoded characters\. 

### Locating PII using \(CLI\)<a name="realtime-pii-api-cli"></a>

The following example uses the `DetectPiiEntities` operation with the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend detect-pii-entities \
  --text "Hello Paul Santos. The latest statement for your credit card \
  account 1111-0000-1111-0000 was mailed to 123 Any Street, Seattle, WA \
   98109." \
  --language-code en
```

Amazon Comprehend responds with the following:

```
{
      "Entities": [
          {
              "Score": 0.9999669790267944,
              "Type": "NAME",
              "BeginOffset": 6,
              "EndOffset": 18
          },
          {
              "Score": 0.8905550241470337,
              "Type": "CREDIT_DEBIT_NUMBER",
              "BeginOffset": 69,
              "EndOffset": 88
          },
          {
              "Score": 0.9999889731407166,
              "Type": "ADDRESS",
              "BeginOffset": 103,
              "EndOffset": 138
          }
      ]
  }
```

## Labeling PII real\-time entities \(API\)<a name="realtime-pii-api-labels"></a>

You can use real\-time synchronous API operations to return the labels of identified PII entity types\. For more information, see [Labeling PII entities](how-pii-labels.md)\.

### Labeling PII entities \(CLI\)<a name="realtime-pii-api-label-cli"></a>

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
# Analyzing Documents Using the Console<a name="get-started-console-analysis"></a>

The Amazon Comprehend console enables you to analyze the contents of documents up to 5,000 characters long\. The results are shown in the console so that you can review the analysis\.

To start analyzing documents, sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

You can replace the sample text with your own text either in English or one of the other languages supported by Amazon Comprehend and then choose **Analyze** to get an analysis of your text\. Below the text being analyzed, the **Results** pane shows more information about the text\. 

## Entities<a name="console-entities"></a>

The **Entities** tab lists each entity, its category, and the level of confidence that Amazon Comprehend has detected in the input text\. The results are color\-coded to indicate different entity types such as organizations, locations, dates, and persons\. For more information, see [Detect Entities](how-entities.md)\.

![\[Amazon Comprehend entities analysis\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-entities.png)

## Key phrases<a name="console-key-phrases"></a>

The **Key phrases** tab lists key noun phrases that Amazon Comprehend detected in the input text and the associated confidence level\. For more information, see [Detect Key Phrases](how-key-phrases.md)\.

![\[The Key phrases tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-key-phrases.png)

## Language<a name="console-language"></a>

The **Language** tab shows the dominant language of the text and Amazon Comprehend's level of confidence that it has detected the dominant language correctly\. Amazon Comprehend can recognize 100 languages\. For more information, see [Detect the Dominant Language](how-languages.md)\.

![\[The Language tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-language.png)

## PII<a name="console-pii"></a>

The **PII** tab lists entities in your input text that contain personally identifiable information \(PII\)\. A PII entity is a textual reference to personal data that could be used to identify an individual, such as an address, bank account number, or phone number\. For more information, see [Detect Personally Identifiable Information \(PII\)](how-pii.md)\.

The **PII** tab provides two analysis modes: 
+ Offsets
+ Labels

### Offsets<a name="console-pii-offsets"></a>

The **Offsets** analysis mode identifies the location of PII in your text documents\. For more information, see [Locate PII Entities](how-pii.md#how-pii-locate)\. 

![\[The PII offsets analysis mode.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-pii.png)

### Labels<a name="console-pii-labels"></a>

The **Labels** analysis mode checks for the presence of PII in your text document and returns the labels of identified PII entity types\. For more information, see [Label Documents with PII Entity Types](how-pii-labels.md#how-pii-label-doc)\. 

![\[The PII labels analysis mode.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-pii-labels.png)

## Sentiment<a name="console-sentiment"></a>

The **Sentiment** tab shows the overall emotional sentiment of the text\. Sentiment can be rated neutral, positive, negative, or mixed\. In this case, each emotional sentiment has a confidence rating, providing an estimate by Amazon Comprehend for that sentiment being dominant\. For more information, see [Determine Sentiment](how-sentiment.md)\.

![\[The Sentiment tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-sentiment.png)

## Syntax<a name="console-syntax"></a>

The **Syntax** tab shows a breakdown of each element in the text, along with its part of speech and the associated confidence score\. For more information, see [Analyze Syntax](how-syntax.md)\.

![\[The Syntax tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-syntax.png)
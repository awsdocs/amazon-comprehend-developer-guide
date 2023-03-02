# Real\-time analysis using the built\-in models<a name="realtime-console-analysis"></a>

You can use the Amazon Comprehend console to run real\-time analysis of a UTF\-8 encoded text document\. The document can be English or one of the other languages supported by Amazon Comprehend\. The results are shown in the console so that you can review the analysis\.

To start analyzing documents, sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

You can replace the sample text with your own text and then choose **Analyze** to get an analysis of your text\. Below the text being analyzed, the **Results** pane shows more information about the text\. 

**Run real\-time analysis using the built\-in model**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. From the left menu, choose **Real\-time analysis**\.

1. Under **Input type**, choose **Built\-in** for **Analysis type**\. 

1. Enter the text you want to analyze\. 

1. Choose **Analyze**\. The console displays the text analysis results in the **Insights** panel\. The **Insights** panel includes a tab for each of the insight types\. The following sections describe the results for insight type\. 

**Topics**
+ [Entities](#realtime-analysis-console-entities)
+ [Key phrases](#realtime-analysis-console-key-phrases)
+ [Language](#realtime-analysis-console-language)
+ [Personally identifiable information \(PII\)](#realtime-analysis-console-pii)
+ [Sentiment](#realtime-analysis-console-sentiment)
+ [Targeted sentiment](#realtime-analysis-console-targeted-sentiment)
+ [Syntax](#realtime-analysis-console-syntax)

## Entities<a name="realtime-analysis-console-entities"></a>

The **Entities** tab lists each entity, its category, and the level of confidence that Amazon Comprehend has detected in the input text\. The results are color\-coded to indicate different entity types such as organizations, locations, dates, and persons\. For more information, see [Entities](how-entities.md)\.

![\[Amazon Comprehend entities analysis\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-entities.png)

## Key phrases<a name="realtime-analysis-console-key-phrases"></a>

The **Key phrases** tab lists key noun phrases that Amazon Comprehend detected in the input text and the associated confidence level\. For more information, see [Key phrases](how-key-phrases.md)\.

![\[The Key phrases tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-key-phrases.png)

## Language<a name="realtime-analysis-console-language"></a>

The **Language** tab shows the dominant language of the text and Amazon Comprehend's level of confidence that it has detected the dominant language correctly\. Amazon Comprehend can recognize 100 languages\. For more information, see [Dominant language](how-languages.md)\.

![\[The Language tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-language.png)

## Personally identifiable information \(PII\)<a name="realtime-analysis-console-pii"></a>

The **PII** tab lists entities in your input text that contain personally identifiable information \(PII\)\. A PII entity is a textual reference to personal data that could be used to identify an individual, such as an address, bank account number, or phone number\. For more information, see [Detecting PII entities](how-pii.md)\.

The **PII** tab provides two analysis modes: 
+ Offsets
+ Labels

### Offsets<a name="realtime-analysis-console-pii-offsets"></a>

The **Offsets** analysis mode identifies the location of PII in your text documents\. For more information, see [Locate PII entities](how-pii.md#how-pii-locate)\. 

![\[The PII offsets analysis mode.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-pii.png)

### Labels<a name="realtime-analysis-console-pii-labels"></a>

The **Labels** analysis mode checks for the presence of PII in your text document and returns the labels of identified PII entity types\. For more information, see [Labeling PII entities](how-pii-labels.md)\. 

![\[The PII labels analysis mode.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-pii-labels.png)

## Sentiment<a name="realtime-analysis-console-sentiment"></a>

The **Sentiment** tab shows the dominant sentiment of the text\. Sentiment can be rated neutral, positive, negative, or mixed\. In this case, each sentiment has a confidence rating, providing an estimate by Amazon Comprehend for that sentiment being dominant\. For more information, see [Sentiment](how-sentiment.md)\.

![\[The Sentiment tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-sentiment.png)

## Targeted sentiment<a name="realtime-analysis-console-targeted-sentiment"></a>

**Targeted sentiment** analysis identifies the sentiments expressed about entities mentioned in the text\. Amazon Comprehend assigns a sentiment rating to each mention of an entity, along with a confidence rating and other information\. A sentiment rating can be neutral, positive, negative, or mixed\. 

In the **Analyzed text** panel, the console underlines each of analyzed entities\. The color of the underlined text indicates the overall sentiment of the entity\. If you hover your cursor over an entity, the console displays additional information in a pop\-up window\.

![\[The Targeted sentiment tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-targeted-sentiment2.png)

The **Results** table provides additional detail about each entity\. If there are multiple mentions of the same entity, called a co\-reference group, the table displays these mentions as a collapsible set of rows associated with the main entity\.

In the following example, the entity is a person named **Zhang Wei**\. The targeted sentiment analysis recognizes that each mention of **your** is a reference to the same person\. The console displays these mentions as sub\-entries of the main entity\.

![\[The Results table for targeted sentiment analysis.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-targeted-sentiment1.png)

If the text you are analyzing doesn't include any targeted sentiment [Entity types](how-targeted-sentiment.md#how-targeted-sentiment-entities), the targeted sentiment analysis displays an empty results field\.

For more information about how to use the console for targeted sentiment real\-time analysis, see [Real time analysis using the console](how-targeted-sentiment.md#how-targeted-sentiment-console)\.

## Syntax<a name="realtime-analysis-console-syntax"></a>

The **Syntax** tab shows a breakdown of each element in the text, along with its part of speech and the associated confidence score\. For more information, see [Syntax analysis](how-syntax.md)\.

![\[The Syntax tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-console-syntax.png)
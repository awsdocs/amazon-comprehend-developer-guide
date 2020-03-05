# Analyzing Documents Using the Console<a name="get-started-console-analysis"></a>

The Amazon Comprehend console enables you to analyze the contents of documents up to 1,000 characters long\. The results are shown in the console so that you can review the analysis\.

To start analyzing documents, sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

You can replace the sample text with your own text either in English or one of the other languages supported by Amazon Comprehend and then choose **Analyze** to get an analysis of your text\.

**Entity types**

![\[Amazon Comprehend entity analysis\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-10.png)

The text is color\-coded to indicate different entity types such as organizations, locations, dates, and persons\.

Below the text being analyzed, the **Results** pane shows more information about the text\. Each entry shows the entity, its category, and the level of confidence Amazon Comprehend has in this analysis\. 

![\[The Entity section of the console Analysis pane.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-20.png)

For more information, see [Detect Entities](how-entities.md)

**Key phrases**

The **Key phrases** tab lists key noun phrases that Amazon Comprehend detected in the input text and the associated confidence level\. 

For more information, see [Detect Key Phrases](how-key-phrases.md)\.

![\[The Key phrases tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-30.png)

**Language**

The **Language** tab shows the dominant language of the text and Amazon Comprehend's level of confidence that it's detected the dominant language correctly\. Amazon Comprehend can recognize 100 languages\. For more information, see [Detect the Dominant Language](how-languages.md)\.

![\[The Language tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-40.png)

**Sentiment**

The **Sentiment** tab shows the overall emotional sentiment of the text\. Sentiment can be rated neutral, positive, negative, or mixed\. In this case, each emotional sentiment has a confidence rating, providing an estimate by Amazon Comprehend for that sentiment being dominant\.

For more information, see [Determine Sentiment](how-sentiment.md)\.

![\[The Sentiment tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-50.png)

**Syntax**

The **Syntax** tab shows a breakdown of each element in the text, along with its part of speech and the associated confidence score\.

For more information, see [Analyze Syntax](how-syntax.md)\.

![\[The Syntax tab.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-70.png)
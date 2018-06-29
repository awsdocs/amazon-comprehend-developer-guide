# Analyzing Documents Using the Console<a name="get-started-console-analysis"></a>

The Amazon Comprehend console enables you to analyze the contents of documents up to 1,000 characters long\. The results are shown in the console so that you can review the analysis\.

To start analyzing documents, sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

The console displays sample text and the analysis of that text: 

![\[The Amazon Comprehend input box.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-10.png)

You can replace the sample text with your own text in English or Spanish and then choose **Analyze** to get an analysis of your text\.

The text is color\-coded to indicate the entity type of significant words:
+ Orange tags identify locations\.
+ Brown tags identify dates\.
+ Magenta tags identify persons\.
+ Blue tags identify organizations\.
+ Black tags identify other entities that don't fit into any of the other entity categories\.

For more information, see [Entities](how-entities.md)

On the right side of the console, the **Analysis** pane shows more information about the text\.

The **Entity** section displays cards for the entities found in the text:

![\[The Entity section of the console Analysis pane.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-20.png)

Each card shows the text and its entity type\. To see a list of all of the entities in the text, choose **List**\. For a JSON structure of the results, choose **JSON**\. The JSON structure is the same as the structure returned by the [DetectEntities](API_DetectEntities.md) operation\.

The **Key phrases** section of the **Analysis** pane lists key noun phrases that Amazon Comprehend detected in the input text\. For the sample input text, the **Key phrases** section looks like this:

![\[The Key phrases section of the Analysis pane.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-30.png)

For an alternative view of the results, choose **List** or **JSON** \. The JSON structure is the same as the one returned by the [DetectKeyPhrases](API_DetectKeyPhrases.md) operation\.

The **Language** section shows the dominant language for the sample text and the Confidence score\. The Confidence score represents the level of confidence that Amazon Comprehend has that it's detected the dominant language correctly\. Amazon Comprehend can recognize 100 languages\. For more information, see [Dominant Language](how-languages.md)\.

![\[The Language section of the Amazon Comprehend Analysis pane.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-40.png)

As with the other sections, you can choose **List** or **JSON** to get another view of the results\. The JSON structure is the same as the one returned by the [DetectDominantLanguage](API_DetectDominantLanguage.md) operation\.

The **Sentiment** section of the **Analysis** pane shows the overall emotional sentiment of the text\. 

![\[The Sentiment section of the Analysis pane.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-50.png)

The score represents the confidence that Amazon Comprehend has that it has correctly detected the emotional sentiment expressed in the text\. Sentiment can be rated positive, neutral, mixed, or negative\.
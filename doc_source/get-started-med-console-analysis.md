# Analyzing Clinical Text Using the Console<a name="get-started-med-console-analysis"></a>

The Comprehend Medical console enables you to analyze the contents of clinical text, up to 20,000 characters long\. The results are shown in the console so that you can review the analysis\.

To start analyzing documents, sign in to the AWS Management Console and open the Comprehend Medical console\.

Under **Comprehend Medical**, choose **Real\-time analysis**\.

The console displays sample text and the analysis of that text: 

![\[The Comprehend Medical input text.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-cm-image-1.png)

You can replace the sample text with your own text in English and then choose **Analyze** to get an analysis of your text\.

![\[The Analyzed Text section of the console.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-cm-image-2.png)

Below the input text, the analyzed text is color\-coded to indicate the entity category:
+ Orange tags identify PHI data\.
+ Red tags identify Medication\.
+ Green tags identify Medical Condition\.
+ Blue tags identify Test, Treatment, or Procedure \(TTP\)\.
+ Purple tags identify Anatomy\.

For more information, see [How It Works](how-medical-works.md)\.

In the console, below the input box, the **Analyzed Text** pane shows more information about the text\.

The **Entity** section displays cards for the entities found in the text:

![\[The Results cards.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-cm-image-3.png)

Each card shows the text and its entity type\.

Next to each of the entities, a score represents the confidence that Comprehend Medical has in the identification of the text as the type of entity shown\.

To see the JSON structure of both the request and the results, choose **Application integration**\. The JSON structure is the same as the structure returned by the [DetectEntities](API_hera_DetectEntities.md) operation\.
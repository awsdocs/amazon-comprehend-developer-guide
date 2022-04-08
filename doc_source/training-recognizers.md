# Training recognizer models<a name="training-recognizers"></a>

A custom entity recognizer identifies only the entity types that you include when you train the model\. It does not automatically include the preset entity types\. If you want to also identify the preset entity types,such as LOCATION, DATE, or PERSON, you need to provide additional training data for those entities\.

When you create a custom entity recognizer using annotated PDF files, you can use the recognizer with a variety of input file formats: plain text, image files \(JPG, PNG, TIFF\), PDF files, and Word documents, with no pre\-processing or doc flattening required\. 

**Note**  
 Amazon Comprehend doesn't support annotation of image files or Word documents\.

After you create a custom entity recognizer, you can monitor the progress of the request using the [DescribeEntityRecognizer](API_DescribeEntityRecognizer.md) operation\. Once the `Status` field is `TRAINED`, the recognizer model is ready to use for custom entity recognition\.

**Topics**
+ [Train custom recognizers \(console\)](realtime-analysis-cer.md)
+ [Train and run custom recognizers \(API\)](get-started-cer.md)
+ [Custom entity recognizer metrics](cer-metrics.md)
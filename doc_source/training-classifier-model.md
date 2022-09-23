# Training classification models<a name="training-classifier-model"></a>

Train your custom classifier model in either multi\-class or multi\-label mode\. The concept of *class* is used for both modes\. It's a custom category that applies to the document being analyzed\. However, each mode uses class differently\. Multi\-class mode associates only a single class with each document\. Multi\-label mode associates more than one class with a document\. The training data formats are different for each mode as well\. 

You can train a custom classifier by using any of the following languages that work with Amazon Comprehend: English, Spanish, German, Italian, French, or Portuguese\. However, you can only train the classifier in one language\. Classifiers do not support multiple languages\.

After you create a custom classifier, you can monitor the progress of the request using the [DescribeDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeDocumentClassifier.html) operation\. Once the `Status` field is `TRAINED` you can then use the classifier to classify documents\.

**Topics**
+ [Train custom classifiers \(console\)](create-custom-classifier-console.md)
+ [Train and run custom classifiers \(API\)](train-custom-classifier-api.md)
+ [Test the training data](testing-the-model.md)
+ [Custom classifier metrics](cer-doc-class.md)
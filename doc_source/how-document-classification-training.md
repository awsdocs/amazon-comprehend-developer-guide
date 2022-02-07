# Training a Custom Classifier<a name="how-document-classification-training"></a>

To train a custom classifier follow these steps\. 

1. Provide your training data with the custom classes that you want the classifier to recognize\.

1. Put your training data in an Amazon Simple Storage Service \(Amazon S3\) bucket\. The bucket must have AWS Identity and Access Management \(IAM\) Amazon Comprehend read permissions that allow Amazon Comprehend access\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\. Create another S3 bucket with the same requirements for your output\.

1. Submit a training job using the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation\. 

Train your custom classifier model in either multi\-class or multi\-label mode\. The concept of *class* is used for both modes\. It's a custom category that applies to the document being analyzed\. However, each mode uses class differently\. Multi\-class mode associates only a single class with each document\. Multi\-label mode associates more than one class with a document\. The training data formats are different for each mode as well\. 

You can train a custom classifier by using any of the following languages that work with Amazon Comprehend: English, Spanish, German, Italian, French, or Portuguese\. However, you can only train the classifier in one language\. Classifiers do not support multiple languages\.

After you ask Amazon Comprehend to create a custom classifier, you can monitor the progress of the request using the [DescribeDocumentClassifier](API_DescribeDocumentClassifier.md) operation\. Once the `Status` field is `TRAINED` you can then use the classifier to classify documents\.

**Topics**
+ [Creating Training Data](how-document-classification-training-data.md)
+ [Multi\-Class Mode](how-document-classification-training-multi-class.md)
+ [Multi\-Label Mode](how-document-classification-training-multi-label.md)
+ [Testing the Training Data](testing-the-model.md)
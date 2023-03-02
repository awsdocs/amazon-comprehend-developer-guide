# Preparing classifier training data<a name="prep-classifier-data"></a>

You can classify your documents using two modes: multi\-class or multi\-label\. Some of the input file formats are different for each mode, so you choose which mode to use when creating your data for training the model\. 

The concept of *class* is used for both modes\. It's a custom category that applies to the document being analyzed\. However, each mode uses class differently\. Multi\-class mode associates only a single class with each document\. Multi\-label mode associates more than one class with a document\. The training data formats are different for each mode as well\. 

You can train a custom classifier by using any of the following languages that work with Amazon Comprehend: English, Spanish, German, Italian, French, or Portuguese\. However, you can only train the classifier in one language\. Classifiers do not support multiple languages\.

To train a custom classifier \(custom model\), identify the classes you want to use for classification\. For example, **pricing**, **defect**, or **profanity**\. Next, identify examples of documents for each of these classes\. For each class, provide a minimum of 10 documents for training\. For example, if you have 10 possible classes, you need a total of at least 100 classified documents to train the model\. For more accurate training, we recommend at least 50 documents or more for each class\.

**Note**  
Even though you can use multiple classes in a classifier, no hierarchy is determined by them when you use the classifier on a document\.

We recommend that you train the model with 50 or more training documents for each class\. While a minimum of 10 training documents for each class is required, you get better accuracy with more documents\. The total size of the training documents must be less than 5 GB\. 

**Topics**
+ [Multi\-class mode](prep-classifier-data-multi-class.md)
+ [Multi\-label mode](prep-classifier-data-multi-label.md)
# Creating Training Data<a name="how-document-classification-training-data"></a>

To train a custom classifier \(custom model\), identify the classes you want to use for classification\. For example, **pricing**, **defect**, or **profanity**\. Next, identify examples of documents for each of these classes\. For each class, provide a minimum of 10 documents for training\. For example, if you have 10 possible classes, you need a total of at least 100 classified documents to train the model\. For more accurate training, we recommend at least 50 documents or more for each class\.

**Note**  
Even though you can use multiple classes in a classifier, no hierarchy is determined by them when you use the classifier on a document\.

We recommend that you train the model with 50 or more training documents for each class\. While a minimum of 10 training documents for each class is required, you get better accuracy with more documents\. The total size of the training documents must be less than 5 GB\. 
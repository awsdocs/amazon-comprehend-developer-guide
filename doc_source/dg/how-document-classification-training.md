# Training a Custom Classifier<a name="how-document-classification-training"></a>

To train a custom classifier follow these steps\. 

1. Provide your training data with the custom classes that you want the classifier to recognize\.

1. Put your training data in an Amazon Simple Storage Service \(Amazon S3\) bucket\. The bucket must have AWS Identity and Access Management \(IAM\) Amazon Comprehend read permissions that allow Amazon Comprehend access\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\. Create another S3 bucket with the same requirements for your output\.

1. Submit a training job using the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation\. 

You can train a custom classifier by using any of the following languages that work with Amazon Comprehend: English, Spanish, German, Italian, French, or Portuguese\. However, you can only train the classifier in one language\. Classifiers do not support multiple languages\.

After you ask Amazon Comprehend to create a custom classifier, you can monitor the progress of the request using the [DescribeDocumentClassifier](API_DescribeDocumentClassifier.md) operation\. Once the `Status` field is `TRAINED` you can then use the classifier to classify documents\.

## Creating Training Data<a name="how-document-classification-training-data"></a>

To train a custom classifier \(custom model\), identify the classes you want to use for classification\. For example, **pricing**, **defect**, or **profanity**\. Next, identify examples of documents for each of these classes\. For each class, provide a minimum of 10 documents for training\. For example, if you have 10 possible classes, you need a total of at least 100 classified documents to train the model\. For more accurate training, we recommend at least 50 documents or more for each class\.

**Note**  
Even though you can use multiple classes in a classifier, no hierarchy is determined by them when you use the classifier on a document\.

When training your classifier, the data must be in a single \.csv file\. The format of the data will depend on which classifier mode you choose\. 

In each line, the class name is placed first, followed by the complete document\.

Classes can be any valid UTF\-8 string\. We suggest classes that are clear and don't overlap in meaning\. Labels must be uppercase and can be multiple\-token\. They can have white space, consist of multiple words connected by underscores or hyphens, or may even contain a comma in it, as long as it is correctly escaped\.

Training documents must be end with \\n or \\r\\n and be valid UTF\-8 in a \.csv file\. Additionally, each document should contain a representative distribution of the types of documents that the classifier must categorize in general practice\.

We recommend that you train the model with 50 or more training documents for each class\. While a minimum of 10 training documents for each class is required, you get better accuracy with more documents\. The total size of the training documents must be less than 5 GB\. 

## Multi\-Class and Multi\-Label Modes<a name="multiclass-multilabel"></a>

Train your custom classifier model in either multi\-class or multi\-label mode\. The concept of *class* is used for both modes\. It's a custom category that applies to the document being analyzed\. However, each mode uses class differently\. Multi\-class mode associates only a single class with each document\. Multi\-label mode associates more than one class with a document\. The training data formats are different for each mode as well\. 

**Multi\-Class Mode**

In multi\-class classification, each document can have one and only one class assigned to it\. The individual classes are mutually exclusive\. For example, a movie can be classed as a documentary or as science fiction, but not both at the same time\. 

When formatting the training documents, the data must be in a two\-column \.csv file\. When creating the \.csv file, do not include headers for the individual columns\. Including headers in your \.csv file may cause runtime errors\. Each line of the \.csv file contains a single class and the text of a document that demonstrates that class\.

```
CLASS,Text of document 1
CLASS,Text of document 2
CLASS,Text of document 3
```

For example:


|  | Multi\-class classification job | 
| --- | --- | 
|  Content  |  DOCUMENTARY,text of Document 1  SCIENCE\_FICTION,text of Document 2 DOCUMENTARY,text of Document 3 DOCUMENTARY,text of Document 4 SCIENCE\_FICTION,text of Document 5 ROMANTIC\_COMEDY,text of Document 6  | 
|  Details  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/comprehend/latest/dg/how-document-classification-training.html)  | 

After you train the custom classifier, you can analyze documents in either asynchronous or synchronous operations\. You can analyze a large number of documents at once using the asynchronous operation\. The resulting analysis is returned in a separate file\. Using the synchronous operation, you can only analyze a single document, but you can get results in real time\. These options are not available when you use multi\-label mode\. For more information, see [Asynchronous Classification](how-document-classification.md#multiclass-async-sync)\.

For training, multi\-class mode supports up to 1 million examples containing up to 1000 unique classes\.

**Multi\-Label Mode**

In multi\-label classification, individual classes represent different categories, but these categories are somehow related and are not mutually exclusive\. As a result, each document has at least one class assigned to it, but can have more\. For example, a movie can simply be an action movie, or it can be an action movie, a science fiction movie, and a comedy, all at the same time\.

As with multi\-class mode, when you format the training documents, the data must be in a two\-column \.csv file\. When creating the \.csv file, do not include headers for the individual columns\. Including headers in your \.csv file may cause runtime errors\. Each line of the \.csv file contains one or more classes and the text of a document that shows those labels\. More than one class can be indicated by using a delimiter \(such as a \| \) between each class\.

```
CLASS,Text of document 1
CLASS,Text of document 2
CLASS|CLASS|CLASS,Text of document 3
```

For example:


|  | Multi\-label classification job | 
| --- | --- | 
|  Content  |  SCIENCE\_FICTION,text of Document 1  SCIENCE\_FICTION\|ACTION,text of Document 2 DRAMA,text of Document 3 COMEDY\|ACTION\|ROMANCE,text of Document 4 ROMANCE,text of Document 5 ROMANCE\|DRAMA,text of Document 6  | 
|  Details  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/comprehend/latest/dg/how-document-classification-training.html)  | 

The default delimiter between class names is a pipe \(\|\)\. However, you can use a different character as a delimiter\. You can use the following characters as a delimiter by specifying it under **Delimiter for labels**\. The delimiter cannot be part of your class name\. For example, if your classes are CLASS\_1, CLASS\_2, and CLASS\_3, the underscore \(**\_**\) is part of the class name\. You cannot use then use an underscore as the delimiter for separating class names\.

The training documents might use a delimiter other than the default or the delimiter you specify\. In this case, the classes on that line are combined to make a single unique class, such as `CLASSCLASSCLASS` in the example\. 

For training, multi\-label mode supports up to 1 million examples containing up to 100 unique classes\.

## Testing the Training Data<a name="testing-the-model"></a>

Once the model has been trained, Amazon Comprehend uses between 10 and 20 percent of the training documents to test the custom classifier model\. Testing the model provides you with metrics that you can use to determine if the model is trained well enough for your purposes\. These metrics are displayed in the **Classifier performance** section of the **Classifier details** page in the console\. They are also returned in the `Metrics` fields returned by the [DescribeDocumentClassifier](API_DescribeDocumentClassifier.md) operation\.

For example, in the sample of training data below, there are 5 labels, DOCUMENTARY, DOCUMENTARY, SCIENCE\_FICTION, DOCUMENTARY, ROMANTIC\_COMEDY\. There are **3 unique classes**: DOCUMENTARY, SCIENCE\_FICTION, ROMANTIC\_COMEDY\. 


| column 1 | column 2 | 
| --- | --- | 
| DOCUMENTARY | document text 1 | 
| DOCUMENTARY | document text 2 | 
| SCIENCE\_FICTION | document text 3 | 
| DOCUMENTARY | document text 4 | 
| ROMANTIC\_COMEDY | document text 5 | 

For instance, if the data contained 1000 instances of the DOCUMENTARY class, 900 instances of the SCIENCE\_FICTION, and a single instance of the ROMANTIC\_COMEDY class, then the test set would approximately be 100 DOCUMENTARY and 90 SCIENCE\_FICTION instances\. The ROMANTIC\_COMEDY class would not be included in the test set, as there is only a single example available\. This is because it's highly unlikely you will see a document classified as ROMANTIC\_COMEDY during prediction/inference in a setting like this\. 

Once you've finished training your model, the training metrics can provide you with information that you can use to decide if the model is trained sufficiently for your needs\. 
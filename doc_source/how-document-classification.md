# Custom Classification<a name="how-document-classification"></a>

You can use Amazon Comprehend to build your own models for *custom classification*\. You can also assign a document to a specific class or category, or to multiple ones\. 

Custom classification is a two\-step process\. First, you train a custom classifier to recognize the classes that are of interest to you\. Then you send unlabeled documents to be classified\.

To train the classifier, specify the options you want, and send Amazon Comprehend documents to be used as training material\. Based on the options you indicated, Amazon Comprehend creates a custom ML model that it trains based on the documents you provided\. This custom model \(the classifier\) examines each document you submit\. It then returns either the specific class that best represents the content \(if you're using multi\-class mode\) or the set of classes that apply to it \(if you're using multi\-label mode\)\. 

For example, you can categorize the content of support requests so that you can route the request to the proper support team\. Or you can categorize emails received from customers to provide guidance on the requests that customers are making\. You can combine Amazon Comprehend with Amazon Transcribe to convert speech to text and then to classify the requests coming from support phone calls\. 

You can have multiple custom classifiers in your account, each trained using different data\. When you submit a classification job, you choose which classifier to use\. Amazon Comprehend returns results based on that classifier, how it was trained, and whether it was trained using multi\-class or multi\-label mode\. The multi\-class mode can be used asynchronously for a large document or set of documents or synchronously \(in real\-time\) for a single document\. The multi\-label mode can only be used asynchronously\.

## Multi\-Class and Multi\-Label Modes<a name="multiclass-multilabel2"></a>

You can classify your documents using two modes: multi\-class or multi\-label\. You can only use one mode at a time and it must be set when training your classifier\. Some of the basic concepts and necessary formats are different for each\. In the Amazon Comprehend console, you choose which mode to use when creating your training job: 

![\[Custom classifier mode\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/classifier-mode.png)

**Multi\-Class mode**

Out of a group of at least two possible classes, multi\-class mode specifies a single class for each document\. The individual classes are mutually exclusive\. For example, a movie can be classed as a documentary or as science fiction, but not both at the same time\. The format must be one class and document per line\. For example:

```
CLASS,Text of document 1
CLASS,Text of document 2
CLASS,Text of document 3
```

After training the custom classifier, you can then analyze documents in either asynchronous or synchronous operations\. You can analyze a large number of documents at once using the asynchronous operation, with the resulting analysis returned in a separate file\. Using the synchronous operation, you can only analyze a single document, but you can get results in real time\. These options are not available when using multi\-label mode\. For more information, see [Asynchronous Classification](#multiclass-async-sync)\.

**Multi\-Label mode**

Out of a group of at least two possible classes, multi\-label mode identifies one or more classes for each document\. Unlike multi\-class mode, these classes are not mutually exclusive and each document can have more than one class assigned to it\. For example, a movie can simply be an action movie, or it can be an action movie, a science fiction movie, and a comedy, all at the same time\.

As with multi\-class mode, when formatting the training documents, the data must be in a two column \.csv file\. Each line of the \.csv file contains one or more classes and the text of a document that demonstrates those labels\. More than one class can be indicated by using a delimiter \(such as a \| \) between each class:

```
CLASS,Text of document 1
CLASS,Text of document 2
CLASS|CLASS|CLASS,Text of document 3
```

## Asynchronous Classification<a name="multiclass-async-sync"></a>

When using multi\-class mode, custom classification can be used for both asynchronous operations\. 

For asynchronous analysis, you first train a custom classifier \(or custom model\) to recognize the categories that are of interest to you\. To train the classifier, you send Amazon Comprehend a group of classified documents, along with the class to which each belongs\. After Amazon Comprehend builds the classifier, you send documents to be classified\. The custom classifier examines each document and returns the category that best represents the content of the document\. The results are then saved to a file in your S3 bucket\. The cost of asynchronous custom classification is based on the number of characters used\. 

You can have multiple custom classifiers in your account, each trained using different data\. You can then choose the classifier to meet your needs\. 

**Topics**
+ [Multi\-Class and Multi\-Label Modes](#multiclass-multilabel2)
+ [Asynchronous Classification](#multiclass-async-sync)
+ [Training a Custom Classifier](how-document-classification-training.md)
+ [Running an Asynchronous Classification Job](how-class-run.md)
+ [Real\-time Analysis with Custom Classification](custom-sync.md)
+ [Tagging Custom Classifiers](class-tagging.md)
+ [Custom Classifier Metrics](cer-doc-class.md)
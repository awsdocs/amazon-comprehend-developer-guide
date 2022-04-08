# Custom classification<a name="how-document-classification"></a>

Use *custom classification* to organize your documents into categories \(classes\) that you define\. Custom classification is a two\-step process\. First, you train a custom classification model \(also called a classifier\) to recognize the classes that are of interest to you\. Then you use your model to classify any number of document sets

For example, you can categorize the content of support requests so that you can route the request to the proper support team\. Or you can categorize emails received from customers to provide guidance on the requests that customers are making\. You can combine Amazon Comprehend with Amazon Transcribe to convert speech to text and then to classify the requests coming from support phone calls\. 

You can have multiple custom classifiers in your account, each trained using different data\. When you submit a classification job, you choose which classifier to use\. Amazon Comprehend returns results based on that classifier, how it was trained, and whether it was trained using multi\-class or multi\-label mode\. For multi\-class mode, you can classify a single document synchronously \(in real\-time\) or classify a large document or set of documents asynchronously\. The multi\-label mode supports asynchronous jobs only\.

**Topics**
+ [Preparing training data](prep-classifier-data.md)
+ [Training classification models](training-classifier-model.md)
+ [Running custom classifier models](running-classifiers.md)
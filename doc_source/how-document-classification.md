# Custom Classification<a name="how-document-classification"></a>

You can use Amazon Comprehend to build your own models for *custom classification*, assigning a document to a class or a category\. 

For example, you can categorize the content of support requests so that you can route the request to the proper support team\. Or you can categorize emails received from customers to provide guidance on the requests that customers are making\. You can combine Amazon Comprehend with Amazon Transcribe to convert speech to text and then to classify the requests coming from support phone calls\.

Custom classification is a two step process\. First you train a custom classifier to recognize the categories that are of interest to you\. To train the classifier, you send Amazon Comprehend a group of labeled documents\. After Amazon Comprehend builds the classifier, you send documents to be classified\. The custom classifier examines each document and returns the label that best represents the content of the document\.

You can have multiple custom classifiers in your account, each trained using different data\. You choose the classifier to use when you submit a classification job\.
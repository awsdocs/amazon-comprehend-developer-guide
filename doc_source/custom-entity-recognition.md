# Custom Entity Recognition<a name="custom-entity-recognition"></a>

Custom entity recognition extends the capability of Amazon Comprehend by enabling you to identify new entity types not supported as one of the preset generic entity types\. This means that in addition to identifying entity types such as LOCATION, DATE, PERSON, and so on, you can analyze documents and extract entities like product codes or business\-specific entities that fit your particular needs\.

Building an accurate in\-house custom entity recognizer on your own can be a complex process, requiring preparation of large sets of manually annotated training documents and the selection of the right algorithms and parameters for model training\. Amazon Comprehend enables you to sidestep some of these issues by providing automatic annotation and model development to create a custom entity recognition model\.

Creating a custom entity recognition model is a more effective approach, compared to using string matching or regular expressions to identify entities\. For example, to extract product codes, it would be difficult to enumerate all possible patterns to apply string matching\. But a custom entity recognition model can learn the context where those product codes are most likely to appear and then make such inferences even though it has never previously seen the exact product codes\. As well, typos in product codes and the addition of new product codes can still be expected to be caught by Amazon Comprehend's custom entity recognition model, but would be missed when using string matches against a static list\.

To use Amazon Comprehend's custom entity recognition service, you need to provide a data set for model training purposes, with either a set of annotated documents, or a list of entities and their type label \(such as `PRODUCT_CODES`\) and a set of documents containing those entities\. The service automatically tests for the best algorithm and parameters while training the model to use, looking for the most accurate combination of these components\. 

**Topics**
+ [Training Custom Entity Recognizers](training-recognizers.md)
+ [Detecting Custom Entities](detecting-cer.md)
+ [Custom Entity Recognizer Metrics](cer-metrics.md)
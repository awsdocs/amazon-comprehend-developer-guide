# Custom Entity Recognition<a name="custom-entity-recognition"></a>

Custom entity recognition extends the capability of Amazon Comprehend by helping you identify your specific new entity types that are not of from the preset [generic entity types](https://docs.aws.amazon.com/comprehend/latest/dg/how-entities.html)\. This means that in addition to identifying predefined entity types such as LOCATION, DATE, PERSON, you can analyze documents and extract entities like product codes or business\-specific entities that fit your particular needs\.

Building an accurate in\-house custom entity recognizer on your own can be a complex process, requiring preparation of large sets of manually annotated training documents and the selection of the right algorithms and parameters for model training\. Amazon Comprehend helps you to sidestep some of these issues by providing automatic annotation and model development to create a custom entity recognition model\.

Creating a custom entity recognition model is a more effective approach, compared to using string matching or regular expressions to extract entities from documents\. For example, to extract ENGINEER names in a document, it would be difficult to enumerate all possible names\. Additionally, without context, it would be challenging to to distinguish between ENGINEER names and ANALYST names\. A custom entity recognition model can learn the context where those names are likely to appear\. Additionally, string matching will not detect entities that have typos or follow new naming conventions, while this is possible using a custom model\. 

To use Amazon Comprehend's custom entity recognition service, you have two options:   [Annotations ](cer-annotation.md)—you provide a data sent containing annotated entities for model training\. For an analysis job on Word docs or PDFs, you need to have trained a custom entity recognizer from annotated PDFs\. We don't support Word document annotation\.   [Entity Lists \(Plain Text Only\)](cer-entity-list.md)—you provide a list of entities and their type label \(such as `PRODUCT_CODES` and a set of unannotated documents containing those entities for model training\.    The service automatically tests for the best algorithm and parameters while training the model to use, looking for the most accurate combination of these components\. 

You can train a model on up to 25 custom entities at once\. Once your model is trained, you can search for those custom entities in each entities detection job\. For more details, see the [Guidelines and Quotas page](https://docs.aws.amazon.com/comprehend/latest/dg/guidelines-and-limits.html)\.

**Topics**
+ [Training Custom Entity Recognizers](training-recognizers.md)
+ [Detecting Custom Entities with an Asynchronous Batch Job with Amazon Comprehend](detecting-cer.md)
+ [Detecting Custom Entities in Real Time with Amazon Comprehend](detecting-cer-real-time.md)
+ [Tagging Custom Entity Recognizers](CER-tagging.md)
+ [Custom Entity Recognizer Metrics](cer-metrics.md)
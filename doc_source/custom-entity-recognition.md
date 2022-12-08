# Custom entity recognition<a name="custom-entity-recognition"></a>

Custom entity recognition extends the capability of Amazon Comprehend by helping you identify your specific new entity types that are not in the preset [generic entity types](https://docs.aws.amazon.com/comprehend/latest/dg/how-entities.html)\. This means that you can analyze documents and extract entities like product codes or business\-specific entities that fit your particular needs\.

Building an accurate custom entity recognizer on your own can be a complex process, requiring preparation of large sets of manually annotated training documents and the selection of the right algorithms and parameters for model training\. Amazon Comprehend helps to reduce the complexity by providing automatic annotation and model development to create a custom entity recognition model\.

Creating a custom entity recognition model is a more effective approach than using string matching or regular expressions to extract entities from documents\. For example, to extract ENGINEER names in a document, it is difficult to enumerate all possible names\. Additionally, without context, it is challenging to distinguish between ENGINEER names and ANALYST names\. A custom entity recognition model can learn the context where those names are likely to appear\. Additionally, string matching will not detect entities that have typos or follow new naming conventions, while this is possible using a custom model\. 

You have two options for creating a custom model: 

1. Annotations – provide a data set containing annotated entities for model training\. 

1. Entity lists \(plaintext only\) – provide a list of entities and their type label \(such as `PRODUCT_CODES` and a set of unannotated documents containing those entities for model training\.

When you create a custom entity recognizer using annotated PDF files, you can use that recognizer with a variety of input file formats: plaintext, image files \(JPG, PNG, TIFF\), PDF files, and Word documents, with no pre\-processing or doc flattening required\. Amazon Comprehend doesn't support annotation of image files or Word documents\.

**Note**  
A custom entity recognizer using annotated PDF files supports English documents only\.

You can train a model on up to 25 custom entities at once\. For more details, see the [Guidelines and quotas page](https://docs.aws.amazon.com/comprehend/latest/dg/guidelines-and-limits.html)\.

After your model is trained, you can use the model for real\-time entity detection and in entity detection jobs\. 

**Topics**
+ [Preparing the training data](prep-training-data-cer.md)
+ [Training custom recognizers](training-recognizers.md)
+ [Running real\-time custom recognizer analysis](running-cer-sync.md)
+ [Running analysis jobs for custom entity recognition](detecting-cer.md)
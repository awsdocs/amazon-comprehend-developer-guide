# Preparing the training data<a name="prep-training-data-cer"></a>

To train a successful custom entity recognition model, it's important to supply the model trainer with high quality data as input\. Without good data, the model won't learn how to correctly identify entities\. 

You can choose one of two ways to provide data to Amazon Comprehend in order to train a custom entity recognition model:
+ **Entity list** – Lists the specific entities so Amazon Comprehend can train to identify your custom entities\. Note: Entity lists can only be used for plain text documents\. 
+ **Annotations** – Provides the location of your entities in a number of documents so Amazon Comprehend can train on both the entity and its context\. To create a model for analyzing image files, PDFs, or Word documents, you must train your recognizer using PDF annotations\. 

In both cases, Amazon Comprehend learns about the kind of documents and the context where the entities occur and builds a recognizer that can generalize to detect the new entities when you analyze documents\.

When you create a custom model \(or train a new version\), you can provide a test dataset\. If you do not provide test data, Amazon Comprehend reserves 10% of the input documents to test the model\. Amazon Comprehend trains the model with the remaining documents\.

**Topics**
+ [When to use annotations vs entity lists](#prep-training-data-comp)
+ [Entity lists \(plain text only\)](cer-entity-list.md)
+ [Annotations](cer-annotation.md)

## When to use annotations vs entity lists<a name="prep-training-data-comp"></a>

 Creating annotations takes more work than creating an entity list, but the resulting model can be significantly more accurate\. Using an entity list is quicker and less work\-intensive, but the results are less refined and less accurate\. This is because the annotations provide more context for Amazon Comprehend to use when training the model\. Without that context, Amazon Comprehend will have a higher number of false positives when trying to identify the entities\. 

There are scenarios when it makes more business sense to avoid the higher expense and workload of using annotations\. For example, the name John Johnson is significant to your search, but whether it's the exact individual isn't relevant\. Or the metrics when using the entity list are good enough to provide you with the recognizer results that you need\. In such instances, using an entity list instead can be the more effective choice\. 

We recommend using the annotations mode in the following cases:
+ If you plan to run inferences for image files, PDFs, or Word documents\. In this scenario, you train a model using annotated PDF files and use the model to run inference jobs for image files, PDFs, and Word documents\. 
+ When the meaning of the entities could be ambiguous and context\-dependent\. For example, the term *Amazon* could either refer to the river in Brazil, or the online retailer Amazon\.com\. When you build a custom entity recognizer to identify business entities such as *Amazon*, you should use annotations instead of an entity list because this method is better able to use context to find entities\.
+ When you are comfortable setting up a process to acquire annotations, which can require some effort\.

We recommend using an entity list in the following cases:
+ When you already have a list of entities or when it is relatively easy to compose a comprehensive list of entities\. If you use an entity list, the list should be complete or at least covers the majority of valid entities that might appear in the documents you provide for training\. 
+ For first\-time users, it is generally recommended to use an entity list because this requires a smaller effort than constructing annotations\. However, it is important to note that the trained model might not be as accurate as if you used annotations\.
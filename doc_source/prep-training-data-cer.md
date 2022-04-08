# Preparing the training data<a name="prep-training-data-cer"></a>

To train a successful custom entity recognition model, it's important to supply the model trainer with high quality data as input\. Without good data, the model won't learn how to correctly identify entities\. 

You can choose one of two ways to provide data to Amazon Comprehend in order to train a custom entity recognition model:
+ [Annotations](cer-annotation.md)—Provides the location of your entities in a large number of documents so Amazon Comprehend can train on both the entity and its context\. To create a model for analyzing image files, PDFs, or Word documents, you must train your recognizer using PDF annotations\. 
+ [Entity lists \(plain text only\)](cer-entity-list.md)—Lists the specific entities so Amazon Comprehend can train to identify your custom entities\. Note: Entity lists can only be used for plain text documents\. 

In both cases, Amazon Comprehend learns about the kind of documents and the context where the entities occur and builds a recognizer that can generalize to detect the new entities when you analyze documents\.

**Annotations**

By submitting annotation along with your documents, you can increase the accuracy of the model\. With Annotations, you're not simply providing the location of the entity you're looking for, but you're also providing more accurate context to the custom entity you're seeking\.

For instance, if you're searching for the name John Johnson, with the entity type JUDGE, providing your annotation might help the model to learn that the person you want to find is a judge\. If it is able to use the context, then Amazon Comprehend won't find people named John Johnson who are attorneys or witnesses\. Without providing annotations, Amazon Comprehend will create its own version of an annotation, but won't be as effective at including only judges\. Providing your own annotations might help to achieve better results and to generate models that are capable of better leverage context when extracting custom entites\.

Providing your own annotation takes more work, but can be significantly more refined\. Not using your own annotation is quicker and less work\-intensive, but the results are less refined and less accurate\.

**Entity lists**

With custom entity recognition, Amazon Comprehend helps you to train your model using an entity list\. If you want to use an entity list, you provide two pieces of information: a list of the entity names with their correspoinding custom entity types and a collection of unannotated documents which you expect your entities will appear\. This is a more straightforward choice than the annotations option, but is probably going to result in a rougher, less specific result\. This is because the annotations provide more context for Amazon Comprehend to use when training the model\. Without that context, Amazon Comprehend will have a higher number of false positives when trying to identify the entities\. 

When you provide an Entity List, Amazon Comprehend uses an intelligent algorithm to detect occurrences of the entity in the documents to serve as the basis for training the custom entity recognizer model\.

For instance, if you are searching for the name John Johnson, with the entity type JUDGE, using an entity list will enable you to identify instances of his name\. However, without exact locations where John Johnson or JUDGE is annotated, Amazon Comprehend might view all instances of the name John Johnson, including other employees with the same name match for your custom entity\. 

**Annotations or entity list?**

This comparison would make it seem as if annotations are always the best approach, but this isn't the case\. Only the name John Johnson might be significant to your search and whether it's the exact individual isn't relevant\. Or the result is useful, but not worth the time and cost of producing an annotation list\. Or the metrics when using the entity list are good enough to provide you with the recognizer you need\. There are many scenarios when it makes more business sense to avoid the higher expense and workload of creating the annotations necessary for the other option\. In such instances, using an entity list instead can be the more effective choice\. 

We recommend using the annotations mode in the following cases:
+ If you plan to run inferences for image files, PDFs, or Word documents\. In this scenario, you train a model using annotated PDF files and use the model to run inference jobs for image files, PDFs, and Word documents\. 
+ When the meaning of the entities could be ambiguous and context\-dependent\. For example, the term *Amazon* could either refer to the river in Brazil, or the online retailer Amazon\.com\. When you build a custom entity recognizer to identify business entities such as *Amazon*, you should use annotations instead of an entity list because this method is better able to use context to find entities\.
+ When you are comfortable setting up a process to acquire annotations, which can require some effort\.

We recommend using entity list in the following cases:
+ When you already have a list of entities or when it is relatively easy to compose a comprehensive list of entities\. If you use an entity list, the list should be complete or at least covers the majority of valid entities that might appear in the documents you provide for training\. 
+ For first\-time users, it is generally recommended to use an entity list because this requires a smaller effort than constructing annotations\. However, it is important to note that the trained model might not be as accurate as if you used annotations\.

**Topics**
+ [Annotations](cer-annotation.md)
+ [Entity lists \(plain text only\)](cer-entity-list.md)
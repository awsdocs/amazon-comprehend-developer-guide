# Training Custom Entity Recognizers<a name="training-recognizers"></a>

Amazon Comprehend's custom entity recognition enables you to analyze your documents to find entities specific to your needs, rather than limiting you to the preset entity types already available\. You can identify almost any kind of entity, simply by providing a sufficient number of details to train your model effectively\. 

Building a successful custom entity recognition model requires training your model\. The training process usually requires extensive knowledge of machine learning \(ML\) and a complex process for model optimization\. Amazon Comprehend automates this for you using a technique called *transfer learning* to build your model on a sophisticated general\-purpose entities recognition model framework\. With this in place, all you need to supply is the data\. However, it's important that you supply it with high quality data as input\. Without good data the model won't learn how to correctly identify entities\. 

You can choose one of two ways to provide data to Amazon Comprehend in order to train a custom entity recognition model:
+ [Annotations](cer-annotation.md)—This uses an annotation list that provides the location of your entities in a large number of documents so Amazon Comprehend can train on both the entity and its context\. 
+ [Entity Lists](cer-entity-list.md)—This provides only a limited context, and uses only a list of the specific entities list so Amazon Comprehend can train to identify the custom entity\. 

**Annotations**

By submitting annotation along with your documents, you can increase the accuracy of the model\. With Annotations, you're not simply providing the location of the entity you're looking for, but you're also providing more accurate context to the custom entity you're seeking\.

For instance, if you're searching for the name John Johnson, with the entity type JUDGE, providing your annotation may help the model to learn that the person you want to find is a judge\. If it is able to use the context, then Amazon Comprehend won't find people named John Johnson who are attorneys or witnesses\. Without providing annotations, Amazon Comprehend will create its own version of an annotation, but won't be as effective at including only judges\.

Providing your own annotation takes more work, but can be significantly more refined\. Not using your own annotation is quicker and less expensive \(in terms of work\), but the results are rougher and less accurate\.

**Entity Lists**

With custom entity recognition, Amazon Comprehend enables you to train your model without submitting annotation, by simply providing a list of the entities rather than an annotations file\. This is a simpler and easier choice than the annotations option, but is probably going to result in a rougher, less specific result\. This is because the annotations provide more context for Amazon Comprehend to use when training the model\. Without that context, Amazon Comprehend will have a higher number of false positives when trying to identify the entities\. 

When you provide an Entity List, Amazon Comprehend uses an intelligent algorithm to detect occurrances of the entity in the documents to serve as the basis for training the custom entity recognizer model\.

For instance, if you are searching for the name John Johnson, with the entity type JUDGE, using an entity list will enable you to identify instances of his name\. However, without an annotations list to provide a clear context that will help Amazon Comprehend to determine if the instance is the correct John Johnson, it will identify instances where a person's name is John Johnson, but is not the correct individual\. 

**Annotations or Entity List?**

This comparison would make it seem as if an annotations list is always desirable, but this isn't the case\. Only the name John Johnson might be significant to your search and whether it's the exact individual isn't relevant\. Or the result is useful, but not worth the time and cost of producing an annotation list\. Or the metrics when using the entity list are good enough to provide you with the results you need\. There are many scenarios when it makes more business sense to avoid the higher expense and workload of creating the annotations necessary for the other option\. In such instances, using an entity list instead can be the more effective choice\. 

We recommend using annotations in the following cases:
+ When the meaning of the entities could be ambiguous and context\-dependent\. For example, the term *Amazon* could either refer to the river in Brazil, or the online retailer Amazon\.com\. When you build a custom entity recognizer to identify business entities such as *Amazon*, you should use annotations instead of an entity list because this method is better able to use context to find entities\.
+ When you are comfortable setting up a process to acquire annotations, which can require a significant amount of effort on your end\.

We recommend using entity list in the following cases:
+ When you already have a list of entities or when it is relatively easy to compose a comprehensive list of entities\. If you use an entity list, the list should be complete or at least covers the majority of valid entities that may appear in the documents you provide for training\. Do not provide a list with few entities in it just to try out the service, because entities that appear in documents but not provided in the entity list will be treated as non\-entities by Amazon Comprehend and may even hurt model training, especially if there are a lot of them\.
+ For first\-time users, it is generally recommended to use an entity list because it involves less effort to prepare training data\. It is important to note that the trained model might not be as accurate as if you used annotations\.

**Data Options**
+ [Annotations](cer-annotation.md)
+ [Entity Lists](cer-entity-list.md)
# Annotations<a name="cer-annotation"></a>

Annotations label entities in context by associating your custom entity types with the locations where they occur in your training documents\.

By submitting annotation along with your documents, you can increase the accuracy of the model\. With Annotations, you're not simply providing the location of the entity you're looking for, but you're also providing more accurate context to the custom entity you're seeking\.

For instance, if you're searching for the name John Johnson, with the entity type JUDGE, providing your annotation might help the model to learn that the person you want to find is a judge\. If it is able to use the context, then Amazon Comprehend won't find people named John Johnson who are attorneys or witnesses\. Without providing annotations, Amazon Comprehend will create its own version of an annotation, but won't be as effective at including only judges\. Providing your own annotations might help to achieve better results and to generate models that are capable of better leverage context when extracting custom entities\.

**Topics**
+ [Minimum number of annotations](#prep-training-data-ann)
+ [Annotation best practices](#cer-annotation-best-practices)
+ [Plain\-text annotation files](cer-annotation-csv.md)
+ [PDF annotation files](cer-annotation-manifest.md)
+ [Annotating PDF files](cer-annotation-pdf.md)

## Minimum number of annotations<a name="prep-training-data-ann"></a>

The minimum number of input documents and annotations required to train a model depends on the type of annotations\. 

**PDF annotations**  
To create a model for analyzing image files, PDFs, or Word documents, train your recognizer using PDF annotations\. For PDF annotations, provide at least 250 input documents and at least 100 annotations per entity\.  
If you provide a test dataset, the test data must include at least one annotation for each of the entity types specified in the creation request\. 

**Plain\-text annotations**  
To create a model for analyzing text documents, you can train your recognizer using plain\-text annotations\.   
For plain\-text annotations, provide at least three input documents and at least 25 annotations per entity\. If you provide less than 50 annotations total, Amazon Comprehend reserves more than 10% of the input documents to test the model \(unless you provided a test dataset in the training request\)\. Don't forget that the minimum document corpus size is 5 KB\.  
If your input contains only a few training documents, you may encounter an error that the training input data contains too few documents that mention one of the entities\. Submit the job again with additional documents that mention the entity\.  
If you provide a test dataset, the test data must include at least one annotation for each of the entity types specified in the creation request\.  
For an example of how to benchmark a model with a small dataset, see [Amazon Comprehend announces lower annotation limits for custom entity recognition](http://aws.amazon.com/blogs/machine-learning/amazon-comprehend-announces-lower-annotation-limits-for-custom-entity-recognition/) on the AWS blog site\.

## Annotation best practices<a name="cer-annotation-best-practices"></a>

There are a number of things to consider to get the best result when using annotations, including: 
+ Annotate your data with care and verify that you annotate every mention of the entity\. Imprecise annotations can lead to poor results\.
+ Input data should not contain duplicates, like a duplicate of a PDF you are going to annotate\. Presence of a duplicate sample might result in test set contamination and could negatively affect the training process, model metrics, and model behavior\.
+ Make sure that all of your documents are annotated, and that the documents without annotations are due to lack of legitimate entities, not due to negligence\. For example, if you have a document that says "J Doe has been an engineer for 14 years", you should also provide an annotation for "J Doe" as well as "John Doe"\. Failing to do so confuses the model and can result in the model not recognizing "J Doe" as ENGINEER\. This should be consistent within the same document and across documents\.
+ In general, more annotations lead to better results\.
+ You can train a model with the [minimum number](guidelines-and-limits.md#limits-custom-entity-recognition) of documents and annotations, but adding data usually improves the model\. We recommend increasing the volume of annotated data by 10% to increase the accuracy of the model\. You can run inference on a test dataset which remains unchanged and can be tested by different model versions\. You can then compare the metrics for successive model versions\.
+ Provide documents that resemble real use cases as closely as possible\. Synthesized data with repetitive patterns should be avoided\. The input data should be as diverse as possible to avoid overfitting and help the underlying model better generalize on real examples\.
+ It is important that documents should be diverse in terms of word count\. For example, if all documents in the training data are short, the resulting model may have difficulty predicting entities in longer documents\.
+ Try and give the same data distribution for training as you expect to be using when you're actually detecting your custom entities \(inference time\)\. For example, at inference time, if you expect to be sending us documents that have no entities in them, this should also be part of your training document set\.

For additional suggestions, see [Improving custom entity recognizer performance](https://docs.aws.amazon.com/comprehend/latest/dg/cer-metrics.html#cer-performance)\.
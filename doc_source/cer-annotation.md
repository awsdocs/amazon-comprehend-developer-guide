# Annotations<a name="cer-annotation"></a>

Annotations label entities in context by associating your custom entity types with the locations where they occur in your training documents\.

You can provide training data as a CSV file, an augmented manifest file from SageMaker Ground Truth, or a PDF\. 

## Annotation best practices<a name="cer-annotation-best-practices"></a>

There are a number of things to consider to get the best result when using annotations, including: 
+ Annotate your data with care and verify that you annotate every mention of the entity\. Imprecise annotations can lead to poor results\.
+ In general, more annotations lead to better results\.
+ Input data should not contain duplicates, like a duplicate of a PDF you are going to annotate\. Presence of a duplicate sample might result in test set contamination and could negatively affect the training process, model metrics, and model behavior\.
+ Make sure that all of your documents are annotated, and that the documents without annotations are due to lack of legitimate entities, not due to negligence\. For example, if you have a document that says "J Doe has been an engineer for 14 years", you should also provide an annotation for "J Doe" as well as "John Doe"\. Failing to do so confuses the model and can result in the model not recognizing "J Doe" as ENGINEER\. This should be consistent within the same document and across documents\.
+ To get started you need 250 documents and 100 annotations per entity\. This minimum of 250 documents helps to ensure prediction quality\. With more training data, you are more likely to produce a higher\-quality model\. If you want higher accuracy, we recommend increasing the volume of annotated data by 10% to further improve the accuracy\. This improvement might be best visible to you by running inference on a held\-out test set which remains unchanged and can be tested by different models\. In this way you can compare successive models\.
+ Provide documents that resemble real use cases as closely as possible\. Synthesized data with repetitive patterns should be avoided\. The input data should be as diverse as possible to avoid overfitting and help the underlying model better generalize on real examples\.
+ It is important that documents should be diverse in terms of word count\. For example, if all documents in the training data are short, the resulting model may have difficulty predicting entities in longer documents\.
+ Try and give the same data distribution for training as you expect to be using when you're actually detecting your custom entities \(inference time\)\. For example, at inference time, if you expect to be sending us documents that have no entities in them, this should also be part of your training document set\.

For additional suggestions, see [Improving custom entity recognizer performance](https://docs.aws.amazon.com/comprehend/latest/dg/cer-metrics.html#cer-performance)\.
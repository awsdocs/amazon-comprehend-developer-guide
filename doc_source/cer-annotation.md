# Annotations<a name="cer-annotation"></a>

Annotations for custom entity recognition needs to be in a comma\-separated value \(CSV\) file, with the following columns:
+ **File**—The name of the file containing the document\. For example, if one of the document files is located at `s3://custom-ner-test-datasets-us-west-2/train-small-001/documents/documents.txt`, the value in the `File` column will be `documents.txt`\. Please note that if the file name has an extension such as `.txt`, this must be included as part of the file name\.
+ **Line**—The line number containing the entity, starting with line 0\. 
+ **Begin Offset**—The character offset in the input text \(relative to the beginning of the line\) that shows where the entity begins\. The first character is at position 0\. 
+ **End Offset**—The character offset in the input text that shows where the entity ends\.
+ **Type**—The customer\-defined entity type\. Entity types must be an uppercase, underscore separated string such as MANAGER or SENIOR\_MANAGER\. Up to 12 entity types can be trained per model\. 

For example:

The file `documents.txt` contains four lines:

```
Josef Brown is an engineer in the high tech industry.
J Doe has been a engineer for 14 years.
Emilio Johnson is a judge on the Washington Supreme Court.
Our latest new employee, Smith, has been a manager in the industry for 4 years.
```

The CSV file with the list of annotations has the following lines: 

```
File, Line, Begin Offset, End Offset, Type
documents.txt, 0, 0, 11, ENGINEER
documents.txt, 1, 0, 5, ENGINEER
documents.txt, 3, 25, 30, MANAGER
```

**Note**  
In the annotations file, the line number containing the entity starts starting with line 0\. In this example, no line 2 is present because no entity was found in line 2 of `documents.txt`\. 

A minimum of 200 annotations are needed per entity to train a model for custom entity recognition\.

**Creating your data files**

It is important that your annotations be in a properly configured CSV file so your chance of having problems with your annotations file is minimal\. To manually configure your CSV file, the following must be true:
+ UTF\-8 encoding must be explicitly specified, even if its used as a default in most cases\.
+ It must include the column names: `File`, `Line`, `Begin Offset`, `End Offset`, `Type`\.

We highly recommended that CSV input files are generated programmatically to avoid potential issues\.

The following example uses Python to generate a CSV for the annotations shown above:

```
import csv 
with open("./annotations/annotations.csv", "w", encoding="utf-8") as csv_file:
    csv_writer = csv.writer(csv_file)
    csv_writer.writerow(["File", "Line", "Begin Offset", "End Offset", "Type"])
    csv_writer.writerow(["documents.txt", 0, 0, 12, "ENGINEER"])
    csv_writer.writerow(["documents.txt", 1, 0, 5, "ENGINEER"])
    csv_writer.writerow(["documents.txt", 3, 25, 30, "MANAGER"])
```

## Getting the Best Results<a name="anno-bestresults"></a>

There are a number of things to consider to get the best result when using annotations, including:
+ Annotate your data with care\. Imprecise annotations can lead to poor results\.
+ In general, more annotations will lead to better results\.
+ Input data should not contain duplicates\. Presence of duplicate samples might result into test set contamination and therefore negatively affect training process, model metrics, and behavior\.
+ For best results, provide at least 50% coverage of document in corpus with annotations\. Make sure that all documents in corpus have been annotated, and that the documents without annotations are due to lack of legitimate entities, not due to negligence\. For example, if you have a document "J Doe has been an engineer for 14 years", you should also provide an annotation for "J Doe" as well as "John Doe"\. Failing to do so will confuse the model and might lead to not recognizing "J Doe" as ENGINEER\.
+ Provide documents that resemble real usecases as closely as possible\. Don't use toy data or synthesized data for production systems\. The input data should be as diverse as possible to avoid overfitting and help underlying model better generalize on real examples\.
+ Try and give the same data distribution for training as you expect to be using when you're actually detecting your custom entities \(inference time\)\. For example, at inference time, if you expect to be sending us documents that have no entities in them, this should also be part of your training document set\.
+  We recommend use open source web tools such as [Brat Rapid Annotation Tool](http://brat.nlplab.org/) for data annotation, and then convert the annotations programmatically to fit the input format required by Amazon Comprehend\. You can also search online for general guidelines on how to measure and improve the quality of human annotations\.
+ [Amazon Mechanical Turk](https://www.mturk.com/) is a good resource for inexpensively annotating a large amount of data\.

Additional suggestions can be found at [Improving Custom Entity Recognizer Performance](cer-metrics.md#cer-performance) 
# Annotations<a name="cer-annotation"></a>

To train a custom entity recognizer, you can provide annotated training data\. Annotations label entities in context by associating your custom entity types with the locations where they occur in your training documents\. To learn about best practices, please see [Annotation Best Practices](annotation-best-practices.md)\.

You can provide training data as a CSV file or as an augmented manifest file from SageMaker Ground Truth\. 

## CSV File \(Plain Text Only\)<a name="cer-annotation-csv"></a>

Annotations for custom entity recognition needs to be in a comma\-separated value \(CSV\) file, with the following columns:
+ **File**—The name of the file containing the document\. For example, if one of the document files is located at `s3://custom-ner-test-datasets-us-west-2/train-small-001/documents/documents.txt`, the value in the `File` column will be `documents.txt`\. Please note that if the file name has an extension such as `.txt`, this must be included as part of the file name\.
+ **Line**—The line number containing the entity, starting with line 0\. 
+ **Begin Offset**—The character offset in the input text \(relative to the beginning of the line\) that shows where the entity begins\. The first character is at position 0\. 
+ **End Offset**—The character offset in the input text that shows where the entity ends\.
+ **Type**—The customer\-defined entity type\. Entity types must be an uppercase, underscore\-separated string\. We recommend using descriptive entity types such as MANAGER, SENIOR\_MANAGER, or PRODUCT\_CODE\. Up to 25 entity types can be trained per model\. 

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
In the annotations file, the line number containing the entity starts starting with line 0\. In this example, line 2 is not present in the CSV file because no entity was found in line 2 of `documents.txt`\. 

**Creating your data files**

It is important that your annotations be in a properly configured CSV file so your chance of having problems with your annotations file is minimal\. To manually configure your CSV file, the following must be true:
+ UTF\-8 encoding must be explicitly specified, even if its used as a default in most cases\.
+ It must include in the first line the column names: `File`, `Line`, `Begin Offset`, `End Offset`, `Type`\.

We highly recommended that CSV input files are generated programmatically to avoid potential issues\.

The following example uses Python to generate a CSV for the annotations shown above:

```
import csv 
with open("./annotations/annotations.csv", "w", encoding="utf-8") as csv_file:
    csv_writer = csv.writer(csv_file)
    csv_writer.writerow(["File", "Line", "Begin Offset", "End Offset", "Type"])
    csv_writer.writerow(["documents.txt", 0, 0, 11, "ENGINEER"])
    csv_writer.writerow(["documents.txt", 1, 0, 5, "ENGINEER"])
    csv_writer.writerow(["documents.txt", 3, 25, 30, "MANAGER"])
```

## Augmented Manifest File<a name="cer-annotation-manifest"></a>

An augmented manifest file is a labeled dataset that is produced by SageMaker Ground Truth\. Ground Truth is a data labeling service that helps you—or a workforce that you employ—build training datasets for machine learning models\. Amazon Comprehend accepts augmented manifest files as training data for custom models\. You can provide these files when you create a custom entty recognizer by using the Amazon Comprehend console or the [ CreateEntityRecognizer ](API_CreateEntityRecognizer.md) API action\. 

You can use the Ground Truth built\-in task type, Named Entity Recognition, to create a labeling job to have workers identify entities in text\. To learn more, see [Named Entity Recognition](https://docs.aws.amazon.com/sagemaker/latest/dg/sms-named-entity-recg.html#sms-creating-ner-console) in the *Amazon SageMaker Developer Guide*\. To learn more about Amazon SageMaker Ground Truth, see [Use Amazon SageMaker Ground Truth to Label Data](https://docs.aws.amazon.com/sagemaker/latest/dg/sms.html)\.

Augmented manifest files are in JSON lines format\. In these files, each line is a complete JSON object that contains a training document and its associated labels\. The following example is an augmented manifest file that trains an entity recognizer to detect the professions of individuals who are mentioned in the text:

```
{"source":"Diego Ramirez is an engineer in the high tech industry.","NamedEntityRecognitionDemo":{"annotations":{"entities":[{"endOffset":13,"startOffset":0,"label":"ENGINEER"}],"labels":[{"label":"ENGINEER"}]}},"NamedEntityRecognitionDemo-metadata":{"entities":[{"confidence":0.92}],"job-name":"labeling-job/namedentityrecognitiondemo","type":"groundtruth/text-span","creation-date":"2020-05-14T21:45:27.175903","human-annotated":"yes"}}
{"source":"J Doe is a judge on the Washington Supreme Court.","NamedEntityRecognitionDemo":{"annotations":{"entities":[{"endOffset":5,"startOffset":0,"label":"JUDGE"}],"labels":[{"label":"JUDGE"}]}},"NamedEntityRecognitionDemo-metadata":{"entities":[{"confidence":0.72}],"job-name":"labeling-job/namedentityrecognitiondemo","type":"groundtruth/text-span","creation-date":"2020-05-14T21:45:27.174910","human-annotated":"yes"}}
{"source":"Our latest new employee, Mateo Jackson, has been a manager in the industry for 4 years.","NamedEntityRecognitionDemo":{"annotations":{"entities":[{"endOffset":38,"startOffset":26,"label":"MANAGER"}],"labels":[{"label":"MANAGER"}]}},"NamedEntityRecognitionDemo-metadata":{"entities":[{"confidence":0.91}],"job-name":"labeling-job/namedentityrecognitiondemo","type":"groundtruth/text-span","creation-date":"2020-05-14T21:45:27.174035","human-annotated":"yes"}}
```

Each line in this JSON lines file is a complete JSON object, where the attributes include the document text, the annotations, and other metadata from Ground Truth\. The following example is a single JSON object in the augmented manifest file, but it's formatted for readability: 

```
{
  "source": "Diego Ramirez is an engineer in the high tech industry.",
  "NamedEntityRecognitionDemo": {
    "annotations": {
      "entities": [
        {
          "endOffset": 13,
          "startOffset": 0,
          "label": "ENGINEER"
        }
      ],
      "labels": [
        {
          "label": "ENGINEER"
        }
      ]
    }
  },
  "NamedEntityRecognitionDemo-metadata": {
    "entities": [
      {
        "confidence": 0.92
      }
    ],
    "job-name": "labeling-job/namedentityrecognitiondemo",
    "type": "groundtruth/text-span",
    "creation-date": "2020-05-14T21:45:27.175903",
    "human-annotated": "yes"
  }
}
```

In this example, the `source` attribute provides the text of the training document, and the `NamedEntityRecognitionDemo` attribute provides the annotations for the entities in the text\. The name of the `NamedEntityRecognitionDemo` attribute is arbitrary, and you provide a name of your choice when you define the labeling job in Ground Truth\.

In this example, the `NamedEntityRecognitionDemo` attribute is the *label attribute name*, which is the attribute that provides the labels that a Ground Truth worker assigns to the training data\. When you provide your training data to Amazon Comprehend, you must specify one or more label attribute names\. The number of attribute names that you specify depends on whether your augmented manifest file is the output of a single labeling job or a chained labeling job\.

If your file is the output of a single labeling job, specify the single label attribute name that was used when the job was created in Ground Truth\. 

If your file is the output of a chained labeling job, specify the label attribute name for one or more jobs in the chain\. Each label attribute name provides the annotations from an individual job\. You can specify up to 5 of these attributes for augmented manifest files that are produced by chained labeling jobs\. 

In an augmented manifest file, the label attribute name typically follows the `source` key\. If the file is the output of a chained job, there will be multiple label attribute names\. When you provide your training data to Amazon Comprehend, provide only those attributes that contain annotations that are relevant for your model\. Do not specify the attributes that end with "\-metadata"\.

For more information about chained labeling jobs, and for examples of the output that they produce, see [Chaining Labeling Jobs](https://docs.aws.amazon.com/sagemaker/latest/dg/sms-reusing-data.html) in the Amazon SageMaker Developer Guide\.
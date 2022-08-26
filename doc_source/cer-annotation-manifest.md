# PDF annotation files<a name="cer-annotation-manifest"></a>

For PDF annotations, you use SageMaker Ground Truth to create a labeled dataset in an augmented manifest file\. Ground Truth is a data labeling service that helps you \(or a workforce that you employ\) to build training datasets for machine learning models\. Amazon Comprehend accepts augmented manifest files as training data for custom models\. You can provide these files when you create a custom entity recognizer by using the Amazon Comprehend console or the [CreateEntityRecognizer](API_CreateEntityRecognizer.md) API action\. 

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
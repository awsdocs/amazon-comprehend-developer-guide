# Multi\-Label Mode<a name="how-document-classification-training-multi-label"></a>

In multi\-label classification, individual classes represent different categories, but these categories are somehow related and are not mutually exclusive\. As a result, each document has at least one class assigned to it, but can have more\. For example, a movie can simply be an action movie, or it can be an action movie, a science fiction movie, and a comedy, all at the same time\.

For training, multi\-label mode supports up to 1 million examples containing up to 100 unique classes\.

You can provide training data as a CSV file or as an augmented manifest file from Amazon SageMaker Ground Truth\.

## CSV File<a name="how-document-classification-training-multi-label-csv"></a>

To train a custom classifier, you can provide training data as a two\-column CSV file\. In it, labels are provided in the first column, and documents are provided in the second\.

Do not include headers for the individual columns\. Including headers in your CSV file may cause runtime errors\. Each line of the file contains one or more classes and the text of the training document\. More than one class can be indicated by using a delimiter \(such as a \| \) between each class\.

```
CLASS,Text of document 1
CLASS,Text of document 2
CLASS|CLASS|CLASS,Text of document 3
```

For example, the following line belongs to a CSV file that trains a custom classifier to detect genres in movie abstracts:

```
COMEDY|MYSTERY|SCIENCE_FICTION|TEEN,"A band of misfit teens become unlikely detectives when they discover troubling clues about their high school English teacher. Could the strange Mrs. Doe be an alien from outer space?"
```

The default delimiter between class names is a pipe \(\|\)\. However, you can use a different character as a delimiter\. The delimiter cannot be part of your class name\. For example, if your classes are CLASS\_1, CLASS\_2, and CLASS\_3, the underscore \(**\_**\) is part of the class name\. You cannot use then use an underscore as the delimiter for separating class names\.

## Augmented Manifest File<a name="how-document-classification-training-multi-label-manifest"></a>

An augmented manifest file is a labeled dataset that is produced by SageMaker Ground Truth\. Ground Truth is a data labeling service that helps you—or a workforce that you employ—build training datasets for machine learning models\. Amazon Comprehend accepts augmented manifest files as training data for custom models\. You can provide these files when you create a custom classifier by using the Amazon Comprehend console or the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) API action\. 

For more information about Ground Truth and the output that it produces, see [Use Amazon SageMaker Ground Truth to Label Data](https://docs.aws.amazon.com/sagemaker/latest/dg/sms.html) in the *Amazon SageMaker Developer Guide*\.

Augmented manifest files are in JSON lines format\. In these files, each line is a complete JSON object that contains a training document and its associated labels\. The following example is an augmented manifest file that trains a custom classifier to detect genres in movie abstracts:

```
{"source":"Document 1 text","MultiLabelJob":[0,4],"MultiLabelJob-metadata":{"job-name":"labeling-job/multilabeljob","class-map":{"0":"action","4":"drama"},"human-annotated":"yes","creation-date":"2020-05-21T19:02:21.521882","confidence-map":{"0":0.66},"type":"groundtruth/text-classification-multilabel"}}
{"source":"Document 2 text","MultiLabelJob":[3,6],"MultiLabelJob-metadata":{"job-name":"labeling-job/multilabeljob","class-map":{"3":"comedy","6":"horror"},"human-annotated":"yes","creation-date":"2020-05-21T19:00:01.291202","confidence-map":{"1":0.61,"0":0.61},"type":"groundtruth/text-classification-multilabel"}}
{"source":"Document 3 text","MultiLabelJob":[1],"MultiLabelJob-metadata":{"job-name":"labeling-job/multilabeljob","class-map":{"1":"action"},"human-annotated":"yes","creation-date":"2020-05-21T18:58:51.662050","confidence-map":{"1":0.68},"type":"groundtruth/text-classification-multilabel"}}
```

Each line in this JSON lines file is a complete JSON object, where the attributes include the document text, one or more class names, and other metadata from Ground Truth\. The following example is a single JSON object in the augmented manifest file, but it's formatted for readability: 

```
{
    "source": "A band of misfit teens become unlikely detectives when they discover troubling clues about their high school English teacher. Could the strange Mrs. Doe be an alien from outer space?",
    "MultiLabelJob": [
        3,
        8,
        10,
        11
    ],
    "MultiLabelJob-metadata": {
        "job-name": "labeling-job/multilabeljob",
        "class-map": {
            "3": "comedy",
            "8": "mystery",
            "10": "science_fiction",
            "11": "teen"
        },
        "human-annotated": "yes",
        "creation-date": "2020-05-21T19:00:01.291202",
        "confidence-map": {
            "3": 0.95,
            "8": 0.77,
            "10": 0.83,
            "11": 0.92
        },
        "type": "groundtruth/text-classification-multilabel"
    }
}
```

In this example, the `source` attribute provides the text of the training document, and the `MultiLabelJob` attribute assigns the indexes of several classes from a classification list\. The name of the `MultiLabelJob` attribute is arbitrary, and you provide a name of your choice when you define the labeling job in Ground Truth\. 

In this example, the `MultiLabelJob` attribute is the *label attribute name*, which is the attribute that provides the labels that a Ground Truth worker assigns to the training data\. When you provide your training data to Amazon Comprehend, you must specify one or more label attribute names\. The number of attribute names that you specify depends on whether your augmented manifest file is the output of a single labeling job or a chained labeling job\.

If your file is the output of a single labeling job, specify the single label attribute name that was used when the job was created in Ground Truth\. 

If your file is the output of a chained labeling job, specify the label attribute name for one or more jobs in the chain\. Each label attribute name provides the annotations from an individual job\. You can specify up to 5 of these attributes for augmented manifest files that are produced by chained labeling jobs\. 

In an augmented manifest file, the label attribute name typically follows the `source` key\. If the file is the output of a chained job, there will be multiple label attribute names\. When you provide your training data to Amazon Comprehend, provide only those attributes that contain annotations that are relevant for your model\. Do not specify the attributes that end with "\-metadata"\.

For more information about chained labeling jobs, and for examples of the output that they produce, see [Chaining Labeling Jobs](https://docs.aws.amazon.com/sagemaker/latest/dg/sms-reusing-data.html) in the Amazon SageMaker Developer Guide\.
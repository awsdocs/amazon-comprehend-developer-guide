# Multi\-class mode<a name="prep-classifier-data-multi-class"></a>

In multi\-class classification, each document can have one and only one class assigned to it\. The individual classes are mutually exclusive\. For example, a movie can be classed as a documentary or as science fiction, but not both at the same time\. 

After you train the custom classifier, you can analyze documents in either asynchronous or synchronous operations\. You can analyze a large number of documents at once using the asynchronous operation\. The resulting analysis is returned in a separate file\. Using the synchronous operation, you can only analyze a single document, but you can get results in real time\. These options are not available when you use multi\-label mode\. 

To train a custom classifier, you must provide labeled training data\. The labels in your training data should resemble the type of output that the trained model produces later when you provide unlabeled input\. You can provide training data as a CSV file or as an augmented manifest file from SageMaker Ground Truth\.

## CSV file<a name="prep-classifier-data-multi-class-csv"></a>

To train a custom classifier, you can provide training data as a two\-column CSV file\. In it, labels are provided in the first column, and documents are provided in the second\.

Classes can be any valid UTF\-8 string\. We suggest classes that are clear and don't overlap in meaning\. They can have white space, and they can consist of multiple words connected by underscores or hyphens\.

Training documents must end with \\n or \\r\\n and be valid UTF\-8 in a CSV file\.

The data must be in two columns\. Do not include headers for the individual columns\. Including headers in your file may cause runtime errors\. Each line of the file contains a single class and the text of a document that demonstrates that class\.

```
CLASS,Text of document 1
CLASS,Text of document 2
CLASS,Text of document 3
```

For example, the following line belongs to a CSV file that trains a custom classifier to detect whether an email message is spam:

```
SPAM, "Paulo, your $1000 award is waiting for you! Claim it while you still can at http://example.com."
```

## Augmented manifest file<a name="prep-classifier-data-multi-class-manifest"></a>

An augmented manifest file is a labeled dataset that is produced by SageMaker Ground Truth\. Ground Truth is a data labeling service that helps you—or a workforce that you employ—build training datasets for machine learning models\. Amazon Comprehend accepts augmented manifest files as training data for custom models\. You can provide these files when you create a custom classifier by using the Amazon Comprehend console or the [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateDocumentClassifier.html) API action\. 

For more information about Ground Truth and the output that it produces, see [Use Amazon SageMaker Ground Truth to Label Data](https://docs.aws.amazon.com/sagemaker/latest/dg/sms.html) in the *Amazon SageMaker Developer Guide*\.

Augmented manifest files are in JSON lines format\. In these files, each line is a complete JSON object that contains a training document and its associated labels\. The following example is an augmented manifest file that trains a custom classifier to determine whether an email message is spam:

```
{"source":"Document 1 text","MultiClassJob":0,"MultiClassJob-metadata":{"confidence":0.62,"job-name":"labeling-job/multiclassjob","class-name":"not_spam","human-annotated":"yes","creation-date":"2020-05-21T17:36:45.814354","type":"groundtruth/text-classification"}}
{"source":"Document 2 text","MultiClassJob":1,"MultiClassJob-metadata":{"confidence":0.81,"job-name":"labeling-job/multiclassjob","class-name":"spam","human-annotated":"yes","creation-date":"2020-05-21T17:37:51.970530","type":"groundtruth/text-classification"}}
{"source":"Document 3 text","MultiClassJob":1,"MultiClassJob-metadata":{"confidence":0.81,"job-name":"labeling-job/multiclassjob","class-name":"spam","human-annotated":"yes","creation-date":"2020-05-21T17:37:51.970566","type":"groundtruth/text-classification"}}
```

Each line in this JSON lines file is a complete JSON object, where the attributes include the document text, a single class name, and other metadata from Ground Truth\. The following example is a single JSON object in the augmented manifest file, but it's formatted for readability: 

```
{
    "source": "Paulo, your $1000 award is waiting for you! Claim it while you still can at http://example.com.",
    "MultiClassJob": 0,
    "MultiClassJob-metadata": {
        "confidence": 0.98,
        "job-name": "labeling-job/multiclassjob",
        "class-name": "spam",
        "human-annotated": "yes",
        "creation-date": "2020-05-21T17:36:45.814354",
        "type": "groundtruth/text-classification"
    }
}
```

In this example, the `source` attribute provides the text of the training document, and the `MultiClassJob` attribute assigns the index of a class from a classification list\. The name of the `MultiClassJob` attribute is arbitrary, and you provide a name of your choice when you define the labeling job in Ground Truth\. 

In this example, the `MultiClassJob` attribute is the *label attribute name*, which is the attribute that provides the labels that a Ground Truth worker assigns to the training data\. When you provide your training data to Amazon Comprehend, you must specify one or more label attribute names\. The number of attribute names that you specify depends on whether your augmented manifest file is the output of a single labeling job or a chained labeling job\.

If your file is the output of a single labeling job, specify the single label attribute name that was used when the job was created in Ground Truth\. 

If your file is the output of a chained labeling job, specify the label attribute name for one or more jobs in the chain\. Each label attribute name provides the annotations from an individual job\. You can specify up to 5 of these attributes for augmented manifest files that are produced by chained labeling jobs\. 

In an augmented manifest file, the label attribute name typically follows the `source` key\. If the file is the output of a chained job, there will be multiple label attribute names\. When you provide your training data to Amazon Comprehend, provide only those attributes that contain annotations that are relevant for your model\. Do not specify the attributes that end with "\-metadata"\.

For more information about chained labeling jobs, and for examples of the output that they produce, see [Chaining Labeling Jobs](https://docs.aws.amazon.com/sagemaker/latest/dg/sms-reusing-data.html) in the Amazon SageMaker Developer Guide\.
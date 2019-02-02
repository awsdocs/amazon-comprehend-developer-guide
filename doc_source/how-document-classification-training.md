# Training a Custom Classifier<a name="how-document-classification-training"></a>

To train a custom classifier you: 

1. Label your training data with the custom categories that you want the classifier to recognize\.

1. Put your training data in an Amazon S3 bucket\. The bucket must have AWS Identity and Access Management \(IAM\) Amazon Comprehend read permissions that allow Amazon Comprehend access\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\. You must also designate another S3 bucket for your output with the same requirements

1. Submit a training job using the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation\. 

You can train a custom classifier using any of the languages that work with Amazon Comprehend: English, Spanish, German, Italian, French, or Portuguese\. However, you can only train the classifier in one language\. Classifiers do not support multiple languages\.

After you ask Amazon Comprehend to create a custom classifier, you can monitor the progress of the request using the [](API_DescribeDocumentClassifier.md) operation\. Once the `Status` field is `TRAINED` you can then use the classifier to classify documents\.

Each custom classifier that you create can only be trained for a one category

## Creating Training Data<a name="how-document-classification-training-data"></a>

To train the custom classifier, you need to have the labels you want \(such as "PRICING", "DEFECT", "PROFANITY" and so on\), and examples of documents for each of those labels\. Each custom classifier you create categorize for multiple labels, based on your dataset, up to a total of 1000 unique labels\. However, its strongly recommended that you have a sufficient number of training documents to accommodate the multiple labels\.

**Note**  
It is important to remember that even though you can use multiple labels in a classifier, no hiearchy is determined by them when you use the classifier on unlabeled document\.

To prepare the training dataset, you build a CSV file that contains a label and document per line: 

```
label,Text of document 1
label,Text of document 2
```

In each line, the label is placed first, followed by the document\.

Labels can be virtually any valid UTF\-8 string, but we strongly suggest labels that are clear and don't overlap in meaning\. They must be uppercase, can be multitoken, have whitespace, consist of multiple words connect by underscores or hyphens or may even contain a comma in it, as long as it is correctly escaped\.

The document can follow the same pattern, although it is not necessary to be uppercase\. Training documents must be ended with with \\n or \\r\\n and be a valid UTF\-8 in a CSV file\. Additionally, each document should contain a good representative distribution of the types of documents that the classifier must categorize in general practice\.

We recommend that you train the model with up to 1,000 training documents for each label\. While a minimum of 50 training documents for each label is required, you will get significantly better accuracy with more documents\. The total size of the training documents must be less than 5 Gb and you can provide up to  1000 unique classes\. In the example below there are 5 total examples \(label, document pairs\)\. There are 5 labels, CAT, CAT, DOG, CAT, FISH\. There are **3 unique classes**: CAT, DOG, FISH\. Amazon Comprehend custom classification supports up to 1 million examples containing up to 1000 unique classes\.


| column 1 | column 2 | 
| --- | --- | 
| CAT | document text 1 | 
| CAT | document text 2 | 
| DOG | document text 3 | 
| CAT | document text 4 | 
| FISH | document text 5 | 

Amazon Comprehend Amazon Comprehend will use between 10 and 20 percent of the documents that you submit for training to test the custom classifier\. This testing material is randomly selected after we ensure that there are no labels in the test set which we have never seen before\. For example, if the data contained 1000 instances of the CAT label, 1000 instances of the DOG, and a single instance of the FISH label, then the test set would approximately be 100 CAT, 100 DOG\. The FISH label would not be included in the test set, as there is only a single example available\. please note that it's highly unlikely you will see a doc labelled as FISH during prediction/inference in a setting like this\. 

The result of the testing is returned in the `Metrics` fields returned by the [DescribeDocumentClassifier](API_DescribeDocumentClassifier.md) operation\.

Once you've finished training your model, the training metrics can provide you with information that you can use to decide if the model is trained sufficiently for your needs\. 

Once the training job completes, the service provides an endpoint to a trained model that is now used to organize unlabeled documents\. 
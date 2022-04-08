# Test the training data<a name="testing-the-model"></a>

Once the model has been trained, Amazon Comprehend uses between 10 and 20 percent of the training documents to test the custom classifier model\. Testing the model provides you with metrics that you can use to determine if the model is trained well enough for your purposes\. These metrics are displayed in the **Classifier performance** section of the **Classifier details** page in the console\. They are also returned in the `Metrics` fields returned by the [DescribeDocumentClassifier](API_DescribeDocumentClassifier.md) operation\.

For example, in the sample of training data below, there are 5 labels, DOCUMENTARY, DOCUMENTARY, SCIENCE\_FICTION, DOCUMENTARY, ROMANTIC\_COMEDY\. There are **3 unique classes**: DOCUMENTARY, SCIENCE\_FICTION, ROMANTIC\_COMEDY\. 


| Column 1 | Column 2 | 
| --- | --- | 
| DOCUMENTARY | document text 1 | 
| DOCUMENTARY | document text 2 | 
| SCIENCE\_FICTION | document text 3 | 
| DOCUMENTARY | document text 4 | 
| ROMANTIC\_COMEDY | document text 5 | 

For instance, if the data contained 1000 instances of the DOCUMENTARY class, 900 instances of the SCIENCE\_FICTION, and a single instance of the ROMANTIC\_COMEDY class, then the test set would approximately be 100 DOCUMENTARY and 90 SCIENCE\_FICTION instances\. The ROMANTIC\_COMEDY class would not be included in the test set, as there is only a single example available\. This is because it's highly unlikely you will see a document classified as ROMANTIC\_COMEDY during prediction/inference in a setting like this\. 

Once you've finished training your model, the training metrics can provide you with information that you can use to decide if the model is trained sufficiently for your needs\. 
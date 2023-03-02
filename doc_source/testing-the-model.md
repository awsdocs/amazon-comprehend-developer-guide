# Test the training data<a name="testing-the-model"></a>

After training the model, Amazon Comprehend tests the custom classifier model\. If you don't provide a test dataset, Amazon Comprehend trains the model with 90 percent of the training data and reserves 10 percent of the training data to use for testing\. If you do provide a test dataset, the test data must include at least one example for each unique label in the training dataset\. 

Testing the model provides you with metrics that you can use to determine if the model is trained well enough for your purposes\. These metrics are displayed in the **Classifier performance** section of the **Classifier details** page in the console\. They are also returned in the `Metrics` fields returned by the [DescribeDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeDocumentClassifier.html) operation\.

In the example training data below, there are 5 labels, DOCUMENTARY, DOCUMENTARY, SCIENCE\_FICTION, DOCUMENTARY, ROMANTIC\_COMEDY\. There are **3 unique classes**: DOCUMENTARY, SCIENCE\_FICTION, ROMANTIC\_COMEDY\. 


| Column 1 | Column 2 | 
| --- | --- | 
| DOCUMENTARY | document text 1 | 
| DOCUMENTARY | document text 2 | 
| SCIENCE\_FICTION | document text 3 | 
| DOCUMENTARY | document text 4 | 
| ROMANTIC\_COMEDY | document text 5 | 

For auto split \(where Amazon Comprehend reserves 10 percent of the training data to use for testing\), if there are only a few examples of a specific label in the training data, the test dataset may contain zero examples of that label\. For instance, if the training dataset contains 1000 instances of the DOCUMENTARY class, 900 instances of SCIENCE\_FICTION, and a single instance of the ROMANTIC\_COMEDY class, the test dataset contains roughly 100 DOCUMENTARY and 90 SCIENCE\_FICTION instances, but no ROMANTIC\_COMEDY instances, as there is only a single example available\. 

Once you've finished training your model, the training metrics can provide you with information that you can use to decide if the model is trained sufficiently for your needs\. 
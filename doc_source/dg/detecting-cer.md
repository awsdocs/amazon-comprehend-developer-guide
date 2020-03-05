# Detecting Custom Entities<a name="detecting-cer"></a>

Once you have a trained model, use the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation to detect custom entities in your documents\. 

Using this operation, you provide the same information as you would when detecting preset entities\. However, in addition to the input and output locations \(S3 buckets\), you also provide the EntityRecognizerArn, which is the Amazon Resource Name \(ARN\) of the trained model\. This ARN is supplied by the response to the [CreateEntityRecognizer](API_CreateEntityRecognizer.md) operation\. 

You can examine one document or many, and each model can be trained on up to 12 custom entities at a time\. You can search for up to 12 entities per **StartEntitiesDetectionJob** operation\.\. 

To detect custom entities in a document set, you use the following request syntax:

The examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\. 

```
aws comprehend start-entities-detection-job \
     --entity-recognizer-arn "entity recognizer arn" \
     --job-name job name \
     --data-access-role-arn "data access role arn" \
     --language-code en \
     --input-data-config "S3Uri=s3://Bucket Name/Bucket Path" \
     --output-data-config "S3Uri=s3://Bucket Name/Bucket Path/" \
     --region region
```

Amazon Comprehend will respond with the `JobID` and `JobStatus` and will return the output from the job in the S3 bucket that you specified in your request\. This output will be similar to the following:

```
{"File": "50_docs", "Line": 0, "Entities": [{"BeginOffset": 0, "EndOffset": 22, "Score": 0.9763959646224976, "Text": "John Johnson", "Type": "JUDGE"}"]}
{"File": "50_docs", "Line": 1, "Entities": [{"BeginOffset": 11, "EndOffset": 15, "Score": 0.9615424871444702, "Text": "Thomas Kincaid", "Type": "JUDGE"}}]}
```
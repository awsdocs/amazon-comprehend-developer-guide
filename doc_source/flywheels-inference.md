# Using flywheels for analysis<a name="flywheels-inference"></a>

You can use the flywheel's active model version to run analysis for custom classification or entity recognition\. The active model version is configurable\. You can use the [ console](flywheels-iterate.md#flywheels-iterate-console-promote) or the [UpdateFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_UpdateFlywheel.html) API operation to set a new version of the model to be the active model version\. 

To use the flywheel, specify the flywheel ARN instead of a custom model ARN when you configure the analysis task\. Amazon Comprehend runs the analysis using the flywheel's active model version\. 

## Real\-time analysis<a name="flywheels-inference-console"></a>

You use an endpoint to run real\-time analysis\. When you create or update an endpoint, you can configure it with the flywheel ARN instead of a model ARN\. When you run the real\-time analysis, select the endpoint associated with the flywheel\. Amazon Comprehend runs the analysis using the active model version of the flywheel\.

When you use [UpdateFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_UpdateFlywheel.html) to set a new active model version for the flywheel, the endpoint updates automatically to start using the new active model version\. If you don't want the endpoint to update automatically, configure the endpoint \(using [UpdateEndpoint](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_UpdateEndpoint.html)\) to use the model version ARN directly\. The endpoint continues to use this model version if the flywheel active model version changes\.

For custom classification, use the [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) API operation\. For custom entity recognition, use the [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) API request\. Provide the endpoint of the flywheel in the EndpointArn parameter\.

You can also use the console to run real\-time analysis for [custom classification](custom-sync.md) or [custom entity recognition](detecting-cer-real-time.md)\.

## Asynchronous jobs<a name="flywheels-inference-api"></a>

### <a name="flywheels-inference-api-async"></a>

For custom classification, use the [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartDocumentClassificationJob.html) API request to start an aysnchronous job\. Provide the FlywheelArn parameter instead of the DocumentClassifierArn\.

For custom entity recognition, use the [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEntitiesDetectionJob.html) API request\. Provide the FlywheelArn parameter instead of the EntityRecognizerArn\.

You can use the console to run asynchronous analysis jobs for [custom classification](analysis-jobs-custom-classifier.md) or [custom entity recognition](detecting-cer.md)\. When you create the job, enter the flywheel ARN in the **Recognizer model** or **Classifier model** field\.
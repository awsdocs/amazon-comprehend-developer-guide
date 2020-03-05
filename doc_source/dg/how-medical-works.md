# How It Works<a name="how-medical-works"></a>

Amazon Comprehend Medical uses a pretrained model to examine and analyze a document or set of documents\. This model is continuously trained on a large body of text so that there is no need for you to provide training data\. Amazon Comprehend Medical can examine and analyze documents in English\.

With Amazon Comprehend Medical you can examine unstructured clinical text for the following use cases:
+ Use the [DetectEntitiesV2](API_medical_DetectEntitiesV2.md) and [DetectPHI](API_medical_DetectPHI.md) operations to detect entities in unstructured clinical text from individual documents\. These are synchronous operations\. You send a document to the Amazon Comprehend Medical service and receive the results of the analysis in the response\. 
+  Use the [StartEntitiesDetectionV2Job](API_medical_StartEntitiesDetectionV2Job.md) and [StartPHIDetectionJob](API_medical_StartPHIDetectionJob.md) operations to start asynchronous jobs to analyze clinical text that is stored in an S3 bucket\. The output of the detection job is written to an S3 bucket so that you can retrieve it when the job is complete\.
+  Use the [InferRxNorm](API_medical_InferRxNorm.md) operation to detect medications as entities and link those entities to standardized concepts in the RxNorm knowledge base\.
+  Use the [InferICD10CM](API_medical_InferICD10CM.md) operation to detect medical conditions as entities and link those entities to standardized concepts in the ICD\-10\-CM coding system\.
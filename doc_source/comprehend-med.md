# What is Comprehend Medical?<a name="comprehend-med"></a>

Comprehend Medical is a new service that detects useful information in unstructured clinical text\. As much as 75% of all health record data is found in unstructured text: physician's notes, discharge summaries, test results, case notes, and so on\. Comprehend Medical uses Natural Language Processing \(NLP\) models to leverage the latest advances in machine learning to sort through this enormous quantity of data and retrieve valuable information that is otherwise difficult to retrieve and use without significant manual effort\.

**Supported Languages**

With this initial release, Comprehend Medical only detects medical entities in English language texts\.

## Important Notice<a name="important-notice"></a>

Amazon Comprehend Medical is not a substitute for professional medical advice, diagnosis, or treatment\. Amazon Comprehend Medical provides confidence scores that indicate the level of confidence in the accuracy of the detected entities\. You should identify the right confidence threshold for your use case, and use high confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately\-trained human reviewers\. For example, Amazon Comprehend Medical should not be used in patient care scenarios without trained medical professionals reviewing results for accuracy and exercising their medical judgment\.

## Examples<a name="how-examples-med"></a>

The following examples show how you might use Comprehend Medical in your health care applications:

**Example 1: Patient Case Management and Outcome**  
Doctors and health care providers can manage their unstructured notes effectively, and can rapidly assess medical information about their patients that doesn't easily fit into the forms traditionally used\. Analyzing case notes, for instance, helps providers identify candidates for early screening for certain medical conditions before the condition becomes more difficult and expensive to treat\. It also allows patients to report their health concerns in a narrative that can provide more information than simple formats, and then makes those narratives easily available to providers, allowing more accurate diagnosis of medical conditions\.

**Example 2: Clinical Research**  
Life sciences and research organizations can:  
+ Optimize the matching process for fitting patients into clinical trials using information from unstructured clinical texts, such as case notes and test results\. For instance, for a clinical trial of a new heart medicine, it becomes much simpler to analyze text and find specific information about heart failure patients\.
+ Improve pharmacovigilance and post\-market surveillance to monitor adverse drug events by using Comprehend Medical to detect pertinent information in clinical text that is otherwise difficult to access\.
+ Assess therapeutic effectiveness by easily detecting vital information in follow\-up notes and other clinical texts\. For instance, it can be easier and more effective to monitor how patients respond to certain therapies by analyzing their narratives\.

**Example 3: Medical Billing and Healthcare Revenue Cycle Management**  
Payors can expand their analytics to include unstructured documents such as clinical notes, where more information about a diagnosis as it relates to billing codes can be determined\. Natural language processing \(NLP\) is the most critical component of computer\-assisted coding \(CAC\)\. Comprehend Medical uses the latest advances in NLP to analyze clinical text, helping to decrease time to revenue and improve reimbursement accuracy\.

## Benefits<a name="how-benefits-med"></a>

Some of the benefits of using Comprehend Medical include:
+ **Integrate powerful natural language processing into your applications**—Comprehend Medical removes the complexity of building text analysis capabilities into your applications by making powerful and accurate natural language processing available with a simple API\. You don't need textual analysis expertise to take advantage of the insights that Comprehend Medical produces\.
+ **Deep learning based on natural language processing**—Comprehend Medical uses deep learning technology to accurately analyze text\. Our models are constantly trained with new data across multiple domains to improve accuracy\.
+ **Scalable natural language processing**—Comprehend Medical enables you to analyze millions of documents so that you can detect the information they contain and more quickly develop better insights into patient health and care\.
+ **Integrate with other AWS services**—Comprehend Medical is designed to work seamlessly with other AWS services like Amazon S3 and AWS Lambda\. Store your documents in Amazon S3, analyze real\-time data with Kinesis Data Firehose, or transcribe patient narratives using Amazon Transcribe and then analyze those narratives using Comprehend Medical\. Support for AWS Identity and Access Management \(IAM\) makes it easy to securely control access to Comprehend Medical operations\. Using IAM, you can create and manage AWS users and groups to grant the appropriate access to your developers and end users\.
+ **Low cost**—With Comprehend Medical, you only pay for the documents that you analyze\. There are no minimum fees or upfront commitments\. 

## HIPAA compliance<a name="how-medical-hipaa"></a>

This is a HIPAA Eligible Service\. For more information about AWS, U\.S\. Health Insurance Portability and Accountability Act of 1996 \(HIPAA\), and using AWS services to process, store, and transmit protected health information \(PHI\), see [HIPAA Overview](https://aws.amazon.com/compliance/hipaa-compliance/)\.

Connections to Comprehend Medical containing PHI must be encrypted and, by default, all connections to Comprehend Medical use HTTPS over TLS\. Comprehend Medical does not persistently store customer content and therefore does not require customers to configure encryption at\-rest within the service\.

## Are You a First\-time User of Comprehend Medical?<a name="first-time-user-med"></a>

If you are a first\-time user of Comprehend Medical, we recommend that you read the following sections in order:

1. [How It Works](how-medical-works.md) – This section introduces Comprehend Medical concepts\. 

1. [Getting Started with Amazon Comprehend Medical](getting-started-med.md) – In this section, you set up your account and test Comprehend Medical\. 

1. [API Reference](API_Reference.md) – In this section, you'll find reference documentation for Comprehend Medical operations\.
# Real\-time analysis for custom entity recognition \(API\)<a name="detecting-cer-real-time-api"></a>

You can use the Amazon Comprehend API to run real\-time analysis with a custom model\. First, you create an endpoint to run the real\-time analysis\. After you create the endpoint, you run the real\-time analysis\.

For information about provisioning endpoint throughput, and the associated costs, see [Using Amazon Comprehend endpoints](using-endpoints.md)\.

**Topics**
+ [Creating an endpoint for custom entity detection](#detecting-cer-real-time-create-endpoint-api)
+ [Running real\-time custom entity detection](#detecting-cer-real-time-run)

## Creating an endpoint for custom entity detection<a name="detecting-cer-real-time-create-endpoint-api"></a>

For information about the costs associated with endpoints, see [Using Amazon Comprehend endpoints](using-endpoints.md)\.

### Creating an Endpoint with the AWS CLI<a name="detecting-cer-real-time-create-endpoint-examples"></a>

To create an endpoint by using the AWS CLI, use the `create-endpoint` command:

```
$ aws comprehend create-endpoint \
> --desired-inference-units number of inference units \
> --endpoint-name endpoint name \
> --model-arn arn:aws:comprehend:region:account-id:model/example \
> --tags Key=Key,Value=Value
```

If your command succeeds, Amazon Comprehend responds with the endpoint ARN:

```
{
   "EndpointArn": "Arn"
}
```

For more information about this command, its parameter arguments, and its output, see [https://docs.aws.amazon.com/cli/latest/reference/comprehend/create-endpoint.html](https://docs.aws.amazon.com/cli/latest/reference/comprehend/create-endpoint.html) in the AWS CLI Command Reference\.

## Running real\-time custom entity detection<a name="detecting-cer-real-time-run"></a>

After you create an endpoint for your custom entity recognizer model, you use the endpoint to run the [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) API operation\. You can provide text input using the `text` or `bytes` parameter\. Enter the other input types using the `bytes` parameter\.

For image files and PDF files, you can use the `DocumentReaderConfig` parameter to override the default text extraction actions\. For details, see [Setting text extraction options](idp-set-textract-options.md)\.

### Detecting entities in text using the AWS CLI<a name="detecting-cer-real-time-run-cli1"></a>

To detect custom entities in text, run the `detect-entities` command with the input text in the `text` parameter\.

**Example : Use the CLI to detect entities in input text**  

```
$ aws comprehend detect-entities \
> --endpoint-arn arn \
> --language-code en \
> --text  "Andy Jassy is the CEO of Amazon."
```
If your command succeeds, Amazon Comprehend responds with the analysis\. For each entity that Amazon Comprehend detects, it provides the entity type, text, location, and confidence score\.

### Detecting entities in semi\-structured documents using the AWS CLI<a name="detecting-cer-real-time-run-cli2"></a>

To detect custom entities in PDF, Word, or image file, run the `detect-entities` command with the input file in the `bytes` parameter\.

**Example : Use the CLI to detect entities in an image file**  
This example shows how to pass in the image file using the `fileb` option to base64 encode the image bytes\. For more information, see [Binary large objects](https://docs.aws.amazon.com/cli/latest/userguide/cli-usage-parameters-types.html#parameter-type-blob) in the AWS Command Line Interface User Guide\.   
This example also passes in a JSON file named `config.json` to set the text extraction options\.  

```
$ aws comprehend detect-entities \
> --endpoint-arn arn \
> --language-code en \
> --bytes fileb://image1.jpg   \
> --document-reader-config file://config.json
```
The config\.json file contains the following content\.  

```
 {
    "DocumentReadMode": "FORCE_DOCUMENT_READ_ACTION",
    "DocumentReadAction": "TEXTRACT_DETECT_DOCUMENT_TEXT"    
 }
```

For more information about the command syntax, see [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) in the Amazon Comprehend API Reference\.
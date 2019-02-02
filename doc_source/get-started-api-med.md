# Step 4: Getting Started Using the Comprehend Medical APIs<a name="get-started-api-med"></a>

The following examples demonstrate how to use Comprehend Medical operations using the AWS CLI, Java, and Python\. Use them to learn about Comprehend Medical operations and as building blocks for your own applications\.

To run the AWS CLI and Python examples, install the AWS CLI\. For more information, see [Step 2: Set Up the AWS Command Line Interface \(AWS CLI\)](setup-awscli-med.md)\.

To run the Java examples, install the AWS SDK for Java\. For instructions for installing the AWS SDK for Java, see [ Set up the AWS SDK for Java](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-install.html)\.

**Topics**
+ [Detecting Medical Entities Using the AWS Command Line Interface](#med-examples-cli)
+ [Detecting Medical Entities Using the AWS SDK for Java](#med-examples-java)
+ [Detecting Medical Entities Using the AWS SDK for Python \(Boto\)](#med-examples-python)

## Detecting Medical Entities Using the AWS Command Line Interface<a name="med-examples-cli"></a>

The following example demonstrates using the `DetectEntities` operation using the AWS CLI to return the medical entities detected in text\. To run the example, you must install the AWS CLI\. For more information, see [Step 2: Set Up the AWS Command Line Interface \(AWS CLI\)](setup-awscli-med.md)\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehendmedical detect-entities \
    --endpoint endpoint \
    --region region \
    --text "aspirin is required 20 mg po daily for 2 times as tab"
```

 The response is the following:

```
{
    "Entities": [
        {
            "Category": "MEDICATION", 
            "BeginOffset": 0, 
            "EndOffset": 7, 
            "Text": "aspirin", 
            "Traits": [], 
            "Score": 0.9988090991973877, 
            "Attributes": [
                {
                    "BeginOffset": 20, 
                    "EndOffset": 25, 
                    "Text": "20 mg", 
                    "Traits": [], 
                    "Score": 0.9559056162834167, 
                    "Type": "DOSAGE", 
                    "Id": 1, 
                    "RelationshipScore": 0.9981593489646912
                }, 
                {
                    "BeginOffset": 26, 
                    "EndOffset": 28, 
                    "Text": "po", 
                    "Traits": [], 
                    "Score": 0.9995359182357788, 
                    "Type": "ROUTE_OR_MODE", 
                    "Id": 2, 
                    "RelationshipScore": 0.9969323873519897
                }, 
                {
                    "BeginOffset": 29, 
                    "EndOffset": 34, 
                    "Text": "daily", 
                    "Traits": [], 
                    "Score": 0.9803128838539124, 
                    "Type": "FREQUENCY", 
                    "Id": 3, 
                    "RelationshipScore": 0.9990783929824829
                }, 
                {
                    "BeginOffset": 39, 
                    "EndOffset": 46, 
                    "Text": "2 times", 
                    "Traits": [], 
                    "Score": 0.8623972535133362, 
                    "Type": "DURATION", 
                    "Id": 4, 
                    "RelationshipScore": 0.9996501207351685
                }, 
                {
                    "BeginOffset": 50, 
                    "EndOffset": 53, 
                    "Text": "tab", 
                    "Traits": [], 
                    "Score": 0.784785270690918, 
                    "Type": "FORM", 
                    "Id": 5, 
                    "RelationshipScore": 0.9986748695373535
                }
            ], 
            "Type": "GENERIC_NAME", 
            "Id": 0
        }
    ], 
    "UnmappedAttributes": []
}
```

## Detecting Medical Entities Using the AWS SDK for Java<a name="med-examples-java"></a>

The following example uses the `DetectEntities` operation with Java\. To run the example, install the AWS SDK for Java\. For instructions on installing the AWS SDK for Java, see [ Set up the AWS SDK for Java](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-install.html)\. 

```
import com.amazonaws.auth.AWSCredentials;
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.client.builder.AwsClientBuilder;
import com.amazonaws.services.comprehendmedical.AWSComprehendMedical;
import com.amazonaws.services.comprehendmedical.AWSComprehendMedicalClient;
import com.amazonaws.services.comprehendmedical.model.DetectEntitiesRequest;
import com.amazonaws.services.comprehendmedical.model.DetectEntitiesResult;
 
public class SampleAPICall {
 
    public static void main() {
 
        AWSCredentialsProvider credentials
                = new AWSStaticCredentialsProvider(new BasicAWSCredentials("YOUR AWS ACCESS KEY", "YOUR AWS SECRET"));
 
        AWSComprehendMedical client = AWSComprehendMedicalClient.builder()
                                                                .withCredentials(credentials)
                                                                .withRegion("YOUR REGION")
                                                                .build();
 
 
        DetectEntitiesRequest request = new DetectEntitiesRequest();
        request.setText("cerealx 84 mg daily");
 
        DetectEntitiesResult result = client.detectEntities(request);
        result.getEntities().forEach(System.out::println);
    }
}
```

The output from the program contains the three entities found in the input text, their location in the input text, and a confidence level that the entity was correctly identified\. The following output shows the `Generic_Name`, `Dosage`, and `Frequency` entities from the preceding example\.

```
{Id: 0,BeginOffset: 0,EndOffset: 3,Score: 0.9940211,Text: Bob,Category: 
PROTECTED_HEALTH_INFORMATION,Type: NAME,Traits: [],}
{Id: 2,BeginOffset: 23,EndOffset: 30,Score: 0.99914634,Text: aspirin,Category: MEDICATION,Type: GENERIC_NAME,Traits: [],Attributes: 
[{Type: DOSAGE,Score: 0.9630807,RelationshipScore: 0.99969745,Id: 1,BeginOffset: 14,EndOffset: 19,Text: 50 mg,Traits: []}]}
```

## Detecting Medical Entities Using the AWS SDK for Python \(Boto\)<a name="med-examples-python"></a>

The following example uses the `DetectEntities` operation with Python\. To run the sample, install the AWS CLI\. For more information, see [Step 2: Set Up the AWS Command Line Interface \(AWS CLI\)](setup-awscli.md)\.

```
import boto3
client = boto3.client(service_name='comprehendmedical', region_name='YOUR REGION')
result = client.detect_entities(Text= 'cerealx 84 mg daily')
entities = result['Entities'];
for entity in entities:
    print('Entity', entity)
```

The output from the program contains the three entities found in the input text, their location in the input text, and a confidence level that the entity was correctly identified\. The following output shows the `Generic_Name`, `Dosage`, and `Frequency` entities from the preceding example\.

```
('Entity', {u'Category': u'MEDICATION', u'BeginOffset': 0, u'EndOffset': 7, 
            u'Text': u'cerealx', u'Traits': [], u'Score': 0.8877691626548767, u'Attributes': [{u'BeginOffset': 8, u'EndOffset': 13, 
            u'Text': u'84 mg', u'Traits': [], u'Score': 0.9337134957313538, u'Type': u'DOSAGE', u'Id': 1, u'RelationshipScore': 0.9995118379592896}, 
            {u'BeginOffset': 14, u'EndOffset': 19, u'Text': u'daily', u'Traits': [], u'Score': 0.990627646446228, u'Type': u'FREQUENCY', 
            u'Id': 2, u'RelationshipScore': 0.9987651109695435}], u'Type': u'BRAND_NAME', u'Id': 0})
```
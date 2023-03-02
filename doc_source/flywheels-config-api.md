# Configuring flywheels using the API<a name="flywheels-config-api"></a>

You can use the Amazon Comprehend API to create, update, and delete flywheels\. 

When you create a flywheel, Amazon Comprehend creates a data lake to hold all the data that the flywheel needs, such as the training data and test data for each version of the model\.

When you delete a flywheel, Amazon Comprehend doesn't delete the data lake or the model associated with the flywheel\. 

The flywheel delete operation fails if the flywheel is running an iteration or creating a dataset\.

Review the information in section [Flywheel creation](flywheels-about.md#flywheels-about-create) before you create a new flywheel\.

## Create a flywheel for an existing model<a name="flywheels-config-api-create-existing"></a>

Use the [CreateFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateFlywheel.html) operation to create a flywheel for an existing model\. 

**Example**  

```
aws comprehend create-flywheel  \
    --flywheel-name "myFlywheel2"  \
    --active-model-arn  "modelArn"  \
    --data-access-role-arn   arn:aws::iam::111122223333:role/testFlywheelDataAccess \
    --data-lake-s3-uri": "https://s3-bucket-endpoint"   \
```
If the operation is successful, the response includes the flywheel ARN\.  

```
{
  "FlywheelArn": "arn:aws::comprehend:aws-region:111122223333:flywheel/name",
  "ActiveModelArn": "modelArn"
}
```

## Create a flywheel for a new model<a name="flywheels-config-api-create-new"></a>

Use the [CreateFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateFlywheel.html) operation to create a flywheel for a new custom classification model\. 

**Example**  

```
aws comprehend create-flywheel \
    --flywheel-name "myFlywheel2" \
    --data-access-role-arn  arn:aws::iam::111122223333:role/testFlywheelDataAccess \
    --model-type "DOCUMENT_CLASSIFIER" \
    --data-lake-s3-uri  "s3Uri"  \
    --task-config  file://taskConfig.json
```
The taskConfig\.json file contains the following content\.  

```
{
    "LanguageCode": "en",
    "DocumentClassificationConfig": {
        "Mode": "MULTI_LABEL",
        "Labels": ["optimism", "anger"]
    } 
}
```
The API response body includes the following content\.  

```
{
  "FlywheelArn": "arn:aws::comprehend:aws-region:111122223333:flywheel/name",
  "ActiveModelArn": "modelArn"
}
```

## Describe a flywheel<a name="flywheels-config-api-desc"></a>

Use the Amazon Comprehend [DescribeFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeFlywheel.html) operation to retrieve configured information about a flywheel\. 

```
aws comprehend describe-flywheel \
    --flywheel-arn  "flywheelArn"
```

The API response body includes the following content\.

```
{
  "FlywheelProperties": {
      "FlywheelArn": "arn:aws::comprehend:aws-region:111122223333:flywheel/myTestFlywheel",
      "DataAccessRoleArn": "arn:aws::iam::111122223333:role/Admin",
      "TaskConfig": {
          "LanguageCode": "en",
          "DocumentClassificationConfig": {
              "Mode": "MULTI_LABEL"
          }
      },
      "DataLakeS3Uri": "s3://my-test-datalake/flywheelbasictest/myTestFlywheel/schemaVersion=1/20220801T014326Z",
      "Status": "ACTIVE",
      "ModelType":  "DOCUMENT_CLASSIFIER",
      "CreationTime": 1659318206.102,
      "LastModifiedTime": 1659318249.05
  }
}
```

## Update a flywheel<a name="flywheels-config-api-update"></a>

Use the [UpdateFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_UpdateFlywheel.html) operation to update the modifiable configuration values of the flywheel\. 

Some configuration fields are JSON structures with subfields\. To update one or more subfields, provide values for all the subfields \(Amazon Comprehend sets the value to null for any subfield missing in the request\)\. 

If you omit a top\-level parameter in the `UpdateFlywheel` request, Amazon Comprehend doesn't change the values of the parameter or any of its subfields in the flywheel\.

To add or remove tags on the flywheel, use the [TagResource](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_TagResource.html) and [UntagResource](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_UntagResource.html) operations\.

You can promote a model version by setting the `ActiveModelArn` parameter, as shown in the following example\. 

```
aws comprehend update-flywheel \
    --region aws-region \
    --flywheel-arn  "flywheelArn" \
    --active-model-arn  "modelArn" \
```

The API response body includes the following content\.

```
{
  "FlywheelArn": "arn:aws::comprehend:aws-region:111122223333:flywheel/name",
  "ActiveModelArn": "modelArn"
}
```

## Delete a flywheel<a name="flywheels-config-api-delete"></a>

Use the Amazon Comprehend [DeleteFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DeleteFlywheel.html) operation to delete flywheels\. 

```
aws comprehend delete-flywheel \
    --flywheel-arn  "flywheelArn"
```

A successful API response contains an empty response message body

## List the flywheels<a name="flywheels-config-api-list"></a>

Use the Amazon Comprehend [ListFlywheels](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ListFlywheels.html) operation to retrieve a list of flywheels in the current region\. 

```
aws comprehend list-flywheel \
    --region aws-region \
    --endpoint-url  "uri"
```

The API response body includes the following content\.

```
{
    "FlywheelSummaryList": [
        {
            "FlywheelArn": "arn:aws::comprehend:aws-region:111122223333:flywheel/myTestFlywheel",
            "DataLakeS3Uri": "s3://my-test-datalake/flywheelbasictest/myTestFlywheel/schemaVersion=1/20220801T014326Z",
            "Status": "ACTIVE",
            ""ModelType":  "DOCUMENT_CLASSIFIER",
            "CreationTime": 1659318206.102,
            "LastModifiedTime": 1659318249.05
        }
    ]
}
```
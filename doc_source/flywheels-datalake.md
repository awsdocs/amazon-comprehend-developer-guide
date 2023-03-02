# Flywheel data lakes<a name="flywheels-datalake"></a>

When you create a flywheel, Amazon Comprehend creates a data lake in your account to contain all the flywheel data, such as the input and output data required for the model versions\. 

Amazon Comprehend creates the data lake in the Amazon S3 location that you specify when you create the flywheel\. You can specify the location as an Amazon S3 bucket or as a new folder in an Amazon S3 bucket\. 

## Data lake folder structure<a name="flywheels-datalake-folders"></a>

When Amazon Comprehend creates the data lake, it sets up the following folder structure in the Amazon S3 location\.

**Warning**  
Amazon Comprehend manages the data lake folder organization and contents\. Always use the Amazon Comprehend API operations to modify the data lake folders, or your flywheel may not operate correctly\.

```
  Document Pool
  Annotations Pool
  Staging
  Model Datasets
    (data for each version of the model)
    VersionID-1
      Training
      Test
      ModelStats
    VersionID-2
      Training
      Test
      ModelStats
```

To view the training assessment of a model version, perform these steps: 

1. Open the folder named **Model Datasets** at the root level of the data lake\. This folder contains a subfolder for each version of the model\. 

1. Open the folder for the model version of interest\.

1. Open the folder named **ModelStats** to view the statistics for the model\.

## Data lake management<a name="flywheels-datalake-mgmt"></a>

Amazon Comprehend performs the following tasks to manage the data lake on your behalf:
+ Defines the folder structure of the data lake and ingests datasets into the appropriate folders\.
+ Manages the input documents \(such as text files and annotation files\) required to train the model\.
+ Manages the training and evaluation output data associated with each version of the model\.
+ Manages encryption for files stored in the data lake\.

Amazon Comprehend performs all the data creation and update operations for the data lake\. You retain full access to the data in the data lake\. For example:
+ You have full access to the contents of the data lake\.
+ The data lake remains available after you delete the flywheel\.
+ You can configure access logs for the Amazon S3 bucket that contains the data lake\.
+ You can provide encryption keys for the data\. You specify these when you create the flywheel\.

 We recommend the following best practices:
+ Don't manually add your own folders or files into the data lake\. Don't modify or delete any files in the data lake\.
+ Always use the Amazon Comprehend creation and update operations to add or modify data in the data lake\. For example, use `CreateDataset` to provide training or test data and `StartFlywheelIteration` to generate evaluation data for model versions\.
+ The data lake structure may evolve over time\. Don't create downstream scripts or programs that rely explicitly on the data lake structure\. 
+ When you provide a data lake location for the flywheel, we recommend creating a common prefix for data related to all flywheels or using a different prefix for each flywheel\. We don't recommend using the complete data lake path of one flywheel as the prefix for another flywheel\.
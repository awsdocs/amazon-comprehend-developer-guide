# Flywheel overview<a name="flywheels-about"></a>

A *flywheel* is an Amazon Comprehend resource that orchestrates the training and evaluation of new versions of a custom model\. You can create a flywheel to use an existing trained model, or Amazon Comprehend can create and train a new model for the flywheel\. Use flywheels with plain\-text custom models for custom classification or custom entity recognition\.

You can configure and manage flywheels using the Amazon Comprehend console or API\. You can also configure flywheels using AWS CloudFormation\.

When you create a flywheel, Amazon Comprehend creates a *data lake* in your account\. The [data lake](flywheels-datalake.md) stores and manages all the flywheel data, such as the training data and test data for all versions of the model\.

You set the *active model version* to be the version of the flywheel model that you want to use for inference jobs or Amazon Comprehend endpoints\. Initially, the flywheel contains one version of the model\. Over time, as you train new model versions, you select the best\-performing version to be the active model version\. When a user specifies the flywheel ARN to run an inference job, Amazon Comprehend runs the job using the flywheel's active model version\. 

Periodically, you obtain new labeled data \(training data or test data\) for the model\. You make new data available to the flywheel by creating one or more *datasets*\. A dataset contains input data for training or testing the custom model associated with a flywheel\. Amazon Comprehend uploads the input data to the flywheel's data lake\.

To incorporate the new datasets into your custom model, you create and run a flywheel *iteration*\. A flywheel iteration is a workflow that uses the new datasets to evaluate the active model version and to train a new model version\. Based on the metrics for the existing and new model versions, you can decide whether to promote the new model version to be the active version\.

You can use the flywheel active model version to run custom analysis \(real time or asynchronous jobs\)\. To use the flywheel model for real\-time analysis, you must create an [endpoint](https://docs.aws.amazon.com/comprehend/dg/latest/manage-endpoints.html) for the flywheel\.

There is no additional charge for using flywheels\. However, when you run a flywheel iteration, you incur the standard charges for training a new model version and storing the model data\. For detailed pricing information, see [Amazon Comprehend Pricing](http://aws.amazon.com/comprehend/pricing)\.

**Topics**
+ [Flywheel datasets](#flywheels-datasets)
+ [Flywheel creation](#flywheels-about-create)
+ [Flywheel states](#flywheels-about-states)
+ [Flywheel iterations](#flywheels-about-iterations)

## Flywheel datasets<a name="flywheels-datasets"></a>

To add new labeled data to a flywheel, you create a dataset\. You configure each dataset as training data or test data\. You associate the dataset with a specific flywheel and custom model\. 

After you create a dataset, Amazon Comprehend uploads the data to the flywheel's data lake\. For more information, see [Flywheel data lakes](flywheels-datalake.md)\. 

## Flywheel creation<a name="flywheels-about-create"></a>

When you create a flywheel, you can associate the flywheel with an existing trained model, or the flywheel can create a new model\. 

When you create a flywheel with an existing model, you specify the active model version\. Amazon Comprehend copies the model's training data and test data into the flywheel's data lake\. Make sure that the model training and test data exist in the same Amazon S3 location as when you created the model\. 

To create a flywheel for a new model, you provide a dataset for training data \(and an optional dataset for test data\) when you create the flywheel\. When you run the flywheel to create the first flywheel iteration, the flywheel trains the new model\.

 When you train a custom model, you specify a list of custom labels \(custom classification\) or custom entities \(custom entity recognition\) for the model to recognize\. Note the following important points about custom labels/entities:
+ When you create a flywheel for a new model, the list of labels/entities that you provide during flywheel creation is the final list for the flywheel\.
+ When you create a flywheel from an existing model, the list of labels/entities associated with that model becomes the final list for the flywheel\.
+ If you associate a new dataset with the flywheel, and that dataset contains additional labels/entities, Amazon Comprehend ignores the new labels/entities\.
+ You can review a flywheel's label/entity list using the [DescribeFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeFlywheel.html) API operation\.
**Note**  
For custom classification, Amazon Comprehend populates the label list after the flywheel status becomes ACTIVE\. Wait until the flywheel is active before calling the DescribeFlywheel API operation\. 

## Flywheel states<a name="flywheels-about-states"></a>

A flywheel transitions between the following states: 
+ CREATING \- Amazon Comprehend is creating the flywheel resources\. You can perform read operations on the flywheel, such as `DescribeFlywheel`\.
+ ACTIVE \- The flywheel is active\. You can determine if a flywheel iteration in progress and view the status of the iteration\. You can perform read actions on the flywheel and actions such as `DeleteFlywheel` and `UpdateFlywheel`\.
+ UPDATING \- Amazon Comprehend is updating the flywheel\. You can perform read operations on the flywheel\.
+ DELETING \- Amazon Comprehend is deleting the flywheel\. You can perform read operations on the flywheel\.
+ FAILED \- the flywheel create operation failed\.

After Amazon Comprehend deletes a flywheel, you retain access to all the model data in the flywheel data lake\. Amazon Comprehend deletes all the internal metadata required for managing the flywheel resources\. Amazon Comprehend also deletes the datasets associated with this flywheel \(the model data is saved in the data lake\)\.

## Flywheel iterations<a name="flywheels-about-iterations"></a>

When you obtain new training or test data for a flywheel model, you create one or more new datasets to upload the new data to the flywheel's data lake\. 

You then run the flywheel to create a new flywheel iteration\. The flywheel iteration evaluates the current active model version using the new data and stores the results in the data lake\. The flywheel also creates and trains a new model version\.

 If the new model exhibits better performance than the current active model version, you can promote the new model version to be the active model version\. You can use the [ console](flywheels-iterate.md#flywheels-iterate-console-promote) or the [UpdateFlywheel](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_UpdateFlywheel.html) API operation to update the active model version\.
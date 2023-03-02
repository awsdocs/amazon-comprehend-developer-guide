# Creating and managing custom models<a name="manage-models"></a>

Amazon Comprehend includes built\-in NLP \(natural language processing\) models that you can use for analyzing insights or topic modeling\. You can also use Amazon Comprehend to create custom models for entity recognition and document classification\. 

You can use model versioning to keep track of your model's history\. When you create and train a new model version, you can make changes to the training dataset\. Amazon Comprehend displays details \(including model performance\) for each model version on the model details page\. Over time, you can see how model performance changes as you make changes to your training dataset\. 

You can create model versions using the Amazon Comprehend console or API\. As an alternative, Amazon Comprehend provides [Flywheels](flywheels.md) to simplify the tasks associated with training and evaluating new custom model versions\.

After you create a custom model, you can share the model with other users by allowing other AWS accounts to import a copy of your model\.

**Topics**
+ [Model versioning with Amazon Comprehend](model-versioning.md)
+ [Copying custom models between AWS accounts](custom-copy.md)
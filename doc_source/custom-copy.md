# Copying custom models between AWS accounts<a name="custom-copy"></a>

Amazon Comprehend users can copy trained custom models between AWS accounts in a two\-step process\. First, a user in one AWS account \(account A\), *shares* a custom model that's in their account\. Then, a user in another AWS account \(account B\) *imports* the model into their account\. The account B user does not need to train the model, and does not need to copy \(or access\) the original training data or test data\.

To share a custom model in account A, the user attaches an AWS Identity and Access Management \(IAM\) policy to a model version\. This policy authorizes an entity in account B, such as an IAM user or role, to import the model version into Amazon Comprehend in their AWS account\. The account B user must import the model into the same AWS Region as the original model\.

To import the model in account B, the user of this account provides Amazon Comprehend with the necessary details, such as the Amazon Resource Name \(ARN\) of the model\. By importing the model, this user creates a new custom model in their AWS account that replicates the model that they imported\. This model is fully trained and ready for inference jobs, such as document classification or named entity recognition\.

Copying a custom model is useful if:
+ You belong to an organization that uses multiple AWS accounts\. For example, your organization might have an AWS account for each phase of development, such as build, stage, test, and deploy\. Or, it might have distinct AWS accounts for business functions, such as data science and engineering\.
+ Your organization works with another, such as an AWS Partner, that trains custom models in Amazon Comprehend and provides them to you as their client\.

In scenarios like these, you can quickly copy a trained custom entity recognizer or document classifier from one AWS account to another\. Copying a model in this way is easier than the alternative, where you copy training data between AWS accounts to train duplicate models\.

**Topics**
+ [Sharing a custom model with another AWS account](custom-copy-sharing.md)
+ [Importing a custom model from another AWS account](custom-copy-importing.md)
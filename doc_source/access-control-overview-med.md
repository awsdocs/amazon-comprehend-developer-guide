# Overview of Managing Access Permissions to Amazon Comprehend Medical Resources<a name="access-control-overview-med"></a>

Permissions policies govern the access to an action\. An account administrator attaches permissions policies to IAM identities to manage access to actions\. IAM identities include users, groups, and roles\.

**Note**  
An *account administrator* \(or administrator user\) is a user with administrator privileges\. For more information, see [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) in the *IAM User Guide*\.

When you grant permissions, you decide both who and what actions get the permissions\.

**Topics**
+ [Managing Access to Actions](#access-control-manage-access-intro-med)
+ [Specifying Policy Elements: Actions, Effects, and Principals](#access-control-specify-comprehend-actions-med)
+ [Specifying Conditions in a Policy](#specifying-conditions-med)

## Managing Access to Actions<a name="access-control-manage-access-intro-med"></a>

A *permissions policy* describes who has access to what\. The following section explains the options for permissions policies\.

**Note**  
This section explains IAM in the context of Amazon Comprehend Medical\. It doesn't provide detailed information about the IAM service\. For more about IAM, see [What Is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) in the *IAM User Guide*\. For information about IAM policy syntax and descriptions, see [AWS IAM Policy Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html) in the *IAM User Guide*\.

Policies attached to an IAM identity are *identity\-based* policies\. Policies attached to a resource are *resource\-based* policies\. Amazon Comprehend Medical supports only identity\-based policies\. 

### Identity\-Based Policies \(IAM Policies\)<a name="access-control-manage-access-intro-iam-policies-med"></a>

You can attach policies to IAM identities\. Here are two examples\.
+ **Attach a permissions policy to a user or a group in your account**\. To allow a user or a group of users to call an Amazon Comprehend Medical action, attach a permissions policy to a user\. Attach a policy to a group that contains the user\.
+ **Attach a permissions policy to a role to grant cross\-account permissions**\. To grant cross\-account permissions, attach an identity\-based policy to an IAM role\. For example, the administrator in Account A can create a role to grant cross\-account permissions to another account\. In this example, call it Account B, which could also be an AWS service\.

  1. Account A administrator creates an IAM role and attaches a policy to the role that grants permissions to resources in Account A\.

  1. Account A administrator attaches a trust policy to the role\. The policy identifies Account B as the principal who can assume the role\. 

  1. Account B administrator can then delegate permissions to assume the role to any users in Account B\. This allows users in Account B to create or access resources in Account A\. If you want to grant an AWS service the permissions to assume the role, the principal in the trust policy can also be an AWS service principal\.

  For more information about using IAM to delegate permissions, see [Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/access.html) in the *IAM User Guide*\.

For more information about using identity\-based policies with Amazon Comprehend Medical, see [Using Identity\-Based Policies \(IAM Policies\) for Amazon Comprehend Medical](access-control-managing-permissions-med.md)\. For more information about users, groups, roles, and permissions, see [Identities \(Users, Groups, and Roles\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) in the *IAM User Guide*\. 

### Resource\-Based Policies<a name="access-control-manage-access-intro-resource-policies-med"></a>

Other services, such as AWS Lambda, support resource\-based permissions policies\. For example, you can attach a policy to an S3 bucket to manage access permissions to that bucket\. Amazon Comprehend Medical doesn't support resource\-based policies\. 

## Specifying Policy Elements: Actions, Effects, and Principals<a name="access-control-specify-comprehend-actions-med"></a>

Amazon Comprehend Medical defines a set of API operations \(see [Actions](API_Operations.md)\)\. To grant permissions for these API operations, Amazon Comprehend Medical defines a set of actions that you can specify in a policy\. 

The four items here are the most basic policy elements\.
+ **Resource** – In a policy, use an Amazon Resource Name \(ARN\) to identify the resource to which the policy applies\. For Amazon Comprehend Medical, the resource is always `"*"`\.
+ **Action** – Use action keywords to identify operations that you want to allow or deny\. For example, depending on the specified effect, `comprehendmedical:DetectEntities` either allows or denies the user permission to perform the Amazon Comprehend Medical `DetectEntities` operation\.
+ **Effect** – Specify the effect of the action that occurs when the user requests the specific action—either allow or deny\. If you don't explicitly grant access to \(allow\) a resource, access is implicitly denied\. You can also explicitly deny access to a resource\. You might do this to make sure that a user cannot access the resource, even if a different policy grants access\.
+ **Principal** – In identity\-based policies, the user that the policy is attached to is the implicit principal\. 

To learn more about IAM policy syntax and descriptions, see [AWS IAM Policy Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies.html) in the *IAM User Guide*\.

For a table showing all of the Amazon Comprehend Medical API actions, see [Amazon Comprehend Medical API Permissions: Actions, Resources, and Conditions Reference](comprehend-api-permissions-ref-med.md)\.

## Specifying Conditions in a Policy<a name="specifying-conditions-med"></a>

When you grant permissions, you use the IAM policy language to specify the conditions under which a policy should take effect\. For example, you might want a policy to be applied only after a specific date\. For more information about specifying conditions in a policy language, see [Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#Condition) in the *IAM User Guide*\. 

AWS provides a set of predefined condition keys for all AWS services that support IAM for access control\. For example, you can use the `aws:userid` condition key to require a specific AWS ID when requesting an action\. For more information and a complete list of AWS keys, see [Available Keys for Conditions](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

Amazon Comprehend Medical does not provide any additional condition keys\.
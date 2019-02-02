# Step 1: Set Up an AWS Account and Create an Administrator User<a name="setting-up-med"></a>

Before you use Comprehend Medical for the first time, complete the following tasks:

1. [Sign Up for AWS](#setting-up-signup-med)

1. [Create an IAM User](#setting-up-iam-med)

## Sign Up for AWS<a name="setting-up-signup-med"></a>

When you sign up for Amazon Web Services \(AWS\), your AWS account is automatically signed up for all AWS services, including Comprehend Medical\. You are charged only for the services that you use\.

With Comprehend Medical, you pay only for the resources that you use\. If you are a new AWS customer, you can get started with Comprehend Medical for free\. For more information, see [AWS Free Usage Tier](https://aws.amazon.com//free/)\.

If you already have an AWS account, skip to the next section\. 

**To create an AWS account**

1. Open [https://aws\.amazon\.com/](https://aws.amazon.com/), and then choose **Create an AWS Account**\.
**Note**  
If you previously signed in to the AWS Management Console using AWS account root user credentials, choose **Sign in to a different account**\. If you previously signed in to the console using IAM credentials, choose **Sign\-in using root account credentials**\. Then choose **Create a new AWS account**\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code using the phone keypad\.

Record your AWS account ID because you'll need it for the next task\.

## Create an IAM User<a name="setting-up-iam-med"></a>

Services in AWS, such as Comprehend Medical, require that you provide credentials when you access them\. This allows the service to determine whether you have permissions to access the service's resources\. 

We strongly recommend that you access AWS using AWS Identity and Access Management \(IAM\), not the credentials for your AWS account\. To use IAM to access AWS, create an IAM user, add the user to an IAM group with administrative permissions, and then grant administrative permissions to the IAM user\. You can then access AWS using a special URL and the IAM user's credentials\.

The Getting Started exercises in this guide assume that you have a user with administrator privileges, `adminuser`\. 

**To create an administrator user and sign in to the console**

1. Create an administrator user called `adminuser` in your AWS account\. For instructions, see [Creating Your First IAM User and Administrators Group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) in the *IAM User Guide*\.

1. Sign in to the AWS Management Console using a special URL\. For more information, see [How Users Sign In to Your Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_how-users-sign-in.html) in the *IAM User Guide*\.

For more information about IAM, see the following:
+ [AWS Identity and Access Management \(IAM\)](https://aws.amazon.com/iam/)
+ [Getting Started](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started.html)
+ [IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/)

## Next Step<a name="setting-up-next-step-2-med"></a>

[Step 2: Set Up the AWS Command Line Interface \(AWS CLI\)](setup-awscli-med.md)
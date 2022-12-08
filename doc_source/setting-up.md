# Setting up<a name="setting-up"></a>

Before you use Amazon Comprehend for the first time, complete the following tasks\.

**Topics**
+ [Sign up for AWS](#setting-up-signup)
+ [Create an IAM user](#setting-up-iam)
+ [Set up the AWS Command Line Interface \(AWS CLI\)](#setup-awscli)

## Sign up for AWS<a name="setting-up-signup"></a>

When you sign up for Amazon Web Services \(AWS\), your AWS account is automatically signed up for all AWS services, including Amazon Comprehend\. You are charged only for the services that you use\.

With Amazon Comprehend, you pay only for the resources that you use\. If you are a new AWS customer, you can get started with Amazon Comprehend for free\. For more information, see [AWS free usage tier](https://aws.amazon.com/free/)\.

If you already have an AWS account, skip to the next section\. 

**To create an AWS account**

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

   When you sign up for an AWS account, an *AWS account root user* is created\. The root user has access to all AWS services and resources in the account\. As a security best practice, [assign administrative access to an administrative user](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html), and use only the root user to perform [tasks that require root user access](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html)\.

Record your AWS account ID because you'll need it for the next task\.

## Create an IAM user<a name="setting-up-iam"></a>

Services in AWS, such as Amazon Comprehend, require that you provide credentials when you access them\. This allows the service to determine whether you have permissions to access the service's resources\. 

We strongly recommend that you access AWS using AWS Identity and Access Management \(IAM\), not the credentials for your AWS account\. To use IAM to access AWS, create an IAM user, add the user to an IAM group with administrative permissions, and then grant administrative permissions to the IAM user\. You can then access AWS using a special URL and the IAM user's credentials\.



The Getting Started exercises in this guide assume that you have a user with administrator privileges, `adminuser`\. 

**To create an administrator user and sign in to the console**

1. Create an administrator user called `adminuser` in your AWS account\. For instructions, see [Creating your first IAM user and administrators group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) in the *IAM User Guide*\.

1. Sign in to the AWS Management Console using a special URL\. For more information, see [How users sign in to Your Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_how-users-sign-in.html) in the *IAM User Guide*\.

For more information about IAM, see the following:
+ [AWS Identity and Access Management \(IAM\)](https://aws.amazon.com/iam/)
+ [Getting started](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started.html)
+ [IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/)

## Set up the AWS Command Line Interface \(AWS CLI\)<a name="setup-awscli"></a>

You don't need the AWS CLI to perform the steps in the Getting Started exercises\. However, some of the other exercises in this guide do require it\. If you prefer, you can skip this step and go to [Getting started with Amazon Comprehend](getting-started.md), and set up the AWS CLI later\. 



**To set up the AWS CLI**

1. Download and configure the AWS CLI\. For instructions, see the following topics in the *AWS Command Line Interface User Guide*: 
   + [Getting set up with the AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-set-up.html)
   + [Configuring the AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)

1. In the AWS CLI config file, add a named profile for the administrator user:\. 

   ```
   [profile adminuser]
   aws_access_key_id = adminuser access key ID
   aws_secret_access_key = adminuser secret access key
   region = aws-region
   ```

   You use this profile when executing the AWS CLI commands\. For more information about named profiles, see [Named profiles](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-multiple-profiles) in the *AWS Command Line Interface User Guide*\. For a list of AWS Regions, see [Regions and endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.

1. Verify the setup by typing the following help command at the command prompt: 

   ```
   aws help
   ```
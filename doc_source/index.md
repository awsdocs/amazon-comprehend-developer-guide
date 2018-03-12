# Amazon Comprehend Developer Guide

-----
*****Copyright &copy; 2018 Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in 
     connection with any product or service that is not Amazon's, 
     in any manner that is likely to cause confusion among customers, 
     or in any manner that disparages or discredits Amazon. All other 
     trademarks not owned by Amazon are the property of their respective
     owners, who may or may not be affiliated with, connected to, or 
     sponsored by Amazon.

-----
## Contents
+ [What Is Amazon Comprehend?](what-is.md)
+ [How It Works](how-it-works.md)
   + [Detecting Entities](how-entities.md)
   + [Detecting Key Phrases](how-key-phrases.md)
   + [Detecting the Primary Language](how-languages.md)
   + [Detecting Sentiments](how-sentiment.md)
   + [Batch Processing Documents](how-batch.md)
   + [Topic Modeling](topic-modeling.md)
+ [Getting Started with Amazon Comprehend](getting-started.md)
   + [Step 1: Set Up an AWS Account and Create an Administrator User](setting-up.md)
   + [Step 2: Set Up the AWS Command Line Interface (AWS CLI)](setup-awscli.md)
   + [Step 3: Getting Started Using the Amazon Comprehend Console](get-started-console.md)
      + [Analyzing Documents Using the Console](get-started-console-analysis.md)
      + [Creating a Topic Modeling Job Using the Console](getting-started-console-topics.md)
   + [Step 4: Getting Started Using the Amazon Comprehend API](get-started-api.md)
      + [Detecting the Dominant Language](get-started-api-dominant-language.md)
      + [Detecting Named Entities](get-started-api-entities.md)
      + [Detecting Key Phrases](get-started-api-key-phrases.md)
      + [Detecting Sentiment](get-started-api-sentiment.md)
      + [Topic Modeling](get-started-topics.md)
      + [Using the Batch APIs](get-started-batch.md)
+ [Authentication and Access Control for Amazon Comprehend](auth-and-access-control.md)
   + [Overview of Managing Access Permissions to Amazon Comprehend Resources](access-control-overview.md)
   + [Using Identity-Based Polices (IAM Policies) for Amazon Comprehend](access-control-managing-permissions.md)
   + [Amazon Comprehend API Permissions: Actions, Resources, and Conditions Reference](comprehend-api-permissions-ref.md)
+ [Guidelines and Limits](guidelines-and-limits.md)
+ [API Reference](API_Reference.md)
   + [Actions](API_Operations.md)
      + [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md)
      + [BatchDetectEntities](API_BatchDetectEntities.md)
      + [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md)
      + [BatchDetectSentiment](API_BatchDetectSentiment.md)
      + [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md)
      + [DetectDominantLanguage](API_DetectDominantLanguage.md)
      + [DetectEntities](API_DetectEntities.md)
      + [DetectKeyPhrases](API_DetectKeyPhrases.md)
      + [DetectSentiment](API_DetectSentiment.md)
      + [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md)
      + [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md)
   + [Data Types](API_Types.md)
      + [BatchDetectDominantLanguageItemResult](API_BatchDetectDominantLanguageItemResult.md)
      + [BatchDetectEntitiesItemResult](API_BatchDetectEntitiesItemResult.md)
      + [BatchDetectKeyPhrasesItemResult](API_BatchDetectKeyPhrasesItemResult.md)
      + [BatchDetectSentimentItemResult](API_BatchDetectSentimentItemResult.md)
      + [BatchItemError](API_BatchItemError.md)
      + [DominantLanguage](API_DominantLanguage.md)
      + [Entity](API_Entity.md)
      + [InputDataConfig](API_InputDataConfig.md)
      + [KeyPhrase](API_KeyPhrase.md)
      + [OutputDataConfig](API_OutputDataConfig.md)
      + [SentimentScore](API_SentimentScore.md)
      + [TopicsDetectionJobFilter](API_TopicsDetectionJobFilter.md)
      + [TopicsDetectionJobProperties](API_TopicsDetectionJobProperties.md)
   + [Common Errors](CommonErrors.md)
   + [Common Parameters](CommonParameters.md)
+ [Document History for Amazon Comprehend](doc-history.md)